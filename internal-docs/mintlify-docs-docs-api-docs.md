# Mintlify Documentation Starter Kit - API Documentation

## Overview

The Mintlify Documentation Starter Kit includes a comprehensive demonstration of API documentation capabilities through an example **Plant Store API**. This API serves as a working reference implementation showcasing how to document RESTful APIs using the OpenAPI 3.1.0 specification format integrated with Mintlify's documentation platform.

**Purpose and Context:**

The Plant Store API is not a production service but rather an educational example demonstrating:

- OpenAPI 3.1.0 specification structure and best practices
- RESTful API design patterns (GET, POST, DELETE operations)
- Authentication implementation (Bearer token scheme)
- Webhook integration patterns
- Request/response schema documentation
- Error handling and status codes
- Automatic documentation generation from OpenAPI specifications

**API Characteristics:**

- **Base URL**: `http://sandbox.mintlify.com`
- **API Version**: 1.0.0
- **Specification Format**: OpenAPI 3.1.0
- **License**: MIT
- **Authentication**: HTTP Bearer token
- **Content Type**: application/json
- **Specification Location**: `api-reference/openapi.json` (194 lines)

**Integration with Mintlify:**

The OpenAPI specification automatically generates interactive API documentation when integrated with Mintlify's platform. This includes:

- Automatic endpoint documentation with request/response examples
- Interactive API testing capabilities ("Try It" functionality)
- Schema visualization and type documentation
- Code generation in multiple programming languages
- Authentication requirement displays
- Integrated navigation within the documentation site

**Documentation Structure:**

The API reference is organized in the navigation (`docs.json` lines 48-65) under the "API reference" tab with two groups:

1. **API documentation** - Introduction and overview (`api-reference/introduction.md`)
2. **Endpoint examples** - Individual endpoint documentation pages:
   - `api-reference/endpoint/get.md` - GET /plants endpoint
   - `api-reference/endpoint/create.md` - POST /plants endpoint
   - `api-reference/endpoint/delete.md` - DELETE /plants/{id} endpoint
   - `api-reference/endpoint/webhook.md` - Webhook notifications

## Implementation

### OpenAPI Specification Architecture

The OpenAPI specification follows a hierarchical structure defined in `api-reference/openapi.json`:

#### Root Configuration (Lines 1-18)

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "OpenAPI Plant Store",
    "description": "A sample API that uses a plant store as an example to demonstrate features in the OpenAPI specification",
    "license": {
      "name": "MIT"
    },
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "http://sandbox.mintlify.com"
    }
  ],
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Configuration Components:**

- **openapi**: Declares OpenAPI specification version (3.1.0)
- **info**: Metadata including title, description, license, and version
- **servers**: Array of API server endpoints (sandbox server in this case)
- **security**: Global security requirements applied to all endpoints

#### Authentication Configuration

