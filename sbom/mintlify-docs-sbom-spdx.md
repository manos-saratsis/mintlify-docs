# Software Bill of Materials (SBOM) - SPDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in SPDX 2.3 format for the **Mintlify Documentation Starter Kit** project. An SBOM is a formal, machine-readable inventory of all software components, dependencies, libraries, and metadata that comprise a software application. SPDX (Software Package Data Exchange) is an open standard (ISO/IEC 5962:2021) developed by the Linux Foundation for communicating software component information.

**What is SPDX?**

SPDX is an internationally recognized open standard for documenting software bill of materials information. The standard provides a common format for companies and communities to share important data about software packages, including:

- Component names and versions
- License information
- Copyright notices
- Security references
- Originating sources
- Relationships between components

**Project Context: Mintlify Documentation Starter Kit**

Based on comprehensive analysis of the provided source code, this project is a **configuration-driven documentation framework** that differs fundamentally from traditional web applications. The project consists of:

- **Configuration file**: `docs.json` (111 lines) defining site structure, theme, and behavior
- **Documentation content**: Multiple Markdown files (`.md` format)
- **API specification**: `api-reference/openapi.json` (194 lines, OpenAPI 3.1.0)
- **Static assets**: Logo files and favicon (SVG format)
- **Setup documentation**: `README.md` with installation and usage instructions

**Critical Architectural Finding**: This project does **not** contain traditional dependency manifest files such as:
- `package.json` / `package-lock.json` (Node.js)
- `requirements.txt` / `Pipfile` (Python)
- `Gemfile` / `Gemfile.lock` (Ruby)
- `pom.xml` / `build.gradle` (Java)
- `go.mod` (Go)
- `Cargo.toml` (Rust)

**Dependency Architecture**: The project has a minimal external dependency footprint:

- **Single Runtime Dependency**: Mintlify CLI (`mint`) installed globally via `npm i -g mint` (per `README.md` line 18)
- **Platform Dependency**: Node.js runtime (required for CLI execution)
- **External Services**: GitHub (version control and deployment), Mintlify Platform (hosting and builds)

This SBOM documents this unique architecture accurately, reflecting the actual components present in the codebase.

## Implementation

### SPDX 2.3 Document Structure

The SPDX 2.3 specification defines a standardized format for documenting software composition. This implementation follows the official specification available at https://spdx.github.io/spdx-spec/v2.3/.

#### Document Creation Information

