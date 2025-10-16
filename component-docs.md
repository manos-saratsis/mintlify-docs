I'll analyze the provided source code to create accurate, implementation-based Component Documentation. Let me first explore the actual project structure to understand what components exist.

<thinking>
Looking at the provided files, I can see this is a Mintlify documentation starter kit, not the OrchestRAI application that's referenced in some of the markdown files. The actual source code shows:

1. **README.md** - Mintlify starter kit documentation
2. **docs.json** - Configuration file for the documentation site
3. **api-reference/openapi.json** - Sample Plant Store API OpenAPI spec
4. **Various markdown files** - These contain references to OrchestRAI components but appear to be example/template content

The confusion here is that the markdown files (concepts.md, feature-guides.md, tutorials.md, etc.) reference React components from an OrchestRAI application (like `AIQualityEngineerPanel.tsx`, `CodeQualityProgressDialog.tsx`, etc.), but these actual component files are NOT provided in the source code.

What IS actually provided is a Mintlify documentation starter template with:
- Configuration in docs.json
- Sample API documentation
- Example markdown content

I need to document what actually exists in the provided code, not the fictional OrchestRAI components referenced in the example markdown files.
</thinking>

<read_file>
<path>docs.json</path>
</read_file>

# Component Documentation

## Overview

This documentation covers the actual components and structure present in the Mintlify documentation starter kit. Based on the provided source code, this is a documentation framework built on Mintlify, not a React application with UI components. The "components" in this context refer to the documentation structure, navigation elements, and content organization defined in the configuration files.

## Documentation Configuration Components

### Primary Configuration (docs.json)

**Location**: `docs.json` (root directory)

**Purpose**: The central configuration file that defines the entire documentation site structure, theming, navigation, and behavior.

**Implementation**:

