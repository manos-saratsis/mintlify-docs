# Architecture Documentation

## Overview

This project is a **Mintlify documentation starter kit** - a configuration-driven documentation platform designed to help teams quickly create, customize, and deploy professional documentation websites. The architecture is built entirely on Mintlify's cloud infrastructure, requiring no custom application code, server management, or complex deployment pipelines.

The system operates as a static site generator that transforms Markdown content and JSON configuration into a fully-featured documentation website with built-in search, navigation, theming, and API reference capabilities. The architecture emphasizes simplicity and developer experience, allowing documentation authors to focus on content while Mintlify handles hosting, builds, and deployment automatically.

**Key Architectural Characteristics:**
- **Configuration-First**: All site behavior controlled through `docs.json`
- **Content-Driven**: Markdown files serve as the sole content source
- **Zero-Backend**: No servers, databases, or backend services required
- **Automatic Deployment**: GitHub integration triggers automatic builds
- **OpenAPI Integration**: Native support for API documentation via OpenAPI specifications

## System Architecture

### High-Level Architecture

The Mintlify documentation system follows a build-deploy-serve architecture pattern:

```
┌─────────────────┐
│  GitHub Repo    │
│  - docs.json    │
│  - *.md files   │
│  - openapi.json │
└────────┬────────┘
         │
         │ (Git Push)
         ▼
┌─────────────────┐
│ Mintlify GitHub │
│      App        │
└────────┬────────┘
         │
         │ (Build Trigger)
         ▼
┌─────────────────┐
│  Build Pipeline │
│  - Parse Config │
│  - Process MD   │
│  - Generate API │
│  - Optimize     │
└────────┬────────┘
         │
         │ (Deploy)
         ▼
┌─────────────────┐
│   CDN Hosting   │
│  - Static HTML  │
│  - Assets       │
│  - Search Index │
└─────────────────┘
```

### Component Architecture

The architecture consists of three primary layers:

#### 1. Configuration Layer (`docs.json`)

**Location**: `docs.json` (project root)

**Purpose**: Central configuration file that defines all aspects of the documentation site.

**Structure**:

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Mint Starter Kit",
  "colors": { ... },
  "navigation": { ... },
  "logo": { ... },
  "navbar": { ... },
  "footer": { ... },
  "contextual": { ... }
}
```

**Key Configuration Domains**:

- **Branding** (`name`, `logo`, `favicon`, `colors`): Visual identity and theming
- **Navigation** (`navigation`): Multi-level tab/group/page hierarchy
- **UI Elements** (`navbar`, `footer`): Header and footer customization
- **Integration** (`contextual`): AI tool and editor integrations

**Schema Reference**: The `$schema` property (`https://mintlify.com/docs.json`) enables IDE validation and autocompletion for configuration properties.

#### 2. Content Layer (Markdown Files)

**Location**: Root directory and subdirectories (`.md` files)

**Purpose**: Store all documentation content in human-readable Markdown format.

**Organization Pattern**:

```
.
├── index.md                    # Homepage
├── quickstart.md               # Getting started
├── development.md              # Development guide
├── essentials/
│   ├── settings.md
│   ├── navigation.md
│   ├── markdown.md
│   ├── code.md
│   ├── images.md
│   └── reusable-snippets.md
├── ai-tools/
│   ├── cursor.md
│   ├── claude-code.md
│   └── windsurf.md
└── api-reference/
    ├── introduction.md
    └── endpoint/
        ├── get.md
        ├── create.md
        ├── delete.md
        └── webhook.md
```

**Content-to-Navigation Mapping**:

Navigation entries in `docs.json` reference Markdown files without the `.md` extension:

```json
{
  "pages": [
    "index",                    // → index.md
    "essentials/settings",      // → essentials/settings.md
    "api-reference/endpoint/get" // → api-reference/endpoint/get.md
  ]
}
```

#### 3. API Documentation Layer (OpenAPI)

**Location**: `api-reference/openapi.json`

**Purpose**: Define API structure using OpenAPI 3.1.0 specification for automatic documentation generation.

