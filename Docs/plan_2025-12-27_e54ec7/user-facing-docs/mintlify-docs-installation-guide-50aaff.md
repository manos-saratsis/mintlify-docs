# Getting Started with Your Documentation

Welcome! In just a few minutes, you'll have a beautiful documentation website up and running. This guide walks you through everything you need to get started, from creating your first documentation project to seeing it live on the web.

## What You'll Need

Before you begin, make sure you have:

- A GitHub account (free to create if you don't have one)
- About 10 minutes of your time
- Content you want to document

That's it! No special technical skills required.

## Create Your Documentation Project

The first step is getting your own documentation workspace set up.

### Get Your Template

1. Go to the documentation starter template on GitHub
2. Look for the green button labeled **"Use this template"** near the top of the page
3. Click it to make your own copy
4. Give your new project a name that makes sense for what you're documenting

Your new project comes with everything you need to get started, including example pages that show you how to create different types of content.

### What's Inside

Your documentation template includes:

- **Example Guide Pages**: Ready-to-edit templates showing you different writing styles
- **Navigation Structure**: An organized menu you can customize
- **API Documentation Templates**: If you need to document APIs
- **Customization Options**: Ways to add your branding and colors

## Preview Your Work Locally

Before publishing, you'll want to see what your documentation looks like as you work on it. This lets you make changes and see the results instantly.

### Install the Preview Tool

The preview tool is a small program that runs on your computer and shows you what your documentation will look like.

Open your command line or terminal and type:

```
npm i -g mint
```

This installs everything you need to preview your documentation.

**What You Need**: To run this command, you'll need Node.js version 19 or higher installed on your computer. If you don't have it, you can download it from the Node.js website.

### Start Previewing

Now you're ready to see your documentation:

1. Open your terminal or command line
2. Navigate to the folder where you saved your documentation (look for a file named `docs.json` - that's how you know you're in the right place)
3. Type this command:
   ```
   mint dev
   ```
4. Open your web browser and go to `http://localhost:3000`

Your documentation appears! As you make changes to your files, your browser will automatically update to show them. This makes it easy to see exactly how your edits will look.

### Using Different Ports

By default, the preview runs on port 3000. If you need to use a different port (maybe because something else is already using 3000), you can specify which one:

```
mint dev --port 3333
```

The preview tool is smart - if the port you want is already in use, it will automatically try the next available one and let you know.

## Customize Your Documentation

Now it's time to make your documentation your own. Everything you need to customize is in a file called `docs.json`.

### Change the Name

Open `docs.json` and look for the line that says `"name"`. Replace the existing name with your project's name. This name appears in the browser tab and throughout your documentation.

### Update the Colors

Your documentation can match your brand colors. In `docs.json`, find the `colors` section:

- **Primary color**: This is your main brand color, used for highlights and important elements
- **Light color**: A lighter accent color for additional highlights
- **Dark color**: A darker version used for buttons and emphasis

Replace the color codes (they look like `#16A34A`) with your own brand colors.

### Add Your Logo

To display your logo in the documentation:

1. Create a folder called `logo` in your project
2. Add two versions of your logo:
   - Save your logo for light backgrounds as `light.svg`
   - Save your logo for dark backgrounds as `dark.svg`
3. The system automatically shows the right version based on whether someone is using light or dark mode

### Set Up Your Navigation

The navigation menu helps people find what they need. In `docs.json`, you'll see a `navigation` section that lists all your pages and how they're organized.

You can:
- Add new sections by following the existing pattern
- Remove sections you don't need
- Rename sections to better describe your content
- Rearrange sections in any order

The structure uses tabs and groups to keep things organized. Each tab can contain multiple groups, and each group contains related pages.

## Write Your Content

Your documentation pages are written in simple text files ending in `.mdx` or `.md`. These use Markdown, an easy-to-learn format:

- Start a line with `#` for a main heading
- Use `##` for a subheading
- Put text between `**` to make it **bold**
- Create links like this: `[link text](web address)`
- Show code by putting it between backticks: `` `code here` ``

The template includes example pages showing you how to format different types of content. You can edit these examples or create new pages from scratch.

### Creating New Pages

To add a new page to your documentation:

1. Create a new `.mdx` file in your project
2. Write your content using Markdown formatting
3. Open `docs.json`
4. Find the navigation section where you want the page to appear
5. Add your filename (without the `.mdx` ending) to the list of pages
6. Save both files

Your new page will appear in the navigation menu.

## Publish Your Documentation

Once you're happy with how your documentation looks, it's time to share it with the world.

### Connect Your Project

1. Go to the dashboard at `https://dashboard.mintlify.com/settings/organization/github-app`
2. Click to install the GitHub app
3. Select the repository where your documentation lives
4. Authorize the connection

That's it! Your documentation is now connected.

### Automatic Publishing

Here's the best part: once connected, your documentation updates automatically whenever you make changes.

The workflow is simple:

1. Make changes to your documentation files
2. Save your changes and push them to GitHub
3. Your live documentation updates within minutes

No manual deployment steps, no commands to run. Just save and push.

### See Your Changes

After you push changes to GitHub, you'll see a confirmation that everything deployed successfully. Your documentation is now live and accessible to anyone with the link.

## Get the Most from Your Documentation

### Start Simple

Don't try to write everything at once. Begin with:

1. A homepage that explains what your project is about
2. A quick start guide showing the first steps
3. One or two detailed guides for common tasks

You can always add more later as you go.

### Learn from Examples

Your template includes examples showing you how to:
- Format text and create sections
- Add code examples with syntax highlighting
- Include images and diagrams
- Create tables and lists
- Use special components like tips and warnings

Browse these examples to see what's possible, then use them as inspiration for your own pages.

### Keep It Clear

The best documentation is simple and easy to follow:
- Use short sentences
- Explain one concept at a time
- Include examples whenever you can
- Think about what someone new to your project needs to know

## Common Questions

**The preview isn't starting - what should I do?**

Run `mint update` in your terminal. This updates the preview tool to the latest version, which usually fixes any issues.

**I see a 404 error when I try to preview**

Make sure you're in the right folder - the one containing the `docs.json` file. You can check by typing `ls` (on Mac/Linux) or `dir` (on Windows) to see what files are in your current location.

**How do I check for broken links?**

Run this command in your documentation folder:
```
mint broken-links
```

This scans your documentation and tells you if any links don't work.

**Can I change which port the preview uses?**

Yes! Use the `--port` flag when starting the preview:
```
mint dev --port 3333
```

Replace 3333 with whatever port number you prefer.

**What if I have an outdated version?**

Keep your preview tool up to date by running:
```
mint update
```

This ensures your local preview matches what people will see in production.

## Getting Help

If you run into any issues or have questions:

- Visit the full documentation at `https://mintlify.com/docs` for detailed guides
- Email support at `hi@mintlify.com`
- Check the example pages included in your template

## What's Next

Now that you have the basics down, here's what to do next:

1. **Browse the Examples**: Look through the sample pages to see different writing styles and features
2. **Write Your First Page**: Replace one of the example pages with real content about your project
3. **Customize the Look**: Update the colors and logo to match your brand
4. **Add More Content**: Create additional pages as you need them
5. **Share with Others**: Once everything looks good, share your documentation link

Remember, documentation is never "done" - it's a living resource that grows with your project. You can update it anytime, and your changes will go live automatically. Start with the basics, and build from there.

Welcome to creating great documentation! 🚀