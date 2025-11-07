I'll analyze the Mintlify Documentation Starter Kit source code to create comprehensive, user-friendly feature guides.

<read_file>
<path>docs.json</path>
</read_file>

<read_file>
<path>README.md</path>
</read_file>

<read_file>
<path>api-reference/openapi.json</path>
</read_file>

Now I'll create comprehensive feature guides based on the actual features in the Mintlify starter kit:

# Mintlify Documentation - Feature Guides

Welcome to the Mintlify Documentation Feature Guides! This guide will show you how to use all the features available in your documentation site.

## Getting Started with Your Documentation

### Creating Your First Page

Want to add a new page to your documentation? It's simple - just create a text file and add it to your project.

**What you'll do:**
1. Create a new file in your documentation folder
2. Name it with a `.md` extension (like `my-page.md`)
3. Write your content using simple formatting
4. Add the page to your navigation
5. Save and preview your changes

**How pages work:**
Every page is just a text file written in Markdown. Markdown is a simple way to format text - you don't need to know any coding. For example:
- `# My Heading` creates a large heading
- `**bold text**` makes text bold
- `[link text](url)` creates a clickable link

**Adding your page to the menu:**
Open the `docs.json` file and find the section where pages are listed. Add your new page name (without the .md part) to the list, and it will appear in your documentation menu.

### Organizing Your Documentation

Your documentation uses a three-level organization system to keep everything neat:

**Tabs** - These are the big sections at the top. The example documentation has two tabs:
- "Guides" - for learning and tutorials
- "API reference" - for technical details

**Groups** - Within each tab, you have groups that organize related pages together. For example, the Guides tab has:
- "Getting started" - for new users
- "Customization" - for personalizing your site
- "Writing content" - for creating documentation
- "AI tools" - for connecting with AI assistants

**Pages** - These are your actual documentation articles

**Example structure:**
Think of it like organizing files on your computer. Tabs are like main folders, groups are subfolders, and pages are the individual documents inside.

## Customizing Your Site's Appearance

### Changing Colors

Make your documentation match your brand by changing the colors.

**What you'll change:**
1. Open the `docs.json` file in your project
2. Find the section labeled "colors"
3. You'll see three color codes (they look like `#16A34A`)
4. Replace these with your own colors
5. Save the file

**The three colors:**
- **Primary color**: Used for important buttons, links, and highlights (currently green: `#16A34A`)
- **Light color**: Used for hover effects and lighter accents (currently lighter green: `#07C983`)
- **Dark color**: Used for selected items and darker accents (currently darker green: `#15803D`)

**How to pick colors:**
You can use any online color picker to get the color codes you want. Just make sure to include the `#` symbol before the color code.

**Example:** To change from green to blue:
```
"colors": {
  "primary": "#0066CC",
  "light": "#3399FF",
  "dark": "#004499"
}
```

### Adding Your Logo

Show your brand by adding your own logo to the documentation.

**What you'll do:**
1. Create a folder called `logo` in your project
2. Add two versions of your logo as image files:
   - One for when people use light mode (name it `light.svg`)
   - One for when people use dark mode (name it `dark.svg`)
3. The documentation will automatically show the right logo based on the viewer's theme preference

**Logo tips:**
- Use SVG files for the best quality
- Make your logos about 120-200 pixels wide
- Make sure they look good on both light and dark backgrounds

### Changing the Site Icon

The small icon that appears in browser tabs is called a favicon.

**What you'll do:**
1. Save your icon file as `favicon.svg` in your main project folder
2. The documentation automatically uses this file
3. Your icon will appear in browser tabs when people visit your documentation

## Setting Up Navigation

### Creating Custom Navigation Links

Add links to important external resources that appear throughout your site.

**What these are:**
These are called "anchors" - they're links that stay visible on every page, no matter where your readers are in the documentation.

**Where to add them:**
In the `docs.json` file, find the section called "anchors" under "global". You can add as many as you need.

**Example links you might add:**
- Link to your support page
- Link to your GitHub repository
- Link to your community forum
- Link to your status page

**What you'll need for each link:**
- The text people will see (like "Support" or "GitHub")
- The web address where it goes
- An icon name (optional, but makes it look nice)

**Available icons:**
The system includes many built-in icons like:
- `life-ring` for support
- `github` for GitHub
- `newspaper` for blogs
- `book-open-cover` for documentation

### Adding Header Navigation

The header is the bar at the top of your documentation. You can add custom links and buttons here.

**Adding regular links:**
These appear as text links in the header. Common examples:
- Support email links
- Status page links
- Community links

**Adding a prominent button:**
You can add one special button that stands out more than regular links. This is called the "primary button." Use it for your most important action, like:
- "Go to Dashboard"
- "Sign Up"
- "Try Free"

**How to set it up:**
In the `docs.json` file, find the "navbar" section. Add your links in the "links" list, and your special button in the "primary" section.

## Adding Social Media Links

Show your social media presence in the footer of every page.

**What you'll do:**
1. Open the `docs.json` file
2. Find the "footer" section
3. Add links to your social media profiles
4. Each platform gets its own line

**Supported platforms:**
- X (formerly Twitter)
- GitHub
- LinkedIn
- Discord
- YouTube
- Slack
- And more!

**How it looks:**
The system automatically shows the right icon for each platform. You just provide the web address.

## Writing Great Content

### Using Markdown Formatting

Markdown is the simple formatting language used for all documentation pages. Here's what you can do:

