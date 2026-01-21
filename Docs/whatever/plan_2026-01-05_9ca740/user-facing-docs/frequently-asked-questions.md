# Frequently Asked Questions

## Getting Started

### How do I start using this documentation template?

Click the green **Use this template** button at the top of the repository to create your own copy. This will give you a starter kit with example pages, navigation setup, customizations, and API reference examples that you can modify for your own project.

### What do I need to have installed before I begin?

You'll need Node.js and npm installed on your computer. Once you have these, you can install the Mintlify CLI tool using the command `npm i -g mint`. This tool allows you to preview your documentation on your local computer before publishing.

### How do I preview my documentation while I'm working on it?

After installing the Mintlify CLI, navigate to your documentation folder (where your main configuration file is located) and run `mint dev`. Your documentation will be available to view in your web browser at `http://localhost:3000`. Any changes you make will be reflected in real-time.

## Publishing & Deployment

### How do I publish my documentation online?

First, install the Mintlify GitHub app from your dashboard settings. Once connected, any changes you push to your default branch (usually "main" or "master") will automatically be deployed to production. There's no manual deployment step required.

### Do I need to manually deploy updates?

No. After you've connected the GitHub app to your repository, all changes pushed to your default branch are automatically deployed to production. This means your documentation stays up-to-date without any extra steps.

### Can I test changes before they go live?

Yes. Use the local preview feature by running `mint dev` on your computer. This lets you see exactly how your documentation will look before you push any changes to your repository.

## Troubleshooting

### My preview isn't loading - what should I do?

First, make sure you're running the preview command from the correct folder - the one that contains your main configuration file (docs.json). If you're in the right location and it still doesn't work, run `mint update` to ensure you have the latest version of the CLI tool installed.

### I'm getting a 404 error when trying to view a page

This usually means you're not running the preview from the correct folder. Make sure you're in the directory that contains your docs.json configuration file when you run the `mint dev` command.

### My local environment stopped working after it was previously running fine

Run `mint update` to get the most recent version of the CLI. Updates often include bug fixes and improvements that resolve common issues.

### Where can I find help if I'm still stuck?

Visit the official Mintlify documentation at mintlify.com/docs for comprehensive guides, tutorials, and troubleshooting resources.

## Customization

### What comes included in the starter kit?

The starter kit includes:
- Example guide pages to show you how to structure content
- Pre-configured navigation setup
- Sample customizations you can adapt
- API reference page examples
- Examples of popular components you can use

### Can I customize the look and feel of my documentation?

Yes. The starter kit includes examples of various customizations. You can modify colors, layouts, navigation structure, and add your own branding to match your product or company style.

### How do I add new pages to my documentation?

You can create new markdown files and add them to your navigation configuration. The starter kit includes examples of different page types (guides, API references, etc.) that you can use as templates for your own content.

## Best Practices

### What's the best way to organize my documentation?

Start by exploring the examples included in the starter kit. These demonstrate proven patterns for organizing guides, API references, and other content types. Use these as a foundation and adapt them to your specific needs.

### Should I modify the example content or start from scratch?

It's recommended to modify the existing examples rather than starting from scratch. The examples demonstrate best practices for structure, formatting, and component usage. Simply replace the example content with your own while keeping the proven structure.

### How often should I update my documentation?

Update your documentation whenever you make changes to your product or receive user feedback about unclear sections. Since deployment is automatic, there's no overhead to making frequent small updates rather than batching changes.

## Integration & Setup

### Do I need a Mintlify account?

Yes, you'll need access to the Mintlify dashboard to install the GitHub app and manage your documentation deployment settings.

### Can I use this with private repositories?

Yes. The Mintlify GitHub app can be connected to both public and private repositories. Configure access through your dashboard settings.

### What file format should I use for my documentation?

Documentation pages are written in Markdown format (.md files), which uses simple text formatting that's easy to write and read. The starter kit includes many examples showing how to format your content.