# Software Bill of Materials (SBOM) - SPDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in SPDX 2.3 format for the **Mintlify Documentation Starter Kit** project. The SPDX (Software Package Data Exchange) format is an open standard (ISO/IEC 5962:2021) developed by the Linux Foundation for communicating software component information, including components, licenses, copyrights, security references, and supply chain provenance.

**What is SPDX?**

SPDX is a standardized format for documenting software components and their associated metadata. It was originally developed to facilitate license compliance but has evolved to support broader supply chain transparency, security vulnerability management, and regulatory compliance requirements. The SPDX specification is maintained by the Linux Foundation and is recognized internationally as ISO/IEC 5962:2021.

**Project Context: Mintlify Documentation Starter Kit**

Based on comprehensive analysis of the provided source code, this project is a **documentation framework** rather than a traditional software application with extensive dependencies. The project consists of:

- **Configuration file** (`docs.json`) - 111 lines defining complete site structure
- **Markdown content files** - Documentation pages in `.md` format
- **OpenAPI specification** (`api-reference/openapi.json`) - 194 lines demonstrating API documentation
- **Static assets** - Logo files (`/logo/light.svg`, `/logo/dark.svg`) and favicon (`/favicon.svg`)
- **Single runtime dependency** - Mintlify CLI tool (`mint`) installed globally via npm

**Critical Architectural Finding**: This project does **NOT** contain traditional dependency manifest files (`package.json`, `package-lock.json`, `requirements.txt`, etc.). The architecture is configuration-driven, with the only external dependency being the globally-installed Mintlify CLI.

**SBOM Purpose and Applications**:

This SPDX SBOM serves multiple critical functions:

1. **License Compliance**: Documents all software licenses to ensure legal compliance
2. **Security Transparency**: Enables vulnerability scanning across the software supply chain
3. **Supply Chain Risk Management**: Provides visibility into component sources and dependencies
4. **Regulatory Compliance**: Meets requirements for software composition transparency (e.g., Executive Order 14028)
5. **Dependency Tracking**: Maintains visibility into direct and transitive dependencies

## Implementation

### Project Structure Analysis

The Mintlify Documentation Starter Kit follows a flat, documentation-focused directory structure:

```
mintlify-documentation-starter-kit/
├── docs.json                      # Primary configuration (111 lines)
├── README.md                      # Setup and usage instructions
├── favicon.svg                    # Site favicon
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── api-reference/
│   └── openapi.json              # OpenAPI 3.1.0 spec (194 lines)
├── api-reference/
│   ├── introduction.md           # API documentation intro
│   └── endpoint/
│       ├── get.md               # GET endpoint docs
│       ├── create.md            # POST endpoint docs
│       ├── delete.md            # DELETE endpoint docs
│       └── webhook.md           # Webhook docs
├── essentials/
│   ├── settings.md              # Settings documentation
│   ├── navigation.md            # Navigation configuration
│   ├── markdown.md              # Markdown usage guide
│   ├── code.md                  # Code block documentation
│   ├── images.md                # Image usage guide
│   └── reusable-snippets.md    # Snippet documentation
├── ai-tools/
│   ├── cursor.md                # Cursor editor integration
│   ├── claude-code.md           # Claude AI integration
│   └── windsurf.md              # Windsurf integration
├── index.md                      # Homepage content
├── quickstart.md                 # Quick start guide
├── development.md                # Development instructions
├── api-docs.md                   # API documentation
├── architecture.md               # Architecture documentation
├── component-docs.md             # Component documentation
├── concepts.md                   # Concepts documentation
├── feature-guides.md             # Feature guides
├── getting-started.md            # Getting started guide
├── how_to.md                     # How-to guides
├── intro.md                      # Quick start introduction
├── reference.md                  # API reference
├── sbom-cyclonedx.md            # CycloneDX SBOM docs
├── sbom-spdx.md                 # SPDX SBOM docs (this file)
├── sbom_cyclonedx.md            # Alternative CycloneDX docs
├── sbom_spdx.md                 # Alternative SPDX docs
└── tutorials.md                  # Tutorial documentation
```

**File Type Distribution**:

- Configuration: 1 JSON file (`docs.json`)
- API Specification: 1 JSON file (`openapi.json`)
- Documentation: 25+ Markdown files (`.md` extension)
- Assets: 3 SVG files (logos and favicon)

### SPDX 2.3 Document Structure

The SPDX specification version 2.3 defines a standardized, hierarchical structure for documenting software composition. The official specification is available at https://spdx.github.io/spdx-spec/v2.3/.

