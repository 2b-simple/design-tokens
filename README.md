# @2b-simple/design-tokens

Shared [Tailwind CSS v4](https://tailwindcss.com/) design tokens for **cube-erp** micro-frontends and related apps.

## Install

```bash
pnpm add -D @2b-simple/design-tokens
```

**Peer dependency:** `tailwindcss` `^4.0.0`.

## Usage

Import the stylesheet so CSS custom properties and Tailwind `@theme` mappings are available to your build:

```css
@import "tailwindcss";
@import "@2b-simple/design-tokens/main.css";

/* Your app sources (add @source for UI libraries you consume) */
@source "../src";
```

After import, utilities such as `bg-background`, `text-foreground`, `border-border`, `bg-primary`, `text-primary-foreground`, `text-muted-foreground`, `ring-ring`, `text-destructive`, `bg-success`, and `text-info` resolve from the tokens defined in `main.css`.

Prefer **semantic** utilities (`bg-muted`, `text-foreground`) over hard-coded palette classes (`bg-slate-100`, `text-gray-600`) so light/dark mode and brand themes stay consistent.

## Theme switching

### Light / dark (`[data-color-scheme]` / `.dark`)

`main.css` mirrors shadcn-style tokens for `:root` and for dark mode via `[data-color-scheme="dark"]` and `.dark` descendants. Apply dark mode by toggling `class="dark"` on `<html>` or `body`, or by setting `data-color-scheme="dark"` on an ancestor, matching the selectors shipped in this package.

### Brand primary (`[data-theme]`)

Primary ramp variables (`--primary`, `--primary-foreground`, `--primary-25` … `--primary-950`) switch when an ancestor has `data-theme`, for example `data-theme="default"` (violet), `credence` (teal), `wangkanai` (lime), `rose-theme`, `olive-theme`, `forest-theme`, or `garnet-gradient-theme`. See `main.css` for the authoritative list and mappings.

## Semantic tokens (quick reference)

| Role | CSS variables | Example utilities |
|------|----------------|-------------------|
| Page | `--background`, `--foreground` | `bg-background`, `text-foreground` |
| Surfaces | `--card`, `--popover`, `--muted` | `bg-card`, `bg-muted`, `text-card-foreground` |
| Brand | `--primary`, `--primary-foreground` | `bg-primary`, `text-primary`, `border-primary` |
| Secondary text | `--muted-foreground` | `text-muted-foreground`, `text-muted-foreground/80` |
| Borders / inputs | `--border`, `--input` | `border-border`, `border-input` |
| Focus ring | `--ring` | `ring-ring`, `focus-visible:ring-ring/30` |
| Danger | `--destructive`, `--destructive-foreground` | `text-destructive`, `bg-destructive/10` |
| Status | `--success`, `--info`, `--warning` (+ foregrounds) | `bg-success`, `text-info`, `text-warning` |

The package also exposes a full **primary** shade scale as Tailwind colors: `bg-primary-500`, `text-primary-700`, etc., via `@theme inline` in `main.css`.

## Package contents

- **Published file:** `main.css` (see `files` in `package.json`).
- **Entry:** `@import "@2b-simple/design-tokens/main.css"` or `"./main.css"` from the package root.

## Developing & releasing

1. Edit `main.css` and verify consuming apps (build + visual regression if applicable).
2. Bump `version` in `package.json`.
3. Publish to npm with appropriate release notes when token changes affect consumers.

## License

MIT — see repository metadata.
