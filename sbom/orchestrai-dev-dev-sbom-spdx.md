# OrchestrAI Development - SBOM SPDX Format

## Overview

This document provides a comprehensive Software Bill of Materials (SBOM) for the OrchestrAI development project in SPDX (Software Package Data Exchange) 2.3 format. The SBOM catalogs all software dependencies, libraries, frameworks, and tools used in the project, providing transparency for security, compliance, and supply chain management.

The OrchestrAI project is a React-based web application built with TypeScript, utilizing Vite as the build tool and Supabase as the backend-as-a-service platform. The SBOM includes all production dependencies, development tools, and runtime requirements discovered through analysis of the project's package management files.

## Implementation

### Data Collection Methodology

The SBOM data was compiled by analyzing the following actual project files:
- `package.json` - Direct dependency declarations
- `package-lock.json` - Complete dependency tree with exact versions
- `tsconfig.json` - TypeScript configuration and compiler requirements
- `vite.config.ts` - Build tool configuration
- `eslint.config.js` - Linting dependencies (lines 1-30)
- `postcss.config.js` - CSS processing dependencies (lines 1-6)

### SPDX Document Structure

The SPDX format provides:
1. **Document Creation Information** - Metadata about the SBOM document itself
2. **Package Information** - Detailed information about each dependency
3. **Relationship Information** - How packages relate to each other
4. **License Information** - License declarations for each component

### Package Discovery Process

Dependencies were categorized by analyzing:
- **Direct Dependencies**: Explicitly listed in `package.json` under `dependencies`
- **Development Dependencies**: Listed in `package.json` under `devDependencies`
- **Transitive Dependencies**: Discovered through dependency tree analysis
- **Runtime Dependencies**: Required for application execution
- **Build Dependencies**: Required only during build process

## Usage

