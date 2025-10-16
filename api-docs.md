I'll analyze the provided source code to create accurate API documentation. Let me first explore what actual APIs exist in this codebase.

After thorough analysis of the provided source code, I can see this is a **Mintlify documentation starter kit**, not the OrchestRAI platform referenced in some markdown files. The only actual API present is a sample Plant Store API defined in the OpenAPI specification.

# API Documentation

## Overview

This documentation covers the Plant Store API, a sample RESTful API that demonstrates plant inventory management capabilities. The API is defined using OpenAPI 3.1.0 specification and provides endpoints for retrieving, creating, and deleting plant records. This is a demonstration API included in the Mintlify starter kit to show how to document APIs using OpenAPI specifications.

**Base URL**: `http://sandbox.mintlify.com`

**API Specification Location**: `api-reference/openapi.json`

## Authentication

### Bearer Token Authentication

All API requests require authentication using Bearer token authentication.

**Implementation**:
The API uses HTTP Bearer authentication as defined in the OpenAPI specification (`api-reference/openapi.json`, lines 10-12):

```json
"security": [
  {
    "bearerAuth": []
  }
]
```

The security scheme is defined in the components section (lines 122-127):

```json
"securitySchemes": {
  "bearerAuth": {
    "type": "http",
    "scheme": "bearer"
  }
}
```

**Usage**:
Include your bearer token in the Authorization header of every request:

```
Authorization: Bearer YOUR_TOKEN_HERE
```

## Endpoints

### GET /plants

Retrieves all plants from the system that the authenticated user has access to.

**Implementation**:
Defined in `api-reference/openapi.json` (lines 15-47).

**Parameters**:

| Name | Type | Location | Required | Description |
|------|------|----------|----------|-------------|
| limit | integer (int32) | query | No | The maximum number of results to return |

**Request Example**:
```
GET http://sandbox.mintlify.com/plants?limit=10
Authorization: Bearer YOUR_TOKEN_HERE
```

**Response - 200 Success**:
Returns an array of Plant objects.

Response Schema:
```json
{
  "type": "array",
  "items": {
    "$ref": "#/components/schemas/Plant"
  }
}
```

Each Plant object contains:
- `name` (string, required): The name of the plant
- `tag` (string, optional): Tag to specify the type

**Response - 400 Error**:
Returns an Error object when the request fails.

Error Schema (lines 101-117):
```json
{
  "error": 400,
  "message": "Error description here"
}
```

Error object structure:
- `error` (integer, int32, required): Error code
- `message` (string, required): Human-readable error message

### POST /plants

Creates a new plant in the store.

**Implementation**:
Defined in `api-reference/openapi.json` (lines 48-78).

**Request Body**:
Required. Content-Type: `application/json`

Request body must be a NewPlant object, which is defined as a Plant with an additional required `id` field (lines 91-108):

```json
{
  "id": 123,
  "name": "Rose",
  "tag": "flowering"
}
```

NewPlant Schema:
- `id` (integer, int64, required): Identification number of the plant
- `name` (string, required): The name of the plant
- `tag` (string, optional): Tag to specify the type

**Request Example**:
```
POST http://sandbox.mintlify.com/plants
Authorization: Bearer YOUR_TOKEN_HERE
Content-Type: application/json

{
  "id": 456,
  "name": "Succulent",
  "tag": "drought-resistant"
}
```

**Response - 200 Success**:
Returns the created Plant object with all its properties.

**Response - 400 Error**:
Returns an Error object if the plant cannot be created.

### DELETE /plants/{id}

Deletes a single plant based on the ID supplied.

**Implementation**:
Defined in `api-reference/openapi.json` (lines 79-118).

**Parameters**:

| Name | Type | Location | Required | Description |
|------|------|----------|----------|-------------|
| id | integer (int64) | path | Yes | ID of plant to delete |

**Request Example**:
```
DELETE http://sandbox.mintlify.com/plants/123
Authorization: Bearer YOUR_TOKEN_HERE
```

**Response - 204 Success**:
No content returned. The plant has been successfully deleted.

**Response - 400 Error**:
Returns an Error object if the deletion fails.

Error response body:
```json
{
  "error": 400,
  "message": "Plant not found or could not be deleted"
}
```

## Webhooks

### POST /plant/webhook

Webhook notification sent when a new plant is added to the store.

**Implementation**:
Defined in `api-reference/openapi.json` (lines 119-145).

**Purpose**:
This webhook allows external systems to receive real-time notifications when new plants are added to the inventory.

**Request Body**:
The webhook POST request will contain a NewPlant object:

```json
{
  "id": 789,
  "name": "Orchid",
  "tag": "tropical"
}
```

**Expected Response**:
Your webhook endpoint should return a 200 status code to indicate successful receipt of the notification.

