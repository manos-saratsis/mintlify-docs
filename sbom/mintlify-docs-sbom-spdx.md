# Software Bill of Materials (SBOM) - SPDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) in SPDX 2.3 format for the **Mintlify Documentation Starter Kit** project. The SPDX (Software Package Data Exchange) format is an open standard (ISO/IEC 5962:2021) developed by the Linux Foundation for communicating software component information, including licenses, copyrights, security references, and supply chain provenance.

**Purpose of This SBOM:**

This SBOM serves multiple critical functions:

1. **License Compliance**: Documenting all software licenses to ensure legal compliance with open source licensing obligations
2. **Security Transparency**: Enabling vulnerability scanning and security assessments across the software supply chain
3. **Supply Chain Risk Management**: Providing visibility into component sources, dependencies, and potential supply chain vulnerabilities
4. **Regulatory Compliance**: Meeting requirements for software composition transparency mandated by regulations such as Executive Order 14028
5. **Dependency Tracking**: Maintaining comprehensive visibility into direct and transitive dependencies throughout the software lifecycle

**Project Context: Mintlify Documentation Starter Kit**

The Mintlify Documentation Starter Kit represents a unique architectural approach to documentation generation. Unlike traditional web applications with extensive runtime dependency trees, this project operates as a **configuration-driven static documentation framework** with minimal external dependencies.

**Architectural Characteristics:**

- **Configuration-First Design**: All site behavior is defined through the `docs.json` configuration file (111 lines)
- **Content-Driven**: Documentation content exists as Markdown files with no application code
- **Minimal Dependencies**: Single external dependency on the Mintlify CLI tool (`mint`)
- **Static Generation**: No runtime frameworks, libraries, or application code in the traditional sense
- **Cloud-Based Build**: Build and deployment processes are handled entirely by Mintlify's cloud infrastructure

**Critical Finding**: This project does **NOT** contain traditional dependency manifest files (`package.json`, `package-lock.json`, `requirements.txt`, `Gemfile`, `pom.xml`, etc.). The absence of these files reflects the project's fundamental architectural difference from conventional software applications.

**Single Runtime Dependency:**

The only external dependency is the **Mintlify CLI (`mint`)**, which:

- Is installed globally via npm: `npm i -g mint` (per `README.md` line 18)
- Provides local development preview: `mint dev` command (README.md line 24)
- Is updated via: `mint update` command (README.md line 41)
- Exists outside the project repository due to global installation pattern
- Is not tracked within the project directory structure itself

This global installation approach means the dependency exists in the user's system-wide npm directory rather than as a project-specific dependency, requiring special consideration in SBOM generation and supply chain analysis.

## Implementation

### Project Structure Analysis

The Mintlify Documentation Starter Kit follows a flat, documentation-focused directory structure optimized for content organization:

```
mintlify-documentation-starter-kit/
├── docs.json                      # Primary configuration file (111 lines)
├── README.md                      # Setup and usage instructions
├── favicon.svg                    # Site favicon
├── logo/
│   ├── light.svg                 # Light theme logo
│   └── dark.svg                  # Dark theme logo
├── api-reference/
│   ├── openapi.json              # OpenAPI 3.1.0 specification (194 lines)
│   ├── introduction.md           # API documentation introduction
│   └── endpoint/
│       ├── get.md               # GET endpoint documentation
│       ├── create.md            # POST endpoint documentation
│       ├── delete.md            # DELETE endpoint documentation
│       └── webhook.md           # Webhook documentation
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
├── api-docs.md                   # Comprehensive API documentation
├── architecture.md               # Architecture documentation
├── component-docs.md             # Component documentation
├── concepts.md                   # Concepts documentation
├── feature-guides.md             # Feature guides
├── getting-started.md            # Getting started guide
├── how_to.md                     # How-to guides
├── intro.md                      # Quick start introduction
├── reference.md                  # API reference
├── tutorials.md                  # Tutorial documentation
└── sbom/
    ├── mintlify-docs-sbom-spdx.md      # SPDX SBOM documentation
    └── mintlify-docs-sbom-cyclonedx.md # CycloneDX SBOM documentation
```

**File Type Distribution:**

