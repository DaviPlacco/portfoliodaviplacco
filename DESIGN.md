# Design System Specification: The Kinetic Luminary

## 1. Overview & Creative North Star
The Creative North Star for this design system is **"The Kinetic Luminary."** 

This system rejects the static nature of traditional web grids in favor of a living, breathing digital canvas. It balances the "heavy" authority of a deep black foundation with the "weightless" ethereality of frosted glass and electric light. We are not building a website; we are curating a high-end gallery where the interface recedes to let the craft shine.

To break the "template" look, designers must embrace **Intentional Asymmetry**. Overlap elements—such as a project title bleeding off the edge of a glass card—and use the massive contrast between `display-lg` typography and `label-sm` metadata to create an editorial feel that mirrors premium print magazines.

---

## 2. Colors & Surface Architecture
The palette is rooted in absolute depth, using `surface` (#131313) as our void, punctuated by the high-energy `primary_container` (#0052ff) to simulate neon luminosity.

### The "No-Line" Rule
**Explicit Instruction:** 1px solid borders for sectioning are strictly prohibited. You may not use a line to separate a header from a hero, or a project list from a footer. 
Boundaries are defined solely through:
- **Background Shifts:** Moving from `surface` to `surface_container_low`.
- **Tonal Transitions:** Using soft radial gradients of `primary` to suggest a boundary without drawing one.

### Surface Hierarchy & Nesting
Treat the UI as a series of stacked, semi-translucent layers. 
- **Base Layer:** `surface` (#131313).
- **Secondary Sectioning:** `surface_container_low` (#1b1b1b).
- **Interactive Elements:** `surface_container_high` (#2a2a2a).
By nesting a `surface_container_highest` card inside a `surface_container_low` section, you create a natural "lift" that feels structural rather than decorative.

### The "Glass & Gradient" Rule
To achieve the requested "ultra-modern" feel, use **Glassmorphism** for all floating UI (Navigation, Popovers, Modals). 
- **Recipe:** Apply `surface_container` at 60% opacity with a `backdrop-filter: blur(20px)`.
- **Signature Texture:** Use subtle linear gradients on CTAs, transitioning from `primary_container` (#0052ff) to `inverse_primary` (#004ced) at a 135-degree angle. This provides a "soul" to the blue that flat hex codes cannot replicate.

---

## 3. Typography
We utilize **Inter** as our typographic backbone, relying on its variable weight capabilities to convey hierarchy.

- **Display Scale (`display-lg` to `display-sm`):** Reserved for hero statements and project titles. Use `letter-spacing: -0.04em` to create a tight, high-fashion tension.
- **Headline & Title:** Use these for section headers. Always pair a `headline-lg` with a `label-md` "kicker" text above it in `primary` color to anchor the eye.
- **Body & Labels:** Use `body-lg` for descriptions, ensuring a maximum line length of 65 characters to preserve readability against the dark background. 

The hierarchy is "Top-Heavy": we use massive scale differences to command attention, then drop significantly to small, precise labels to create a sense of technical sophistication.

---

## 4. Elevation & Depth
In this design system, depth is a function of light and translucency, not shadows.

### The Layering Principle
Achieve elevation by stacking surface tokens. A project card should not have a shadow by default; it should be a `surface_container_high` block sitting on a `surface_dim` background. 

### Ambient Shadows
If an element must float (e.g., a modal), use an **Ambient Shadow**:
- **Color:** `on_secondary_fixed` (#1c1b1b) at 40% opacity.
- **Specs:** `0px 24px 48px`. The blur must be at least double the offset to mimic natural light dispersion.

### The "Ghost Border" Fallback
Where accessibility requires a container definition, use a **Ghost Border**:
- **Token:** `outline_variant` (#434656) at **15% opacity**. 
- This creates a hint of an edge that disappears and reappears as the user scrolls, maintaining the "minimalist" ethos.

---

## 5. Components

### Buttons
- **Primary:** `primary_container` background, `on_primary` text. No border. `xl` (0.75rem) roundedness. On hover, apply a `primary` outer glow (8px blur).
- **Tertiary:** No background. `primary` text. Use `label-md` all-caps with `letter-spacing: 0.1em`. Underline on hover with a 2px `primary` stroke.

### Premium Project Cards
- **Structure:** Forbid divider lines. 
- **Styling:** Use `surface_container_low`. On hover, transition to `surface_container_highest` and apply a subtle `backdrop-filter: saturate(1.5)`. 
- **Spacing:** Use `spacing-8` (2.75rem) for internal padding to ensure the work "breathes."

### Frosted Navigation
- **Styling:** Fixed position at the top. `surface_container_lowest` at 70% opacity. 
- **Blur:** 32px backdrop blur. 
- **Interaction:** Active links should utilize a `primary` glow dot (4px x 4px) beneath the text rather than a bold weight change.

### Input Fields
- **Styling:** `surface_container_low` background. Bottom-border only using `outline_variant` at 30% opacity.
- **Focus State:** The border animates to 100% `primary` width from the center outward.

---

## 6. Do's and Don'ts

### Do
- **Do** use `spacing-20` and `spacing-24` for vertical section gaps. High-end design requires "wasteful" space.
- **Do** use `primary` (#b7c4ff) as a "light leak" (large, low-opacity radial gradients) in the background of the hero section.
- **Do** keep animations "weighted." Use `cubic-bezier(0.23, 1, 0.32, 1)` for all transitions to give a sense of premium inertia.

### Don't
- **Don't** use pure white (#FFFFFF) for body text. Use `on_surface` (#e2e2e2) to reduce eye strain on the deep black background.
- **Don't** use standard 12-column grids for everything. Offset your text blocks to the left or right to create a more dynamic, editorial flow.
- **Don't** use icons with varying stroke weights. All icons must match the `outline` token's perceived weight.