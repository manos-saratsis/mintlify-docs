# Endpoints Reference

## Getting Started with the API

The Plant Store API allows you to manage your plant inventory through simple web requests. All interactions require an access token for security.

**What You'll Need:**
- An access token (you'll receive this when you sign up)
- The ability to make web requests (through your browser, a tool, or your application)

**Base Web Address:**
All requests go to: `http://sandbox.mintlify.com`

## Authentication

Every request you make needs to include your access token for security. Think of it like showing your membership card - it proves you have permission to access the system.

**How to Include Your Token:**

When making requests, add a special header called "Authorization" with your token:

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Replace `YOUR_ACCESS_TOKEN` with the actual token provided to you.

## Available Actions

### View Your Plants

**What it does:** Shows you all the plants in your inventory that you have permission to see.

**How to access:** Send a GET request to `/plants`

**Optional Settings:**
- **limit**: Control how many plants you want to see at once. For example, if you only want to see 10 plants instead of hundreds, set this to 10.

**What you'll get back:**

When successful, you'll receive a list of your plants. Each plant shows:
- The plant's name
- A tag describing the plant type (optional)

**Example of what you'll see:**
```json
[
  {
    "name": "Fiddle Leaf Fig",
    "tag": "indoor"
  },
  {
    "name": "Snake Plant",
    "tag": "succulent"
  }
]
```

**If something goes wrong:**

You'll receive an error message explaining what happened. This includes:
- An error number indicating the type of problem
- A description of what went wrong

### Add a New Plant

**What it does:** Adds a new plant to your inventory.

**How to access:** Send a POST request to `/plants`

**What you need to provide:**

You must send the following information about the plant:
- **id**: A unique number for this plant (required)
- **name**: The plant's name (required)
- **tag**: A category or type for the plant (optional)

**Example information to send:**
```json
{
  "id": 101,
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**What you'll get back:**

When successful, you'll see confirmation with the plant's details:
```json
{
  "name": "Peace Lily",
  "tag": "flowering"
}
```

**If something goes wrong:**

You might see an error message if:
- A plant with that ID already exists
- Required information is missing
- The information format is incorrect

The error message will include:
- An error number
- An explanation of the problem

### Remove a Plant

**What it does:** Permanently removes a plant from your inventory.

**How to access:** Send a DELETE request to `/plants/{id}` where `{id}` is the plant's ID number

**What you need to provide:**
- The ID number of the plant you want to remove (included in the web address)

**Example:** To delete plant #101, send the request to `/plants/101`

**What you'll get back:**

When successful, you won't see any response content - the plant is simply removed. You'll receive a confirmation status indicating the deletion was successful.

**If something goes wrong:**

You'll receive an error message if:
- The plant doesn't exist
- You don't have permission to delete it
- The ID format is incorrect

### Receive Notifications

**What it does:** Automatically notifies you when someone adds a new plant to the system.

**How it works:** 

When a new plant is created, the system will automatically send information about it to a web address you've registered. This is called a "webhook" - it's like setting up a doorbell that rings whenever something happens.

**What information you'll receive:**

The notification includes all details about the new plant:
- **id**: The plant's unique identification number
- **name**: The plant's name
- **tag**: The plant's category or type (if provided)

**Example notification:**
```json
{
  "id": 104,
  "name": "Spider Plant",
  "tag": "hanging"
}
```

**What you need to do:**

Your system needs to:
1. Accept the incoming notification
2. Process the information as needed
3. Send back a confirmation response to acknowledge receipt

## Understanding Responses

### Success Responses

**Viewing Plants:**
- You'll receive a list of plant objects
- Each plant shows its name and optional tag

**Adding a Plant:**
- You'll receive the newly created plant's details
- This confirms the plant was successfully added

**Removing a Plant:**
- You won't receive any content
- An empty response means the deletion was successful

**Webhook Notifications:**
- Your system should respond with a confirmation
- This tells the API you received the notification

### Error Responses

When something goes wrong, you'll receive an error message containing:
- **error**: A number identifying the type of error
- **message**: A clear explanation of what went wrong

**Common errors:**
- Authentication problems (invalid or missing token)
- Invalid data format (missing required information)
- Resource not found (trying to access or delete a plant that doesn't exist)
- Duplicate data (trying to create a plant with an ID that already exists)

## Data Requirements

### Plant Information

Every plant in the system has:
- **name** (required): The plant's name - can be any text
- **tag** (optional): A category or type - can be any text

### New Plant Information

When creating a plant, you must provide:
- **id** (required): A unique number to identify the plant
- **name** (required): The plant's name
- **tag** (optional): A category or type for the plant

### Error Information

Error messages always include:
- **error** (always present): A number indicating the error type
- **message** (always present): Text explaining what happened

## Best Practices

### Managing Your Token

- Keep your access token private and secure
- Never share your token publicly
- Store it in a safe place where only authorized users can access it

### Making Requests Efficiently

- Use the limit setting when viewing plants to avoid loading more data than needed
- Only request information when you actually need it
- If you're viewing the same information repeatedly, consider storing it temporarily

### Handling Errors

- Always check for error responses after making requests
- Read error messages carefully - they explain what needs to be fixed
- If you receive errors repeatedly, verify your token is correct and you're sending the right information

### Working with Webhooks

- Make sure your notification receiver responds quickly
- Always send back a confirmation response
- Store or process the notification data as needed for your application
- Test your webhook receiver before registering it

## Common Scenarios

### Viewing a Limited Number of Plants

If you have many plants but only want to see a few at a time:
1. Add the limit parameter to your request
2. Set it to the number of plants you want to see
3. For example, to see 20 plants, request `/plants?limit=20`

### Adding Multiple Plants

To add several plants:
1. Add each plant one at a time using separate requests
2. Make sure each plant has a unique ID number
3. Wait for each creation to complete before adding the next

### Finding Out When Plants Are Added

To be notified automatically when plants are created:
1. Set up a web address that can receive notifications
2. Register this address with the API service
3. Your system will receive a message every time someone adds a plant

### Recovering from Errors

If you receive an error:
1. Read the error message to understand what went wrong
2. Fix the issue (check your token, verify your data, etc.)
3. Try the request again
4. If errors continue, contact support for assistance