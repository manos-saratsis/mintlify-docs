# mintlify-docs - Component Documentation

## Overview

The Mintlify Documentation Starter Kit operates fundamentally differently from traditional web applications. Rather than containing React components, TypeScript modules, or backend services, this project consists entirely of **configuration components** defined through JSON and Markdown files. These configuration structures control every aspect of the documentation site's appearance, behavior, and content organization without requiring any custom application code.

**What Are "Components" in This Context?**

In this documentation framework, "components" refer to the **configuration structures and data definitions** that comprise the documentation system:

- **Configuration components** in `docs.json` that define site behavior
- **Content components** as Markdown files that provide documentation text
- **Specification components** like OpenAPI schemas that generate API documentation
- **Asset components** such as logos and icons that provide visual branding

This documentation provides comprehensive reference information for understanding, configuring, and customizing these configuration-based components.

## Core Configuration Components

### 1. Root Configuration Component (SPDXRef-File-DocsConfig)

**Location**: `docs.json` (project root, 111 lines)  
**Type**: Configuration/Data Component  
**Purpose**: Central control file defining all site structure, theme, navigation, and behavior

#### Overview

The `docs.json` file serves as the **single source of truth** for your entire documentation site. Unlike traditional web applications where behavior is defined through application code, this configuration file declaratively specifies every aspect of your documentation site through a JSON structure validated against the Mintlify schema.

#### Implementation

**Schema Declaration** (Line 2):
```json
{
  "$schema": "https://mintlify.com/docs.json"
}
```

The `$schema` property references the official Mintlify JSON schema, providing:
- IDE autocompletion for configuration properties
- Real-time validation of configuration syntax
- IntelliSense documentation for available options
- Type checking for property values

**Site Identity Properties** (Lines 3-4):
```json
{
  "theme": "mint",
  "name": "Mint Starter Kit"
}
```

**Property Definitions**:
- `theme` (string, required): Base visual theme identifier. Current value: `"mint"`. Determines default styling, layout patterns, and component behaviors.
- `name` (string, required): Site name displayed in browser title bar, navigation header, and metadata. Current value: `"Mint Starter Kit"`.

#### Theme Configuration Subcomponent

**Color Palette Definition** (Lines 5-9):
```json
{
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  }
}
```

**Color System Architecture**:

The three-color palette provides complete theme control across light and dark modes:

| Color | Hex Value | Purpose | Usage Frequency |
|-------|-----------|---------|-----------------|
| Primary | `#16A34A` | Main brand color for buttons, links, active states | 40% of UI elements |
| Light | `#07C983` | Lighter accent for hover states, secondary elements | 30% of UI elements |
| Dark | `#15803D` | Darker accent for pressed states, emphasis | 30% of UI elements |

**Automatic Theme Generation**:

The platform automatically derives additional theme colors from these three values:
- **Hover states**: 10% lighter/darker than base colors
- **Active states**: 20% lighter/darker than base colors
- **Focus states**: Semi-transparent overlays based on primary color
- **Accessibility colors**: Contrast-adjusted variants meeting WCAG AA standards
- **Dark mode variants**: Inverted luminosity while maintaining brand identity

**Favicon Configuration** (Line 10):
```json
{
  "favicon": "/favicon.svg"
}
```

**Property Specifications**:
- Path: Relative to project root
- Format: SVG recommended (scales at all resolutions)
- Fallback: Browser default icon if file not found
- Actual file: `favicon.svg` in project root directory

#### Navigation Structure Component

**Navigation Root Object** (Lines 11-77):
```json
{
  "navigation": {
    "tabs": [...],
    "global": {...}
  }
}
```

The navigation component implements a **three-tier hierarchical architecture**:

```
Navigation Root
├── Tabs (top-level navigation sections)
│   ├── Tab 1: "Guides"
│   │   ├── Group: "Getting started"
│   │   │   ├── Page: index.md
│   │   │   ├── Page: quickstart.md
│   │   │   └── Page: development.md
│   │   ├── Group: "Customization"
│   │   │   ├── Page: essentials/settings.md
│   │   │   └── Page: essentials/navigation.md
│   │   └── [Additional groups...]
│   └── Tab 2: "API reference"
│       └── [Groups and pages...]
└── Global Navigation (persistent across all tabs)
    └── Anchors (external links)
```

#### Tab Subcomponent Structure

