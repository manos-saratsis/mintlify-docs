I'll retrieve the key source file first to understand the product and generate the FAQ documentation.# Frequently Asked Questions

## General Questions

### What is this documentation platform?

This is a modern documentation platform built on Mintlify that helps you create professional, searchable documentation websites. You can write guides, document APIs, and share knowledge with your users—all using simple text files that automatically become beautiful web pages.

### Do I need to know how to code?

No! You can create great documentation using Markdown, which is as simple as writing text in a document. For example, typing `# Heading` creates a heading, and `**bold**` makes text bold. The platform handles all the technical details of turning your text into a website.

### Is this free to use?

The starter kit is open source with an MIT license, which means it's free to use for any purpose. You'll just need a free GitHub account to store your documentation files and get started.

### What can I use this for?

You can create any type of documentation:
- Product guides and tutorials for your users
- Technical documentation for developers
- API reference documentation
- Knowledge bases and help centers
- Internal team documentation
- Project wikis

## Getting Started

### How long does it take to set up?

You can have your first documentation site running in about 10 minutes. This includes getting the template, previewing it on your computer, and making your first customizations.

### What do I need before I start?

You need three things:
- A GitHub account (free to create)
- About 10 minutes of time
- The content you want to document

### Can I see what my documentation looks like before publishing?

Yes! You can preview your documentation on your own computer as you work. Run a simple command in your terminal, and your documentation opens in your browser. Any changes you make appear immediately when you refresh.

### What if I get stuck during setup?

The getting started guide includes troubleshooting tips for common issues. If the preview tool isn't starting, try updating it with a simple command. If you see errors, check that you're in the correct folder. You can also reach out for help via the support email.

## Creating and Organizing Content

### How do I create a new page?

Creating a page is simple:
1. Create a new text file ending in `.md` (like `my-guide.md`)
2. Write your content using simple Markdown formatting
3. Add the page to your navigation menu in the `docs.json` file
4. Save and preview—your new page appears in your documentation

### How do I organize pages into sections?

Your documentation uses a three-level structure:
- **Tabs** are top-level sections (like "Guides" and "API Reference")
- **Groups** organize related pages (like "Getting Started" or "Advanced Features")
- **Pages** are individual articles

You control this structure by editing the `docs.json` file.

### Can I include images in my documentation?

Yes! You can add images to illustrate your guides and make them easier to understand. Save your images in an `images` folder, then reference them in your pages using simple Markdown syntax.

### How do I add code examples?

Code examples are easy to include. Just wrap your code in special markers (three backticks) and specify the programming language. The platform automatically adds syntax highlighting to make the code easy to read.

### Can I reuse content across multiple pages?

Yes! The platform supports reusable snippets—write content once and include it on multiple pages. This is helpful for warnings, common instructions, or any content that appears in several places.

## Customization

### How do I change the colors?

Open your `docs.json` file and find the colors section. You'll see three color codes:
- Primary color (for links and buttons)
- Light color (for accents)
- Dark color (for emphasis)

Replace these with your brand colors (in hex format like `#0066CC`) and save the file. Your documentation updates immediately.

### Can I add my company logo?

Yes! Create a `logo` folder and add two versions of your logo:
- `light.svg` for light theme
- `dark.svg` for dark theme

The platform automatically shows the right logo based on what theme someone is viewing.

### What if I don't have SVG logos?

SVG format works best because it scales perfectly at any size. If you have PNG or JPG logos, you can use free online tools to convert them to SVG format.

### Can I change the navigation menu?

Yes! The navigation menu is completely customizable. You can add new sections, remove ones you don't need, rename sections, and rearrange pages in any order. All navigation settings are in the `docs.json` file.

### How do I add links to external resources?

You can add persistent links that appear throughout your documentation using the "anchors" feature in `docs.json`. For example, you might link to your support site, GitHub repository, or status page. These links appear on every page with icons you choose.

## Publishing and Updates

### How do I publish my documentation?

After you've created your content, connect your GitHub repository to the Mintlify dashboard. From that point on, publishing is automatic—just save your changes to GitHub, and your live documentation updates within minutes.

