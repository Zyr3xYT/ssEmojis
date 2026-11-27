ssEmojis

<p align="center">
  <strong>Bring your Minecraft chat to life with custom emojis, sprites, and images.</strong>
  <br>
  Powered by <strong>Shark Studios</strong>
</p><p align="center">
  <img src="https://img.shields.io/badge/Minecraft-Paper%201.21.x-blue" alt="Minecraft">
  <img src="https://img.shields.io/badge/Java-21-orange" alt="Java">
  <img src="https://img.shields.io/badge/Version-1.0.0-green" alt="Version">
</p>---

📖 About

ssEmojis is a modern Minecraft plugin designed to bring sprite-based emoji support to Minecraft chat and text components.

It combines supported native Minecraft atlas sprites with custom glyph sprites that can be delivered through a matching resource pack.

Developed by zyr3xyt.yml under Shark Studios.

✨ Features

- Native Minecraft Sprites — Use supported sprites from Minecraft's built-in atlas through Adventure sprite components.
- Custom Glyph Sprites — Display custom glyph-based sprites when players have the matching resource pack.
- MiniMessage Integration — Supports sprite tags such as "<sprite:diamond>" where the component is supported.
- Resource Pack Settings — Configure resource-pack URL, SHA-1, force option, and prompt.
- PlaceholderAPI Support — Optional integration when PlaceholderAPI is installed.
- Command System — Access plugin functionality through "/ssem" and its aliases.
- Developer API — Integrate ssEmojis into your own projects.

🔗 Official Links

- GitHub: [ssEmojis Repository](https://github.com/Zyr3xYT/ssEmojis)
- SpigotMC: [ssEmojis Resource](https://www.spigotmc.org/resources/ssemojis-universal-emojis-and-custom-image-system.140970/)
- Issues: [Report a Bug](https://github.com/Zyr3xYT/ssEmojis/issues)
- Discord: [Join Shark Studios](https://discord.gg/yzTTAeNArf)
- Source Code: [Browse Repository](https://github.com/Zyr3xYT/ssEmojis/tree/main)
- Documentation: [Read README](https://github.com/Zyr3xYT/ssEmojis#readme)

⚙️ Requirements

Requirement| Version
Minecraft Server| Paper 1.21.x
Java| Java 21
PlaceholderAPI| Optional

Compatibility note: This release targets Paper 1.21.x. Compatibility with other server software and Minecraft versions has not been verified.

📥 Installation

1. Download the latest "ssEmojis.jar" from the "SpigotMC resource page" (https://www.spigotmc.org/resources/ssemojis-universal-emojis-and-custom-image-system.140970/).
2. Make sure your server uses Paper 1.21.x and Java 21.
3. Place "ssEmojis.jar" inside your server's "plugins/" folder.
4. Start or restart your server.
5. Open the generated "plugins/ssEmojis/" folder.
6. Review the configuration and configure resource-pack settings if you use custom glyph sprites.

💬 Commands

Main command: "/ssem"

Aliases:

- "/emoji"
- "/emojis"

Image Command Family

Command| Purpose
"/ssem image list"| List image entries
"/ssem image info"| View image information
"/ssem image test"| Run an image test
"/ssem image validate"| Run image validation
"/ssem image reload"| Reload image-related data
"/ssem image remove"| Remove an image entry

Note: The custom-image management pipeline is currently limited. These commands should not be interpreted as a complete automatic PNG-to-resource-pack generation or hosting workflow.

🎨 Using Sprite Components

MiniMessage sprite tags use this general format:

<sprite:diamond>

The sprite key above is an example. Rendering depends on the target client, the text-display context, and whether the referenced sprite is available.

📦 Resource Pack

Custom glyph sprites require a resource pack containing the matching font and texture definitions.

The plugin's resource-pack settings include:

- Resource-pack URL
- SHA-1 hash
- Force option
- Prompt text

Use a valid, directly downloadable resource-pack URL and the SHA-1 hash matching the exact resource-pack file.

Supported native Minecraft atlas sprites do not require a custom resource pack when the client already supports the relevant sprite component.

🔌 PlaceholderAPI

PlaceholderAPI is an optional integration.

Install PlaceholderAPI separately if your server needs its placeholder support. The core sprite functionality does not require PlaceholderAPI.

👨‍💻 Developer API

Public API class:

zyrexyt.yml.ssemojis.api.ssEmoji

Use the API exposed by your installed ssEmojis version. Check the source code for the exact methods available in your build.

⚠️ Known Limitations

- The current release targets Paper 1.21.x and Java 21.
- Native sprite rendering depends on client-side component support.
- Custom glyph sprites require a matching resource pack.
- The custom-image workflow is not a complete automatic image-pack generation and hosting system.
- Protocol rewriting through ViaVersion or ProtocolLib is not implemented.
- Arbitrary PNG images cannot be rendered in a vanilla scoreboard simply by installing a server plugin.
- Multi-version support outside the stated target has not been verified.

🛠️ Building from Source

The source archive is available in this repository.

Extract the archive, open the project in your Java IDE or build environment, and use the build configuration included with the source.

"Browse ssEmojis Source Code" (https://github.com/Zyr3xYT/ssEmojis/tree/main)

🐛 Support & Bug Reports

Found a bug or have a feature request?

- [Open a GitHub Issue](https://github.com/Zyr3xYT/ssEmojis/issues)
- [Join Shark Studios Discord](https://discord.gg/yzTTAeNArf)

When reporting an issue, include:

- Minecraft server software and version
- Java version
- ssEmojis version
- Relevant console errors
- Steps to reproduce the issue

📌 Project Information

Detail| Value
Project| ssEmojis
Version| 1.0.0
Developer| zyr3xyt.yml
Studio| Shark Studios
Main Command| "/ssem"
Main Class| "zyrexyt.yml.ssemojis.ssEmojis"
API Class| "zyrexyt.yml.ssemojis.api.ssEmoji"
Language| Java

---

<p align="center">
  <strong>Made with care by Shark Studios 🦈</strong>
</p>
