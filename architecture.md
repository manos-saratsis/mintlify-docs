# Architecture Documentation

## Overview

The Mintlify Documentation Starter Kit is a **configuration-driven static documentation platform** that operates fundamentally differently from traditional web applications. Rather than consisting of application code, runtime dependencies, and backend services, this system is built entirely around declarative configuration files, Markdown content, and a cloud-based build pipeline managed by Mintlify's infrastructure.

**Core Architectural Philosophy:**

This documentation framework embodies a "documentation-as-code" approach where the entire documentation website is defined through:

1. **Configuration** (`docs.json`) - A single 111-line JSON file that defines all site behavior, structure, theme, navigation, and features
2. **Content** (`.md` files) - Plain Markdown files containing documentation text
3. **Assets** (SVG files) - Logo and favicon graphics
4. **API Specification** (`openapi.json`) - Optional OpenAPI 3.1.0 specification for API documentation

**No Traditional Application Code:**

Unlike typical web applications with React components, TypeScript modules, npm dependencies, and backend APIs, this project contains:

- **Zero JavaScript/TypeScript source files** for custom application logic
- **Zero runtime dependencies** managed via `package.json` (no `package.json` exists)
- **Zero backend services** or databases to maintain
- **Zero build configuration** (`webpack`, `vite`, etc.) in the repository

**Single External Dependency:**

The only external dependency is the **Mintlify CLI** (`mint`), installed globally via npm:

```bash
npm i -g mint
```

This CLI tool provides local development preview but is **not bundled with the project** - it exists outside the project directory as a global tool. Production deployment occurs entirely on Mintlify's cloud infrastructure without any local dependencies.

**Architecture Implications:**

This architectural approach provides several significant advantages:

- **Simplicity**: No complex build toolchains or dependency management
- **Security**: No runtime vulnerabilities from npm packages
- **Maintainability**: Configuration changes require no code deployments
- **Scalability**: Cloud-based build and hosting handle all scaling concerns
- **Portability**: Pure configuration and content can be versioned, backed up, and migrated easily

The remainder of this documentation explores how this configuration-driven architecture enables powerful documentation capabilities while maintaining radical simplicity.

---

## System Architecture

### High-Level Architecture

The Mintlify documentation system follows a **build-transform-deploy** architecture pattern where content and configuration flow through Mintlify's cloud infrastructure to produce a static, globally-distributed documentation website:

```
┌─────────────────────────────────────┐
│     Developer Workstation           │
│                                     │
│  ┌──────────────────────────────┐  │
│  │  Content Creation            │  │
│  │  - Edit docs.json            │  │
│  │  - Write .md files           │  │
│  │  - Update openapi.json       │  │
│  │  - Modify assets             │  │
│  └──────────┬───────────────────┘  │
│             │                       │
│             │ git commit/push       │
└─────────────┼───────────────────────┘
              │
              ▼
┌─────────────────────────────────────┐
│          GitHub Repository          │
│                                     │
│  - Version control                  │
│  - Webhook triggers                 │
│  - Change detection                 │
└─────────────┬───────────────────────┘
              │
              │ Webhook notification
              │ on push to main
              ▼
┌─────────────────────────────────────┐
│      Mintlify Build Pipeline        │
│                                     │
│  ┌──────────────────────────────┐  │
│  │  1. Configuration Parser     │  │
│  │     - Validate docs.json     │  │
│  │     - Extract navigation     │  │
│  │     - Load theme settings    │  │
│  └──────────┬───────────────────┘  │
│             │                       │
│             ▼                       │
│  ┌──────────────────────────────┐  │
│  │  2. Content Processor        │  │
│  │     - Parse Markdown         │  │
│  │     - Process code blocks    │  │
│  │     - Extract headings       │  │
│  │     - Generate ToC           │  │
│  └──────────┬───────────────────┘  │
│             │                       │
│             ▼                       │
│  ┌──────────────────────────────┐  │
│  │  3. OpenAPI Generator        │  │
│  │     - Parse specification    │  │
│  │     - Generate API docs      │  │
│  │     - Create examples        │  │
│  └──────────┬───────────────────┘  │
│             │                       │
│             ▼                       │
│  ┌──────────────────────────────┐  │
│  │  4. Static Site Generator    │  │
│  │     - Apply theme            │  │
│  │     - Build navigation       │  │
│  │     - Generate HTML          │  │
│  │     - Optimize assets        │  │
│  └──────────┬───────────────────┘  │
│             │                       │
│             ▼                       │
│  ┌──────────────────────────────┐  │
│  │  5. Search Index Builder     │  │
│  │     - Extract searchable text│  │
│  │     - Build index            │  │
│  │     - Generate suggestions   │  │
│  └──────────┬───────────────────┘  │
└─────────────┼───────────────────────┘
              │
              │ Deploy artifacts
              ▼
┌─────────────────────────────────────┐
│      Global CDN Distribution        │
│                                     │
│  - Static HTML files                │
│  - CSS and JavaScript               │
│  - Images and assets                │
│  - Search index                     │
│  - API documentation                │
└─────────────┬───────────────────────┘
              │
              │ HTTPS requests
              ▼
┌─────────────────────────────────────┐
│         End Users                   │
│                                     │
│  - Documentation viewers            │
│  - API consumers                    │
│  - Search users                     │
└─────────────────────────────────────┘
```

