# Plant Store API Overview

## What is the Plant Store API?

The Plant Store API is a simple, easy-to-use service that helps you manage plant inventory. Think of it as a digital catalog where you can view all your plants, add new ones, and remove plants you no longer have. The API also lets you know automatically when new plants are added, so your systems stay up-to-date without you having to check constantly.

## What Can You Do?

With the Plant Store API, you can:

- **Browse Your Plant Collection**: See a list of all plants in your store
- **Filter Results**: Choose how many plants to see at once (helpful when you have many plants)
- **Add New Plants**: Register new plants when they arrive at your store
- **Remove Plants**: Delete plants when they're sold or no longer available
- **Get Real-Time Updates**: Receive automatic notifications when new plants are added

## Getting Started

Before you can use the Plant Store API, you'll need an access token. This is like a special key that proves you're authorized to view and manage the plant inventory. Once you have your token, you'll include it with every request to the API.

The API is available at: `http://sandbox.mintlify.com`

## How Information is Organized

### Plant Details

Every plant in the system has these properties:

- **Name**: What the plant is called (required)
- **Tag**: A category or type label (optional) - like "indoor", "succulent", or "tropical"

### New Plant Registration

When adding a new plant, you need to provide:

- **ID Number**: A unique identification number for the plant
- **Name**: What to call the plant
- **Tag**: An optional category label

### Error Messages

If something goes wrong, you'll receive a message explaining what happened. Error messages include:

- **Error Code**: A number indicating what type of problem occurred
- **Message**: A clear explanation in plain English

## Available Actions

### Viewing Your Plants

You can request a list of all plants you have access to. The system will send back information about each plant, including its name and category tag. If you have many plants, you can limit how many results you receive at once - for example, requesting only the first 10 or 25 plants.

**Example**: Request all plants or just the first 20 to keep the response manageable.

### Adding a New Plant

When you receive a new plant, you can register it in the system. You'll provide:
- A unique ID number
- The plant's name
- An optional category tag

The system will confirm that your plant was added successfully by sending back the plant's details.

**Example**: Add a "Peace Lily" with category "flowering" and ID number 101.

### Removing a Plant

When a plant is sold or no longer available, you can remove it from the system by providing its ID number. The system will confirm the deletion was successful.

**Example**: Remove the plant with ID number 101.

### Getting Automatic Updates

Instead of constantly checking for new plants, you can set up automatic notifications. Whenever someone adds a new plant to the system, the API will send the plant's information directly to your specified web address. This way, your inventory stays current without manual checking.

## How Results are Delivered

All information is sent in a structured format called JSON. This makes it easy for computer programs to read and process the data.

**Success Responses**: When things work correctly, you'll receive the requested information (like a list of plants or confirmation of an action).

**Error Responses**: If there's a problem (like trying to add a plant with a duplicate ID), you'll receive a message explaining what went wrong and how to fix it.

## Response Types

### Successful Requests

- **List Retrieved**: You'll get an array of plants with their names and tags
- **Plant Added**: You'll receive the details of the newly created plant
- **Plant Removed**: You'll get confirmation that the deletion worked (with no additional data)

### Error Situations

- **Invalid Request**: When the information you provide doesn't meet requirements
- **Duplicate Entry**: When trying to add a plant with an ID that already exists
- **Not Found**: When trying to delete a plant that doesn't exist
- **Authentication Error**: When your access token is missing or invalid

## Common Use Cases

### Store Management
Perfect for plant stores managing their inventory. View what's in stock, add new arrivals, and remove sold items.

### Inventory Tracking
Keep real-time tabs on plant availability across multiple locations or systems.

### Automated Systems
Set up automatic notifications so your website, mobile app, or warehouse system knows immediately when new plants arrive.

### Reporting and Analytics
Pull plant data to create reports on inventory levels, popular categories, or stock trends.

## Best Practices

### Keep Requests Efficient
- Request only the data you need using the limit parameter
- Don't repeatedly request the same information - save it temporarily if you'll use it multiple times

### Handle Errors Gracefully
- Always check if your request was successful before proceeding
- Read error messages carefully - they tell you exactly what to fix
- If you get an error, don't immediately retry - understand and fix the issue first

### Secure Your Access Token
- Never share your access token publicly
- Store it securely and don't include it in public code
- If you suspect your token is compromised, request a new one immediately

### Set Up Notifications Wisely
- Use webhooks for real-time updates instead of constantly checking for changes
- Make sure your notification receiver responds quickly to avoid timeouts
- Always acknowledge received notifications with a success response

## When Things Go Wrong

### Can't Access the API
Double-check that your access token is included correctly in your requests and hasn't expired.

### Getting Error Messages
Read the error message carefully - it explains exactly what's wrong. Common issues include:
- Missing required information (like plant name or ID)
- Trying to add a plant with an ID that already exists
- Trying to delete a plant that doesn't exist

### Not Receiving Notifications
Verify that your notification web address is accessible from the internet and responds promptly with a success message.

### Results Don't Look Right
Make sure you're requesting the correct information and interpreting the response format properly. Plant data comes as an array (list) while single plant operations return individual objects.

## Privacy and Data

Your access token controls what plant data you can see and modify. You can only access plants associated with your account. All data transfers are handled securely, and your token acts as your identity verification for every request.

## Getting Help

If you encounter issues not covered here or need clarification on how something works, check the detailed API documentation for technical specifics, code examples, and endpoint details. The documentation includes step-by-step examples in multiple programming languages.