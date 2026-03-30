# Design System Specification: The Command Line Editorial

## 1. Overview & Creative North Star
**Creative North Star: "The Brutalist Architect"**

This design system rejects the "softness" of modern consumer interfaces in favor of the raw, high-contrast utility of early computing. It is an intentional homage to the Command Line Interface (CLI), reimagined as a high-end editorial experience. We move beyond the "hacker aesthetic" by applying rigorous typographic hierarchy and structured asymmetry. 

Instead of depth via shadows or rounded containers, we define space through **Rigid Geometry** and **Tactile Borders**. The interface does not "float" above a background; it is carved into it. Every pixel is intentional, every line a structural necessity.

## 2. Colors & Surface Logic
The palette is rooted in absolute blacks and high-energy phosphors. It utilizes a sophisticated layering of dark tones to simulate the "scanline" depth of a CRT monitor.

### The Phosphor Palette
*   **Primary (`#00E639`):** Our "Green Screen" phosphor. Reserved for high-priority actions, success states, and primary prompt symbols (`>`).
*   **Secondary (`#FFBA43`):** The "Amber Alert." Used for warnings, secondary data visualizations, or to highlight nested code structures.
*   **Surface (`#131313`):** The base terminal shell. 

### The "No-Shadow" Mandate
Traditional drop shadows are strictly prohibited. Depth is achieved via:
1.  **Tonal Nesting:** Use `surface_container_lowest` (#0E0E0E) for the main background and `surface_container` (#201F1F) for active window shells.
2.  **ASCII-Inspired Dividers:** Use the `outline_variant` (#3B4B37) to create hair-line borders (1px) that mimic the box-drawing characters of DOS-era interfaces.

### Surface Hierarchy
*   **Deep Background:** `surface_dim` (#131313)
*   **Terminal Windows:** `surface_container` (#201F1F) with a 1px solid `outline` (#84967E) border.
*   **Code Blocks/Inputs:** `surface_container_highest` (#353534).

## 3. Typography
The system uses a mono-spaced logic to maintain the "grid-aligned" feel of a terminal. While the tokens mention Inter/Space Grotesk, for this specific editorial direction, we override these with **JetBrains Mono** or **Fira Code** to ensure every character occupies a predictable block of space.

*   **Display (Display-LG/MD):** Used for massive, "glitch-art" style headers. Letter-spacing should be set to `-0.05em` to create a dense, architectural block of text.
*   **Headlines:** Used for section titles. Always uppercase. Prepend with a `//` or `#` comment syntax to reinforce the CLI theme.
*   **Body:** High-readability monospace. Line height should be generous (1.6x) to prevent the "wall of text" effect common in actual terminals.
*   **Labels:** Small, high-contrast (`primary` or `secondary`) text used for metadata and status indicators (e.g., `[ STATUS: OK ]`).

## 4. Structural Integrity (Elevation & Depth)
In this system, "Elevation" is a misnomer. We use **Structural Inset** instead.

*   **The Layering Principle:** Rather than lifting an element with a shadow, we "cut" into the surface. An active modal is simply a container with a `primary` (#00E639) 1px border and a slightly lighter `surface_bright` (#3A3939) background.
*   **The "Ghost Border":** For non-interactive grouping, use `outline_variant` (#3B4B37) at 20% opacity. This creates a "suggestion" of a container without breaking the brutalist flow.
*   **The Scanline Overlay:** For high-end hero sections, use a repeating linear gradient overlay to simulate CRT scanlines (1px lines, 4px gap, 3% opacity).

## 5. Components

### Buttons (The "Command" Variant)
*   **Primary:** Solid `primary_container` (#00FF41) with `on_primary` (#003907) text. Rectangular (0px radius). On hover, invert colors.
*   **Secondary:** 1px `primary` border, transparent background. Text is `primary`.
*   **Tertiary:** Text-only, prepended with a cursor `_` that blinks on focus.

### Input Fields (The "Prompt")
*   **Style:** A simple underline using `primary` or a full box with `surface_container_lowest`. 
*   **State:** The active state must include a "Block Cursor" (a solid rectangle of `primary` color) at the end of the text string.
*   **Error:** Replace the border with `error` (#FFB4AB) and prefix the helper text with `[!] ERROR:`.

### Cards & Lists (The "Data Grid")
*   **No Dividers:** Use the Spacing Scale (specifically `spacing-8` or `spacing-10`) to create "voids" between content blocks.
*   **Selection:** An active list item should have a `primary` background with the text inverted, mimicking a terminal text selection.

### ASCII Elements
*   **Progress Bars:** `[||||||||||.....] 65%`
*   **Separators:** Use strings of hyphens `---------` or equal signs `=========`.

## 6. Do's and Don'ts

### Do:
*   **Do** use intentional asymmetry. Align a small block of text to the far right while the headline stays left to mimic disparate terminal outputs.
*   **Do** embrace the 0px border radius. Every corner must be sharp and uncompromising.
*   **Do** use color to denote "System State." Amber for warnings, Green for active/ready, and Grey for inactive/legacy data.

### Don't:
*   **Don't** use soft transitions or blurs. Transitions should be "instant" or "stepped" (e.g., a 2-frame blink) rather than a 300ms ease-in-out.
*   **Don't** use drop shadows. If an element needs to stand out, give it a thicker 2px border or a high-contrast background shift.
*   **Don't** use imagery with soft edges. Photos should be treated with a high-contrast bitmask or dithered filter to match the UI's grit.

## 7. Spacing Scale Implementation
The spacing scale is mathematical and rigid. Use `0.9rem` (spacing-4) as the base "character width" unit. All layout margins should be multiples of this unit to ensure the typography feels locked into a global grid, even if the layout is asymmetrical.