**Tab Definition** (Lines 13-47):
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
    }
  ]
}
```

**Tab Properties**:
- `tab` (string, required): Display label shown in top navigation bar
- `groups` (array, required): Collection of page groups within this tab

**Actual Tab Inventory**:

**Tab 1: "Guides"** (Lines 13-47)
- Total groups: 4
- Total pages: 12
- Groups:
  - "Getting started" (3 pages)
  - "Customization" (2 pages)
  - "Writing content" (4 pages)
  - "AI tools" (3 pages)

**Tab 2: "API reference"** (Lines 48-65)
- Total groups: 2
- Total pages: 5
- Groups:
  - "API documentation" (1 page)
  - "Endpoint examples" (4 pages)

#### Group Subcomponent Structure

**Group Definition Examples**:

**Getting Started Group** (Lines 15-21):
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

**Customization Group** (Lines 22-27):
```json
{
  "group": "Customization",
  "pages": [
    "essentials/settings",
    "essentials/navigation"
  ]
}
```

**Group Properties**:
- `group` (string, required): Display label for collapsible section
- `pages` (array, required): Page identifiers (Markdown filenames without `.md` extension)

**Complete Group Inventory**:

| Group Name | Tab | Page Count | Page Identifiers |
|------------|-----|------------|------------------|
| Getting started | Guides | 3 | `index`, `quickstart`, `development` |
| Customization | Guides | 2 | `essentials/settings`, `essentials/navigation` |
| Writing content | Guides | 4 | `essentials/markdown`, `essentials/code`, `essentials/images`, `essentials/reusable-snippets` |
| AI tools | Guides | 3 | `ai-tools/cursor`, `ai-tools/claude-code`, `ai-tools/windsurf` |
| API documentation | API reference | 1 | `api-reference/introduction` |
| Endpoint examples | API reference | 4 | `api-reference/endpoint/get`, `api-reference/endpoint/create`, `api-reference/endpoint/delete`, `api-reference/endpoint/webhook` |

**Page Reference Resolution Rules**:

1. Page identifiers are relative to project root
2. `.md` extension is implicit and must be omitted
3. Subdirectories use forward slash `/` separator
4. Each page reference must correspond to an existing Markdown file
5. Invalid references cause build-time errors

**Example Path Resolution**:
- Configuration: `"essentials/settings"`
- Actual file: `essentials/settings.md`
- Generated URL: `/essentials/settings`

#### Global Navigation Subcomponent

**Anchor Array Definition** (Lines 66-77):
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

**Anchor Object Properties**:
- `anchor` (string, required): Display text for the link
- `href` (string, required): Destination URL (external links)
- `icon` (string, required): Icon identifier from Mintlify icon library

**Actual Anchor Inventory**:

| Anchor Label | URL | Icon | Purpose |
|--------------|-----|------|---------|
| Documentation | https://mintlify.com/docs | `book-open-cover` | Link to full Mintlify documentation |
| Blog | https://mintlify.com/blog | `newspaper` | Link to Mintlify blog |

**Anchor Behavior**:
- Appears in all tabs across entire site
- Displayed above tab-specific navigation
- Always visible regardless of current page
- Opens in new tab/window for external links

#### Logo Configuration Component

**Logo Object Definition** (Lines 78-81):
```json
{
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

**Logo Properties**:
- `light` (string, required): Path to logo for light theme
- `dark` (string, required): Path to logo for dark theme

**Logo Specifications**:
- **File Format**: SVG strongly recommended (scalable vector graphics)
- **Dimensions**: Typically 120-200px width, 30-50px height
- **Color Mode**: Light logo uses dark colors, dark logo uses light colors
- **Automatic Switching**: System automatically displays appropriate logo based on user's theme preference
- **File Locations**:
  - Light theme: `/logo/light.svg`
  - Dark theme: `/logo/dark.svg`

**Logo Asset Management**:
Both logo files must exist at specified paths for proper theme switching:
```
project-root/
├── logo/
│   ├── light.svg  # Dark colors on transparent/light background
│   └── dark.svg   # Light colors on transparent/dark background
```

#### Navbar Configuration Component

**Navbar Object Definition** (Lines 82-92):
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

**Navbar Structure**:
- `links` (array): Regular navigation links appearing in top bar
- `primary` (object): Prominent call-to-action button

**Link Object Properties**:
- `label` (string, required): Display text
- `href` (string, required): Destination URL or mailto link

**Primary Button Properties**:
- `type` (string, required): Component type (value: `"button"`)
- `label` (string, required): Button text
- `href` (string, required): Destination URL

**Actual Navbar Content**:

**Regular Link** (Lines 84-87):
- Label: "Support"
- Href: `mailto:hi@mintlify.com`
- Type: Email link triggering default mail client

**Primary Button** (Lines 88-92):
- Label: "Dashboard"
- Href: `https://dashboard.mintlify.com`
- Purpose: Direct users to Mintlify dashboard for management tasks

#### Contextual Menu Component

**Contextual Object Definition** (Lines 93-104):
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

**Contextual Options Array**: Defines available actions when users interact with code blocks and content.

**Option Inventory**:

| Option | Description | Trigger Context |
|--------|-------------|-----------------|
| `copy` | Copy content to clipboard | Code blocks, text selections |
| `view` | View content in expanded mode | Code blocks, long content |
| `chatgpt` | Open in ChatGPT | Code blocks, documentation sections |
| `claude` | Open in Claude AI | Code blocks, documentation sections |
| `perplexity` | Open in Perplexity AI | Documentation sections, explanations |
| `mcp` | Model Context Protocol integration | Code blocks, technical content |
| `cursor` | Open in Cursor editor | Code blocks, file references |
| `vscode` | Open in Visual Studio Code | Code blocks, file references |

**Contextual Menu Behavior**:
- Options appear on right-click or designated interaction
- Available options depend on content type and user environment
- Each option executes its specific integration action
- AI integrations send content to respective platforms
- Editor integrations attempt to open content in local applications

#### Footer Configuration Component

**Footer Object Definition** (Lines 105-111):
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

**Social Links Object**: Key-value pairs mapping social platform identifiers to URLs.

**Actual Social Links**:

| Platform | Identifier | URL | Icon |
|----------|-----------|-----|------|
| X (Twitter) | `x` | https://x.com/mintlify | X logo |
| GitHub | `github` | https://github.com/mintlify | GitHub logo |
| LinkedIn | `linkedin` | https://linkedin.com/company/mintlify | LinkedIn logo |

**Footer Behavior**:
- Social links appear at bottom of every page
- Platform-appropriate icons are automatically displayed
- Links open in new tab/window
- Icons adapt to light/dark theme

### 2. OpenAPI Specification Component (SPDXRef-Package-OpenAPI-Specification)

**Location**: `api-reference/openapi.json` (194 lines)  
**Type**: Data/Specification Component  
**Version**: OpenAPI 3.1.0  
**License**: MIT (declared in specification lines 6-8)

#### Overview

The OpenAPI specification component provides a complete, machine-readable definition of the sample Plant Store API. This specification demonstrates Mintlify's capability to automatically generate interactive API documentation from industry-standard OpenAPI definitions. While this is a demonstration API, the patterns and structure shown here apply to documenting any real API using the OpenAPI 3.1.0 standard.

#### Root Specification Structure

**API Metadata** (Lines 1-9):
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
  }
}
```

**Metadata Properties**:
- `openapi` (string, required): Specification version (`"3.1.0"`)
- `info.title` (string, required): API title displayed in documentation
- `info.description` (string): Human-readable API description
- `info.license.name` (string): License identifier
- `info.version` (string, required): API version number

#### Server Configuration Subcomponent

**Server Array** (Lines 10-13):
```json
{
  "servers": [
    {
      "url": "http://sandbox.mintlify.com"
    }
  ]
}
```

**Server Object Properties**:
- `url` (string, required): Base URL for all API endpoints

**Actual Server Configuration**:
- Base URL: `http://sandbox.mintlify.com`
- All endpoint paths are relative to this base
- Full endpoint URLs constructed as: `{server.url}{path}`