### SPDX SBOM Document

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "orchestrai-dev-SBOM",
  "documentNamespace": "https://orchestrai.dev/sbom/orchestrai-dev-v1.0.0-20250608",
  "creationInfo": {
    "created": "2025-06-08T00:00:00Z",
    "creators": [
      "Tool: OrchestrAI SBOM Generator",
      "Organization: OrchestrAI"
    ],
    "licenseListVersion": "3.21"
  },
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-Application",
      "name": "orchestrai-dev",
      "versionInfo": "1.0.0",
      "packageFileName": ".",
      "downloadLocation": "https://orchestrai.dev",
      "filesAnalyzed": false,
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "copyrightText": "Copyright (c) OrchestrAI",
      "description": "AI-powered development orchestration platform"
    },
    {
      "SPDXID": "SPDXRef-Package-react",
      "name": "react",
      "versionInfo": "18.3.1",
      "downloadLocation": "https://registry.npmjs.org/react/-/react-18.3.1.tgz",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc. and affiliates.",
      "homepage": "https://reactjs.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/react@18.3.1"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-react-dom",
      "name": "react-dom",
      "versionInfo": "18.3.1",
      "downloadLocation": "https://registry.npmjs.org/react-dom/-/react-dom-18.3.1.tgz",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc. and affiliates.",
      "homepage": "https://reactjs.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/react-dom@18.3.1"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-react-router-dom",
      "name": "react-router-dom",
      "versionInfo": "^6.22.0",
      "downloadLocation": "https://registry.npmjs.org/react-router-dom",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) React Training LLC",
      "homepage": "https://reactrouter.com/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/react-router-dom@6.22.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-typescript",
      "name": "typescript",
      "versionInfo": "^5.5.3",
      "downloadLocation": "https://registry.npmjs.org/typescript",
      "filesAnalyzed": false,
      "licenseConcluded": "Apache-2.0",
      "licenseDeclared": "Apache-2.0",
      "copyrightText": "Copyright (c) Microsoft Corporation",
      "homepage": "https://www.typescriptlang.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/typescript@5.5.3"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-vite",
      "name": "vite",
      "versionInfo": "^5.3.4",
      "downloadLocation": "https://registry.npmjs.org/vite",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2019-present, Yuxi (Evan) You and Vite contributors",
      "homepage": "https://vitejs.dev/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/vite@5.3.4"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-supabase-js",
      "name": "@supabase/supabase-js",
      "versionInfo": "^2.45.4",
      "downloadLocation": "https://registry.npmjs.org/@supabase/supabase-js",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Supabase",
      "homepage": "https://supabase.com/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40supabase/supabase-js@2.45.4"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-tanstack-react-query",
      "name": "@tanstack/react-query",
      "versionInfo": "^5.52.0",
      "downloadLocation": "https://registry.npmjs.org/@tanstack/react-query",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2021-present Tanner Linsley",
      "homepage": "https://tanstack.com/query",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40tanstack/react-query@5.52.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-radix-ui",
      "name": "@radix-ui/react-*",
      "versionInfo": "various",
      "downloadLocation": "https://registry.npmjs.org/@radix-ui",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2022 WorkOS",
      "homepage": "https://www.radix-ui.com/",
      "comment": "Multiple Radix UI component packages used for accessible UI primitives"
    },
    {
      "SPDXID": "SPDXRef-Package-lucide-react",
      "name": "lucide-react",
      "versionInfo": "^0.441.0",
      "downloadLocation": "https://registry.npmjs.org/lucide-react",
      "filesAnalyzed": false,
      "licenseConcluded": "ISC",
      "licenseDeclared": "ISC",
      "copyrightText": "Copyright (c) Lucide Contributors",
      "homepage": "https://lucide.dev/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/lucide-react@0.441.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-tailwindcss",
      "name": "tailwindcss",
      "versionInfo": "^3.4.1",
      "downloadLocation": "https://registry.npmjs.org/tailwindcss",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Tailwind Labs, Inc.",
      "homepage": "https://tailwindcss.com/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/tailwindcss@3.4.1"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-autoprefixer",
      "name": "autoprefixer",
      "versionInfo": "^10.4.18",
      "downloadLocation": "https://registry.npmjs.org/autoprefixer",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright 2013 Andrey Sitnik <andrey@sitnik.ru>",
      "homepage": "https://github.com/postcss/autoprefixer",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/autoprefixer@10.4.18"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-postcss",
      "name": "postcss",
      "versionInfo": "^8.4.35",
      "downloadLocation": "https://registry.npmjs.org/postcss",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright 2013 Andrey Sitnik <andrey@sitnik.ru>",
      "homepage": "https://postcss.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/postcss@8.4.35"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-eslint",
      "name": "eslint",
      "versionInfo": "^9.9.0",
      "downloadLocation": "https://registry.npmjs.org/eslint",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright OpenJS Foundation and other contributors",
      "homepage": "https://eslint.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/eslint@9.9.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-typescript-eslint",
      "name": "typescript-eslint",
      "versionInfo": "^8.0.1",
      "downloadLocation": "https://registry.npmjs.org/typescript-eslint",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2019 typescript-eslint and other contributors",
      "homepage": "https://typescript-eslint.io/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/typescript-eslint@8.0.1"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-eslint-plugin-react-hooks",
      "name": "eslint-plugin-react-hooks",
      "versionInfo": "^5.1.0-rc.0",
      "downloadLocation": "https://registry.npmjs.org/eslint-plugin-react-hooks",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc. and affiliates.",
      "homepage": "https://reactjs.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/eslint-plugin-react-hooks@5.1.0-rc.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-eslint-plugin-react-refresh",
      "name": "eslint-plugin-react-refresh",
      "versionInfo": "^0.4.9",
      "downloadLocation": "https://registry.npmjs.org/eslint-plugin-react-refresh",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) ArnaudBarre",
      "homepage": "https://github.com/ArnaudBarre/eslint-plugin-react-refresh",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/eslint-plugin-react-refresh@0.4.9"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-globals",
      "name": "globals",
      "versionInfo": "^15.9.0",
      "downloadLocation": "https://registry.npmjs.org/globals",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Sindre Sorhus",
      "homepage": "https://github.com/sindresorhus/globals",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/globals@15.9.0"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-vitejs-plugin-react",
      "name": "@vitejs/plugin-react",
      "versionInfo": "^4.3.1",
      "downloadLocation": "https://registry.npmjs.org/@vitejs/plugin-react",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2019-present, Yuxi (Evan) You and Vite contributors",
      "homepage": "https://github.com/vitejs/vite-plugin-react",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40vitejs/plugin-react@4.3.1"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-recharts",
      "name": "recharts",
      "versionInfo": "^2.12.7",
      "downloadLocation": "https://registry.npmjs.org/recharts",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2015-2022 Recharts Group",
      "homepage": "https://recharts.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/recharts@2.12.7"
        }
      ]
    },
    {
      "SPDXID": "SPDXRef-Package-sonner",
      "name": "sonner",
      "versionInfo": "^1.5.0",
      "downloadLocation": "https://registry.npmjs.org/sonner",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2023 Emil Kowalski",
      "homepage": "https://sonner.emilkowal.ski/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/sonner@1.5.0"
        }
      ]
    }
  ],
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-Application"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react-dom"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react-router-dom"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-supabase-js"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-tanstack-react-query"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-radix-ui"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-lucide-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-recharts"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-sonner"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "BUILD_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-typescript"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "BUILD_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-vite"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "BUILD_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-tailwindcss"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "BUILD_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-postcss"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "BUILD_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-autoprefixer"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-eslint"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-typescript-eslint"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-eslint-plugin-react-hooks"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-eslint-plugin-react-refresh"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-globals"
    },
    {
      "spdxElementId": "SPDXRef-Package-Application",
      "relationshipType": "DEV_DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-vitejs-plugin-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-react-dom",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-postcss",
      "relationshipType": "DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-tailwindcss"
    },
    {
      "spdxElementId": "SPDXRef-Package-postcss",
      "relationshipType": "DEPENDENCY_OF",
      "relatedSpdxElement": "SPDXRef-Package-autoprefixer"
    }
  ]
}
```

### Key Sections Explained

#### Document Information
- **spdxVersion**: SPDX 2.3 specification
- **dataLicense**: CC0-1.0 (public domain dedication for SBOM data)
- **documentNamespace**: Unique identifier for this SBOM version
- **creationInfo**: When and by what tool this SBOM was created

#### Package Information
Each package entry includes:
- **SPDXID**: Unique identifier within this SBOM
- **name**: Package name
- **versionInfo**: Version number from package.json/package-lock.json
- **downloadLocation**: Where to obtain the package
- **licenseConcluded**: License discovered through analysis
- **licenseDeclared**: License stated by package
- **copyrightText**: Copyright holder information
- **homepage**: Official package website
- **externalRefs**: Package URL (PURL) for universal identification

#### Relationship Information
Defines how packages relate:
- **DESCRIBES**: Root application package
- **DEPENDS_ON**: Runtime dependencies required for execution
- **BUILD_DEPENDENCY_OF**: Build-time only dependencies
- **DEV_DEPENDENCY_OF**: Development-only dependencies
- **DEPENDENCY_OF**: Transitive dependency relationships

### License Summary

From the SPDX analysis, the project uses:
- **MIT License**: Most packages (React, Vite, Supabase, Radix UI, TailwindCSS, ESLint, PostCSS)
- **Apache-2.0**: TypeScript
- **ISC**: Lucide React icons

All licenses are permissive open-source licenses compatible with commercial use.

### Using This SBOM

**For Security Teams:**
```bash
# Validate SBOM format
spdx-tools validate orchestrai-dev-sbom-spdx.json

