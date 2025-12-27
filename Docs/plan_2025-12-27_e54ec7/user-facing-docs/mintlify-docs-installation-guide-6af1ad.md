# Getting Started with Your Documentation

Welcome! In just a few minutes, you'll have a professional documentation website up and running. This guide walks you through everything you need to get started—from your first setup to publishing your live documentation.

## What You'll Need

Before you begin:
- A GitHub account (free to create at github.com)
- About 10 minutes
- A computer with internet access

No technical experience required—we'll guide you through each step.

## Step 1: Get Your Documentation Template

First, you'll create your own copy of the documentation starter:

1. Visit the Mintlify starter repository on GitHub
2. Look for the green **"Use this template"** button at the top of the page
3. Click the button to create your own copy
4. Give your new documentation project a name
5. Click "Create repository from template"

That's it! You now have a complete documentation site with example pages, ready to customize.

### What's Inside

Your new documentation includes:
- Example guide pages showing you how to write documentation
- A pre-configured navigation menu
- Sample API documentation pages
- Customization examples
- All the structure you need to get started

## Step 2: Install the Preview Tool

To see your documentation on your computer as you work on it, you'll need to install a small helper tool.

**What You Need First:**
- Node.js version 19 or higher installed on your computer (download from nodejs.org if you don't have it)
- Your documentation files saved somewhere on your computer

### Install the Tool

Open your command line or terminal and type:

```
npm i -g mint
```

Press Enter. This installs the Mintlify preview tool on your computer.

### See Your Documentation Live

Now you can see what your documentation looks like:

1. Open your command line or terminal
2. Navigate to the folder where your documentation files are saved (look for a file named `docs.json`)
3. Type:
   ```
   mint dev
   ```
4. Press Enter
5. Open your web browser and go to `http://localhost:3000`

Your documentation appears! When you make changes to any file, your browser automatically updates to show them.

**Using a Different Port:**
If you need to use a different port number (for example, if port 3000 is already in use), add `--port` followed by your preferred number:

```
mint dev --port 3333
```

If the port you chose is already in use, the tool automatically tries the next available port.

## Step 3: Make It Your Own

Now comes the fun part—customizing your documentation to match your project.

### Change the Name and Colors

Open the file named `docs.json` in any text editor. This file controls how your documentation looks.

**Update the Site Name:**
Find the line that says `"name"` and change it to your project's name:
```json
"name": "Your Project Name"
```

**Change the Colors:**
Find the `"colors"` section. You can change three colors:
- `"primary"`: Your main brand color (used for highlights and accents in light mode)
- `"light"`: A lighter accent color (used in dark mode)
- `"dark"`: A darker color (used for important buttons)

Replace the color codes with your own. For example:
```json
"colors": {
  "primary": "#16A34A",
  "light": "#07C983",
  "dark": "#15803D"
}
```

Use any hex color codes that match your brand.

### Add Your Logo

To add your logo:

1. Create a folder named `logo` in your documentation project
2. Add two versions of your logo:
   - Save your light-mode logo as `light.svg`
   - Save your dark-mode logo as `dark.svg`
3. Make sure the paths in `docs.json` point to these files:
   ```json
   "logo": {
     "light": "/logo/light.svg",
     "dark": "/logo/dark.svg"
   }
   ```

Your documentation automatically shows the correct logo depending on whether someone is using light or dark mode.

### Customize the Icon

You can also change the small icon that appears in browser tabs:

1. Add your icon file to your project (name it something like `favicon.svg`)
2. Update the `favicon` line in `docs.json`:
   ```json
   "favicon": "/favicon.svg"
   ```

### Organize Your Pages

The navigation menu is also in the `docs.json` file. Under `"navigation"`, you'll see your pages organized into groups.

**To add a new page:**
1. Create your new page file (for example, `my-new-page.mdx`)
2. Find the group where you want it to appear in `docs.json`
3. Add the filename (without the file extension) to the `"pages"` list
4. Save the file

**To remove a page:**
Simply delete its filename from the `"pages"` list.

**To rename a group:**
Change the `"group"` name to whatever you want to appear in the navigation.

### Write Your Content

All your documentation pages are written in simple text files that end in `.mdx`. These files use Markdown, which is easy to learn:

- `# Heading` creates a large heading
- `## Smaller Heading` creates a subheading
- `**bold text**` makes text bold
- `*italic text*` makes text italic
- `[link text](url)` creates a clickable link
- `` `code` `` shows code
- Start a line with `-` to create a bullet point

You can edit any of the example pages or create new ones.

## Step 4: Connect Your Documentation for Publishing

Once you're happy with your documentation, you'll set it up so that changes you make automatically appear online.

### Install the Publishing Connection

1. Go to your dashboard at `https://dashboard.mintlify.com/settings/organization/github-app`
2. Click to install the Mintlify GitHub app
3. Choose your documentation repository (the one you created in Step 1)
4. Authorize the connection

That's all the setup you need!

### How Updates Work

From now on, your documentation updates automatically:

1. You make changes to your documentation files on your computer
2. You save your changes and push them to GitHub
3. Your live documentation updates automatically within minutes

No extra steps needed—it just happens.

## Step 5: Check Your Work

Before sharing your documentation with others:

**Check for Broken Links:**
Run this command to find any broken links in your documentation:
```
mint broken-links
```

If any links are broken, you'll see a list so you can fix them.

**Preview Your Changes:**
Always check your local preview at `http://localhost:3000` before publishing to make sure everything looks the way you want.

**Publish Your Changes:**
When you're ready:
1. Save all your files
2. Commit your changes to your repository
3. Push to GitHub
4. Your documentation goes live automatically

## Common Questions

**"The preview tool won't start. What should I do?"**

First, make sure you have Node.js version 19 or higher. You can check by typing `node --version` in your command line.

If you have the right version but it still won't work, try:
1. Remove the tool: `npm remove -g mint`
2. Reinstall it: `npm i -g mint`
3. Try starting it again: `mint dev`

You can also try updating the tool to the latest version:
```
npm mint update
```

**"I see a 404 error when trying to preview."**

Make sure you're in the right folder—the one that contains the `docs.json` file. Type `ls` (Mac/Linux) or `dir` (Windows) to see what files are in your current folder.

**"The preview and my live site look different."**

Make sure your preview tool is up to date. Run:
```
npm mint update
```

This ensures your local preview matches the live version.

**"Something went wrong and I'm getting an error I don't understand."**

Try this fix:
1. Go to your home folder
2. Delete the hidden folder named `.mintlify`
3. Run `mint dev` again

This clears out any corrupted settings.

**"Where do I put my images?"**

Create a folder called `images` in your project and put your image files there. Then reference them in your pages like this:
```markdown
![Description of image](/images/your-image.png)
```

## Next Steps

Now that you have your documentation set up, here's what to do next:

### Explore the Examples
Look through the example pages that came with your template. They show you how to:
- Format text and create sections
- Add code examples with syntax highlighting
- Include images and other media
- Create tables and lists
- Use special components like callouts and accordions

### Write Your First Page
Replace one of the example pages with your own content:
1. Pick a page you want to customize
2. Open the file in your text editor
3. Replace the content with your own text
4. Save and check the preview
5. Adjust until it looks right

### Add More Pages
As your project grows, add new pages:
1. Create a new `.mdx` file
2. Add your content
3. Add the filename to `docs.json` in the right navigation group
4. Save and check the preview

### Customize the Design
Make your documentation truly yours:
- Update colors to match your brand
- Add your logos
- Adjust the navigation structure
- Add social media links in the footer

### Share With Your Team
Once you're happy with your documentation:
1. Push your changes to GitHub
2. Wait a few minutes for it to go live
3. Share the URL with your team or users

## Tips for Success

**Start Small:** Don't try to document everything at once. Start with:
- A homepage explaining what your project does
- A quick start guide
- Documentation for one or two main features

You can always add more pages later.

**Keep It Simple:** Good documentation is clear and simple:
- Use short sentences
- Explain one thing at a time
- Include examples
- Think about what someone new to your project needs to know

**Use the Examples:** The template includes lots of examples showing different ways to format and present information. Copy what works for you.

**Update Regularly:** Documentation is never truly finished. As your project changes, keep your documentation up to date.

## Get Help

If you run into problems or have questions:

- Check the full documentation at `https://mintlify.com/docs` for detailed guides
- Email support at `hi@mintlify.com` for help
- Look at example documentation sites at `https://mintlify.com/customers` for inspiration
- Review the example pages in your template

You've got everything you need to create great documentation. Take it one step at a time, and don't hesitate to reach out if you need help. Happy documenting! 🚀