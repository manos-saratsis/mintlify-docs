# Quick Start Guide

Welcome! This guide will get you up and running with your documentation site in just a few minutes. Follow these three simple steps to create, preview, and publish beautiful documentation.

## What You'll Need

Before you begin, make sure you have:
- A GitHub account (create one for free at github.com if needed)
- Node.js version 19 or higher installed on your computer
- About 10 minutes

## Step 1: Set Up Your Documentation

### Get Your Own Copy

First, you'll create your own documentation project:

1. Visit the starter repository on GitHub
2. Look for the green **"Use this template"** button at the top of the page
3. Click it to create your own copy
4. Give your new repository a name (like "my-docs" or "company-docs")
5. Click "Create repository"

Congratulations! You now have a complete documentation site with example pages ready to customize.

### Get It On Your Computer

To work on your documentation locally:

1. Visit your dashboard at `https://dashboard.mintlify.com` to find your repository link
2. Follow GitHub's guide to clone your repository to your computer
3. Open a terminal or command prompt
4. Navigate to the folder where you saved your documentation

You're ready to start previewing and editing!

## Step 2: See Your Documentation Live

### Install the Preview Tool

Open your terminal and type:

```
npm i -g mint
```

This installs a small helper program that lets you preview your documentation on your computer.

### Start the Preview

In your terminal, navigate to your documentation folder (where you'll find a file called `docs.json`) and run:

```
mint dev
```

Then open your web browser and visit `http://localhost:3000`

You'll see your documentation site running live! Any changes you make to your files will automatically appear in your browser—no need to refresh.

**Using a different port**: If you need to use a different port (for example, if 3000 is already in use), you can specify one like this:

```
mint dev --port 3333
```

If your chosen port is busy, the system will automatically try the next available port.

## Step 3: Make It Yours and Publish

### Quick Customization

Let's make your first change to personalize your site:

1. Open the `docs.json` file in your text editor
2. Find the `"name"` field and change it to your project's name
3. Update the `"colors"` section to match your brand:
   - `"primary"`: Your main brand color (in hex format, like `#16A34A`)
   - `"light"`: A lighter shade for accents
   - `"dark"`: A darker shade for emphasis
4. Save the file

Look at your browser—your changes appear instantly at `http://localhost:3000`!

### Publish Your Documentation

Now let's get your documentation online:

1. Go to your dashboard at `https://dashboard.mintlify.com/settings/organization/github-app`
2. Click to install the GitHub app
3. Connect it to the repository containing your documentation
4. Authorize the connection

Once connected, publishing is automatic:

1. Make changes to your documentation files
2. Save and commit your changes
3. Push them to GitHub
4. Your live documentation updates automatically in moments

No manual deployment needed—just commit and push, and your changes go live!

## What's Next

Now that you have your documentation running, here's what you can explore:

**Add Your Content**: Edit the example pages or create new ones using simple Markdown formatting. Your pages are just text files ending in `.md` or `.mdx`.

**Organize Your Navigation**: Update the `docs.json` file to arrange pages in the order that makes sense for your users. You can add sections, rearrange pages, and create multiple tabs.

**Add Your Logo**: Create a `logo` folder and add your logo images (one for light mode, one for dark mode). The site will automatically display the right one based on the user's theme preference.

**Explore Advanced Features**: Check out code examples, images, reusable snippets, and API documentation features when you're ready.

## Common Issues

**Preview not starting?** Run `mint update` in your terminal to get the latest version of the preview tool.

**Seeing a 404 error?** Make sure you're in the correct folder—the one with the `docs.json` file. You can check by typing `ls` (Mac/Linux) or `dir` (Windows) to see what files are in your current location.

**Changes not showing?** Your preview should update automatically. If it doesn't, try stopping the preview (press Ctrl+C) and running `mint dev` again.

**Need to check for broken links?** Run `mint broken-links` to scan your documentation for any broken links.

## Get Help

Need assistance? Here are your options:

- **Visit the full documentation** at `https://mintlify.com/docs` for detailed guides
- **Email support** at `hi@mintlify.com` for help
- **Check the examples** included in your template to see what's possible

You're all set! Start by editing a few pages, preview your changes, and push them live. Your documentation is now a living resource that you can update anytime. Happy documenting! 🚀