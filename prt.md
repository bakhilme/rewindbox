ROLE: You are a Senior Shopify Theme Developer. Your task is to apply a "Cyberpunk/90s Retro" visual overhaul to the standard Dawn theme without breaking its core functionality or future update compatibility.

BRAND GUIDELINES:

Name: Rewind Box

Vibe: 90s Arcade, Synthwave, High-Contrast Dark Mode.

Primary Colors: Black (#0a0a0a), Neon Green (#39ff14), Neon Purple (#bd00ff).

Fonts: 'Press Start 2P' (Headings), 'Inter' (Body).

TASK LIST:

Task 1: Create the Style Override File

Create a NEW file at: assets/retro-style.css.

Do NOT edit assets/base.css. We want a separate file for safety.

Content: Add CSS variables for the colors and fonts. Override the following Dawn classes to enforce "Dark Mode" and "Pixelated Styles":

body / .gradient: Background #0a0a0a, Text #e0e0e0.

h1, h2, h3, .button: Font-family 'Press Start 2P', Uppercase, Neon text-shadows.

.button: Remove border-radius (sharp corners), add solid 4px neon box-shadow (arcade button look).

.card: Dark background #111, border 1px solid #333.

Task 2: Create the Marquee Section

Create a NEW file at: sections/scrolling-marquee.liquid.

Functionality: An infinite scrolling text bar (CSS animation) that moves from right to left.

Schema: Allow the user to change the Text, Background Color, and Text Color in the Theme Editor.

Style: Include a "Retro Tilt" option (rotate -1deg) for style.

Task 3: Connect Everything

Edit layout/theme.liquid.

Step A: In the <head>, add the Google Fonts link for 'Press Start 2P'.

Step B: Find where base.css is linked. Immediately AFTER it, link the new retro-style.css file.

CONSTRAINTS:

Do not delete any existing files.

Do not modify assets/base.css or assets/global.js.

Ensure all new classes are scoped or clearly commented.

2. The "Danger Zone" (Files NOT to Touch)
To ensure your store remains stable and upgradable, strict adherence to these rules is required:

❌ assets/base.css: Never edit this. It is huge (3000+ lines). If you change it, you cannot update the theme later without losing work. Always use your separate retro-style.css.

❌ assets/global.js: Do not touch the JavaScript. It handles the "Add to Cart" logic, variant switching, and search. Breaking this stops sales.

❌ snippets/price.liquid & snippets/product-card.liquid: Logic-heavy files. Change their look via CSS, but avoid changing their HTML structure unless absolutely necessary.

❌ config/settings_schema.json: Do not edit manually. This breaks the "Customize" button if there is a syntax error.

3. Shopify Standards & QA Checklist
Before you publish, check these 4 points. If they pass, your code is production-ready.

The "Mobile Overflow" Check:

Issue: The "Press Start 2P" font is very wide. Long words like "SPECIFICATIONS" often break off the screen on mobile phones.

Fix: Ensure your CSS includes word-break: break-word; for headings, or use font-size: clamp(...) to scale text down on small screens.

The "Button Click" Check:

Issue: Custom CSS sometimes covers buttons with invisible layers (z-index issues).

Test: Go to a product page. Click "Add to Cart". Does the drawer open? If not, check your z-index on the marquee or header.

The "Loading Flash" Check:

Issue: The page loads white for 0.5 seconds before turning black.

Fix: In layout/theme.liquid, find the <body class="..."> tag. Add a localized style style="background-color: #0a0a0a;" directly to the HTML tag to prevent the "white flash of death."

Accessibility (A11y):

Issue: Neon Green text on a Light Grey background is hard to read.

Rule: Ensure high contrast. Your Neon Green (#39ff14) works great on Black (#0a0a0a), but is invisible on White. Keep the background dark.
