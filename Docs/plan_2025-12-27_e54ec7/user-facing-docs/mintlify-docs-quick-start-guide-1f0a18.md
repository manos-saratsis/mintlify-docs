# Quick Start Guide

Welcome! This guide will help you get your documentation site up and running in just a few minutes. Follow these simple steps to create, customize, and publish beautiful documentation.

## What You'll Need

Before you begin:
- A GitHub account (free to create at github.com)
- About 5-10 minutes
- Node.js installed on your computer (version 19 or higher)

## Step 1: Create Your Documentation Site

### Get Your Template

First, you'll get your own copy of the documentation starter:

1. Go to the GitHub repository with the starter template
2. Click the green **"Use this template"** button at the top
3. Name your new repository
4. Click "Create repository"

You now have your own documentation site with example pages and structure already set up!

### What's Inside

Your new documentation includes:
- Example guide pages you can edit
- A navigation menu ready to customize
- Sample API documentation
- Pre-configured styling and layout

## Step 2: Preview on Your Computer

See your documentation live as you make changes.

### Install the Preview Tool

Open your terminal or command prompt and type:

```
npm i -g mint
```

This installs a helper tool that lets you see your documentation locally.

### Start the Preview

1. Open your terminal
2. Navigate to the folder where you saved your documentation (look for the `docs.json` file)
3. Type:
   ```
   mint dev
   ```
4. Open your web browser and go to `http://localhost:3000`

Your documentation is now running! Any changes you make to files will automatically show up in your browser.

<Tip>
**Using a different port:** If port 3000 is busy, you can use a custom port by typing `mint dev --port 3333` (or any port number you prefer).
</Tip>

## Step 3: Make It Yours

### Add Your Branding

Open the `docs.json` file in your editor to personalize your site:

**Update the Name:**
Find the `"name"` field and change it to your project name. This appears in browser tabs and the navigation.

**Change Colors:**
Find the `"colors"` section and update:
- `"primary"`: Your main brand color (in hex format like `#16A34A`)
- `"light"`: A lighter accent color
- `"dark"`: A darker shade for important elements

**Add Your Logo:**
1. Create a `logo` folder in your project
2. Add two logo files:
   - `light.svg` - Your logo for light mode
   - `dark.svg` - Your logo for dark mode
3. The correct logo will automatically display based on the viewer's theme

**Example:**
```json
{
  "name": "My Project",
  "colors": {
    "primary": "#16A34A",
    "light": "#07C983",
    "dark": "#15803D"
  },
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg"
  }
}
```

### Customize Your Navigation

Your navigation menu is also in `docs.json`. You'll see tabs and groups like:
- Guides
- Getting Started
- API Reference

To add a new page to the menu, add its filename (without the `.mdx` extension) to the appropriate `"pages"` list.

**Example:**
```json
"pages": ["quickstart", "your-new-page"]
```

### Create and Edit Pages

All documentation pages are files ending in `.mdx` (markdown format). To write content:

**Common Formatting:**
- `# Large Heading` - Main page title
- `## Section Heading` - Section headers
- `**bold text**` - Make text bold
- `[link text](url)` - Create links
- `` `code` `` - Show inline code

You can edit the example pages or create new ones by adding new `.mdx` files.

## Step 4: Go Live

Once you're happy with your documentation, it's time to publish it online.

### Connect to Your Dashboard

1. Visit your dashboard at `https://dashboard.mintlify.com/settings/organization/github-app`
2. Click to install the GitHub integration
3. Select the repository containing your documentation
4. Authorize the connection

### Publish Your Changes

From now on, publishing is automatic:

1. Make changes to your documentation files
2. Save your work
3. Push your changes to GitHub (to the main branch)
4. Your live documentation updates automatically in moments

No manual deployment needed—it just happens!

## Quick Wins

Here are some fast wins to get started:

**Add a New Page:**
1. Create a new file like `my-page.mdx`
2. Add basic content with a title: `# My New Page`
3. Add it to `docs.json` in the navigation
4. Save and refresh your preview to see it

**Customize Your Homepage:**
Edit the `index.mdx` file to introduce your project and what users can do.

**Try Dark Mode:**
Click the mode toggle (moon/sun icon) to see how your documentation looks in both light and dark themes.

## Need Help?

**Preview Not Starting?**
Run `mint update` in your terminal to get the latest version, then try `mint dev` again.

**Seeing a 404 Error?**
Make sure you're in the correct folder—the one containing `docs.json`. You can check by listing files in your current directory.

**Page Not Showing in Navigation?**
Double-check that you added the page filename to the `"pages"` list in `docs.json`.

**How Do I Add Images?**
Create an `images` folder, add your image files there, then reference them in your pages using `![description](/images/your-image.png)`.

## What's Next

Now that you're set up:

1. **Explore the Examples** - Look through the sample pages to see what's possible
2. **Edit Your First Page** - Replace example content with information about your project
3. **Add More Content** - Create additional pages as needed
4. **Customize Further** - Adjust colors, fonts, and layout to match your brand
5. **Share Your Docs** - Once published, share the link with your users

Your documentation will grow with your project. You can always add new pages, update content, and refine the design. Changes go live automatically when you push to GitHub.

Welcome to great documentation—you're all set! 🚀