# GitHub Colorblind themes for Pi

Two adaptations of GitHub's Light Colorblind and Dark Colorblind (Beta) themes:

- `github-colorblind-dark.json`
- `github-colorblind-light.json`

## Use

Run `/reload`, then open `/settings` → **Theme** and select either theme.
Your current theme setting has not been changed.

To follow your terminal's appearance, set this in `~/.config/pi/settings.json`
(light theme first, dark theme second):

```json
{
  "theme": "github-colorblind-light/github-colorblind-dark"
}
```

Merge that property into the existing settings; do not replace the entire file.

Pi themes do not set the terminal's default background. For the closest match,
use a terminal background of `#0d1117` for dark or `#ffffff` for light. The themes
set explicit foreground and panel colors; HTML exports also use these canvas
colors. Contrast measurements below assume those terminal backgrounds.

## Source analysis

GitHub replaces the entire green scale with its blue scale and the entire red
scale with its orange scale. This affects not just UI status indicators, but
syntax, diff highlighting, and ANSI colors. The important distinction is
**blue for success/additions** and **orange for errors/deletions**, rather than
red versus green. Purple remains the function/entity accent; strings and
constants use different blue shades. Gray UI surfaces remain relatively quiet.

| Role | Dark | Light |
| --- | --- | --- |
| Canvas | `#0d1117` | `#ffffff` |
| Main text | `#c9d1d9` | `#24292f` |
| Secondary text | `#8b949e` | `#57606a` |
| Links / success | `#58a6ff` | `#0969da` |
| Errors | `#d47616` | `#aa5500` (adapted) |
| Keywords / operators | `#ec8e2c` | `#aa5500` (adapted) |
| Functions | `#d2a8ff` | `#7f4eda` (adapted) |
| Variables | `#fdac54` | `#8a4600` |
| Strings | `#a5d6ff` | `#0a3069` |
| Numbers / types / inline code | `#79c0ff` | `#0550ae` |
| Added diff lines | `#a5d6ff` | `#0550ae` |
| Removed diff lines | `#fdac54` | `#6f3800` |

## Pi mapping and deliberate differences

- Syntax follows GitHub's VS Code token mapping, collapsed into Pi's smaller
  token set. Types use the blue support/constant role, and operators use keywords.
- Headings and inline code use GitHub's blue Markdown roles. List markers and
  blockquotes follow its orange and blue (remapped green) roles respectively.
- User messages and pending tools use the subtle neutral canvas. Successful
  tools use the success tint, errors the danger tint, and custom messages the
  purple done tint.
- Pi accepts opaque RGB colors, not RGBA backgrounds. Translucent Primer colors
  are composited against the corresponding canvas, with channels rounded to the
  nearest integer. Selection uses `accent.muted`; dark search uses
  `searchKeyword.hl`; other tinted panels use the corresponding `*.subtle` token.
- Light orange is darkened from `#b35900` to `#aa5500`, and light function purple
  from `#8250df` to `#7f4eda`, to preserve at least 4.5:1 syntax contrast on all
  message/tool panels. Light comments use `fg.muted` (`#57606a`) instead of the
  upstream syntax gray (`#6e7781`) for the same reason.
- Tool output uses main text rather than dimmed text, improving long-output
  readability. Dim text and decorative borders retain lower-contrast upstream
  grays. Normal borders use a stronger gray than GitHub's thin GUI separators.
- Pi-specific thinking borders use gray, blue, purple, yellow, then orange.
  These levels have no direct GitHub equivalent.
- Pi cannot override subprocess ANSI palettes through theme JSON. The palette
  mapping applies to Pi-owned UI, Markdown, syntax, and tool diff colors.

## Validation

Both themes pass Pi 1.5.2's own schema validator and runtime loader in truecolor
and 256-color modes, resolving all 56 color tokens. The source alpha-compositing
calculations were checked separately.

Minimum WCAG contrast ratios, calculated from the actual 24-bit RGB values
across the canvas and every message/tool panel:

| Text category | Dark | Light |
| --- | --- | --- |
| Body / secondary / tool output | 5.13:1 | 5.62:1 |
| All syntax roles | 5.13:1 | 4.60:1 |
| Diff foregrounds / context | 5.13:1 | 5.62:1 |
| Search match text | 5.74:1 | 13.60:1 |
| Selected item text | 6.53:1 | 10.54:1 |

These checks do not cover dim text, decorative borders, arbitrary terminal
backgrounds, ANSI-colored subprocess output, or 256-color approximation.
They are not a guarantee of accessibility for every form of color vision
 deficiency. Pi's existing diff signs and status labels remain important
non-color cues. No interactive visual review was performed.

## Provenance

- [GitHub VS Code Theme](https://github.com/primer/github-vscode-theme), version
  6.3.5, source commit `cd78e5e4e7bcf132a6f428ae0f32264bb1b729cf`.
  The source `src/theme.js` defines the syntax/Markdown mappings and `src/colors.js`
  selects the Primer palettes.
- [`@primer/primitives` 7.10.0](https://www.npmjs.com/package/@primer/primitives/v/7.10.0),
  the exact version used by that theme, specifically
  `dist/json/colors/dark_colorblind.json` and `light_colorblind.json`.
- Upstream MIT notices are retained in `LICENSE.github-colorblind.txt`.

These are unofficial adaptations, not themes published or endorsed by GitHub.
