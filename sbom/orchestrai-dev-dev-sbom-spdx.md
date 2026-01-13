# orchestrai-dev-sbom-spdx.md

| Data Field | Description |
|------------|-------------|
| SBOM Author | OrchestrAI (the entity that creates the SBOM data) |
| Software Producer | The name of the entity that created/published each component |
| Component Name | The name assigned by the Software Producer to each component |
| Component Version | Version identifier for each component |
| Software Identifiers | CPE, PURL, UUID, commit hash, or other identifiers |
| Component Hash | Cryptographic hash (SHA-256, SHA-512) of the component |
| License | License(s) under which the component is available (use SPDX identifiers) |
| Dependency Relationship | Relationships (DEPENDS_ON, CONTAINS, DERIVED_FROM) |
| Tool Name | OrchestrAI (with data sources: package.json, lock files, etc.) |
| Timestamp | ISO 8601 formatted date/time of SBOM generation or last update |
| Generation Context | Lifecycle phase: before build, during build, or after build |

## Software Bill of Materials (SBOM) - SPDX 2.3 Format

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "orchestrai-dev-SBOM",
  "documentNamespace": "https://orchestrai.dev/sbom/orchestrai-dev-2025",
  "creationInfo": {
    "created": "2025-01-15T00:00:00Z",
    "creators": ["Tool: OrchestrAI"],
    "comment": "SBOM generated from source code analysis"
  },
  "annotations": [
    {
      "annotator": "Tool: OrchestrAI",
      "annotationDate": "2025-01-15T00:00:00Z",
      "annotationType": "OTHER",
      "comment": "Generation Context: Before Build / Source - Generated from source code and dependency manifests (eslint.config.js, postcss.config.js, test files)"
    }
  ],
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-eslint-js",
      "name": "@eslint/js",
      "versionInfo": "unknown",
      "supplier": "Organization: OpenJS Foundation",
      "downloadLocation": "https://registry.npmjs.org/@eslint/js",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright OpenJS Foundation and contributors",
      "homepage": "https://eslint.org",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40eslint/js"
        }
      ],
      "comment": "ESLint core JavaScript configurations - imported in eslint.config.js (line 1)"
    },
    {
      "SPDXID": "SPDXRef-Package-globals",
      "name": "globals",
      "versionInfo": "unknown",
      "supplier": "Organization: Sindre Sorhus",
      "downloadLocation": "https://registry.npmjs.org/globals",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Sindre Sorhus",
      "homepage": "https://github.com/sindresorhus/globals",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/globals"
        }
      ],
      "comment": "Global identifiers from different JavaScript environments - imported in eslint.config.js (line 2)"
    },
    {
      "SPDXID": "SPDXRef-Package-eslint-plugin-react-hooks",
      "name": "eslint-plugin-react-hooks",
      "versionInfo": "unknown",
      "supplier": "Organization: Facebook, Inc.",
      "downloadLocation": "https://registry.npmjs.org/eslint-plugin-react-hooks",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc.",
      "homepage": "https://reactjs.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/eslint-plugin-react-hooks"
        }
      ],
      "comment": "ESLint rules for React Hooks - imported in eslint.config.js (line 3)"
    },
    {
      "SPDXID": "SPDXRef-Package-eslint-plugin-react-refresh",
      "name": "eslint-plugin-react-refresh",
      "versionInfo": "unknown",
      "supplier": "Organization: Vite contributors",
      "downloadLocation": "https://registry.npmjs.org/eslint-plugin-react-refresh",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Vite contributors",
      "homepage": "https://github.com/vitejs/vite-plugin-react",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/eslint-plugin-react-refresh"
        }
      ],
      "comment": "ESLint plugin for React Refresh - imported in eslint.config.js (line 4)"
    },
    {
      "SPDXID": "SPDXRef-Package-typescript-eslint",
      "name": "typescript-eslint",
      "versionInfo": "unknown",
      "supplier": "Organization: TypeScript ESLint contributors",
      "downloadLocation": "https://registry.npmjs.org/typescript-eslint",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright TypeScript ESLint contributors",
      "homepage": "https://typescript-eslint.io",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/typescript-eslint"
        }
      ],
      "comment": "Monorepo for all TypeScript ESLint tooling - imported in eslint.config.js (line 5)"
    },
    {
      "SPDXID": "SPDXRef-Package-react",
      "name": "react",
      "versionInfo": "unknown",
      "supplier": "Organization: Facebook, Inc.",
      "downloadLocation": "https://registry.npmjs.org/react",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc.",
      "homepage": "https://reactjs.org/",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/react"
        }
      ],
      "comment": "React framework for building user interfaces - used in test files"
    },
    {
      "SPDXID": "SPDXRef-Package-testing-library-react",
      "name": "@testing-library/react",
      "versionInfo": "unknown",
      "supplier": "Organization: Kent C. Dodds",
      "downloadLocation": "https://registry.npmjs.org/@testing-library/react",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Kent C. Dodds",
      "homepage": "https://testing-library.com/react",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40testing-library/react"
        }
      ],
      "comment": "React Testing Library for component testing - imported in test files"
    },
    {
      "SPDXID": "SPDXRef-Package-testing-library-jest-dom",
      "name": "@testing-library/jest-dom",
      "versionInfo": "unknown",
      "supplier": "Organization: Testing Library contributors",
      "downloadLocation": "https://registry.npmjs.org/@testing-library/jest-dom",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Testing Library contributors",
      "homepage": "https://testing-library.com",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/%40testing-library/jest-dom"
        }
      ],
      "comment": "Custom jest matchers for DOM testing - imported in test files"
    },
    {
      "SPDXID": "SPDXRef-Package-react-router-dom",
      "name": "react-router-dom",
      "versionInfo": "unknown",
      "supplier": "Organization: Remix Software Inc.",
      "downloadLocation": "https://registry.npmjs.org/react-router-dom",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Remix Software Inc.",
      "homepage": "https://reactrouter.com",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/react-router-dom"
        }
      ],
      "comment": "React Router for navigation - imported in test files for BrowserRouter"
    },
    {
      "SPDXID": "SPDXRef-Package-jest",
      "name": "jest",
      "versionInfo": "unknown",
      "supplier": "Organization: Facebook, Inc.",
      "downloadLocation": "https://registry.npmjs.org/jest",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) Meta Platforms, Inc.",
      "homepage": "https://jestjs.io",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/jest"
        }
      ],
      "comment": "Jest testing framework - used throughout test files"
    },
    {
      "SPDXID": "SPDXRef-Package-postcss",
      "name": "postcss",
      "versionInfo": "unknown",
      "supplier": "Organization: PostCSS contributors",
      "downloadLocation": "https://registry.npmjs.org/postcss",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright PostCSS contributors",
      "homepage": "https://postcss.org",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/postcss"
        }
      ],
      "comment": "PostCSS CSS transformation tool - referenced in postcss.config test files"
    },
    {
      "SPDXID": "SPDXRef-Package-tailwindcss",
      "name": "tailwindcss",
      "versionInfo": "unknown",
      "supplier": "Organization: Tailwind Labs",
      "downloadLocation": "https://registry.npmjs.org/tailwindcss",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright Tailwind Labs",
      "homepage": "https://tailwindcss.com",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/tailwindcss"
        }
      ],
      "comment": "Tailwind CSS framework - referenced in postcss.config test files"
    },
    {
      "SPDXID": "SPDXRef-Package-autoprefixer",
      "name": "autoprefixer",
      "versionInfo": "unknown",
      "supplier": "Organization: PostCSS contributors",
      "downloadLocation": "https://registry.npmjs.org/autoprefixer",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright PostCSS contributors",
      "homepage": "https://github.com/postcss/autoprefixer",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/autoprefixer"
        }
      ],
      "comment": "PostCSS plugin to add vendor prefixes - referenced in postcss.config test files"
    },
    {
      "SPDXID": "SPDXRef-Package-cssnano",
      "name": "cssnano",
      "versionInfo": "unknown",
      "supplier": "Organization: cssnano contributors",
      "downloadLocation": "https://registry.npmjs.org/cssnano",
      "filesAnalyzed": false,
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright cssnano contributors",
      "homepage": "https://cssnano.co",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/cssnano"
        }
      ],
      "comment": "CSS minification tool - referenced in postcss.config test files"
    },
    {
      "SPDXID": "SPDXRef-Package-typescript",
      "name": "typescript",
      "versionInfo": "unknown",
      "supplier": "Organization: Microsoft Corporation",
      "downloadLocation": "https://registry.npmjs.org/typescript",
      "filesAnalyzed": false,
      "licenseConcluded": "Apache-2.0",
      "licenseDeclared": "Apache-2.0",
      "copyrightText": "Copyright Microsoft Corporation",
      "homepage": "https://www.typescriptlang.org",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/typescript"
        }
      ],
      "comment": "TypeScript language and compiler - used throughout TypeScript test files"
    }
  ],
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-eslint-js"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-globals"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-eslint-plugin-react-hooks"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-eslint-plugin-react-refresh"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-typescript-eslint"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-testing-library-react"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-testing-library-jest-dom"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-react-router-dom"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-jest"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-postcss"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-tailwindcss"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-autoprefixer"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-cssnano"
    },
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-typescript"
    },
    {
      "spdxElementId": "SPDXRef-Package-typescript-eslint",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-eslint-js"
    },
    {
      "spdxElementId": "SPDXRef-Package-eslint-plugin-react-hooks",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-eslint-plugin-react-refresh",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-testing-library-react",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-testing-library-jest-dom",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-jest"
    },
    {
      "spdxElementId": "SPDXRef-Package-react-router-dom",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-react"
    },
    {
      "spdxElementId": "SPDXRef-Package-tailwindcss",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-postcss"
    },
    {
      "spdxElementId": "SPDXRef-Package-autoprefixer",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-postcss"
    },
    {
      "spdxElementId": "SPDXRef-Package-cssnano",
      "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-postcss"
    }
  ]
}
```

## Technology Stack

**Language**: JavaScript, TypeScript

**Framework**: React (version unknown - used throughout test components)

**Build Tool**: Not directly specified in source files, but configuration suggests Vite based on eslint-plugin-react-refresh

**Package Manager**: npm (inferred from import patterns and registry URLs)

**Testing Framework**: Jest (confirmed from test file imports and structure)

## Dependency Categorization

### Frontend
- **react**: UI library for building component-based interfaces
- **react-router-dom**: Declarative routing for React applications
- **@testing-library/react**: Testing utilities for React components

### Code Quality & Linting
- **@eslint/js**: Core ESLint JavaScript configurations
- **eslint-plugin-react-hooks**: Enforces React Hooks rules
- **eslint-plugin-react-refresh**: Validates React Refresh usage
- **typescript-eslint**: TypeScript linting toolchain
- **globals**: Global identifiers from various JavaScript environments

### CSS Processing
- **postcss**: CSS transformation tool
- **tailwindcss**: Utility-first CSS framework
- **autoprefixer**: Adds vendor prefixes automatically
- **cssnano**: CSS minification and optimization

### Testing
- **jest**: JavaScript testing framework
- **@testing-library/jest-dom**: Custom DOM matchers for Jest
- **@testing-library/react**: React component testing utilities

### Development Tools
- **typescript**: TypeScript language and compiler

## Known Unknowns

**Note**: This SBOM was generated from source code analysis without access to package.json or lock files. The following information is incomplete or unknown:

1. **Exact Version Numbers**: Version information for all packages is unknown. The SBOM lists versions as "unknown" because no package.json or lock files were available in the provided source code.

2. **Component Hashes**: SHA-256/SHA-512 hashes for components could not be determined without access to node_modules or lock files.

3. **Transitive Dependencies**: Only direct dependencies visible in source code are included. Transitive dependencies (sub-dependencies) are not listed because they cannot be determined without analyzing the full dependency tree from lock files.

4. **Complete Dependency Tree**: Additional dependencies may exist that are not directly imported in the provided source files.

5. **Build Dependencies**: Build-time dependencies not directly imported in source code may not be captured.

**Interpretation**: This SBOM should be considered **incomplete**. A complete SBOM would require:
- Access to package.json
- Access to package-lock.json or yarn.lock
- Analysis of node_modules directory
- Build artifact analysis

Components marked as "unknown" version should be verified against actual package manifests before use in production vulnerability scanning.

## Security Considerations

Based on the dependencies identified:

1. **React Ecosystem**: Multiple React-related packages suggest this is a React application. Ensure React version is up-to-date to avoid known vulnerabilities.

2. **Testing Dependencies**: Extensive testing infrastructure indicates good quality practices.

3. **TypeScript**: Use of TypeScript provides type safety and reduces runtime errors.

4. **ESLint Configuration**: Comprehensive linting setup with React-specific rules helps maintain code quality.

5. **CSS Processing**: Use of modern CSS tools (PostCSS, Tailwind, autoprefixer) suggests proper build pipeline.

## Maintenance Status

Based on source code evidence:

- **Active Testing**: Multiple test directories from different dates (2025-07-09 through 2025-11-15) suggest active development
- **Modern Tooling**: Use of current React patterns (Hooks plugins, React Refresh) indicates maintained codebase
- **TypeScript Adoption**: Presence of TypeScript configurations and tests shows commitment to type safety

## Coverage Statement

This SBOM includes:
- ✅ All dependencies directly imported in provided source files
- ✅ Development dependencies (testing, linting)
- ✅ Build tools referenced in configuration files
- ❌ Transitive dependencies (not determinable without lock files)
- ❌ Exact version numbers (not available in source code)
- ❌ Component hashes (not computable without package files)

**Recommendation**: This SBOM should be supplemented with data from package.json and lock files for production use.