### Do I need to manually deploy updates?

No! Once you've connected your repository to the dashboard, updates happen automatically. Make changes to your files, save them to GitHub, and your live site updates on its own. No commands to run, no manual deployment steps.

### How long do updates take to appear?

Changes typically appear on your live site within a few minutes after you push them to GitHub. The system detects your changes, rebuilds your documentation, and updates the live site automatically.

### Can I preview changes before they go live?

Yes! The preview tool on your computer shows exactly what your documentation will look like. Test your changes locally before saving them to GitHub, and you can be confident everything will work correctly.

### What happens if I make a mistake?

Because your documentation is stored in GitHub, you have complete version history. If something goes wrong, you can easily revert to a previous version. GitHub keeps track of every change you make.

## API Documentation

### Can I document my API?

Yes! If you have an OpenAPI specification (also called Swagger), the platform automatically generates beautiful, interactive API documentation. Just include your OpenAPI file in your project, and the documentation creates itself.

### What if I don't have an OpenAPI specification?

The starter kit includes a complete example API (the Plant Store API) that shows you what OpenAPI looks like and how it generates documentation. You can use this as a template for creating your own API specification.

### What does API documentation include?

Automatically generated API documentation shows:
- All available endpoints and methods
- Required and optional parameters
- Request and response examples
- Authentication requirements
- Data schemas and types
- Error responses

### Do I need to be a developer to document an API?

Creating the OpenAPI specification requires some technical knowledge, but the documentation platform handles all the formatting and presentation automatically. Once you have the specification file, the rest is automatic.

## AI Tools and Integrations

### What are the contextual options?

Contextual options are interactive features that appear when people use your documentation. These include the ability to copy code examples, open code in editors like VS Code, or send examples to AI assistants like ChatGPT or Claude.

### Which AI tools can I integrate?

The platform supports several AI assistant integrations:
- ChatGPT
- Claude
- Perplexity
- Model Context Protocol (MCP)

You choose which options to enable based on what your users need.

### Do I need to integrate AI tools?

No! These integrations are optional. You can start with basic features like copy-to-clipboard and add AI integrations later if they're useful for your audience.

### What about code editor integrations?

You can enable quick-open links that let users open code examples directly in VS Code or Cursor editor. This is especially helpful for developer-focused documentation.

## Teams and Collaboration

### Can multiple people work on the same documentation?

Yes! Because your documentation lives in GitHub, multiple team members can collaborate using standard Git workflows. You can assign different people to work on different sections, review changes, and manage everything through GitHub's collaboration features.

### How do we prevent conflicts when multiple people edit?

GitHub handles this through its version control system. If two people edit the same file, GitHub helps you merge the changes or choose which version to keep. The documentation platform doesn't add any complexity—it's just like collaborating on any other project in GitHub.

### Can we control who can edit documentation?

Yes! GitHub provides robust permission management. You can give some team members read-only access while others can edit, and you can require reviews before changes go live.

### How do we review documentation changes?

Use GitHub's pull request feature to review changes before they're published. Team members can propose updates, discuss them, suggest improvements, and approve them—all within GitHub's familiar interface.

## Search and Navigation

### How do people search the documentation?

Your documentation includes built-in search functionality. Users can search for any term, and results show relevant pages with context. The search works automatically—you don't need to configure anything.

### Does search work immediately on new pages?

Yes! When you add new pages or update existing content, the search index updates automatically. Users can find your new content as soon as it's published.

### Can users navigate without using search?

Yes! Your navigation menu appears on every page, organized into the sections you've defined. Users can browse through sections, expand groups, and jump between related pages easily.

### What if someone shares a direct link to a page?

Direct links work perfectly. Anyone with the link can access that specific page, and they'll still see the full navigation menu to explore other pages if they want.

## Content Formatting

### What is Markdown?

Markdown is a simple way to format text using plain text symbols. For example:
- `# Heading` creates a large heading
- `## Subheading` creates a smaller heading
- `**bold**` makes text bold
- `*italic*` makes text italic
- `[link text](url)` creates a link

