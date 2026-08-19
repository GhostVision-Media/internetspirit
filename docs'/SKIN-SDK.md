# Michael Hardy's ™ Internet Spirit Web Browser!® Skin SDK

A skin is a directory containing `skin.json`, optionally `skin.css`, and any assets you want to reference from CSS. The browser can also install a complete skin from a ZIP file.

## Skin package layout

```text
MyUltimateSkin/
  skin.json
  skin.css
  assets/
    chrome.webp
    animated-header.gif
    back.png
    forward.png
    cursor.cur
    hand.cur
```

For ZIP installation, zip the folder or zip the files directly. The installer locates `skin.json`, extracts only files under that skin root, and rejects path traversal entries.

## skin.json

```json
{
  "id": "my-ultimate-skin",
  "name": "My Ultimate Skin",
  "author": "Your Name",
  "version": "1.0",
  "variables": {
    "--chrome-bg": "#152331",
    "--chrome-bg-2": "#22425e",
    "--accent": "#64d7ff",
    "--text": "#f5fbff",
    "--muted": "#9fb3c5",
    "--panel-bg": "#edf5fb",
    "--panel-text": "#142536",
    "--tab-active": "#ffffff",
    "--tab-active-text": "#153653",
    "--tab-inactive": "#1b3954",
    "--border": "#41617c",
    "--content-bg": "#ffffff",
    "--hover": "rgba(255,255,255,.15)",
    "--danger": "#bd3b46",
    "--radius": "6px",
    "--font": "\"Segoe UI\", sans-serif",
    "--cursor-default": "default",
    "--cursor-link": "pointer"
  }
}
```

## Advanced skin.css

`skin.css` loads after the base interface CSS. Relative asset URLs are rewritten to local `file:` URLs automatically.

```css
.chrome {
  background-image:
    linear-gradient(rgba(0,0,0,.2), rgba(0,0,0,.45)),
    url("assets/chrome.webp");
  background-size: cover;
}

.brand-orb {
  background-image: url("assets/animated-header.gif");
}
```

Animated GIF and WebP assets work anywhere Chromium accepts them in CSS.

## Replace toolbar graphics

```css
#back {
  background: url("assets/back.png") center/24px 24px no-repeat;
  font-size: 0;
}
#forward {
  background: url("assets/forward.png") center/24px 24px no-repeat;
  font-size: 0;
}
```

Useful selectors include:

- `#back`
- `#forward`
- `#reload`
- `#home`
- `#newTab`
- `#privateTab`
- `#splitToggle`
- `#captureBtn`
- `#sidebarToggle`
- `#downloadsToggle`
- `#skinQuick`

## Custom cursors

You can set cursors globally with advanced CSS:

```css
body { cursor: url("assets/cursor.cur"), default; }
button, a, .tab { cursor: url("assets/hand.cur"), pointer; }
```

You can also set `--cursor-default` and `--cursor-link` in the manifest to normal CSS cursor values.

## Themeable UI surfaces

The following are all CSS skin targets:

- title strip and brand area
- menu strip
- navigation toolbar
- omnibox
- favorites bar
- tabs and tab groups
- sidebar and sidebar icons
- status bar
- popup menus
- options/search/toolbar/about dialogs
- new-tab chrome container
- split-view controls
- toast notifications

## Recommendations

- Toolbar icons: 24x24 or 32x32 transparent PNG/WebP.
- Keep chrome textures reasonably small.
- Test at 100%, 125% and 150% display scale.
- Preserve readable contrast for normal, active and disabled controls.
- Prefer CSS animation for chrome effects; use GIF/WebP when the artwork itself must animate.

## v1.0.4 fully themed buttons and custom title bar

The Windows/Electron frame is disabled in v1.0.4. The top browser title row is now the draggable title bar, while menu buttons and Minimize/Maximize/Close are marked as interactive no-drag controls.

Every browser button can now inherit these skin variables:

- `--button-bg`
- `--button-bg-hover`
- `--button-bg-active`
- `--button-text`
- `--button-border`
- `--button-shadow`
- `--button-radius`
- `--button-font-weight`
- `--button-text-shadow`
- `--button-disabled-opacity`
- `--titlebar-button-bg`
- `--titlebar-button-hover`
- `--titlebar-button-text`
- `--titlebar-close-hover`

These variables theme both the button surface and its text. Advanced skins can still override individual controls with `skin.css` and PNG/WebP/GIF assets.


## v1.0.8 animated cursor engine