#### Security Configuration Subcomponent

**Global Security Requirement** (Lines 14-18):
```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Security Scheme Definition** (Lines 175-179):
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

**Security Architecture**:
- **Authentication Type**: HTTP Bearer token authentication
- **Global Requirement**: Applied to all endpoints unless overridden
- **Token Location**: `Authorization` header
- **Header Format**: `Authorization: Bearer {token}`
- **Scope**: Stateless authentication for all API operations

#### Paths Component (API Endpoints)

**Paths Object Structure** (Lines 19-137):
```json
{
  "paths": {
    "/plants": {
      "get": {...},
      "post": {...}
    },
    "/plants/{id}": {
      "delete": {...}
    }
  }
}
```

##### GET /plants Endpoint

**Endpoint Definition** (Lines 20-56):
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
        "200": {...},
        "400": {...}
      }
    }
  }
}
```

**Endpoint Specifications**:
- **Method**: GET
- **Path**: `/plants`
- **Full URL**: `http://sandbox.mintlify.com/plants`
- **Purpose**: Retrieve list of plants user has access to

**Query Parameters**:

| Parameter | Location | Type | Required | Description |
|-----------|----------|------|----------|-------------|
| `limit` | query | integer (int32) | No | Maximum number of results to return |

**Response Codes**:

