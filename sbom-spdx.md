# Software Bill of Materials - SPDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in SPDX 2.3 format for the Mintlify Documentation Starter Kit project. An SBOM is a formal, machine-readable inventory of all software components, dependencies, and metadata that comprise a software application. The SPDX (Software Package Data Exchange) format is an open standard (ISO/IEC 5962:2021) developed by the Linux Foundation for communicating software component information, licenses, copyrights, and security references.

The Mintlify Documentation Starter Kit is a lightweight documentation framework that operates primarily as a configuration-driven static site generator. Unlike traditional software applications with extensive runtime dependencies, this project consists mainly of:

- **Configuration files** (`docs.json`) defining site structure and behavior
- **Content files** (Markdown documentation)
- **API specifications** (OpenAPI 3.1.0 format)
- **Static assets** (logos, favicon)
- **Single runtime dependency** (Mintlify CLI tool)

This SBOM serves multiple critical purposes:
- **License Compliance**: Tracking open source licenses and ensuring compliance obligations
- **Security Transparency**: Enabling vulnerability scanning and security assessments
- **Supply Chain Risk Management**: Understanding component sources and dependencies
- **Regulatory Compliance**: Meeting requirements for software composition transparency

## Implementation

### Project Structure Analysis

The Mintlify Documentation Starter Kit has a unique architecture as a documentation-focused project. Based on analysis of the provided source code, the project structure is:

```
mintlify-starter-kit/
├── docs.json                      # Main configuration file
├── README.md                      # Setup and usage instructions
├── api-reference/
│   └── openapi.json              # Sample API specification
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── favicon.svg                    # Site favicon
└── *.md files                     # Documentation content
```

**Key Finding**: This project does **not** contain traditional dependency manifest files (`package.json`, `requirements.txt`, etc.). The only external dependency is the Mintlify CLI tool (`mint`), which is installed globally via npm:

```bash
npm i -g mint
```

This global installation pattern means the dependency is not tracked within the project itself, requiring special consideration in SBOM generation.

### SPDX Document Structure

The SPDX 2.3 specification defines a standardized structure for documenting software components. Our SBOM implementation includes:

#### 1. Document Creation Information