- **Configuration**: 1 JSON file (`docs.json`)
- **API Specification**: 1 JSON file (`openapi.json`)
- **Documentation**: 18+ Markdown files (`.md` extension)
- **Assets**: 3 SVG files (logo variants and favicon)

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
      "Tool: OrchestrAI-Documentation-Specialist",
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

**Field Definitions:**

- **spdxVersion**: SPDX specification version (`SPDX-2.3`)
- **dataLicense**: Required CC0-1.0 public domain dedication for SPDX documents per specification
- **SPDXID**: Unique identifier for this SPDX document (`SPDXRef-DOCUMENT`)
- **name**: Human-readable name for this SBOM instance
- **documentNamespace**: Unique URI identifying this specific SBOM version (includes timestamp for uniqueness)
- **created**: ISO 8601 timestamp indicating when this SBOM was generated
- **creators**: Tools and organizations responsible for SBOM creation
- **licenseListVersion**: SPDX License List version used (3.22 is current as of 2024)
- **documentDescribes**: References to primary packages described by this SBOM

#### Package Information

This section documents all software packages and components within the project.

**Primary Application Package:**

```json
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
  "licenseComments": "License information not explicitly declared in source code. Project appears to be provided as example/starter template by Mintlify.",
  "copyrightText": "NOASSERTION",
  "summary": "Mintlify documentation starter kit providing templates and configuration for creating professional documentation websites",
  "description": "A comprehensive documentation starter kit built on the Mintlify platform. Includes example guide pages, API reference capabilities, navigation structures, theme customization options, and AI tool integrations. The project is configuration-driven, with all site behavior defined through docs.json and content provided as Markdown files. Features include: dual-theme support (light/dark), OpenAPI 3.1.0 integration for API documentation, contextual menu options for AI tool integration (ChatGPT, Claude, Perplexity, Cursor, VS Code), social media footer links, and automatic deployment via GitHub integration.",
  "homepage": "https://mintlify.com/docs",
  "sourceInfo": "Configuration-driven documentation framework consisting of JSON configuration, Markdown content, OpenAPI specification, and SVG assets",
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
    },
    {
      "referenceCategory": "OTHER",
      "referenceType": "vcs",
      "referenceLocator": "https://github.com/mintlify/starter"
    }
  ],
  "comment": "This package represents the complete Mintlify Documentation Starter Kit. It is not a traditional software application with compiled code, but rather a configuration and content package that leverages the Mintlify platform for static site generation and hosting. The package includes: 1 configuration file (docs.json - 111 lines), 18+ markdown documentation files, 1 OpenAPI specification file (194 lines), and 3 SVG asset files."
}
```

**Mintlify CLI Dependency Package:**

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
  "licenseComments": "License information not available from npm package metadata in provided source code. License should be verified from npmjs.com package page.",
  "copyrightText": "Copyright (c) Mintlify",
  "summary": "Mintlify CLI tool for local documentation preview and development",
  "description": "Command-line interface tool for the Mintlify documentation platform. Provides local development server with hot reload capabilities on port 3000, validation of docs.json configuration, and deployment management. Installed globally via npm (npm i -g mint). Primary commands include: 'mint dev' for local preview server, 'mint update' for updating to latest CLI version. The CLI is required for local documentation development but not needed for production deployment, which is handled by the Mintlify GitHub app integration.",
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
    },
    {
      "referenceCategory": "OTHER",
      "referenceType": "documentation",
      "referenceLocator": "https://mintlify.com/docs"
    }
  ],
  "comment": "Runtime dependency for local development only. Installed globally via npm rather than as project dependency. Version specified as 'latest' per README.md installation instructions (line 18). This CLI tool is not bundled with the documentation project but is required for local preview functionality via the 'mint dev' command (README.md line 24)."
}
```

**Node.js Runtime Environment Package:**

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
  "licenseComments": "Node.js is released under the MIT License as documented at https://github.com/nodejs/node/blob/main/LICENSE",
  "copyrightText": "Copyright Node.js contributors. All rights reserved.",
  "summary": "JavaScript runtime environment required for Mintlify CLI execution",
  "description": "Node.js is an open-source, cross-platform JavaScript runtime environment built on Chrome's V8 JavaScript engine. Required as the runtime platform for executing the Mintlify CLI tool (mint). Provides the npm package manager used for CLI installation via 'npm i -g mint'. Specific version requirements not specified in project documentation, but modern LTS versions (14.x or higher) are typically compatible with npm-distributed CLI tools.",
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
  "comment": "Platform dependency required for Mintlify CLI execution. Not directly managed by the documentation project but essential for local development workflow. Version not specified in project documentation; users should install current LTS version from nodejs.org."
}
```