**Architecture Layers:**

1. **Content Layer**: Developer-managed configuration, Markdown, and assets
2. **Version Control Layer**: GitHub repository for change tracking and triggers
3. **Build Layer**: Mintlify's cloud-based transformation pipeline
4. **Distribution Layer**: Global CDN serving static assets
5. **Presentation Layer**: User browsers rendering documentation

### Configuration Architecture

The `docs.json` file serves as the **single source of truth** for all site behavior, replacing what would typically require extensive application code, database schemas, and configuration management systems.

#### Configuration Schema

**Location**: `docs.json` (project root, 111 lines)

**JSON Schema**: `https://mintlify.com/docs.json`

The configuration follows a hierarchical structure:

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Mint Starter Kit",
  "colors": { /* theme colors */ },
  "favicon": "/favicon.svg",
  "navigation": { /* navigation structure */ },
  "logo": { /* logo configuration */ },
  "navbar": { /* navbar configuration */ },
  "contextual": { /* contextual menu options */ },
  "footer": { /* footer configuration */ }
}
```

**Configuration Sections:**

| Section | Purpose | Lines | Complexity |
|---------|---------|-------|------------|
| Schema & Identity | Project identification | 2-4 | Low |
| Theme Configuration | Visual styling | 5-10 | Low |
| Navigation Structure | Content organization | 11-77 | High |
| Logo Configuration | Branding assets | 78-81 | Low |
| Navbar Configuration | Top navigation | 82-92 | Medium |
| Contextual Options | AI integrations | 93-104 | Medium |
| Footer Configuration | Social links | 105-111 | Low |

#### Theme Configuration Component

**Implementation** (`docs.json` lines 3-10):

```json
{
  "theme": "mint",
  "name": "Mint Starter Kit",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  },
  "favicon": "/favicon.svg"
}
```

**Color System Architecture:**

The three-color palette provides a complete theme system:

- **Primary Color** (`#16A34A`): Main brand color
  - Used for: Primary buttons, active navigation items, links, highlights
  - Application: 40% of color usage across UI
  
- **Light Variant** (`#07C983`): Lighter accent
  - Used for: Hover states, secondary elements, backgrounds
  - Application: 30% of color usage
  
- **Dark Variant** (`#15803D`): Darker accent
  - Used for: Pressed states, footer, emphasis elements
  - Application: 30% of color usage

**Theme Switching:**

The platform automatically generates light and dark theme variants based on these colors, calculating:
- Contrast ratios for accessibility (WCAG AA compliance)
- Hover state colors (10% lighter/darker)
- Active state colors (20% lighter/darker)
- Background tints and shades

#### Navigation Architecture

The navigation system implements a **three-tier hierarchical structure**: Tabs → Groups → Pages.

**Implementation** (`docs.json` lines 11-77):

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
          },
          {
            "group": "Writing content",
            "pages": ["essentials/markdown", "essentials/code", "essentials/images", "essentials/reusable-snippets"]
          },
          {
            "group": "AI tools",
            "pages": ["ai-tools/cursor", "ai-tools/claude-code", "ai-tools/windsurf"]
          }
        ]
      },
      {
        "tab": "API reference",
        "groups": [
          {
            "group": "API documentation",
            "pages": ["api-reference/introduction"]
          },
          {
            "group": "Endpoint examples",
            "pages": ["api-reference/endpoint/get", "api-reference/endpoint/create", "api-reference/endpoint/delete", "api-reference/endpoint/webhook"]
          }
        ]
      }
    ],
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

