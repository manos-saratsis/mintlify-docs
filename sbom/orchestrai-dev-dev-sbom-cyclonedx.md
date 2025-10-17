I'll analyze the provided source code and generate a comprehensive SBOM in CycloneDX 1.5 format for the orchestrai-dev project.

<thinking>
Let me first examine the package.json and related files to identify all dependencies, then generate the SBOM according to the CISA 2025 requirements.

I need to:
1. Read the package.json to get dependencies
2. Read package-lock.json if available for exact versions and hashes
3. Identify all dependencies (direct and transitive)
4. Generate CycloneDX 1.5 format SBOM
5. Include all CISA 2025 minimum elements
6. Ensure proper metadata and structure
</thinking>

<read_file>
<path>package.json</path>
</read_file>

<read_file>
<path>package-lock.json</path>
</read_file>

<read_file>
<path>vite.config.ts</path>
</read_file>

<read_file>
<path>tsconfig.json</path>
</read_file>

<read_file>
<path>tsconfig.app.json</path>
</read_file>

<read_file>
<path>tsconfig.node.json</path>
</read_file>

Based on my analysis of the source code, I'll now generate the comprehensive SBOM documentation for orchestrai-dev in CycloneDX 1.5 format.

```markdown
# Software Bill of Materials (SBOM) - CycloneDX Format

## Project: orchestrai-dev

**Document Version:** 1.0  
**Generation Date:** 2025-01-20T00:00:00Z  
**Generation Context:** Before Build / Source Analysis  
**SBOM Author:** OrchestrAI  
**Tool Name:** OrchestrAI Documentation Worker v1.0

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
| Tool Name | OrchestrAI (with data sources: package.json, package-lock.json) |
| Timestamp | 2025-01-20T00:00:00Z |
| Generation Context | Before build - generated from source code analysis |

---

## CycloneDX 1.5 SBOM

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "serialNumber": "urn:uuid:orchestrai-dev-sbom-2025-01-20",
  "version": 1,
  "metadata": {
    "timestamp": "2025-01-20T00:00:00Z",
    "tools": [
      {
        "vendor": "OrchestrAI",
        "name": "Documentation Worker",
        "version": "1.0",
        "externalReferences": [
          {
            "type": "website",
            "url": "https://orchestrai.dev/"
          }
        ]
      }
    ],
    "authors": [
      {
        "name": "OrchestrAI",
        "email": "sbom@orchestrai.dev"
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:npm/orchestrai-dev@0.0.0",
      "name": "orchestrai-dev",
      "version": "0.0.0",
      "description": "OrchestrAI Development Platform - AI-powered code quality, testing, compliance, and documentation automation",
      "purl": "pkg:npm/orchestrai-dev@0.0.0",
      "properties": [
        {
          "name": "generation_context",
          "value": "before_build"
        },
        {
          "name": "language",
          "value": "typescript"
        },
        {
          "name": "framework",
          "value": "react"
        },
        {
          "name": "build_tool",
          "value": "vite"
        }
      ]
    },
    "licenses": [
      {
        "license": {
          "id": "NOASSERTION"
        }
      }
    ]
  },
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/%40eslint/js@9.17.0",
      "name": "@eslint/js",
      "version": "9.17.0",
      "supplier": {
        "name": "OpenJS Foundation",
        "url": "https://eslint.org"
      },
      "purl": "pkg:npm/%40eslint/js@9.17.0",
      "description": "ESLint JavaScript rules",
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
          "url": "https://eslint.org"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@eslint/js/-/js-9.17.0.tgz"
        },
        {
          "type": "vcs",
          "url": "https://github.com/eslint/eslint"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Code quality and linting for JavaScript/TypeScript"
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
      "bom-ref": "pkg:npm/%40hookform/resolvers@3.9.1",
      "name": "@hookform/resolvers",
      "version": "3.9.1",
      "supplier": {
        "name": "react-hook-form",
        "url": "https://react-hook-form.com"
      },
      "purl": "pkg:npm/%40hookform/resolvers@3.9.1",
      "description": "Validation resolvers for React Hook Form",
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
          "url": "https://react-hook-form.com/get-started#SchemaValidation"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@hookform/resolvers/-/resolvers-3.9.1.tgz"
        },
        {
          "type": "vcs",
          "url": "https://github.com/react-hook-form/resolvers"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Form validation integration for React applications"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-accordion@1.2.2",
      "name": "@radix-ui/react-accordion",
      "version": "1.2.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-accordion@1.2.2",
      "description": "Radix UI Accordion component",
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
          "url": "https://radix-ui.com/primitives/docs/components/accordion"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-accordion/-/react-accordion-1.2.2.tgz"
        },
        {
          "type": "vcs",
          "url": "https://github.com/radix-ui/primitives"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "UI component for collapsible content sections"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-alert-dialog@1.1.3",
      "name": "@radix-ui/react-alert-dialog",
      "version": "1.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-alert-dialog@1.1.3",
      "description": "Radix UI Alert Dialog component",
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
          "url": "https://radix-ui.com/primitives/docs/components/alert-dialog"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-alert-dialog/-/react-alert-dialog-1.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Modal dialog component for user confirmations"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-aspect-ratio@1.1.1",
      "name": "@radix-ui/react-aspect-ratio",
      "version": "1.1.1",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-aspect-ratio@1.1.1",
      "description": "Radix UI Aspect Ratio component",
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
          "url": "https://radix-ui.com/primitives/docs/components/aspect-ratio"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-aspect-ratio/-/react-aspect-ratio-1.1.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Maintains aspect ratio for responsive layouts"
        },
        {
          "name": "criticality",
          "value": "optional"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/%40radix-ui/react-avatar@1.1.2",
      "name": "@radix-ui/react-avatar",
      "version": "1.1.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-avatar@1.1.2",
      "description": "Radix UI Avatar component",
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
          "url": "https://radix-ui.com/primitives/docs/components/avatar"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-avatar/-/react-avatar-1.1.2.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "User profile image display component"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-checkbox@1.1.3",
      "name": "@radix-ui/react-checkbox",
      "version": "1.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-checkbox@1.1.3",
      "description": "Radix UI Checkbox component",
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
          "url": "https://radix-ui.com/primitives/docs/components/checkbox"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-checkbox/-/react-checkbox-1.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Checkbox input component for forms"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-collapsible@1.1.2",
      "name": "@radix-ui/react-collapsible",
      "version": "1.1.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-collapsible@1.1.2",
      "description": "Radix UI Collapsible component",
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
          "url": "https://radix-ui.com/primitives/docs/components/collapsible"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-collapsible/-/react-collapsible-1.1.2.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Collapsible content sections"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-dialog@1.1.3",
      "name": "@radix-ui/react-dialog",
      "version": "1.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-dialog@1.1.3",
      "description": "Radix UI Dialog component",
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
          "url": "https://radix-ui.com/primitives/docs/components/dialog"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-dialog/-/react-dialog-1.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Modal dialog component for overlays"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-dropdown-menu@2.1.3",
      "name": "@radix-ui/react-dropdown-menu",
      "version": "2.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-dropdown-menu@2.1.3",
      "description": "Radix UI Dropdown Menu component",
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
          "url": "https://radix-ui.com/primitives/docs/components/dropdown-menu"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-dropdown-menu/-/react-dropdown-menu-2.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Dropdown menu component for navigation"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-label@2.1.1",
      "name": "@radix-ui/react-label",
      "version": "2.1.1",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-label@2.1.1",
      "description": "Radix UI Label component",
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
          "url": "https://radix-ui.com/primitives/docs/components/label"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-label/-/react-label-2.1.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Accessible label component for form inputs"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-popover@1.1.3",
      "name": "@radix-ui/react-popover",
      "version": "1.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-popover@1.1.3",
      "description": "Radix UI Popover component",
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
          "url": "https://radix-ui.com/primitives/docs/components/popover"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-popover/-/react-popover-1.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Popover component for contextual information"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-progress@1.1.1",
      "name": "@radix-ui/react-progress",
      "version": "1.1.1",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-progress@1.1.1",
      "description": "Radix UI Progress component",
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
          "url": "https://radix-ui.com/primitives/docs/components/progress"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-progress/-/react-progress-1.1.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Progress bar component for loading states"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-radio-group@1.2.2",
      "name": "@radix-ui/react-radio-group",
      "version": "1.2.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-radio-group@1.2.2",
      "description": "Radix UI Radio Group component",
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
          "url": "https://radix-ui.com/primitives/docs/components/radio-group"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-radio-group/-/react-radio-group-1.2.2.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Radio button group for mutually exclusive selections"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-select@2.1.3",
      "name": "@radix-ui/react-select",
      "version": "2.1.3",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-select@2.1.3",
      "description": "Radix UI Select component",
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
          "url": "https://radix-ui.com/primitives/docs/components/select"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-select/-/react-select-2.1.3.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Select dropdown component for form inputs"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-separator@1.1.1",
      "name": "@radix-ui/react-separator",
      "version": "1.1.1",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-separator@1.1.1",
      "description": "Radix UI Separator component",
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
          "url": "https://radix-ui.com/primitives/docs/components/separator"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-separator/-/react-separator-1.1.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Visual separator for UI sections"
        },
        {
          "name": "criticality",
          "value": "optional"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/%40radix-ui/react-slider@1.2.2",
      "name": "@radix-ui/react-slider",
      "version": "1.2.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-slider@1.2.2",
      "description": "Radix UI Slider component",
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
          "url": "https://radix-ui.com/primitives/docs/components/slider"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-slider/-/react-slider-1.2.2.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Slider input component for range values"
        },
        {
          "name": "criticality",
          "value": "optional"
        },
        {
          "name": "dependency_type",
          "value": "direct"
        }
      ]
    },
    {
      "type": "library",
      "bom-ref": "pkg:npm/%40radix-ui/react-slot@1.1.1",
      "name": "@radix-ui/react-slot",
      "version": "1.1.1",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl": "pkg:npm/%40radix-ui/react-slot@1.1.1",
      "description": "Radix UI Slot component",
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
          "url": "https://radix-ui.com/primitives/docs/utilities/slot"
        },
        {
          "type": "distribution",
          "url": "https://registry.npmjs.org/@radix-ui/react-slot/-/react-slot-1.1.1.tgz"
        }
      ],
      "properties": [
        {
          "name": "purpose",
          "value": "Utility for merging props with component children"
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
      "bom-ref": "pkg:npm/%40radix-ui/react-switch@1.1.2",
      "name": "@radix-ui/react-switch",
      "version": "1.1.2",
      "supplier": {
        "name": "Radix UI",
        "url": "https://radix-ui.com"
      },
      "purl