**Headings:**
Create headings with `#` symbols:
- `# Biggest Heading`
- `## Medium Heading`
- `### Smaller Heading`

**Text formatting:**
- `**bold text**` makes text **bold**
- `*italic text*` makes text *italic*
- `` `code` `` shows `code` in a special font

**Lists:**
Create bullet lists by starting lines with `-`:
```
- First item
- Second item
- Third item
```

Create numbered lists by using numbers:
```
1. First step
2. Second step
3. Third step
```

**Links:**
Create clickable links: `[click here](https://example.com)`

**Images:**
Add images: `![description](path-to-image.png)`

### Adding Code Examples

Show code examples with syntax highlighting.

**How to add code:**
Wrap your code in triple backticks and specify the programming language:

````
```javascript
function hello() {
  console.log("Hello, world!");
}
```
````

**The system will automatically:**
- Color-code your code based on the language
- Add a copy button so readers can easily copy the code
- Make it easy to read and understand

**Supported languages:**
JavaScript, Python, Java, Go, Ruby, PHP, and many more.

## Connecting with AI Tools

Your documentation can integrate with popular AI assistants and code editors to help your readers.

**What this does:**
When readers see code in your documentation, they can quickly:
- Copy it to their clipboard
- Open it in ChatGPT to ask questions
- Send it to Claude AI for explanations
- Open it directly in their code editor

**Available integrations:**
- Copy to clipboard
- ChatGPT
- Claude
- Perplexity
- Cursor editor
- VS Code

**Setting this up:**
In the `docs.json` file, find the "contextual" section and choose which options you want to enable.

**Example - just copy functionality:**
```
"options": [
  "copy",
  "view"
]
```

**Example - AI assistants:**
```
"options": [
  "copy",
  "chatgpt",
  "claude",
  "perplexity"
]
```

## Including API Documentation

If you have an API, you can include beautiful, interactive API documentation.

**What this does:**
Instead of writing API documentation manually, you provide a special file that describes your API, and the system automatically creates nice-looking documentation pages with:
- All your API endpoints
- Request and response examples
- Interactive testing capabilities
- Beautiful formatting

**How it works:**
1. Create an OpenAPI specification file (a standard format for describing APIs)
2. Save it in your project (usually in an `api-reference` folder)
3. Add references to it in your navigation
4. The documentation generates automatically

**The example includes:**
The starter kit includes a sample API (the Plant Store API) to show you how this works. You can see it in the `api-reference/openapi.json` file.

**What the sample shows:**
- How to define API endpoints
- How to document request parameters
- How to show response formats
- How to include authentication requirements

## Previewing Your Changes

See your documentation live on your computer as you work on it.

**What you'll do:**
1. Open your terminal or command prompt
2. Go to your documentation folder
3. Type: `mint dev`
4. Open your web browser to `http://localhost:3000`

**What happens:**
Your documentation appears in the browser. When you make changes to your files, the browser automatically refreshes to show your updates.

**If something goes wrong:**
- Make sure you're in the right folder (look for `docs.json`)
- Try running `mint update` to get the latest version
- Check that you have Node.js installed on your computer

## Publishing Your Documentation

Make your documentation live on the internet for everyone to see.

**What you'll do:**
1. Go to the Mintlify dashboard (dashboard.mintlify.com)
2. Connect your GitHub repository
3. Set up automatic publishing
4. Every time you save changes and push to GitHub, your documentation updates automatically

**How it works:**
- You edit your documentation files
- You save and commit your changes to GitHub
- Mintlify detects the changes
- Your live documentation updates automatically within minutes

**No manual steps needed:**
Once set up, publishing is completely automatic. Just save your changes to GitHub.

## Common Questions

**Q: Can I change the site name?**
A: Yes! In `docs.json`, change the "name" value to whatever you want.

**Q: How do I remove example pages?**
A: Delete the markdown files you don't want, and remove their references from the navigation in `docs.json`.

**Q: Can I add my own custom pages?**
A: Absolutely! Create new `.md` files and add them to the navigation.

**Q: What if I want different colors for light and dark mode?**
A: The system automatically adjusts colors for both modes based on your three chosen colors.

**Q: Can I have more than two tabs?**
A: Yes! Add as many tabs as you need in the navigation section.

**Q: How do I know which files I can safely edit?**
A: You can edit any `.md` file (your content) and `docs.json` (your settings). Don't edit system files.

**Q: Can I preview changes before publishing?**
A: Yes! Run `mint dev` to see changes on your computer before they go live.

## Tips for Success

### Start Simple
Begin with just a few pages and add more as you need them. You don't need to create everything at once.

### Use Clear Navigation Names
Name your groups and pages so people immediately understand what they'll find there.

### Keep Colors Consistent
Choose colors that work well together and match your brand.

### Test Your Links
After adding navigation links, click them to make sure they go to the right places.

### Update Regularly
Keep your documentation current by updating it when your product changes.

### Get Feedback
Ask others to read your documentation and tell you what's confusing or missing.

## Next Steps

Now that you know the features:

1. **Customize the appearance** with your colors and logo
2. **Organize your content** with clear navigation
3. **Write your first pages** using Markdown
4. **Set up publishing** so changes go live automatically
5. **Share your documentation** with your team and users

Remember: Great documentation takes time. Start with the basics and improve as you go. Your readers will appreciate clear, well-organized information more than fancy features.

Need help? Check the Mintlify documentation at mintlify.com/docs for more details and examples.