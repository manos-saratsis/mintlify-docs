I'll analyze the provided source code to create comprehensive, accurate component documentation based on what actually exists in the codebase.

After thorough analysis, I can confirm this is a **Mintlify documentation starter kit**, not the OrchestRAI application referenced in the example markdown files. I will document only the actual components present in the provided source code.

---

# Component Documentation

## Overview

This documentation covers the configuration and structural components of the Mintlify documentation starter kit. Unlike traditional software applications with UI components, this is a documentation framework where "components" refer to the configuration structures, navigation elements, and content organization defined in JSON and markdown files.

The Mintlify starter kit is a documentation-as-code system where all visual and structural elements are defined through configuration files rather than React components or TypeScript classes. This documentation focuses on these configuration components and their relationships.

## Core Configuration Components

### 1. Main Configuration Component (docs.json)

**Location**: `docs.json` (project root)

**Purpose**: The central configuration file that defines the entire documentation site's structure, appearance, and behavior.

#### Overview

The `docs.json` file serves as the single source of truth for your documentation site. It controls theming, navigation structure, branding, and global settings. This component is required and must be present at the project root for the Mintlify CLI to function.

#### Implementation

**Schema Declaration**:
```json
{
  "$schema": "https://mintlify.com/docs.json"
}
```

The schema property (line 2) references the Mintlify JSON schema, enabling IDE autocompletion and validation.

**Basic Properties**:
```json
{
  "theme": "mint",
  "name": "Mint Starter Kit",
  "favicon": "/favicon.svg"
}
```

- `theme` (line 3): Defines the base visual theme. Value: `"mint"`
- `name` (line 4): Site name displayed in the browser and navigation. Value: `"Mint Starter Kit"`
- `favicon` (line 10): Path to favicon file. Value: `"/favicon.svg"`

#### Usage

To customize the basic configuration:

1. Open `docs.json` in your project root
2. Modify the `name` property to match your project:
   ```json
   "name": "Your Project Name"
   ```
3. Replace the favicon by placing your favicon at `/favicon.svg` or update the path
4. Save the file - changes appear immediately in `mint dev` preview

### 2. Color Scheme Component

**Location**: `docs.json` → `colors` object (lines 5-9)

**Purpose**: Defines the color palette for the entire documentation site, controlling primary actions, highlights, and theme variations.

#### Implementation

```json
{
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  }
}
```

**Properties**:
- `primary` (line 6): Main brand color used for buttons, links, and highlights. Default: `#16A34A` (green)
- `light` (line 7): Lighter accent color for hover states and secondary elements. Default: `#07C983` (lighter green)
- `dark` (line 8): Darker accent color for pressed states and emphasis. Default: `#15803D` (darker green)

#### Usage

To apply your brand colors:

```json
{
  "colors": {
    "primary": "#0066CC",
    "light": "#3399FF",
    "dark": "#004499"
  }
}
```

**Color Application**:
- Primary: Navigation active states, call-to-action buttons, important links
- Light: Hover effects, secondary buttons, subtle highlights
- Dark: Selected states, footer elements, emphasis text

### 3. Navigation Component

**Location**: `docs.json` → `navigation` object (lines 11-71)

**Purpose**: Defines the complete navigation structure including tabs, groups, and pages.

#### Implementation

The navigation component uses a hierarchical structure: Tabs → Groups → Pages