**Security Requirement Definition** (Lines 14-18):
```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

This global security requirement means all endpoints require bearer token authentication by default.

**Security Scheme Implementation** (Lines 175-179):
```json
{
  "securitySchemes": {
    "bearerAuth": {
      "type": "http",
      "scheme": "bearer"
    }
  }
}
```

**Authentication Mechanism:**

- **Type**: HTTP authentication
- **Scheme**: Bearer token
- **Header Format**: `Authorization: Bearer {token}`
- **Scope**: Applied globally to all API operations
- **Implementation**: Stateless token-based authentication

### Endpoint Definitions

#### GET /plants - Retrieve Plant List

**Specification** (`openapi.json` lines 20-56):

```json
{
  "/plants": {
    "get": {
      "description": "Returns all plants from the system that the user has access to",
      "parameters": [
        {
          "name": "limit",
          "in": "query",
          "description": "The maximum number of results to return",
          "schema": {
            "type": "integer",
            "format": "int32"
          }
        }
      ],
      "responses": {
        "200": {
          "description": "Plant response",
          "content": {
            "application/json": {
              "schema": {
                "type": "array",
                "items": {
                  "$ref": "#/components/schemas/Plant"
                }
              }
            }
          }
        },
        "400": {
          "description": "Unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Details:**

- **HTTP Method**: GET
- **Path**: /plants
- **Description**: Returns all plants the authenticated user can access
- **Authentication**: Bearer token required (inherited from global security)

**Query Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| limit | integer (int32) | No | Maximum number of results to return |

**Response Codes:**

- **200 OK**: Successfully retrieved plants
  - Content-Type: application/json
  - Schema: Array of Plant objects
  
- **400 Bad Request**: Error occurred (invalid parameters, authentication failure)
  - Content-Type: application/json
  - Schema: Error object with code and message

**Response Schema Reference:**

The 200 response references `#/components/schemas/Plant`, which is defined in the components section (lines 154-169). Each plant in the array includes:
- `name` (required): Plant name string
- `tag` (optional): Plant category/type string

#### POST /plants - Create New Plant

**Specification** (`openapi.json` lines 57-94):

```json
{
  "/plants": {
    "post": {
      "description": "Creates a new plant in the store",
      "requestBody": {
        "description": "Plant to add to the store",
        "content": {
          "application/json": {
            "schema": {
              "$ref": "#/components/schemas/NewPlant"
            }
          }
        },
        "required": true
      },
      "responses": {
        "200": {
          "description": "plant response",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Plant"
              }
            }
          }
        },
        "400": {
          "description": "unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Details:**

- **HTTP Method**: POST
- **Path**: /plants
- **Description**: Creates a new plant in the inventory
- **Authentication**: Bearer token required

**Request Body:**

- **Required**: Yes
- **Content-Type**: application/json
- **Schema**: NewPlant object (references `#/components/schemas/NewPlant`)

The NewPlant schema (lines 165-183) extends the Plant schema and adds:
- `id` (required): Unique identification number (integer, int64 format)
- `name` (required): Plant name (inherited from Plant schema)
- `tag` (optional): Plant category (inherited from Plant schema)

**Response Codes:**

- **200 OK**: Plant successfully created
  - Content-Type: application/json
  - Schema: Plant object (without id - returns only name and tag)
  
- **400 Bad Request**: Creation failed
  - Possible causes: Duplicate ID, invalid data, authentication failure
  - Content-Type: application/json
  - Schema: Error object

**Business Logic:**

The specification implies the server:
1. Validates the request body contains required fields (id, name)
2. Checks for duplicate IDs
3. Validates data types and formats
4. Stores the plant with the provided ID
5. Returns the plant data (name and tag only) upon success

#### DELETE /plants/{id} - Remove Plant

**Specification** (`openapi.json` lines 95-137):

```json
{
  "/plants/{id}": {
    "delete": {
      "description": "Deletes a single plant based on the ID supplied",
      "parameters": [
        {
          "name": "id",
          "in": "path",
          "description": "ID of plant to delete",
          "required": true,
          "schema": {
            "type": "integer",
            "format": "int64"
          }
        }
      ],
      "responses": {
        "204": {
          "description": "Plant deleted",
          "content": {}
        },
        "400": {
          "description": "unexpected error",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/Error"
              }
            }
          }
        }
      }
    }
  }
}
```

**Endpoint Details:**

- **HTTP Method**: DELETE
- **Path**: /plants/{id}
- **Description**: Deletes a single plant by ID
- **Authentication**: Bearer token required

**Path Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | integer (int64) | Yes | Unique identifier of plant to delete |

**Response Codes:**

- **204 No Content**: Plant successfully deleted
  - No response body
  - Empty content object in specification
  
- **400 Bad Request**: Deletion failed
  - Possible causes: Plant not found, invalid ID format, authentication failure
  - Content-Type: application/json
  - Schema: Error object

**Implementation Notes:**

- The 204 status code indicates successful deletion with no response body
- Idempotent operation: Deleting a non-existent plant may still return 204
- Path parameter is required and must be a valid int64 integer
- The server validates the ID format before attempting deletion

### Webhook System

**Webhook Specification** (`openapi.json` lines 139-173):

```json
{
  "webhooks": {
    "/plant/webhook": {
      "post": {
        "description": "Information about a new plant added to the store",
        "requestBody": {
          "description": "Plant added to the store",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/NewPlant"
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Return a 200 status to indicate that the data was received successfully"
          }
        }
      }
    }
  }
}
```

**Webhook Behavior:**

- **Trigger Event**: Occurs when a new plant is created via POST /plants
- **HTTP Method**: POST (the API sends POST requests to registered webhook URLs)
- **Payload**: NewPlant object containing id, name, and tag
- **Content-Type**: application/json

**Webhook Registration:**

The specification documents the webhook behavior but does not define the registration mechanism. In a production implementation, clients would typically:

1. Register webhook URLs through an API endpoint or configuration interface
2. Provide authentication credentials for the webhook endpoint
3. Specify which events trigger notifications

**Webhook Payload Structure:**

```json
{
  "id": 101,
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**Expected Webhook Receiver Response:**

- **200 OK**: Webhook successfully received and processed
- Webhook receivers should respond promptly (within seconds)
- Failed deliveries may trigger automatic retries based on implementation

**Implementation Considerations:**

- Webhook receivers must be accessible via HTTP/HTTPS
- Endpoints should handle requests asynchronously to avoid timeouts
- Implement idempotency to handle duplicate webhook deliveries
- Validate webhook authenticity using signatures or shared secrets
- Log all webhook deliveries for debugging and auditing

### Data Schemas

The OpenAPI specification defines three data models in the components section:

#### Plant Schema

**Definition** (`openapi.json` lines 154-169):

```json
{
  "Plant": {
    "required": [
      "name"
    ],
    "type": "object",
    "properties": {
      "name": {
        "description": "The name of the plant",
        "type": "string"
      },
      "tag": {
        "description": "Tag to specify the type",
        "type": "string"
      }
    }
  }
}
```

**Schema Properties:**

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| name | string | Yes | The name of the plant |
| tag | string | No | Tag to specify the plant type or category |

**Usage Contexts:**

- Response body for GET /plants (array of Plant objects)
- Response body for POST /plants (single Plant object)
- Base schema extended by NewPlant

**Validation Rules:**

- `name` field is mandatory (must be present and non-null)
- `name` should be a non-empty string
- `tag` is optional and can be omitted
- Additional properties not defined in the schema may be rejected

#### NewPlant Schema

**Definition** (`openapi.json` lines 165-183):

```json
{
  "NewPlant": {
    "allOf": [
      {
        "$ref": "#/components/schemas/Plant"
      },
      {
        "required": [
          "id"
        ],
        "type": "object",
        "properties": {
          "id": {
            "description": "Identification number of the plant",
            "type": "integer",
            "format": "int64"
          }
        }
      }
    ]
  }
}
```

**Schema Composition:**

The NewPlant schema uses OpenAPI's `allOf` composition keyword, combining:

1. All properties from the Plant schema (name, tag)
2. An additional required `id` property

**Effective Schema Properties:**

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| id | integer (int64) | Yes | Unique identification number |
| name | string | Yes | Plant name (inherited from Plant) |
| tag | string | No | Plant category (inherited from Plant) |

**Usage Contexts:**

- Request body for POST /plants
- Webhook payload for /plant/webhook

**Validation Rules:**

- `id` must be present and must be a valid int64 integer
- `id` should be unique (enforced by server logic)
- `name` is required (inherited constraint from Plant schema)
- `tag` is optional
- All Plant schema validation rules also apply

**Integer Format Specifications:**

- **int64**: Signed 64-bit integer
- Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
- Typically mapped to `long` in Java, `int64` in Go, `bigint` in JavaScript

#### Error Schema

**Definition** (`openapi.json` lines 184-194):

```json
{
  "Error": {
    "required": [
      "error",
      "message"
    ],
    "type": "object",
    "properties": {
      "error": {
        "type": "integer",
        "format": "int32"
      },
      "message": {
        "type": "string"
      }
    }
  }
}
```

**Schema Properties:**

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| error | integer (int32) | Yes | Numeric error code |
| message | string | Yes | Human-readable error description |

**Usage Contexts:**

- Response body for 400 Bad Request errors across all endpoints
- Returned when validation fails
- Returned when authentication fails
- Returned when business logic constraints are violated

**Example Error Responses:**

```json
{
  "error": 400,
  "message": "Invalid request parameters"
}
```

```json
{
  "error": 400,
  "message": "Plant with ID 101 already exists"
}
```

```json
{
  "error": 401,
  "message": "Authentication required"
}
```

**Error Code Conventions:**

While the schema allows any int32 value, typical HTTP status code conventions apply:
- 400: Bad Request (invalid parameters, validation failure)
- 401: Unauthorized (missing or invalid authentication)
- 403: Forbidden (insufficient permissions)
- 404: Not Found (resource doesn't exist)
- 500: Internal Server Error (server-side failure)

## Usage

### Authentication

All API requests require bearer token authentication as specified in the global security configuration (`openapi.json` lines 14-18).

**Obtaining an Access Token:**

The specification does not define the authentication endpoint or token acquisition process. In a production implementation, tokens would typically be obtained through:

1. OAuth 2.0 authorization flow
2. API key generation interface
3. Service account credentials
4. JWT token generation endpoint

**Making Authenticated Requests:**

Include the bearer token in the Authorization header of every request:

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

**Example: cURL**

```bash
curl -X GET "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." \
  -H "Content-Type: application/json"
```

**Example: JavaScript (fetch)**

```javascript
const accessToken = 'YOUR_ACCESS_TOKEN';

const response = await fetch('http://sandbox.mintlify.com/plants', {
  method: 'GET',
  headers: {
    'Authorization': `Bearer ${accessToken}`,
    'Content-Type': 'application/json'
  }
});

if (!response.ok) {
  const error = await response.json();
  console.error('API Error:', error);
  throw new Error(error.message);
}

const plants = await response.json();
console.log('Plants:', plants);
```

**Example: Python (requests)**

```python
import requests

access_token = 'YOUR_ACCESS_TOKEN'

headers = {
    'Authorization': f'Bearer {access_token}',
    'Content-Type': 'application/json'
}

response = requests.get('http://sandbox.mintlify.com/plants', headers=headers)

if response.status_code == 200:
    plants = response.json()
    print('Plants:', plants)
else:
    error = response.json()
    print(f"Error {error['error']}: {error['message']}")
```

**Security Best Practices:**

1. **Never hardcode tokens** in source code
2. **Use environment variables** for token storage
3. **Rotate tokens regularly** to minimize security risk
4. **Use HTTPS** in production (not demonstrated in sandbox URL)
5. **Implement token expiration** and refresh mechanisms
6. **Store tokens securely** using secure storage mechanisms
7. **Validate token format** before making requests

### Retrieving Plants

**Endpoint**: `GET /plants`

Retrieves a list of all plants the authenticated user has access to.

**Request Parameters:**

- **limit** (optional): Maximum number of results to return (integer)

**Example: Retrieve All Plants**

```bash
curl -X GET "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Accept: application/json"
```

**Example: Retrieve Limited Results**

```bash
curl -X GET "http://sandbox.mintlify.com/plants?limit=10" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Accept: application/json"
```

**Success Response (200 OK):**

```json
[
  {
    "name": "Fiddle Leaf Fig",
    "tag": "indoor"
  },
  {
    "name": "Snake Plant",
    "tag": "succulent"
  },
  {
    "name": "Monstera Deliciosa",
    "tag": "tropical"
  }
]
```

**Error Response (400 Bad Request):**

```json
{
  "error": 400,
  "message": "Invalid limit parameter: must be a positive integer"
}
```

**JavaScript Implementation:**

```javascript
class PlantStoreClient {
  constructor(baseURL, accessToken) {
    this.baseURL = baseURL;
    this.accessToken = accessToken;
  }

  async getPlants(limit = null) {
    const url = new URL(`${this.baseURL}/plants`);
    if (limit !== null) {
      url.searchParams.append('limit', limit);
    }

    const response = await fetch(url, {
      method: 'GET',
      headers: {
        'Authorization': `Bearer ${this.accessToken}`,
        'Accept': 'application/json'
      }
    });

    if (!response.ok) {
      const error = await response.json();
      throw new Error(`API Error ${error.error}: ${error.message}`);
    }

    return await response.json();
  }
}

// Usage
const client = new PlantStoreClient('http://sandbox.mintlify.com', 'YOUR_TOKEN');

try {
  // Get all plants
  const allPlants = await client.getPlants();
  console.log('All plants:', allPlants);

  // Get limited plants
  const limitedPlants = await client.getPlants(5);
  console.log('First 5 plants:', limitedPlants);
} catch (error) {
  console.error('Failed to retrieve plants:', error.message);
}
```

**Python Implementation:**

```python
import requests
from typing import Optional, List, Dict

class PlantStoreClient:
    def __init__(self, base_url: str, access_token: str):
        self.base_url = base_url
        self.access_token = access_token
        self.headers = {
            'Authorization': f'Bearer {access_token}',
            'Accept': 'application/json'
        }

    def get_plants(self, limit: Optional[int] = None) -> List[Dict]:
        """Retrieve plants from the store.
        
        Args:
            limit: Optional maximum number of results to return
            
        Returns:
            List of plant dictionaries
            
        Raises:
            Exception: If API request fails
        """
        url = f'{self.base_url}/plants'
        params = {'limit': limit} if limit is not None else {}
        
        response = requests.get(url, headers=self.headers, params=params)
        
        if response.status_code == 200:
            return response.json()
        else:
            error = response.json()
            raise Exception(f"API Error {error['error']}: {error['message']}")

# Usage
client = PlantStoreClient('http://sandbox.mintlify.com', 'YOUR_TOKEN')

try:
    # Get all plants
    all_plants = client.get_plants()
    print(f'Retrieved {len(all_plants)} plants')
    
    # Get limited plants
    limited_plants = client.get_plants(limit=5)
    print(f'First 5 plants: {limited_plants}')
except Exception as e:
    print(f'Error: {e}')
```

### Creating Plants

**Endpoint**: `POST /plants`

Creates a new plant in the inventory.

**Request Body Requirements:**

- **id** (required): Unique integer identifier (int64)
- **name** (required): Plant name string
- **tag** (optional): Plant category or type string

**Example: cURL Request**

```bash
curl -X POST "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "id": 101,
    "name": "Peace Lily",
    "tag": "flowering"
  }'
```

**Success Response (200 OK):**

```json
{
  "name": "Peace Lily",
  "tag": "flowering"
}
```

Note: The response returns the Plant schema (without id), not the NewPlant schema.

**Error Response (400 Bad Request) - Duplicate ID:**

```json
{
  "error": 400,
  "message": "Plant with ID 101 already exists"
}
```

**Error Response (400 Bad Request) - Missing Required Field:**

```json
{
  "error": 400,
  "message": "Missing required field: name"
}
```

**JavaScript Implementation:**

```javascript
async function createPlant(client, plantData) {
  // Validate required fields
  if (!plantData.id) {
    throw new Error('Plant ID is required');
  }
  if (!plantData.name) {
    throw new Error('Plant name is required');
  }

  const response = await fetch(`${client.baseURL}/plants`, {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${client.accessToken}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(plantData)
  });

  if (!response.ok) {
    const error = await response.json();
    throw new Error(`Failed to create plant: ${error.message}`);
  }

  return await response.json();
}

// Usage examples
try {
  // Create plant with tag
  const plant1 = await createPlant(client, {
    id: 102,
    name: 'Boston Fern',
    tag: 'fern'
  });
  console.log('Created plant:', plant1);

  // Create plant without tag
  const plant2 = await createPlant(client, {
    id: 103,
    name: 'Cactus'
  });
  console.log('Created plant:', plant2);
} catch (error) {
  console.error('Creation failed:', error.message);
}
```

**Python Implementation:**

```python
def create_plant(client: PlantStoreClient, plant_data: Dict) -> Dict:
    """Create a new plant in the store.
    
    Args:
        client: PlantStoreClient instance
        plant_data: Dictionary with id (required), name (required), tag (optional)
        
    Returns:
        Dictionary with created plant details
        
    Raises:
        ValueError: If required fields are missing
        Exception: If API request fails
    """
    # Validate required fields
    if 'id' not in plant_data:
        raise ValueError('Plant ID is required')
    if 'name' not in plant_data:
        raise ValueError('Plant name is required')
    
    url = f'{client.base_url}/plants'
    
    response = requests.post(
        url,
        headers=client.headers,
        json=plant_data
    )
    
    if response.status_code == 200:
        return response.json()
    else:
        error = response.json()
        raise Exception(f"API Error {error['error']}: {error['message']}")

# Usage examples
try:
    # Create plant with tag
    plant1 = create_plant(client, {
        'id': 104,
        'name': 'Pothos',
        'tag': 'vine'
    })
    print(f'Created plant: {plant1}')
    
    # Create plant without tag
    plant2 = create_plant(client, {
        'id': 105,
        'name': 'Aloe Vera'
    })
    print(f'Created plant: {plant2}')
except ValueError as e:
    print(f'Validation error: {e}')
except Exception as e:
    print(f'API error: {e}')
```

### Deleting Plants

**Endpoint**: `DELETE /plants/{id}`

Deletes a plant from the inventory by its unique identifier.

**Path Parameters:**

- **id** (required): Plant identification number (int64)

**Example: cURL Request**

```bash
curl -X DELETE "http://sandbox.mintlify.com/plants/101" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**Success Response (204 No Content):**

- HTTP status code 204
- Empty response body
- Indicates successful deletion

**Error Response (400 Bad Request):**

```json
{
  "error": 400,
  "message": "Plant with ID 101 not found"
}
```

**JavaScript Implementation:**

```javascript
async function deletePlant(client, plantId) {
  const response = await fetch(`${client.baseURL}/plants/${plantId}`, {
    method: 'DELETE',
    headers: {
      'Authorization': `Bearer ${client.accessToken}`
    }
  });

  if (response.status === 204) {
    return { success: true, message: 'Plant deleted successfully' };
  }

  if (!response.ok) {
    const error = await response.json();
    throw new Error(`Failed to delete plant: ${error.message}`);
  }
}

// Usage
try {
  await deletePlant(client, 101);
  console.log('Plant deleted successfully');
} catch (error) {
  console.error('Deletion failed:', error.message);
}
```

**Python Implementation:**

```python
def delete_plant(client: PlantStoreClient, plant_id: int) -> Dict:
    """Delete a plant from the store.
    
    Args:
        client: PlantStoreClient instance
        plant_id: Unique identifier of plant to delete
        
    Returns:
        Dictionary with success status
        
    Raises:
        Exception: If deletion fails
    """
    url = f'{client.base_url}/plants/{plant_id}'
    
    response = requests.delete(url, headers=client.headers)
    
    if response.status_code == 204:
        return {'success': True, 'message': 'Plant deleted successfully'}
    else:
        error = response.json()
        raise Exception(f"API Error {error['error']}: {error['message']}")

# Usage
try:
    result = delete_plant(client, 101)
    print(result['message'])
except Exception as e:
    print(f'Error: {e}')
```

### Webhook Integration

Implementing a webhook receiver to handle plant creation notifications.

**Webhook Specification:**

- **URL Path**: /plant/webhook (on your server)
- **HTTP Method**: POST (sent by the Plant Store API)
- **Content-Type**: application/json
- **Payload**: NewPlant object (id, name, tag)
- **Expected Response**: 200 OK

**Node.js/Express Webhook Receiver:**

```javascript
const express = require('express');
const app = express();

app.use(express.json());

// Webhook endpoint
app.post('/plant/webhook', async (req, res) => {
  const newPlant = req.body;
  
  // Validate webhook payload
  if (!newPlant.id || !newPlant.name) {
    return res.status(400).json({
      error: 400,
      message: 'Invalid webhook payload: missing required fields'
    });
  }
  
  // Log the webhook receipt
  console.log('[Webhook] New plant created:', {
    id: newPlant.id,
    name: newPlant.name,
    tag: newPlant.tag,
    timestamp: new Date().toISOString()
  });
  
  try {
    // Process the webhook (e.g., update database, send notifications)
    await processPlantCreation(newPlant);
    
    // Acknowledge receipt with 200 status
    res.status(200).json({
      received: true,
      timestamp: new Date().toISOString()
    });
  } catch (error) {
    console.error('[Webhook] Processing error:', error);
    
    // Return 200 even if processing fails to prevent retries
    // (or return error