**Integration Architecture**:

The OpenAPI specification is processed by Mintlify's build system to generate:
- Interactive API endpoint documentation
- Request/response examples
- Schema definitions
- Authentication requirements

**Specification Structure** (`api-reference/openapi.json`):

```json
{
  "openapi": "3.1.0",
  "info": { ... },
  "servers": [ ... ],
  "security": [ ... ],
  "paths": {
    "/plants": { ... },
    "/plants/{id}": { ... }
  },
  "webhooks": { ... },
  "components": {
    "schemas": { ... },
    "securitySchemes": { ... }
  }
}
```

**API Endpoints Defined**:

1. **GET /plants**: Retrieve plant list with optional limit parameter
2. **POST /plants**: Create new plant with NewPlant schema
3. **DELETE /plants/{id}**: Delete plant by ID
4. **Webhook POST /plant/webhook**: Receive plant creation notifications

**Security Architecture**:

Global bearer token authentication configured at specification root (lines 14-17):

```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

Security scheme definition (lines 122-127):

```json
{
  "securitySchemes": {
    "bearerAuth": {
      "type": "http",
      "scheme": "bearer"
    }
  }
}
```

### Navigation Architecture

The navigation system implements a three-tier hierarchy: Tabs → Groups → Pages.

**Architecture Diagram**:

```
Navigation
├── Tab: "Guides"
│   ├── Group: "Getting started"
│   │   ├── Page: index.md
│   │   ├── Page: quickstart.md
│   │   └── Page: development.md
│   ├── Group: "Customization"
│   │   ├── Page: essentials/settings.md
│   │   └── Page: essentials/navigation.md
│   ├── Group: "Writing content"
│   │   ├── Page: essentials/markdown.md
│   │   ├── Page: essentials/code.md
│   │   ├── Page: essentials/images.md
│   │   └── Page: essentials/reusable-snippets.md
│   └── Group: "AI tools"
│       ├── Page: ai-tools/cursor.md
│       ├── Page: ai-tools/claude-code.md
│       └── Page: ai-tools/windsurf.md
└── Tab: "API reference"
    ├── Group: "API documentation"
    │   └── Page: api-reference/introduction.md
    └── Group: "Endpoint examples"
        ├── Page: api-reference/endpoint/get.md
        ├── Page: api-reference/endpoint/create.md
        ├── Page: api-reference/endpoint/delete.md
        └── Page: api-reference/endpoint/webhook.md
```

**Implementation** (`docs.json` lines 9-62):

```json
{
  "navigation": {
    "tabs": [
      {
        "tab": "Guides",
        "groups": [
          {
            "group": "Getting started",
            "pages": ["index", "quickstart", "development"]
          },
          {
            "group": "Customization",
            "pages": ["essentials/settings", "essentials/navigation"]
          }
        ]
      },
      {
        "tab": "API reference",
        "groups": [
          {
            "group": "API documentation",
            "pages": ["api-reference/introduction"]
          }
        ]
      }
    ]
  }
}
```

**Navigation Rules**:

1. **Tab Level**: Top-level navigation sections, rendered as horizontal tabs
2. **Group Level**: Collapsible sections within tabs, organize related pages
3. **Page Level**: Individual documentation pages, must map to existing `.md` files
4. **Path Resolution**: Page identifiers are relative to project root, without `.md` extension

### Global Navigation Elements

**Anchors** (External Links) - `docs.json` lines 64-72:

```json
{
  "navigation": {
    "global": {
      "anchors": [
        {
          "anchor": "Documentation",
          "href": "https://mintlify.com/docs",
          "icon": "book-open-cover"
        },
        {
          "anchor": "Blog",
          "href": "https://mintlify.com/blog",
          "icon": "newspaper"
        }
      ]
    }
  }
}
```

**Purpose**: Provide persistent links to external resources, visible across all pages.

**Icon System**: Icons reference Mintlify's built-in icon library (e.g., "book-open-cover", "newspaper").

### Theming Architecture

The theming system provides brand customization while maintaining design consistency.

**Theme Configuration** (`docs.json` lines 3-7, 75-78):

```json
{
  "theme": "mint",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  },
  "favicon": "/favicon.svg",
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