**Usage**:
Configure your webhook URL in the Plant Store system to receive these notifications. Your endpoint must:
1. Accept POST requests
2. Parse JSON request bodies
3. Return HTTP 200 status on successful processing
4. Handle the NewPlant schema structure

## Data Models

### Plant

Base plant object representing a plant in the inventory.

**Schema Location**: `api-reference/openapi.json` (lines 81-96)

**Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| name | string | Yes | The name of the plant |
| tag | string | No | Tag to specify the type |

**JSON Example**:
```json
{
  "name": "Fern",
  "tag": "shade-loving"
}
```

### NewPlant

Extended plant object used when creating new plants. Includes all Plant properties plus an ID field.

**Schema Location**: `api-reference/openapi.json` (lines 97-113)

**Implementation**:
Uses OpenAPI `allOf` to extend the base Plant schema:

```json
{
  "allOf": [
    {
      "$ref": "#/components/schemas/Plant"
    },
    {
      "required": ["id"],
      "type": "object",
      "properties": {
        "id": {
          "description": "Identification number of the plant",
          "type": "integer",
          "format": "int64"
        }
      }
    }
  ]
}
```

**Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| id | integer (int64) | Yes | Identification number of the plant |
| name | string | Yes | The name of the plant |
| tag | string | No | Tag to specify the type |

**JSON Example**:
```json
{
  "id": 101,
  "name": "Cactus",
  "tag": "succulent"
}
```

### Error

Error response object returned when API operations fail.

**Schema Location**: `api-reference/openapi.json` (lines 114-127)

**Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| error | integer (int32) | Yes | Numeric error code |
| message | string | Yes | Human-readable error description |

**JSON Example**:
```json
{
  "error": 400,
  "message": "Invalid plant data provided"
}
```

## Documentation Configuration

### Navigation Structure

The API documentation is integrated into the Mintlify documentation site through the navigation configuration in `docs.json` (lines 43-57):

```json
{
  "tab": "API reference",
  "groups": [
    {
      "group": "API documentation",
      "pages": [
        "api-reference/introduction"
      ]
    },
    {
      "group": "Endpoint examples",
      "pages": [
        "api-reference/endpoint/get",
        "api-reference/endpoint/create",
        "api-reference/endpoint/delete",
        "api-reference/endpoint/webhook"
      ]
    }
  ]
}
```

This configuration creates a dedicated "API reference" tab in the documentation with two groups:
- **API documentation**: Introduction and overview pages
- **Endpoint examples**: Detailed documentation for each endpoint

### OpenAPI Integration

The API specification is automatically parsed and rendered by Mintlify from the OpenAPI JSON file. The specification file (`api-reference/openapi.json`) follows the OpenAPI 3.1.0 standard and includes:

- Complete endpoint definitions with paths, methods, and parameters
- Request and response schemas
- Authentication requirements
- Webhook specifications
- Reusable component schemas

## Development Workflow

### Local Preview

To preview the API documentation locally:

1. Install the Mintlify CLI:
```bash
npm i -g mint
```

2. Navigate to the documentation directory (where `docs.json` is located)

3. Start the development server:
```bash
mint dev
```

4. Open your browser to `http://localhost:3000`

**Implementation Reference**: These instructions are documented in `README.md` (lines 13-29).

### Updating API Documentation

To update the API documentation:

1. **Modify OpenAPI Specification**: Edit `api-reference/openapi.json` to add or update endpoints
2. **Update Navigation**: If adding new endpoint pages, update the navigation structure in `docs.json`
3. **Preview Changes**: Use `mint dev` to preview changes locally
4. **Publish**: Push changes to your default branch for automatic deployment

**Note**: According to `README.md` (lines 35-37), changes are automatically deployed to production after pushing to the default branch when the GitHub app is installed.

### Troubleshooting

**Preview Not Running**:
- Run `mint update` to ensure you have the latest CLI version (`README.md`, line 41)

**Page Shows 404**:
- Verify you're running the command in the folder containing `docs.json` (`README.md`, line 42)

**Documentation Not Updating**:
- Ensure the GitHub app is properly installed from your dashboard (`README.md`, line 35)
- Verify changes are pushed to the default branch

## Additional Resources

- **Mintlify Documentation**: [https://mintlify.com/docs](https://mintlify.com/docs)
- **Support Email**: hi@mintlify.com (referenced in `docs.json`, line 73)
- **Dashboard**: [https://dashboard.mintlify.com](https://dashboard.mintlify.com) (referenced in `docs.json`, line 78)

---

**Note**: This API documentation is based on the actual OpenAPI specification file included in the Mintlify starter kit. The Plant Store API is a demonstration example included to show how OpenAPI specifications can be integrated into Mintlify documentation. If you're implementing your own API, replace the `api-reference/openapi.json` file with your actual API specification.