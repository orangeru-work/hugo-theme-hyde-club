# hugo-theme-hyde-club

A Hugo theme for small clubs and community organizations, extending [spf13/hyde](https://github.com/spf13/hyde).

## Features

- Responsive sidebar: full flex layout on desktop, compact dropdown on mobile (480px breakpoint)
- PWA support (manifest, apple-mobile-web-app meta tags)
- `private` front matter param to noindex pages
- Event schema.org structured data (triggered by `event: true` in front matter)
- Hook partials for site-specific extensibility

## Hook Partials

Override these in your site's `layouts/partials/` to extend without modifying the theme:

| Hook | Purpose |
|---|---|
| `hook_head_end.html` | Injected at end of `<head>` (e.g. analytics, extra CSS) |
| `hook_sidebar_icons.html` | Icons/actions in the sidebar (e.g. login button, notification bell) |

## Params

| Param | Description |
|---|---|
| `logo` | Path to logo image shown in sidebar |
| `themeColor` | Hyde theme color class (e.g. `theme-base-0f`) |
| `description` | Site description shown in meta and sidebar |
| `copyright` | Copyright text (defaults to current year) |
| `sidebarBgColor` | Solid sidebar fallback color |
| `sidebarLinkColor` | Optional link color for content links (defaults to `sidebarBgColor`) |
| `sidebarGradient` | Optional sidebar gradient config (see below) |

## Sidebar gradient config

```yaml
Params:
  sidebarGradient:
    type: linear # linear | radial
    startColor: "#516d21" # optional
    endColor: "#2e3f13"   # optional
```

Behavior:

- `type: linear` applies a right-to-left gradient on desktop and bottom-to-top on mobile.
- `type: radial` applies a radial gradient centered on the logo position.
- `startColor` and `endColor` default to the active theme palette when omitted.
- If `sidebarGradient` is unset, the sidebar uses `sidebarBgColor` (or Hyde defaults if that is unset).

## CSS Variable

The mobile dropdown menu background defaults to `rgba(0,0,0,0.85)`. Override with:

```css
:root {
  --sidebar-mobile-menu-bg: rgba(32, 19, 12, 0.95);
}
```

## Usage

In your site's `hugo.yaml`:

```yaml
module:
  imports:
    - path: github.com/orangeru-work/hugo-theme-hyde-club
```

In your site's `go.mod`:

```
require github.com/orangeru-work/hugo-theme-hyde-club v0.1.0
```
