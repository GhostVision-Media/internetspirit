# Michael Hardy's ™ Internet ® Spirit © Web Browser! — Help & Information

![Internet Spirit Help](../assets/readme/help-documentation.png)

This help file is a GitHub-friendly companion to the main project README. It covers everyday browser controls, themes/skins, animated cursors, downloads, common troubleshooting, and the most important project links.

## Quick Navigation

- [Browser Basics](#browser-basics)
- [Tabs and Private Browsing](#tabs-and-private-browsing)
- [Bookmarks, History and Sessions](#bookmarks-history-and-sessions)
- [Downloads](#downloads)
- [Themes and Skins](#themes-and-skins)
- [Animated Cursors](#animated-cursors)
- [PNG Scrollbars](#png-scrollbars)
- [Startup Splash](#startup-splash)
- [Toolbar Sizes and States](#toolbar-sizes-and-states)
- [Web/PWA Build](#webpwa-build)
- [Troubleshooting](#troubleshooting)
- [Official Links](#official-links)

## Browser Basics

Use the main toolbar for Back, Forward, Reload/Stop, Home, New Tab, Private Tab, split view, page capture, sidebar, downloads, skins, and related commands. The omnibox accepts a website address or search text.

Use the menu strip for additional commands such as full screen, zoom, Find in Page, Browser Options, Search Engine Manager, Toolbar Designer, security-verification reset, Theme Store, About, and help links.

## Tabs and Private Browsing

Internet Spirit supports normal tabs, private tabs, closed-tab recovery, tab groups, and split-view controls. Website favicons and page titles are tracked so tabs remain easy to identify.

If a site asks to open a new browser window, supported requests can be redirected into a new Internet Spirit tab instead.

## Bookmarks, History and Sessions

Bookmarks and history are persisted locally. The sidebar provides quick access to browser data and session tools. Session restore can reopen your previous browsing state, and the closed-tab list can recover recently closed pages.

## Downloads

The Advanced Download Manager tracks active and completed downloads. Depending on download state, controls include Pause, Resume, Cancel, Open File, Show in Folder, Delete File, Pause All, Resume All, and Clear Completed.

Progress bars use the active skin/theme.

## Themes and Skins

The complete v2.2.0 assembled package contains 306 themes/skins. Built-in skins include Classic Blue Power Browser, Ghost Night, Ghost Ultimate, Carbon Fiber, Aurora Glass, and Windows XP Color Toolbar.

Desktop user themes may contain `skin.json`, optional `skin.css`, and image assets. ZIP installation is supported by the desktop theme engine.

For detailed authoring instructions, open [`SKIN-SDK.md`](SKIN-SDK.md).

Theme Store: https://internet-spirit.com/Theme-Store/

## Animated Cursors

Internet Spirit supports animated Normal, Link, Text, Busy, Drag, Horizontal Resize, and Vertical Resize cursors. Themes may use APNG, animated WebP, GIF, or frame sequences.

In v2.2.0, the normal operating-system pointer/hand is hidden while the animated skin cursor is active. Turn animated cursors off in Browser Options to return to normal system/CSS cursors.

## PNG Scrollbars

A v2.2.0 theme can provide PNG artwork for vertical and horizontal tracks, Normal/Hover/Active thumbs, directional buttons, and the scrollbar corner. Check that every path in the theme manifest points to an existing PNG file.

## Startup Splash

The startup splash is transparent, frameless, animated, and driven by the selected skin. Themes can add a dedicated `splash.css` and local image/animation assets.

Browser Options can disable the splash or change its timing.

## Toolbar Sizes and States

Toolbar size choices are:

```text
Small
Normal
Large
Extra Large
```

Each toolbar control can supply:

```text
normal.png
hover.png
hot.png
pressed.png
disabled.png
```

The Windows XP Color Toolbar theme also demonstrates XP-style hot tracking.

## Web/PWA Build

After assembling all split source/theme packages, rebuild the HTML5/PWA edition with:

```bash
npm run build:web
```

To serve it locally:

```bash
npm run serve:web
```

## Troubleshooting

### A theme is missing graphics

Confirm `skin.json` paths are correct and that all referenced files were copied with the theme. Reinstall/reapply the skin after fixing the files.

### The animated cursor has a normal pointer under it

Confirm you are running v2.2.0 or newer. The current build includes native pointer/hand suppression while the animated cursor system is enabled.

### Cursor position feels wrong

Check the theme's hotspot coordinates. The hotspot is the exact click point within the cursor image.

### Cursor is too large

Change the cursor size/scaling option in Browser Options. Smaller built-in cursor artwork is intended to reduce visual obstruction.

### Scrollbars are invisible or hard to see

Verify the track/thumb PNGs and use enough visual contrast between the thumb, track, and browser content.

### Web themes are missing after assembling the split package

Run `npm run build:web`. The generated `dist-web` folder is intentionally omitted from the split download to avoid duplicating the full 306-theme collection.

### A website verification challenge repeats

Use the browser's security-verification reset command, then reload the website. Verification services can also change behavior independently of Internet Spirit.

### Desktop build fails

Run `npm install` again, confirm a Node.js/npm version compatible with the Electron 43.x project toolchain, and make sure the target operating system has the packaging tools needed for that platform.

## Official Links

Official Web Site: https://internet-spirit.com/

Theme Store: https://internet-spirit.com/Theme-Store/

Microsoft Store publisher page: https://apps.microsoft.com/search/publisher?name=%C2%AENightWare+%C2%A9Studios%21++-++%28+Michael+Hardy+%29

Windows Store protocol:

```text
ms-windows-store://publisher/?name=®NightWare ©Studios!  -  ( Michael Hardy )
```

## Credits

Written, Created & Developed By **Michael James Hardy**

**®NightW@re ©Studios!  -  ( Michael Hardy )**

---

**Michael Hardy's ™ Internet ® Spirit © Web Browser! v2.2.0**