Michael Hardy's ™ Internet Spirit Web Browser!® can now render a skin-supplied animated cursor **over the browser chrome and inside web pages**. The browser uses a top-level cursor overlay and the guest preload reports pointer movement and cursor roles from each webview.

Supported animated image formats for `src` include formats Chromium can animate in an `<img>`, such as **GIF, animated WebP, and APNG**. The skin engine also supports deterministic **PNG/WebP frame sequences** through the `frames` array.

Add a `cursors` object to `skin.json`:

```json
{
  "cursors": {
    "enabled": true,
    "defaultSize": [40, 40],
    "frameMs": 80,
    "normal": {
      "src": "assets/cursors/normal.gif",
      "hotspot": [3, 2],
      "size": [40, 40]
    },
    "link": {
      "src": "assets/cursors/link.webp",
      "hotspot": [10, 3]
    },
    "text": {
      "frames": [
        "assets/cursors/text-01.png",
        "assets/cursors/text-02.png",
        "assets/cursors/text-03.png"
      ],
      "frameMs": 65,
      "hotspot": [20, 20]
    },
    "busy": { "src": "assets/cursors/busy.gif", "hotspot": [20,20] },
    "drag": { "src": "assets/cursors/drag.gif", "hotspot": [20,20] },
    "resizeEW": { "src": "assets/cursors/resize-ew.gif", "hotspot": [20,20] },
    "resizeNS": { "src": "assets/cursors/resize-ns.gif", "hotspot": [20,20] }
  }
}
```

### Cursor roles

- `normal` — default pointer
- `link` — links, buttons, clickable controls
- `text` — text fields, textareas, editable content
- `busy` — pages/controls reporting `wait` or `progress`
- `drag` — draggable/grab/move controls
- `resizeEW` — horizontal resize controls
- `resizeNS` — vertical resize controls

### Hotspots

`hotspot: [x, y]` identifies the exact click point inside the cursor image. For an arrow cursor the hotspot is normally near the top-left tip. For a busy ring or resize cursor it is normally near the center.

### Global user control

Users can turn all animated skin cursors on/off in **Tools > Options > Enable animated skin cursors**. When disabled, the browser immediately restores ordinary CSS/Windows cursor behavior without changing the selected skin.

### Built-in examples

v1.0.8 includes animated cursor packs for Classic Blue, Ghost Night, Ghost Ultimate, Carbon Fiber, and Aurora Glass. These provide working examples for all seven roles above.


## v1.0.12 Download Manager and Splash Skinning

The Download Manager and startup splash use the same skin manifest as the browser chrome. Add any of these variables under `variables` in `skin.json`:

- `--progress-track`
- `--progress-fill`
- `--progress-glow`
- `--progress-text`
- `--download-card-bg`
- `--download-card-border`
- `--download-complete`
- `--download-warning`
- `--download-error`
- `--splash-panel`

`--progress-fill` can be a CSS gradient. The existing `skin.css` can fully restyle `.download-progress-track`, `.download-progress-fill`, `.download-card`, and the Download Manager dialog.

### Optional splash.css

A skin may now contain an optional `splash.css` beside `skin.json`. Internet Spirit loads it only into the startup splash. Relative `url(...)` references are rewritten to that skin folder, so user themes can provide PNG, WebP, GIF, or other local splash artwork.

Example:

```css
.splash-shell {
  background: linear-gradient(rgba(0,0,0,.45),rgba(0,0,0,.72)),
              url("assets/splash-background.png") center/cover no-repeat;
}
.progress-energy {
  background: url("assets/progress-fill.gif") center/cover repeat-x;
}
```

This allows the splash background and progress fill to be image-based and animated while preserving the normal skin-variable fallbacks.


## v1.0.13 modal-dialog cursor layer and compact cursor sizing

Internet Spirit now renders its animated cursor as a manual HTML Popover. Popovers are
placed in Chromium's top layer, so the cursor can be re-promoted above modal `<dialog>`
windows such as Browser Options, Search Engine Manager, Toolbar Designer, Download
Manager, and About.

Built-in cursor artwork now uses a 28×28 compact base size instead of the older 40×40
artwork. Recommended user-skin sizes are 22–32 pixels.

Users can select Tiny, Compact, or Standard cursor scaling from Browser Options.

A cursor manifest still uses role-specific `size` and `hotspot` values. Internet Spirit
multiplies both by the selected cursor scale so hotspots remain accurate.