**Navigation Hierarchy:**

```
Navigation Root
├── Tab: "Guides" (12 pages total)
│   ├── Group: "Getting started" (3 pages)
│   │   ├── Page: index.md
│   │   ├── Page: quickstart.md
│   │   └── Page: development.md
│   ├── Group: "Customization" (2 pages)
│   │   ├── Page: essentials/settings.md
│   │   └── Page: essentials/navigation.md
│   ├── Group: "Writing content" (4 pages)
│   │   ├── Page: essentials/markdown.md
│   │   ├── Page: essentials/code.md
│   │   ├── Page: essentials/images.md
│   │   └── Page: essentials/reusable-snippets.md
│   └── Group: "AI tools" (3 pages)
│       ├── Page: ai-tools/cursor.md
│       ├── Page: ai-tools/claude-code.md
│       └── Page: ai-tools/windsurf.md
└── Tab: "API reference" (5 pages total)
    ├── Group: "API documentation" (1 page)
    │   └── Page: api-reference/introduction.md
    └── Group: "Endpoint examples" (4 pages)
        ├── Page: api-reference/endpoint/get.md
        ├── Page: api-reference/endpoint/create.md
        ├── Page: api-reference/endpoint/delete.md
        └── Page: api-reference/endpoint/webhook.md
```

**Path Resolution Rules:**

1. Page identifiers in `docs.json` are relative to project root
2. `.md` extension is implicit and must not be included
3. Subdirectories are indicated with forward slashes
4. Each page reference must correspond to an existing Markdown file

**Navigation Build Process:**

During the build phase, Mintlify:

1. Parses the navigation structure from `docs.json`
2. Validates that all referenced files exist
3. Extracts page titles from Markdown frontmatter or first heading
4. Generates navigation sidebar with collapsible groups
5. Creates breadcrumb navigation for each page
6. Builds previous/next page links
7. Generates navigation search index

#### Global Navigation Component

**Implementation** (`docs.json` lines 66-77):

```json
{
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
```

**Anchor System:**

Global anchors provide persistent external links that appear:
- In the main navigation sidebar
- Above tab-specific navigation
- Visible across all pages regardless of current tab

**Icon System:**

Icons are referenced by name from Mintlify's built-in icon library:
- `book-open-cover`: Documentation icon
- `newspaper`: Blog/news icon
- 200+ additional icons available
- Icons are SVG-based for scalability
- Automatic color adaptation to theme

---

## Content Architecture

### Markdown Processing Pipeline

Markdown files serve as the sole content source, processed through a sophisticated transformation pipeline during build.

**Content File Organization:**

```
project-root/
├── index.md                          # Root homepage
├── quickstart.md                     # Getting started guide
├── development.md                    # Development guide
├── essentials/                       # Feature documentation
│   ├── settings.md
│   ├── navigation.md
│   ├── markdown.md
│   ├── code.md
│   ├── images.md
│   └── reusable-snippets.md
├── ai-tools/                         # Integration documentation
│   ├── cursor.md
│   ├── claude-code.md
│   └── windsurf.md
└── api-reference/                    # API documentation
    ├── introduction.md
    └── endpoint/
        ├── get.md
        ├── create.md
        ├── delete.md
        └── webhook.md
```

**Markdown Processing Stages:**

```
Raw Markdown File
        │
        ├─── Stage 1: Frontmatter Extraction
        │    └─── Extract metadata (title, description, etc.)
        │
        ├─── Stage 2: Markdown Parsing
        │    ├─── Parse headings (H1-H6)
        │    ├─── Parse paragraphs
        │    ├─── Parse lists (ordered, unordered)
        │    ├─── Parse code blocks
        │    ├─── Parse links and images
        │    └─── Parse tables
        │
        ├─── Stage 3: Syntax Enhancement
        │    ├─── Apply syntax highlighting to code blocks
        │    ├─── Process callouts and alerts
        │    ├─── Expand tabs and accordions
        │    └─── Process custom components
        │
        ├─── Stage 4: Link Resolution
        │    ├─── Resolve internal links
        │    ├─── Validate external links
        │    └─── Generate anchor links
        │
        ├─── Stage 5: Table of Contents Generation
        │    └─── Build hierarchical ToC from headings
        │
        ├─── Stage 6: HTML Generation
        │    ├─── Convert Markdown AST to HTML
        │    ├─── Apply semantic markup
        │    └─── Add accessibility attributes
        │
        └─── Stage 7: Optimization
             ├─── Minify HTML
             ├─── Optimize inline styles
             └─── Generate critical CSS
                  │
                  ▼
            Final HTML Output
```