Metadata about the SBOM document itself:

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "Mintlify-Documentation-Starter-Kit-SBOM",
  "documentNamespace": "https://mintlify.com/sbom/starter-kit-2024-01",
  "creationInfo": {
    "created": "2024-01-15T00:00:00Z",
    "creators": [
      "Tool: OrchestrAI-SBOM-Generator",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22"
  }
}
```

**Field Explanations**:
- `spdxVersion`: Declares SPDX specification version (2.3)
- `dataLicense`: CC0-1.0 is required for all SPDX documents per specification
- `SPDXID`: Unique identifier for this document (`SPDXRef-DOCUMENT`)
- `documentNamespace`: Unique URI identifying this specific SBOM instance
- `created`: ISO 8601 timestamp of SBOM generation
- `licenseListVersion`: Version of SPDX License List used (3.22 current as of 2024)

#### 2. Package Information

Documentation of software packages and components:

**Main Application Package**:

```json
{
  "SPDXID": "SPDXRef-Package-Documentation-Starter-Kit",
  "name": "Mintlify-Documentation-Starter-Kit",
  "versionInfo": "1.0.0",
  "downloadLocation": "NOASSERTION",
  "filesAnalyzed": true,
  "licenseConcluded": "NOASSERTION",
  "licenseDeclared": "NOASSERTION",
  "copyrightText": "NOASSERTION",
  "description": "A Mintlify documentation starter kit providing templates, navigation structures, API reference capabilities, and documentation components for creating professional documentation websites.",
  "homepage": "https://mintlify.com/docs",
  "primaryPackagePurpose": "APPLICATION",
  "comment": "Documentation framework consisting primarily of configuration and content files"
}
```

**Mintlify CLI Dependency**:

```json
{
  "SPDXID": "SPDXRef-Package-Mintlify-CLI",
  "name": "mint",
  "versionInfo": "latest",
  "packageFileName": "mint",
  "downloadLocation": "https://registry.npmjs.org/mint",
  "filesAnalyzed": false,
  "licenseConcluded": "NOASSERTION",
  "licenseDeclared": "NOASSERTION",
  "copyrightText": "Copyright (c) Mintlify",
  "description": "Mintlify CLI tool for local documentation preview and development. Provides live development server with hot reload capabilities.",
  "homepage": "https://www.npmjs.com/package/mint",
  "externalRefs": [
    {
      "referenceCategory": "PACKAGE-MANAGER",
      "referenceType": "purl",
      "referenceLocator": "pkg:npm/mint"
    }
  ],
  "primaryPackagePurpose": "APPLICATION"
}
```

**OpenAPI Specification Component**:

```json
{
  "SPDXID": "SPDXRef-Package-OpenAPI-Spec",
  "name": "OpenAPI-Plant-Store-Specification",
  "versionInfo": "3.1.0",
  "downloadLocation": "NOASSERTION",
  "filesAnalyzed": true,
  "licenseConcluded": "MIT",
  "licenseDeclared": "MIT",
  "copyrightText": "NOASSERTION",
  "description": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features. Includes plant store endpoints (GET, POST, DELETE), webhook definitions, and bearer authentication scheme.",
  "comment": "Located in api-reference/openapi.json",
  "primaryPackagePurpose": "DATA"
}
```

#### 3. File Information

Individual file documentation with checksums and metadata:

**Configuration File**:

```json
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
  "copyrightText": "NOASSERTION",
  "comment": "Primary configuration file defining site structure, theme (mint), colors (primary: #16A34A), navigation with tabs and groups, logo references, navbar configuration, contextual options, and footer social links. Contains 111 lines defining complete site behavior."
}
```

**README Documentation**:

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
  "copyrightText": "NOASSERTION",
  "comment": "Setup instructions including: CLI installation (npm i -g mint), development server usage (mint dev at http://localhost:3000), publishing via GitHub app integration, and troubleshooting guidance (mint update for issues, verify docs.json location for 404s)."
}
```

**OpenAPI Specification File**:

```json
{
  "SPDXID": "SPDXRef-File-OpenAPI",
  "fileName": "./api-reference/openapi.json",
  "fileTypes": ["TEXT", "APPLICATION"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseDeclared": "MIT",
  "copyrightText": "NOASSERTION",
  "comment": "OpenAPI 3.1.0 specification defining Plant Store API. Server: http://sandbox.mintlify.com. Security: bearer authentication. Endpoints: GET /plants (with limit query param), POST /plants (creates NewPlant), DELETE /plants/{id}. Webhook: POST /plant/webhook. Schemas: Plant (name required, tag optional), NewPlant (extends Plant with required id field), Error (error code and message)."
}
```

**Documentation Content Files**:

```json
{
  "SPDXID": "SPDXRef-File-API-Docs",
  "fileName": "./api-docs.md",
  "fileTypes": ["TEXT", "DOCUMENTATION"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "copyrightText": "NOASSERTION",
  "comment": "Comprehensive API documentation for Plant Store API covering: authentication (bearer token), endpoints (GET/POST plants, DELETE plants/{id}), webhook integration, data models (Plant, NewPlant, Error), integration guide with code examples, and troubleshooting."
}
```

```json
{
  "SPDXID": "SPDXRef-File-Architecture",
  "fileName": "./architecture.md",
  "fileTypes": ["TEXT", "DOCUMENTATION"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "copyrightText": "NOASSERTION",
  "comment": "Architecture documentation explaining: configuration-first design, component-based structure (docs.json, markdown, OpenAPI), navigation hierarchy (tabs → groups → pages), build and deployment architecture (local via mint dev, production via GitHub app), data flow, security, performance optimization, and scalability considerations."
}
```