**Full Structure**:
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
    ],
    "global": {
      "anchors": [...]
    }
  }
}
```

#### Tab Subcomponent

**Definition**: Top-level navigation sections visible in the main navigation bar.

**Implementation** (lines 13-50):
```json
{
  "tab": "Guides",
  "groups": [
    {
      "group": "Getting started",
      "pages": ["index", "quickstart", "development"]
    }
  ]
}
```

**Properties**:
- `tab` (string): Display name for the tab
- `groups` (array): Collection of page groups within this tab

**Actual Tabs in Codebase**:

1. **Guides Tab** (lines 13-47):
   - Contains 4 groups
   - 12 total pages
   - Groups: "Getting started", "Customization", "Writing content", "AI tools"

2. **API Reference Tab** (lines 48-65):
   - Contains 2 groups
   - 5 total pages
   - Groups: "API documentation", "Endpoint examples"

#### Group Subcomponent

**Definition**: Collapsible sections within tabs that organize related pages.

**Implementation Examples**:

**Getting Started Group** (lines 15-21):
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

**Customization Group** (lines 22-27):
```json
{
  "group": "Customization",
  "pages": [
    "essentials/settings",
    "essentials/navigation"
  ]
}
```

**Properties**:
- `group` (string): Display name for the collapsible section
- `pages` (array of strings): Page identifiers (markdown filenames without `.md` extension)

**Complete Group List**:

1. **Getting started** (3 pages):
   - `index` → `index.md`
   - `quickstart` → `quickstart.md`
   - `development` → `development.md`

2. **Customization** (2 pages):
   - `essentials/settings` → `essentials/settings.md`
   - `essentials/navigation` → `essentials/navigation.md`

3. **Writing content** (4 pages):
   - `essentials/markdown` → `essentials/markdown.md`
   - `essentials/code` → `essentials/code.md`
   - `essentials/images` → `essentials/images.md`
   - `essentials/reusable-snippets` → `essentials/reusable-snippets.md`

4. **AI tools** (3 pages):
   - `ai-tools/cursor` → `ai-tools/cursor.md`
   - `ai-tools/claude-code` → `ai-tools/claude-code.md`
   - `ai-tools/windsurf` → `ai-tools/windsurf.md`

5. **API documentation** (1 page):
   - `api-reference/introduction` → `api-reference/introduction.md`

6. **Endpoint examples** (4 pages):
   - `api-reference/endpoint/get` → `api-reference/endpoint/get.md`
   - `api-reference/endpoint/create` → `api-reference/endpoint/create.md`
   - `api-reference/endpoint/delete` → `api-reference/endpoint/delete.md`
   - `api-reference/endpoint/webhook` → `api-reference/endpoint/webhook.md`

#### Usage

**Adding a New Page**:

1. Create the markdown file:
   ```bash
   touch my-new-page.md
   ```

2. Add to navigation in `docs.json`:
   ```json
   {
     "group": "Getting started",
     "pages": [
       "index",
       "quickstart",
       "development",
       "my-new-page"
     ]
   }
   ```

**Adding a New Group**:
```json
{
  "tab": "Guides",
  "groups": [
    {
      "group": "Getting started",
      "pages": ["index", "quickstart", "development"]
    },
    {
      "group": "New Section",
      "pages": ["new-page-1", "new-page-2"]
    }
  ]
}
```

**Adding a New Tab**:
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
      },
      {
        "tab": "Tutorials",
        "groups": [
          {
            "group": "Beginner",
            "pages": ["tutorial-1", "tutorial-2"]
          }
        ]
      }
    ]
  }
}
```

### 4. Global Navigation Component

**Location**: `docs.json` → `navigation.global` object (lines 66-77)

**Purpose**: Defines navigation elements that appear across all pages, independent of tab selection.

#### Implementation

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

#### Anchor Subcomponent

**Properties**:
- `anchor` (string): Display text for the link
- `href` (string): Destination URL (external links)
- `icon` (string): Icon identifier from Mintlify's icon library

**Actual Anchors** (lines 68-76):

1. **Documentation Anchor**:
   - Text: "Documentation"
   - URL: https://mintlify.com/docs
   - Icon: `book-open-cover`

2. **Blog Anchor**:
   - Text: "Blog"
   - URL: https://mintlify.com/blog
   - Icon: `newspaper`

#### Usage

