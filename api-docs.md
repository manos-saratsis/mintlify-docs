# API Documentation

## Overview

This documentation provides a comprehensive reference for the **Plant Store API**, a RESTful API included as a demonstration in the Mintlify Documentation Starter Kit. The Plant Store API is a sample implementation designed to showcase how to document APIs using Mintlify's OpenAPI integration capabilities.

**Purpose**: The Plant Store API serves as a working example of OpenAPI 3.1.0 specification implementation, demonstrating best practices for API documentation including endpoints, authentication, webhooks, and data schemas. While functional as a sandbox API, its primary purpose is educational - showing documentation authors how to integrate their own API specifications into Mintlify documentation sites.

**API Characteristics**:
- **Base URL**: `http://sandbox.mintlify.com`
- **API Version**: 1.0.0
- **Specification Format**: OpenAPI 3.1.0
- **License**: MIT
- **Authentication**: Bearer token (HTTP Bearer authentication scheme)
- **Content Type**: application/json

**Source Files**:
- OpenAPI Specification: `api-reference/openapi.json` (194 lines)
- API Documentation: `api-docs.md`
- Endpoint Examples: `api-reference/endpoint/get.md`, `create.md`, `delete.md`, `webhook.md`

## Implementation

### OpenAPI Specification Structure

The Plant Store API is defined in `api-reference/openapi.json` following the OpenAPI 3.1.0 standard. The specification follows a hierarchical structure:

**Root Configuration** (lines 1-18):
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

### Authentication System

**Bearer Token Authentication** is configured globally for all endpoints.

**Security Requirement** (lines 14-18):
```json
{
  "security": [
    {
      "bearerAuth": []
    }
  ]
}
```

**Security Scheme Definition** (lines 175-179):
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

**Implementation Details**:
- **Authentication Type**: HTTP Bearer token authentication
- **Scope**: Applied globally to all API endpoints
- **Token Location**: `Authorization` header
- **Header Format**: `Authorization: Bearer {token}`

The bearer authentication scheme is a stateless authentication method where the client includes a token in the Authorization header of each request. The server validates this token to authenticate and authorize the request.

### API Endpoints

The Plant Store API defines three REST endpoints for managing plant inventory:

#### 1. GET /plants - Retrieve Plant List

**Endpoint Definition** (lines 20-56):
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

**Query Parameters**:
- `limit` (optional): Integer (int32) specifying maximum number of results to return

**Response Codes**:
- **200 Success**: Returns array of Plant objects
- **400 Error**: Returns Error object with error code and message

**Response Schema**: Array of `Plant` objects (defined in components/schemas)

#### 2. POST /plants - Create New Plant

**Endpoint Definition** (lines 57-94):
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

**Request Body**:
- **Required**: Yes
- **Content-Type**: application/json
- **Schema**: `NewPlant` object (includes id, name, and optional tag)

**Response Codes**:
- **200 Success**: Returns created Plant object
- **400 Error**: Returns Error object (e.g., duplicate ID, validation failure)

#### 3. DELETE /plants/{id} - Remove Plant

**Endpoint Definition** (lines 95-137):
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

**Path Parameters**:
- `id` (required): Integer (int64) identifying the plant to delete

**Response Codes**:
- **204 No Content**: Plant successfully deleted (no response body)
- **400 Error**: Returns Error object (e.g., plant not found)

### Webhook System

The API implements a webhook notification system for real-time event notifications.

**Webhook Endpoint** (lines 139-173):
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

**Webhook Behavior**:
- **Trigger Event**: New plant creation (POST /plants)
- **Payload**: NewPlant object (id, name, tag)
- **Expected Response**: HTTP 200 status code
- **Content-Type**: application/json

**Implementation Notes**:
- External systems register webhook URLs to receive notifications
- The API POSTs to registered webhook endpoints when new plants are created
- Webhook receivers must respond with 200 to acknowledge receipt
- Failed webhook deliveries may be retried based on implementation

### Data Schemas

The API defines three data schemas in the components section:

#### Plant Schema

**Definition** (lines 132-148):
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

**Properties**:
- `name` (string, required): The plant's name
- `tag` (string, optional): Type classification or category

