# Software Bill of Materials (SBOM) - CycloneDX Format

## Overview

This documentation provides a comprehensive guide to understanding and generating Software Bill of Materials (SBOM) in CycloneDX format for the Mintlify documentation starter kit project. A Software Bill of Materials is a formal, machine-readable inventory of all components, dependencies, and metadata that comprise a software application, serving as a critical artifact for security, compliance, and supply chain transparency.

The CycloneDX format is an OWASP-led industry standard specifically designed for application security contexts and software supply chain component analysis. Unlike general-purpose dependency formats, CycloneDX is purpose-built to support security use cases including vulnerability management, license compliance, and supply chain risk assessment. This format has been adopted by major organizations and security tools worldwide for its comprehensive approach to describing software composition.

**Key Characteristics of CycloneDX**:

- **Security-Focused Design**: Built specifically for security analysis and vulnerability management
- **Machine-Readable Format**: Enables automated tooling and integration with security platforms
- **Comprehensive Metadata**: Captures licenses, copyrights, cryptographic hashes, and provenance information
- **Standardized Structure**: Follows OWASP CycloneDX specification (currently version 1.5)
- **Tool Ecosystem**: Extensive tool support across vulnerability scanners, SCA platforms, and SBOM generators

**Mintlify Documentation Project Context**:

The Mintlify documentation starter kit is a lightweight, documentation-focused project that relies primarily on configuration files (`docs.json`), markdown content files, and the Mintlify CLI tool for local development and preview. Unlike traditional web applications with extensive npm dependency trees, this project has a minimal external dependency footprint, making it an ideal example for understanding SBOM fundamentals without the complexity of large dependency graphs.

Based on analysis of the project structure, the primary dependency is:

- **Mintlify CLI (`mint`)**: Installed globally via npm (`npm i -g mint` per `README.md` line 18)
- **Node.js Runtime**: Required for executing the Mintlify CLI
- **OpenAPI 3.1.0 Specification**: Used for API documentation examples (`api-reference/openapi.json`)

## Implementation

### Project Structure and Dependency Analysis

The Mintlify documentation project differs from typical web applications in its dependency architecture. Analysis of the provided source code reveals:

**Configuration-Based Architecture**:

The project is driven by a central configuration file (`docs.json`) that defines all aspects of the documentation site:

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Mint Starter Kit",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  }
}
```

This configuration-first approach eliminates the need for traditional application dependencies like React, Vue, or Angular, as all rendering and functionality is handled by the Mintlify platform.

**Dependency Discovery Process**:

A comprehensive dependency analysis for SBOM generation would typically examine:

1. **Package Manifest Files**: `package.json`, `package-lock.json` (not present in this project)
2. **Platform Dependencies**: Runtime requirements (Node.js for Mintlify CLI)
3. **Service Dependencies**: External platforms (GitHub for version control, Mintlify hosting)
4. **Data Dependencies**: API specifications and configuration schemas

**Critical Finding**: This project does NOT contain a `package.json` or `package-lock.json` file, indicating it does not use npm package management for direct dependencies. The only runtime dependency is the globally-installed Mintlify CLI tool.

### CycloneDX Document Structure

A CycloneDX SBOM follows a hierarchical JSON structure defined by the CycloneDX specification version 1.5. The complete structure includes:

#### Document Metadata Section

The metadata section identifies the SBOM document itself and the software it describes:

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
        "name": "CycloneDX Generator",
        "version": "1.5.0"
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "pkg:generic/mintlify-docs@1.0.0",
      "name": "Mintlify Documentation Starter Kit",
      "version": "1.0.0",
      "description": "A documentation starter kit using Mintlify for creating beautiful, searchable documentation sites"
    }
  }
}
```

**Field Definitions**:

- `bomFormat`: Always "CycloneDX" for this format
- `specVersion`: CycloneDX specification version ("1.5" is current)
- `serialNumber`: Unique UUID URN identifying this specific SBOM instance
- `version`: SBOM document version (incremented for updates)
- `metadata.timestamp`: ISO 8601 timestamp of SBOM generation
- `metadata.tools`: Tools used to generate the SBOM
- `metadata.component`: The primary application/component this SBOM describes

#### Components Section

The components array catalogs all software dependencies, libraries, and frameworks:

```json
{
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/mint@latest",
      "purl": "pkg:npm/mint",
      "name": "mint",
      "version": "latest",
      "description": "Mintlify CLI for previewing documentation changes locally",
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
        }
      ]
    }
  ]
}
```

**Component Field Definitions**:

- `type`: Component category (library, framework, application, platform, etc.)
- `bom-ref`: Unique identifier for this component within the SBOM
- `purl`: Package URL following the PURL specification format
- `name`: Component name
- `version`: Specific version or version range
- `description`: Human-readable description of component purpose
- `scope`: Usage context (required, optional, excluded)
- `licenses`: SPDX license identifiers or license objects
- `externalReferences`: URLs to documentation, source repositories, websites

