<p align="center">
  <img src=".github/assets/icon.png" width="96" height="96" alt="Terminalia icon">
</p>

<h1 align="center">Terminalia</h1>

<p align="center">
  <strong>Free native SSH client for Mac.</strong><br>
  Import your <code>~/.ssh/config</code> and get SFTP, a remote editor, SSH tunnels, PM2 and Docker processes, live logs and a terminal in one window, over a single SSH connection.
</p>

<p align="center">
  <a href="https://github.com/agustinalonsocantoli/terminalia/releases/latest"><strong>Download the latest release</strong></a> ·
  <a href="https://terminalia.dev/en">Website</a> ·
  <a href="https://terminalia.dev/en/changelog">Changelog</a> ·
  <a href="https://terminalia.dev/en/support">Support</a>
</p>

<p align="center">
  <img src=".github/assets/explorer.webp" alt="Terminalia showing the SFTP file browser connected to a server, with the process panel on the right">
</p>

## What it is

Terminalia is a free SSH client for macOS. It uses the OpenSSH that already ships with your Mac and the hosts you already have in `~/.ssh/config`, ProxyJump included. Everything runs over one master connection (ControlMaster), so files, tunnels, processes, logs and the terminal share a single SSH session.

- **No account.** Nothing to sign up for.
- **No telemetry.** The app sends no analytics.
- **Works offline.** The editor is bundled with the app; it only talks to your servers over SSH.
- **Your config stays yours.** Profiles come from `~/.ssh/config`; key passphrases and saved server passwords live in the macOS Keychain.

## Features

| | |
|---|---|
| **Connections** | Import hosts from `~/.ssh/config` with preview, including LocalForward, RemoteForward, DynamicForward, ProxyJump and CertificateFile. Groups and PROD / STG / DEV badges. Master session with automatic reconnect and a status panel (socket, PID, latency). |
| **Tunnels** | `-L`, `-R` and SOCKS (`-D`) forwards you can toggle live, auto-start on connect, and detection of busy local ports. |
| **Snippets** | Save named commands, paste them into the terminal or run them on a connection, also from the ⌘K palette. |
| **SFTP and editor** | File browser with favorites, permissions and drag and drop to and from Finder. Tabbed editor with atomic saves and a diff view. |
| **Processes** | PM2 and Docker Compose in one panel: start, stop, restart, grouped by project. Works with pm2 installed through nvm or Homebrew. |
| **Logs and terminal** | Live PM2, Docker and file logs with search and filters, plus a built-in tabbed terminal and a ⌘K command palette. |

<p align="center">
  <img src=".github/assets/tunnels.webp" width="49%" alt="Tunnels panel with local and remote forwards">
  <img src=".github/assets/processes.webp" width="49%" alt="Processes panel with PM2 and Docker Compose services">
</p>
<p align="center">
  <img src=".github/assets/editor.webp" width="49%" alt="Remote file editor with tabs">
  <img src=".github/assets/logs.webp" width="49%" alt="Live logs window with search and level filter">
</p>

## Requirements

- macOS 14 Sonoma or later
- Apple Silicon or Intel (universal binary)
- Sign in with a private key (ed25519, ECDSA or RSA), username and password, or an OpenSSH user certificate.
- Spanish or English interface.

## Install

1. Download `Terminalia-1.1.0.dmg` from [Releases](https://github.com/agustinalonsocantoli/terminalia/releases/latest) or from [terminalia.dev](https://terminalia.dev/en/download).
2. Open the DMG and drag Terminalia to Applications.
3. The first time, macOS will block it because the app is not notarized by Apple yet. Go to **System Settings › Privacy & Security** and click **Open Anyway**. You only need to do this once.

Verify the download (optional):

```sh
shasum -a 256 ~/Downloads/Terminalia-1.1.0.dmg
# 06249d1213760d4539d76a28985acf4d08d03d9351735e8d4382df27b75d84bb
```

## Guides

- [SSH tunnels on Mac: -L, -R and -D](https://terminalia.dev/en/guides/ssh-tunnel-mac)
- [~/.ssh/config with examples](https://terminalia.dev/en/guides/ssh-config)
- [ProxyJump through a bastion](https://terminalia.dev/en/guides/proxyjump-bastion)
- [Terminalia vs Termius](https://terminalia.dev/en/termius-alternative)

## Feedback and bugs

Use the [contact form](https://terminalia.dev/en/support) to report a bug, or [request a feature](https://terminalia.dev/en/changelog) on the changelog page.

## License

Terminalia is free to download and use. It is not open source: this repository hosts releases and documentation only. © 2026 Terminalia. All rights reserved.