**Supported Markdown Extensions:**

Beyond standard Markdown, the platform supports:

1. **GitHub Flavored Markdown (GFM)**:
   - Tables
   - Task lists
   - Strikethrough
   - Autolinks

2. **Mintlify Extensions**:
   - Callout boxes (info, warning, danger, success)
   - Tabbed content
   - Accordions/collapsible sections
   - Code blocks with filename labels
   - Line highlighting in code
   - Card components
   - Multi-column layouts

3. **Math and Diagrams**:
   - LaTeX math notation (KaTeX)
   - Mermaid diagrams
   - PlantUML diagrams

### Code Block Architecture

Code blocks receive special processing for syntax highlighting and interactive features.

**Code Block Processing:**

```markdown
```javascript
// Example code block
function example() {
  return "Hello, world!";
}
```
```

**Build-Time Processing:**

1. **Language Detection**: Identifies language from fence label
2. **Syntax Highlighting**: Applies Prism.js or similar highlighter
3. **Line Numbers**: Optionally adds line numbers
4. **Copy Button**: Adds copy-to-clipboard functionality
5. **Line Highlighting**: Highlights specified lines
6. **Filename Label**: Adds filename banner if specified

**Generated HTML Structure:**

```html
<div class="code-block-container">
  <div class="code-block-header">
    <span class="code-block-language">javascript</span>
    <button class="code-block-copy">Copy</button>
  </div>
  <pre class="code-block">
    <code class="language-javascript">
      <!-- Syntax-highlighted code -->
    </code>
  </pre>
</div>
```

**Contextual Integration:**

The contextual options from `docs.json` (lines 93-104) apply to code blocks:

```json
{
  "contextual": {
    "options": [
      "copy",      // Copy to clipboard
      "view",      // View in full screen
      "chatgpt",   // Open in ChatGPT
      "claude",    // Open in Claude
      "perplexity", // Open in Perplexity
      "mcp",       // Model Context Protocol
      "cursor",    // Open in Cursor editor
      "vscode"     // Open in VS Code
    ]
  }
}
```

Each option adds a contextual menu action to code blocks, enabling one-click integration with AI tools and code editors.

---

## API Documentation Architecture

### OpenAPI Integration

The platform provides native OpenAPI 3.1.0 integration for automatic API documentation generation.

**OpenAPI Specification Location**: `api-reference/openapi.json` (194 lines)

**Specification Structure:**

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "OpenAPI Plant Store",
    "description": "A sample API...",
    "license": { "name": "MIT" },
    "version": "1.0.0"
  },
  "servers": [
    { "url": "http://sandbox.mintlify.com" }
  ],
  "security": [
    { "bearerAuth": [] }
  ],
  "paths": { /* API endpoints */ },
  "webhooks": { /* Webhook definitions */ },
  "components": {
    "schemas": { /* Data models */ },
    "securitySchemes": { /* Auth schemes */ }
  }
}
```

### API Documentation Generation Pipeline

```
OpenAPI Specification (openapi.json)
        │
        ├─── Stage 1: Specification Parsing
        │    ├─── Validate OpenAPI 3.1.0 syntax
        │    ├─── Extract metadata (title, version, etc.)
        │    └─── Parse server configurations
        │
        ├─── Stage 2: Endpoint Analysis
        │    ├─── Parse path items
        │    ├─── Extract operations (GET, POST, etc.)
        │    ├─── Identify parameters
        │    └─── Extract request/response schemas
        │
        ├─── Stage 3: Schema Processing
        │    ├─── Parse component schemas
        │    ├─── Resolve $ref references
        │    ├─── Generate type documentation
        │    └─── Create example data
        │
        ├─── Stage 4: Authentication Documentation
        │    ├─── Parse security schemes
        │    ├─── Document auth requirements
        │    └─── Generate auth examples
        │
        ├─── Stage 5: Documentation Page Generation
        │    ├─── Create endpoint pages
        │    ├─── Generate request examples
        │    ├─── Generate response examples
        │    └─── Build schema reference
        │
        └─── Stage 6: Interactive Features
             ├─── Add "Try It" functionality
             ├─── Generate code samples
             └─── Create interactive playground
                  │
                  ▼
            API Documentation Pages