**Package URL (PURL) Format**:

The PURL specification provides standardized package identification:

```
pkg:npm/mint@latest
│   │   │    │
│   │   │    └─ Version
│   │   └────── Package name
│   └────────── Package type/ecosystem
└────────────── Scheme identifier
```

PURLs enable consistent package identification across different tools and platforms, facilitating automated vulnerability scanning and dependency tracking.

#### Services Section

External services the software depends on are documented separately:

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
      "externalReferences": [
        {
          "type": "documentation",
          "url": "https://docs.github.com"
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
      "description": "Documentation hosting and deployment service",
      "endpoints": [
        "https://dashboard.mintlify.com"
      ],
      "authenticated": true
    }
  ]
}
```

The services section is particularly important for cloud-native applications that rely on external platforms for deployment, hosting, authentication, or other critical functions.

#### Dependencies Section

The dependencies section maps relationships between components:

```json
{
  "dependencies": [
    {
      "ref": "pkg:generic/mintlify-docs@1.0.0",
      "dependsOn": [
        "pkg:npm/mint@latest",
        "service:github",
        "service:mintlify-platform"
      ]
    },
    {
      "ref": "pkg:npm/mint@latest",
      "dependsOn": []
    }
  ]
}
```

This creates a directed acyclic graph (DAG) of dependencies, enabling tools to understand the complete dependency tree and identify transitive dependencies.

### Complete CycloneDX SBOM for Mintlify Documentation Project

Based on comprehensive analysis of the project structure, configuration files, and documentation, here is the complete CycloneDX SBOM:

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
      "description": "A documentation starter kit using Mintlify for creating beautiful, searchable documentation sites with guide pages, navigation, customizations, and API reference capabilities",
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
        "name": "Mintlify Team"
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
    },
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
        }
      ]
    },
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
        }
      ],
      "externalReferences": [
        {
          "type": "specification",
          "url": "https://spec.openapis.org/oas/v3.1.0"
        }
      ]
    },
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
  ],
  "services": [
    {
      "bom-ref": "service:github",
      "provider": {
        "name": "GitHub, Inc.",
        "url": ["https://github.com"]
      },
      "name": "GitHub",
      "description": "Version control platform providing repository hosting and automatic deployment integration via GitHub app",
      "endpoints": [
        "https://github.com",
        "https://api.github.com"
      ],
      "authenticated": true,
      "trustZone": "external",
      "externalReferences": [
        {
          "type": "website",
          "url": "https://github.com"
        },
        {
          "type": "documentation",
          "url": "https://docs.github.com"
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

### Generating CycloneDX SBOMs

To generate a CycloneDX SBOM for your own Mintlify documentation project or similar configuration-based projects:

#### Step 1: Install SBOM Generation Tools

Several tools support CycloneDX SBOM generation for various project types:

**For Node.js/npm Projects**:

```bash
# Install CycloneDX Node.js module globally
npm install -g @cyclonedx/cyclonedx-npm

# Verify installation
cyclonedx-npm --version
```

**For Multi-Language Projects**:

```bash
# Install Syft (supports multiple ecosystems)
brew install syft  # macOS
# or
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin  # Linux

# Verify installation
syft version
```

**For Docker/Container Images**:

```bash
# Install Trivy
brew install aquasecurity/trivy/trivy  # macOS
# or
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy  # Ubuntu/Debian
```

#### Step 2: Generate SBOM from Project

For standard npm projects with `package.json`:

```bash
# Navigate to project root
cd /path/to/mintlify-documentation-project

# Generate CycloneDX SBOM
cyclonedx-npm --output-file cyclonedx-sbom.json

# Generate with specific output format
cyclonedx-npm --output-format json --output-file cyclonedx-sbom.json
```

**Important Note**: The Mintlify documentation project does NOT have a `package.json`, so the standard npm tool will not work directly. For configuration-based projects like this, manual SBOM creation or custom tooling is required.

**Alternative: Using Syft for Broader Detection**:

```bash
# Generate SBOM from directory
syft dir:. -o cyclonedx-json > cyclonedx-sbom.json

# Syft can detect various package types beyond npm
syft dir:. -o cyclonedx-json --scope all-layers > cyclonedx-sbom-complete.json
```

#### Step 3: Validate Generated SBOM

Ensure the generated SBOM conforms to CycloneDX specification:

```bash
# Install CycloneDX CLI for validation
npm install -g @cyclonedx/cyclonedx-cli

# Validate SBOM
cyclonedx-cli validate --input-file cyclonedx-sbom.json --input-format json --fail-on-errors

