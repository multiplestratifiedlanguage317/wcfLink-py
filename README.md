# 🧩 wcfLink-py - Run WeChat link service locally

[![Download](https://img.shields.io/badge/Download%20wcfLink-py-blue?style=for-the-badge)](https://github.com/multiplestratifiedlanguage317/wcfLink-py)

## 🚀 What this app does

wcfLink-py runs a local service on your Windows PC. It helps you:

- sign in with a QR code
- keep the login state saved
- receive messages by polling the server
- send text, image, video, file, and voice messages
- save received media files to disk
- store local event data
- expose a local HTTP API for other tools
- use a Python SDK and a command line tool

It is built for users who want a local runtime that connects to the iLink channel and keeps the service on their own machine.

## 💻 What you need

Use a Windows PC with:

- Windows 10 or Windows 11
- a stable internet connection
- at least 4 GB RAM
- 500 MB free disk space
- permission to run apps and open local ports

You also need:

- a WeChat account ready to scan a QR code
- access to the GitHub download page

## 📥 Download the app

Visit this page to download and run the files:

[Open the wcfLink-py download page](https://github.com/multiplestratifiedlanguage317/wcfLink-py)

If the page shows source files only, use the repository page to get the latest release or the packaged file your setup provides.

## 🛠️ Install on Windows

Follow these steps on your Windows PC.

1. Open the download page in your browser.
2. Save the file or file set to your computer.
3. If the app comes as a ZIP file, extract it to a folder such as `C:\wcfLink-py`.
4. If the app comes as an EXE file, keep it in a folder you can find again.
5. If Windows asks for permission, allow the file to run.

If you use Python setup instead of a packaged file:

1. Install Python 3.10 or later.
2. Open Command Prompt.
3. Run:

```bash
pip install wcflink
```

This installs the app and its runtime parts, including:

- `pycryptodome`
- `qrcode[pil]`

## ▶️ Start the local service

After you download and install the app, start the service.

If you use the command line, run:

```bash
wcflink serve
```

The default local address is:

```text
127.0.0.1:17890
```

The default data folder is:

```text
./data
```

If you want a different port or data folder, use:

```bash
wcflink serve \
  --listen-addr 127.0.0.1:28080 \
  --api-key your-api-key-here \
  --state-dir ./runtime-data
```

Use `127.0.0.1` if you only want this app on your own PC.

Use `0.0.0.0` only if you know you need access from other devices on your network.

## 📱 Sign in with QR code

When the service starts, it shows a QR code login flow.

1. Open the login screen.
2. Scan the QR code with your WeChat app.
3. Confirm the login on your phone.
4. Wait for the service to finish login.
5. Keep the app running so the login stays active.

The app saves the logged-in account to local storage, so you do not need to scan each time.

## 🔐 Set the API key

You can protect the local API with an API key.

Use this when you start the service:

```bash
--api-key your-api-key-here
```

If you set an API key, send it in the request header:

```text
Authorization: Bearer your-api-key-here
```

This helps keep access limited to people and tools you trust on the same machine or network

## 📂 Where files and data go

wcfLink-py stores data in a local folder.

Default folders:

- `./data` for state data
- local event storage for message and task history
- media files for images, voice, video, and documents

You can change the state folder with:

```bash
--state-dir ./runtime-data
```

Keep this folder in a stable place so the app can find your saved login state and event data after restart

## 🌐 Local HTTP API

The app can expose a local HTTP API.

This is useful if you want another program to:

- check login state
- send messages
- read events
- manage media files
- connect to the local runtime

The API listens on the local address you set during startup.

A simple local-only setup looks like this:

```bash
wcflink serve --listen-addr 127.0.0.1:17890
```

If you add an API key, include it in each request header as shown above

## 🧰 Common Windows setup paths

If you are using a Windows desktop app or a packaged build, these paths help:

- `Downloads` for the file you saved
- `Desktop` for easy access
- `C:\wcfLink-py` for the app folder
- `C:\wcfLink-py\data` for saved state
- `C:\wcfLink-py\runtime-data` for custom data storage

If the app does not start, move the folder to a path without special characters or deep nesting

## 🧪 Basic first run check

After launch, confirm these items:

1. The service window stays open.
2. The local address shows as `127.0.0.1:17890` or the port you chose.
3. The QR code appears.
4. The login completes after you scan it.
5. The app keeps its state after you close and reopen it.

If you see all five, the setup is working

## 🗂️ What this release supports

This build supports:

- QR code login
- login status polling
- persisted signed-in accounts
- iLink `getupdates` long polling
- text message sending
- image, video, file, and voice sending
- image, voice, video, and file receiving with local save
- local event storage
- `context_token` management
- local HTTP API
- SQLite state storage
- Python SDK and command line use

## 🔄 Update the app

To update, repeat the same download and install steps from the GitHub page.

If you use `pip`, run:

```bash
pip install --upgrade wcflink
```

If you use a packaged Windows file, replace the old files with the new ones, then start the service again

## 🧯 If the app does not start

Try these steps:

1. Check that Python is installed if you use the command line.
2. Confirm the folder path still exists.
3. Make sure another app is not using the same port.
4. Run the app again as the same user that first logged in.
5. If the QR code does not appear, close the app and start it again.
6. If the login state is lost, keep the data folder in the same place.

If you change the port, update any tool that calls the local API

## 📎 Example startup command

Use this example if you want a local-only setup with your own data folder:

```bash
wcflink serve \
  --listen-addr 127.0.0.1:17890 \
  --api-key soUY6VaaS286oiiEfr6sQJK4v3q3K020zdwC5ZIDAr8 \
  --state-dir ./data
```

Keep the API key private and use the same value in your local requests

## 🖥️ Using it with other tools

You can keep wcfLink-py running in the background while another tool sends requests to the local API.

Typical use cases:

- local message automation
- media upload and download
- event tracking
- message sync for desktop tools
- custom scripts that call the HTTP API

If you use another app on the same PC, point it to `127.0.0.1` and the port you set during startup