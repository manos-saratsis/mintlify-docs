# API Reference Documentation

Welcome to the Plant Store API documentation. This guide will help you understand how to work with our plant management system to view, add, and manage plants in your store.

## Getting Started

The Plant Store API lets you manage your plant inventory through simple web requests. Whether you want to see what plants are available, add new ones to your catalog, or remove plants that are out of stock, this API makes it straightforward.

### What You Need

Before you start using the API, make sure you have:

1. **Your Access Key**: You'll receive a special access token that proves you're authorized to use the API. Keep this safe and don't share it with anyone.
2. **Internet Connection**: The API is available online at `http://sandbox.mintlify.com`
3. **A Way to Make Web Requests**: You can use tools like your web browser, command-line tools, or programming languages

### Proving Your Identity

Every time you interact with the API, you need to include your access key. Think of it like showing your membership card at a store - it confirms you're allowed to access the system.

You'll include this key in something called a "header" with each request. Don't worry if that sounds technical - the examples below will show you exactly how to do it.

## Viewing Your Plants

### See All Plants in Your Store

This lets you get a list of all the plants you have access to in the system.

**How it works**: Send a request to `/plants` and you'll get back information about each plant.

**Controlling How Many Results You See**:

Sometimes you might have hundreds of plants in your system. Instead of getting overwhelmed with information, you can limit how many plants you see at once. For example, if you only want to see 10 plants at a time, you can specify that in your request.

**What You'll Get Back**:

When everything works correctly, you'll receive a list of plants. Each plant includes:
- **Name**: What the plant is called (like "Snake Plant" or "Fiddle Leaf Fig")
- **Tag**: A category that describes the plant type (like "succulent" or "indoor")

Here's what the information looks like:
```
Fiddle Leaf Fig (indoor)
Snake Plant (succulent)
Monstera Deliciosa (tropical)
```

**If Something Goes Wrong**:

If there's a problem with your request (like using an incorrect access key or asking for an invalid number of plants), you'll get an error message explaining what went wrong. The message will include:
- An error number that identifies the type of problem
- A description explaining what happened

For example, if you tried to limit results with an invalid number, you might see: "Invalid limit parameter"

## Adding New Plants

### Add a Plant to Your Store

When you get new plants in stock, you can add them to your system so they appear in your inventory.

**What You Need to Provide**:

For each new plant, you must tell the system:
- **Identification Number**: A unique number for this plant (no two plants can have the same number)
- **Name**: What you want to call the plant
- **Tag** (optional): A category or type for organizing your plants

**How to Add a Plant**:

Send the plant information to `/plants` and the system will create it in your inventory. The identification number must be unique - if you try to add a plant with a number that's already in use, you'll get an error.

Here's an example of adding a new plant called "Peace Lily" with the category "flowering":
```
Identification Number: 101
Name: Peace Lily
Tag: flowering
```

**What Happens Next**:

When the plant is successfully added, you'll receive confirmation with all the plant details you provided. This confirms the plant is now in your system and available in searches.

**If Something Goes Wrong**:

If there's a problem (like trying to use an identification number that already exists), you'll get an error message explaining the issue. For example: "Plant with ID 101 already exists"

## Removing Plants

### Delete a Plant from Your Store

When a plant is no longer available or you need to remove it from your inventory, you can delete it from the system.

**What You Need**:

You'll need to know the plant's identification number - the unique number that was assigned when the plant was first added to the system.

**How to Remove a Plant**:

Specify which plant to delete by including its identification number in your request to `/plants/{id}` (where `{id}` is the actual number).

For example, to remove plant number 101, you would reference `/plants/101` in your request.

**What Happens Next**:

When a plant is successfully deleted, you'll receive confirmation that the removal is complete. The plant will no longer appear in your inventory.

**Important Things to Know**:

- **This Action is Permanent**: Once you delete a plant, it's gone from the system completely. There's no "undo" button.
- **Double-Check Before Deleting**: Make sure you have the right identification number before removing a plant.
- **Already Deleted Plants**: If you try to delete a plant that's already been removed, you'll still get a success message (the system doesn't treat this as an error).

**If Something Goes Wrong**:

If there's a problem with the deletion (like the plant doesn't exist), you'll get an error message. For example: "Plant with ID 101 not found"

## Getting Automatic Updates

### How the System Can Notify You

