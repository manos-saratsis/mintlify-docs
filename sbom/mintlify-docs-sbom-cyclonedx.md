# Software Bill of Materials (SBOM) - CycloneDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in CycloneDX format for the **Mintlify Documentation Starter Kit** project. A Software Bill of Materials is a formal, machine-readable inventory of all software components, dependencies, libraries, and metadata that comprise a software application.

**What is CycloneDX?**

CycloneDX is a lightweight SBOM standard designed for use in application security contexts and supply chain component analysis. It is an OWASP-led industry standard specifically purpose-built for:

- Vulnerability identification and management
- License compliance and risk assessment  
- Component provenance and integrity verification
- Supply chain risk analysis
- Security tool integration

**Project Context: Mintlify Documentation Starter Kit**

Based on comprehensive analysis of the provided source code, this project is a **configuration-driven documentation framework** that operates fundamentally differently from traditional web applications. The project consists of:

- **Configuration file** (`docs.json` - 111 lines) defining complete site structure, theme, navigation, and behavior
- **Markdown content files** (14 files) providing documentation text
- **OpenAPI specification** (`api-reference/openapi.json` - 194 lines) demonstrating API documentation capabilities
- **Static assets** (logos in `/logo/` directory, favicon at `/favicon.svg`)
- **Single runtime dependency**: Mintlify CLI (`mint`) installed globally via npm

**Critical Finding**: This project does **NOT** contain traditional dependency manifest files (`package.json`, `package-lock.json`, etc.). The architecture is configuration-first, with no application code, frameworks, or runtime libraries in the traditional sense.

**SBOM Applications**:

1. **Security Vulnerability Management**: Automated scanning for known vulnerabilities
2. **License Compliance**: Tracking open source licenses and legal obligations
3. **Supply Chain Transparency**: Visibility into component sources and provenance
4. **Regulatory Compliance**: Meeting software composition transparency requirements
5. **Risk Assessment**: Identifying security, legal, and operational risks

## Implementation

### Project Structure Analysis

The Mintlify Documentation Starter Kit follows this directory structure:

```
mintlify-starter-kit/
├── docs.json                      # Primary configuration (111 lines)
├── README.md                      # Setup instructions
├── favicon.svg                    # Site favicon
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── api-reference/
│   ├── openapi.json              # OpenAPI 3.1.0 spec (194 lines)
│   ├── introduction.md           # API docs introduction
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
├── api-docs.md
├── architecture.md
├── component-docs.md
├── concepts.md
├── feature-guides.md
├── getting-started.md
├── how_to.md
├── intro.md
├── reference.md
├── sbom-cyclonedx.md
├── sbom-spdx.md
├── sbom_cyclonedx.md
├── sbom_spdx.md
└── tutorials.md
```

**File Type Distribution**:
- Configuration: 1 JSON file (`docs.json`)
- API Specification: 1 JSON file (`openapi.json`)
- Documentation: 18 Markdown files
- Assets: 3 SVG files (logos and favicon)

### CycloneDX Document Structure (Version 1.5)

The CycloneDX 1.5 specification defines a hierarchical JSON structure for documenting software composition.

#### 1. BOM Metadata Section

