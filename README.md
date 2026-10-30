# NOALBS Config Editor

A one-page editor for the `config.json` and `.env` files used by [NOALBS](https://github.com/NOALBS/nginx-obs-automatic-low-bitrate-switching), the tool that switches your OBS scenes when an IRL stream's bitrate drops. Instead of editing JSON by hand, you fill in labelled fields, and the editor writes a file NOALBS can read.

It's a single HTML file that runs in your browser: there's nothing to install, and your config stays on your PC.

> This is a community tool, not part of the official NOALBS project. It's built for NOALBS v2.

## Getting started

1. **Download the editor.** Click [`noalbs-config-editor.html`](noalbs-config-editor.html), then the **Download raw file** button (↓) at the top right.
2. **Open it** by double-clicking the downloaded file. Use Chrome or Edge if you can (see [Browsers](#browsers)). If it opens in a different browser, right-click the file and choose **Open with**.
3. **Close NOALBS** while you edit.
4. **Open your config.** Click **Open** and pick the `config.json` in your NOALBS folder, or drag the file onto the page. No config yet? Click **Start a new one**.
5. **Connect to OBS (optional)** with the **Connect OBS** button at the top, so you can pick scene names from dropdowns instead of typing them. See [Pick scenes from OBS](#pick-scenes-from-obs-optional).
6. **Work through the tabs.** If a **things to check** list appears at the top, fix what it lists. Click an item to jump to it.
7. **Save** with the **Save config.json** button or **Ctrl+S**.
8. **Start NOALBS again** so it loads your changes.

## The tabs

| Tab | What's there |
| --- | --- |
| 🔧 Setup | How NOALBS connects to OBS, and scene collections for the `!collection` command |
| ⚡ Switcher | Your Live, Low and Offline scenes, and the bitrate and RTT triggers that switch between them |
| 🌐 Servers | The stream servers your feed comes in through: BELABOX, SRT Live Server, NGINX, MediaMTX and more |
| 💬 Chat | Your channel (Twitch or Kick), admins, ignored users, and who can use each chat command |
| ⚙️ Optional | Starting, ending, privacy and refresh scenes, auto-recording, and the offline timeout |
| 🔑 Environment | The `.env` file with your chat bot's login |

## Bot login (.env)

NOALBS reads the login for the account it chats as from a `.env` file in your NOALBS folder.

1. On the **🔑 Environment** tab, click **Load .env** (or drag your `.env` onto the page).
2. **TWITCH_BOT_USERNAME** is the account that posts in chat. It can be your own.
3. **TWITCH_BOT_OAUTH** is a token from [twitchtokengenerator.com](https://twitchtokengenerator.com), made while logged in as the bot. The `oauth:` prefix is added for you.
4. Click **Save .env**.

Other lines in the file, such as `CONFIG_DIR` or `LOG_DIR`, are kept as they are. Keep `.env` private: anyone with the token can post as your bot.

## Pick scenes from OBS (optional)

Scene names in the config must match OBS exactly, capital letters included. Instead of typing them, you can pick them from your real OBS scenes:

1. In OBS (version 28 or newer), open **Tools → WebSocket Server Settings**, tick **Enable WebSocket server**, and note the port and password.
2. On the editor's **🔧 Setup** tab, enter the same host, port and password, then click **Connect to OBS** (or the **Connect OBS** button at the top of the page).

Every scene field becomes a dropdown of your OBS scenes, and the OBS source, profile and scene collection fields list what OBS has too. If your config names something OBS doesn't have, it stays selected, marked "not in OBS", and shows up in the things-to-check list.

- **Added a scene in OBS?** Click the OBS button at the top of the page to reload the lists.
- **Next time**, the editor reconnects by itself when you open a config.
- **Want to type names instead?** Click **Disconnect** on the Setup tab.

## Browsers

| Browser | Saving |
| --- | --- |
| Chrome, Edge | Saves straight back to the file you opened. The browser may ask permission the first time. |
| Firefox and others | Downloads a new copy. Move it into your NOALBS folder, replacing the old file. |

If a downloaded `.env` ends up with a different name (like `env` or `.env.txt`), rename it to exactly `.env`.

## Good to know

- **Nothing gets dropped.** Settings the editor doesn't show, such as `logToFile`, are saved back unchanged, and so are stream server types it doesn't recognise.
- **Allowed values match NOALBS.** Chat languages, server types and command names were checked against the NOALBS v2 source code.
- **Your files stay private.** The page only goes online to load its fonts from Google Fonts, and to reach OBS at the address you enter when you connect.

## Troubleshooting

- **"Couldn't reach OBS":** check that OBS is open, its WebSocket server is enabled, and the host and port match **Tools → WebSocket Server Settings**.
- **Saving downloads a file instead:** your browser can't write files directly. Use Chrome or Edge, or move the downloaded file into your NOALBS folder.
- **NOALBS ignores your changes:** restart NOALBS after saving.
- **Found a bug?** [Open an issue](https://github.com/musicman0917/NOALBS-configuration-file/issues).

## License

[MIT](LICENSE)
