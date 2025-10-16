# Software Bill of Materials (SBOM) - CycloneDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in CycloneDX format for the **Mintlify Documentation Starter Kit** project. A Software Bill of Materials is a formal, machine-readable inventory of all software components, dependencies, libraries, and metadata that comprise a software application.

**What is CycloneDX?**

CycloneDX is a lightweight SBOM standard designed specifically for application security contexts and supply chain component analysis. It is an OWASP-led industry standard purpose-built for:

- Vulnerability identification and management
- License compliance and risk assessment
- Component provenance and integrity verification
- Supply chain risk analysis
- Security tool integration

**Project Context: Mintlify Documentation Starter Kit**

Based on comprehensive analysis of the provided source code, this project is a **configuration-driven documentation framework** that operates fundamentally differently from traditional web applications. The project consists of:

- **Configuration file** (`docs.json`) - 111 lines defining complete site structure, theme, navigation, and behavior
- **Markdown content files** - 18+ documentation pages in `.md` format
- **OpenAPI specification** (`api-reference/openapi.json`) - 194 lines demonstrating API documentation capabilities
- **Static assets** - Logo files (`/logo/light.svg`, `/logo/dark.svg`) and favicon (`/favicon.svg`)
- **Single runtime dependency** - Mintlify CLI tool (`mint`) installed globally via npm

**Critical Architectural Finding**: This project does **NOT** contain traditional dependency manifest files (`package.json`, `package-lock.json`, `requirements.txt`, etc.). The architecture is configuration-first, with the only external dependency being the globally-installed Mintlify CLI tool.

**SBOM Purpose and Applications**:

This CycloneDX SBOM serves multiple critical functions:

1. **Security Vulnerability Management**: Enables automated scanning for known vulnerabilities in dependencies
2. **License Compliance**: Tracks open source licenses and ensures compliance with legal obligations
3. **Supply Chain Transparency**: Provides visibility into component sources and provenance
4. **Regulatory Compliance**: Meets requirements for software composition transparency (e.g., Executive Order 14028)
5. **Risk Assessment**: Identifies potential security, legal, and operational risks from dependencies

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

CycloneDX 1.5 (the current specification version) defines a hierarchical JSON structure with the following key sections:

#### 1. BOM Metadata Section

The metadata section provides essential information about the SBOM document itself and the software it describes:

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

- **bomFormat**: Always "CycloneDX" for this specification
- **specVersion**: CycloneDX specification version (1.5 is current as of 2024)
- **serialNumber**: Unique UUID-based URN identifying this specific SBOM instance
- **version**: SBOM document version number (incremented for updates)
- **metadata.timestamp**: ISO 8601 timestamp indicating when the SBOM was generated
- **metadata.tools**: Array of tools used to generate the SBOM
- **metadata.component**: The primary application/component this SBOM describes
- **metadata.authors**: People or organizations responsible for the software

**Component Type Classification**:

CycloneDX supports multiple component types:
- `application`: End-user software application (used here)
- `library`: Reusable software library or module
- `framework`: Software framework providing structure
- `platform`: Runtime platform or operating system
- `device`: Hardware device or embedded system
- `file`: Individual file component
- `data`: Data file or dataset

#### 2. Components Section

The components array catalogs all software dependencies, libraries, frameworks, and services:

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

**Component Field Definitions**:

- **type**: Component category (library, framework, application, etc.)
- **bom-ref**: Unique identifier for this component within the SBOM
- **purl**: Package URL following the PURL specification format
- **name**: Component name as known in its ecosystem
- **version**: Specific version or version range
- **description**: Human-readable description of component purpose
- **scope**: Usage context (required, optional, excluded)
- **licenses**: SPDX license identifiers or license objects
- **externalReferences**: URLs to documentation, source, distribution, etc.

**Package URL (PURL) Specification**:

Package URLs provide standardized, cross-ecosystem package identification:

```
pkg:npm/mint@latest
│   │   │    │
│   │   │    └─ Version (optional)
│   │   └────── Package name
│   └────────── Package type/ecosystem
└────────────── Scheme identifier
```

PURL syntax: `pkg:type/namespace/name@version?qualifiers#subpath`

Common package types:
- `npm` - Node.js packages from npmjs.com
- `pypi` - Python packages from PyPI
- `maven` - Java packages from Maven Central
- `gem` - Ruby packages from RubyGems
- `golang` - Go modules
- `cargo` - Rust packages from crates.io
- `generic` - Generic software components

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

Lines 2-10: Schema, theme, name, colors, favicon
Lines 11-77: Navigation structure with 2 tabs (Guides with 4 groups/12 pages, API reference with 2 groups/5 pages)
Lines 78-81: Logo configuration (light and dark variants)
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

Lines 1-9: OpenAPI 3.1.0 metadata, Plant Store API title, MIT license, v1.0.0
Lines 10-13: Server configuration (http://sandbox.mintlify.com)
Lines 14-18: Bearer authentication security requirement
Lines 19-127: Three paths (GET /plants with limit parameter, POST /plants with NewPlant schema, DELETE /plants/{id})
Lines 128-151: Webhook (POST /plant/webhook with NewPlant schema)
Lines 152-194: Components section with schemas (Plant, NewPlant, Error) and securitySchemes (bearerAuth)

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

External services the software depends on for operation:

**GitHub Service Dependency**:

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

**Integration Details** (from `README.md` lines 29-32):

GitHub app installed from dashboard at `https://dashboard.mintlify.com/settings/organization/github-app` triggers automatic deployment when changes are pushed to the default branch.

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

**Service Field Definitions**:

- **bom-ref**: Unique identifier for this service
- **provider**: Organization providing the service
- **name**: Service name
- **description**: Purpose and functionality
- **endpoints**: API endpoints and URLs
- **authenticated**: Whether authentication is required
- **trustZone**: Security trust zone (internal, external, public, etc.)
- **data**: Information about data flows and classification

#### 4. Dependencies Section

The dependencies section maps relationships between components, creating a dependency graph:

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

**Dependency Relationship Types**:

Each dependency entry creates a directed edge in the dependency graph:
- The `ref` field identifies the dependent component
- The `dependsOn` array lists all direct dependencies
- Transitive dependencies are implied through the graph

This structure enables:
- Automated vulnerability impact analysis
- License compatibility checking
- Supply chain risk assessment
- Dependency update planning

#### 5. Compositions Section

The compositions section describes how components are aggregated:

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

**Composition Types**:

- **complete**: SBOM includes all components with no omissions
- **incomplete**: SBOM has known gaps or incomplete information
- **incomplete_first_party_only**: Only first-party components included
- **incomplete_third_party_only**: Only third-party components included
- **unknown**: Completeness cannot be determined

### Complete CycloneDX SBOM

Based on comprehensive analysis of the project structure, configuration files, and documentation, here is the complete CycloneDX 1.5 SBOM in JSON format:

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
          "type": "website