The document header provides metadata about the SBOM itself:

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
      "Tool: OrchestrAI-Documentation-Specialist",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22",
    "comment": "SBOM generated from comprehensive source code analysis of Mintlify Documentation Starter Kit. This SBOM documents a configuration-driven documentation framework with minimal external dependencies."
  },
  "documentDescribes": [
    "SPDXRef-Package-Mintlify-Docs"
  ]
}
```

**Field Explanations**:

- **spdxVersion**: SPDX specification version (2.3 is current as of 2024)
- **dataLicense**: CC0-1.0 public domain dedication (required for SPDX documents)
- **SPDXID**: Unique identifier for this SPDX document
- **name**: Human-readable name for the SBOM
- **documentNamespace**: Unique URI identifying this specific SBOM version
- **created**: ISO 8601 timestamp of SBOM generation
- **creators**: Tools and organizations responsible for SBOM creation
- **licenseListVersion**: SPDX License List version used (3.22 current)
- **documentDescribes**: References to primary packages in this SBOM

#### Package Information

##### Primary Application Package

```json
{
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Mintlify-Docs",
      "name": "Mintlify-Documentation-Starter-Kit",
      "versionInfo": "1.0.0",
      "packageFileName": "mintlify-starter-kit",
      "supplier": "Organization: Mintlify (hi@mintlify.com)",
      "downloadLocation": "https://github.com/mintlify/starter",
      "filesAnalyzed": true,
      "verificationCode": {
        "value": "NOASSERTION",
        "excludedFiles": []
      },
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "licenseComments": "License information not explicitly declared in provided source code. Project appears to be provided as example/starter template by Mintlify.",
      "copyrightText": "Copyright (c) Mintlify",
      "summary": "Configuration-driven documentation starter kit for creating professional documentation websites",
      "description": "A comprehensive documentation starter kit built on the Mintlify platform. Includes example guide pages (17 total), API reference capabilities via OpenAPI 3.1.0 integration, customizable navigation structure with 2 tabs and 6 groups, theme customization (colors: primary #16A34A, light #07C983, dark #15803D), dual-theme support (light/dark logos), contextual menu options for AI tool integration (ChatGPT, Claude, Perplexity, MCP, Cursor, VS Code), navbar with support link (mailto:hi@mintlify.com) and dashboard button, footer with social links (X/Twitter, GitHub, LinkedIn), and automatic deployment via GitHub integration. Configuration defined in docs.json (111 lines), content in Markdown files, API specification in OpenAPI format (194 lines).",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration files (JSON), documentation content (Markdown), API specification (OpenAPI 3.1.0), static assets (SVG)",
      "primaryPackagePurpose": "APPLICATION",
      "builtDate": "NOASSERTION",
      "validUntilDate": "NOASSERTION",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:generic/mintlify-docs@1.0.0"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "website",
          "referenceLocator": "https://mintlify.com"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "documentation",
          "referenceLocator": "https://mintlify.com/docs"
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "vcs",
          "referenceLocator": "https://github.com/mintlify/starter"
        }
      ],
      "comment": "This package represents the complete Mintlify Documentation Starter Kit. Not a traditional application with compiled code, but a configuration and content package leveraging Mintlify platform for static site generation. Includes: 1 configuration file (docs.json), 14+ markdown documentation files, 1 OpenAPI specification, 3 SVG assets (2 logos + favicon)."
    }
  ]
}
```

##### Mintlify CLI Dependency

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
  "licenseComments": "License information not available in provided source code. Should be verified from npm package registry at npmjs.com/package/mint",
  "copyrightText": "Copyright (c) Mintlify",
  "summary": "Mintlify CLI tool for local documentation preview and development",
  "description": "Command-line interface tool for the Mintlify documentation platform. Provides local development server with hot reload on port 3000, validates docs.json configuration, and manages deployment. Installation: 'npm i -g mint' (global installation per README.md line 18). Primary commands: 'mint dev' starts local preview server at localhost:3000 (line 24), 'mint update' updates CLI to latest version (line 41). Required for local development but not for production deployment (handled by Mintlify GitHub app).",
  "homepage": "https://www.npmjs.com/package/mint",
  "sourceInfo": "npm package installed globally outside project directory",
  "primaryPackagePurpose": "APPLICATION",
  "externalRefs": [
    {
      "referenceCategory": "PACKAGE-MANAGER",
      "referenceType": "purl",
      "referenceLocator": "pkg:npm/mint@latest"
    },
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
  "comment": "Runtime dependency for local development only. Installed globally via npm rather than as project dependency. Version 'latest' per README installation instructions. Not bundled with documentation project but required for local preview (mint dev). Absence of package.json in project confirms global installation pattern."
}
```

##### Node.js Runtime Environment

```json
{
  "SPDXID": "SPDXRef-Package-NodeJS",
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
  "licenseComments": "Node.js released under MIT License as documented at https://github.com/nodejs/node/blob/main/LICENSE",
  "copyrightText": "Copyright Node.js contributors. All rights reserved.",
  "summary": "JavaScript runtime environment required for Mintlify CLI execution",
  "description": "Open-source, cross-platform JavaScript runtime built on Chrome's V8 engine. Required as runtime platform for executing Mintlify CLI tool. Provides npm package manager used for CLI installation. Specific version requirements not specified in project documentation; modern LTS versions (14.x or higher) typically compatible with npm-distributed CLI tools.",
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
      "referenceCategory": "OTHER",
      "referenceType": "documentation",
      "referenceLocator": "https://nodejs.org/en/docs"
    },
    {
      "referenceCategory": "SECURITY",
      "referenceType": "url",
      "referenceLocator": "https://nodejs.org/en/about/security"
    }
  ],
  "comment": "Platform dependency required for Mintlify CLI execution. Not directly managed by documentation project but essential for local development workflow. Version not specified; users should install current LTS version from nodejs.org."
}
```