Add custom global links:
```json
{
  "global": {
    "anchors": [
      {
        "anchor": "Support",
        "href": "https://support.yoursite.com",
        "icon": "life-ring"
      },
      {
        "anchor": "GitHub",
        "href": "https://github.com/yourorg/yourrepo",
        "icon": "github"
      }
    ]
  }
}
```

### 5. Logo Component

**Location**: `docs.json` → `logo` object (lines 78-81)

**Purpose**: Defines logo images for light and dark theme modes, enabling automatic theme-aware logo switching.

#### Implementation

```json
{
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

**Properties**:
- `light` (string): Path to logo for light mode. Value: `"/logo/light.svg"`
- `dark` (string): Path to logo for dark mode. Value: `"/logo/dark.svg"`

**File Requirements**:
- Logo files must exist at specified paths
- SVG format recommended for scalability
- Paths are relative to project root
- Both variants required for proper theme switching

#### Usage

**Replace with Custom Logos**:

1. Create logo directory structure:
   ```
   project-root/
   ├── logo/
   │   ├── light.svg
   │   └── dark.svg
   ```

2. Place your logo files in the directory

3. Verify paths in `docs.json`:
   ```json
   {
     "logo": {
       "light": "/logo/light.svg",
       "dark": "/logo/dark.svg"
     }
   }
   ```

**Using Different Paths**:
```json
{
  "logo": {
    "light": "/assets/images/logo-light.svg",
    "dark": "/assets/images/logo-dark.svg"
  }
}
```

**Design Recommendations**:
- Keep both logos visually consistent
- Ensure sufficient contrast with background
- Typical dimensions: 120-200px width, 30-50px height
- Export as SVG for best quality across devices

### 6. Navbar Component

**Location**: `docs.json` → `navbar` object (lines 82-92)

**Purpose**: Configures the top navigation bar with custom links and a primary action button.

#### Implementation

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

#### Link Subcomponent

**Properties**:
- `label` (string): Display text for the link
- `href` (string): Destination URL or mailto link

**Actual Link** (lines 84-87):
- Label: "Support"
- Href: `mailto:hi@mintlify.com`

#### Primary Button Subcomponent

**Properties**:
- `type` (string): Component type. Value: `"button"`
- `label` (string): Button text. Value: `"Dashboard"`
- `href` (string): Destination URL. Value: `"https://dashboard.mintlify.com"`

**Implementation** (lines 88-92):
```json
{
  "primary": {
    "type": "button",
    "label": "Dashboard",
    "href": "https://dashboard.mintlify.com"
  }
}
```

#### Usage

**Multiple Navbar Links**:
```json
{
  "navbar": {
    "links": [
      {
        "label": "Support",
        "href": "mailto:support@yoursite.com"
      },
      {
        "label": "Status",
        "href": "https://status.yoursite.com"
      },
      {
        "label": "Community",
        "href": "https://community.yoursite.com"
      }
    ]
  }
}
```

**Customizing Primary Button**:
```json
{
  "navbar": {
    "primary": {
      "type": "button",
      "label": "Get Started",
      "href": "https://app.yoursite.com/signup"
    }
  }
}
```

### 7. Contextual Menu Component

**Location**: `docs.json` → `contextual` object (lines 93-104)

**Purpose**: Enables contextual actions and integrations with AI tools and development environments, appearing as right-click or contextual menu options on code blocks and content.

#### Implementation

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
- `options` (array of strings): List of enabled contextual actions

**Available Options** (lines 95-103):

1. **copy**: Copy code to clipboard
2. **view**: View full source or context
3. **chatgpt**: Open content in ChatGPT
4. **claude**: Open content in Claude AI
5. **perplexity**: Open content in Perplexity AI
6. **mcp**: Model Context Protocol integration
7. **cursor**: Open in Cursor editor
8. **vscode**: Open in Visual Studio Code

#### Usage

**Enable Specific Options Only**:
```json
{
  "contextual": {
    "options": [
      "copy",
      "view",
      "vscode"
    ]
  }
}
```

**Enable All AI Integrations**:
```json
{
  "contextual": {
    "options": [
      "copy",
      "chatgpt",
      "claude",
      "perplexity"
    ]
  }
}
```

**Developer-Focused Configuration**:
```json
{
  "contextual": {
    "options": [
      "copy",
      "view",
      "cursor",
      "vscode",
      "mcp"
    ]
  }
}
```

**Behavior**:
- Options appear when users interact with code blocks
- Right-click or designated gesture triggers contextual menu
- Each option executes its specific action (copy, open in tool, etc.)
- Not all options may be available depending on user's environment

### 8. Footer Component

**Location**: `docs.json` → `footer` object (lines 105-111)

**Purpose**: Configures the site footer with social media links and additional information.

#### Implementation

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
- `socials` (object): Key-value pairs mapping social platform to URL

**Actual Social Links** (lines 107-110):

| Platform | URL |
|----------|-----|
| X (Twitter) | https://x.com/mintlify |
| GitHub | https://github.com/mintlify |
| LinkedIn | https://linkedin.com/company/mintlify |

#### Usage

**Add More Social Platforms**:
```json
{
  "footer": {
    "socials": {
      "x": "https://x.com/yourhandle",
      "github": "https://github.com/yourorg",
      "linkedin": "https://linkedin.com/company/yourcompany",
      "discord": "https://discord.gg/yourinvite",
      "youtube": "https://youtube.com/@yourchannel",
      "slack": "https://yourworkspace.slack.com"
    }
  }
}
```

**Supported Social Platforms**:
- x (Twitter/X)
- github
- linkedin
- discord
- youtube
- slack
- facebook
- instagram
- medium
- (others supported by Mintlify)

**Minimal Configuration**:
```json
{
  "footer": {
    "socials": {
      "github": "https://github.com/yourorg/yourrepo"
    }
  }
}
```

## API Specification Components

### 9. OpenAPI Configuration

**Location**: `api-reference/openapi.json`

**Purpose**: Defines the API structure using OpenAPI 3.1.0 specification, enabling automatic generation of interactive API documentation.

#### Overview

The OpenAPI specification provides a complete, machine-readable definition of the Plant Store API, including endpoints, request/response schemas, authentication requirements, and webhooks.

#### Implementation

**Root Configuration** (lines 1-9):
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

**Properties**:
- `openapi`: Specification version (`"3.1.0"`)
- `info.title`: API title (`"OpenAPI Plant Store"`)
- `info.description`: API description
- `info.license.name`: License type (`"MIT"`)
- `info.version`: API version (`"1.0.0"`)

#### Usage

**Customize API Metadata**:
```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "Your API Name",
    "description": "Description of your API's purpose and capabilities",
    "license": {
      "name": "Apache 2.0"
    },
    "version": "2.0.0"
  }
}
```

### 10. Server Configuration Component

**Location**: `api-reference/openapi.json` → `servers` (lines 10-13)

**Purpose**: Defines API server endpoints where the API is accessible.

#### Implementation

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
- `url` (string): Base URL for all API endpoints

**Actual Server**: `http://sandbox.mintlify.com`

