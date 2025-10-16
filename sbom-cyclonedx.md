# Software Bill of Materials (SBOM) - CycloneDX Format

## Overview

This documentation provides a comprehensive Software Bill of Materials (SBOM) in CycloneDX format for the **Mintlify Documentation Starter Kit** project. A Software Bill of Materials is a formal, machine-readable inventory of all components, dependencies, libraries, and metadata that comprise a software application. The CycloneDX format is an OWASP-led industry standard specifically designed for application security contexts and software supply chain component analysis.

**What is CycloneDX?**

CycloneDX is a lightweight SBOM standard designed for use in application security contexts and supply chain component analysis. Unlike SPDX (which originated from license compliance needs), CycloneDX was purpose-built for security use cases including:

- Vulnerability identification and management
- License compliance and risk assessment
- Component provenance and integrity verification
- Supply chain risk analysis
- Security tool integration

**Project Context: Mintlify Documentation Starter Kit**

The Mintlify Documentation Starter Kit is a configuration-driven documentation framework that differs significantly from traditional web applications. Based on comprehensive analysis of the provided source code, this project consists primarily of:

- **Configuration file** (`docs.json`) defining site structure, theme, navigation, and behavior
- **Markdown content files** providing documentation text
- **OpenAPI specification** (`api-reference/openapi.json`) demonstrating API documentation capabilities
- **Static assets** (logos, favicon) for branding
- **Single runtime dependency** (Mintlify CLI tool installed globally via npm)

**Key Characteristic**: This project does **not** contain a traditional `package.json` or dependency manifest file within the project directory. The only external dependency is the Mintlify CLI (`mint`), installed globally via `npm i -g mint` (as documented in `README.md` line 18).

**SBOM Purpose and Applications**:

This CycloneDX SBOM serves multiple critical functions:

1. **Security Vulnerability Management**: Enables automated scanning for known vulnerabilities in dependencies
2. **License Compliance**: Tracks open source licenses and ensures compliance with legal obligations
3. **Supply Chain Transparency**: Provides visibility into component sources and provenance
4. **Regulatory Compliance**: Meets requirements for software composition transparency (e.g., Executive Order 14028)
5. **Risk Assessment**: Identifies potential security, legal, and operational risks from dependencies

## Implementation

### Project Structure Analysis

The Mintlify Documentation Starter Kit has a unique architecture optimized for documentation generation. Analysis of the provided source code reveals the following structure:

```
mintlify-documentation-starter-kit/
├── docs.json                      # Central configuration file (111 lines)
├── README.md                      # Setup and usage instructions
├── api-reference/
│   ├── introduction.md           # API documentation introduction
│   ├── openapi.json              # OpenAPI 3.1.0 specification (194 lines)
│   └── endpoint/
│       ├── get.md                # GET endpoint documentation
│       ├── create.md             # POST endpoint documentation
│       ├── delete.md             # DELETE endpoint documentation
│       └── webhook.md            # Webhook documentation
├── essentials/
│   ├── settings.md               # Settings documentation
│   ├── navigation.md             # Navigation configuration guide
│   ├── markdown.md               # Markdown usage guide
│   ├── code.md                   # Code block documentation
│   ├── images.md                 # Image usage guide
│   └── reusable-snippets.md     # Snippet documentation
├── ai-tools/
│   ├── cursor.md                 # Cursor editor integration
│   ├── claude-code.md            # Claude AI integration
│   └── windsurf.md               # Windsurf integration
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── favicon.svg                    # Site favicon
├── index.md                       # Homepage content
├── quickstart.md                  # Quick start guide
└── development.md                 # Development instructions
```

**Dependency Discovery Process**:

For traditional web applications, SBOM generation typically examines:
- `package.json` and `package-lock.json` (Node.js/JavaScript)
- `requirements.txt` or `Pipfile` (Python)
- `Gemfile` and `Gemfile.lock` (Ruby)
- `pom.xml` or `build.gradle` (Java)
- `go.mod` (Go)
- `Cargo.toml` (Rust)

**Critical Finding**: This project contains **none** of these standard dependency manifest files. The architecture is fundamentally different from typical applications, relying instead on:

1. **Global CLI Tool**: Mintlify CLI (`mint`) installed globally via npm
2. **Cloud Platform**: Mintlify hosting infrastructure for builds and deployment
3. **External Services**: GitHub for version control and deployment triggers
4. **Configuration**: `docs.json` defining all site behavior without code dependencies

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
        "version": "1.5.0"
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:generic/mintlify-docs@1.0.0",
      "name": "Mintlify Documentation Starter Kit",
      "version": "1.0.0",
      "description": "A documentation starter kit using Mintlify for creating beautiful, searchable documentation sites with guide pages, navigation, customizations, and API reference capabilities"
    },
    "authors": [
      {
        "name": "Mintlify Team"
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
      "description": "Mintlify CLI for previewing documentation changes locally and managing documentation deployments",
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
      ]
    }
  ]
}
```

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
  "description": "Primary configuration file defining navigation structure, theme colors, branding, and global settings for the documentation site",
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
    }
  ]
}
```

**OpenAPI Specification Component**:

```json
{
  "type": "data",
  "bom-ref": "spec:openapi",
  "name": "OpenAPI Plant Store Specification",
  "version": "3.1.0",
  "description": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features with plant store endpoints",
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
    }
  ]
}
```

**Platform Dependency: Node.js Runtime**:

```json
{
  "type": "platform",
  "bom-ref": "platform:nodejs",
  "name": "Node.js",
  "description": "JavaScript runtime environment required for executing Mintlify CLI",
  "scope": "required",
  "externalReferences": [
    {
      "type": "website",
      "url": "https://nodejs.org"
    },
    {
      "type": "documentation",
      "url": "https://nodejs.org/docs"
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
      "description": "Version control and deployment platform integrated via GitHub app",
      "endpoints": [
        "https://github.com",
        "https://api.github.com"
      ],
      "authenticated": true,
      "trustZone": "external",
      "data": [
        {
          "flow": "bi-directional",
          "classification": "public"
        }
      ],
      "externalReferences": [
        {
          "type": "documentation",
          "url": "https://docs.github.com"
        }
      ]
    }
  ]
}
```

**Mintlify Platform Service**:

```json
{
  "bom-ref": "service:mintlify-platform",
  "provider": {
    "name": "Mintlify",
    "url": ["https://mintlify.com"]
  },
  "name": "Mintlify Platform",
  "description": "Documentation hosting and deployment service providing automatic builds, CDN delivery, and search indexing",
  "endpoints": [
    "https://dashboard.mintlify.com",
    "https://api.mintlify.com"
  ],
  "authenticated": true,
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

#### 5. Compositions Section (Optional)

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

### Complete CycloneDX SBOM for Mintlify Documentation Starter Kit

Based on comprehensive analysis of the project structure, configuration files, and documentation, here is the complete CycloneDX 1.5 SBOM:

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

## Usage

### Generating CycloneDX SBOMs for Your Projects

This section provides comprehensive guidance on generating CycloneDX SBOMs for various project types, including documentation projects like this Mintlify starter kit and traditional software applications with extensive dependencies.

#### Tool Installation and Setup

**For Node.js/npm Projects**:

The CycloneDX Node.js module provides native support for npm-based projects:

```bash
# Install CycloneDX npm plugin globally
npm install -g @cyclonedx/cyclonedx-npm

# Verify installation
cyclonedx-npm --version
```

**For Multi-Ecosystem Projects**:

Syft is a powerful CLI tool that supports multiple package ecosystems and can detect dependencies across different languages:

```bash
# macOS installation via Homebrew
brew install syft

# Linux installation via script
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin

# Verify installation
syft version
```

**For Docker/Container Images**:

Trivy provides comprehensive scanning for containers and filesystems:

```bash
# macOS installation
brew install aquasecurity/trivy/trivy

# Ubuntu/Debian installation
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy

# Verify installation
trivy version
```

#### Generating SBOM from Standard Node.js Projects

For projects with `package.json` (unlike this Mintlify project):

```bash
# Navigate to project root
cd /path/to/your-project

# Generate CycloneDX SBOM in JSON format
cyclonedx-npm --output-format json --output-file cyclonedx-sbom.json

# Generate with specific options
cyclonedx-