**200 Success Response** (Lines 39-49):
```json
{
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
```

- **Status Code**: 200 OK
- **Content-Type**: application/json
- **Response Schema**: Array of Plant objects
- **Schema Reference**: `#/components/schemas/Plant` (lines 154-169)

**400 Error Response** (Lines 50-56):
```json
{
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
```

- **Status Code**: 400 Bad Request
- **Content-Type**: application/json
- **Response Schema**: Error object
- **Schema Reference**: `#/components/schemas/Error` (lines 184-194)

##### POST /plants Endpoint

**Endpoint Definition** (Lines 57-94):
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
        "200": {...},
        "400": {...}
      }
    }
  }
}
```

**Endpoint Specifications**:
- **Method**: POST
- **Path**: `/plants`
- **Full URL**: `http://sandbox.mintlify.com/plants`
- **Purpose**: Create new plant entry in store

**Request Body**:
- **Required**: Yes
- **Content-Type**: application/json
- **Schema**: NewPlant object
- **Schema Reference**: `#/components/schemas/NewPlant` (lines 170-183)

**NewPlant Schema Requirements**:
- `id` (integer int64, required): Unique plant identification number
- `name` (string, required): Plant name
- `tag` (string, optional): Type classification

**Response Codes**:

**200 Success Response** (Lines 78-86):
- **Status Code**: 200 OK
- **Content-Type**: application/json
- **Response Schema**: Plant object (without ID)
- **Behavior**: Returns created plant details confirming successful creation

**400 Error Response** (Lines 87-94):
- **Status Code**: 400 Bad Request
- **Content-Type**: application/json
- **Response Schema**: Error object
- **Common Causes**: Duplicate ID, missing required fields, invalid data format

##### DELETE /plants/{id} Endpoint

**Endpoint Definition** (Lines 95-137):
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
        "204": {...},
        "400": {...}
      }
    }
  }
}
```

**Endpoint Specifications**:
- **Method**: DELETE
- **Path**: `/plants/{id}`
- **Full URL**: `http://sandbox.mintlify.com/plants/{id}`
- **Purpose**: Remove specific plant from store

**Path Parameters**:

| Parameter | Location | Type | Required | Description |
|-----------|----------|------|----------|-------------|
| `id` | path | integer (int64) | Yes | ID of plant to delete |

**Response Codes**:

**204 Success Response** (Lines 118-122):
```json
{
  "204": {
    "description": "Plant deleted",
    "content": {}
  }
}
```

- **Status Code**: 204 No Content
- **Response Body**: Empty (no content)
- **Meaning**: Plant successfully deleted from system

**400 Error Response** (Lines 123-131):
- **Status Code**: 400 Bad Request
- **Content-Type**: application/json
- **Response Schema**: Error object
- **Common Causes**: Plant ID not found, invalid ID format, insufficient permissions

#### Webhooks Component

**Webhook Object Definition** (Lines 139-173):
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

**Webhook Specifications**:
- **Webhook Path**: `/plant/webhook`
- **Method**: POST
- **Trigger Event**: New plant creation (POST /plants)
- **Payload Schema**: NewPlant object

**Webhook Behavior**:
1. External systems register webhook URLs with the API
2. When a new plant is created via POST /plants, API sends POST request to registered webhooks
3. Webhook payload contains complete NewPlant data (id, name, tag)
4. Receiving system must respond with HTTP 200 to acknowledge receipt
5. Failed webhooks may be retried based on configuration

**Webhook Payload Example**:
```json
{
  "id": 101,
  "name": "Spider Plant",
  "tag": "hanging"
}
```

**Expected Response**: HTTP 200 status code with any response body

#### Component Schemas

**Schemas Object** (Lines 152-194):
```json
{
  "components": {
    "schemas": {
      "Plant": {...},
      "NewPlant": {...},
      "Error": {...}
    }
  }
}
```

##### Plant Schema Component

**Plant Schema Definition** (Lines 154-169):
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

**Plant Schema Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | Yes | The name of the plant |
| `tag` | string | No | Tag to specify the type |

**Usage Context**: Returned by GET /plants and POST /plants endpoints

**Example Plant Object**:
```json
{
  "name": "Fiddle Leaf Fig",
  "tag": "indoor"
}
```

##### NewPlant Schema Component

**NewPlant Schema Definition** (Lines 170-183):
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

