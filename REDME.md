# ssEmojis

**Minecraft Emoji & Custom Sprite Plugin**  
**Version:** `1.0.0`  
**Developer:** `zyr3xyt.yml`  
**Brand:** Shark Studios

ssEmojis is a modern Paper plugin for parsing emoji-style sprite shortcodes into Adventure components. It includes a registry of Minecraft atlas sprites, glyph-based custom sprites, MiniMessage sprite tags, optional PlaceholderAPI integration, and a public Java API.

> **Compatibility:** This release targets Paper 1.21.x and Java 21. It is not a universal Minecraft 1.8–26.3 server build. Read [COMPATIBILITY.md](COMPATIBILITY.md) before installing.

## Features

- **Sprite shortcodes** — Parse identifiers such as `:diamond:`, `:minecraft:netherite_sword:`, and `:custom:server_logo:`.
- **Native Minecraft atlas sprites** — Built-in sprites use Adventure sprite components and do not need a custom resource pack on clients that support this component.
- **Custom glyph sprites** — Register custom private-use glyphs. The matching font/image assets must be provided in a client resource pack.
- **MiniMessage integration** — Use the `<sprite:diamond>` tag in supported MiniMessage parsing contexts.
- **Sprite registry** — Query, register, unregister, list, and reload sprites.
- **Optional PlaceholderAPI integration** — PlaceholderAPI is a soft dependency.
- **Public Java API** — Parse text into Adventure components and manage registered sprites.
- **Resource-pack request support** — Configure a resource-pack URL, SHA-1, prompt, and force behavior.

## Requirements

| Requirement | Version |
|---|---|
| Server software | Paper or compatible fork |
| Minecraft server target | Paper 1.21.x |
| Java | 21 |
| Optional dependency | PlaceholderAPI |

Native atlas sprite rendering depends on client support for Adventure sprite/object components. Custom glyph sprites require a matching resource pack.

## Installation

1. Download `ssEmojis.jar`.
2. Put it in your server's `plugins/` directory.
3. Start or restart the server.
4. Edit `plugins/ssEmojis/config.yml` if required.
5. Run `/ssem help` in-game or from the console.

## Usage

Use sprite shortcodes in supported ssEmojis parsing contexts:

```text
Welcome :diamond:
Kit: :netherite_sword: :diamond_pickaxe:
Reward: :golden_apple:
```

Namespaced identifiers:

```text
:minecraft:apple:
:custom:server_logo:
```

MiniMessage sprite tag:

```text
<red>Hello <sprite:diamond></red>
```

Unknown identifiers follow the configured `settings.unknown-sprite-behavior` setting.

## Built-in sprite examples

The default configuration includes examples from several groups:

- **Weapons:** netherite sword, diamond sword, iron sword, golden sword, bow, crossbow, trident
- **Tools:** netherite pickaxe, diamond pickaxe, diamond axe, netherite axe, fishing rod
- **Armor:** diamond helmet, chestplate, leggings, boots
- **Items:** apple, golden apple, diamond, emerald, ingots, nether star, totem, ender pearl, ender eye, experience bottle, shield, potion
- **Blocks:** chest, ender chest, crafting table, furnace, TNT
- **Other:** creeper head, player head

The exact available identifiers are defined in `config.yml`.

## Custom glyph sprites

Custom glyph entries can be configured in the `sprites` section. Example:

```yaml
sprites:
  custom:server_logo:
    glyph: "\uE101"
  custom:diamond_spear:
    glyph: "\uE102"
```

These private-use characters are only meaningful when the player's client has a resource pack with the matching font glyph/image mapping. The plugin does not make arbitrary PNG files appear in ordinary chat or scoreboard text without client-side assets.

## Resource-pack settings

The plugin can request a configured resource pack from players. Relevant configuration:

```yaml
resource-pack:
  enabled: true
  url: ""
  sha1: ""
  force: false
  prompt: "Download the ssEmojis sprite pack for custom glyphs"
  auto-generate: true
  auto-host: true
  host-port: 8765
  host-bind: "0.0.0.0"
```

Set `url` to a resource-pack URL that your players can reach and provide the matching SHA-1 when applicable. Do not assume that enabling the configuration options alone means a custom image pack has been generated and deployed. Verify the actual pack contents and hosting setup before distributing custom glyph sprites.

## Commands

