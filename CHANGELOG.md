# Changelog

Full release notes: [terminalia.dev/en/changelog](https://terminalia.dev/en/changelog)

## 1.2.0 · 2026-10-12

Terminal and files.

### Terminal
- Split panes: split right (⌘D) or down (⌥⇧⌘D), move between panes with ⌥⌘ and the arrows, resize by dragging. Each pane shows its connection and environment badge; ⌘W closes the focused pane.
- Panes in one tab can use different connections; snippets always go to a pane of the chosen connection.
- Search in the terminal (⌘F): match counter, case-sensitive and regex options, next and previous.
- Workspaces: save your tabs, panes and connections and restore them in one click from the sidebar or the ⌘K palette. Restoring opens the connections and the layout; it never runs commands.

### Files
- Each file opens in its own editor window, titled "file — server" with a stripe in the environment colour. Opening a file that is already open brings its window to the front.
- Unsaved changes are protected per window: closing, switching servers or disconnecting asks Save, Discard or Cancel. An unexpected connection loss never discards changes.
- Dual-pane browser: "This Mac" on the left and the server on the right. Copy with → / ←, "Copy to other pane" or drag and drop. Local files open in the same editor; deleting a local file moves it to the Trash.

### App
- Sidebar (⌘0), process column (⌥⌘0) and bottom panel (⌘J) can be hidden and shown again with always-visible buttons; when the bottom panel is hidden its tabs stay at the bottom. The app remembers which ones were open.
- Settings › Keyboard shortcuts: every menu shortcut can be changed, with search, conflict warnings, macOS reserved shortcut warnings and reset.

## 1.1.0 · 2026-10-11

Authentication, groups, snippets and SOCKS tunnels.

### Connections
- Three ways to sign in: private key, username and password, or an OpenSSH user certificate.
- Password login: the password can be saved in the macOS Keychain, separate from key passphrases; if you don't save it, the app asks when connecting. It is never written to disk or passed in process arguments. Automatic reconnects never ask for it.
- Certificate login: pick the `-cert.pub` file and its private key is detected; the app shows validity and principals and warns when it has expired. Importing `~/.ssh/config` recognizes `CertificateFile`.
- A `.pem` file is a private key: it goes under "Private key".
- Connection groups by project or client in the sidebar, and a PROD / STG / DEV environment badge in the list, the detail view and the status bar.

### Snippets
- New Snippets section (⌘7) to save named commands.
- "Paste in terminal" writes the command without running it; "Run on <connection>" runs it.
- Snippets show up in the ⌘K palette (↵ runs, ⇥ pastes), and any history entry can be saved as a snippet (⌘S).
- Section shortcuts: Transfers moves to ⌘8 and Settings to ⌘9.

### Tunnels
- SOCKS tunnels (`-D`) next to `-L` and `-R`: first free port from 1080, "Copy address", and a warning when listening on 0.0.0.0.
- `DynamicForward` is imported from `~/.ssh/config`.

### Terminal
- A terminal tab waits while you type the server password instead of timing out.

## 1.0.2 · 2026-10-10

Languages.

### App
- The app is available in Spanish and English.
- Language picker in Settings › General: Automatic (system language), Español or English. The change applies on restart, with a button to restart right away.
- In Automatic mode, if the system language is neither Spanish nor English, the app uses English.
- Dates, sizes and numbers follow the system format; sizes are calculated the same way Finder does.

## 1.0.1 · 2026-10-10

Fixes. Shipped together with 1.0.2; there is no separate 1.0.1 download.

### Editor
- Safer remote saves: if the connection drops halfway through a save, the original file no longer disappears. Permissions, owner and symlinks are preserved, and the editor doesn't mark as saved anything that wasn't uploaded.
- Switching servers or disconnecting closes the previous server's open files; with unsaved changes it asks Save, Discard or Cancel. An unexpected connection loss doesn't discard changes.
- Monaco is bundled with the app: the editor works offline and makes no CDN requests.

### File browser
- On servers behind ProxyJump, the file browser no longer takes about 10 s to open.
- The listing shows up without waiting for symlinks to resolve, and quick folder changes no longer flicker.

### Connections
- Stricter server identity checks: a revoked key (`@revoked`) or one that differs from `known_hosts` is never accepted; unsupported cases go through OpenSSH.

### Logs and terminal
- Command history is saved with permissions for your user only (`0600`).
- "Open in terminal" from the ⌘K palette uses your login shell's PATH (nvm, Homebrew), same as running the command directly.

## 1.0.0 · 2026-10-05

First public release.

### Connections
- Connection profiles with private key, passphrase in the Keychain, start directory and extra `-o` options.
- Import from `~/.ssh/config` with preview and per-host selection; includes LocalForward, RemoteForward and ProxyJump.
- Master session with ControlMaster, automatic reconnect with increasing backoff, and a status panel with socket, PID and latency.

### Tunnels
- `-L` and `-R` forwards you can toggle live, with auto-start on connect and re-applied after a reconnect.
- Busy local port detection with the name and PID of the process using it.

### File browser and transfers
- SFTP browser with a file table, editable path, favorites, recents, permissions and context menu.
- Drag and drop to and from Finder, plus move or copy within the server. Transfer queue with progress, speed and cancel; scp for large files.
- Automatic compatibility mode when the server doesn't allow native SFTP with your key.

### Editor
- Tabbed Monaco editor with atomic saves to the server, external change detection and a diff view.

### Processes
- Process panel with PM2 and Docker in tabs, grouping by Compose project, per-row and bulk actions, and typed confirmation for deletes.
- Remote commands use your real login shell: pm2 installed with nvm or Homebrew is detected with zero setup.

### Logs and terminal
- PM2, Docker and file logs in floating windows or the bottom panel, with search, pause, level filter and a configurable buffer.
- Built-in tabbed terminal over the master session, plus a ⌘K quick command palette with history and output.

### App
- Settings by section: general, connections, transfers, editor, logs and terminal.
- Adaptive window: the process column and sidebar hide in narrow windows; minimum size 760 × 560.
- Universal binary for Apple Silicon and Intel, shipped as a 12 MB DMG.