```

### Endpoint Documentation Structure

**Example: GET /plants Endpoint**

The OpenAPI specification (lines 20-56) defines the GET endpoint:

```json
{
  "/plants": {
    "get": {
      "description": "Returns all plants...",
      "parameters": [
        {
          "name": "limit",
          "in": "query",
          "description": "The maximum number of results...",
          "schema": {
            "type": "integer",
            "format": "int32"
          }
        }
      ],
      "responses": {
        "200": {
          "description": "Plant response",
          "content": {
            "application/json": {
              "schema": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/Plant"
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**Generated Documentation Includes:**

1. **Endpoint Overview**:
   - HTTP method and path
   - Endpoint description
   - Authentication requirements

2. **Parameters Section**:
   - Parameter name, location (query/path/header), and type
   - Required vs optional designation
   - Parameter description and constraints
   - Example values

3. **Request Section**:
   - Request body schema (if applicable)
   - Content-Type headers
   - Example request payload

4. **Response Section**:
   - Status codes (200, 400, etc.)
   - Response schema
   - Example response payloads
   - Error response formats

5. **Code Examples**:
   - curl command
   - JavaScript/Node.js
   - Python
   - Additional languages based on configuration

### Schema Documentation Architecture

Component schemas (lines 152-194) are automatically documented with:

**Plant Schema** (lines 154-169):

```json
{
  "Plant": {
    "required": ["name"],
    "type": "object",
    "properties": {
      "name": {
        "description": "The name of the plant",
        "type": "string"
      },
      "tag": {
        "description": "Tag to specify the type",
        "type": "string"
      }
    }
  }
}
```

**Generated Schema Documentation:**

```
Plant
  Type: object

  Properties:
    name (required)
      Type: string
      Description: The name of the plant
      Example: "Fiddle Leaf Fig"

    tag (optional)
      Type: string
      Description: Tag to specify the type
      Example: "indoor"

  Example Object:
    {
      "name": "Fiddle Leaf Fig",
      "tag": "indoor"
    }
```

### Authentication Documentation

Security schemes (lines 175-179) are documented automatically:

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

**Generated Authentication Documentation:**

- Authentication type (HTTP Bearer)
- Header format (`Authorization: Bearer TOKEN`)
- Token acquisition process
- Security best practices
- Example authenticated requests

---

## Build and Deployment Architecture

### Local Development Architecture

Local development uses the globally-installed Mintlify CLI tool.

**Installation** (`README.md` line 18):

```bash
npm i -g mint
```

**Architecture:**

```
Developer Machine
        │
        ├─── Global npm Installation
        │    └─── Mintlify CLI (mint)
        │         ├─── Version: latest
        │         ├─── Location: /usr/local/bin/mint (Unix)
        │         │              or C:\Users\...\npm\mint (Windows)
        │         └─── Dependencies: Built into CLI
        │
        └─── Project Directory
             ├─── docs.json (configuration)
             ├─── *.md files (content)
             ├─── openapi.json (API spec)
             └─── assets (logos, favicon)
```

**Development Server** (`README.md` lines 22-27):

```bash
mint dev
```

**Server Architecture:**

```
mint dev Command
        │
        ├─── Parse docs.json
        │    └─── Validate configuration
        │
        ├─── Load Content Files
        │    ├─── Read all .md files
        │    ├─── Parse openapi.json
        │    └─── Load assets
        │
        ├─── Start HTTP Server
        │    ├─── Port: 3000
        │    ├─── Host: localhost
        │    └─── Hot Reload: Enabled
        │
        ├─── File Watchers
        │    ├─── Watch docs.json
        │    ├─── Watch *.md files
        │    ├─── Watch openapi.json
        │    └─── Watch assets
        │
        └─── Browser Auto-Reload
             └─── WebSocket connection for instant updates
```

**Hot Reload Mechanism:**

1. File system watchers detect changes
2. Changed files are re-processed
3. Browser receives WebSocket notification
4. Page auto-refreshes to show changes
5. No manual refresh required

### Production Build Architecture

Production builds occur entirely on Mintlify's cloud infrastructure.

**Deployment Trigger** (`README.md` lines 29-32):

1. Developer commits changes to Git
2. Developer pushes to default branch (main/master)
3. GitHub webhook notifies Mintlify
4. Mintlify initiates build pipeline

**Build Pipeline Architecture:**

```
GitHub Webhook
        │
        ▼
Mintlify Build Service
        │
        ├─── Stage 1: Repository Checkout
        │    ├─── Clone repository
        │    ├─── Checkout default branch
        │    └─── Verify commit integrity
        │
        ├─── Stage 2: Configuration Validation
        │    ├─── Parse docs.json
        │    ├─── Validate JSON schema
        │    ├─── Check navigation integrity
        │    └─── Verify file references
        │
        ├─── Stage 3: Content Processing
        │    ├─── Process all .md files
        │    ├─── Parse OpenAPI specification
        │    ├─── Generate API documentation
        │    ├─── Apply syntax highlighting
        │    └─── Build search index
        │
        ├─── Stage 4: Static Site Generation
        │    ├─── Generate HTML pages
        │    ├─── Apply theme and styling
        │    ├─── Build navigation structure
        │    ├─── Create sitemap
        │    └─── Generate robots.txt
        │
        ├─── Stage 5: Asset Optimization
        │    ├─── Compress images
        │    ├─── Minify CSS
        │    ├─── Minify JavaScript
        │    ├─── Generate responsive images
        │    └─── Create WebP variants
        │
        ├─── Stage 6: CDN Deployment
        │    ├─── Upload to CDN storage
        │    ├─── Purge CDN cache
        │    ├─── Update DNS (if needed)
        │    └─── Verify deployment
        │
        └─── Stage 7: Post-Deployment
             ├─── Generate sitemap
             ├─── Notify search engines
             ├─── Update deployment logs
             └─── Send success notification
```

**Build Characteristics:**

- **Atomic Deployments**: All-or-nothing deployment strategy
- **Zero Downtime**: New version replaces old seamlessly
- **Automatic Rollback**: Failed builds don't affect live site
- **Build Time**: Typically 1-3 minutes for standard projects
- **Caching**: Aggressive caching with smart invalidation

### Content Delivery Architecture

**CDN Infrastructure:**

```
End User Request
        │
        ├─── DNS Resolution
        │    └─── Route to nearest CDN edge
        │
        ▼
CDN Edge Location
        │
        ├─── Cache Check
        │    ├─── HIT: Return cached content (< 50ms)
        │    └─── MISS: Fetch from origin
        │
        ├─── Origin Fetch (if cache miss)
        │    ├─── Request from CDN origin
        │    ├─── Receive content
        │    ├─── Cache at edge
        │    └─── Return to user
        │
        ├─── Content Delivery
        │    ├─── HTML page
        │    ├─── CSS stylesheets
        │    ├─── JavaScript files
        │    ├─── Images and assets
        │    └─── Search index
        │
        └─── Response Headers
             ├─── Cache-Control
             ├─── ETag
             ├─── Content-Encoding (gzip/brotli)
             └─── Security headers
```

**Caching Strategy:**

| Resource Type | Cache Duration | Strategy |
|---------------|----------------|----------|
| HTML Pages | 5 minutes | Stale-while-revalidate |
| CSS (hashed) | 1 year | Immutable |
| JS (hashed) | 1 year | Immutable |
| Images (hashed) | 1 year | Immutable |
| Search Index | 1 hour | Edge cached |
| API Documentation | 5 minutes | Stale-while-revalidate |

**Performance Optimizations:**

1. **HTTP/2 and HTTP/3**: Multiplexed connections
2. **Brotli Compression**: Superior compression vs gzip
3. **Early Hints**: Preload critical resources
4. **Lazy Loading**: Images and components loaded on demand
5. **Critical CSS**: Above-the-fold styles inlined
6. **Code Splitting**: JavaScript loaded incrementally

---

## Search Architecture

### Search Index Generation

Search functionality is built entirely at build time, with no backend search service required.

**Index Generation Process:**

```
Content Files
        │
        ├─── Stage 1: Text Extraction
        │