**Usage**: Returned by GET and POST endpoints

#### NewPlant Schema

**Definition** (lines 151-169):
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

**Schema Composition**: Uses OpenAPI `allOf` to extend Plant schema

**Properties**:
- Inherits all Plant properties (name, tag)
- `id` (integer int64, required): Unique identification number

**Usage**: Required in POST request bodies and webhook payloads

#### Error Schema

**Definition** (lines 170-183):
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

**Properties**:
- `error` (integer int32, required): Numeric error code (typically HTTP status code)
- `message` (string, required): Human-readable error description

**Usage**: Returned in 400 error responses across all endpoints

### Mintlify Integration

The OpenAPI specification integrates seamlessly with Mintlify's documentation platform:

**Navigation Configuration** (`docs.json` lines 48-65):
```json
{
  "tab": "API reference",
  "groups": [
    {
      "group": "API documentation",
      "pages": [
        "api-reference/introduction"
      ]
    },
    {
      "group": "Endpoint examples",
      "pages": [
        "api-reference/endpoint/get",
        "api-reference/endpoint/create",
        "api-reference/endpoint/delete",
        "api-reference/endpoint/webhook"
      ]
    }
  ]
}
```

**Integration Features**:
- Automatic endpoint documentation generation from OpenAPI spec
- Interactive request/response examples
- Schema visualization and type documentation
- Authentication requirement display
- Integrated navigation structure

## Usage

### Authentication Setup

All API requests require bearer token authentication. Obtain your access token from the API provider and include it in request headers.

**Header Format**:
```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

**Example using curl**:
```bash
curl -X GET "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer your_token_here" \
  -H "Content-Type: application/json"
```

**Example using JavaScript (fetch)**:
```javascript
const response = await fetch('http://sandbox.mintlify.com/plants', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer your_token_here',
    'Content-Type': 'application/json'
  }
});

const plants = await response.json();
```

**Example using Python (requests)**:
```python
import requests

headers = {
    'Authorization': 'Bearer your_token_here',
    'Content-Type': 'application/json'
}

response = requests.get('http://sandbox.mintlify.com/plants', headers=headers)
plants = response.json()
```

### Retrieving Plants

**Endpoint**: `GET /plants`

**Get All Plants**:
```bash
curl -X GET "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**Response Example**:
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

**Get Limited Results**:
```bash
curl -X GET "http://sandbox.mintlify.com/plants?limit=10" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**JavaScript Implementation**:
```javascript
// Get all plants
async function getAllPlants() {
  const response = await fetch('http://sandbox.mintlify.com/plants', {
    headers: {
      'Authorization': 'Bearer YOUR_TOKEN',
      'Content-Type': 'application/json'
    }
  });
  
  if (!response.ok) {
    const error = await response.json();
    throw new Error(`API Error: ${error.message}`);
  }
  
  return await response.json();
}