#### 4. Relationship Information

Relationships between SPDX elements define the dependency structure:

**Document Relationships**:

```json
{
  "spdxElementId": "SPDXRef-DOCUMENT",
  "relationshipType": "DESCRIBES",
  "relatedSpdxElement": "SPDXRef-Package-Documentation-Starter-Kit",
  "comment": "This SBOM document describes the Mintlify Documentation Starter Kit application"
}
```

**Dependency Relationships**:

```json
{
  "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
  "relationshipType": "DEPENDS_ON",
  "relatedSpdxElement": "SPDXRef-Package-Mintlify-CLI",
  "comment": "Runtime dependency on Mintlify CLI for local development and publishing"
}
```

**Containment Relationships**:

```json
{
  "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
  "relationshipType": "CONTAINS",
  "relatedSpdxElement": "SPDXRef-File-DocsConfig",
  "comment": "Primary configuration file"
}
```

### Complete SPDX 2.3 Document

Below is the complete, valid SPDX 2.3 document for the Mintlify Documentation Starter Kit:

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "Mintlify-Documentation-Starter-Kit-SBOM",
  "documentNamespace": "https://mintlify.com/sbom/starter-kit-2024-01-15/v1.0.0",
  "creationInfo": {
    "created": "2024-01-15T00:00:00Z",
    "creators": [
      "Tool: OrchestrAI-SBOM-Generator-v1.0",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22",
    "comment": "SBOM generated from source code analysis of Mintlify Documentation Starter Kit"
  },
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Documentation-Starter-Kit",
      "name": "Mintlify-Documentation-Starter-Kit",
      "versionInfo": "1.0.0",
      "downloadLocation": "NOASSERTION",
      "filesAnalyzed": true,
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "description": "A Mintlify documentation starter kit providing templates, navigation structures, API reference capabilities, and documentation components for creating professional documentation websites. Includes example pages, customization options, and OpenAPI integration.",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration-driven documentation framework with markdown content",
      "primaryPackagePurpose": "APPLICATION",
      "comment": "Main application package consisting of configuration files (docs.json), markdown content, API specifications, and static assets"
    },
    {
      "SPDXID": "SPDXRef-Package-Mintlify-CLI",
      "name": "mint",
      "versionInfo": "latest",
      "packageFileName": "mint",
      "downloadLocation": "https://registry.npmjs.org/mint",
      "filesAnalyzed": false,
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "copyrightText": "Copyright (c) Mintlify",
      "description": "Mintlify CLI tool for local documentation preview and development. Provides live development server on port 3000 with hot reload, validation, and publishing capabilities. Installed globally via npm.",
      "homepage": "https://www.npmjs.com/package/mint",
      "sourceInfo": "npm package installed globally",
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
      "primaryPackagePurpose": "APPLICATION",
      "comment": "Runtime dependency for local development (mint dev) and CLI operations (mint update)"
    },
    {
      "SPDXID": "SPDXRef-Package-OpenAPI-Spec",
      "name": "OpenAPI-Plant-Store-Specification",
      "versionInfo": "3.1.0",
      "downloadLocation": "NOASSERTION",
      "filesAnalyzed": true,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "NOASSERTION",
      "description": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features within Mintlify. Defines plant store API with GET /plants, POST /plants, DELETE /plants/{id} endpoints, webhook integration, bearer authentication, and three schemas (Plant, NewPlant, Error).",
      "comment": "Example API specification in api-reference/openapi.json demonstrating OpenAPI integration capabilities",
      "primaryPackagePurpose": "DATA"
    },
    {
      "SPDXID": "SPDXRef-Package-Node-Runtime",
      "name": "Node.js",
      "versionInfo": "NOASSERTION",
      "downloadLocation": "https://nodejs.org",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Node.js contributors",
      "description": "JavaScript runtime environment required for executing Mintlify CLI (mint). Provides npm package manager for CLI installation.",
      "homepage": "https://nodejs.org",
      "externalRefs": [
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://nodejs.org/en/docs"
        }
      ],
      "primaryPackagePurpose": "FRAMEWORK",
      "comment": "Platform dependency required for Mintlify CLI execution"
    }
  ],
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
      "copyrightText": "NOASSERTION",
      "comment": "Primary configuration (111 lines) defining: schema reference (mintlify.com/docs.json), theme (mint), name (Mint Starter Kit), colors (primary #16A34A, light #07C983, dark #15803D), navigation structure with Guides tab (4 groups: Getting started, Customization, Writing content, AI tools) and API reference tab (2 groups: API documentation, Endpoint examples), global anchors (Documentation, Blog), logo paths (light.svg, dark.svg), navbar (Support email link, Dashboard button), contextual options (copy, view, chatgpt, claude, perplexity, mcp, cursor, vscode), footer socials (x, github, linkedin)"
    },
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
      "copyrightText": "NOASSERTION",
      "comment": "Setup and usage documentation covering: template usage (green 'Use this template' button), development setup (npm i -g mint for CLI installation), local preview (mint dev command at http://localhost:3000 in directory with docs.json), publishing (GitHub app from dashboard.mintlify.com/settings/organization/github-app, automatic deployment on push to default branch), troubleshooting (mint update for environment issues, docs.json location for 404 errors), and resource links (Mintlify documentation at mintlify.com/docs)"
    },
    {
      "SPDXID": "SPDXRef-File-OpenAPI",
      "fileName": "./api-reference/openapi.json",
      "fileTypes": ["TEXT", "APPLICATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "NOASSERTION",
      "comment": "OpenAPI 3.1.0 specification (194 lines) defining: info (title: OpenAPI Plant Store, license: MIT, version: 1.0.0), server (http://sandbox.mintlify.com), security (bearerAuth scheme), paths (GET /plants with limit query param returning Plant array, POST /plants with NewPlant body returning Plant, DELETE /plants/{id} with id path param returning 204), webhook (POST /plant/webhook with NewPlant body), components with schemas (Plant with required name and optional tag, NewPlant extending Plant with required id, Error with required error code and message), securitySchemes (bearerAuth using HTTP bearer scheme)"
    },
    {
      "SPDXID": "SPDXRef-File-API-Docs",
      "fileName": "./api-docs.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Comprehensive API documentation covering: overview (Plant Store API at http://sandbox.mintlify.com), authentication (bearer token in Authorization header), GET /plants endpoint (with limit parameter, returns 200 with Plant array or 400 with Error), POST /plants endpoint (creates plant with NewPlant schema, returns 200 with Plant or 400 with Error), DELETE /plants/{id} endpoint (deletes by ID, returns 204 success or 400 error), POST /plant/webhook webhook (receives NewPlant payload, expects 200 response), data models (Plant with name and tag, NewPlant extending Plant with id, Error with code and message), integration guide with JavaScript examples, rate limiting best practices, and troubleshooting guidance"
    },
    {
      "SPDXID": "SPDXRef-File-Architecture",
      "fileName": "./architecture.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Architecture documentation explaining: system overview (configuration-driven static site generator), core architectural principles (configuration-first via docs.json, content-driven with markdown, zero-backend, automatic deployment via GitHub integration, OpenAPI integration for API docs), component architecture (configuration layer with JSON schema, content layer with markdown files, API documentation layer with OpenAPI spec), navigation architecture (three-tier hierarchy: tabs → groups → pages), theming architecture (color system with primary/light/dark, logo system with theme-aware switching, favicon), navbar configuration (links and primary button), footer (social media links), contextual menu integration (AI tools and dev environments), build and deployment (local via mint dev on port 3000, production via GitHub app with automatic builds), data flow patterns, security considerations, performance optimization strategies, and scalability architecture"
    },
    {
      "SPDXID": "SPDXRef-File-ComponentDocs",
      "fileName": "./component-docs.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Component documentation covering: main configuration component (docs.json structure and properties), color scheme component (primary/light/dark colors), navigation component (tabs, groups, pages hierarchy), global navigation component (anchors for external links), logo component (theme-aware light/dark variants), navbar component (links and primary button), contextual menu component (AI tool and editor integrations), footer component (social media configuration), OpenAPI configuration (specification metadata), server configuration (API endpoints), security configuration (authentication schemes), path components (API endpoint definitions), webhook components, and schema components (data models)"
    },
    {
      "SPDXID": "SPDXRef-File-GettingStarted",
      "fileName": "./getting-started.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Getting started guide covering: introduction (creating modern documentation websites), prerequisites (GitHub account, project/API, 10 minutes), step-by-step setup (template usage, local environment setup with npm i -g mint, live preview with mint dev), included features (guide pages, navigation, customizations, API reference, components), customization instructions (branding via docs.json colors/logo/name, content organization, writing in markdown), publishing workflow (dashboard connection via dashboard.mintlify.com/settings/organization/github-app, automatic deployment on git push), troubleshooting (mint update for preview issues, docs.json verification for 404s), next steps, and quick reference commands"
    },
    {
      "SPDXID": "SPDXRef-File-Reference",
      "fileName": "./reference.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "API reference documentation in user-friendly format covering: getting started with API (requirements and authentication), working with plants (viewing all with limit parameter, adding new with required id/name and optional tag, removing by id with permanent deletion warning), real-time updates via webhooks (automatic notifications for new plants with endpoint setup requirements), understanding responses (success and error formats with common error reasons), data structures (plant information with required/optional fields, complete plant records with identification numbers, error information structure), best practices (efficient usage with limits/error handling/access key security/webhooks, performance tips for caching and rate limiting), and help resources"
    },
    {
      "SPDXID": "SPDXRef-File-Tutorials",
      "fileName": "./tutorials.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Tutorial documentation providing step-by-step workflows (note: contains example OrchestRAI content as template, actual product is Mintlify documentation starter kit)"
    },
    {
      "SPDXID": "SPDXRef-File-FeatureGuides",
      "fileName": "./feature-guides.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Feature guides documentation (note: contains example OrchestRAI content as template)"
    },
    {
      "SPDXID": "SPDXRef-File-HowTo",
      "fileName": "./how_to.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "How-to guides documentation header (note: contains minimal content, references OrchestRAI as example)"
    },
    {
      "SPDXID": "SPDXRef-File-Intro",
      "fileName": "./intro.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Quick start guide header (minimal content)"
    },
    {
      "SPDXID": "SPDXRef-File-Concepts",
      "fileName": "./concepts.md",
      "fileTypes": ["TEXT", "DOCUMENTATION"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "copyrightText": "NOASSERTION",
      "comment": "Concepts and architecture documentation (note: contains example OrchestRAI concepts as template content)"
    }
  ],
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-Documentation-Starter-Kit",
      "comment": "This SBOM describes the Mintlify Documentation Starter Kit application"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-Mintlify-CLI",
      "comment": "Runtime dependency for local development and publishing workflows"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-CLI",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-Node-Runtime",
      "comment": "Mintlify CLI requires Node.js runtime environment"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-DocsConfig",
      "comment": "Primary configuration file defining site structure and behavior"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-README",
      "comment": "Setup and usage instructions"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-Package-OpenAPI-Spec",
      "comment": "Contains OpenAPI specification component"
    },
    {
      "spdxElementId": "SPDXRef-Package-OpenAPI-Spec",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-OpenAPI",
      "comment": "OpenAPI specification file"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-API-Docs",
      "comment": "API documentation content"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-Architecture",
      "comment": "Architecture documentation"
    },
    {
      "spdxElementId": "SPDXRef-Package-Documentation-Starter-Kit",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-ComponentDocs",
      "comment": "Component documentation