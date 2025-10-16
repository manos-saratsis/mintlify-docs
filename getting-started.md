# Getting Started

Welcome! This guide will help you create beautiful, professional documentation for your project in just a few minutes. Whether you're documenting an API, writing user guides, or creating developer documentation, you'll have everything you need to get started.

## What You Can Do

With this platform, you can:
- Create a modern documentation website that's fast and easy to search
- Share guides and tutorials with your users
- Document your APIs automatically
- Customize the look and feel to match your brand
- Publish your documentation with automatic updates

## What You'll Need

Before you begin, make sure you have:
- A GitHub account (it's free if you don't have one)
- About 10 minutes to set everything up
- Your project or content that needs documentation

## Step 1: Get Your Documentation Started

### Create Your Documentation Project

First, you'll get your own copy of the documentation template:

1. Visit the starter repository on GitHub
2. Look for the green **"Use this template"** button near the top
3. Click it to create your own copy
4. Give your new repository a name

That's it! You now have all the example pages and structure you need to get started.

### What's Included

Your new documentation comes with helpful examples:
- **Guide Pages**: Ready-to-use templates for step-by-step instructions
- **Navigation Structure**: An organized menu you can customize
- **API Reference**: Templates for documenting your APIs
- **Customization Options**: Easy ways to add your branding

## Step 2: Preview Your Documentation Locally

To see your documentation on your own computer as you work on it, you'll install a preview tool.

### Install the Preview Tool

Open your terminal or command prompt and type:

```
npm i -g mint
```

This installs a small helper program that lets you preview your documentation.

### See Your Documentation Live

Now you can see what your documentation looks like:

1. Open your terminal
2. Go to the folder where you saved your documentation (look for a file called `docs.json`)
3. Type this command:
   ```
   mint dev
   ```
4. Open your web browser and visit `http://localhost:3000`

You'll see your documentation running! When you make changes to your files, they'll appear right away in your browser.

## Step 3: Make It Your Own

### Add Your Branding

Open the file called `docs.json` to personalize your documentation:

**Change the Colors**:
The default colors are green, but you can use your brand colors. Look for the section that says `colors` and replace the color codes with your own:
- `primary`: Your main brand color
- `light`: A lighter version for accents
- `dark`: A darker version for emphasis

**Add Your Logo**:
1. Create a folder called `logo` in your project
2. Add two versions of your logo:
   - One for light mode (save it as `light.svg`)
   - One for dark mode (save it as `dark.svg`)
3. The documentation will automatically show the right logo based on what theme someone is using

**Update the Site Name**:
Change the `name` field to match your project's name. This appears in the browser tab and navigation.

### Organize Your Content

The navigation menu is also in the `docs.json` file. You'll see sections like:
- Getting Started
- Customization
- Writing Content
- API Reference

You can:
- Add new sections by copying the pattern you see
- Remove sections you don't need
- Rearrange sections in any order
- Rename sections to match your needs

### Write Your Content

All your documentation pages are written in simple text files ending in `.md`. These use Markdown, which is easy to learn:
- `# Heading` creates a large heading
- `## Smaller Heading` creates a subheading
- `**bold text**` makes text bold
- `[link text](url)` creates a link
- `` `code` `` shows code

You can:
- Edit the example pages to match your content
- Create new pages by adding new `.md` files
- Add images, code examples, and more

## Step 4: Publish Your Documentation

When you're ready to share your documentation with the world, you'll set up automatic publishing.

### Connect to the Dashboard

1. Visit `https://dashboard.mintlify.com/settings/organization/github-app`
2. Click to install the GitHub app
3. Choose which repository to connect (the one with your documentation)
4. Authorize the connection

### Automatic Updates

Once connected, your documentation updates automatically! Here's how it works:

1. You make changes to your documentation files
2. You save and push your changes to GitHub
3. Your live documentation updates automatically within minutes

No need to manually deploy or run commands—it just happens.

## Tips for Success

### Start Small
Don't try to write everything at once. Start with:
1. A simple homepage explaining what your project does
2. A quick start guide to help people get started
3. One or two detailed guides for common tasks

You can always add more pages later.

### Look at the Examples
The template includes example pages showing you:
- How to format text and create sections
- How to add code examples
- How to include images
- How to create tables and lists

Use these as inspiration for your own pages.

### Keep It Simple
Good documentation is clear and simple:
- Use short sentences
- Explain one thing at a time
- Include examples whenever possible
- Think about what someone new to your project would need to know

## Common Questions

**"The preview isn't starting. What should I do?"**

Type `mint update` in your terminal to get the latest version of the preview tool. This usually fixes the problem.

**"I'm seeing a 404 error when I try to preview."**

Make sure you're in the right folder—the one that has the `docs.json` file. You can check by typing `ls` (Mac/Linux) or `dir` (Windows) to see what's in the current folder.

**"How do I add a new page?"**

1. Create a new `.md` file with your content
2. Open `docs.json`
3. Find the navigation section where you want the page to appear
4. Add the filename (without `.md`) to the list of pages
5. Save both files

**"Can I include my API documentation?"**

Yes! If you have an OpenAPI specification (also called Swagger), you can include it in your project. The system will automatically create beautiful, interactive API documentation from it.

## Get Help

If you get stuck or have questions:

- **Documentation**: Visit the full documentation at `https://mintlify.com/docs` for detailed guides
- **Support**: Email `hi@mintlify.com` for help
- **Examples**: Look at the example pages included in your template

## What's Next

Now that you have the basics set up, here's what to do next:

1. **Explore the Examples**: Look through the sample pages to see what's possible
2. **Write Your First Page**: Replace one of the example pages with content about your project
3. **Customize the Design**: Update colors and logos to match your brand
4. **Add More Pages**: Create additional pages as you need them
5. **Go Live**: Connect to the dashboard and publish your documentation

Remember, your documentation is a living resource. You can update it anytime, and your changes will appear on your live site automatically. Take it one step at a time, and don't hesitate to look at the examples or reach out for help.

Welcome to creating great documentation—you've got this! 🚀