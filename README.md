# Darooghe — Design System Audit for Figma

Darooghe checks every component in a Figma frame against **your** design system. It shows exactly what's off and how to fix it, stamps clean frames as **verified** for handoff, and notices if they change afterwards.

**Version 2.13.0** · [Figma Community](#) · Free

---

## Install

- **From Figma Community** (recommended): open the Community page and click *Open in…* / *Try it out*.
- **From this repository** (development copy):
  1. Download or clone this repository.
  2. In Figma Desktop, go to **Plugins → Development → Import plugin from manifest…** and choose `manifest.json`.

## Set up (once per library)

Darooghe needs no token and no account. It learns your design system directly from the library file:

1. Open your design system **library file** in Figma.
2. Run Darooghe and open **Settings → Register this file as a library**. Only published components are registered, so publish the library first.
3. Repeat for each library you use, for example icons or illustrations.

Re-register a library after you publish changes to it. Registered libraries are stored on your device and work in every file.

## Use

1. **Select a frame** on the canvas (Shift-select to audit several), or pick one from the list.
2. Press **Run audit**.
3. The summary shows the compliance %, then a split bar: on system · accepted exceptions · modified · off system.
4. **Issues** are grouped by type, and each one shows the exact value that changed and how to fix it. The same issue repeated across instances is one row with a count («×30 · on 30 screens»), with Accept all, Select on canvas and Show. Click the arrow to jump to the layer.
5. **A section or several frames** get one verdict and a short list of screens (failed first; frames without components fold into one line). Click a screen to see only its issues.
5. Fix the issues and re-audit until the frame passes.

### What it finds

| Code | Meaning |
|---|---|
| `MOD` | A design system component with hard-coded overrides (colour, gradient, removed fill, font, stroke, spacing, radius, effects, opacity), or a nested part swapped to a component outside your design system |
| `LOC` | A local component instead of a library component |
| `EXT` | A component from a library you haven't registered |
| `UNP` | An internal part (`_Name`) used directly |
| `MIS` | An instance whose main component is gone |
| `DET` | A layer detached from a design system component (detached from anything else, it's just a frame) |

Values from variables or styles are fine, and so are overrides on hidden layers. Text content and layout-driven size changes are ignored. Sections are audited with everything inside them.

**Export CSV** saves the whole audit (issues, accepted exceptions and passed instances, with Figma links).

**Warnings (`RAW`)** — layers outside components with a raw colour or text without a text style appear in a Warnings tab. They don't block verification. Hand-drawn vectors inside a group (badges, illustrations) aren't checked, and in a section, frames without components (labels, notes) are skipped.

### Handoff
- **Verified stamp**: a frame with zero issues gets stamped. If it changes later, the stamp turns into *Changed since verification*. Copy edits and resizing don't count.
- **Ready for dev**: mark a verified frame ready in one click. Developers see the stamp in Dev Mode.
- **History**: every audited frame keeps a log of who audited it, when, and every change since (what changed, before → after, and the editor's name when they had Darooghe open).
- **Jump to the problem**: click the layer name in an override (e.g. `Vector`) to select it, or a verification card to select the frame. The view only moves when the target isn't already on screen, and glides instead of jumping.
- **Exceptions**: accept an intentional deviation (any issue type) with a note. It moves to the *Exceptions* tab and stays accepted until the layer really changes. Tick several rows to accept them at once.
- **Exceptions report**: export every accepted exception in the file as CSV.

## Privacy

Audits run entirely inside Figma. Darooghe never sends your designs anywhere. The only network request is the optional newsletter sign-up in Settings, which sends only the email you enter, through Formspree.

## Feedback

Questions, bugs or ideas: amirsaharkhiz72@gmail.com

---

© Amir Saharkhiz. All rights reserved. You may use the plugin freely; the source code is published for transparency and may not be redistributed or sold without permission.