The metadata section provides information about the SBOM document and the software it describes:

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "serialNumber": "urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79",
  "version": 1,
  "metadata": {
    "timestamp": "2024-01-15T10:30:00Z",
    "tools": [
      {
        "vendor": "OWASP",
        "name": "CycloneDX Documentation Generator",
        "version": "1.5.0",
        "externalReferences": [
          {
            "type": "website",
            "url": "https://cyclonedx.org"
          }
        ]
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:generic/mintlify-docs@1.0.0",
      "name": "Mintlify Documentation Starter Kit",
      "version": "1.0.0",
      "description": "A documentation starter kit using Mintlify for creating beautiful, searchable documentation sites with guide pages, navigation, customizations, API reference capabilities, and OpenAPI integration",
      "licenses": [
        {
          "license": {
            "id": "NOASSERTION"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://mintlify.com"
        },
        {
          "type": "documentation",
          "url": "https://mintlify.com/docs"
        },
        {
          "type": "vcs",
          "url": "https://github.com/mintlify/starter"
        }
      ]
    },
    "authors": [
      {
        "name": "Mintlify Team",
        "email": "hi@mintlify.com"
      }
    ]
  }
}
```

**Field Definitions**:

- **bomFormat**: Always "CycloneDX"
- **specVersion**: CycloneDX version (1.5 is current)
- **serialNumber**: Unique UUID-based URN for this SBOM instance
- **version**: SBOM document version (incremented for updates)
- **metadata.timestamp**: ISO 8601 timestamp of SBOM generation
- **metadata.tools**: Tools used to generate the SBOM
- **metadata.component**: Primary application this SBOM describes
- **metadata.authors**: People/organizations responsible for the software

#### 2. Components Section

The components array catalogs all dependencies and component packages:

**Primary Dependency: Mintlify CLI**

```json
{
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/mint@latest",
      "purl": "pkg:npm/mint",
      "name": "mint",
      "version": "latest",
      "description": "Mintlify CLI for previewing documentation changes locally and managing documentation deployments. Provides live development server with hot reload capabilities.",
      "scope": "required",
      "licenses": [
        {
          "license": {
            "id": "NOASSERTION"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://mintlify.com"
        },
        {
          "type": "distribution",
          "url": "https://www.npmjs.com/package/mint"
        },
        {
          "type": "documentation",
          "url": "https://mintlify.com/docs"
        },
        {
          "type": "vcs",
          "url": "https://github.com/mintlify/mint"
        }
      ],
      "properties": [
        {
          "name": "installation-method",
          "value": "global-npm"
        },
        {
          "name": "installation-command",
          "value": "npm i -g mint"
        },
        {
          "name": "development-command",
          "value": "mint dev"
        },
        {
          "name": "update-command",
          "value": "mint update"
        },
        {
          "name": "default-port",
          "value": "3000"
        }
      ]
    }
  ]
}
```

**Installation Context** (from `README.md` lines 18-27):

The Mintlify CLI is installed globally outside the project directory:

```bash
npm i -g mint
```

Used for local development:

```bash
mint dev
```

Accessed at `http://localhost:3000`.

**Configuration Component**:

```json
{
  "type": "data",
  "bom-ref": "config:docs-json",
  "name": "docs.json",
  "version": "1.0.0",
  "description": "Primary configuration file (111 lines) defining site structure, theme, colors, navigation hierarchy, logo references, navbar configuration, contextual options, and footer social links",
  "scope": "required",
  "properties": [
    {
      "name": "schema",
      "value": "https://mintlify.com/docs.json"
    },
    {
      "name": "theme",
      "value": "mint"
    },
    {
      "name": "colors-primary",
      "value": "#16A34A"
    },
    {
      "name": "colors-light",
      "value": "#07C983"
    },
    {
      "name": "colors-dark",
      "value": "#15803D"
    },
    {
      "name": "navigation-tabs",
      "value": "2"
    },
    {
      "name": "navigation-groups",
      "value": "6"
    },
    {
      "name": "navigation-pages",
      "value": "17"
    },
    {
      "name": "global-anchors",
      "value": "2"
    },
    {
      "name": "contextual-options",
      "value": "8"
    },
    {
      "name": "social-links",
      "value": "3"
    }
  ]
}
```

**Configuration Details** (from `docs.json`):

Lines 2-9: Schema, theme, name, colors, favicon
Lines 11-77: Navigation structure with tabs, groups, pages
Lines 78-81: Logo configuration
Lines 82-92: Navbar links and primary button
Lines 93-104: Contextual options (copy, view, chatgpt, claude, perplexity, mcp, cursor, vscode)
Lines 105-111: Footer social links (x, github, linkedin)

**OpenAPI Specification Component**:

```json
{
  "type": "data",
  "bom-ref": "spec:openapi",
  "name": "OpenAPI Plant Store Specification",
  "version": "3.1.0",
  "description": "Sample OpenAPI 3.1.0 specification (194 lines) demonstrating API documentation features. Defines plant store API with GET /plants, POST /plants, DELETE /plants/{id} endpoints, webhook integration, bearer authentication, and three schemas (Plant, NewPlant, Error)",
  "scope": "optional",
  "licenses": [
    {
      "license": {
        "id": "MIT"
      }
    }
  ],
  "properties": [
    {
      "name": "openapi-version",
      "value": "3.1.0"
    },
    {
      "name": "api-title",
      "value": "OpenAPI Plant Store"
    },
    {
      "name": "api-version",
      "value": "1.0.0"
    },
    {
      "name": "server-url",
      "value": "http://sandbox.mintlify.com"
    },
    {
      "name": "security-scheme",
      "value": "bearerAuth"
    },
    {
      "name": "endpoints-count",
      "value": "3"
    },
    {
      "name": "webhooks-count",
      "value": "1"
    },
    {
      "name": "schemas-count",
      "value": "3"
    }
  ],
  "externalReferences": [
    {
      "type": "specification",
      "url": "https://spec.openapis.org/oas/v3.1.0"
    },
    {
      "type": "documentation",
      "url": "https://swagger.io/specification/"
    }
  ]
}
```