**OpenAPI Specification Component Package:**

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
  "licenseComments": "License declared within OpenAPI specification info.license field (api-reference/openapi.json lines 6-8)",
  "copyrightText": "NOASSERTION",
  "summary": "Sample OpenAPI 3.1.0 specification demonstrating API documentation features",
  "description": "Example OpenAPI specification file defining a fictional Plant Store API. Demonstrates Mintlify's OpenAPI integration capabilities for automatic API documentation generation. Specification includes: server configuration (http://sandbox.mintlify.com), bearer token authentication scheme, three REST endpoints (GET /plants with limit parameter, POST /plants for creation, DELETE /plants/{id} for deletion), webhook definition (POST /plant/webhook), and three data schemas (Plant with required name and optional tag, NewPlant extending Plant with required id field, Error with required error code and message). Total specification length: 194 lines. Specification follows OpenAPI 3.1.0 standard as documented at https://spec.openapis.org/oas/v3.1.0.",
  "homepage": "https://spec.openapis.org/oas/v3.1.0",
  "sourceInfo": "Static data file in JSON format conforming to OpenAPI 3.1.0 specification",
  "primaryPackagePurpose": "DATA",
  "externalRefs": [
    {
      "referenceCategory": "OTHER",
      "referenceType": "specification",
      "referenceLocator": "https://spec.openapis.org/oas/v3.1.0"
    }
  ],
  "comment": "This is a sample/example API specification included as a demonstration of Mintlify's OpenAPI integration capabilities. It is not a production API. The specification is located at api-reference/openapi.json and is 194 lines in length. It demonstrates OpenAPI 3.1.0 features including paths, webhooks, components/schemas, and security schemes."
}
```

#### File Information Section

This section documents individual files with checksums, licenses, and metadata.

**Configuration File - docs.json:**

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
  "licenseInfoInFiles": ["NOASSERTION"],
  "copyrightText": "NOASSERTION",
  "noticeText": "NOASSERTION",
  "comment": "Primary configuration file (111 lines) defining complete documentation site structure and behavior. Contains: JSON schema reference (https://mintlify.com/docs.json - line 2), theme configuration (mint theme - line 3), site name (Mint Starter Kit - line 4), color scheme (primary: #16A34A, light: #07C983, dark: #15803D - lines 5-9), favicon path (/favicon.svg - line 10), navigation structure with 2 tabs (lines 11-77): Guides tab with 4 groups containing 12 pages total (Getting started, Customization, Writing content, AI tools), API reference tab with 2 groups containing 5 pages (API documentation, Endpoint examples), global anchors (Documentation link to mintlify.com/docs with book-open-cover icon, Blog link to mintlify.com/blog with newspaper icon - lines 66-77), logo configuration (light: /logo/light.svg, dark: /logo/dark.svg - lines 78-81), navbar configuration (Support email link to hi@mintlify.com, Dashboard primary button linking to dashboard.mintlify.com - lines 82-92), contextual options (copy, view, chatgpt, claude, perplexity, mcp, cursor, vscode - lines 93-104), footer social links (x: x.com/mintlify, github: github.com/mintlify, linkedin: linkedin.com/company/mintlify - lines 105-111). This single file controls all site behavior without requiring application code.",
  "fileContributors": ["Organization: Mintlify"]
}
```