# Validate with specific schema version
cyclonedx-cli validate --input-file cyclonedx-sbom.json --schema-version 1.5
```

Expected validation output:
```
Validating CycloneDX BOM...
✓ BOM is valid according to CycloneDX 1.5 specification
```

### Consuming and Analyzing CycloneDX SBOMs

#### Vulnerability Scanning with Generated SBOM

**Using OWASP Dependency-Track**:

Dependency-Track is a comprehensive platform for continuous SBOM analysis and vulnerability management:

```bash
# Upload SBOM to Dependency-Track instance
curl -X "PUT" "https://dependency-track.example.com/api/v1/bom" \
  -H "X-Api-Key: YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d @cyclonedx-sbom.json

# Alternative: Upload via Dependency-Track UI
# 1. Navigate to Projects > Create Project
# 2. Upload cyclonedx-sbom.json via BOM upload interface
# 3. Review vulnerability findings in dashboard
```

Dependency-Track provides:
- Automatic vulnerability detection against multiple databases (NVD, OSS Index, VulnDB)
- Policy compliance checking
- License risk analysis
- Outdated component detection
- Continuous monitoring with webhook notifications

**Using Grype for Vulnerability Scanning**:

```bash
# Install Grype
brew install grype  # macOS
# or
curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sh -s -- -b /usr/local/bin

# Scan SBOM for vulnerabilities
grype sbom:./cyclonedx-sbom.json

# Generate detailed report
grype sbom:./cyclonedx-sbom.json -o table

# Generate JSON report for automation
grype sbom:./cyclonedx-sbom.json -o json > vulnerability-report.json

# Filter by severity
grype sbom:./cyclonedx-sbom.json --only-fixed --fail-on high
```

Example Grype output:
```
NAME     INSTALLED  VULNERABILITY  SEVERITY
mint     latest     CVE-2023-xxxxx Critical
                   Fixed in: 4.1.2
```

#### License Compliance Analysis

**Using FOSSology**:

FOSSology provides comprehensive open source license compliance analysis:

```bash
# Extract license information from SBOM
cat cyclonedx-sbom.json | jq '.components[] | {
  name: .name,
  version: .version,
  licenses: .licenses
}' > license-inventory.json

# Review license compliance
cat license-inventory.json | jq '.licenses[] | select(.license.id | contains("GPL"))'
```

**Using CycloneDX License Scanner**:

```bash
# Analyze license compliance
cyclonedx-cli analyze --input-file cyclonedx-sbom.json --license-compliance

# Generate license attribution report
cyclonedx-cli convert --input-file cyclonedx-sbom.json --output-format text --output-file LICENSE-ATTRIBUTION.txt
```

#### Supply Chain Risk Assessment

**Analyzing Component Provenance**:

```bash
# Extract component sources and external references
cat cyclonedx-sbom.json | jq '.components[] | {
  name: .name,
  purl: .purl,
  external_refs: .externalReferences
}' > component-provenance.json

# Identify components from specific sources
cat cyclonedx-sbom.json | jq '.components[] | 
  select(.externalReferences[]?.type == "vcs") | 
  {name: .name, repo: .externalReferences[] | select(.type == "vcs").url}'
```

**Service Dependency Risk Analysis**:

```bash
# Extract external service dependencies
cat cyclonedx-sbom.json | jq '.services[] | {
  name: .name,
  provider: .provider.name,
  endpoints: .endpoints,
  authenticated: .authenticated
}'
```

This analysis helps identify:
- Third-party service dependencies
- Authentication requirements
- External trust boundaries
- Data flow patterns

### Integrating SBOM Generation into CI/CD Pipelines

#### GitHub Actions Workflow

Create `.github/workflows/sbom-generation.yml`:

```yaml
name: Generate and Publish SBOM

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]
  release:
    types: [ created, published ]