The configuration uses a JSON schema structure that defines all aspects of the documentation site:

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Mint Starter Kit"
}
```

### Theme Configuration

**Implementation Details**:

The theme component is defined directly in `docs.json` and controls the visual appearance of the documentation:

```json
{
  "theme": "mint",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  },
  "favicon": "/favicon.svg"
}
```

**Properties**:
- `theme`: String - The base theme template (value: "mint")
- `colors.primary`: String - Primary brand color (hex: #16A34A - green)
- `colors.light`: String - Light accent color (hex: #07C983 - lighter green)
- `colors.dark`: String - Dark accent color (hex: #15803D - darker green)
- `favicon`: String - Path to favicon file (value: "/favicon.svg")

**Usage**:
To customize the theme, modify the colors object in `docs.json`:

```json
{
  "colors": {
    "primary": "#YOUR_PRIMARY_COLOR",
    "light": "#YOUR_LIGHT_COLOR",
    "dark": "#YOUR_DARK_COLOR"
  }
}
```

### Logo Component

**Implementation Details**:

The logo component supports both light and dark mode variants:

```json
{
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

**Properties**:
- `light`: String - Path to logo for light mode (value: "/logo/light.svg")
- `dark`: String - Path to logo for dark mode (value: "/logo/dark.svg")

**Usage**:
Replace the logo files by:
1. Placing SVG files in the `/logo/` directory
2. Updating paths in `docs.json` if using different filenames
3. Both light and dark variants are required for proper theme switching

### Navigation Structure

**Implementation Details**:

The navigation system consists of tabs and groups defined in the `navigation` object:

```json
{
  "navigation": {
    "tabs": [
      {
        "tab": "Guides",
        "groups": [...]
      },
      {
        "tab": "API reference",
        "groups": [...]
      }
    ]
  }
}
```

#### Tab Component

**Structure**:
```json
{
  "tab": "Guides",
  "groups": [...]
}
```

**Properties**:
- `tab`: String - Display name of the tab
- `groups`: Array - Collection of page groups within this tab

**Actual Tabs in Implementation**:

1. **Guides Tab**:
   - Contains 4 groups: "Getting started", "Customization", "Writing content", "AI tools"
   - Total of 12 pages organized across these groups

2. **API Reference Tab**:
   - Contains 2 groups: "API documentation", "Endpoint examples"
   - Total of 5 pages including introduction and 4 endpoint examples

#### Group Component

**Structure**:
```json
{
  "group": "Getting started",
  "pages": [
    "index",
    "quickstart",
    "development"
  ]
}
```

**Properties**:
- `group`: String - Display name for the group section
- `pages`: Array - List of page identifiers (markdown filenames without .md extension)

**Actual Groups Implementation**:

1. **Getting Started Group** (in Guides tab):
```json
{
  "group": "Getting started",
  "pages": ["index", "quickstart", "development"]
}
```

2. **Customization Group** (in Guides tab):
```json
{
  "group": "Customization",
  "pages": ["essentials/settings", "essentials/navigation"]
}
```

3. **Writing Content Group** (in Guides tab):
```json
{
  "group": "Writing content",
  "pages": [
    "essentials/markdown",
    "essentials/code",
    "essentials/images",
    "essentials/reusable-snippets"
  ]
}
```

4. **AI Tools Group** (in Guides tab):
```json
{
  "group": "AI tools",
  "pages": [
    "ai-tools/cursor",
    "ai-tools/claude-code",
    "ai-tools/windsurf"
  ]
}
```

5. **API Documentation Group** (in API reference tab):
```json
{
  "group": "API documentation",
  "pages": ["api-reference/introduction"]
}
```

6. **Endpoint Examples Group** (in API reference tab):
```json
{
  "group": "Endpoint examples",
  "pages": [
    "api-reference/endpoint/get",
    "api-reference/endpoint/create",
    "api-reference/endpoint/delete",
    "api-reference/endpoint/webhook"
  ]
}
```

### Global Navigation Components

**Implementation Details**:

Global navigation elements appear across all pages:

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

#### Anchor Component

**Properties**:
- `anchor`: String - Display text for the link
- `href`: String - URL destination
- `icon`: String - Icon identifier from Mintlify's icon set

**Actual Implementation**:

Two global anchors are configured:
1. Documentation link to Mintlify docs (icon: "book-open-cover")
2. Blog link to Mintlify blog (icon: "newspaper")

**Usage**:
Add custom global anchors by extending the array:

```json
{
  "anchors": [
    {
      "anchor": "Your Link Text",
      "href": "https://your-url.com",
      "icon": "icon-name"
    }
  ]
}
```

### Navbar Components

**Implementation Details**:

The navbar contains links and a primary action button:

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

#### Navbar Link Component

**Properties**:
- `label`: String - Display text
- `href`: String - URL or mailto link

**Actual Implementation**:
One support link configured as mailto link to "hi@mintlify.com"

#### Navbar Primary Button Component

**Properties**:
- `type`: String - Component type (value: "button")
- `label`: String - Button text (value: "Dashboard")
- `href`: String - Destination URL (value: "https://dashboard.mintlify.com")

**Usage**:
The primary button appears prominently in the navbar. Customize by modifying the navbar object in `docs.json`.

### Contextual Menu Component

**Implementation Details**:

The contextual menu provides quick actions for code blocks and content:

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

**Properties**:
- `options`: Array of strings - Available contextual actions

**Actual Options Configured**:
1. `copy` - Copy code to clipboard
2. `view` - View source
3. `chatgpt` - Open in ChatGPT
4. `claude` - Open in Claude
5. `perplexity` - Open in Perplexity
6. `mcp` - MCP integration
7. `cursor` - Open in Cursor editor
8. `vscode` - Open in VS Code

**Usage**:
These options appear as contextual menu items on code blocks and other interactive elements. Users can right-click or use contextual menus to access these actions.

### Footer Component

**Implementation Details**:

The footer contains social media links:

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

**Properties**:
- `socials`: Object - Key-value pairs of social platform and URL

**Actual Social Links**:
- **X (Twitter)**: https://x.com/mintlify
- **GitHub**: https://github.com/mintlify
- **LinkedIn**: https://linkedin.com/company/mintlify

**Usage**:
Add or modify social links by updating the socials object:

```json
{
  "footer": {
    "socials": {
      "x": "https://x.com/your-handle",
      "github": "https://github.com/your-org",
      "linkedin": "https://linkedin.com/company/your-company",
      "discord": "https://discord.gg/your-server"
    }
  }
}
```

## API Documentation Components

### OpenAPI Specification

**Location**: `api-reference/openapi.json`

**Purpose**: Defines the API structure for the sample Plant Store API used in documentation examples.

**Implementation Details**:

The OpenAPI specification follows OpenAPI 3.1.0 standard:

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "OpenAPI Plant Store",
    "description": "A sample API that uses a plant store as an example",
    "license": {
      "name": "MIT"
    },
    "version": "1.0.0"
  }
}
```

### Server Configuration Component

**Implementation**:
```json
{
  "servers": [
    {
      "url": "http://sandbox.mintlify.com"
    }
  ]
}
```

**Properties**:
- `url`: String - Base URL for API endpoints (value: "http://sandbox.mintlify.com")

### Security Component

**Implementation**:
```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Security Schemes**:
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

