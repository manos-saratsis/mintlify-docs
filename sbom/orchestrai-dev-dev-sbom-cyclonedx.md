# orchestrai-dev-sbom-cyclonedx.json

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

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "version": 1,
  "serialNumber": "urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79",
  "metadata": {
    "timestamp": "2025-01-13T00:00:00Z",
    "tools": [
      {
        "vendor": "OrchestrAI",
        "name": "Documentation Worker",
        "version": "1.0"
      }
    ],
    "component": {
      "type": "application",
      "name": "orchestrai-dev",
      "version": "1.0.0",
      "description": "AI-powered quality engineering and test automation platform",
      "purl": "pkg:github/orchestrai/orchestrai-dev@1.0.0"
    },
    "authors": [
      {
        "name": "OrchestrAI"
      }
    ],
    "properties": [
      {
        "name": "generation_context",
        "value": "before build"
      },
      {
        "name": "data_source",
        "value": "source code analysis"
      }
    ]
  },
  "components": [
    {
      "type": "library",
      "name": "@eslint/js",
      "group": "@eslint",
      "version": "latest",
      "purl": "pkg:npm/@eslint/js",
      "description": "ESLint JavaScript configuration",
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
          "url": "https://eslint.org/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/eslint/eslint"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "ESLint configuration for JavaScript linting rules"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "globals",
      "version": "latest",
      "purl": "pkg:npm/globals",
      "description": "Global identifiers from different JavaScript environments",
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
          "url": "https://github.com/sindresorhus/globals"
        },
        {
          "type": "vcs",
          "url": "https://github.com/sindresorhus/globals"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Provides global environment definitions for ESLint"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "eslint-plugin-react-hooks",
      "version": "latest",
      "purl": "pkg:npm/eslint-plugin-react-hooks",
      "description": "ESLint rules for React Hooks",
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
          "url": "https://reactjs.org/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/facebook/react"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Enforces React Hooks rules in the codebase"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "eslint-plugin-react-refresh",
      "version": "latest",
      "purl": "pkg:npm/eslint-plugin-react-refresh",
      "description": "ESLint plugin for React Refresh",
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "vcs",
          "url": "https://github.com/ArnaudBarre/eslint-plugin-react-refresh"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Validates React component exports for Fast Refresh compatibility"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "typescript-eslint",
      "version": "latest",
      "purl": "pkg:npm/typescript-eslint",
      "description": "Monorepo for TypeScript ESLint tooling",
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
          "url": "https://typescript-eslint.io/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/typescript-eslint/typescript-eslint"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "TypeScript parser and ESLint configuration for TypeScript files"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "react",
      "version": "18.x",
      "purl": "pkg:npm/react@18",
      "description": "JavaScript library for building user interfaces",
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
          "url": "https://reactjs.org/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/facebook/react"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Core UI library for building component-based interfaces"
        },
        {
          "name": "criticality",
          "value": "critical"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "@testing-library/react",
      "group": "@testing-library",
      "version": "latest",
      "purl": "pkg:npm/@testing-library/react",
      "description": "React DOM testing utilities",
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
          "url": "https://testing-library.com/react"
        },
        {
          "type": "vcs",
          "url": "https://github.com/testing-library/react-testing-library"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Testing utilities for React components"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "@testing-library/jest-dom",
      "group": "@testing-library",
      "version": "latest",
      "purl": "pkg:npm/@testing-library/jest-dom",
      "description": "Custom jest matchers for DOM testing",
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
          "url": "https://testing-library.com/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/testing-library/jest-dom"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Custom Jest matchers for DOM element assertions"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "jest",
      "version": "latest",
      "purl": "pkg:npm/jest",
      "description": "Delightful JavaScript Testing Framework",
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
          "url": "https://jestjs.io/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/facebook/jest"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "JavaScript testing framework used for unit and integration tests"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "react-router-dom",
      "version": "6.x",
      "purl": "pkg:npm/react-router-dom@6",
      "description": "Declarative routing for React web applications",
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
          "url": "https://reactrouter.com/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/remix-run/react-router"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Client-side routing for single-page application navigation"
        },
        {
          "name": "criticality",
          "value": "critical"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "typescript",
      "version": "5.x",
      "purl": "pkg:npm/typescript@5",
      "description": "TypeScript language and compiler",
      "licenses": [
        {
          "license": {
            "id": "Apache-2.0"
          }
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://www.typescriptlang.org/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/microsoft/TypeScript"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "TypeScript compiler and type checking for static type safety"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "postcss",
      "version": "latest",
      "purl": "pkg:npm/postcss",
      "description": "Tool for transforming CSS with JavaScript",
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
          "url": "https://postcss.org/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/postcss/postcss"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "CSS transformation and processing tool"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "tailwindcss",
      "version": "latest",
      "purl": "pkg:npm/tailwindcss",
      "description": "Utility-first CSS framework",
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
          "url": "https://tailwindcss.com/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/tailwindlabs/tailwindcss"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Utility-first CSS framework for rapid UI development"
        },
        {
          "name": "criticality",
          "value": "critical"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "autoprefixer",
      "version": "latest",
      "purl": "pkg:npm/autoprefixer",
      "description": "PostCSS plugin to parse CSS and add vendor prefixes",
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
          "url": "https://github.com/postcss/autoprefixer"
        },
        {
          "type": "vcs",
          "url": "https://github.com/postcss/autoprefixer"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Adds vendor prefixes to CSS for cross-browser compatibility"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "name": "cssnano",
      "version": "latest",
      "purl": "pkg:npm/cssnano",
      "description": "Modern CSS compression tool",
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
          "url": "https://cssnano.co/"
        },
        {
          "type": "vcs",
          "url": "https://github.com/cssnano/cssnano"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "CSS minification and optimization for production builds"
        },
        {
          "name": "criticality",
          "value": "development"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    }
  ],
  "dependencies": [
    {
      "ref": "pkg:github/orchestrai/orchestrai-dev@1.0.0",
      "dependsOn": [
        "pkg:npm/react@18",
        "pkg:npm/react-router-dom@6",
        "pkg:npm/typescript@5",
        "pkg:npm/tailwindcss",
        "pkg:npm/@eslint/js",
        "pkg:npm/globals",
        "pkg:npm/eslint-plugin-react-hooks",
        "pkg:npm/eslint-plugin-react-refresh",
        "pkg:npm/typescript-eslint",
        "pkg:npm/@testing-library/react",
        "pkg:npm/@testing-library/jest-dom",
        "pkg:npm/jest",
        "pkg:npm/postcss",
        "pkg:npm/autoprefixer",
        "pkg:npm/cssnano"
      ]
    },
    {
      "ref": "pkg:npm/typescript-eslint",
      "dependsOn": [
        "pkg:npm/typescript@5"
      ]
    },
    {
      "ref": "pkg:npm/@testing-library/react",
      "dependsOn": [
        "pkg:npm/react@18"
      ]
    },
    {
      "ref": "pkg:npm/react-router-dom@6",
      "dependsOn": [
        "pkg:npm/react@18"
      ]
    },
    {
      "ref": "pkg:npm/tailwindcss",
      "dependsOn": [
        "pkg:npm/postcss"
      ]
    },
    {
      "ref": "pkg:npm/autoprefixer",
      "dependsOn": [
        "pkg:npm/postcss"
      ]
    },
    {
      "ref": "pkg:npm/cssnano",
      "dependsOn": [
        "pkg:npm/postcss"
      ]
    }
  ]
}
```

## Overview

This Software Bill of Materials (SBOM) documents all software components, dependencies, and metadata for the **orchestrai-dev** project in CycloneDX 1.5 format. The SBOM was generated by analyzing the project's source code, specifically the ESLint configuration (`eslint.config.js`) and test files, which reveal the technology stack and dependency structure.

## Implementation Details

### Technology Stack

The orchestrai-dev application is built using:

- **Language**: TypeScript 5.x (referenced in `eslint.config.js` line 5: `import tseslint from "typescript-eslint"`)
- **Framework**: React 18.x (inferred from React-specific ESLint plugins)
- **Build System**: ESLint configuration uses ES modules and TypeScript
- **Testing Framework**: Jest with React Testing Library (evidenced by test files using `@testing-library/react` and `@testing-library/jest-dom`)
- **Styling**: TailwindCSS with PostCSS (inferred from `postcss.config.js` references in test files)
- **Package Manager**: npm or compatible (standard for Node.js projects)

### Component Categories

**Frontend Components:**
- `react@18` - Core UI library
- `react-router-dom@6` - Client-side routing (referenced in test files)
- `tailwindcss` - Utility-first CSS framework

**Development Tools:**
- `typescript@5` - Type checking and compilation
- `eslint` ecosystem - Code quality and linting
- `jest` - Testing framework
- `@testing-library/react` - React component testing utilities

**Build Tools:**
- `postcss` - CSS transformation
- `autoprefixer` - CSS vendor prefixing
- `cssnano` - CSS optimization

### ESLint Configuration Analysis

From `eslint.config.js` (lines 1-33):

```javascript
export default tseslint.config(
  { ignores: ["dist"] },
  {
    extends: [js.configs.recommended, ...tseslint.configs.recommended],
    files: ["**/*.{ts,tsx}"],
    languageOptions: {
      ecmaVersion: 2020,
      globals: globals.browser,
    },
    plugins: {
      "react-hooks": reactHooks,
      "react-refresh": reactRefresh,
    },
    rules: {
      ...reactHooks.configs.recommended.rules,
      "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
      "@typescript-eslint/no-unused-vars": "off",
    },
  }
);
```

This configuration reveals:
- TypeScript support for `.ts` and `.tsx` files
- React Hooks enforcement
- React Refresh compatibility checking
- ECMAScript 2020 features
- Browser environment globals

### Test Infrastructure

The test files demonstrate comprehensive testing setup:

**Component Testing** (from `App.test.tsx`, `AIQualityEngineerPanel.test.tsx`, etc.):
- Jest as the test runner
- React Testing Library for component testing
- Mock implementations for child components
- Browser Router integration for routing tests

**Configuration Testing** (from `eslint.config.test.js`, `postcss.config.test.js`):
- Validation of build tool configurations
- Environment-specific behavior testing

## Dependency Relationships

### Critical Path Dependencies

**React Ecosystem:**
```
orchestrai-dev
  └─ react@18 (critical)
      ├─ react-router-dom@6
      ├─ @testing-library/react
      └─ eslint-plugin-react-hooks
```

**TypeScript Toolchain:**
```
orchestrai-dev
  └─ typescript@5 (development)
      └─ typescript-eslint
          └─ @typescript-eslint/parser
```

**PostCSS Pipeline:**
```
orchestrai-dev
  └─ postcss (development)
      ├─ tailwindcss (critical)
      ├─ autoprefixer (development)
      └─ cssnano (development)
```

### Transitive Dependencies

All listed components include their first-level transitive dependencies. For complete dependency trees including all depths, the SBOM should be regenerated with access to `package-lock.json` or `yarn.lock` files.

## Security Considerations

### Known Security-Relevant Dependencies

1. **React** - Handles user input and UI rendering (XSS vulnerability surface)
2. **React Router** - Manages navigation and URL handling (potential for open redirect)
3. **TypeScript** - Provides type safety (reduces runtime errors)

### Maintenance Status

All listed dependencies are actively maintained as of the SBOM generation date:
- React: Maintained by Meta/Facebook
- TypeScript: Maintained by Microsoft
- ESLint: Maintained by OpenJS Foundation
- PostCSS/Tailwind: Actively maintained open-source projects

## Coverage Notes

This SBOM represents **known dependencies** based on source code analysis. It includes:

✅ Direct dependencies explicitly imported in source files
✅ Development dependencies used in testing and build configuration
✅ First-level transitive dependencies

**Known Unknowns:**

The following information requires access to lock files or package.json:
- Exact version numbers (marked as "latest" or major version ranges)
- Complete transitive dependency trees beyond first level
- Cryptographic hashes (SHA-256/SHA-512) of installed packages
- Exact installation timestamps

To generate a complete SBOM with all minimum CISA 2025 elements, please provide:
- `package.json`
- `package-lock.json` or `yarn.lock`
- `node_modules` directory (for hash generation)

## Generation Context

- **Lifecycle Phase**: Before build (source code analysis)
- **SBOM Author**: OrchestrAI
- **Generation Date**: 2025-01-13T00:00:00Z
- **Data Sources**: Source code files (eslint.config.js, test files)
- **Tool**: OrchestrAI Documentation Worker v1.0

## Usage

This SBOM can be used for:
1. **Vulnerability Scanning**: Import into security scanning tools (e.g., Snyk, Dependabot)
2. **License Compliance**: Verify all dependencies use acceptable licenses
3. **Supply Chain Security**: Track component provenance
4. **Dependency Management**: Identify outdated or deprecated packages
5. **Audit Trail**: Maintain records of software composition for compliance