**Setup Documentation - README.md:**

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
  "comment": "Setup and usage documentation file. Contains: project introduction (Mintlify Starter Kit for documentation deployment), template usage instructions (green 'Use this template' button to copy repo), included features list (guide pages, navigation, customizations, API reference, popular components), link to full quickstart guide (https://starter.mintlify.com/quickstart - line 14), development setup section (install Mintlify CLI via 'npm i -g mint' - line 18, run 'mint dev' at root where docs.json is located - lines 24-26, view at http://localhost:3000 - line 28), publishing section (install GitHub app from dashboard.mintlify.com/settings/organization/github-app - line 32, automatic deployment on push to default branch), troubleshooting section (run 'mint update' for environment issues - line 41, verify docs.json location for 404 errors - line 42), resources section (Mintlify documentation at mintlify.com/docs - line 46).",
  "fileContributors": ["Organization: Mintlify"]
}
```

**OpenAPI Specification File - api-reference/openapi.json:**

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
  "comment": "OpenAPI 3.1.0 specification file (194 lines) defining sample Plant Store API. Structure: info section (lines 2-9: title: OpenAPI Plant Store, description, license: MIT, version: 1.0.0), servers array (lines 10-13: single server at http://sandbox.mintlify.com), security array (lines 14-18: bearerAuth requirement), paths object containing GET /plants endpoint (lines 20-56: query param 'limit' of type integer/int32, responses 200 with Plant array, 400 with Error), POST /plants endpoint (lines 57-94: requestBody with NewPlant schema required, responses 200 with Plant, 400 with Error), DELETE /plants/{id} endpoint (lines 95-137: path param 'id' required integer/int64, responses 204 plant deleted, 400 with Error), webhooks object containing POST /plant/webhook (lines 139-173: requestBody with NewPlant, response 200 success), components object with schemas (lines 152-194: Plant: required name string, optional tag string; NewPlant: allOf extending Plant with required id integer/int64; Error: required error integer/int32 and message string) and securitySchemes (lines 175-179: bearerAuth: type http, scheme bearer). This specification demonstrates OpenAPI integration capabilities within Mintlify documentation platform.",
  "fileContributors": ["NOASSERTION"]
}
```

#### Relationship Information Section

SPDX relationships define the dependency structure and containment hierarchy:

**Document Description Relationships:**

```json
{
  "spdxElementId": "SPDXRef-DOCUMENT",
  "relationshipType": "DESCRIBES",
  "relatedSpdxElement": "SPDXRef-Package-Mintlify-Docs-Starter",
  "comment": "This SBOM document describes the Mintlify Documentation Starter Kit as the primary application package"
}
```

**Package Dependency Relationships:**

```json
{
  "spdxElementId": "SPDXRef-Package-Mintlify-Docs-Starter",
  "relationshipType": "DEPENDS_ON",
  "relatedSpdxElement": "SPDXRef-Package-Mintlify-CLI",
  "comment": "Runtime dependency for local development workflow (mint dev command). Required for local preview but not for production deployment which uses GitHub app integration."
},
{
  "spdxElementId": "SPDXRef-Package-Mintlify-CLI",
  "relationshipType": "DEPENDS_ON",
  "relatedSpdxElement": "SPDXRef-Package-NodeJS-Runtime",
  "comment": "Mintlify CLI requires Node.js runtime environment for execution"
}
```

**Package Containment Relationships:**

```json
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
```

### Complete SPDX 2.3 SBOM

Based on comprehensive analysis of the project structure, configuration files, and documentation, here is the complete SPDX 2.3 SBOM:

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
      "licenseComments": "License information not explicitly declared in source code. Project appears to be provided as example/starter template by Mintlify.",
      "copyrightText": "NOASSERTION",
      "summary": "Mintlify documentation starter kit providing templates and configuration for creating professional documentation websites",
      "description": "A comprehensive documentation starter kit built on the Mintlify platform. Includes example guide pages, API reference capabilities, navigation structures, theme customization options, and AI tool integrations. The project is configuration-driven, with all site behavior defined through docs.json and content provided as Markdown files. Features include: dual-theme support (light/dark), OpenAPI 3.1.0 integration for API documentation, contextual menu options for AI tool integration (ChatGPT, Claude, Perplexity, Cursor, VS Code), social media footer links, and automatic deployment via GitHub integration.",
      "homepage": "https://mintlify.com/docs",
      "sourceInfo": "Configuration-driven documentation framework consisting of JSON configuration, Markdown content, OpenAPI specification, and SVG assets",
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
        },
        {
          "referenceCategory": "OTHER",
          "referenceType": "vcs",
          "referenceLocator": "https://github.com/mintlify/starter"
        }
      ],
      "comment": "This package represents the complete Mintlify Documentation Starter Kit. It is not a traditional software application with compiled code, but rather a configuration and content package that leverages the Mintlify platform for static site generation and hosting. The package includes: 1 configuration file (docs.json - 111 lines), 18+ markdown documentation files, 1 OpenAPI specification file (194 lines), and 3 SVG asset files."
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
      "licenseComments": "License information not available from npm package metadata in provided source