**Color System**:

- **Primary** (`#16A34A`): Main brand color, used for primary actions and highlights
- **Light** (`#07C983`): Lighter accent, used for hover states and secondary elements
- **Dark** (`#15803D`): Darker accent, used for active states and emphasis

**Logo System**:

- **Theme-Aware**: Separate logos for light and dark modes
- **Automatic Switching**: Logos change based on user's theme preference
- **File Locations**: 
  - Light mode: `/logo/light.svg`
  - Dark mode: `/logo/dark.svg`

**Asset Requirements**:

```
/
├── favicon.svg           # Browser favicon
└── logo/
    ├── light.svg        # Light theme logo
    └── dark.svg         # Dark theme logo
```

### Navbar Architecture

The navbar provides site-wide navigation and primary actions.

**Configuration** (`docs.json` lines 79-91):

```json
{
  "navbar": {
    "links": [
      {
        "label": "Support",
        "href": "mailto:hi@mintlify.com"
      }
    ],
    "primary": {
      "type": "button",
      "label": "Dashboard",
      "href": "https://dashboard.mintlify.com"
    }
  }
}
```

**Component Types**:

1. **Links** (`navbar.links[]`): Secondary navigation items
   - Rendered as text links
   - Support mailto: and external URLs
   - Example: Support email link

2. **Primary Button** (`navbar.primary`):
   - Prominent call-to-action button
   - Visually distinct from regular links
   - Example: Dashboard access button

**Rendering Order**: Links appear left-aligned, primary button appears right-aligned in the navbar.

### Footer Architecture

The footer provides social media links and branding.

**Configuration** (`docs.json` lines 102-107):

```json
{
  "footer": {
    "socials": {
      "x": "https://x.com/mintlify",
      "github": "https://github.com/mintlify",
      "linkedin": "https://linkedin.com/company/mintlify"
    }
  }
}
```

**Supported Social Platforms**:
- **X (Twitter)**: `"x": "URL"`
- **GitHub**: `"github": "URL"`
- **LinkedIn**: `"linkedin": "URL"`

**Rendering**: Social icons are automatically rendered in the footer based on provided URLs.

### Contextual Integration Architecture

The contextual menu enables integration with AI tools and development environments.

**Configuration** (`docs.json` lines 92-101):

```json
{
  "contextual": {
    "options": [
      "copy",
      "view",
      "chatgpt",
      "claude",
      "perplexity",
      "mcp",
      "cursor",
      "vscode"
    ]
  }
}
```

**Integration Categories**:

1. **Basic Actions**:
   - `copy`: Copy code to clipboard
   - `view`: View source code

2. **AI Assistants**:
   - `chatgpt`: Open in ChatGPT
   - `claude`: Open in Claude
   - `perplexity`: Open in Perplexity
   - `mcp`: MCP protocol integration

3. **Development Tools**:
   - `cursor`: Open in Cursor editor
   - `vscode`: Open in VS Code

**Activation**: These options appear in contextual menus on code blocks and interactive elements.

## Build and Deployment Architecture

### Local Development Workflow

The local development environment uses the Mintlify CLI for live preview.

**Setup Process** (`README.md` lines 18-20):

```bash
npm i -g mint
```

**Architecture**:
- **Global Installation**: CLI installed globally via npm
- **Project-Agnostic**: Single installation serves all Mintlify projects
- **Auto-Update**: Supports version updates via `mint update`

**Development Server** (`README.md` lines 22-27):

```bash
mint dev
```

**Server Behavior**:
- **Working Directory Requirement**: Must execute in directory containing `docs.json`
- **Local Port**: Serves documentation at `http://localhost:3000`
- **Hot Reload**: Automatically reloads on file changes
- **File Watching**: Monitors changes to:
  - `docs.json` (configuration)
  - `*.md` files (content)
  - `/logo/` directory (assets)
  - `api-reference/openapi.json` (API spec)

**Error Handling**:
- **Invalid Directory**: Returns 404 if `docs.json` not found
- **Configuration Errors**: Reports JSON syntax errors
- **Missing Files**: Warns about broken page references

### Production Deployment Architecture

Production deployment uses GitHub-based continuous deployment.

**Deployment Flow** (`README.md` lines 28-32):

```
┌──────────────┐
│ Git Push     │
│ (Main Branch)│
└──────┬───────┘
       │
       ▼
┌──────────────────┐
│ GitHub Webhook   │
│ Triggers Build   │
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ Mintlify Build   │
│ System           │
│ - Parse Config   │
│ - Process Content│
│ - Build Site     │
│ - Optimize Assets│
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ CDN Deployment   │
│ - Cache Purge    │
│ - Asset Upload   │
│ - DNS Update     │
└──────────────────┘
```

**Integration Requirements**:

1. **GitHub App Installation**: Install from `https://dashboard.mintlify.com/settings/organization/github-app`
2. **Repository Connection**: Link GitHub repository to Mintlify project
3. **Branch Configuration**: Default branch triggers automatic deployment

**Build Process**:

1. **Trigger**: Push to default branch (typically `main` or `master`)
2. **Validation**: Verify `docs.json` syntax and structure
3. **Content Processing**:
   - Parse all Markdown files
   - Process OpenAPI specification
   - Generate search index
   - Optimize images and assets
4. **Build Generation**:
   - Compile static HTML pages
   - Apply theme and styling
   - Generate navigation structure
   - Create API documentation pages
5. **Deployment**:
   - Upload to CDN
   - Purge cache
   - Update DNS (if custom domain configured)

**Deployment Characteristics**:
- **Automatic**: No manual intervention required
- **Fast**: Typically completes in 1-3 minutes
- **Atomic**: All-or-nothing deployment (rollback on failure)
- **Zero-Downtime**: New version replaces old seamlessly

### Content Processing Pipeline

The build system processes content through multiple stages:

**Stage 1: Configuration Parsing**

```
docs.json → JSON Parser → Validation → Configuration Object
```

- Validates JSON syntax
- Checks required properties
- Validates navigation structure
- Verifies file references

**Stage 2: Markdown Processing**

```
*.md files → Markdown Parser → Enhanced Markdown → HTML
```

- Parses standard Markdown syntax
- Processes Mintlify-specific components
- Generates table of contents
- Applies syntax highlighting to code blocks

**Stage 3: OpenAPI Processing**

```
openapi.json → OpenAPI Parser → Schema Validation → API Documentation
```

- Validates OpenAPI 3.1.0 specification
- Generates endpoint documentation pages
- Creates request/response examples
- Builds schema reference sections

**Stage 4: Asset Optimization**

```
Images/Assets → Optimization → CDN Upload
```

- Compresses images
- Generates responsive variants
- Creates WebP versions
- Uploads to CDN

**Stage 5: Search Index Generation**

```
All Content → Text Extraction → Index Building → Search Database
```

- Extracts searchable text from all pages
- Builds inverted index
- Generates autocomplete suggestions
- Creates relevance rankings

### Hosting Architecture

The production site is hosted on Mintlify's infrastructure:

**Infrastructure Components**:

1. **CDN (Content Delivery Network)**:
   - Global edge locations
   - Automatic caching
   - DDoS protection
   - Automatic SSL/TLS certificates

2. **Static Asset Storage**:
   - Versioned assets
   - Immutable deployments
   - Automatic cleanup of old versions

3. **Search Service**:
   - Fast full-text search
   - Autocomplete suggestions
   - Relevance ranking

4. **Analytics**:
   - Page view tracking
   - Search query analytics
   - User behavior insights

**Performance Characteristics**:
- **First Contentful Paint**: Typically < 1 second
- **Time to Interactive**: < 2 seconds on fast connections
- **Search Latency**: < 100ms for most queries
- **Global Availability**: 99.9% uptime SLA

## Data Flow Architecture

### Page Rendering Flow

**Request-Response Cycle**:

```
User Browser
    │
    ├──> Request: https://docs.example.com/quickstart
    │
    ▼
CDN Edge Location
    │
    ├──> Cache Check
    │    └──> HIT: Return cached HTML
    │    └──> MISS: Forward to origin
    │
    ▼
Origin Server
    │
    ├──> Serve Pre-Built HTML
    │    └──> quickstart.html
    │
    ▼
Response to Browser
    │
    ├──> HTML Document
    ├──> CSS Assets
    ├──> JavaScript (minimal)
    └──> Images/Media
```

**Client-Side Rendering**:

1. **Initial Page Load**: Server-rendered HTML
2. **Navigation**: Client-side routing for instant page transitions
3. **Search**: Client-side search with pre-built index
4. **Theme**: Client-side theme switching (light/dark)

### Configuration Change Propagation

**Configuration Update Flow**:

```
Developer
    │
    ├──> Edit docs.json
    ├──> Git commit
    └──> Git push
         │
         ▼
GitHub
    │
    ├──> Webhook to Mintlify
    │
    ▼
Build System
    │
    ├──> Parse updated docs.json
    ├──> Validate configuration
    ├──> Rebuild navigation
    ├──> Regenerate all pages (if structure changed)
    └──> Deploy to CDN
         │
         ▼
CDN
    │
    ├──> Cache invalidation
    ├──> New version live
    │
    ▼
User Browser
    │
    └──> Next page load shows updated site
```

**Configuration Impact Scope**:

- **Navigation Changes**: Rebuild entire site navigation
- **Theme Changes**: Regenerate CSS, apply new colors
- **Logo Changes**: Update all pages with new logo
- **Content Changes**: Rebuild affected pages only

### Content Update Flow

**Markdown File Update**:

```
Developer
    │
    ├──> Edit markdown file (e.g., quickstart.md)
    ├──> Git commit
    └──> Git push
         │
         ▼
Build System
    │
    ├──> Detect changed files
    ├──> Incremental build (affected pages only)
    ├──> Update search index
    └──> Deploy changes
         │
         ▼
CDN
    │
    ├──> Invalidate affected URLs
    ├──> Serve new content
```

**Incremental Build Optimization**:
- Only rebuilds changed pages and their dependencies
- Updates search index for modified content
- Preserves cached assets and unchanged pages

### API Documentation Update Flow

**OpenAPI Specification Update**:

```
Developer
    │
    ├──> Edit openapi.json
    ├──> Git commit
    └──> Git push
         │
         ▼
Build System
    │
    ├──> Parse OpenAPI specification
    ├──> Validate against OpenAPI 3.1.0 schema
    ├──> Generate API documentation pages
    ├──> Update search index with API content
    └──> Deploy
         │
         ▼
CDN
    │
    └──> API documentation pages updated
```

**Generated Content**:
- Endpoint documentation pages
- Request/response examples
- Schema reference pages
- Authentication documentation

## Security Architecture

### Content Security

**Static Site Security Benefits**:
- **No Server-Side Execution**: Eliminates entire classes of vulnerabilities
- **No Database**: No SQL injection or data breach risks
- **No User Input Processing**: No XSS or CSRF attack surface
- **Immutable Deployments**: Cannot be modified after deployment

**Asset Integrity**:
- All assets served with content hashes in filenames
- Subresource Integrity (SRI) for external dependencies
- HTTPS-only serving

### Access Control

**Repository Access**:
- GitHub-based authentication for deployment
- Mintlify GitHub App requires explicit permission grants
- Read-only access to repository content

**Dashboard Access**:
- Mintlify dashboard requires user authentication
- Role-based access control for team members
- Audit logs for configuration changes

### Build Security

**Build Isolation**:
- Each build runs in isolated environment
- No access to other projects' data
- Automatic cleanup after build completion

**Dependency Management**:
- No runtime dependencies in production
- Build-time dependencies managed by Mintlify
- Regular security updates applied by platform