Instead of constantly checking if new plants have been added, you can set up automatic notifications. This way, the system will send you a message whenever someone adds a new plant to the store.

**How It Works**:

You provide the system with a web address (URL) where you want to receive notifications. Whenever a new plant is added anywhere in the system, the API will automatically send that plant's information to your address.

**What You'll Receive**:

Each notification includes the complete details of the newly added plant:
- The identification number
- The plant name
- The plant tag (if one was provided)

For example, if someone adds a "Rubber Plant" with ID 102 and tag "indoor", you'll receive all that information automatically.

**Setting This Up**:

Your notification address needs to be accessible over the internet and able to receive information. When it gets a notification, it should respond with a success message to confirm the notification was received. This helps ensure no notifications get lost.

## Understanding the Results You Get

### When Things Work Correctly

When your requests succeed, you'll receive the information you asked for in a consistent, organized format. This makes it easy to use the information in your applications or processes.

The format is designed to be easy to read and work with, whether you're looking at it yourself or having a computer program process it.

### When There Are Problems

Sometimes things don't work as expected. When that happens, you'll receive an error message that helps you understand and fix the problem.

Every error includes:
- **A Number**: Identifies what type of error occurred
- **A Description**: Explains in plain language what went wrong

**Common Problems and What They Mean**:

- **Authentication Issues**: Your access key might be missing, incorrect, or expired. Solution: Check that you're including the correct key with your request.

- **Plant Not Found**: You're trying to access or delete a plant that doesn't exist. Solution: Verify the identification number is correct.

- **Invalid Information**: The information you provided doesn't meet the requirements. Solution: Check that all required fields are included and properly formatted.

- **Duplicate Plant**: You're trying to add a plant with an identification number that's already in use. Solution: Use a different identification number.

## Plant Information Structure

### Basic Plant Details

Every plant in the system has certain properties. Some are required (you must provide them), while others are optional (you can include them if you want).

**Required Information**:
- **Name**: Every plant must have a name. You can't create a plant without one.

**Optional Information**:
- **Tag**: A category or classification for the plant. This helps organize your plants but isn't required.

### Complete Plant Records

When you work with plants in the system (creating them, viewing them, or updating them), you'll see these complete records that include:

- **Identification Number**: The unique number assigned to this plant
- **Name**: What the plant is called
- **Tag**: The plant's category (if one was provided)

The identification number is automatically assigned when you create a plant and can't be changed afterward. You'll use this number whenever you need to reference the specific plant later (like when deleting it).

### Error Information

When errors occur, you'll receive structured information about what went wrong:

- **Error Number**: A code that identifies the specific type of error
- **Description**: An explanation of what happened

These error codes follow standard conventions, making it easier to handle them in your applications and systems.

## Tips for Using the API Effectively

### Making Your Requests Efficient

1. **Limit Your Results**: When getting plant lists, only request the number of plants you actually need. This makes responses faster and easier to work with.

2. **Handle Errors Appropriately**: Always check for and handle error messages. If something goes wrong, explain the problem clearly and tell users what they can do to fix it.

3. **Keep Your Access Key Secure**: Treat your access key like a password. Never share it publicly or include it in places where others can see it.

4. **Use Automatic Notifications**: Instead of repeatedly checking for new plants, set up the webhook system to be notified immediately when plants are added.

### Keeping Things Running Smoothly

- **Request Only What You Need**: Don't ask for more information than necessary. This keeps things fast for everyone.

- **Save Information When Appropriate**: If certain plant information doesn't change often, you can save it rather than requesting it repeatedly.

- **Spread Out Your Requests**: If you need to make many requests, space them out rather than sending them all at once.

- **Monitor Your Usage**: Keep track of how much you're using the system to avoid exceeding any limits.

## Need Help?

### Finding Solutions

1. **Check Error Messages**: When something goes wrong, the error message often tells you exactly what needs to be fixed.

2. **Review the Examples**: Look at the example requests and responses in this documentation to see how things should work.

3. **Verify Your Access**: Make sure your access key is valid and included correctly in your requests.

4. **Get Support**: If you're stuck on a complex issue, reach out to the support team at hi@mintlify.com for help.

This API documentation provides everything you need to manage your plant inventory effectively. Whether you're building an application, managing a website, or setting up automated systems, these tools will help you keep your plant catalog organized and up-to-date.