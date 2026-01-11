# Architecture Overview and Key Components

## System Architecture

This application uses a modern full-stack architecture that separates the user interface from the business logic and data management. The system consists of three main layers that communicate through well-defined interfaces:

### Frontend Layer
The user interface runs as a standalone web application built with modern web technologies. When you interact with the application through your browser, you're communicating with this layer, which handles everything you see and click.

### Backend Layer
Behind the scenes, a separate application server processes all business logic, manages user authentication, and handles data operations. This server exposes a standardized API that the frontend uses to request and send data.

### Database Layer
All application data is stored in a PostgreSQL database that only the backend can access directly. This includes user accounts, application data, and system configurations.

## How Components Work Together

### Separated Frontend and Backend

The application uses a clear separation between what you see (the frontend) and what processes your requests (the backend). These two parts run independently and communicate through HTTP requests:

- The frontend makes requests to specific API endpoints (accessible at `/api/v1/`)
- The backend processes these requests and returns structured data
- Both parts can be updated, scaled, or deployed independently

**CORS Configuration**: To allow the frontend and backend to communicate securely across different domains, the system includes Cross-Origin Resource Sharing (CORS) settings. The backend accepts requests from the configured frontend location and any additional trusted domains specified in the environment settings.

### Authentication and Security

When you sign in to the application, the system uses JSON Web Tokens (JWT) to remember who you are:

1. **Initial Login**: When you provide your email and password, the backend verifies your credentials against the database
2. **Token Generation**: If your credentials are correct, the backend creates a unique JWT token that expires after 8 days
3. **Subsequent Requests**: Your browser automatically includes this token with every request you make
4. **Token Validation**: The backend checks this token before processing any request to ensure you're authorized

**Security Key**: All tokens are cryptographically signed using a secret key that's unique to your installation. This prevents anyone from creating fake tokens or impersonating users.

### Database Integration

The application uses SQLModel with PostgreSQL to manage all persistent data:

**Connection Management**: The backend connects to PostgreSQL using connection details specified in the environment configuration (server address, port, database name, username, and password). The connection string is automatically constructed from these individual settings.

**Data Models**: Application data is organized into structured tables that define what information can be stored and how different pieces of data relate to each other.

### Containerized Services

The application runs as multiple isolated services that work together:

**Database Service**: A PostgreSQL container stores all application data with persistent storage that survives restarts. The service includes health checks to ensure the database is ready before other services attempt to connect.

**Backend Service**: The application server runs in its own container and depends on the database being healthy before it starts. It exposes port 8000 and includes health monitoring.

**Frontend Service**: The web interface runs in a separate container that serves the user interface on port 80.

**Database Management Tool**: An Adminer interface provides a convenient way to inspect and manage database contents during development.

**Initialization Service**: A special "prestart" service runs before the backend starts to set up the database schema and create the initial administrator account.

### Automatic API Client Generation

The frontend doesn't manually write code to communicate with the backend. Instead, it uses automatically generated client code:

**OpenAPI Specification**: The backend automatically generates a complete description of its API in OpenAPI format (available at `/api/v1/openapi.json`). This specification documents every endpoint, what data it expects, and what it returns.

**Generated Client Code**: Based on this specification, the system generates TypeScript code that the frontend uses to make API calls. This includes:
- Type definitions for all data structures
- Functions for each API endpoint
- Request and response schemas
- Error handling patterns

**Benefits**: When the backend API changes, regenerating the client code ensures the frontend always uses the correct data structures and endpoints. You don't need to manually synchronize the two.

### Environment-Based Configuration

The application adapts its behavior based on the environment it's running in:

**Local Development**: When running on your development machine, the system uses relaxed security settings, enables detailed error messages, and connects to a local database.

**Staging and Production**: In deployed environments, the system enforces strict security requirements, validates that default passwords have been changed, and may enable error tracking through Sentry.

**Configuration Sources**: All environment-specific settings come from a `.env` file that defines database credentials, security keys, email server details, and feature flags. The backend reads this file at startup and validates that all required settings are present.

### Request Flow Through the System

When you perform an action in the application, here's what happens:

1. **User Action**: You click a button or submit a form in your browser
2. **Frontend Processing**: The web application validates your input and prepares an API request
3. **Token Inclusion**: Your authentication token is automatically attached to the request
4. **Network Transit**: The request travels over the network to the backend server
5. **CORS Validation**: The backend verifies the request came from an allowed origin
6. **Authentication Check**: The system validates your token and extracts your user identity
7. **Business Logic**: The backend processes your request according to the application's rules
8. **Database Operations**: If needed, the backend reads from or writes to the PostgreSQL database
9. **Response Generation**: The backend packages the results into a structured response
10. **Frontend Update**: The web application receives the response and updates what you see

### Development vs Production Differences

**Development Mode**:
- Frontend runs on `http://localhost:5173`
- Backend runs on `http://localhost:8000`
- Database warnings appear for default passwords
- Detailed error messages help with debugging
- Services may run directly without containers

**Production Mode**:
- Services run behind a Traefik reverse proxy
- HTTPS encryption is enforced with automatic certificate management
- Frontend is accessible at `dashboard.[your-domain]`
- Backend API is accessible at `api.[your-domain]`
- Database management interface is at `adminer.[your-domain]`
- HTTP requests automatically redirect to HTTPS
- Strict security validation prevents deployment with default passwords

## Service Dependencies

The system orchestrates multiple services with specific startup ordering:

1. **Database starts first** and must pass health checks
2. **Initialization service runs** to prepare the database schema
3. **Backend service starts** after initialization completes successfully
4. **Frontend service starts** independently and connects to the backend

If any service fails its health check or startup fails, dependent services won't start. This prevents the application from running in an inconsistent state where some parts are missing.

## API Versioning

All API endpoints are prefixed with `/api/v1/`, creating a versioning system that allows the backend to introduce new API versions without breaking existing frontend applications. This means future updates can add new endpoints at `/api/v2/` while maintaining backward compatibility.