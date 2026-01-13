# Customizing the Frontend Theme and UI

This tutorial will guide you through personalizing your application's appearance using the built-in theming system. You'll learn how to change colors, adjust spacing, modify existing elements, and create a unique look that matches your brand.

## Understanding the Theme Structure

Your application uses a centralized theme system that controls the visual appearance throughout the entire interface. All theme settings are managed in a single location, making it easy to maintain consistency.

The theme controls three main aspects:

1. **Global Styles** - Settings that apply to the entire application
2. **Design Tokens** - Reusable values like colors and spacing
3. **Component Recipes** - Specific styling rules for different interface elements

## Changing Colors

### Updating the Primary Color

The main color that appears throughout your application is called `ui.main`. To change it:

1. Open the theme configuration file (`frontend/src/theme.tsx`)
2. Find the colors section within the tokens area
3. Replace the hex color value with your preferred color

**Example:** To change from teal to purple:

```typescript
tokens: {
  colors: {
    ui: {
      main: { value: "#7C3AED" }, // Changed from #009688 to purple
    },
  },
}
```

### Adding New Colors

You can add additional color options for use throughout your application:

```typescript
tokens: {
  colors: {
    ui: {
      main: { value: "#009688" },
      secondary: { value: "#FF6B6B" },
      accent: { value: "#4ECDC4" },
    },
  },
}
```

Once defined, these colors can be referenced in any part of your interface styling.

## Modifying Typography

### Changing Base Font Size

The application sets a base font size for consistency. To adjust text sizing:

1. Locate the `globalCss` section
2. Modify the `fontSize` value under `html` for overall scaling
3. Adjust the `body` fontSize for content text specifically

**Example:** To increase text size application-wide:

```typescript
globalCss: {
  html: {
    fontSize: "18px", // Increased from 16px
  },
  body: {
    fontSize: "1rem", // Adjusted from 0.875rem
  },
}
```

### Creating Text Styles

You can define custom text styles for consistent typography:

```typescript
globalCss: {
  ".main-link": {
    color: "ui.main",
    fontWeight: "bold",
  },
  ".heading-style": {
    fontSize: "1.5rem",
    fontWeight: "600",
    color: "ui.accent",
  },
}
```

## Customizing Component Appearance

### Understanding Component Recipes

Component recipes are style templates that define how specific interface elements look. The application includes a button recipe system (`frontend/src/theme/button.recipe`) that demonstrates this pattern.

### Modifying Button Styles

To customize how buttons appear:

1. Navigate to the button recipe file
2. Adjust properties like colors, borders, padding, and hover effects
3. Save your changes - they'll automatically apply to all buttons

### Creating Custom Component Styles

You can add recipes for other interface elements:

```typescript
theme: {
  recipes: {
    button: buttonRecipe,
    card: cardRecipe,
    input: inputRecipe,
  },
}
```

## Adjusting Spacing and Layout

### Global Spacing

To modify spacing throughout your application, add margin and padding adjustments:

```typescript
globalCss: {
  body: {
    margin: 0,
    padding: 0, // Modify these values to add default spacing
  },
}
```

### Container Widths

Control how wide content appears on different screen sizes by adding container tokens:

```typescript
tokens: {
  sizes: {
    container: {
      sm: { value: "640px" },
      md: { value: "768px" },
      lg: { value: "1024px" },
      xl: { value: "1280px" },
    },
  },
}
```

## Managing Responsive Design

### Understanding Breakpoints

The theme system includes built-in support for responsive design, allowing your interface to adapt to different screen sizes automatically.

### Creating Mobile-Friendly Adjustments

Add responsive rules to ensure your customizations work well on all devices:

```typescript
globalCss: {
  body: {
    fontSize: "0.875rem",
    "@media (max-width: 768px)": {
      fontSize: "0.8rem", // Smaller text on mobile
    },
  },
}
```

## Creating Theme Variants

### Light and Dark Modes