#### Document Creation Information

The document creation section provides metadata about the SBOM itself:

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "Mintlify-Documentation-Starter-Kit-SBOM",
  "documentNamespace": "https://sbom.mintlify.com/starter-kit/2024-01-15",
  "creationInfo": {
    "created": "2024-01-15T00:00:00Z",
    "creators": [
      "Tool: SPDX-Documentation-Generator",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22",
    "comment": "SBOM generated from comprehensive source code analysis of Mintlify Documentation Starter Kit. This SBOM documents a configuration-driven documentation framework with minimal external dependencies. The project operates primarily through configuration (docs.json) and markdown content, with a single runtime dependency on the globally-installed Mintlify CLI tool."
  },
  "documentDescribes": [
    "SPDXRef-Package-Mintlify-Docs-Starter"
  ]
}
```

**Field Explanations**:

- **spdxVersion**: SPDX specification version (`SPDX-2.3`)
- **dataLicense**: Required CC0-1.0 public domain dedication for SPDX documents
- **SPDXID**: Unique identifier for this SPDX document
- **name**: Human-readable name for this SBOM
- **documentNamespace**: Unique URI identifying this specific SBOM version
- **created**: ISO 8601 timestamp of SBOM generation
- **creators**: Tools and organizations responsible for SBOM creation
- **licenseListVersion**: SPDX License List version (3.22 current as of 2024)
- **documentDescribes**: References to primary packages described

#### Package Information

**Primary Application Package**:

```json
{
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Mintlify-Docs-Starter",
      "name": "Mintlify-Documentation-Starter-Kit",
      "versionInfo": "1.0.0",
      "packageFileName": "mintlify-starter-kit",
      "supplier": "Organization: Mintlify",
      "downloadLocation": "NOASSERTION",
      "filesAnalyzed": true,
      "verificationCode": {
        "value": "NOASSERTION"
      },
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "licenseComments": "License information not explicitly declared in source code. Project provided as example/starter template by Mintlify.",
      "copyrightText": "NOASSERTION",
      "summary": "Mintlify documentation starter kit for creating professional documentation websites",
      "description": "Configuration-driven documentation framework built on Mintlify platform. Includes example guide pages, API reference capabilities, navigation structures, theme customization, and AI tool integrations. Site behavior defined through docs.json with content in Markdown files. Features: dual-theme support (light/dark), OpenAPI 3.1.0 integration, contextual AI tool options (ChatGPT, Claude, Perplexity, Cursor, VS Code), social media footer links, automatic GitHub deployment.",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration-driven documentation framework with JSON config, Markdown content, OpenAPI spec, SVG assets",
      "primaryPackagePurpose": "APPLICATION",
      "builtDate": "2024-01-15T00:00:00Z",
      "validUntilDate": "NOASSERTION",
      "externalRefs": [
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://mintlify.com"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "documentation",
          "referenceLocator": "https://mintlify.com/docs"
        }
      ],
      "comment": "Complete Mintlify Documentation Starter Kit. Configuration and content package leveraging Mintlify platform for static site generation and hosting. Includes: 1 config file (docs.json), 25+ markdown files, 1 OpenAPI spec, 3 SVG assets."
    }
  ]
}
```

**Mintlify CLI Dependency Package**:

```json
{
  "SPDXID": "SPDXRef-Package-Mintlify-CLI",
  "name": "mint",
  "versionInfo": "latest",
  "packageFileName": "mint",
  "supplier": "Organization: Mintlify",
  "downloadLocation": "https://registry.npmjs.org/mint",
  "filesAnalyzed": false,
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseDeclared": "NOASSERTION",
  "licenseComments": "License information not available in provided source. Should be verified from npmjs.com package page.",
  "copyrightText": "Copyright (c) Mintlify",
  "summary": "Mintlify CLI tool for local documentation preview and development",
  "description": "Command-line interface for Mintlify documentation platform. Provides local development server with hot reload on port 3000, docs.json validation, deployment management. Installed globally via 'npm i -g mint'. Commands: 'mint dev' (local preview), 'mint update' (update CLI). Required for local development but not production deployment (handled by Mintlify GitHub app).",
  "homepage": "https://www.npmjs.com/package/mint",
  "sourceInfo": "npm package installed globally outside project directory",
  "primaryPackagePurpose": "APPLICATION",
  "externalRefs": [
    {
      "referenceCategory": "PACKAGE-MANAGER",
      "referenceType": "purl",
      "referenceLocator": "pkg:npm/mint"
    },
    {
      "referenceCategory": "OTHER",
      "referenceType": "website",
      "referenceLocator": "https://mintlify.com"
    }
  ],
  "comment": "Runtime dependency for local development only. Installed globally via npm. Version 'latest' per README.md. Not bundled with project but required for local preview (mint dev)."
}
```

**Node.js Runtime Environment**:

```json
{
  "SPDXID": "SPDXRef-Package-NodeJS-Runtime",
  "name": "Node.js",
  "versionInfo": "NOASSERTION",
  "supplier": "Organization: Node.js contributors",
  "downloadLocation": "https://nodejs.org/en/download",
  "filesAnalyzed": false,
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseDeclared": "MIT",
  "licenseComments": "Node.js released under MIT License: https://github.com/nodejs/node/blob/main/LICENSE",
  "copyrightText": "Copyright Node.js contributors. All rights reserved.",
  "summary": "JavaScript runtime environment required for Mintlify CLI execution",
  "description": "Open-source, cross-platform JavaScript runtime built on Chrome's V8 engine. Required for executing Mintlify CLI tool. Provides npm package manager for CLI installation. Version requirements not specified but modern LTS versions (14.x+) typically compatible.",
  "homepage": "https://nodejs.org",
  "sourceInfo": "Platform dependency installed separately from project",
  "primaryPackagePurpose": "FRAMEWORK",
  "externalRefs": [
    {
      "referenceCategory": "OTHER",
      "referenceType": "website",
      "referenceLocator": "https://nodejs.org"
    },
    {
      "referenceCategory": "SECURITY",
      "referenceType": "url",
      "referenceLocator": "https://nodejs.org/en/about/security"
    }
  ],
  "comment": "Platform dependency for Mintlify CLI execution. Not directly managed by project but essential for local development. Version not specified; users should install current LTS."
}
```

**OpenAPI Specification Component**:

```json
{
  "SPDXID": "SPDXRef-Package-OpenAPI-Specification",
  "name": "OpenAPI-Plant-Store-Specification",
  "versionInfo": "3.1.0",
  "packageFileName": "api-reference/openapi.json",
  "supplier": "NOASSERTION",
  "downloadLocation": "NOASSERTION",
  "filesAnalyzed": true,
  "verificationCode": {
    "value": "NOASSERTION"
  },
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseDeclared": "MIT",
  "licenseComments": "License declared in OpenAPI specification info.license field (lines 6-7 of api-reference/openapi.json)",
  "copyrightText": "NOASSERTION",
  "summary": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features",
  "description": "Example OpenAPI spec defining fictional Plant Store API. Demonstrates Mintlify's OpenAPI integration for automatic API documentation. Includes: server config (http://sandbox.mintlify.com), bearer token auth, 3 REST endpoints (GET /plants, POST /plants, DELETE /plants/{id}), webhook (POST /plant/webhook), 3 schemas (Plant, NewPlant, Error). Total: 194 lines. Conforms to OpenAPI 3.1.0 standard.",
  "homepage": "https://spec.openapis.org/oas/v3.1.0",
  "sourceInfo": "Static JSON data file conforming to OpenAPI 3.1.0 specification",
  "primaryPackagePurpose": "DATA",
  "externalRefs": [
    {
      "referenceCategory": "OTHER",
      "referenceType": "specification",
      "referenceLocator": "https://spec.openapis.org/oas/v3.1.0"
    }
  ],
  "comment": "Sample/example API specification demonstrating Mintlify's OpenAPI integration. Not a production API. Located at api-reference/openapi.json, 194 lines."
}
```

#### File Information

**Configuration File - docs.json**:

```json
{
  "files": [
    {
      "SPDXID": "SPDXRef-File-DocsConfig",
      "fileName": "./docs.json",
      "fileTypes": ["TEXT", "APPLICATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseInfoInFiles": ["NOASSERTION"],
      "copyrightText": "NOASSERTION",
      "noticeText": "NOASSERTION",
      "comment": "Primary configuration file (111 lines) defining complete site structure. Contains: JSON schema reference, theme config (mint), site name (Mint Starter Kit), colors (primary #16A34A, light #07C983, dark #15803D), favicon (/favicon.svg), navigation (2 tabs: Guides with 4 groups/12 pages, API reference with 2 groups/5 pages), global anchors (Documentation, Blog), logo config (light/dark variants), navbar (Support email, Dashboard button), contextual options (copy, view, chatgpt, claude, perplexity, mcp, cursor, vscode), footer socials (x, github, linkedin). Single file controls all site behavior.",
      "fileContributors": ["Organization: Mintlify"]
    }
  ]
}
```

**Setup Documentation - README.md**:

```json
{
  "SPDXID": "SPDXRef-File-README",
  "fileName": "./README.md",
  "fileTypes": ["TEXT", "DOCUMENTATION"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseInfoInFiles": ["NOASSERTION"],
  "copyrightText": "NOASSERTION",
  "noticeText": "NOASSERTION",
  "comment": "Setup and usage documentation. Contains: project intro (Mintlify Starter Kit), template usage (green 'Use this template' button), features (guides, navigation, customizations, API reference, components), quickstart link, development setup ('npm i -g mint', 'mint dev', localhost:3000), publishing (GitHub app at dashboard.mintlify.com/settings/organization/github-app, auto-deploy on push), troubleshooting ('mint update', verify docs.json), resources (mintlify.com/docs).",
  "fileContributors": ["Organization: Mintlify"]
}
```

**OpenAPI Specification - api-reference/openapi.json**:

```json
{
  "SPDXID": "SPDXRef-File-OpenAPI-JSON",
  "fileName": "./api-reference/openapi.json",
  "fileTypes": ["TEXT", "APPLICATION"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseInfoInFiles": ["MIT"],
  "copyrightText": "NOASSERTION",
  "noticeText": "NOASSERTION",
  "comment": "OpenAPI 3.1.0 spec (194 lines) defining Plant Store API. Structure: info (title, description, MIT license, v1.0.0), servers (http://sandbox.mintlify.com), security (bearerAuth), paths (GET /plants with limit param, POST /plants with NewPlant body, DELETE /plants/{id}), webhooks (POST /plant/webhook), components/schemas (Plant: required name/optional tag, NewPlant: extends Plant with required id, Error: required error code/message), securitySchemes (bearerAuth: http/bearer). Demonstrates OpenAPI integration in Mintlify.",
  "fileContributors": ["NOASSERTION"]
}
```

#### Relationship Information

SPDX relationships define dependency structure and containment hierarchy:

```json
{
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-Mintlify-Docs-Starter",
      "comment": "SBOM describes Mintlify Documentation Starter Kit as primary application package"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-Mintlify-CLI",
      "comment": "Runtime dependency for local development workflow (mint dev). Required for local preview but not production deployment."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-CLI",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-NodeJS-Runtime",
      "comment": "Mintlify CLI requires Node.js runtime environment for execution"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-DocsConfig",
      "comment": "Primary configuration file contained in main package"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-README",
      "comment": "Setup documentation contained in main package"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-OpenAPI-JSON",
      "comment": "OpenAPI specification contained in main package"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
      "relationshipType": "HAS_PREREQUISITE",
      "relatedSpdxElement": "SPDXRef-Package-OpenAPI-Specification",
      "comment": "OpenAPI specification demonstrates API documentation capabilities"
    }
  ]
}
```

### Complete SPDX 2.3 SBOM

Based on comprehensive analysis of the project structure, configuration files, and documentation, here is the complete SPDX 2.3 SBOM in JSON format:

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "Mintlify-Documentation-Starter-Kit-SBOM",
  "documentNamespace": "https://sbom.mintlify.com/starter-kit/2024-01-15",
  "creationInfo": {
    "created": "2024-01-15T00:00:00Z",
    "creators": [
      "Tool: SPDX-Documentation-Generator-v1.0",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22",
    "comment": "SBOM generated from comprehensive source code analysis of Mintlify Documentation Starter Kit. This SBOM documents a configuration-driven documentation framework with minimal external dependencies. The project operates primarily through configuration (docs.json) and markdown content, with a single runtime dependency on the globally-installed Mintlify CLI tool."
  },
  "documentDescribes": [
    "SPDXRef-Package-Mintlify-Docs-Starter"
  ],
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Mintlify-Docs-Starter",
      "name": "Mintlify-Documentation-Starter-Kit",
      "versionInfo": "1.0.0",
      "packageFileName": "mintlify-starter-kit",
      "supplier": "Organization: Mintlify",
      "downloadLocation": "NOASSERTION",
      "filesAnalyzed": true,
      "verificationCode": {
        "value": "NOASSERTION"
      },
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "licenseComments": "License information not explicitly declared in source code. Project provided as example/starter template by Mintlify.",
      "copyrightText": "NOASSERTION",
      "summary": "Mintlify documentation starter kit for creating professional documentation websites",
      "description": "Configuration-driven documentation framework built on Mintlify platform. Includes example guide pages, API reference capabilities, navigation structures, theme customization, and AI tool integrations. Site behavior defined through docs.json with content in Markdown files. Features: dual-theme support (light/dark), OpenAPI 3.1.0 integration, contextual AI tool options (ChatGPT, Claude, Perplexity, Cursor, VS Code), social media footer links, automatic GitHub deployment.",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration-driven documentation framework with JSON config, Markdown content, OpenAPI spec, SVG assets",
      "primaryPackagePurpose": "APPLICATION",
      "builtDate": "2024-01-15T00:00:00Z",
      "validUntilDate": "NOASSERTION",
      "externalRefs": [
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://mintlify.com"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "documentation",
          "referenceLocator": "https://mintlify.com/docs"
        }
      ],
      "comment": "Complete Mintlify Documentation Starter Kit. Configuration and content package leveraging Mintlify platform for static site generation and hosting. Includes: 1 config file (docs.json), 25+ markdown files, 1 OpenAPI spec, 3 SVG assets."
    },
    {
      "SPDXID": "SPDXRef-Package-Mintlify-CLI",
      "name": "mint",
      "versionInfo": "latest",
      "packageFileName": "mint",
      "supplier": "Organization: Mintlify",
      "downloadLocation": "https://registry.npmjs.org/mint",
      "filesAnalyzed": false,
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "licenseComments": "License information not available in provided source. Should be verified from npmjs.com package page.",
      "copyrightText": "Copyright (c) Mintlify",
      "summary": "Mintlify CLI tool for local documentation preview and development",
      "description": "Command-line interface for Mintlify documentation platform. Provides local development server with hot reload on port 3000, docs.json validation, deployment management. Installed globally via 'npm i -g mint'. Commands: 'mint dev' (local preview), 'mint update' (update CLI). Required for local development but not production deployment (handled by Mintlify GitHub app).",
      "homepage": "https://www.npmjs.com/package/mint",
      "sourceInfo": "npm package installed globally outside project directory",
      "primaryPackagePurpose": "APPLICATION",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/mint"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://mintlify.com"
        }
      ],
      "comment": "Runtime dependency for local development only. Installed globally via npm. Version 'latest' per README.md. Not bundled with project but required for local preview (mint dev)."
    },
    {
      "SPDXID": "SPDXRef-Package-NodeJS-Runtime",
      "name": "Node.js",
      "versionInfo": "NOASSERTION",
      "supplier": "Organization: Node.js contributors",
      "downloadLocation": "https://nodejs.org/en/download",
      "filesAnalyzed": false,
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "licenseComments": "Node.js released under MIT License: https://github.com/nodejs/node/blob/main/LICENSE",
      "copyrightText": "Copyright Node.js contributors. All rights reserved.",
      "summary": "JavaScript runtime environment required for Mintlify CLI execution",
      "description": "Open-source, cross-platform JavaScript runtime built on Chrome's V8 engine. Required for executing Mintlify CLI tool. Provides npm package manager for CLI installation. Version requirements not specified but modern LTS versions (14.x+) typically compatible.",
      "homepage": "https://nodejs.org",
      "sourceInfo": "Platform dependency installed separately from project",
      "primaryPackagePurpose": "FRAMEWORK",
      "externalRefs": [
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://nodejs.org"
        },
        {
          "referenceCategory": "SECURITY",
          "referenceType": "url",
          "referenceLocator": "https://nodejs.org/en/about/security"
        }
      ],
      "comment": "Platform dependency for Mintlify CLI execution. Not directly managed by project but essential for local development. Version not specified; users should install current LTS."
    },
    {
      "SPDXID": "SPDXRef-Package-OpenAPI-Specification",
      "name": "OpenAPI-Plant-Store-Specification",
      "versionInfo": "3.1.0",
      "packageFileName": "api-reference/openapi.json",
      "supplier": "NOASSERTION",
      "downloadLocation": "NOASSERTION",
      "filesAnalyzed": true,
      "verificationCode": {
        "value": "NOASSERTION"
      },
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "licenseComments": "License declared in OpenAPI specification info.license field (lines 6-7 of api-reference/openapi.json)",
      "copyrightText": "NOASSERTION",
      "summary": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features",
      "description": "Example OpenAPI spec defining fictional Plant Store API. Demonstrates Mintlify's OpenAPI integration for automatic API documentation. Includes: server config (http://sandbox.mintlify.com), bearer token auth, 3 REST endpoints (GET /plants, POST /plants, DELETE /plants/{id}),