#### Usage

**Multiple Environments**:
```json
{
  "servers": [
    {
      "url": "https://api.production.com",
      "description": "Production server"
    },
    {
      "url": "https://api.staging.com",
      "description": "Staging server"
    },
    {
      "url": "http://localhost:3000",
      "description": "Local development"
    }
  ]
}
```

**Server Variables**:
```json
{
  "servers": [
    {
      "url": "https://{environment}.yourapi.com",
      "variables": {
        "environment": {
          "default": "api",
          "enum": ["api", "api.staging", "api.dev"]
        }
      }
    }
  ]
}
```

### 11. Security Configuration Component

**Location**: `api-reference/openapi.json` → `security` and `components.securitySchemes`

**Purpose**: Defines authentication requirements for the API.

#### Implementation

**Global Security Requirement** (lines 14-18):
```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Security Scheme Definition** (lines 175-179):
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
- `type`: Authentication type (`"http"`)
- `scheme`: HTTP authentication scheme (`"bearer"`)

#### Usage

**API Key Authentication**:
```json
{
  "security": [
    {
      "apiKey": []
    }
  ],
  "components": {
    "securitySchemes": {
      "apiKey": {
        "type": "apiKey",
        "in": "header",
        "name": "X-API-Key"
      }
    }
  }
}
```

**OAuth 2.0 Authentication**:
```json
{
  "security": [
    {
      "oauth2": ["read", "write"]
    }
  ],
  "components": {
    "securitySchemes": {
      "oauth2": {
        "type": "oauth2",
        "flows": {
          "authorizationCode": {
            "authorizationUrl": "https://auth.yourapi.com/oauth/authorize",
            "tokenUrl": "https://auth.yourapi.com/oauth/token",
            "scopes": {
              "read": "Read access",
              "write": "Write access"
            }
          }
        }
      }
    }
  }
}
```

### 12. Path Component (API Endpoints)

**Location**: `api-reference/openapi.json` → `paths`

**Purpose**: Defines individual API endpoints with their operations, parameters, and responses.

#### GET /plants Endpoint Component

**Implementation** (lines 19-56):
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

**Structure**:
- **Path**: `/plants`
- **Method**: `get`
- **Parameters**: `limit` (optional query parameter, integer)
- **Response 200**: Array of Plant objects
- **Response 400**: Error object

#### POST /plants Endpoint Component

**Implementation** (lines 57-88):
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

**Structure**:
- **Path**: `/plants`
- **Method**: `post`
- **Request Body**: NewPlant object (required)
- **Response 200**: Created Plant object
- **Response 400**: Error object

#### DELETE /plants/{id} Endpoint Component

**Implementation** (lines 89-127):
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

**Structure**:
- **Path**: `/plants/{id}`
- **Method**: `delete`
- **Parameters**: `id` (required path parameter, integer)
- **Response 204**: No content (success)
- **Response 400**: Error object

#### Usage

**Add New Endpoint**:
```json
{
  "paths": {
    "/plants/{id}": {
      "get": {
        "description": "Get a single plant by ID",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "required": true,
            "schema": {
              "type": "integer",
              "format": "int64"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Successful response",
            "content": {
              "application/json": {
                "schema": {
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

### 13. Webhook Component

**Location**: `api-reference/openapi.json` → `webhooks` (lines 128-151)

**Purpose**: Defines webhook notifications that the API sends to external systems.

#### Implementation

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

**Structure**:
- **Webhook Path**: `/plant/webhook`
- **Method**: `post`
- **Request Body**: NewPlant schema
- **Expected Response**: 200 status code

#### Usage

Configure your endpoint to receive webhook:

```json
{
  "webhooks": {
    "/inventory/update": {
      "post": {
        "description": "Notification when inventory changes",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "event": {
                    "type": "string",
                    "enum": ["created", "updated", "deleted"]
                  },
                  "item_id": {
                    "type": "integer"
                  },
                  "timestamp": {
                    "type": "string",
                    "format": "date-time"
                  }
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

### 14. Schema Components

**Location**: `api-reference/openapi.json` → `components.schemas`

**Purpose**: Defines reusable data models used throughout the API specification.

#### Plant Schema Component

**Implementation** (lines 153-164):
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
- `name` (string, required): Plant name
- `tag` (string, optional): Type classification

#### NewPlant Schema Component

**Implementation** (lines 165-180):
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

**Structure**:
- Extends Plant schema using `allOf`
- Adds required `id` property (integer, int64)

#### Error Schema Component

**Implementation** (lines 181-194):
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
- `error` (integer, required): Error code
- `message` (string, required): Error message

#### Usage

**Define Custom Schema**:
```json
{
  "components": {