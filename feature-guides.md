# Feature Guides

Welcome to the Mintlify Documentation Starter Kit feature guides. These guides show you how to use each feature with clear, step-by-step instructions. Everything in this guide is based on what actually exists in your documentation project.

## Getting Started with Your Documentation

### Creating Your First Documentation Page

Want to add content to your documentation? It's simple - just create text files and they'll automatically become pages on your site.

**What You'll Get:**
- A new page that appears in your documentation
- Automatic formatting and styling
- Search functionality that includes your new content
- Navigation that updates to include your page

**How to Create a Page:**

1. Open your documentation folder on your computer (where you see the `docs.json` file)
2. Create a new file with a `.md` extension - for example, `my-feature.md`
3. Write your content using simple text formatting (we'll show you how below)
4. Add the page to your navigation so people can find it
5. Save your file and see it appear in your documentation

**Understanding Your Page Structure:**

Each page uses Markdown, which is like writing a regular text document with simple formatting symbols. You don't need to know HTML or programming.

**Adding Your Page to Navigation:**

To make your page appear in the menu, open the `docs.json` file and add your page name:

Find the section that looks like this:
```
"pages": [
  "index",
  "quickstart"
]
```

Add your page name (without the .md extension):
```
"pages": [
  "index",
  "quickstart",
  "my-feature"
]
```

**Viewing Your Changes:**

If you have the preview running (by running `mint dev` in your terminal), your new page appears immediately. Just refresh your browser to see it.

## Organizing Your Documentation

### Setting Up Your Navigation Menu

The navigation menu is how people find their way around your documentation. You organize it using tabs, groups, and pages - think of it like folders and files on your computer.

**What You'll Get:**
- A clear menu structure that makes sense to your users
- Related pages grouped together
- Multiple sections for different types of content
- Easy navigation between topics

**How Navigation Works:**

Your documentation uses a three-level structure:

**Tabs** are the top-level sections. In the example documentation, there are two tabs:
- "Guides" for learning and setup information
- "API reference" for technical API details

**Groups** organize related pages within a tab. For example, the Guides tab has groups like:
- "Getting started" for new users
- "Customization" for personalizing your site
- "Writing content" for content creation help

**Pages** are the actual documentation articles within each group.

**Setting Up Your Navigation:**

Open the `docs.json` file and find the navigation section. You'll see it's organized like this:

```
"navigation": {
  "tabs": [
    {
      "tab": "Guides",
      "groups": [
        {
          "group": "Getting started",
          "pages": [
            "index",
            "quickstart",
            "development"
          ]
        }
      ]
    }
  ]
}
```

**Adding a New Group:**

To add a new section to your menu:

1. Find the tab where you want the new group
2. Add a new group with its pages:
```
{
  "group": "My New Section",
  "pages": [
    "page-one",
    "page-two"
  ]
}
```

**Creating a New Tab:**

To add a completely new top-level section:

1. Add a new tab at the same level as existing tabs:
```
{
  "tab": "Tutorials",
  "groups": [
    {
      "group": "Beginner Tutorials",
      "pages": ["tutorial-1", "tutorial-2"]
    }
  ]
}
```

## Customizing Your Site's Appearance

### Changing Colors and Branding

Make your documentation match your brand by customizing colors, logos, and visual elements.

**What You'll Get:**
- Documentation that matches your company colors
- Your logo displayed prominently
- A consistent brand experience
- Professional-looking pages

**How to Change Colors:**

Open your `docs.json` file and find the colors section. You'll see three color settings:

- **Primary color**: Used for buttons, links, and important elements (currently set to green: `#16A34A`)
- **Light color**: Used for hover effects and lighter accents (currently `#07C983`)
- **Dark color**: Used for selected items and darker accents (currently `#15803D`)

To change these to your brand colors:

1. Find the colors section in `docs.json`
2. Replace the color codes with your brand colors
3. Save the file and refresh your preview

For example, to use blue instead of green:
```
"colors": {
  "primary": "#0066CC",
  "light": "#3399FF",
  "dark": "#004499"
}
```

**Adding Your Logo:**

Your documentation can show different logos for light and dark themes:

1. Create a folder called `logo` in your documentation directory
2. Save your light theme logo as `light.svg` in that folder
3. Save your dark theme logo as `dark.svg` in the same folder
4. The system automatically switches between them based on the viewer's theme preference

Your logos should be SVG files for the best quality, typically around 120-200 pixels wide and 30-50 pixels tall.

**Changing the Site Icon:**

The small icon that appears in browser tabs (called a favicon):

1. Save your icon as `favicon.svg` in your main documentation folder
2. Make sure the file path in `docs.json` matches: `"favicon": "/favicon.svg"`

## Adding External Links

### Creating Global Navigation Links

Add links to external resources that appear throughout your documentation.

**What You'll Get:**
- Persistent links to important external resources
- Icons that make links easy to identify
- Links that appear on every page
- Professional navigation that connects to your broader ecosystem

**How to Add External Links:**

Your documentation includes a feature called "anchors" - these are links that appear globally across all pages.

The example documentation includes two anchors:
- A link to the full Mintlify documentation
- A link to the Mintlify blog

**Adding Your Own Links:**

Find the anchors section in `docs.json` and add your links:

```
"anchors": [
  {
    "anchor": "Support",
    "href": "https://support.yoursite.com",
    "icon": "life-ring"
  },
  {
    "anchor": "GitHub",
    "href": "https://github.com/yourorg/yourrepo",
    "icon": "github"
  }
]
```

The three parts you need for each link:
- **anchor**: The text people see
- **href**: Where the link goes
- **icon**: A symbol that appears next to the text

## Configuring the Top Navigation Bar

### Setting Up Header Links and Buttons

Customize the bar that appears at the top of every documentation page.

**What You'll Get:**
- Quick access to support and important resources
- A prominent button for key actions
- Professional header that matches your needs
- Consistent navigation across all pages

**How to Add Header Links:**

The navigation bar can include regular links and a special primary button.

**Adding Regular Links:**

These appear in the top bar and can go anywhere. The example includes a support email link:

```
"links": [
  {
    "label": "Support",
    "href": "mailto:hi@mintlify.com"
  }
]
```

You can add multiple links:
```
"links": [
  {
    "label": "Support",
    "href": "mailto:support@yoursite.com"
  },
  {
    "label": "Status",
    "href": "https://status.yoursite.com"
  }
]
```

**Adding a Primary Button:**

The primary button is a prominent call-to-action in your header. The example links to a dashboard:

```
"primary": {
  "type": "button",
  "label": "Dashboard",
  "href": "https://dashboard.mintlify.com"
}
```

Change it to suit your needs:
```
"primary": {
  "type": "button",
  "label": "Get Started",
  "href": "https://app.yoursite.com/signup"
}
```

## Enabling AI Tool Integration

### Connecting Documentation with Development Tools

Allow developers to open documentation content directly in their AI assistants and code editors.

**What You'll Get:**
- Quick access to AI assistants from code examples
- Ability to open code in editors like VS Code or Cursor
- Copy functionality for code blocks
- Modern developer experience

**How to Configure AI Integrations:**

The documentation includes a feature called "contextual options" that appears when people interact with your documentation.

Current options in the example:
- **copy**: Copy content to clipboard
- **view**: View in different formats
- **chatgpt**: Open in ChatGPT
- **claude**: Open in Claude AI
- **perplexity**: Open in Perplexity
- **mcp**: Model Context Protocol integration
- **cursor**: Open in Cursor editor
- **vscode**: Open in VS Code

**Choosing Which Options to Enable:**

Find the contextual section in `docs.json` and select the options you want:

For basic functionality:
```
"options": [
  "copy",
  "view"
]
```

For developers who use specific tools:
```
"options": [
  "copy",
  "view",
  "vscode",
  "github"
]
```

For comprehensive AI integration:
```
"options": [
  "copy",
  "chatgpt",
  "claude",
  "perplexity"
]
```

These options appear when people right-click or interact with code blocks in your documentation.

## Adding Social Media Links

### Creating Footer Social Connections

Add links to your social media profiles in the footer of every page.

**What You'll Get:**
- Professional footer with social links
- Icons for each platform
- Links that appear on every page
- Easy way for people to connect with you

**How to Add Social Links:**

The footer section lets you add links to various social platforms. The example includes:
- X (formerly Twitter)
- GitHub
- LinkedIn

**Adding Your Links:**

Find the footer section in `docs.json` and add your profile URLs:

```
"socials": {
  "x": "https://x.com/yourhandle",
  "github": "https://github.com/yourorg",
  "linkedin": "https://linkedin.com/company/yourcompany"
}
```

**Supported Platforms:**

You can add links to many platforms:
- **x**: X/Twitter
- **github**: GitHub
- **linkedin**: LinkedIn
- **discord**: Discord
- **youtube**: YouTube
- **slack**: Slack workspace

Just add the ones you want:
```
"socials": {
  "github": "https://github.com/yourorg",
  "discord": "https://discord.gg/yourinvite",
  "youtube": "https://youtube.com/@yourchannel"
}
```

## Setting Up API Documentation

### Documenting Your API Automatically

If you have an API, you can document it automatically by providing an OpenAPI specification.

**What You'll Get:**
- Beautiful API documentation
- Interactive examples
- Automatic request/response formatting
- Professional API reference pages

**How It Works:**

The example documentation includes a sample API (the Plant Store API) to show how this feature works. The API documentation is generated from a file called `openapi.json` in the `api-reference` folder.

**What the API Documentation Shows:**

For the Plant Store example, the documentation automatically displays:

**Available Operations:**
- Viewing all plants (with options to limit results)
- Adding new plants
- Removing plants
- Webhook notifications when plants are added

**Authentication Information:**
- How to authenticate with the API
- What credentials are needed
- Where to include authentication tokens

**Data Structures:**
- What information each API operation accepts
- What responses you'll receive
- Error message formats

**Using This for Your Own API:**

To document your API:

1. Create your OpenAPI specification file (a JSON file describing your API)
2. Save it in the `api-reference` folder
3. Update the navigation in `docs.json` to include your API pages
4. The documentation generates automatically from your specification

The OpenAPI file includes everything about your API:
- Available endpoints and methods
- Required and optional parameters
- Response formats
- Error conditions
- Authentication requirements

## Previewing Your Changes

### Seeing Your Documentation Live

As you make changes, you can see them immediately on your computer before publishing.

**What You'll Get:**
- Instant preview of your changes
- Ability to test before publishing
- Confidence that everything works correctly
- Fast feedback on your edits

**How to Start the Preview:**

1. Open your terminal or command prompt
2. Navigate to your documentation folder (where `docs.json` is located)
3. Run this command: `mint dev`
4. Open your browser and go to `http://localhost:3000`

Your documentation appears in the browser. Any changes you make to files automatically update in the browser - just refresh the page to see them.

**Troubleshooting the Preview:**

**If the preview won't start:**
- Make sure you're in the right folder (where you see `docs.json`)
- Try updating the preview tool by running `mint update`
- Check that you have Node.js installed on your computer

**If you see 404 errors:**
- Verify you're running the preview from the folder with `docs.json`
- Check that page files exist where your navigation says they should be
- Make sure file names in navigation match actual file names (without .md)

**If changes don't appear:**
- Try refreshing your browser
- Check that you saved your files
- Look for error messages in the terminal

## Publishing Your Documentation

### Making Your Documentation Live

When you're ready to share your documentation with the world, you can publish it automatically.

**What You'll Get:**
- Automatic updates when you make changes
- Fast, reliable hosting
- No manual deployment steps
- Version control integrated with your documentation

**How to Set Up Publishing:**

1. Go to the Mintlify dashboard at `dashboard.mintlify.com/settings/organization/github-app`
2. Install the GitHub app
3. Connect it to your documentation repository
4. Choose which branch should trigger automatic updates

**What Happens When You Publish:**

After setup, publishing is automatic:

1. Make changes to your documentation files
2. Save and commit your changes to GitHub
3. Push the changes to your repository
4. Your live documentation updates automatically

You don't need to run any commands or manually deploy - just save your files and push to GitHub.

**How Long Publishing Takes:**

Typically, your changes appear on your live site within a few minutes of pushing to GitHub. The system:
- Detects your changes
- Rebuilds your documentation
- Updates your live site
- Clears caches so changes appear immediately

## Maintaining Your Documentation

### Keeping Everything Current

Good documentation stays up to date with your product. Here's how to maintain yours effectively.

**What You'll Get:**
- Documentation that stays current with your product
- Easy process for making updates
- Confidence that information is accurate
- Happy users who find what they need

**Regular Maintenance Tasks:**

**Reviewing Content Accuracy:**
- Periodically check that instructions still work correctly
- Update screenshots and examples when your interface changes
- Test links to ensure they still go to the right places
- Verify code examples work with current versions

**Updating for New Features:**
- Add documentation when you release new features
- Update existing pages that new features affect
- Add examples showing how new features work
- Update navigation to include new pages

**Responding to Feedback:**
- Track questions users ask
- Update documentation to answer common questions
- Fix errors or unclear sections that users report
- Add missing information that users request

**Organizing Content:**
- As your documentation grows, reorganize navigation for clarity
- Group related pages together
- Create clear section names that make sense to users
- Remove or archive outdated information

## Understanding Your Documentation Structure

### How Everything Fits Together

Your documentation is organized as a collection of text files and a configuration file that controls how everything appears.

**The Key Files:**

**docs.json**: The control center
- Contains all settings for your site
- Defines navigation structure
- Controls colors and branding
- Manages external links and integrations

**Markdown files (.md)**: Your content
- Each file becomes a page
- Simple text format with basic formatting
- Can include code examples, images, and links
- Organized in folders matching your navigation

**Logo and icon files**: Visual branding
- SVG files for your logo (light and dark versions)
- Favicon for browser tabs
- Stored in the logo folder

**API specification files**: Optional API documentation
- OpenAPI files that describe your API
- Generate automatic API documentation
- Include examples and schemas

**How They Work Together:**

When someone views your documentation:

1. The system reads `docs.json` to understand your site structure
2. It finds the content in your markdown files
3. It applies your colors and branding
4. It generates the navigation based on your configuration
5. It creates a fast, searchable website

You just focus on writing content and configuring `docs.json` - the system handles everything else.

---

These feature guides cover everything you can do with your Mintlify Documentation Starter Kit. Each guide focuses on practical, actionable steps using the features that actually exist in your documentation project. Start with the basics like creating pages and customizing colors, then explore advanced features like API documentation and AI tool integration as your documentation grows.