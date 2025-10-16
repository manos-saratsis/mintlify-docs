# API Documentation

## Overview

This documentation covers the **Plant Store API**, a RESTful API included as a demonstration in the Mintlify documentation starter kit. The API provides endpoints for managing a plant inventory system, including operations to retrieve, create, and delete plant records. The API specification follows the OpenAPI 3.1.0 standard and is defined in `api-reference/openapi.json`.

**Base URL**: `http://sandbox.mintlify.com`

**API Version**: 1.0.0

**License**: MIT

The API is designed as a sample implementation to demonstrate how to document APIs using Mintlify's OpenAPI integration. All endpoints require bearer token authentication for secure access.

## Authentication

### Bearer Token Authentication

All API requests require authentication using the HTTP Bearer authentication scheme.

**Implementation**:

The security configuration is defined in `api-reference/openapi.json` (lines 14-17):

```json
"security": [
  {
    "bearerAuth": []
  }
]
```

The bearer authentication scheme is defined in the security schemes section (lines 175-179):

```json
"securitySchemes": {
  "bearerAuth": {
    "type": "http",
    "scheme": "bearer"
  }
}
```

**Usage**:

Include your bearer token in the `Authorization` header of every API request:

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Example using curl:

```bash
curl -X GET "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

**Security Notes**:
- Keep your bearer token secure and never expose it in client-side code
- Tokens should be transmitted only over HTTPS in production environments
- The API applies bearer authentication globally to all endpoints

## Endpoints

### GET /plants

Retrieves all plants from the system that the authenticated user has access to.

**Endpoint**: `GET /plants`

**Implementation**: Defined in `api-reference/openapi.json` (lines 20-56)

**Query Parameters**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| limit | integer (int32) | No | The maximum number of results to return |

**Request Example**:

```bash
GET http://sandbox.mintlify.com/plants?limit=10
Authorization: Bearer YOUR_ACCESS_TOKEN
```

**Response - 200 Success**:

Returns an array of Plant objects.

Response schema (lines 41-48):
```json
{
  "type": "array",
  "items": {
    "$ref": "#/components/schemas/Plant"
  }
}
```

Example response body:
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

**Response - 400 Error**:

Returns an Error object when the request fails.

Error response schema (lines 51-57):
```json
{
  "$ref": "#/components/schemas/Error"
}
```

Example error response:
```json
{
  "error": 400,
  "message": "Invalid limit parameter"
}
```

**Usage Notes**:
- If no `limit` parameter is provided, all accessible plants are returned
- The limit parameter helps with pagination and performance for large datasets
- The response order is determined by the server implementation

---

### POST /plants

Creates a new plant in the store inventory.

**Endpoint**: `POST /plants`

**Implementation**: Defined in `api-reference/openapi.json` (lines 57-94)

**Request Body**:

Required. Content-Type: `application/json`

The request body must contain a NewPlant object (lines 62-69):

```json
{
  "description": "Plant to add to the store",
  "content": {
    "application/json": {
      "schema": {
        "$ref": "#/components/schemas/NewPlant"
      }
    }
  },
  "required": true
}
```

**NewPlant Schema**:

NewPlant extends the Plant schema with an additional required `id` field (lines 151-169):

```json
{
  "allOf": [
    {
      "$ref": "#/components/schemas/Plant"
    },
    {
      "required": ["id"],
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
```

**Required Fields**:
- `id` (integer, int64): Unique identification number for the plant
- `name` (string): The name of the plant

**Optional Fields**:
- `tag` (string): Tag to specify the plant type

**Request Example**:

```bash
POST http://sandbox.mintlify.com/plants
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

{
  "id": 101,
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**Response - 200 Success**:

Returns the created Plant object (lines 72-79):

```json
{
  "description": "plant response",
  "content": {
    "application/json": {
      "schema": {
        "$ref": "#/components/schemas/Plant"
      }
    }
  }
}
```

Example success response:
```json
{
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**Response - 400 Error**:

Returns an Error object if the plant cannot be created (lines 82-88):

```json
{
  "description": "unexpected error",
  "content": {
    "application/json": {
      "schema": {
        "$ref": "#/components/schemas/Error"
      }
    }
  }
}
```

Example error response:
```json
{
  "error": 400,
  "message": "Plant with ID 101 already exists"
}
```

**Usage Notes**:
- The `id` field must be unique across all plants in the system
- Duplicate IDs will result in a 400 error response
- The response returns only the Plant properties (name and tag), not including the ID

---

### DELETE /plants/{id}

Deletes a single plant based on the ID supplied.

**Endpoint**: `DELETE /plants/{id}`

**Implementation**: Defined in `api-reference/openapi.json` (lines 95-137)

**Path Parameters**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | integer (int64) | Yes | ID of the plant to delete |

Path parameter definition (lines 99-108):
```json
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
```

**Request Example**:

```bash
DELETE http://sandbox.mintlify.com/plants/101
Authorization: Bearer YOUR_ACCESS_TOKEN
```

**Response - 204 Success**:

No content returned. The plant has been successfully deleted (lines 111-114):

```json
{
  "description": "Plant deleted",
  "content": {}
}
```

A 204 status code indicates successful deletion with no response body.

**Response - 400 Error**:

Returns an Error object if the deletion fails (lines 117-123):

```json
{
  "description": "unexpected error",
  "content": {
    "application/json": {
      "schema": {
        "$ref": "#/components/schemas/Error"
      }
    }
  }
}
```

Example error response:
```json
{
  "error": 400,
  "message": "Plant with ID 101 not found"
}
```

**Usage Notes**:
- The deletion operation is idempotent - deleting an already-deleted plant returns the same success response
- There is no undo operation; deletions are permanent
- Always verify the plant ID before deletion in production systems
- The endpoint returns 204 with no body on success, not 200

---

## Webhooks

### POST /plant/webhook

Webhook endpoint that receives notifications when a new plant is added to the store.

**Webhook**: `POST /plant/webhook`

**Implementation**: Defined in `api-reference/openapi.json` (lines 139-173)

**Purpose**:

This webhook allows external systems to receive real-time notifications when new plants are added to the inventory. Your system can register a webhook URL, and the Plant Store API will POST new plant information to your endpoint whenever a plant is created.

**Webhook Payload**:

The webhook POST request contains a NewPlant object (lines 143-152):

```json
{
  "description": "Plant added to the store",
  "content": {
    "application/json": {
      "schema": {
        "$ref": "#/components/schemas/NewPlant"
      }
    }
  }
}
```

Example webhook payload:
```json
{
  "id": 102,
  "name": "Rubber Plant",
  "tag": "indoor"
}
```

**Expected Response**:

Your webhook endpoint must return a 200 status code to acknowledge successful receipt (lines 155-157):

```json
{
  "description": "Return a 200 status to indicate that the data was received successfully"
}
```

**Implementation Requirements**:

To implement a webhook receiver:

1. **Create an HTTPS endpoint** at your specified URL
2. **Accept POST requests** with JSON payloads
3. **Parse the NewPlant schema** from the request body
4. **Return HTTP 200** status code to confirm receipt
5. **Handle errors gracefully** and implement retry logic if needed

Example webhook receiver (Node.js/Express):

```javascript
app.post('/plant/webhook', (req, res) => {
  const newPlant = req.body;
  
  console.log('New plant received:', newPlant);
  
  // Process the new plant data
  // Store in database, send notifications, etc.
  
  // Return 200 to acknowledge receipt
  res.status(200).send('Webhook received');
});
```

**Usage Notes**:
- Webhook endpoints must be publicly accessible over HTTPS
- Implement proper authentication/verification for webhook requests in production
- Consider implementing idempotency to handle duplicate webhook deliveries
- Store webhook payloads for audit and debugging purposes
- Implement exponential backoff if your webhook endpoint fails

---

## Data Models

### Plant

Base plant object representing a plant in the inventory system.

**Schema Location**: `api-reference/openapi.json` (lines 132-148)

**Implementation**:

```json
{
  "Plant": {
    "required": ["name"],
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

| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| name | string | Yes | The name of the plant | "Boston Fern" |
| tag | string | No | Tag to specify the type | "fern" |

**JSON Example**:

```json
{
  "name": "Aloe Vera",
  "tag": "succulent"
}
```

**Usage**:
- The Plant schema is used in GET responses to return plant data
- The Plant schema is also used in POST responses to confirm creation
- The `name` field is always required; missing names will cause validation errors
- The `tag` field provides optional categorization for filtering and organization

---

### NewPlant

Extended plant object used when creating new plants. Includes all Plant properties plus a unique identifier.

**Schema Location**: `api-reference/openapi.json` (lines 149-169)

**Implementation**:

The NewPlant schema uses OpenAPI's `allOf` composition to extend the Plant schema:

```json
{
  "NewPlant": {
    "allOf": [
      {
        "$ref": "#/components/schemas/Plant"
      },
      {
        "required": ["id"],
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

**Properties**:

| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| id | integer (int64) | Yes | Unique identification number | 12345 |
| name | string | Yes | The name of the plant | "Spider Plant" |
| tag | string | No | Tag to specify the type | "hanging" |

**JSON Example**:

```json
{
  "id": 200,
  "name": "Pothos",
  "tag": "vine"
}
```

**Usage**:
- NewPlant is used in POST request bodies when creating plants
- NewPlant is used in webhook payloads when notifying about new plants
- The `id` field must be unique across the entire plant inventory
- The `id` is a 64-bit integer, supporting large-scale inventories
- All Plant properties (name, tag) are inherited in NewPlant

**Schema Composition Notes**:
- The `allOf` keyword combines the Plant schema with additional properties
- This approach ensures consistency between Plant and NewPlant schemas
- Changes to the Plant schema automatically apply to NewPlant
- The composition pattern follows OpenAPI best practices for schema reuse

---

### Error

Standard error response object returned when API operations fail.

**Schema Location**: `api-reference/openapi.json` (lines 170-183)

**Implementation**:

```json
{
  "Error": {
    "required": ["error", "message"],
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

| Property | Type | Required | Description | Example |
|----------|------|----------|-------------|---------|
| error | integer (int32) | Yes | Numeric error code | 400 |
| message | string | Yes | Human-readable error description | "Plant not found" |

**JSON Example**:

```json
{
  "error": 400,
  "message": "Invalid plant data: name field is required"
}
```

**Common Error Codes**:

| Code | Description | Typical Causes |
|------|-------------|----------------|
| 400 | Bad Request | Invalid input data, missing required fields, malformed JSON |
| 401 | Unauthorized | Missing or invalid bearer token |
| 404 | Not Found | Plant ID does not exist |
| 409 | Conflict | Duplicate plant ID on creation |
| 500 | Internal Server Error | Server-side processing error |

**Usage**:
- All error responses use this consistent Error schema
- The `error` field contains the HTTP status code
- The `message` field provides specific details about what went wrong
- Error messages should be logged for debugging but may be shown to users
- Client applications should handle errors gracefully based on error codes

---

## Integration Guide

### Setting Up API Access

**Step 1: Obtain Access Credentials**

Contact the API provider to receive your bearer token. Store this token securely using environment variables or a secrets management system:

```bash
# .env file
PLANT_STORE_API_TOKEN=your_bearer_token_here
```

**Step 2: Configure API Client**

Set up your HTTP client with the base URL and authentication:

```javascript
// JavaScript example
const axios = require('axios');

const apiClient = axios.create({
  baseURL: 'http://sandbox.mintlify.com',
  headers: {
    'Authorization': `Bearer ${process.env.PLANT_STORE_API_TOKEN}`,
    'Content-Type': 'application/json'
  }
});
```

```python
# Python example
import os
import requests

BASE_URL = 'http://sandbox.mintlify.com'
HEADERS = {
    'Authorization': f'Bearer {os.environ["PLANT_STORE_API_TOKEN"]}',
    'Content-Type': 'application/json'
}
```

### Common Integration Patterns

**Retrieving and Displaying Plants**

```javascript
// JavaScript example
async function getAllPlants(limit = 50) {
  try {
    const response = await apiClient.get('/plants', {
      params: { limit }
    });
    return response.data;
  } catch (error) {
    console.error('Error fetching plants:', error.response.data);
    throw error;
  }
}
```

**Creating Plants with Validation**

```javascript
// JavaScript example
async function createPlant(plantData) {
  // Validate required fields
  if (!plantData.id || !plantData.name) {
    throw new Error('Plant ID and name are required');
  }
  
  try {
    const response = await apiClient.post('/plants', plantData);
    console.log('Plant created successfully:', response.data);
    return response.data;
  } catch (error) {
    if (error.response.status === 400) {
      console.error('Invalid plant data:', error.response.data.message);
    }
    throw error;
  }
}
```

**Deleting Plants Safely**

```javascript
// JavaScript example
async function deletePlant(plantId) {
  try {
    await apiClient.delete(`/plants/${plantId}`);
    console.log(`Plant ${plantId} deleted successfully`);
    return true;
  } catch (error) {
    if (error.response.status === 404) {
      console.warn(`Plant ${plantId} not found`);
    }
    throw error;
  }
}
```

**Implementing Webhook Receiver**

```javascript
// Express.js webhook endpoint
const express = require('express');
const app = express();

app.post('/plant/webhook', express.json(), (req, res) => {
  const newPlant = req.body;
  
  // Validate webhook payload
  if (!newPlant.id || !newPlant.name) {
    return res.status(400).send('Invalid webhook payload');
  }
  
  // Process the new plant
  console.log('New plant notification:', newPlant);
  
  // Store in database, send notifications, etc.
  // ... your business logic here
  
  // Acknowledge receipt
  res.status(200).send('Webhook processed');
});
```

### Error Handling Best Practices

```javascript
// Comprehensive error handling example
async function apiOperation() {
  try {
    const response = await apiClient.get('/plants');
    return response.data;
  } catch (error) {
    if (error.response) {
      // Server returned error response
      const { error: errorCode, message } = error.response.data;
      
      switch (errorCode) {
        case 400:
          console.error('Bad request:', message);
          // Handle invalid input
          break;
        case 401:
          console.error('Authentication failed');
          // Refresh token or prompt for login
          break;
        case 404:
          console.error('Resource not found:', message);
          // Handle missing resource
          break;
        default:
          console.error('API error:', message);
      }
    } else if (error.request) {
      // Request made but no response received
      console.error('Network error: No response from server');
    } else {
      // Error setting up the request
      console.error('Request error:', error.message);
    }
    
    throw error;
  }
}
```

---

## Rate Limiting and Best Practices

### API Usage Guidelines

While specific rate limits are not defined in the OpenAPI specification, follow these best practices for reliable API usage:

**Request Optimization**:
- Use the `limit` parameter on GET requests to retrieve only needed data
- Implement caching for frequently accessed plant data
- Batch operations when possible to reduce request count
- Use conditional requests (ETags) if supported by the server implementation

**Error Handling**:
- Implement exponential backoff for failed requests
- Log all errors with request context for debugging
- Provide user-friendly error messages in your application
- Monitor error rates to detect API or connectivity issues

**Security**:
- Never expose bearer tokens in client-side code or version control
- Rotate access tokens regularly
- Use HTTPS for all API communications in production
- Validate and sanitize all user input before sending to the API

**Webhook Implementation**:
- Verify webhook authenticity using signature validation if available
- Implement idempotency to handle duplicate webhook deliveries
- Use a queue system to process webhooks asynchronously
- Return 200 status quickly and process data in background jobs

---

## Development Workflow

### Local Development

**Testing with curl**:

```bash
# Get all plants
curl -X GET "http://sandbox.mintlify.com/plants?limit=10" \
  -H "Authorization: Bearer YOUR_TOKEN"

# Create a plant
curl -X POST "http://sandbox.mintlify.com/plants" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"id": 999, "name": "Test Plant", "tag": "test"}'

# Delete a plant
curl -X DELETE "http://sandbox.mintlify.com/plants/999" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**API Documentation Preview**:

This API documentation is built using Mintlify. To preview the documentation locally:

1. Install the Mintlify CLI:
```bash
npm i -g mint
```

2. Navigate to the documentation directory (where `docs.json` is located)

3. Start the development server:
```bash
mint dev
```

4. Open your browser to `http://localhost:3000`

5. View the API reference tab to see the OpenAPI-generated documentation

**Updating API Documentation**:

The API documentation is automatically generated from `api-reference/openapi.json`. To update:

1. Modify the OpenAPI specification in `api-reference/openapi.json`
2. Save the file
3. The local preview will automatically update (if running `mint dev`)
4. Commit and push changes to deploy to production

### Deployment

Changes to the API documentation deploy automatically when pushed to the default branch (as configured in `README.md` line 36). The Mintlify GitHub app monitors the repository and triggers deployments on every commit.

**Troubleshooting**:

- **Preview not starting**: Run `mint update` to ensure you have the latest CLI version (`README.md` line 41)
- **404 errors**: Verify you're running `mint dev` in the directory containing `docs.json` (`README.md` line 42)
- **Changes not deploying**: Ensure the Mintlify GitHub app is installed from your dashboard (`README.md` line 35)

---

## Support and Resources

### Getting Help

- **Support Email**: hi@mintlify.com (from `docs.json` line 73)
- **Dashboard**: [https://dashboard.mintlify.com](https://dashboard.mintlify.com) (from `docs.json` line 78)
- **Documentation**: [https://mintlify.com/docs](https://mintlify.com/docs) (from `docs.json` line 66)
- **Blog**: [https://mintlify.com/blog](https://mintlify.com/blog) (from `docs.json` line 70)

### Additional Resources

- **GitHub Repository**: [https://github.com/mintlify](https://github.com/mintlify) (from `docs.json` line 105)
- **LinkedIn**: [https://linkedin.com/company/mintlify](https://linkedin.com/company/mintlify) (from `docs.json` line 106)
- **Twitter/X**: [https://x.com/mintlify](https://x.com/mintlify) (from `docs.json` line 104)

---

## Appendix

### OpenAPI Specification

The complete OpenAPI specification for this API is located at `api-reference/openapi.json` in the project repository. The specification follows OpenAPI 3.1.0 standards and includes:

- Complete endpoint definitions with request/response schemas
- Security scheme configurations
- Reusable component schemas
- Webhook specifications
- Server configuration

**Specification Metadata** (from `api-reference/openapi.json` lines 1-9):

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
  }
}
```

### Navigation Configuration

The API documentation is integrated into the Mintlify documentation site through the navigation configuration in `docs.json` (lines 43-57):

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

This creates a dedicated "API reference" tab with two sections:
- API documentation: Introduction and overview
- Endpoint examples: Detailed documentation for each endpoint

---

**Note**: This API documentation is based on the actual OpenAPI specification file (`api-reference/openapi.json`) included in the Mintlify documentation starter kit. The Plant Store API is a demonstration example designed to show how OpenAPI specifications integrate with Mintlify documentation. For production APIs, replace the OpenAPI specification with your actual API definition.