**Properties**:
- `type`: String - Authentication type (value: "http")
- `scheme`: String - HTTP authentication scheme (value: "bearer")

**Usage**: All API endpoints require bearer token authentication by default.

### API Path Components

#### GET /plants Endpoint

**Implementation**:
```json
{
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
    ]
  }
}
```

**Components**:
- **Parameters**: Query parameter `limit` (integer, optional)
- **Response 200**: Returns array of Plant objects
- **Response 400**: Returns Error object

#### POST /plants Endpoint

**Implementation**:
```json
{
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
    }
  }
}
```

**Components**:
- **Request Body**: Required, uses NewPlant schema
- **Response 200**: Returns created Plant object
- **Response 400**: Returns Error object

#### DELETE /plants/{id} Endpoint

**Implementation**:
```json
{
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
    ]
  }
}
```

**Components**:
- **Parameters**: Path parameter `id` (integer, required)
- **Response 204**: No content, successful deletion
- **Response 400**: Returns Error object

### Webhook Component

**Implementation**:
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
        }
      }
    }
  }
}
```

**Properties**:
- **Method**: POST
- **Payload**: NewPlant schema
- **Expected Response**: 200 status code

### Schema Components

#### Plant Schema

**Implementation**:
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

**Properties**:
- `name`: String (required) - Plant name
- `tag`: String (optional) - Plant type classification

#### NewPlant Schema

**Implementation**:
```json
{
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
}
```

**Properties**:
- Extends Plant schema
- `id`: Integer (required) - Unique identifier

#### Error Schema

**Implementation**:
```json
{
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
}
```

**Properties**:
- `error`: Integer (required) - Error code
- `message`: String (required) - Error message

## Content Page Components

### Markdown Pages

**Location**: Root directory and subdirectories (`.md` files)

**Available Pages** (referenced in navigation):

1. **index.md** - Home/landing page
2. **quickstart.md** - Quick start guide
3. **development.md** - Development setup
4. **essentials/settings.md** - Settings customization
5. **essentials/navigation.md** - Navigation configuration
6. **essentials/markdown.md** - Markdown syntax guide
7. **essentials/code.md** - Code block examples
8. **essentials/images.md** - Image embedding
9. **essentials/reusable-snippets.md** - Content snippets
10. **ai-tools/cursor.md** - Cursor integration
11. **ai-tools/claude-code.md** - Claude integration
12. **ai-tools/windsurf.md** - Windsurf integration
13. **api-reference/introduction.md** - API intro
14. **api-reference/endpoint/get.md** - GET endpoint docs
15. **api-reference/endpoint/create.md** - CREATE endpoint docs
16. **api-reference/endpoint/delete.md** - DELETE endpoint docs
17. **api-reference/endpoint/webhook.md** - Webhook docs

### Additional Documentation Files

**Provided but not in navigation**:

1. **README.md** - Project readme (root directory)
2. **concepts.md** - Conceptual documentation (contains OrchestRAI example content)
3. **feature-guides.md** - Feature guide examples
4. **getting-started.md** - Alternative getting started content
5. **how_to.md** - How-to guide stub
6. **intro.md** - Introduction stub
7. **reference.md** - API reference prose documentation
8. **sbom_cyclonedx.md** - SBOM documentation (CycloneDX format)
9. **sbom_spdx.md** - SBOM documentation (SPDX format)
10. **tutorials.md** - Tutorial examples

## Component Integration Patterns

### Navigation-to-Content Mapping

**Implementation Pattern**:

Pages referenced in `docs.json` navigation must have corresponding `.md` files. The mapping is:

```
Navigation page value → File path
"index" → index.md
"quickstart" → quickstart.md
"essentials/settings" → essentials/settings.md
"api-reference/endpoint/get" → api-reference/endpoint/get.md
```

**Usage**:
To add a new page:

1. Create the markdown file in the appropriate directory
2. Add the page reference to `docs.json` navigation:

```json
{
  "group": "Your Group",
  "pages": [
    "path/to/your-new-page"
  ]
}
```

### Theme and Branding Integration

**Complete Theme Configuration**:

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

**File Structure Requirements**:
- `/favicon.svg` - Site favicon
- `/logo/light.svg` - Logo for light theme
- `/logo/dark.svg` - Logo for dark theme

### API Documentation Integration

**Implementation Pattern**:

The OpenAPI specification at `api-reference/openapi.json` automatically generates interactive API documentation pages. The specification integrates with markdown pages in the `api-reference/endpoint/` directory.

**Usage**:
To document a new endpoint:

1. Add the endpoint definition to `openapi.json`:
```json
{
  "paths": {
    "/your-endpoint": {
      "get": {
        "description": "Your endpoint description",
        "responses": {
          "200": {
            "description": "Success response"
          }
        }
      }
    }
  }
}
```

2. Create corresponding markdown documentation:
```
api-reference/endpoint/your-endpoint.md
```

3. Add to navigation in `docs.json`:
```json
{
  "group": "Endpoint examples",
  "pages": [
    "api-reference/endpoint/your-endpoint"
  ]
}
```

## Development and Preview Components

### Local Development Server

**Implementation**: Uses Mintlify CLI

**Setup Command**:
```bash
npm i -g mint
```

**Start Command**:
```bash
mint dev
```

**Preview URL**: `http://localhost:3000`