// Get plants with limit
async function getLimitedPlants(limit) {
  const url = new URL('http://sandbox.mintlify.com/plants');
  url.searchParams.append('limit', limit);
  
  const response = await fetch(url, {
    headers: {
      'Authorization': 'Bearer YOUR_TOKEN',
      'Content-Type': 'application/json'
    }
  });
  
  return await response.json();
}
```

### Creating Plants

**Endpoint**: `POST /plants`

**curl Example**:
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

**Success Response**:
```json
{
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**Error Response** (400):
```json
{
  "error": 400,
  "message": "Plant with ID 101 already exists"
}
```

**JavaScript Implementation**:
```javascript
async function createPlant(plantData) {
  // Validate required fields
  if (!plantData.id || !plantData.name) {
    throw new Error('Plant ID and name are required');
  }
  
  const response = await fetch('http://sandbox.mintlify.com/plants', {
    method: 'POST',
    headers: {
      'Authorization': 'Bearer YOUR_TOKEN',
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

// Usage example
try {
  const newPlant = await createPlant({
    id: 102,
    name: 'Boston Fern',
    tag: 'fern'
  });
  console.log('Created plant:', newPlant);
} catch (error) {
  console.error('Error:', error.message);
}
```

**Python Implementation**:
```python
import requests
import json

def create_plant(plant_data):
    """Create a new plant in the store."""
    url = 'http://sandbox.mintlify.com/plants'
    headers = {
        'Authorization': 'Bearer YOUR_TOKEN',
        'Content-Type': 'application/json'
    }
    
    # Validate required fields
    if 'id' not in plant_data or 'name' not in plant_data:
        raise ValueError('Plant ID and name are required')
    
    response = requests.post(url, headers=headers, json=plant_data)
    
    if response.status_code == 200:
        return response.json()
    else:
        error = response.json()
        raise Exception(f"API Error {error['error']}: {error['message']}")

# Usage example
try:
    new_plant = create_plant({
        'id': 103,
        'name': 'Pothos',
        'tag': 'vine'
    })
    print('Created plant:', new_plant)
except Exception as e:
    print('Error:', str(e))
```

### Deleting Plants

**Endpoint**: `DELETE /plants/{id}`

**curl Example**:
```bash
curl -X DELETE "http://sandbox.mintlify.com/plants/101" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**Success Response**: HTTP 204 No Content (empty response body)

**Error Response** (400):
```json
{
  "error": 400,
  "message": "Plant with ID 101 not found"
}
```

**JavaScript Implementation**:
```javascript
async function deletePlant(plantId) {
  const response = await fetch(`http://sandbox.mintlify.com/plants/${plantId}`, {
    method: 'DELETE',
    headers: {
      'Authorization': 'Bearer YOUR_TOKEN',
      'Content-Type': 'application/json'
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

// Usage with error handling
try {
  await deletePlant(101);
  console.log('Plant deleted successfully');
} catch (error) {
  console.error('Deletion failed:', error.message);
}
```

**Python Implementation**:
```python
def delete_plant(plant_id):
    """Delete a plant by ID."""
    url = f'http://sandbox.mintlify.com/plants/{plant_id}'
    headers = {
        'Authorization': 'Bearer YOUR_TOKEN',
        'Content-Type': 'application/json'
    }
    
    response = requests.delete(url, headers=headers)
    
    if response.status_code == 204:
        return {'success': True, 'message': 'Plant deleted successfully'}
    else:
        error = response.json()
        raise Exception(f"API Error {error['error']}: {error['message']}")

# Usage example
try:
    result = delete_plant(101)
    print(result['message'])
except Exception as e:
    print('Error:', str(e))
```

### Implementing Webhook Receivers

**Webhook Payload** (NewPlant schema):
```json
{
  "id": 104,
  "name": "Spider Plant",
  "tag": "hanging"
}
```

**Node.js/Express Webhook Receiver**:
```javascript
const express = require('express');
const app = express();

app.use(express.json());

app.post('/plant/webhook', (req, res) => {
  const newPlant = req.body;
  
  // Validate webhook payload
  if (!newPlant.id || !newPlant.name) {
    return res.status(400).json({
      error: 400,
      message: 'Invalid webhook payload'
    });
  }
  
  // Process the new plant notification
  console.log('New plant added:', newPlant);
  
  // Store in database, send notifications, etc.
  // ... your business logic here
  
  // Acknowledge receipt with 200 status
  res.status(200).json({
    received: true,
    timestamp: new Date().toISOString()
  });
});

app.listen(3000, () => {
  console.log('Webhook receiver listening on port 3000');
});
```

**Python/Flask Webhook Receiver**:
```python
from flask import Flask, request, jsonify
from datetime import datetime

app = Flask(__name__)

@app.route('/plant/webhook', methods=['POST'])
def plant_webhook():
    """Receive new plant notifications."""
    new_plant = request.json
    
    # Validate webhook payload
    if 'id' not in new_plant or 'name' not in new_plant:
        return jsonify({
            'error': 400,
            'message': 'Invalid webhook payload'
        }), 400
    
    # Process the new plant notification
    print(f"New plant added: {new_plant}")
    
    # Store in database, send notifications, etc.
    # ... your business logic here
    
    # Acknowledge receipt
    return jsonify({
        'received': True,
        'timestamp': datetime.utcnow().isoformat()
    }), 200

if __name__ == '__main__':
    app.run(port=3000)
```

### Error Handling Best Practices

**Comprehensive Error Handling Pattern**:
```javascript
class PlantStoreAPIClient {
  constructor(baseURL, token) {
    this.baseURL = baseURL;
    this.token = token;
  }
  
  async request(endpoint, options = {}) {
    const url = `${this.baseURL}${endpoint}`;
    const headers = {
      'Authorization': `Bearer ${this.token}`,
      'Content-Type': 'application/json',
      ...options.headers
    };
    
    try {
      const response = await fetch(url, {
        ...options,
        headers
      });
      
      // Handle successful deletion (204 No Content)
      if (response.status === 204) {
        return { success: true };
      }
      
      // Parse JSON response
      const data = await response.json();
      
      // Handle error responses
      if (!response.ok) {
        throw new APIError(
          data.error || response.status,
          data.message || 'Unknown error occurred',
          data
        );
      }
      
      return data;
    } catch (error) {
      if (error instanceof APIError) {
        throw error;
      }
      
      // Handle network errors
      throw new APIError(
        0,
        `Network error: ${error.message}`,
        null
      );
    }
  }
  
  async getPlants(limit) {
    const endpoint = limit ? `/plants?limit=${limit}` : '/plants';
    return await this.request(endpoint);
  }
  
  async createPlant(plantData) {
    return await this.request('/plants', {
      method: 'POST',
      body: JSON.stringify(plantData)
    });
  }
  
  async deletePlant(plantId) {
    return await this.request(`/plants/${plantId}`, {
      method: 'DELETE'
    });
  }
}

class APIError extends Error {
  constructor(code, message, data) {
    super(message);
    this.name = 'APIError';
    this.code = code;
    this.data = data;
  }
}

// Usage example with error handling
const client = new PlantStoreAPIClient(
  'http://sandbox.mintlify.com',
  'YOUR_TOKEN'
);

async function exampleUsage() {
  try {
    // Get plants
    const plants = await client.getPlants(10);
    console.log('Plants:', plants);
    
    // Create plant
    const newPlant = await client.createPlant({
      id: 105,
      name: 'Rubber Plant',
      tag: 'indoor'
    });
    console.log('Created:', newPlant);
    
    // Delete plant
    await client.deletePlant(105);
    console.log('Deleted successfully');
    
  } catch (error) {
    if (error instanceof APIError) {
      console.error(`API Error ${error.code}: ${error.message}`);
      if (error.data) {
        console.error('Error details:', error.data);
      }
    } else {
      console.error('Unexpected error:', error.message);
    }
  }
}
```

### Rate Limiting and Best Practices

**Request Optimization Strategies**:

1. **Use Limit Parameter**: Request only needed data
```javascript
// Good: Request specific amount
const plants = await client.getPlants(25);

// Avoid: Requesting all data when only few needed
const allPlants = await client.getPlants(); // May return thousands
```

2. **Implement Exponential Backoff**:
```javascript
async function fetchWithRetry(fn, maxRetries = 3) {
  let lastError;
  
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fn();
    } catch (error) {
      lastError = error;
      
      if (error.code === 429) { // Rate limit exceeded
        const delay = Math.pow(2, i) * 1000; // Exponential backoff
        console.log(`Rate limited, retrying in ${delay}ms...`);
        await new Promise(resolve => setTimeout(resolve, delay));
      } else {
        throw error; // Don't retry other errors
      }
    }
  }
  
  throw lastError;
}

// Usage
const plants = await fetchWithRetry(() => client.getPlants());
```

3. **Implement Caching**:
```javascript
class CachedPlantStoreClient extends PlantStoreAPIClient {
  constructor(baseURL, token, cacheTTL = 60000) {
    super(baseURL, token);
    this.cache = new Map();
    this.cacheTTL = cacheTTL;
  }
  
  async getPlants(limit) {
    const cacheKey = `plants_${limit || 'all'}`;
    const cached = this.cache.get(cacheKey);
    
    if (cached && Date.now() - cached.timestamp < this.cacheTTL) {
      console.log('Returning cached data');
      return cached.data;
    }
    
    const data = await super.getPlants(limit);
    
    this.cache.set(cacheKey, {
      data,
      timestamp: Date.now()
    });
    
    return data;
  }
}
```

### Security Best Practices

**Token Management**:

1. **Never Hardcode Tokens**:
```javascript
// ❌ Bad: Hardcoded token
const client = new PlantStoreAPIClient(
  'http://sandbox.mintlify.com',
  'abc123token'
);

// ✅ Good: Environment variable
const client = new PlantStoreAPIClient(
  process.env.API_BASE_URL,
  process.env.API_TOKEN
);
```

2. **Secure Token Storage** (Browser):
```javascript
// Store token securely
class SecureTokenStorage {
  static setToken(token) {
    // Use sessionStorage for temporary storage
    sessionStorage.setItem('api_token', token);
    
    // Or use secure cookie with httpOnly flag (server-side)
  }
  
  static getToken() {
    return sessionStorage.getItem('api_token');
  }
  
  static clearToken() {
    sessionStorage.removeItem('api_token');
  }
}
```

3. **Token Rotation**:
```javascript
class TokenManager {
  constructor(baseURL) {
    this.baseURL = baseURL;
    this.token = null;
    this.tokenExpiry = null;
  }
  
  async ensureValidToken() {
    if (this.token && this.tokenExpiry > Date.now()) {
      return this.token;
    }
    
    // Refresh token logic
    const newToken = await this.refreshToken();
    this.token = newToken.access_token;
    this.tokenExpiry = Date.now() + (newToken.expires_in * 1000);
    
    return this.token;
  }
  
  async refreshToken() {
    // Implementation depends on authentication service
    // This is a placeholder example
    const response = await fetch(`${this.baseURL}/auth/refresh`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ refresh_token: this.getRefreshToken() })
    });
    
    return await response.json();
  }
}
```

### Testing API Integration

**Unit Test Example (Jest)**:
```javascript
const PlantStoreAPIClient = require('./plant-store-client');

