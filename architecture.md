I need to explore the actual source code to create accurate architecture documentation. Let me search for the real application code.

<shell>
<command>find . -type f -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" | grep -E "(src/|components/|lib/|services/)" | head -20</command>
</shell>

<shell>
<command>ls -la</command>
</shell>

<shell>
<command>find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.json" \) | head -30</command>
</shell>

<shell>
<command>cat package.json 2>/dev/null || echo "No package.json found"</command>
</shell>

<shell>
<command>find . -name "*.md" -type f</command>
</shell>

<read_file>
<path>concepts.md</path>
</read_file>

Based on my analysis of the provided source code, I can see that this is actually a **Mintlify documentation starter kit**, not the OrchestRAI application referenced in the example markdown files. The example content in `concepts.md`, `tutorials.md`, etc. are template/placeholder content that doesn't match the actual codebase.

Let me create accurate architecture documentation based on the **actual source code** provided:

---

# Architecture Documentation

## Overview

This project is a **Mintlify documentation starter kit** designed to help teams quickly create and deploy professional documentation websites. The architecture is built on Mintlify's documentation platform, which provides a configuration-driven approach to building documentation sites with minimal code.

The system consists of:
- A JSON-based configuration system (`docs.json`)
- Markdown-based content files
- An OpenAPI specification for API documentation
- Integration with Mintlify's hosting and deployment infrastructure

## Implementation

### Project Structure

The documentation project follows this file organization:

```
.
├── docs.json                    # Main configuration file
├── README.md                    # Setup instructions
├── *.md                        # Content pages (guides, tutorials, etc.)
├── api-reference/
│   ├── openapi.json           # OpenAPI 3.1.0 specification
│   └── endpoint/*.md          # API endpoint documentation pages
└── logo/
    ├── light.svg              # Logo for light theme
    └── dark.svg               # Logo for dark theme
```

### Configuration Architecture

The entire documentation site is configured through `docs.json` (located at the project root). This file uses Mintlify's schema and controls all aspects of the documentation site.

