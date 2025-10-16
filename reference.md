# API Reference Documentation

Welcome to the Plant Store API documentation. This guide helps you understand how to interact with our plant management system to retrieve, create, and manage plant information.

## Getting Started with the API

The Plant Store API allows you to manage a catalog of plants through simple web requests. You can view all available plants, add new plants to the store, or remove plants that are no longer available. All interactions happen through standard web addresses (URLs) that you can access from any application or programming language.

### What You'll Need

Before you can use the API, you'll need:

1. **Access Credentials**: You'll receive a special access key (called a bearer token) that proves you're authorized to use the API
2. **Basic Understanding**: Familiarity with making web requests (don't worry - we'll show you examples)
3. **API Address**: All requests go to `http://sandbox.mintlify.com`

### Authentication - Proving Who You Are

Every request you make to the API needs to include your special access key. Think of it like showing your ID card when entering a building - it proves you're allowed to be there.

When making requests, you'll include your access key in the request headers. The API uses "bearer authentication," which is a secure and widely-used method for verifying your identity.

## Working with Plants

### Viewing All Plants

**What it does**: Retrieves a list of all plants in the store that you have permission to see.

**How to use it**: Send a request to `/plants` and you'll receive back a list of plants with all their details.

**Controlling Results**: You can limit how many plants you see at once by specifying a maximum number. This is helpful when you have hundreds or thousands of plants and only want to see a manageable amount at a time.

For example, if you only want to see the first 10 plants, you can specify that limit in your request. This helps keep responses quick and manageable.

**What you get back**:
- **Success**: You'll receive a list of plants, each with their name and type classification
- **Error**: If something goes wrong (like using an invalid access key), you'll receive an error message explaining what happened

Each plant in the list includes:
- **Name**: The plant's common or scientific name
- **Tag**: A classification that describes what type of plant it is

### Adding a New Plant

**What it does**: Adds a brand new plant to the store catalog.

**How to use it**: Send the new plant's information to `/plants` and the system will create it in the database.

**Required Information**:
You must provide certain details about the plant:
- **Identification Number**: A unique number that identifies this specific plant
- **Name**: What the plant is called
- **Tag** (optional): A classification or category for the plant

**What you get back**:
- **Success**: You'll receive confirmation that the plant was created, along with all the details you provided
- **Error**: If something goes wrong (like trying to add a duplicate plant or providing invalid information), you'll get an error message explaining the problem

### Removing a Plant

**What it does**: Permanently removes a plant from the store catalog.

**How to use it**: Specify which plant to remove by providing its identification number in the web address.

**Required Information**:
- **Plant ID**: The unique identification number of the plant you want to remove

**What you get back**:
- **Success**: The plant is deleted and you'll receive confirmation
- **Error**: If the plant doesn't exist or something goes wrong, you'll get an error message

**Important**: This action cannot be undone. Once a plant is deleted, it's permanently removed from the system.

## Real-Time Updates with Webhooks

Webhooks are a way for the Plant Store API to notify your application automatically when something important happens. Instead of you constantly checking "has anything changed?", the API will send you a message when a new plant is added.

### New Plant Notifications

**What it does**: Sends you an automatic notification whenever someone adds a new plant to the store.

**How it works**: You provide the API with a web address (URL) where you want to receive notifications. When a new plant is added, the API will send the plant's information to that address.

**What you receive**: The complete details of the newly added plant, including its identification number, name, and tag.

**Important**: Your notification endpoint must respond with a success message to confirm you received the notification. This helps ensure no notifications get lost.

## Understanding Responses

### Success Responses

When everything works correctly, you'll receive the information you requested along with a success indicator. The format is structured and consistent, making it easy to process in your applications.

### Error Responses

When something goes wrong, you'll receive an error response that helps you understand and fix the problem. Every error includes:

- **Error Code**: A number that identifies the type of error
- **Message**: A human-readable explanation of what went wrong

Common reasons for errors:
- Using an invalid or expired access key
- Requesting a plant that doesn't exist
- Providing incomplete or invalid information when creating a plant
- Exceeding rate limits or usage quotas

## Data Structures

### Plant Information

Every plant in the system has these properties:

**Required Fields**:
- **Name** (text): The plant's name - this is always required

**Optional Fields**:
- **Tag** (text): A classification or category for organizing plants

### Complete Plant Record

When you retrieve or create a plant, you'll work with a complete record that includes:

**All plant properties plus**:
- **Identification Number** (number): A unique identifier assigned by the system

This identification number is generated automatically and cannot be changed. It's used to reference the plant in future operations like updates or deletions.

### Error Information

When errors occur, you'll receive a structured error response:

**Error Properties**:
- **Error Code** (number): Identifies the specific type of error
- **Message** (text): Explains what went wrong in plain language

Error codes follow standard conventions, making it easier to handle them programmatically in your applications.

## Best Practices

### Efficient API Usage

1. **Limit Results**: When retrieving plant lists, use the limit parameter to request only what you need. This makes responses faster and reduces unnecessary data transfer.

2. **Handle Errors Gracefully**: Always check for and handle error responses. Your application should explain problems clearly to users and provide actionable next steps.

3. **Secure Your Access Key**: Keep your bearer token private and secure. Never share it publicly or commit it to version control systems.

4. **Use Webhooks**: Instead of repeatedly checking for new plants, set up webhook notifications to be informed immediately when changes occur.

### Performance Tips

- Request only the data you need by using appropriate limits
- Cache plant information that doesn't change frequently
- Handle rate limits gracefully by spacing out requests
- Monitor your usage to stay within quota limits

## Need Help?

If you encounter issues or have questions:

1. **Check Error Messages**: Error responses often explain exactly what needs to be fixed
2. **Review Examples**: Look at the example requests and responses in this documentation
3. **Verify Authentication**: Ensure your access key is valid and properly included in requests
4. **Contact Support**: Reach out to the support team for assistance with complex issues

This API reference provides everything you need to integrate the Plant Store system into your applications, whether you're building a mobile app, website, or automated system for managing plant inventory.