# orchestrai-dev - SBOM CycloneDX

**Generation Date:** 2025-01-21T10:30:00Z  
**SBOM Author:** OrchestrAI  
**Generation Context:** After Build / Source Code Analysis  
**Tool:** OrchestrAI Documentation Worker v1.0

---

## CISA 2025 Minimum Elements Reference

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
| Generation Context | Lifecycle phase: after build (source code and dependency analysis) |

---

## Overview

This Software Bill of Materials (SBOM) documents all dependencies and components used in the **orchestrai-dev** project. The project is a React-based web application built with TypeScript and Vite, focusing on AI-powered code quality, testing, and compliance analysis.

### Project Metadata
- **Project Name:** orchestrai-dev
- **Primary Language:** TypeScript/JavaScript
- **Framework:** React 18.3.1
- **Build Tool:** Vite 6.0.7
- **Package Manager:** npm
- **Main Application:** AI-powered software development platform

---

## CycloneDX 1.5 SBOM

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "serialNumber": "urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79",
  "version": 1,
  "metadata": {
    "timestamp": "2025-01-21T10:30:00Z",
    "tools": [
      {
        "vendor": "OrchestrAI",
        "name": "Documentation Worker",
        "version": "1.0"
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:npm/orchestrai-dev@1.0.0",
      "name": "orchestrai-dev",
      "version": "1.0.0",
      "description": "AI-powered software development platform with code quality analysis, testing, and compliance features",
      "licenses": [
        {
          "license": {
            "id": "NOASSERTION"
          }
        }
      ]
    },
    "authors": [
      {
        "name": "OrchestrAI"
      }
    ],
    "properties": [
      {
        "name": "generation_context",
        "value": "after_build"
      },
      {
        "name": "sbom_author",
        "value": "OrchestrAI"
      },
      {
        "name": "data_source",
        "value": "source_code_analysis"
      }
    ]
  },
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/react@18.3.1",
      "purl": "pkg:npm/react@18.3.1",
      "name": "react",
      "version": "18.3.1",
      "description": "React is a JavaScript library for building user interfaces",
      "supplier": {
        "name": "Meta Platforms, Inc.",
        "url": [
          "https://reactjs.org/"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
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
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/react/-/react-18.3.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Core UI library for building component-based interface"
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
      "bom-ref": "pkg:npm/react-dom@18.3.1",
      "purl": "pkg:npm/react-dom@18.3.1",
      "name": "react-dom",
      "version": "18.3.1",
      "description": "React package for working with the DOM",
      "supplier": {
        "name": "Meta Platforms, Inc.",
        "url": [
          "https://reactjs.org/"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
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
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/react-dom/-/react-dom-18.3.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "DOM rendering for React components"
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
      "bom-ref": "pkg:npm/react-router-dom@6.28.0",
      "purl": "pkg:npm/react-router-dom@6.28.0",
      "name": "react-router-dom",
      "version": "6.28.0",
      "description": "DOM bindings for React Router",
      "supplier": {
        "name": "Remix Software Inc.",
        "url": [
          "https://reactrouter.com"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://reactrouter.com"
        },
        {
          "type": "vcs",
          "url": "https://github.com/remix-run/react-router"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Client-side routing for navigation between Enterprise, Mission, Product pages"
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
      "bom-ref": "pkg:npm/@tanstack/react-query@5.64.2",
      "purl": "pkg:npm/%40tanstack/react-query@5.64.2",
      "name": "@tanstack/react-query",
      "version": "5.64.2",
      "description": "Powerful asynchronous state management for React",
      "supplier": {
        "name": "Tanner Linsley",
        "url": [
          "https://tanstack.com/query"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://tanstack.com/query"
        },
        {
          "type": "vcs",
          "url": "https://github.com/TanStack/query"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Data fetching and caching for API calls"
        },
        {
          "name": "criticality",
          "value": "high"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@supabase/supabase-js@2.48.1",
      "purl": "pkg:npm/%40supabase/supabase-js@2.48.1",
      "name": "@supabase/supabase-js",
      "version": "2.48.1",
      "description": "Isomorphic Javascript client for Supabase",
      "supplier": {
        "name": "Supabase",
        "url": [
          "https://supabase.com"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://supabase.com"
        },
        {
          "type": "vcs",
          "url": "https://github.com/supabase/supabase-js"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Backend-as-a-Service integration for authentication, database, and edge functions"
        },
        {
          "name": "criticality",
          "value": "critical"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        },
        {
          "name": "security_sensitive",
          "value": "true"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/lucide-react@0.468.0",
      "purl": "pkg:npm/lucide-react@0.468.0",
      "name": "lucide-react",
      "version": "0.468.0",
      "description": "React implementation of the lucide icon library",
      "supplier": {
        "name": "Lucide Contributors",
        "url": [
          "https://lucide.dev"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "ISC"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://lucide.dev"
        },
        {
          "type": "vcs",
          "url": "https://github.com/lucide-icons/lucide"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Icon library used extensively in UI components (X, Bot, FileText, AlertCircle, Shield, etc.)"
        },
        {
          "name": "criticality",
          "value": "high"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-dialog@1.1.2",
      "purl": "pkg:npm/%40radix-ui/react-dialog@1.1.2",
      "name": "@radix-ui/react-dialog",
      "version": "1.1.2",
      "description": "A modal dialog component",
      "supplier": {
        "name": "Radix UI",
        "url": [
          "https://radix-ui.com"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://radix-ui.com"
        },
        {
          "type": "vcs",
          "url": "https://github.com/radix-ui/primitives"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Modal dialogs (ComplianceProgressDialog, DocumentationProgressDialog, WelcomeModal)"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-checkbox@1.1.2",
      "purl": "pkg:npm/%40radix-ui/react-checkbox@1.1.2",
      "name": "@radix-ui/react-checkbox",
      "version": "1.1.2",
      "description": "A checkbox component",
      "supplier": {
        "name": "Radix UI",
        "url": [
          "https://radix-ui.com"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Checkbox inputs for scope and content structure selection in AIDocumentationSpecialistPanel"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-collapsible@1.1.1",
      "purl": "pkg:npm/%40radix-ui/react-collapsible@1.1.1",
      "name": "@radix-ui/react-collapsible",
      "version": "1.1.1",
      "description": "A collapsible component",
      "supplier": {
        "name": "Radix UI"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Expandable sections for advanced options in panels"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-progress@1.1.0",
      "purl": "pkg:npm/%40radix-ui/react-progress@1.1.0",
      "name": "@radix-ui/react-progress",
      "version": "1.1.0",
      "description": "A progress bar component",
      "supplier": {
        "name": "Radix UI"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Progress indicators for compliance and documentation analysis"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-toast@1.2.2",
      "purl": "pkg:npm/%40radix-ui/react-toast@1.2.2",
      "name": "@radix-ui/react-toast",
      "version": "1.2.2",
      "description": "A toast notification component",
      "supplier": {
        "name": "Radix UI"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Toast notifications for user feedback"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/@radix-ui/react-label@2.1.0",
      "purl": "pkg:npm/%40radix-ui/react-label@2.1.0",
      "name": "@radix-ui/react-label",
      "version": "2.1.0",
      "description": "A label component",
      "supplier": {
        "name": "Radix UI"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Form labels for input fields"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/tailwindcss@3.4.17",
      "purl": "pkg:npm/tailwindcss@3.4.17",
      "name": "tailwindcss",
      "version": "3.4.17",
      "description": "A utility-first CSS framework",
      "supplier": {
        "name": "Tailwind Labs",
        "url": [
          "https://tailwindcss.com"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://tailwindcss.com"
        },
        {
          "type": "vcs",
          "url": "https://github.com/tailwindlabs/tailwindcss"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "CSS framework for styling throughout the application"
        },
        {
          "name": "criticality",
          "value": "high"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/autoprefixer@10.4.20",
      "purl": "pkg:npm/autoprefixer@10.4.20",
      "name": "autoprefixer",
      "version": "10.4.20",
      "description": "PostCSS plugin to parse CSS and add vendor prefixes",
      "supplier": {
        "name": "Andrey Sitnik",
        "url": [
          "https://github.com/postcss/autoprefixer"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "CSS vendor prefix automation for cross-browser compatibility"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/postcss@8.4.49",
      "purl": "pkg:npm/postcss@8.4.49",
      "name": "postcss",
      "version": "8.4.49",
      "description": "Tool for transforming styles with JS plugins",
      "supplier": {
        "name": "Andrey Sitnik",
        "url": [
          "https://postcss.org"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "CSS processing pipeline for Tailwind and autoprefixer"
        },
        {
          "name": "criticality",
          "value": "medium"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/typescript@5.6.3",
      "purl": "pkg:npm/typescript@5.6.3",
      "name": "typescript",
      "version": "5.6.3",
      "description": "TypeScript is a language for application scale JavaScript development",
      "supplier": {
        "name": "Microsoft Corporation",
        "url": [
          "https://www.typescriptlang.org"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "Apache-2.0"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://www.typescriptlang.org"
        },
        {
          "type": "vcs",
          "url": "https://github.com/microsoft/TypeScript"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Type checking and compilation for TypeScript source code"
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
      "bom-ref": "pkg:npm/vite@6.0.7",
      "purl": "pkg:npm/vite@6.0.7",
      "name": "vite",
      "version": "6.0.7",
      "description": "Native-ESM powered web dev build tool",
      "supplier": {
        "name": "Evan You",
        "url": [
          "https://vitejs.dev"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "NOASSERTION"
        }
      ],
      "externalReferences": [
        {
          "type": "website",
          "url": "https://vitejs.dev"
        },
        {
          "type": "vcs",
          "url": "https://github.com/vitejs/vite"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Build tool and development server"
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
      "bom-ref": "pkg:npm/@vitejs/plugin-react@4.3.4",
      "purl": "pkg:npm/%40vitejs/plugin-react@4.3.4",
      "name": "@vitejs/plugin-react",
      "version": "4.3.4",
      "description": "The all-in-one Vite plugin for React projects",
      "supplier": {
        "name": "Vite Team"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "React Fast Refresh and JSX transformation for Vite"
        },
        {
          "name": "criticality",
          "value": "high"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/eslint@9.17.0",
      "purl": "pkg:npm/eslint@9.17.0",
      "name": "eslint",
      "version": "9.17.0",
      "description": "An AST-based pattern checker for JavaScript",
      "supplier": {
        "name": "OpenJS Foundation",
        "url": [
          "https://eslint.org"
        ]
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "JavaScript/TypeScript linting"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        },
        {
          "name": "scope",
          "value": "development"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/typescript-eslint@8.18.1",
      "purl": "pkg:npm/typescript-eslint@8.18.1",
      "name": "typescript-eslint",
      "version": "8.18.1",
      "description": "Monorepo for all the tooling which enables ESLint to support TypeScript",
      "supplier": {
        "name": "TypeScript ESLint"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "TypeScript-specific linting rules and parser"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        },
        {
          "name": "scope",
          "value": "development"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/eslint-plugin-react-hooks@5.1.0",
      "purl": "pkg:npm/eslint-plugin-react-hooks@5.1.0",
      "name": "eslint-plugin-react-hooks",
      "version": "5.1.0",
      "description": "ESLint rules for React Hooks",
      "supplier": {
        "name": "Meta Platforms, Inc."
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Enforces React Hooks rules"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        },
        {
          "name": "scope",
          "value": "development"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/eslint-plugin-react-refresh@0.4.16",
      "purl": "pkg:npm/eslint-plugin-react-refresh@0.4.16",
      "name": "eslint-plugin-react-refresh",
      "version": "0.4.16",
      "description": "Validate that your components can safely be updated with Fast Refresh",
      "supplier": {
        "name": "Vite Team"
      },
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Ensures React components are compatible with Fast Refresh"
        },
        {
          "name": "criticality",
          "value": "low"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        },
        {
          "name": "scope",
          "value": "development"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/globals@15.13.0",
      "purl": "pkg:npm/globals@15.13.0",
      "name": "globals",
      "version": "15.13.0",
      "description": "Global identifiers from different JavaScript environments",
      "supplier": {
        "name": "Sindre Sorhus"
      },
      "licenses": [
        {
          "license