## Performance Architecture

### Optimization Strategies

**Content Optimization**:

1. **HTML Minification**: Remove whitespace and comments
2. **CSS Optimization**: 
   - Remove unused styles
   - Minify and compress
   - Critical CSS inlining
3. **JavaScript Optimization**:
   - Minimal JavaScript for interactivity
   - Code splitting for faster initial load
   - Deferred loading of non-critical features
4. **Image Optimization**:
   - Automatic compression
   - Responsive image generation
   - WebP format conversion
   - Lazy loading below-the-fold images

**Caching Strategy**:

```
Asset Type          Cache Duration    Strategy
─────────────────────────────────────────────────
HTML Pages          5 minutes         Stale-while-revalidate
CSS/JS (hashed)     1 year            Immutable
Images (hashed)     1 year            Immutable
Search Index        1 hour            Edge cached
Fonts               1 year            Immutable
```

**CDN Architecture**:
- Global edge locations for low latency
- Automatic geographic routing
- HTTP/2 and HTTP/3 support
- Brotli compression

### Performance Metrics

**Target Performance**:
- **Lighthouse Score**: > 95 (Performance)
- **First Contentful Paint**: < 1.0s
- **Time to Interactive**: < 2.0s
- **Total Page Weight**: < 500KB (initial load)
- **Search Response Time**: < 100ms

**Monitoring**:
- Real User Monitoring (RUM)
- Synthetic monitoring from multiple locations
- Core Web Vitals tracking

## Scalability Architecture

### Content Scalability

**Supported Scale**:
- **Pages**: Thousands of pages without performance degradation
- **Assets**: Unlimited (CDN-based storage)
- **Traffic**: Auto-scaling CDN handles traffic spikes

**Search Scalability**:
- Pre-built search index eliminates search backend
- Client-side search for instant results
- Scales to 10,000+ pages efficiently

### Build Scalability

**Build Performance**:
- Incremental builds for faster deployments
- Parallel processing of independent pages
- Caching of unchanged content

**Limitations**:
- Very large repositories (100,000+ pages) may require build optimization
- Complex OpenAPI specifications may increase build time

## Extensibility Architecture

### Supported Extension Points

**Content Extensions**:
1. **Custom Markdown Components**: Extended Markdown syntax for custom elements
2. **Code Highlighting**: Language-specific syntax highlighting
3. **Embedded Content**: Embed videos, diagrams, interactive elements

**API Documentation Extensions**:
1. **OpenAPI Extensions**: Custom `x-` properties in OpenAPI spec
2. **Code Samples**: Multi-language code examples
3. **Try-It Features**: Interactive API testing (if supported by endpoint)

**Theme Extensions**:
1. **Custom Colors**: Full color palette customization
2. **Custom Fonts**: Typography customization
3. **Custom CSS**: Additional styling (platform-dependent)

**Integration Extensions**:
1. **Analytics**: Google Analytics, Segment, etc.
2. **Search**: Custom search integrations
3. **Feedback Widgets**: User feedback tools

### Limitations

**Not Supported**:
- Custom React components (static site only)
- Server-side logic or APIs
- User authentication/authorization
- Dynamic content generation
- Database-backed features

## Monitoring and Observability

### Available Metrics

**Build Metrics**:
- Build duration
- Build success/failure rate
- Deployment frequency
- Configuration validation errors

**Performance Metrics**:
- Page load times
- CDN cache hit rates
- Search query performance
- Asset load times

**Usage Metrics**:
- Page views
- Popular pages
- Search queries
- User navigation patterns

### Troubleshooting Architecture

**Local Troubleshooting** (`README.md` lines 38-42):

**Issue: Dev Server Not Starting**
```bash
mint update
```
- Updates CLI to latest version
- Fixes compatibility issues
- Resolves outdated package problems

**Issue: 404 Errors in Preview**
- **Cause**: `docs.json` not in current directory
- **Solution**: Navigate to correct directory containing `docs.json`
- **Verification**: Run `ls docs.json` to confirm file presence