**Core Configuration Structure:**

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
  "favicon": "/favicon.svg"
}
```

**Key Configuration Components:**

1. **Theme System**: The `theme` property (`"mint"`) determines the overall visual style
2. **Color Scheme**: Three color values (`primary`, `light`, `dark`) define the brand colors throughout the site
3. **Branding**: `name`, `logo`, and `favicon` properties control site branding

### Navigation System

The navigation architecture is defined in the `navigation` object within `docs.json`. It supports a multi-tab interface with nested groups and pages.

**Navigation Structure (`docs.json` lines 9-72):**

```json
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
```

**Navigation Hierarchy:**

1. **Tabs**: Top-level navigation sections (e.g., "Guides", "API reference")
2. **Groups**: Subsections within each tab (e.g., "Getting started", "Customization")
3. **Pages**: Individual markdown files referenced by path without `.md` extension

### Content Management

Content is managed through Markdown files that are referenced in the navigation configuration.

**Content File Locations:**

- Root-level pages: `index.md`, `quickstart.md`, `development.md`
- Nested pages: `essentials/settings.md`, `essentials/navigation.md`
- API reference: `api-reference/introduction.md`, `api-reference/endpoint/*.md`

**Markdown Processing:**

The Mintlify platform processes standard Markdown with extended support for:
- Code blocks with syntax highlighting
- Custom components (as referenced in `README.md`)
- Images and media
- Reusable snippets

### API Documentation Architecture

The API documentation uses OpenAPI 3.1.0 specification located in `api-reference/openapi.json`.

**API Specification Structure:**

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "OpenAPI Plant Store",
    "description": "A sample API...",
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

**API Endpoints Defined:**

1. **GET /plants** (line 18): Retrieves all plants with optional limit parameter
2. **POST /plants** (line 46): Creates a new plant
3. **DELETE /plants/{id}** (line 82): Deletes a plant by ID
4. **Webhook /plant/webhook** (line 113): Receives plant creation notifications

**Security Configuration:**

Bearer authentication is configured globally (lines 13-15):

```json
"security": [
  {
    "bearerAuth": []
  }
]
```

Security scheme definition (lines 175-179):

```json
"securitySchemes": {
  "bearerAuth": {
    "type": "http",
    "scheme": "bearer"
  }
}
```

### Global Navigation Elements

The `navigation.global` section defines site-wide navigation elements.

**Anchors (External Links):**

Located in `docs.json` (lines 64-72):

```json
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
```

### Brand and UI Customization

**Logo Configuration (`docs.json` lines 75-78):**

```json
"logo": {
  "light": "/logo/light.svg",
  "dark": "/logo/dark.svg"
}
```

Supports theme-aware logos that automatically switch based on user's theme preference.

**Navbar Configuration (`docs.json` lines 79-91):**

```json
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
```

**Footer Configuration (`docs.json` lines 102-107):**

```json
"footer": {
  "socials": {
    "x": "https://x.com/mintlify",
    "github": "https://github.com/mintlify",
    "linkedin": "https://linkedin.com/company/mintlify"
  }
}
```

### Contextual Integration Features

The `contextual` configuration enables AI tool integrations (`docs.json` lines 92-101):

```json
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
```

This enables users to interact with documentation through various AI assistants and development tools.

## Development Workflow

### Local Development Setup

**Prerequisites (`README.md` lines 18-20):**

1. Node.js environment
2. npm package manager

**Installation (`README.md` lines 18-20):**

```bash
npm i -g mint
```

This installs the Mintlify CLI globally on the system.

**Running Local Preview (`README.md` lines 22-24):**

```bash
mint dev
```

This command must be executed in the directory containing `docs.json`. The local preview server runs at `http://localhost:3000`.

### Deployment Architecture

**GitHub-Based Deployment:**

The deployment architecture uses GitHub integration as described in `README.md` (lines 28-32):

1. Install the Mintlify GitHub app from the dashboard
2. Connect the app to the documentation repository
3. Push changes to the default branch
4. Changes automatically deploy to production

**Deployment Flow:**

```
Git Push → GitHub → Mintlify GitHub App → Production Deployment
```

No manual build or deployment steps are required.

### Troubleshooting Architecture

**Common Issues (`README.md` lines 36-38):**

1. **Dev environment not running**: Execute `mint update` to ensure latest CLI version
2. **404 errors**: Verify `docs.json` exists in the current directory

## Data Schemas

### OpenAPI Schema Definitions

**Plant Schema (`api-reference/openapi.json` lines 132-150):**

```json
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
```

**NewPlant Schema (lines 151-169):**

Uses `allOf` composition to extend Plant with an ID:

```json
"NewPlant": {
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

**Error Schema (lines 170-183):**

```json
"Error": {
  "required": ["error", "message"],
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
```

## Build and Deployment Architecture

### Build Process

The Mintlify platform handles all build processes automatically:

1. **Markdown Processing**: Converts `.md` files to HTML
2. **OpenAPI Processing**: Generates interactive API documentation from `openapi.json`
3. **Asset Optimization**: Optimizes images and other static assets
4. **Search Indexing**: Creates searchable documentation index
5. **Theme Application**: Applies configured colors and branding

### Hosting Architecture

Documentation is hosted on Mintlify's infrastructure:

- **Production URL**: Configured through Mintlify dashboard
- **CDN Distribution**: Global content delivery network
- **HTTPS**: Automatic SSL certificate management
- **Custom Domains**: Configurable through dashboard

## Extension Points

### Adding New Content

**New Pages:**

1. Create a new `.md` file in the appropriate directory
2. Add the file path (without `.md`) to `docs.json` navigation
3. Commit and push changes

**New API Endpoints:**

1. Add endpoint definition to `api-reference/openapi.json`
2. Optionally create dedicated `.md` page for detailed documentation
3. Reference in navigation configuration

### Customization Options

**Available Customizations:**

1. **Colors**: Modify `colors` object in `docs.json`
2. **Branding**: Update `logo`, `favicon`, and `name` properties
3. **Navigation**: Restructure `navigation` object
4. **External Links**: Modify `anchors` in global navigation
5. **Social Links**: Update `footer.socials` configuration

## Technology Stack

**Core Technologies:**

- **Mintlify Platform**: Documentation hosting and rendering
- **Markdown**: Content authoring format
- **OpenAPI 3.1.0**: API specification standard
- **JSON**: Configuration format
- **Node.js**: Development tooling (CLI)

**No Custom Code:**

This architecture is entirely configuration-driven. There are no custom React components, TypeScript files, or build scripts in the provided codebase.

## Security Architecture

**Authentication:**

The sample API uses bearer token authentication as defined in the OpenAPI specification:

- Security scheme: HTTP Bearer
- Applied globally to all endpoints
- Token management handled by consuming applications

**Data Validation:**

Schema validation is defined in OpenAPI specification:
- Required fields enforced
- Type validation (string, integer, etc.)
- Format validation (int32, int64)

## Performance Considerations

**Static Generation:**

Documentation is pre-rendered for optimal performance:
- Fast page loads
- SEO-friendly HTML
- Minimal client-side JavaScript

**CDN Distribution:**

Global CDN ensures low-latency access worldwide.

**Search Optimization:**

Built-in search indexing provides fast content discovery without external dependencies.

---

**Note**: This architecture documentation is based exclusively on the actual source code provided (Mintlify starter kit), not the OrchestRAI application referenced in the example markdown files. The codebase contains no React components, TypeScript application code, or Supabase integration - it is purely a documentation project configuration.