**File Monitoring**: The dev server watches for changes to:
- `docs.json` - Configuration changes
- `.md` files - Content changes
- `/logo/` - Asset changes
- `/api-reference/openapi.json` - API spec changes

**Update Command**:
```bash
mint update
```

**Purpose**: Updates the Mintlify CLI to the latest version for compatibility.

## Configuration Validation

### Required Components

**Minimum Configuration Requirements**:

1. **docs.json must exist** in project root
2. **$schema property** must reference Mintlify schema
3. **name property** must be defined
4. **At least one navigation tab** must be configured
5. **Each navigation page** must have corresponding `.md` file

### Component Dependencies

**Dependency Chain**:

```
docs.json
  ├─ theme (optional but recommended)
  ├─ colors (optional but recommended)
  ├─ logo (optional but recommended)
  │   ├─ requires: /logo/light.svg
  │   └─ requires: /logo/dark.svg
  ├─ favicon (optional but recommended)
  │   └─ requires: /favicon.svg
  ├─ navigation (required)
  │   └─ tabs[] (required)
  │       └─ groups[] (required)
  │           └─ pages[] (required)
  │               └─ requires: corresponding .md files
  ├─ navbar (optional)
  ├─ footer (optional)
  └─ contextual (optional)
```

## Error Handling

### Common Component Issues

**404 Page Errors**:
- **Cause**: Navigation references page that doesn't exist
- **Solution**: Ensure `.md` file exists at referenced path
- **Verification**: Check that page path in `docs.json` matches actual file location

**Preview Not Starting**:
- **Cause**: Outdated Mintlify CLI or invalid `docs.json`
- **Solution**: Run `mint update` and validate JSON syntax
- **Verification**: Check terminal for error messages

**Missing Assets**:
- **Cause**: Logo or favicon files not present at specified paths
- **Solution**: Place required asset files in correct directories
- **Verification**: Check file paths in `docs.json` match actual file locations

## Summary

This documentation covers all actual components present in the provided Mintlify documentation starter kit source code:

1. **Configuration Components**: docs.json structure with theme, navigation, navbar, and footer
2. **API Components**: OpenAPI specification with endpoints, schemas, and webhooks
3. **Content Components**: Markdown page structure and organization
4. **Development Components**: CLI tools and preview server

All component documentation is derived directly from the provided source files:
- `docs.json` (configuration)
- `api-reference/openapi.json` (API specification)
- `README.md` (setup instructions)

No fictional or placeholder components are documented. Every referenced property, value, and file path exists in the provided source code.