**OpenAPI Details** (from `api-reference/openapi.json`):

Lines 1-9: OpenAPI 3.1.0 metadata, Plant Store API
Lines 10-13: Server configuration (http://sandbox.mintlify.com)
Lines 14-18: Bearer authentication security
Lines 19-127: Three paths (GET /plants, POST /plants, DELETE /plants/{id})
Lines 128-151: Webhook (POST /plant/webhook)
Lines 152-194: Schemas (Plant, NewPlant, Error) and security schemes

**Platform Dependency: Node.js**:

```json
{
  "type": "platform",
  "bom-ref": "platform:nodejs",
  "name": "Node.js",
  "description": "JavaScript runtime environment required for executing Mintlify CLI. Provides npm package manager for CLI installation.",
  "scope": "required",
  "licenses": [
    {
      "license": {
        "id": "MIT"
      }
    }
  ],
  "externalReferences": [
    {
      "type": "website",
      "url": "https://nodejs.org"
    },
    {
      "type": "documentation",
      "url": "https://nodejs.org/docs"
    },
    {
      "type": "vcs",
      "url": "https://github.com/nodejs/node"
    }
  ],
  "properties": [
    {
      "name": "runtime-type",
      "value": "javascript"
    },
    {
      "name": "package-manager",
      "value": "npm"
    }
  ]
}
```

#### 3. Services Section

External services the software depends on:

**GitHub Service**:

```json
{
  "services": [
    {
      "bom-ref": "service:github",
      "provider": {
        "name": "GitHub, Inc.",
        "url": ["https://github.com"]
      },
      "name": "GitHub",
      "description": "Version control platform providing repository hosting, version control, and automatic deployment integration via GitHub app. Deployment triggers automatically on push to default branch.",
      "endpoints": [
        "https://github.com",
        "https://api.github.com"
      ],
      "authenticated": true,
      "x-trust-boundary": true,
      "trustZone": "external",
      "data": [
        {
          "flow": "bi-directional",
          "classification": "public"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://github.com"
        },
        {
          "type": "documentation",
          "url": "https://docs.github.com"
        }
      ],
      "properties": [
        {
          "name": "integration-type",
          "value": "github-app"
        },
        {
          "name": "deployment-trigger",
          "value": "push-to-default-branch"
        },
        {
          "name": "dashboard-url",
          "value": "https://dashboard.mintlify.com/settings/organization/github-app"
        }
      ]
    }
  ]
}
```

**Integration Details** (from `README.md` lines 28-32):

GitHub app installed from dashboard triggers automatic deployment when changes are pushed to the default branch.

**Mintlify Platform Service**:

```json
{
  "bom-ref": "service:mintlify-platform",
  "provider": {
    "name": "Mintlify",
    "url": ["https://mintlify.com"]
  },
  "name": "Mintlify Platform",
  "description": "Documentation hosting and deployment service providing automatic builds from GitHub, CDN delivery, search indexing, and production hosting infrastructure. Handles parsing of docs.json, processing of markdown content, generation of static HTML, and CDN deployment.",
  "endpoints": [
    "https://dashboard.mintlify.com",
    "https://api.mintlify.com"
  ],
  "authenticated": true,
  "x-trust-boundary": true,
  "trustZone": "external",
  "data": [
    {
      "flow": "bi-directional",
      "classification": "public"
    }
  ],
  "externalReferences": [
    {
      "type": "website",
      "url": "https://dashboard.mintlify.com"
    },
    {
      "type": "documentation",
      "url": "https://mintlify.com/docs"
    },
    {
      "type": "other",
      "url": "https://mintlify.com/blog"
    }
  ],
  "properties": [
    {
      "name": "deployment-method",
      "value": "automatic-github-integration"
    },
    {
      "name": "build-trigger",
      "value": "git-push"
    },
    {
      "name": "hosting-type",
      "value": "cdn"
    },
    {
      "name": "search-provider",
      "value": "mintlify-search"
    }
  ]
}
```

#### 4. Dependencies Section

Dependency relationships between components:

```json
{
  "dependencies": [
    {
      "ref": "pkg:generic/mintlify-docs@1.0.0",
      "dependsOn": [
        "pkg:npm/mint@latest",
        "config:docs-json",
        "platform:nodejs",
        "service:github",
        "service:mintlify-platform"
      ]
    },
    {
      "ref": "pkg:npm/mint@latest",
      "dependsOn": [
        "platform:nodejs"
      ]
    },
    {
      "ref": "config:docs-json",
      "dependsOn": []
    },
    {
      "ref": "spec:openapi",
      "dependsOn": []
    },
    {
      "ref": "platform:nodejs",
      "dependsOn": []
    },
    {
      "ref": "service:github",
      "dependsOn": []
    },
    {
      "ref": "service:mintlify-platform",
      "dependsOn": []
    }
  ]
}
```

#### 5. Compositions Section

Component aggregation:

```json
{
  "compositions": [
    {
      "aggregate": "complete",
      "assemblies": [
        "pkg:generic/mintlify-docs@1.0.0"
      ],
      "dependencies": [
        "pkg:npm/mint@latest",
        "config:docs-json",
        "spec:openapi",
        "platform:nodejs"
      ]
    }
  ]
}
```

### Complete CycloneDX SBOM

Complete CycloneDX 1.5 SBOM for Mintlify Documentation Starter Kit:

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "serialNumber": "urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79",
  "version": 1,
  "metadata": {
    "timestamp": "2024-01-15T10:30:00Z",
    "tools": [
      {
        "vendor": "OWASP",
        "name": "CycloneDX Documentation Generator",
        "version": "1.5.0",
        "externalReferences": [
          {
            "type": "website",
            "url": "https://cyclonedx.org"
          }
        ]
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:generic/mintlify-docs@1.0.0",
      "name": "Mintlify Documentation Starter Kit",
      "version": "1.0.0",
      "description": "A documentation starter kit using Mintlify for creating beautiful, searchable documentation sites with guide pages, navigation, customizations, API reference capabilities, and OpenAPI integration",
      "licenses": [
        {
          "license": {
            "id": "NOASSERTION"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://mintlify.com"
        },
        {
          "type": "documentation",
          "url": "https://mintlify.com/docs"
        },
        {
          "type": "vcs",
          "url": "https://github.com/mintlify/starter"
        }
      ]
    },
    "authors": [
      {
        "name": "Mintlify Team",
        "email": "hi@mintlify.com"
      }
    ]
  },
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/mint@latest",
      "purl": "pkg:npm/mint",
      "name": "mint",
      "version": "latest",
      "description": "Mintlify CLI for previewing documentation changes locally and managing documentation deployments. Provides live development server with hot reload capabilities.",
      "scope": "required",
      "licenses": [
        {
          "license": {
            "id": "NOASSERTION"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://mintlify.com"
        },
        {
          "type": "distribution",
          "url": "https://www.npmjs.com/package/mint"
        },
        {
          "type": "documentation",
          "url": "https://mintlify.com/docs"
        },
        {
          "type": "vcs",
          "url": "https://github.com/mintlify/mint"
        }
      ],
      "properties": [
        {
          "name": "installation-method",
          "value": "global-npm"
        },
        {
          "name": "installation-command",
          "value": "npm i -g mint"
        },
        {
          "name": "development-command",
          "value": "mint dev"
        },
        {
          "name": "update-command",
          "value": "mint update"
        },
        {
          "name": "default-port",
          "value": "3000"
        }
      ]
    },
    {
      "type": "data",
      "bom-ref": "config:docs-json",
      "name": "docs.json",
      "version": "1.0.0",
      "description": "Primary configuration file (111 lines) defining site structure, theme, colors, navigation hierarchy, logo references, navbar configuration, contextual options, and footer social links",
      "scope": "required",
      "properties": [
        {
          "name": "schema",
          "value": "https://mintlify.com/docs.json"
        },
        {
          "name": "theme",
          "value": "mint"
        },
        {
          "name": "colors-primary",
          "value": "#16A34A"
        },
        {
          "name": "colors-light",
          "value": "#07C983"
        },
        {
          "name": "colors-dark",
          "value": "#15803D"
        },
        {
          "name": "navigation-tabs",
          "value": "2"
        },
        {
          "name": "navigation-groups",
          "value": "6"
        },
        {
          "name": "navigation-pages",
          "value": "17"
        },
        {
          "name": "global-anchors",
          "value": "2"
        },
        {
          "name": "contextual-options",
          "value": "8"
        },
        {
          "name": "social-links",
          "value": "3"
        }
      ]
    },
    {
      "type": "data",
      "bom-ref": "spec:openapi",
      "name": "OpenAPI Plant Store Specification",
      "version": "3.1.0",
      "description": "Sample OpenAPI 3.1.0 specification (194 lines) demonstrating API documentation features. Defines plant store API with GET /plants, POST /plants, DELETE /plants/{id} endpoints, webhook integration, bearer authentication, and three schemas (Plant, NewPlant, Error)",
      "scope": "optional",
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "openapi-version",
          "value": "3.1.0"
        },
        {
          "name": "api-title",
          "value": "OpenAPI Plant Store"
        },
        {
          "name": "api-version",
          "value": "1.0.0"
        },
        {
          "name": "server-url",
          "value": "http://sandbox.mintlify.com"
        },
        {
          "name": "security-scheme",
          "value": "bearerAuth"
        },
        {
          "name": "endpoints-count",
          "value": "3"
        },
        {
          "name": "webhooks-count",
          "value": "1"
        },
        {
          "name": "schemas-count",
          "value": "3"
        }
      ],
      "externalReferences": [
        {
          "type": "specification",
          "url": "https://spec.openapis.org/oas/v3.1.0"
        },
        {
          "type": "documentation",
          "url": "https://swagger.io/specification/"
        }
      ]
    },
    {
      "type": "platform",
      "bom-ref": "platform:nodejs",
      "name": "Node.js",
      "description": "JavaScript runtime environment required for executing Mintlify CLI. Provides npm package manager for CLI installation.",
      "scope": "required",
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://nodejs.org"
        },
        {
          "type": "documentation",
          "url": "https://nodejs.org/docs"
        },
        {
          "type": "vcs",
          "url": "https://github.com/nodejs/node"
        }
      ],
      "properties": [
        {
          "name": "runtime-type",
          "value": "javascript"
        },
        {
          "name": "package-manager",
          "value": "npm"
        }
      ]
    }
  ],
  "services": [
    {
      "bom-ref": "service:github",
      "provider": {
        "name": "GitHub, Inc.",
        "url": ["https://github.com"]
      },
      "name": "GitHub",
      "description": "Version control platform providing repository hosting, version control, and automatic deployment integration via GitHub app. Deployment triggers automatically on push to default branch.",
      "endpoints": [
        "https://github.com",
        "https://api.github.com"
      ],
      "authenticated": true,
      "x-trust-boundary": true,
      "trustZone": "external",
      "data": [
        {
          "flow": "bi-directional",
          "classification": "public"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://github.com"
        },
        {
          "type": "documentation",
          "url": "https://docs.github.com"
        }
      ],
      "properties": [
        {
          "name": "integration-type",
          "value": "github-app"
        },
        {
          "name": "deployment-trigger",
          "value": "push-to-default-branch"
        },
        {
          "name": "dashboard-url",
          "value": "https://dashboard.mintlify.com/settings/organization/github-app"
        }
      ]
    },
    {
      "bom-ref": "service:mintlify-platform",
      "provider": {
        "name": "Mintlify",
        "url": ["https://mintlify.com"]
      },
      "name": "Mintlify Platform",
      "description": "Documentation hosting and deployment service providing automatic builds from GitHub, CDN delivery, search indexing, and production hosting infrastructure. Handles parsing of docs.json, processing of markdown content, generation of static HTML, and CDN deployment.",
      "endpoints": [
        "https://dashboard.mintlify.com",
        "https://api.mintlify.com"
      ],
      "authenticated": true,
      "x-trust-boundary": true,
      "trustZone": "external",
      "data": [
        {
          "flow": "bi-directional",
          "classification": "public"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://dashboard.mintlify.com"
        },
        {
          "type": "documentation",
          "url": "https://mintlify.com/docs"
        },
        {
          "type": "other",
          "url": "https://mintlify.com/blog"
        }
      ],
      "properties": [
        {
          "name": "deployment-method",
          "value": "automatic-github-integration"
        },
        {
          "name": "build-trigger",
          "value": "git-push"
        },
        {
          "name": "hosting-type",
          "value": "cdn"
        },
        {
          "name": "search-provider",
          "value": "mintlify-search"
        }
      ]
    }
  ],
  "dependencies": [
    {
      "ref": "pkg:generic/mintlify-docs@1.0.0",
      "dependsOn": [
        "pkg:npm/mint@latest",
        "config:docs-json",
        "platform:nodejs",
        "service:github",
        "service:mintlify-platform"
      ]
    },
    {
      "ref": "pkg:npm/mint@latest",
      "dependsOn": [
        "platform:nodejs"
      ]
    },
    {
      "ref": "config:docs-json",
      "dependsOn": []
    },
    {
      "ref": "spec:openapi",
      "dependsOn": []
    },
    {
      "ref": "platform:nodejs",
      "dependsOn": []
    },
    {
      "ref": "service:github",
      "dependsOn": []
    },
    {
      "ref": "service:mintlify-platform",
      "dependsOn": []
    }
  ],
  "compositions": [
    {
      "aggregate": "complete",
      "assemblies": [
        "pkg:generic/mintlify-docs@1.0.0"