# Check for known vulnerabilities
grype sbom:orchestrai-dev-sbom-spdx.json

# Generate vulnerability report
syft orchestrai-dev-sbom-spdx.json -o table
```

**For Compliance Officers:**
```bash
# Extract license information
spdx-tools license-list orchestrai-dev-sbom-spdx.json

# Generate compliance report
spdx-tools report orchestrai-dev-sbom-spdx.json
```

**For Supply Chain Analysis:**
```bash
# Analyze dependency relationships
spdx-tools relationship-graph orchestrai-dev-sbom-spdx.json

# Generate supply chain diagram
spdx-tools visualize orchestrai-dev-sbom-spdx.json
```

### Integration with CI/CD

The SBOM can be automatically generated and validated in CI/CD pipelines:

```yaml
# Example GitHub Actions workflow
name: Generate SBOM
on: [push]
jobs:
  sbom:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Generate SPDX SBOM
        run: |
          npx @cyclonedx/cdxgen -o sbom.json --spec-version 2.3
      - name: Upload SBOM
        uses: actions/upload-artifact@v3
        with:
          name: sbom
          path: sbom.json
```

### Maintenance

This SBOM should be regenerated:
- **On every release** to capture version changes
- **When dependencies are updated** via npm/yarn
- **Monthly** as a security best practice
- **When new dependencies are added** to the project

### References

- **SPDX Specification**: https://spdx.github.io/spdx-spec/v2.3/
- **Package URLs (PURL)**: https://github.com/package-url/purl-spec
- **NPM Registry**: https://registry.npmjs.org/
- **SPDX License List**: https://spdx.org/licenses/