| Command | Description |
|---|---|
| `/ssem` or `/ssem help` | Show help |
| `/ssem reload` | Reload plugin configuration and sprite data |
| `/ssem list` | List registered sprites |
| `/ssem info <id>` | Show sprite information |
| `/ssem test <id>` | Preview a sprite |
| `/ssem pack` | Show resource-pack status |
| `/ssem image list` | List image entries exposed by the image command |
| `/ssem image info <name>` | Show image entry information |
| `/ssem image test <name>` | Preview an image entry |
| `/ssem image validate <name>` | Validate/check an image entry |
| `/ssem image reload` | Reload image-related sprite data |
| `/ssem image remove <name>` | Unregister an image sprite |

Aliases: `/emoji`, `/emojis`

**Note:** The image API and image commands are present, but the supplied test report says the real image upload/validation and directory-scanning pipeline is not fully wired in this release. Treat image-management commands as limited until tested on a live server.

## Permissions

| Permission | Purpose |
|---|---|
| `ssem.admin` | Parent administrative permission |
| `ssem.reload` | Reload plugin data |
| `ssem.list` | List and inspect sprites |
| `ssem.test` | Preview sprites |
| `ssem.pack` | View resource-pack status |
| `ssem.image` | Parent image-management permission |
| `ssem.image.list` | List image entries |
| `ssem.image.reload` | Reload image-related data |
| `ssem.image.remove` | Unregister image sprites |
| `ssem.image.upload` | Declared upload permission node |

Most administrative permissions default to server operators.

## PlaceholderAPI

PlaceholderAPI is an optional soft dependency. The plugin includes a PlaceholderAPI expansion class. Install PlaceholderAPI alongside ssEmojis to enable its integration. Check the source for the exact expansion identifiers available in this build.

## Developer API

API class:

```java
zyr3xyt.yml.ssemojis.api.ssEmoji
```

Example:

```java
import zyr3xyt.yml.ssemojis.api.ssEmoji;
import net.kyori.adventure.text.Component;

ssEmoji api = ssEmoji.getInstance();

if (api != null) {
    Component message = api.parse("Hello :diamond:");

    boolean exists = api.hasSprite("diamond");
    api.registerSprite("custom:my_logo", "\uE200");
}
```

The API also exposes sprite lookup, collection, registration, and unregistration methods. Its image methods currently register glyph-backed sprite placeholders; they do not provide a complete PNG upload-to-resource-pack pipeline.

## Configuration

The default configuration is generated at:

```text
plugins/ssEmojis/config.yml
```

It contains settings for shortcode parsing, unknown sprite behavior, MiniMessage tags, resource-pack requests, image options, compatibility flags, and the built-in sprite registry.

## Build from source

This repository uses Gradle.

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd ssEmojis
./gradlew build
```

The compiled JAR is generated under:

```text
build/libs/
```

Build with Java 21.

## Compatibility and test reports

Read these files before deployment:

- [COMPATIBILITY.md](COMPATIBILITY.md)
- [TEST-REPORT.md](TEST-REPORT.md)

The supplied test report records compilation and offline/code-level checks. It does not report a live Paper server test or a multi-version client test matrix.

## Known limitations

- This JAR targets Paper 1.21.x and Java 21; it does not support 1.8–1.19.x servers.
- Native Minecraft atlas sprites require client support for Adventure sprite/object components.
- Custom glyph sprites require a matching resource pack.
- Resource-pack-free arbitrary PNG rendering in scoreboard lines is not implemented.
- ViaVersion/ProtocolLib protocol rewriting is not implemented, despite compatibility-related config flags.
- The image directory scanning and full image validation/upload pipeline are not fully wired according to the supplied test report.
- Live server startup, chat behavior, player resource-pack flow, and multi-client compatibility still require real-server testing.

## Project identity

| Property | Value |
|---|---|
| Plugin | `ssEmojis` |
| Version | `1.0.0` |
| Developer | `zyr3xyt.yml` |
| Main class | `zyr3xyt.yml.ssemojis.ssEmojis` |
| API class | `zyr3xyt.yml.ssemojis.api.ssEmoji` |
| Main command | `/ssem` |
| Aliases | `/emoji`, `/emojis` |
| Permission prefix | `ssem` |

## Community & Support

Join the Shark Studios Discord community for support, updates, announcements, and discussions:

**Discord:** https://discord.gg/yzTTAeNArf

## License & Attribution

Review and include the appropriate `LICENSE` file before redistributing this project. Preserve any required third-party notices and attributions.