jobs:
  generate-sbom:
    name: Generate CycloneDX SBOM
    runs-on: ubuntu-latest
    
    permissions:
      contents: write
      security-events: write
    
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
      
      - name: Install dependencies (if package.json exists)
        if: hashFiles('package.json') != ''
        run: npm ci
      
      - name: Install CycloneDX Generator
        run: npm install -g @cyclonedx/cyclonedx-npm
      
      - name: Generate SBOM
        run: |
          if [ -f "package.json" ]; then
            cyclonedx-npm --output-file cyclonedx-sbom.json
          else
            # For projects without package.json, use Syft
            curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin
            syft dir:. -o cyclonedx-json > cyclonedx-sbom.json
          fi
      
      - name: Validate SBOM
        run: |
          npm install -g @cyclonedx/cyclonedx-cli
          cyclonedx-cli validate --input-file cyclonedx-sbom.json --fail-on-errors
      
      - name: Upload SBOM as artifact
        uses: actions/upload-artifact@v4
        with:
          name: cyclonedx-sbom
          path: cyclonedx-sbom.json
          retention-days: 90
      
      - name: Scan for vulnerabilities
        uses: anchore/scan-action@v3
        with:
          sbom: cyclonedx-sbom.json
          fail-build: true
          severity-cutoff: high
      
      - name: Submit to Dependency-Track
        if: github.event_name == 'push' && github.ref == 'refs/heads/main'
        run: |
          curl -X "PUT" "${{ secrets.DEPENDENCY_TRACK_URL }}/api/v1/bom" \
            -H "X-Api-Key: ${{ secrets.DEPENDENCY_TRACK_API_KEY }}" \
            -H "Content-Type: application/json" \
            -d @cyclonedx-sbom.json
      
      - name: Attach SBOM to release
        if: github.event_name == 'release'
        uses: actions/upload-release-asset@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          upload_url: ${{ github.event.release.upload_url }}
          asset_path: ./cyclonedx-sbom.json
          asset_name: cyclonedx-sbom.json
          asset_content_type: application/json
```

This workflow:
1. Generates SBOM on every push and pull request
2. Validates SBOM against CycloneDX schema
3. Scans for vulnerabilities
4. Uploads to Dependency-Track for continuous monitoring
5. Attaches SBOM to GitHub releases

#### GitLab CI/CD Pipeline

Create `.gitlab-ci.yml`:

```yaml
stages:
  - sbom
  - security
  - publish

generate_sbom:
  stage: sbom
  image: node:18
  script:
    - npm install -g @cyclonedx/cyclonedx-npm
    - |
      if [ -f "package.json" ]; then
        cyclonedx-npm --output-file cyclonedx-sbom.json
      else
        curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin
        syft dir:. -o cyclonedx-json > cyclonedx-sbom.json
      fi
  artifacts:
    paths:
      - cyclonedx-sbom.json
    expire_in: 90 days

validate_sbom:
  stage: security
  image: node:18
  dependencies:
    - generate_sbom
  script:
    - npm install -g @cyclonedx/cyclonedx-cli
    - cyclonedx-cli validate --input-file cyclonedx-sbom.json --fail-on-errors

vulnerability_scan:
  stage: security
  image: anchore/grype:latest
  dependencies:
    - generate_sbom
  script:
    - grype sbom:./cyclonedx-sbom.json --fail-on high
  allow_failure: false

publish_sbom:
  stage: publish
  image: curlimages/curl:latest
  dependencies:
    - generate_sbom
  script:
    - |
      curl -X "PUT" "$DEPENDENCY_TRACK_URL/api/v1/bom" \
        -H "X-Api-Key: $DEPENDENCY_TRACK_API_KEY" \
        -H "Content-Type: application/json" \
        -d @cyclonedx-sbom.json
  only:
    - main
```

### SBOM Version Management and Historical Tracking

#### Tagging and Storing Historical SBOMs

Maintain SBOM history alongside code versions:

```bash
# Generate SBOM for release
cyclonedx-npm --output-file cyclonedx-sbom.json

# Create versioned copy
VERSION=$(jq -r '.metadata.component.version' cyclonedx-sbom.json)
cp cyclonedx-sbom.json "sbom-archive/cyclonedx-sbom-v${VERSION}.json"

# Add to version control
git add "sbom-archive/cyclonedx-sbom-v${VERSION}.json"
git commit -m "Add SBOM for version ${VERSION}"
git tag -a "sbom-v${VERSION}" -m "SBOM for version ${VERSION}"
git push origin "sbom-v${VERSION}"
```

#### SBOM Comparison and Diff Analysis

Compare SBOMs between versions to track dependency changes:

```bash
# Install SBOM diff tool
npm install -g @cyclonedx/sbom-diff

# Compare two SBOM versions
sbom-diff \
  --old sbom-archive/cyclonedx-sbom-v1.0.0.json \
  --new cyclonedx-sbom.json \
  --output diff-report.json

# View human-readable diff
sbom-diff \
  --old sbom-archive/cyclonedx-sbom-v1.0.0.json \
  --new cyclonedx-sbom.json \
  --format markdown > SBOM-CHANGES.md
```

Example diff output:
```markdown
# SBOM Changes: v1.0.0 → v1.1.0

## Added Components
- react@18.2.0 (new dependency)
- axios@1.4.0 (new dependency)

## Updated Components
- mint: latest → 4.1.0 (version specified)
- typescript: 5.0.0 → 5.1.3 (minor update)

## Removed Components
- lodash@4.17.21 (removed dependency)

## Security Impact
- 2 new vulnerabilities introduced
- 3 vulnerabilities resolved
```

#### Automated SBOM Archival

Create automated arch