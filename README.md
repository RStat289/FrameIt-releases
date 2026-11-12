# FrameIt

A fast, tidy screenshot tool for Windows. Press a key, pick what you want, and FrameIt files it into a folder for
the day, ready to annotate, pin, copy or drag wherever it needs to go.

**[Download FrameIt for Windows](https://github.com/RStat289/FrameIt-releases/releases/latest/download/FrameIt-win-Setup.exe)**
&nbsp;·&nbsp; [All versions](https://github.com/RStat289/FrameIt-releases/releases)

Windows 10 (version 2004 or later) or Windows 11, 64-bit.

## Install

1. Download **FrameIt-win-Setup.exe** using the link above and run it.
2. Windows will show a blue **"Windows protected your PC"** notice, because the installer isn't code-signed.
   Choose **More info**, then **Run anyway**.
3. If your PC doesn't have the .NET 10 Desktop Runtime, the installer offers to install it for you. Say yes.

FrameIt installs for your user account only (no administrator rights needed), adds Start menu and desktop
shortcuts, and opens when it's done.

## What it does

**Capture**
- **Region capture** with a frozen screen: hover to snap to a window or panel, or drag any rectangle. A magnifier
  shows the exact pixels, position and colour under the cursor.
- **Full screen**, **active window**, **repeat last region**, and **delayed capture** for menus and hover states.
- Optional mouse pointer in the shot, and a soft shutter sound to confirm each capture.

**Organise**
- Every capture is saved as a PNG into a folder for that day, automatically.
- A gallery shows your captures day by day, with search across everything.
- Drag captures straight out of the gallery into an email, chat or document.
- File names can include the date, time, and the window or app you captured.

**Edit**
- Arrows, lines, rectangles, ellipses, freehand pen, text and numbered steps.
- Everything you draw stays movable: select it, drag it, reshape it, recolour it, or delete it.
- Highlight, blur and pixelate; crop, resize, borders and drop shadows.

**Extras**
- **Pin** a capture on top of your other windows for reference.
- **Copy text** out of any part of the screen or an image (uses Windows' built-in text recognition, on your PC).
- **Colour picker**: click any pixel to copy its hex code.
- Open a capture in PhotoCraft or another editor with one click.

## Getting started

FrameIt lives in the system tray, next to the clock. Closing its window doesn't quit it, so the hotkeys keep working.

| Action | Default |
|---|---|
| Capture a region | `PrintScreen` |
| Edit the last capture | `Ctrl` + `PrintScreen` |
| Open FrameIt | Double-click the tray icon |
| Everything else | Right-click the tray icon |

Every hotkey can be changed, and more can be added, under **Settings > Hotkeys**.

While selecting a region: **click** captures the highlighted window, **drag** captures a custom area, the
**arrow keys** nudge the cursor one pixel, **Space** captures everything, and **Esc** cancels.

> **On Windows 11**, the PrintScreen key may be reserved for the Snipping Tool. If FrameIt says it couldn't
> register the hotkey, turn off *Settings > Accessibility > Keyboard > Use the Print screen key to open screen
> capture*, or choose a different hotkey in FrameIt.

## Updates

FrameIt keeps itself up to date. It checks for a new version shortly after it starts and a few times a day,
downloads it in the background, and lets you know when it's ready. Click the notification to restart into the new
version, or just carry on: it installs the next time FrameIt starts.

To check by hand, right-click the tray icon and choose **Check for updates**. Your version number is shown there too.

## Privacy

Your screenshots stay on your PC. FrameIt doesn't upload captures, doesn't have accounts, and doesn't collect
usage data. The only time it goes online is to check this page for a new version.

## Uninstall

Open **Windows Settings > Apps > Installed apps**, find **FrameIt**, and choose **Uninstall**. Your saved
screenshots are left untouched.

## Questions and problems

Found a bug or want to suggest something? [Open an issue](https://github.com/RStat289/FrameIt-releases/issues)
and include your FrameIt version and what you were doing when it happened.

---

This repository hosts FrameIt's installers and updates only. It doesn't contain the source code.
