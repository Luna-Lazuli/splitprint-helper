# splitprint-helper

Windows installer for the native messaging host used by the **SplitPrint**
Chrome extension.

Chrome extensions cannot select a printer directly on Windows, so
SplitPrint needs a small local helper to split a PDF by page range and
send each range to a specific printer. `SplitPrint-Setup.exe` installs
that helper and registers it with Chrome.

## How to use

1. Install the **SplitPrint** extension from the Chrome Web Store.
2. Open `chrome://extensions`, turn on **Developer mode**, and copy the
   extension ID shown on the SplitPrint card.
3. Download `SplitPrint-Setup.exe` from the
   [latest release](../../releases/latest).
4. Double-click the exe. Paste the extension ID into the window that
   appears and click **Install**.
5. Back on `chrome://extensions`, click the reload arrow on the
   SplitPrint card.

The installer copies itself to `%LOCALAPPDATA%\SplitPrint\`, writes a
native messaging manifest JSON next to it, and registers it under
`HKCU\Software\Google\Chrome\NativeMessagingHosts\com.splitprint.host`.
No admin rights needed.

## Uninstall

```
SplitPrint-Setup.exe --uninstall
```

Also remove the SplitPrint extension from `chrome://extensions`.

## Notes

- **SmartScreen warning**: the exe is unsigned, so Windows SmartScreen
  will warn you on first run. Click **More info > Run anyway**.
- **Debug helpers**: `SplitPrint-Setup.exe --ping` and
  `SplitPrint-Setup.exe --list-printers` are available if something is
  misbehaving.

Developed by Luna Lazuli ([lunalazuli.net](https://lunalazuli.net)).