describe('PlantStoreAPIClient', () => {
  let client;
  
  beforeEach(() => {
    client = new PlantStoreAPIClient(
      'http://sandbox.mintlify.com',
      'test_token'
    );
  });
  
  describe('getPlants', () => {
    it('should fetch all plants without limit', async () => {
      global.fetch = jest.fn(() =>
        Promise.resolve({
          ok: true,
          json: () => Promise.resolve([
            { name: 'Test Plant 1', tag: 'indoor' },
            { name: 'Test Plant 2', tag: 'outdoor' }
          ])
        })
      );
      
      const plants = await client.getPlants();
      
      expect(plants).toHaveLength(2);
      expect(plants[0].name).toBe('Test Plant 1');
      expect(fetch).toHaveBeenCalledWith(
        'http://sandbox.mintlify.com/plants',
        expect.objectContaining({
          headers: expect.objectContaining({
            'Authorization': 'Bearer test_token'
          })
        })
      );
    });
    
    it('should respect limit parameter', async () => {
      global.fetch = jest.fn(() =>
        Promise.resolve({
          ok: true,
          json: () => Promise.resolve([
            { name: 'Test Plant', tag: 'indoor' }
          ])
        })
      );
      
      await client.getPlants(1);
      
      expect(fetch).toHaveBeenCalledWith(
        'http://sandbox.mintlify.com/plants?limit=1',
        expect.any(Object)
      );
    });
  });
  
  describe('createPlant', () => {
    it('should create plant with valid data', async () => {
      const plantData = {
        id: 999,
        name: 'Test Plant',
        tag: 'test'
      };
      
      global.fetch = jest.fn(() =>
        Promise.resolve({
          ok: true,
          json: () => Promise.resolve({
            name: plantData.name,
            tag: plantData.tag
          })
        })
      );
      
      const result = await client.createPlant(plantData);
      
      expect(result.name).toBe('Test Plant');
      expect(fetch).toHaveBeenCalledWith(
        'http://sandbox.mintlify.com/plants',
        expect.objectContaining({
          method: 'POST',
          body: JSON.stringify(plantData)
        })
      );
    });
    
    it('should handle duplicate ID error', async () => {
      global.fetch