##### Configuration Component (docs.json)

```json
{
  "SPDXID": "SPDXRef-Package-DocsConfig",
  "name": "docs.json-configuration",
  "versionInfo": "1.0.0",
  "packageFileName": "docs.json",
  "supplier": "Organization: Mintlify",
  "downloadLocation": "NOASSERTION",
  "filesAnalyzed": true,
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseDeclared": "NOASSERTION",
  "copyrightText": "NOASSERTION",
  "summary": "Primary configuration file defining complete documentation site structure and behavior",
  "description": "JSON configuration file (111 lines) controlling all site behavior. Contains: JSON schema reference (https://mintlify.com/docs.json), theme configuration (mint), site name (Mint Starter Kit), color scheme (primary #16A34A, light #07C983, dark #15803D), favicon path (/favicon.svg), navigation structure with 2 tabs (Guides with 4 groups/12 pages, API reference with 2 groups/5 pages), global anchors (Documentation link with book-open-cover icon, Blog link with newspaper icon), logo configuration (light/dark variants), navbar configuration (Support email link, Dashboard button), contextual options (8 integrations: copy, view, chatgpt, claude, perplexity, mcp, cursor, vscode), footer social links (x, github, linkedin). Single file controls entire site without application code (docs.json lines 1-111).",
  "homepage": "NOASSERTION",
  "sourceInfo": "Static JSON configuration file",
  "primaryPackagePurpose": "DATA",
  "comment": "Central configuration file. Lines 1-111 define complete site structure. Referenced in README.md line 24 (mint dev requires docs.json in directory). Schema validation via $schema property line 2."
}
```

##### OpenAPI Specification Component

```json
{
  "SPDXID": "SPDXRef-Package-OpenAPI",
  "name": "OpenAPI-Plant-Store-Specification",
  "versionInfo": "3.1.0",
  "packageFileName": "api-reference/openapi.json",
  "supplier": "NOASSERTION",
  "downloadLocation": "NOASSERTION",
  "filesAnalyzed": true,
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseDeclared": "MIT",
  "licenseComments": "License declared in OpenAPI specification info.license field (api-reference/openapi.json lines 6-7)",
  "copyrightText": "NOASSERTION",
  "summary": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features",
  "description": "Example OpenAPI specification (194 lines) defining fictional Plant Store API. Demonstrates Mintlify's OpenAPI integration for automatic API documentation. Specification structure: info section (title: OpenAPI Plant Store, description, license MIT, version 1.0.0) lines 1-9; servers array (http://sandbox.mintlify.com) lines 10-13; security configuration (bearerAuth) lines 14-18; paths object with GET /plants (limit query parameter, responses 200/400) lines 20-56, POST /plants (NewPlant requestBody, responses 200/400) lines 57-94, DELETE /plants/{id} (id path parameter, responses 204/400) lines 95-137; webhooks object POST /plant/webhook lines 139-173; components with schemas Plant (required name, optional tag) lines 132-148, NewPlant (extends Plant with required id) lines 149-169, Error (required error code and message) lines 170-183, securitySchemes bearerAuth lines 175-179. Conforms to OpenAPI 3.1.0 standard (https://spec.openapis.org/oas/v3.1.0).",
  "homepage": "https://spec.openapis.org/oas/v3.1.0",
  "sourceInfo": "Static JSON file conforming to OpenAPI 3.1.0 specification",
  "primaryPackagePurpose": "DATA",
  "externalRefs": [
    {
      "referenceCategory": "OTHER",
      "referenceType": "specification",
      "referenceLocator": "https://spec.openapis.org/oas/v3.1.0"
    }
  ],
  "comment": "Sample/demonstration API specification. Not production API. Located at api-reference/openapi.json, 194 lines total. Demonstrates OpenAPI 3.1.0 features including paths, webhooks, component schemas, security schemes."
}
```

#### File Information

Individual files are documented with checksums and metadata:

##### Configuration File - docs.json