The application supports theme switching through the provider system (`CustomProvider` in `frontend/src/main.tsx`). This provider enables users to toggle between visual modes.

### Adding Variant-Specific Colors

Define colors that change based on the selected theme:

```typescript
tokens: {
  colors: {
    ui: {
      main: { value: "#009688" },
      background: {
        light: { value: "#FFFFFF" },
        dark: { value: "#1A202C" },
      },
    },
  },
}
```

## Advanced Customization Techniques

### Creating Semantic Color Tokens

Define colors based on their purpose rather than appearance:

```typescript
tokens: {
  colors: {
    semantic: {
      success: { value: "#48BB78" },
      error: { value: "#F56565" },
      warning: { value: "#ED8936" },
      info: { value: "#4299E1" },
    },
  },
}
```

### Adding Animation Tokens

Control animation speeds for consistent motion:

```typescript
tokens: {
  durations: {
    fast: { value: "150ms" },
    normal: { value: "300ms" },
    slow: { value: "500ms" },
  },
}
```

## Testing Your Changes

### Visual Verification Process

After making theme changes, verify they appear correctly:

1. Start the development server
2. Navigate through different pages in your application
3. Check that colors, spacing, and typography look as expected
4. Test interactive elements like buttons and menus
5. Verify appearance on different screen sizes

### Testing Across Components

Your theme changes will automatically apply to:

- Navigation areas (Navbar and Sidebar)
- Content sections throughout the application
- Forms and input fields
- Buttons and action menus
- Error and status messages

Visit each area to ensure consistent appearance.

### Browser Testing

Test your customizations in different browsers:

- Chrome/Edge
- Firefox
- Safari
- Mobile browsers

This ensures your theme works universally.

## Common Customization Scenarios

### Scenario 1: Company Branding

To match corporate colors:

1. Replace `ui.main` with your primary brand color
2. Add secondary brand colors as additional tokens
3. Update link colors to match branding
4. Adjust button styles to reflect brand guidelines

### Scenario 2: Improving Readability

To enhance text legibility:

1. Increase base font sizes in the global CSS
2. Adjust line height for better spacing
3. Choose higher contrast colors
4. Increase spacing between elements

### Scenario 3: Minimalist Design

To create a cleaner look:

1. Reduce color variety to 2-3 main colors
2. Remove borders and shadows from component recipes
3. Increase whitespace with larger margins
4. Use simpler font weights

## Troubleshooting Theme Issues

### Changes Not Appearing

If your modifications don't show up:

1. Ensure you saved the theme file
2. Restart the development server
3. Clear your browser cache
4. Check for syntax errors in your theme code

### Inconsistent Colors

If colors appear differently than expected:

1. Verify hex color values are correct (include the # symbol)
2. Check that color tokens are properly nested
3. Ensure you're using the correct token names in components

### Responsive Design Problems

If layouts break on certain screen sizes:

1. Test breakpoint values match your target devices
2. Verify media query syntax is correct
3. Check that responsive values are properly defined

## Best Practices

### Maintain Consistency

- Define colors once in tokens and reuse them
- Use semantic naming for clarity (e.g., "primary" instead of "blue")
- Keep spacing values consistent across similar elements

### Document Your Changes

Keep notes about:

- Why specific colors were chosen
- The intended use of custom tokens
- Any special considerations for certain components

### Test Thoroughly

Before finalizing changes:

- View every major section of your application
- Test all interactive elements
- Verify appearance in both light and dark modes
- Check mobile and desktop layouts

### Performance Considerations

- Avoid overly complex animations
- Keep the number of custom fonts minimal
- Use standard color formats (hex or rgb) for best performance

## Next Steps

Once you're comfortable with basic theme customization, explore:

- Creating entirely new component recipes for custom elements
- Building a comprehensive design system with multiple variants
- Implementing advanced responsive design patterns
- Adding custom animations and transitions

Your theme changes will persist across the entire application, giving users a consistent and polished experience that reflects your unique design vision.