# FrameIt

A Windows screenshot and screen-recording utility, inspired by ShareX.

- **Region capture** with a global hotkey, modelled on ShareX: hover to highlight the window or control under the
  cursor and click to capture it, or drag a rectangle for a custom area. A magnifier shows the pixels, position
  and colour under the cursor.
- **Capture sound**: a short shutter click confirms each capture (can be turned off in Settings).
- **Daily folders**: every capture is saved as a PNG in `<save folder>\<date>\`, and a new folder is created each day.
- **Basic editor**: crop, resize, pen, line, arrow, rectangle, ellipse, text, highlight, blur, undo/redo.
- **Adjustable hotkeys** for capture, edit last capture, and open the screenshot folder.

No uploading: everything stays on your PC.

## Build and run

Requires Windows 10 (version 2004 or later) or 11 and the [.NET 10 SDK](https://dotnet.microsoft.com/download).

```
dotnet run -c Release
```

To produce a single `FrameIt.exe` in the `publish` folder, run `build.bat`.

## Giving it to other people

`release.bat 1.0.0` builds an installer (`FrameIt-win-Setup.exe`) and publishes it to a public releases
repository; installed copies then update themselves. See [RELEASING.md](RELEASING.md) for the one-time setup.

## Using it

The main window is dark-themed, with the actions in a sidebar and a card gallery of your captures, one day at a
time. Use the arrows or the drop-down in the header to change day. Double-click a card to edit it; right-click for copy, show in File Explorer and delete (to the Recycle Bin).

**Search** (the box in the header, or `Ctrl+F`) finds captures by file name or date across every day; `Esc` clears
it. The day list also has an **All captures** entry. Both show the newest 600. You can **drag** one or more
selected cards out of the gallery into an email, chat, folder or document.

Closing the window hides it to the system tray and the app keeps running, so the hotkeys still work.
Double-click the tray icon to bring the window back, or right-click it for the menu. Use **Exit** to quit.
When started with Windows, the app starts in the tray without showing the window.

| Action | Default hotkey |
|---|---|
| Capture region | `PrintScreen` |
| Capture full screen (the monitor the cursor is on) | none |
| Capture active window | none |
| Repeat last region | none |
| Capture after delay | none |
| Pick a colour from the screen | none |
| Copy text from the screen | none |
| Edit last capture | `Ctrl+PrintScreen` |
| Open screenshot folder | none |

**Capture after delay** counts down (5 seconds by default, changeable in Settings) and then opens the region
overlay with the screen frozen, so open menus and hover effects can be captured. Click the countdown to cancel.
Settings also has an option to include the mouse pointer in captures.

**Recording** (sidebar **Record** button, tray menu, or hotkeys you set): choose **video (MP4)** or **GIF**, select
the area with the same overlay as a screenshot, and recording starts. A red outline marks the area and a small bar
beside it shows the time with **Stop** and **Discard**. Recordings are saved in the day's folder and appear in the
gallery with a VIDEO or GIF badge; double-click opens them in FrameIt's viewer. Recording uses [FFmpeg](https://ffmpeg.org/). FrameIt
uses a copy already on the PC if it finds one, and otherwise offers to download it (about 110 MB) the first time.
On the **Recording** tab in Settings you can turn on **system audio** (what the PC is playing) and the
**microphone** for videos, and hide the **mouse pointer**.

The **viewer** plays videos with a seek bar (`Space` plays and pauses, the arrow keys step a second) and shows GIFs
animated. For videos it can **trim** the start and end, **remove the sound**, **save a frame** as a screenshot
(which opens in the image editor), and **export a GIF**. Changes are applied when you save.

The viewer has the picture editor's drawing tools: **Select**, **Pen**, **Line**, **Arrow**, **Rectangle**,
**Ellipse**, **Text**, **Step** and **Highlight**, with the same colour, width, size, fill and text-background
options, and undo/redo (`Ctrl+Z`, `Ctrl+Y`). Drawing pauses the video. With Select you can move, reshape, recolour
and delete (`Delete`) what you drew, and double-click text to change its words.

Everything drawn gets a row on the small **timeline** under the seek bar. A new item shows for the whole video;
drag its bar to move it in time, drag the bar's ends to change when it appears and disappears, or select it and use
**Show from here**, **Show until here** and **Whole video** in the options bar. With more than four items the
mouse wheel scrolls the rows. What you drew becomes part of the picture when you save or export a GIF, and can't be
edited after that.

The **FilmCraft** button opens the saved video in FilmCraft. It looks in `C:\Program Files\ArtCraft\FilmCraft`
and, if it isn't there, offers to locate it or to open its download page
(https://getartcraft.com/apps/filmcraft); the path is remembered and can be changed on the
**Recording** tab in Settings.

**Screen tools** (sidebar button, tray menu, or their hotkeys):

- **Pick a colour:** click any pixel on the frozen screen; its hex code (for example `#3B82F6`) is copied.
- **Copy text:** select an area and the text in it is recognised, copied, and shown in a window. Text recognition
  is Windows' own and runs on your PC. It is also on a capture's right-click menu and the editor's **Read text** button.

**File names** follow a pattern set in Settings (default `Screenshot_{date}_{time}`); `{window}` and `{app}` add the
active window's title and program name. **Clean-up** (off by default) moves a day's captures to the Recycle Bin
once all of them are older than the number of days you set.

While selecting a region:

| Input | Effect |
|---|---|
| Click | Capture the highlighted window, control or monitor |
| Drag | Capture a custom rectangle |
| Arrow keys | Move the cursor 1 px (`Shift` = 10 px) |
| Mouse wheel | Change the magnifier's zoom area |
| `Enter` | Capture the highlighted area |
| `Space` | Capture everything (all monitors) |
| `1`-`9` | Capture that monitor |
| `` ` `` | Capture the monitor under the cursor |
| `Esc` or right-click | Cancel |

Change hotkeys, the save folder and the daily folder name under **Settings**. The folder name is a .NET date
format (default `yyyy-MM-dd`); use `/` for nested folders, for example `yyyy/MM/dd`.

Settings are stored in `%AppData%\FrameIt\settings.json`.

### Windows 11 and the PrintScreen key

Windows 11 can reserve `PrintScreen` for the Snipping Tool. If the app reports that it could not register the
hotkey, turn off **Settings > Accessibility > Keyboard > Use the Print screen key to open screen capture**, or
pick a different hotkey.

## Editor

Three bars sit above the image: file actions and zoom, the tools, and the options for the selected tool
(colour presets, line width or text size) with a one-line hint.

Everything you draw (pen, line, arrow, rectangle, ellipse, text) stays a separate object until the window is
closed. With the **Select** tool you can click one to select it, drag to move it, press `Delete` to remove it,
change its colour, width or text size from the options bar, and double-click text to edit it. Saving draws the
objects into the image file; they are not editable again after the editor is reopened. Highlight and blur change
the screenshot itself, underneath anything drawn on top.

More editor tools:

- **Step:** click to drop numbered markers (1, 2, 3...) for how-to screenshots.
- **Fill** (rectangle and ellipse) and **Background** (text) are toggles in the options bar. With Background on,
  **Plate colour** sets the colour behind the text: automatic, a preset, or any custom colour.
- **Pixelate** turns an area into blocks, as an alternative to blur.
- **Reshape:** with the Select tool, drag the square handles on a line, arrow, rectangle or ellipse.
- **Frame:** adds a border in the current colour (1, 3 or 8 px) or a drop shadow around the whole picture.
- **Open in:** lists the ArtCraft programs installed on this PC, plus the default image viewer and any program you pick.

The **Pin** button (also on the gallery's right-click menu and the tray menu) floats the image in a small
always-on-top window: drag to move, mouse wheel to resize, right-click for copy, save, opacity and close,
double-click or `Esc` to close.

The **PhotoCraft** button opens the saved image in PhotoCraft. It looks for PhotoCraft in its default
install folder, `C:\Program Files\ArtCraft\PhotoCraft`. If it isn't there, a window offers to locate it or to open
its download page (https://getartcraft.com/apps/photocraft). The path is remembered and can be changed in Settings. When you save in PhotoCraft and switch back, the
editor reloads the image (unless you have unsaved edits in the editor).

### Shortcuts

`Ctrl+S` save, `Ctrl+Shift+S` save as, `Ctrl+C` copy, `Ctrl+Z` undo, `Ctrl+Y` redo, `Ctrl+mouse wheel` zoom,
`Ctrl+0` actual size. In the text tool, `Ctrl+Enter` or clicking away finishes the text and `Esc` cancels it.

## Layout

| File | Purpose |
|---|---|
| `src/Program.cs` | Entry point, single-instance check |
| `src/TrayContext.cs` | Tray icon, menu, capture workflow |
| `src/MainForm.cs` | Main window: sidebar actions and day browser |
| `src/GalleryView.cs` | Card gallery control used by the main window |
| `src/Theme.cs` | Dark theme colours, fonts, rounded button, menu/toolbar renderer |
| `src/HotkeyManager.cs` | Global hotkey registration |
| `src/RegionOverlayForm.cs` | Region selection overlay |
| `src/WindowFinder.cs` | Finds the windows the overlay can snap to |
| `src/CaptureSound.cs` | Shutter sound played after a capture |
| `src/CaptureStore.cs` | Screen grab, daily-folder saving, app icon loading |
| `assets/FrameIt.ico` | App icon (16 to 256 px) |
| `src/EditorForm.cs` | Image editor and resize dialog |
| `src/Annotation.cs` | A drawn object in the editor: drawing, hit-testing, moving |
| `src/PinForm.cs` | Pinned always-on-top image window |
| `src/CountdownForm.cs` | On-screen countdown for delayed capture |
| `src/TextRecognizer.cs` | Text recognition using Windows' built-in OCR |
| `src/TextResultForm.cs` | Window showing recognised text |
| `src/CaptureCleanup.cs` | Optional removal of old captures |
| `src/ScreenRecorder.cs` | Finds or downloads FFmpeg; runs a video or GIF recording |
| `src/AudioRecorder.cs` | Captures system audio and the microphone during a recording |
| `src/VideoForm.cs` | Viewer and editor for videos and GIFs: drawing tools, trim, mute, frame grab and GIF export |
| `src/VideoItems.cs` | Things drawn on videos: the timed item, the FFmpeg overlay, the item timeline and the text dialog |
| `src/VideoText.cs` | Empty (its code moved to `VideoItems.cs`); can be deleted |
| `src/RecordingForms.cs` | Recording outline, control bar, and the FFmpeg prompt |
| `src/Updater.cs` | Update check, download and restart (Velopack) |
| `src/PhotoCraftPromptForm.cs` | "PhotoCraft / FilmCraft not found" window: locate or download |
| `release-repo.txt` | Address of the public releases repository |
| `release.bat`, `RELEASING.md` | Build and publish a release |
| `src/SettingsForm.cs` | Settings window, hotkey box, start-with-Windows |
| `src/AppSettings.cs` | Settings model and JSON storage |