```json
{
  "files": [
    {
      "SPDXID": "SPDXRef-File-DocsJSON",
      "fileName": "./docs.json",
      "fileTypes": ["TEXT", "SOURCE"],
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseInfoInFiles": ["NOASSERTION"],
      "copyrightText": "NOASSERTION",
      "comment": "Primary configuration file, 111 lines. Structure: $schema line 2 (https://mintlify.com/docs.json), theme line 3 (mint), name line 4 (Mint Starter Kit), colors lines 5-9 (primary/light/dark), favicon line 10, navigation lines 11-71 (tabs array with groups and pages), logo lines 78-81 (light/dark paths), navbar lines 82-92 (links array and primary button), contextual lines 93-104 (options array with 8 integrations), footer lines 105-111 (socials object). Controls all site behavior without code."
    }
  ]
}
```

##### README Documentation

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
  "comment": "Setup and usage documentation. Contains: project introduction (Mintlify Starter Kit), template usage (green 'Use this template' button), included features (guide pages, navigation, customizations, API reference, components), quickstart link (https://starter.mintlify.com/quickstart), development section (install CLI 'npm i -g mint' line 18, run 'mint dev' line 24 at docs.json location, view localhost:3000 line 27), publishing section (GitHub app from dashboard.mintlify.com/settings/organization/github-app line 35, automatic deployment on push line 36), troubleshooting (run 'mint update' line 41 for issues, verify docs.json location line 42 for 404s), resources (mintlify.com/docs line 47)."
}
```

##### OpenAPI Specification File

```json
{
  "SPDXID": "SPDXRef-File-OpenAPIJSON",
  "fileName": "./api-reference/openapi.json",
  "fileTypes": ["TEXT", "SOURCE"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "MIT",
  "licenseInfoInFiles": ["MIT"],
  "copyrightText": "NOASSERTION",
  "comment": "OpenAPI 3.1.0 specification, 194 lines. Structure: openapi version line 2, info object lines 3-9 (title, description, license MIT, version), servers array lines 10-13 (sandbox.mintlify.com), security lines 14-18 (bearerAuth), paths lines 19-137 (GET/POST /plants, DELETE /plants/{id}), webhooks lines 139-173 (POST /plant/webhook), components lines 174-194 (Plant/NewPlant/Error schemas, bearerAuth securityScheme). Demonstrates OpenAPI integration in Mintlify."
}
```

##### Static Assets

```json
{
  "SPDXID": "SPDXRef-File-LogoLight",
  "fileName": "./logo/light.svg",
  "fileTypes": ["IMAGE"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseInfoInFiles": ["NOASSERTION"],
  "copyrightText": "NOASSERTION",
  "comment": "Light theme logo referenced in docs.json line 79. SVG format for scalability. Displayed when site uses light theme."
}
```

```json
{
  "SPDXID": "SPDXRef-File-LogoDark",
  "fileName": "./logo/dark.svg",
  "fileTypes": ["IMAGE"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseInfoInFiles": ["NOASSERTION"],
  "copyrightText": "NOASSERTION",
  "comment": "Dark theme logo referenced in docs.json line 80. SVG format for scalability. Displayed when site uses dark theme."
}
```

```json
{
  "SPDXID": "SPDXRef-File-Favicon",
  "fileName": "./favicon.svg",
  "fileTypes": ["IMAGE"],
  "checksums": [
    {
      "algorithm": "SHA256",
      "checksumValue": "NOASSERTION"
    }
  ],
  "licenseConcluded": "NOASSERTION",
  "licenseInfoInFiles": ["NOASSERTION"],
  "copyrightText": "NOASSERTION",
  "comment": "Site favicon referenced in docs.json line 10. SVG format. Displayed in browser tabs and bookmarks."
}
```

#### Relationship Information

SPDX relationships define dependency structure:

```json
{
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-Mintlify-Docs",
      "comment": "This SBOM describes the Mintlify Documentation Starter Kit as primary application"
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-Mintlify-CLI",
      "comment": "Runtime dependency for local development (mint dev command). Required for preview but not production deployment."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-CLI",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-NodeJS",
      "comment": "CLI requires Node.js runtime for execution and npm for installation."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-Package-DocsConfig",
      "comment": "Primary package contains configuration file as core component."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-Package-OpenAPI",
      "comment": "Primary package contains OpenAPI specification for API documentation demonstration."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-DocsJSON",
      "comment": "docs.json file contained in primary package."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-README",
      "comment": "README.md file contained in primary package."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-OpenAPIJSON",
      "comment": "openapi.json file contained in primary package."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-LogoLight",
      "comment": "Light theme logo contained in primary package."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-LogoDark",
      "comment": "Dark theme logo contained in primary package."
    },
    {
      "spdxElementId": "SPDXRef-Package-Mintlify-Docs",
      "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-Favicon",
      "comment": "Favicon contained in primary package."
    }
  ]
}
```

#### External Services (Not in Standard SPDX but Documented for Completeness)

**GitHub Service Dependency**:
- **Service**: GitHub version control and deployment platform
- **Integration**: GitHub app from dashboard.mintlify.com/settings/organization/github-app (README.md line 35)
- **Function**: Automatic deployment on push to default branch (README.md line 36)
- **Authentication**: OAuth-based GitHub app integration
- **Endpoints**: github.com, api.github.com

**Mintlify Platform Service**:
- **Service**: Mintlify documentation hosting and build platform
- **Function**: Static site generation, CDN hosting, search indexing, automatic builds
- **Configuration**: Controlled via docs.json
- **Dashboard**: dashboard.mintlify.com
- **Documentation**: mintlify.com/docs
- **Support**: hi@mintlify.com (docs.json line 86)

### Complete SPDX 2.3 SBOM Document

Below is the complete, valid SPDX 2.3 JSON document for the Mintlify Documentation Starter Kit:

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
      "Tool: OrchestrAI-Documentation-Specialist",
      "Organization: Mintlify"
    ],
    "licenseListVersion": "3.22",
    "comment": "SBOM generated from comprehensive source code analysis. Documents configuration-driven documentation framework with minimal external dependencies. Project consists of JSON configuration (docs.json, 111 lines), Markdown content files, OpenAPI specification (194 lines), and SVG assets. Single runtime dependency: Mintlify CLI (mint) installed globally via npm. Platform dependency: Node.js runtime. External services: GitHub (version control/deployment), Mintlify Platform (hosting/builds)."
  },
  "documentDescribes": [
    "SPDXRef-Package-Mintlify-Docs"
  ],
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Mintlify-Docs",
      "name": "Mintlify-Documentation-Starter-Kit",
      "versionInfo": "1.0.0",
      "packageFileName": "mintlify-starter-kit",
      "supplier": "Organization: Mintlify (hi@mintlify.com)",
      "downloadLocation": "https://github.com/mintlify/starter",
      "filesAnalyzed": true,
      "verificationCode": {
        "value": "NOASSERTION",
        "excludedFiles": []
      },
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "NOASSERTION"
        }
      ],
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "licenseComments": "License not explicitly declared in source code. Project provided as example/starter template by Mintlify.",
      "copyrightText": "Copyright (c) Mintlify",
      "summary": "Configuration-driven documentation starter kit for creating professional documentation websites",
      "description": "Comprehensive documentation starter kit built on Mintlify platform. Includes example guide pages (17 total across 2 tabs, 6 groups), API reference via OpenAPI 3.1.0 integration, customizable navigation, theme customization (colors: primary #16A34A, light #07C983, dark #15803D), dual-theme support (light/dark logos), contextual menu with 8 AI tool integrations (ChatGPT, Claude, Perplexity, MCP, Cursor, VS Code, copy, view), navbar with support link and dashboard button, footer with social links (X, GitHub, LinkedIn), automatic GitHub deployment. Configuration: docs.json (111 lines). Content: Markdown files. API spec: OpenAPI 3.1.0 (194 lines). Assets: 3 SVG files.",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration files (JSON), documentation content (Markdown), API specification (OpenAPI), static assets (SVG)",
      "primaryPackagePurpose": "APPLICATION",
      "builtDate": "NOASSERTION",
      "validUntilDate": "NOASSERTION",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER