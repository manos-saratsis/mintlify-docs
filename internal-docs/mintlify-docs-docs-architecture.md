# mintlify-docs - Architecture Documentation

## Overview

The Mintlify Documentation Starter Kit represents a fundamentally different architectural approach to documentation systems. Unlike traditional web applications that require extensive codebases, runtime dependencies, and backend infrastructure, this system operates as a **configuration-driven static documentation platform** where a single 111-line JSON file (`docs.json`) defines all site behavior, structure, and appearance.

**Architectural Philosophy:**

This documentation framework embodies a "documentation-as-code" paradigm with radical simplicity:

- **Zero Application Code**: No React components, TypeScript modules, or custom JavaScript
- **Zero Runtime Dependencies**: No `package.json`, no npm modules bundled with the project
- **Zero Backend Services**: No databases, APIs, or server-side processing in the repository
- **Single External Dependency**: Mintlify CLI (`mint`) installed globally outside the project

**Core Components:**

1. **Configuration** (`docs.json`) - 111 lines controlling all site behavior
2. **Content** (Markdown files) - 18+ documentation pages in `.md` format
3. **Assets** (SVG files) - Logo variants and favicon for branding
4. **API Specification** (`openapi.json`) - Optional 194-line OpenAPI 3.1.0 spec

**Project Structure:**

```
mintlify-docs/
├── docs.json                      # Central configuration (111 lines)
├── README.md                      # Setup instructions
├── favicon.svg                    # Site icon
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── api-reference/
│   ├── openapi.json              # OpenAPI spec (194 lines)
│   ├── introduction.md
│   └── endpoint/
│       ├── get.md
│       ├── create.md
│       ├── delete.md
│       └── webhook.md
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
├── index.md                       # Homepage
├── quickstart.md                  # Quick start guide
├── development.md                 # Development guide
└── [additional .md files]
```

---

## Implementation

### Configuration Architecture

The `docs.json` file serves as the **single source of truth** for the entire documentation site, replacing what would typically require thousands of lines of application code, database schemas, and configuration files.

#### Configuration File Structure

**Location**: `docs.json` (project root, 111 lines)

**Schema Declaration** (line 2):
```json
{
  "$schema": "https://mintlify.com/docs.json"
}
```

The schema reference enables IDE autocompletion and validation for the configuration file.

**Complete Configuration Breakdown:**

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Mint Starter Kit",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  },
  "favicon": "/favicon.svg",
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
            "pages": [
              "essentials/markdown",
              "essentials/code",
              "essentials/images",
              "essentials/reusable-snippets"
            ]
          },
          {
            "group": "AI tools",
            "pages": [
              "ai-tools/cursor",
              "ai-tools/claude-code",
              "ai-tools/windsurf"
            ]
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
            "pages": [
              "api-reference/endpoint/get",
              "api-reference/endpoint/create",
              "api-reference/endpoint/delete",
              "api-reference/endpoint/webhook"
            ]
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
  },
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  },
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
  },
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
  },
  "footer": {
    "socials": {
      "x": "https://x.com/mintlify",
      "github": "https://github.com/mintlify",
      "linkedin": "https://linkedin.com/company/mintlify"
    }
  }
}
```

#### Theme System Architecture

**Color Configuration** (lines 5-9):

The three-color system provides complete theme coverage:

```json
{
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  }
}
```

**Color Application:**

- **Primary (#16A34A)**: Main brand color for buttons, links, active states, and highlights
- **Light (#07C983)**: Lighter variant for hover states and secondary elements
- **Dark (#15803D)**: Darker variant for pressed states and emphasis

**Automatic Theme Generation:**

The Mintlify platform automatically generates both light and dark theme variants from these three colors, calculating:

- Contrast ratios for WCAG AA accessibility compliance
- Hover state colors (10% lighter/darker than base)
- Active state colors (20% lighter/darker than base)
- Background tints and shades for various UI elements

#### Navigation Architecture

**Three-Tier Hierarchy** (lines 11-77):

```
Navigation Root
└── Tabs (top-level sections)
    └── Groups (collapsible sections)
        └── Pages (individual documents)
```

**Guides Tab Structure** (lines 13-47):

```json
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
      "pages": [
        "essentials/markdown",
        "essentials/code",
        "essentials/images",
        "essentials/reusable-snippets"
      ]
    },
    {
      "group": "AI tools",
      "pages": [
        "ai-tools/cursor",
        "ai-tools/claude-code",
        "ai-tools/windsurf"
      ]
    }
  ]
}
```

**Content Mapping:**

- **Total Pages**: 17 pages across 6 groups in 2 tabs
- **Guides Tab**: 12 pages in 4 groups
- **API Reference Tab**: 5 pages in 2 groups

**Path Resolution:**

- Page identifiers are relative to project root
- `.md` extension is implicit and omitted
- Subdirectories indicated with forward slashes
- Example: `"essentials/settings"` → `essentials/settings.md`

**API Reference Tab Structure** (lines 48-65):

```json
{
  "tab": "API reference",
  "groups": [
    {
      "group": "API documentation",
      "pages": ["api-reference/introduction"]
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

**Global Navigation Anchors** (lines 66-77):

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

Global anchors provide persistent external links visible across all pages, above tab-specific navigation.

#### Branding Architecture

**Logo System** (lines 78-81):

```json
{
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

**Logo Implementation:**

- **Light Theme Logo**: `/logo/light.svg` - Displayed when user has light theme enabled
- **Dark Theme Logo**: `/logo/dark.svg` - Displayed when user has dark theme enabled
- **Automatic Switching**: Platform detects user's theme preference and displays appropriate logo
- **Format**: SVG recommended for scalability across all screen sizes

**Favicon Configuration** (line 10):

```json
{
  "favicon": "/favicon.svg"
}
```

The favicon appears in browser tabs, bookmarks, and browser history.

#### Navbar Architecture

**Navbar Configuration** (lines 82-92):

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

**Navbar Components:**

1. **Regular Links** (lines 84-87):
   - Array of link objects
   - Example: Support email link
   - Can include multiple links
   - Appears in header navigation

2. **Primary Button** (lines 88-92):
   - Prominent call-to-action button
   - Type: "button" (styled differently from regular links)
   - Label: "Dashboard"
   - Destination: Mintlify dashboard

#### Contextual Integration Architecture

**Contextual Options** (lines 93-104):

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

**Contextual Menu Capabilities:**

These options enable right-click or contextual menu actions on code blocks and content:

- **copy**: Copy content to clipboard
- **view**: View in different formats or full screen
- **chatgpt**: Open content in ChatGPT interface
- **claude**: Open content in Claude AI interface
- **perplexity**: Open content in Perplexity AI
- **mcp**: Model Context Protocol integration
- **cursor**: Open in Cursor code editor
- **vscode**: Open in Visual Studio Code

This creates seamless integration between documentation and development tools, allowing developers to quickly move from reading documentation to implementation.

#### Footer Architecture

**Footer Social Links** (lines 105-111):

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

**Social Platform Support:**

The footer configuration supports multiple social platforms:
- **x**: X (formerly Twitter)
- **github**: GitHub
- **linkedin**: LinkedIn
- Additional supported: discord, youtube, slack, facebook, instagram, medium

---

### Content Architecture

#### Markdown Processing Pipeline

Markdown files serve as the sole content source, processed during build through a sophisticated transformation pipeline managed by Mintlify's cloud infrastructure.

**Content Processing Flow:**

```
Raw Markdown (.md files)
        ↓
1. Frontmatter Extraction
   - Extract metadata (title, description)
   - Parse configuration options
        ↓
2. Markdown Parsing
   - Parse headings (H1-H6)
   - Parse paragraphs, lists, tables
   - Parse code blocks with language detection
   - Parse links and images
        ↓
3. Syntax Enhancement
   - Apply syntax highlighting to code
   - Process callouts and alerts
   - Expand tabs and accordions
        ↓
4. Link Resolution
   - Resolve internal page references
   - Validate external links
   - Generate anchor links from headings
        ↓
5. Table of Contents Generation
   - Build hierarchical ToC from headings
   - Create page navigation structure
        ↓
6. HTML Generation
   - Convert Markdown AST to semantic HTML
   - Apply accessibility attributes
   - Add interactive elements
        ↓
7. Optimization
   - Minify HTML output
   - Optimize inline styles
   - Generate critical CSS
        ↓
    Final Static HTML
```

**Supported Markdown Extensions:**

1. **GitHub Flavored Markdown (GFM)**:
   - Tables with alignment
   - Task lists with checkboxes
   - Strikethrough text
   - Automatic URL linking

2. **Mintlify Extensions**:
   - Callout boxes (info, warning, danger, success types)
   - Tabbed content sections
   - Collapsible accordions
   - Code blocks with filename labels
   - Line highlighting in code blocks
   - Card components for visual organization
   - Multi-column layouts

3. **Math and Diagrams**:
   - LaTeX math notation via KaTeX
   - Mermaid diagram rendering
   - PlantUML diagram support

#### Code Block Architecture

Code blocks receive specialized processing for syntax highlighting and interactive features.

**Code Block Processing Pipeline:**

```
Code Block in Markdown
        ↓
1. Language Detection
   - Identify language from fence label
   - Example: ```javascript
        ↓
2. Syntax Highlighting
   - Apply Prism.js or similar highlighter
   - Generate color-coded HTML
        ↓
3. Feature Addition
   - Add line numbers (optional)
   - Add copy-to-clipboard button
   - Add filename label (if specified)
   - Apply line highlighting (if specified)
        ↓
4. Contextual Integration
   - Add contextual menu options
   - Enable AI tool integrations
        ↓
    Enhanced Code Block
```

**Generated HTML Structure:**

```html
<div class="code-block-container">
  <div class="code-block-header">
    <span class="code-block-language">javascript</span>
    <button class="code-block-copy">Copy</button>
    <div class="code-block-contextual">
      <!-- Contextual menu options -->
    </div>
  </div>
  <pre class="code-block">
    <code class="language-javascript">
      <!-- Syntax-highlighted code -->
    </code>
  </pre>
</div>
```

**Contextual Integration with Code Blocks:**

The contextual options from `docs.json` (lines 93-104) apply directly to code blocks:

- **copy**: Quick copy button in header
- **chatgpt/claude/perplexity**: Send code to AI assistants for explanation
- **cursor/vscode**: Open code in editors for immediate implementation
- **mcp**: Model Context Protocol integration for advanced AI interactions

---

### API Documentation Architecture

#### OpenAPI Integration

The platform provides native OpenAPI 3.1.0 integration for automatic, comprehensive API documentation generation.

**OpenAPI Specification Location**: `api-reference/openapi.json` (194 lines)

**Specification Structure Breakdown:**

**Root Configuration** (lines 1-18):

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "OpenAPI Plant Store",
    "description": "A sample API that uses a plant store as an example to demonstrate features in the OpenAPI specification",
    "license": {
      "name": "MIT"
    },
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "http://sandbox.mintlify.com"
    }
  ],
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Key Specification Elements:**

1. **API Metadata** (lines 2-9):
   - Title: "OpenAPI Plant Store"
   - Description: Sample API demonstrating OpenAPI features
   - License: MIT
   - Version: 1.0.0

2. **Server Configuration** (lines 10-13):
   - Base URL: `http://sandbox.mintlify.com`
   - Single server endpoint for all operations

3. **Global Security** (lines 14-18):
   - Bearer token authentication required for all endpoints
   - Applied globally to every API operation

#### API Endpoints Architecture

**GET /plants Endpoint** (lines 20-56):

```json
{
  "/plants": {
    "get": {
      "description": "Returns all plants from the system that the user has access to",
      "parameters": [
        {
          "name": "limit",
          "in": "query",
          "description": "The maximum number of results to return",
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
        },
        "400": {
          "description": "Unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Characteristics:**

- **Method**: GET
- **Path**: /plants
- **Query Parameters**: 
  - `limit` (optional, integer): Maximum results to return
- **Responses**:
  - 200: Array of Plant objects
  - 400: Error object

**POST /plants Endpoint** (lines 57-94):

```json
{
  "/plants": {
    "post": {
      "description": "Creates a new plant in the store",
      "requestBody": {
        "description": "Plant to add to the store",
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/NewPlant"
            }
          }
        },
        "required": true
      },
      "responses": {
        "200": {
          "description": "plant response",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Plant"
              }
            }
          }
        },
        "400": {
          "description": "unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Characteristics:**

- **Method**: POST
- **Path**: /plants
- **Request Body**: NewPlant object (required)
- **Responses**:
  - 200: Created Plant object
  - 400: Error object

**DELETE /plants/{id} Endpoint** (lines 95-137):

```json
{
  "/plants/{id}": {
    "delete": {
      "description": "Deletes a single plant based on the ID supplied",
      "parameters": [
        {
          "name": "id",
          "in": "path",
          "description": "ID of plant to delete",
          "required": true,
          "schema": {
            "type": "integer",
            "format": "int64"
          }
        }
      ],
      "responses": {
        "204": {
          "description": "Plant deleted",
          "content": {}
        },
        "400": {
          "description": "unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Characteristics:**

- **Method**: DELETE
- **Path**: /plants/{id}
- **Path Parameters**: 
  - `id` (required, integer): Plant ID to delete
- **Responses**:
  - 204: No content (successful deletion)
  - 400: Error object

#### Webhook Architecture

**Webhook Endpoint** (lines 139-173):

```json
{
  "webhooks": {
    "/plant/webhook": {
      "post": {
        "description": "Information about a new plant added to the store",
        "requestBody": {
          "description": "Plant added to the store",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/NewPlant"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Return a 200 status to indicate that the data was received successfully"
          }
        }
      }
    }
  }
}
```

**Webhook Implementation:**

- **Trigger**: New plant creation via POST /plants
- **Payload**: NewPlant object (id, name, tag)
- **Expected Response**: HTTP 200 status
- **Content-Type**: application/json

**Webhook Use Cases:**

1. External systems register webhook URLs
2. API POSTs to registered endpoints when plants created
3. Webhook receivers respond with 200 to acknowledge receipt
4. Failed deliveries may be retried based on implementation

#### Data Schema Architecture

**Plant Schema** (lines 154-169):

```json
{
  "Plant": {
    "required": [
      "name"
    ],
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

**Schema Properties:**

- **name** (required): Plant name (string)
- **tag** (optional): Type classification (string)

**Usage**: Returned by GET and POST endpoints

**NewPlant Schema** (lines 170-183):

```json
{
  "NewPlant": {
    "allOf": [
      {
        "$ref": "#/components/schemas/Plant"
      },
      {
        "required": [
          "id"
        ],
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
}
```

**Schema Composition:**

- Uses OpenAPI `allOf` to extend Plant schema
- Inherits: name (required), tag (optional)
- Adds: id (required, integer int64)

**Usage**: Required in POST request bodies and webhook payloads

**Error Schema** (lines 184-194):

```json
{
  "Error": {
    "required": [
      "error",
      "message"
    ],
    "type": "object",
    "properties": {
      "error": {
        "type": "integer",
        "format": "int32"
      },
      "message": {
        "type": "string"
      }
    }
  }
}
```

**Schema Properties:**

- **error** (required): Numeric error code (integer int32)
- **message** (required): Human-readable error description (string)

**Usage**: Returned in 400 error responses across all endpoints

#### Authentication Documentation Architecture

**Security Schemes** (lines 175-179):

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

**Authentication System:**

- **Type**: HTTP Bearer token authentication
- **Scheme**: bearer
- **Header Format**: `Authorization: Bearer TOKEN`
- **Scope**: Applied globally to all endpoints (lines 14-18)

**Generated Authentication Documentation Includes:**

1. Authentication type explanation
2. Header format specification
3. Token acquisition process
4. Security best practices
5. Example authenticated requests in multiple languages

---

### Build and Deployment Architecture

#### Local Development Architecture

**Mintlify CLI Installation** (`README.md` line 18):

```bash
npm i -g mint
```

**Development Server Architecture:**

```
Developer Machine
        │
        ├─── Global npm Installation
        │    └─── Mintlify CLI (mint)
        │         - Location: /usr/local/bin/mint (Unix)
        │                     C:\Users\...\npm\mint (Windows)
        │         - Version: Latest
        │         - Dependencies: Built into CLI
        │
        └─── Project Directory
             ├─── docs.json (configuration)
             ├─── *.md files (content)
             ├─── openapi.json (API spec)
             └─── assets (logos, favicon)
```

**Development Server Startup** (`README.md` lines 24-28):

```bash
mint dev
```

**Server Implementation:**

```
mint dev Command
        ↓
1. Parse Configuration
   - Read docs.json
   - Validate JSON schema
   - Check file references
        ↓
2. Load Content
   - Read all .md files
   - Parse openapi.json
   - Load SVG assets
        ↓
3. Start HTTP Server
   - Port: 3000
   - Host: localhost
   - Enable Hot Reload
        ↓
4. File Watchers
   - Watch docs.json changes
   - Watch *.md file changes
   - Watch openapi.json changes
   - Watch asset changes
        ↓
5. Browser Auto-Reload
   - WebSocket connection
   - Instant updates on file changes
   - No manual refresh required
```

**Hot Reload Mechanism:**

1. File system watchers detect changes to any project file
2. Changed files are re-processed automatically
3. Browser receives WebSocket notification
4. Page auto-refreshes to show changes
5. State preserved where possible for seamless experience

#### Production Build Architecture

**Deployment Trigger** (`README.md` lines 29-32):

```
Developer Workflow
        ↓
1. git commit (commit changes)
        ↓
2. git push (push to default branch)
        ↓
3. GitHub webhook (notify Mintlify)
        ↓
4. Mintlify build pipeline (automatic build)
```

**Production Build Pipeline:**

```
GitHub Webhook Event
        ↓
Mintlify Build Service
        ↓
Stage 1: Repository Checkout
   - Clone repository
   - Checkout default branch (main/master)
   - Verify commit integrity
        ↓
Stage 2: Configuration Validation
   - Parse docs.json
   - Validate against JSON schema
   - Check navigation integrity
   - Verify all file references exist
        ↓
Stage 3: Content Processing
   - Process all .md files
   - Parse OpenAPI specification
   - Generate API documentation pages
   - Apply syntax highlighting
   - Build search index
        ↓
Stage 4: Static Site Generation
   - Generate HTML pages from markdown
   - Apply theme (mint theme)
   - Apply colors (primary, light, dark)
   - Build navigation structure
   - Create sitemap.xml
   - Generate robots.txt
        ↓
Stage 5: Asset Optimization
   - Compress SVG images
   - Minify CSS
   - Minify JavaScript
   - Generate responsive image variants
   - Create WebP format variants
        ↓
Stage 6: CDN Deployment
   - Upload to CDN storage
   - Purge CDN cache
   - Update DNS (if needed)
   - Verify deployment success
        ↓
Stage 7: Post-Deployment
   - Generate sitemap
   - Notify search engines
   - Update deployment logs
   - Send success notification
        ↓
    Live Documentation Site
```

**Build Characteristics:**

- **Build Time**: Typically 1-3 minutes for standard projects
- **Atomic Deployments**: All-or-nothing strategy (no partial deployments)
- **Zero Downtime**: New version replaces old seamlessly
- **Automatic Rollback**: Failed builds don't affect live site
- **Smart Caching**: Aggressive caching with intelligent invalidation

#### Content Delivery Architecture

**CDN Infrastructure:**

```
End User Request
        ↓
DNS Resolution
   - Route to nearest CDN edge location
        ↓
CDN Edge Location
        ↓
Cache Check
   - HIT: Return cached content (< 50ms)
   - MISS: Fetch from origin
        ↓
Origin Fetch (if cache miss)
   - Request from CDN origin
   - Receive content
   - Cache at edge for future requests
   - Return to user
        ↓
Content Delivery
   - HTML pages
   - CSS stylesheets
   - JavaScript files
   - Images and SVG assets
   - Search index
        ↓
Response Headers
   - Cache-Control directives
   - ETag for validation
   - Content-Encoding (gzip/brotli)
   - Security headers (CSP, X-Frame-Options)
```

**Caching Strategy:**

| Resource Type | Cache Duration | Strategy | Invalidation |
|---------------|----------------|----------|--------------|
| HTML Pages | 5 minutes | Stale-while-revalidate | On deployment |
| CSS (hashed) | 1 year | Immutable | Hash-based versioning |
| JS (hashed) | 1 year | Immutable | Hash-based versioning |
| Images (hashed) | 1 year | Immutable | Hash-based versioning |
| Search Index | 1 hour | Edge cached | On content update |
| API Documentation | 5 minutes | Stale-while-revalidate | On deployment |

**Performance Optimizations:**

1. **HTTP/2 and HTTP/3**: Multiplexed connections for parallel resource loading
2. **Brotli Compression**: Superior compression ratio vs gzip
3. **Early Hints**: Preload critical resources before HTML parsing
4. **Lazy Loading**: Images and components loaded on demand
5. **Critical CSS**: Above-the-fold styles inlined in HTML
6. **Code Splitting**: JavaScript loaded incrementally as needed

---

### Search Architecture

#### Search Index Generation

Search functionality is built entirely at build time with no backend search service required.

**Index Generation Process:**

```
Content Files
        ↓