It's designed to be readable even before it's formatted, and it's easy to learn in minutes.

### Can I use tables?

Yes! Markdown supports tables using a simple text-based format. The platform automatically formats them into clean, readable tables in your documentation.

### How do I create lists?

Lists are simple in Markdown:
- For bullet lists, start lines with `-` or `*`
- For numbered lists, start lines with numbers like `1.` and `2.`
- You can nest lists by indenting

### Can I add warnings or callout boxes?

Yes! The platform supports special formatting for important information like warnings, tips, or notes. These appear as highlighted boxes that draw attention to important content.

### What about videos or embedded content?

You can embed videos and other content in your documentation. The exact method depends on the content type, but the platform supports various embed formats.

## Technical Questions

### Where is my documentation hosted?

After you connect to the Mintlify dashboard, your documentation is hosted on Mintlify's infrastructure. This provides fast loading times, reliable uptime, and automatic scaling as your documentation grows.

### Do I need to manage servers?

No! The platform handles all hosting, scaling, and infrastructure management automatically. You just focus on creating great content.

### Can I use a custom domain?

Yes! You can configure your documentation to appear on your own domain (like `docs.yourcompany.com`). This makes your documentation feel like a natural part of your company's online presence.

### Is the documentation fast?

Yes! The platform uses modern web technologies to ensure your documentation loads quickly for users anywhere in the world. Pages are optimized automatically, and the platform uses content delivery networks for fast global access.

### What about mobile devices?

Your documentation automatically adapts to any screen size. It works perfectly on phones, tablets, and desktop computers without any extra configuration needed.

## Maintenance and Updates

### How often should I update documentation?

Update your documentation whenever your product changes. This might include:
- When you release new features
- When you change how existing features work
- When users report confusion or errors
- When you discover better ways to explain things

### How do I know what needs updating?

Pay attention to questions users ask. If multiple people ask about the same thing, your documentation probably needs clarification in that area. Track common support questions and update documentation to address them.

### Can I schedule documentation updates?

While there's no built-in scheduling feature, you can use GitHub's draft pull requests to prepare updates in advance, then publish them when you're ready by merging the pull request.

### What if I need to archive old content?

You can remove pages from your documentation by deleting the files and removing them from your navigation menu. The files remain in GitHub's history if you ever need to reference them later.

## Troubleshooting

### The preview isn't showing my changes

Try these solutions:
- Refresh your browser
- Make sure you saved your files
- Check the terminal for error messages
- Try stopping the preview (Ctrl+C) and starting it again

### I see a 404 error in the preview

This usually means:
- You're not in the correct folder (look for `docs.json`)
- A page referenced in navigation doesn't exist
- A filename in navigation doesn't match the actual file

### My colors aren't changing

Make sure:
- You saved the `docs.json` file
- The color codes are in the correct format (like `#0066CC`)
- You refreshed your browser after making changes

### The preview tool won't start

Try:
- Updating the tool with the command `mint update`
- Checking that Node.js is installed on your computer
- Making sure you're in the right folder

### My changes aren't appearing on the live site

Check that:
- You pushed your changes to GitHub
- You're pushing to the correct branch (usually `main`)
- The connection to Mintlify dashboard is still active
- Wait a few minutes—updates typically take 2-5 minutes

## Support and Help

### Where can I find more detailed guides?

The full Mintlify documentation at `mintlify.com/docs` provides comprehensive guides on every feature. You can also explore the example pages included in your starter kit.

### How do I get help if I'm stuck?

Several options are available:
- Check the troubleshooting sections in the documentation
- Email support at `hi@mintlify.com`
- Look at the example pages in your template
- Review the full documentation online

### Can I see examples of what's possible?

Yes! Visit the Mintlify customer showcase to see real documentation sites built with this platform. These examples show different styles, organizations, and features you can use as inspiration.

### Is there a community I can join?

The Mintlify community includes many documentation creators who share tips and help each other. Check the Mintlify website for links to community resources.

### What if I need custom features?

The platform is extensible and supports customization for specific needs. Contact support to discuss custom requirements—they can often provide guidance or solutions for unique use cases.