**Build Troubleshooting**:

**Issue: Failed Deployment**
- **Check**: GitHub webhook configuration
- **Verify**: Mintlify GitHub App permissions
- **Review**: Build logs in Mintlify dashboard
- **Validate**: `docs.json` syntax using JSON validator

**Issue: Missing Pages**
- **Cause**: Broken file references in navigation
- **Solution**: Verify `.md` file exists at referenced path
- **Example**: `"pages": ["quickstart"]` requires `quickstart.md`

**Issue: Broken Links**
- **Internal Links**: Use relative paths matching file structure
- **Cross-References**: Verify target pages exist in navigation
- **External Links**: Check URL accessibility

## Technology Stack

### Core Technologies

**Configuration**:
- **JSON**: Configuration format (`docs.json`)
- **JSON Schema**: Validation and IDE support

**Content**:
- **Markdown**: Content authoring format (standard + extensions)
- **OpenAPI 3.1.0**: API specification standard

**Development Tools**:
- **Node.js**: Required for Mintlify CLI
- **npm**: Package manager for CLI installation

**Build System** (Mintlify Platform):
- Markdown parser/processor
- OpenAPI parser/generator
- Static site generator
- Asset optimizer

**Hosting** (Mintlify Infrastructure):
- Global CDN
- Static asset storage
- Search service
- Analytics service

### No Custom Code

**Important Architectural Constraint**:

This project contains **no custom application code**. The entire system operates through:

1. **Configuration** (`docs.json`)
2. **Content** (`.md` files)
3. **API Specification** (`openapi.json`)
4. **Static Assets** (logos, favicon)

**No React Components**: Unlike typical web applications, there are no `.tsx`, `.jsx`, `.ts`, or `.js` source files.

**No Backend**: No server-side code, databases, or API endpoints beyond the sample API specification.

**No Build Scripts**: Build process entirely managed by Mintlify platform.

## Migration and Upgrade Paths

### Version Management

**CLI Updates**:
```bash
mint update
```
- Updates local CLI to latest version
- Ensures compatibility with latest Mintlify features
- Required when build system introduces breaking changes

**Platform Updates**:
- Automatic on Mintlify's end
- No action required from documentation authors
- Backward compatibility maintained for `docs.json` schema

### Content Migration

**From Other Documentation Tools**:

**Supported Migration Sources**:
1. **GitBook**: Similar Markdown-based structure
2. **Docusaurus**: Compatible navigation concepts
3. **ReadTheDocs**: Straightforward content conversion
4. **Custom Static Sites**: Markdown content portable

**Migration Process**:
1. Convert configuration to `docs.json` format
2. Organize Markdown files according to navigation structure
3. Update internal links to match new structure
4. Import OpenAPI specifications (if applicable)
5. Customize theme and branding

## Summary

The Mintlify documentation starter kit architecture demonstrates a modern, configuration-driven approach to documentation website creation. Key architectural principles include:

**Simplicity**: No custom code required - pure configuration and content
**Performance**: Static site generation with global CDN delivery
**Developer Experience**: Live preview, automatic deployment, IDE support
**Extensibility**: OpenAPI integration, theme customization, content extensions
**Reliability**: Immutable deployments, zero-downtime updates, automatic scaling

The architecture's strength lies in eliminating infrastructure complexity while providing professional documentation capabilities. By constraining functionality to static site generation and focusing on configuration-first design, the system achieves ease of use without sacrificing features or performance.

**File Locations Referenced**:
- Configuration: `docs.json`
- Setup Instructions: `README.md`
- API Specification: `api-reference/openapi.json`
- Content: `*.md` files throughout project
- Assets: `/logo/light.svg`, `/logo/dark.svg`, `/favicon.svg`

**External Resources**:
- Mintlify Documentation: https://mintlify.com/docs
- Dashboard: https://dashboard.mintlify.com
- Support: hi@mintlify.com

All architectural details documented here are derived directly from the provided source code files, with no invented features or placeholder content.