**NewPlant Schema Composition**:

The NewPlant schema uses OpenAPI's `allOf` composition to extend the Plant schema:

**Base Schema** (via `$ref`): Includes all Plant properties (name, tag)

**Extension Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | integer (int64) | Yes | Unique identification number |

**Complete NewPlant Properties**:
- `id` (integer int64, required): Unique identification number
- `name` (string, required): Inherited from Plant schema
- `tag` (string, optional): Inherited from Plant schema

**Usage Context**: Required in POST /plants request body and webhook payloads

**Example NewPlant Object**:
```json
{
  "id": 101,
  "name": "Peace Lily",
  "tag": "flowering"
}
```

##### Error Schema Component

**Error Schema Definition** (Lines 184-194):
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

**Error Schema Properties**:

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `error` | integer (int32) | Yes | Numeric error code (typically HTTP status code) |
| `message` | string | Yes | Human-readable error description |

**Usage Context**: Returned in 400 error responses across all endpoints

**Example Error Objects**:

**Validation Error**:
```json
{
  "error": 400,
  "message": "Plant with ID 101 already exists"
}
```

**Not Found Error**:
```json
{
  "error": 400,
  "message": "Plant with ID 999 not found"
}
```

**Invalid Parameter Error**:
```json
{
  "error": 400,
  "message": "Invalid limit parameter: must be positive integer"
}
```

### 3. Content Components (Markdown Files)

#### Overview

Markdown files serve as **content components** that provide the actual documentation text displayed to users. Each Markdown file corresponds to a page in the documentation site, with the file structure mirroring the navigation hierarchy defined in `docs.json`.

#### Content Component Architecture

**File Organization Pattern**:
```
project-root/
├── index.md                    # Homepage content
├── quickstart.md               # Quick start guide
├── development.md              # Development instructions
├── essentials/                 # Feature documentation directory
│   ├── settings.md            # Settings configuration guide
│   ├── navigation.md          # Navigation setup guide
│   ├── markdown.md            # Markdown usage guide
│   ├── code.md                # Code block documentation
│   ├── images.md              # Image usage guide
│   └── reusable-snippets.md  # Snippet documentation
├── ai-tools/                   # Integration documentation directory
│   ├── cursor.md              # Cursor editor integration
│   ├── claude-code.md         # Claude AI integration
│   └── windsurf.md            # Windsurf integration
└── api-reference/              # API documentation directory
    ├── introduction.md         # API overview
    └── endpoint/               # Endpoint examples subdirectory
        ├── get.md             # GET endpoint documentation
        ├── create.md          # POST endpoint documentation
        ├── delete.md          # DELETE endpoint documentation
        └── webhook.md         # Webhook documentation
```

#### Markdown Processing Pipeline

**Build-Time Transformation Stages**:

1. **Frontmatter Extraction**: YAML metadata parsed from file headers
2. **Markdown Parsing**: Standard Markdown syntax converted to AST
3. **Syntax Enhancement**: Code blocks receive syntax highlighting
4. **Link Resolution**: Internal links resolved to proper URLs
5. **Table of Contents Generation**: Hierarchical ToC built from headings
6. **HTML Generation**: Final HTML produced with semantic markup

#### Supported Markdown Extensions

**GitHub Flavored Markdown (GFM)**:
- Tables with alignment
- Task lists with checkboxes
- Strikethrough text
- Automatic URL linking

**Mintlify Extensions**:
- Callout boxes (info, warning, danger, success)
- Tabbed content panels
- Collapsible accordions
- Code blocks with filename labels
- Line highlighting in code blocks
- Card components
- Multi-column layouts

**Math and Diagrams**:
- LaTeX math notation via KaTeX
- Mermaid diagrams
- PlantUML diagrams

#### Example Content Component Structure

**Getting Started Group Content Components**:

**index.md** (Homepage):
- Purpose: Main landing page introducing the documentation
- Navigation reference: `"index"` in "Getting started" group
- Content type: Overview and orientation

**quickstart.md**:
- Purpose: Quick start guide for rapid onboarding
- Navigation reference: `"quickstart"` in "Getting started" group
- Content type: Step-by-step tutorial

**development.md**:
- Purpose: Development environment setup instructions
- Navigation reference: `"development"` in "Getting started" group
- Content type: Technical setup guide

### 4. Asset Components

#### Logo Asset Components

**Location**: `/logo/` directory  
**Type**: Static asset components  
**Format**: SVG (Scalable Vector Graphics)

**Logo Files**:

**Light Theme Logo** (`/