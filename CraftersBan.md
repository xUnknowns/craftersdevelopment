# CraftersBan

<p align="center">
  <strong>A comprehensive punishment system for Minecraft servers</strong><br>
  <a href="https://craftersdevelopment.pages.dev/">Website</a> •
  <a href="#installation">Installation</a> •
  <a href="#configuration">Configuration</a> •
  <a href="#commands">Commands</a> •
  <a href="#compatibility">Compatibility</a>
</p>

---

## 📋 Table of Contents

- [What is CraftersBan?](#what-is-craftersban)
- [Features](#features)
- [Compatibility](#compatibility)
- [Download](#download)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Commands & Permissions](#commands--permissions)
- [Proxy Support](#proxy-support)
- [Support](#support)
- [License](#license)

---

## 🔍 What is CraftersBan?

**CraftersBan** is a powerful, all-in-one punishment plugin designed for Minecraft servers running Spigot, Paper, or Velocity/BungeeCord proxies. It provides a complete punishment management system with support for temporary and permanent bans, mutes, kicks, and warnings.

Built with performance and scalability in mind, CraftersBan supports both local H2 databases for single-server setups and MySQL for network-wide punishment synchronization across multiple servers.

---

## ✨ Features

### Core Punishments
- **Ban** - Ban players permanently or temporarily with custom reasons
- **IP Ban** - Ban players by IP address to prevent alt account evasion
- **Mute** - Prevent players from chatting temporarily or permanently
- **IP Mute** - Mute all accounts sharing the same IP
- **Kick** - Remove players from the server with custom messages
- **Warn** - Issue warnings to players with optional expiration

### Advanced Features
- 🌐 **Network Support** - Full BungeeCord, Waterfall, and Velocity proxy support
- 🗄️ **Database Options** - H2 (local) or MySQL (network shared)
- 📊 **Punishment History** - Complete history tracking with pagination
- 🔍 **Alt Account Detection** - Check for alternative accounts by IP
- 🌍 **GeoIP Integration** - Display player geolocation information
- 🔒 **Lockdown Mode** - Server lockdown for maintenance or emergencies
- 📋 **List Commands** - View all active bans, mutes, and warnings
- 🎨 **Customizable Messages** - Fully configurable with color codes and placeholders
- 🔗 **Discord Webhooks** - Optional punishment notifications to Discord
- 📝 **Template System** - Pre-defined punishment templates for common offenses

---

## 🖥️ Compatibility

### Server Software
| Software | Versions | Support |
|----------|----------|---------|
| **Paper** | 1.13 - 1.21.5+ | ✅ Full Support |
| **Spigot** | 1.13 - 1.21.5+ | ✅ Full Support |
| **Purpur** | 1.13 - 1.21.5+ | ✅ Full Support |
| **Bukkit/CraftBukkit** | Any | ❌ Not Compatible |
| **Forge/Fabric** | Any | ❌ Not Compatible |

### Proxy Support
| Proxy | Versions | Support |
|-------|----------|---------|
| **BungeeCord** | 1.21-R0.4+ | ✅ Full Support |
| **Waterfall** | Latest | ✅ Full Support |
| **Velocity** | 3.4.0+ | ✅ Full Support |

### Requirements
- **Java 11** or higher
- **Minecraft 1.13** or higher (backend server)

---

## ⬇️ Download

### Official Sources
- **Website:** [https://craftersdevelopment.pages.dev/](https://craftersdevelopment.pages.dev/)
- **Latest Release:** Check the website for the most recent version

---

## 🚀 Installation

### Single Server Setup (Spigot/Paper)

1. **Download** the latest `craftersban-1.9.jar`
2. **Place** the JAR file in your server's `plugins/` folder
3. **Start** the server to generate default configuration files
4. **Configure** the plugin by editing files in `plugins/CraftersBan/`
5. **Restart** the server to apply changes

### Network Setup (BungeeCord/Waterfall/Velocity)

1. **Install on Proxy:**
   - Place `craftersban-1.9.jar` in your proxy's `plugins/` folder
   - Configure `plugins/CraftersBan/proxy-config.yml`

2. **Install on Backend Servers:**
   - Place the same JAR on all backend servers (Spigot/Paper)
   - Configure each server to connect to the same MySQL database for network-wide sync

3. **Database Configuration:**
   - For network sync, use MySQL on all servers
   - For independent servers, use H2 (default)

---

## ⚙️ Configuration

### Main Configuration (`config.yml`)

```yaml
# =====================================================
#   CraftersBan - Main Configuration
# =====================================================

# Server identification for network setups
server-name: "Server1"
network-name: "MyNetwork"

# Database Configuration
database:
  type: "h2"  # Options: h2, mysql
  host: "localhost"
  port: 3306
  name: "craftersban"
  username: "sa"
  password: ""

# Appeal URL shown in ban screens
appeal-url: "https://appeal.yourserver.com"

# Discord Webhook (optional)
discord:
  enabled: false
  webhook-url: ""
  
# Punishment Settings
settings:
  broadcast-punishments: true
  staff-notifications: true
  show-punishment-id: true
```

### Messages Configuration (`messages.yml`)

```yaml
# Plugin prefix shown in messages
prefix: "&8[&cCraftersBan&8] &r"

# Ban kick screen (shown to banned players)
ban:
  kick-screen: |
    &4&l⚠ &c&lYOU'RE BANNED &4&l⚠
    &r
    &7 USERNAME  &f» &e{player}
    &7 PUNISHED ON  &f» &e{date}
    &7 PUNISHED BY  &f» &e{staff}
    &7 REASON  &f» &e{reason}
    &7 EXPIRES  &f» &e{expires}
    &7 PUNISHMENT ID  &f» &e#{id}

# Staff notification format
  staff-notify: "&8[&cStaff&8] &e{staff} &cbanned &e{player} &8| &7Reason: &e{reason}"
```

### Proxy Configuration (`proxy-config.yml`)

```yaml
# Network Settings
network-name: "MyNetwork"

# Proxy Database (H2 for local, MySQL for shared)
database:
  type: "h2"
  host: "localhost"
  port: 3306
  name: "craftersban"
  username: "sa"
  password: ""

# Network Features
broadcast-network-wide: true
kick-from-all-servers: true
network-lockdown: true

# Proxy Kick Screens (shown when proxy blocks connections)
kick-screens:
  ban: |
    &4&l⚠ &c&lYOU'RE BANNED FROM THE NETWORK &4&l⚠
    &7Reason: &e{reason}
    &7Banned by: &e{staff}
    &7Appeal at: &eappeal.yourserver.com
```

---

## 🎮 Usage

### Basic Commands

**Ban a player permanently:**
```
/ban Notch Griefing
```

**Ban a player temporarily:**
```
/ban Notch 7d Griefing spawn
```

**IP Ban a player:**
```
/ipban Notch 30d Ban evasion
```

**Mute a player:**
```
/mute Notch 1h Spam in chat
```

**Kick a player:**
```
/kick Notch AFK in spawn
```

**Warn a player:**
```
/warn Notch Please read the rules
```

### Time Format Examples
- `10s` - 10 seconds
- `5m` - 5 minutes
- `2h` - 2 hours
- `7d` - 7 days
- `2w` - 2 weeks
- `1mo` - 1 month
- `perm` or `permanent` - Permanent

### Silent Punishments
Add `-s` flag to any command to execute silently (no broadcast):
```
/ban -s Notch 1d Testing
```

---

## 📚 Commands & Permissions

### Punishment Commands
| Command | Permission | Description |
|---------|------------|-------------|
| `/ban <player> [time] [reason]` | `craftersban.ban` | Ban a player |
| `/ipban <ip/player> [time] [reason]` | `craftersban.ipban` | Ban by IP address |
| `/mute <player> [time] [reason]` | `craftersban.mute` | Mute a player |
| `/ipmute <ip/player> [time] [reason]` | `craftersban.ipmute` | IP mute |
| `/kick <player> [reason]` | `craftersban.kick` | Kick a player |
| `/warn <player> [reason]` | `craftersban.warn` | Warn a player |
| `/tempwarn <player> <duration> [reason]` | `craftersban.warn` | Temporary warn |

### Management Commands
| Command | Permission | Description |
|---------|------------|-------------|
| `/unban <player/ip>` | `craftersban.unban` | Unban a player |
| `/unmute <player/ip>` | `craftersban.unmute` | Unmute a player |
| `/unwarn <player> [id]` | `craftersban.unwarn` | Remove warning |

### Information Commands
| Command | Permission | Description |
|---------|------------|-------------|
| `/checkban <player/ip>` | `craftersban.checkban` | Check ban status |
| `/checkmute <player/ip>` | `craftersban.checkmute` | Check mute status |
| `/checkwarn <player>` | `craftersban.checkwarn` | Check warnings |
| `/history <player>` | `craftersban.history.others` | View punishment history |
| `/alts <player/ip>` | `craftersban.alts` | Check alt accounts |
| `/geoip <player/ip>` | `craftersban.geoip` | IP geolocation |

### Admin Commands
| Command | Permission | Description |
|---------|------------|-------------|
| `/banlist` | `craftersban.banlist` | View ban list |
| `/mutelist` | `craftersban.mutelist` | View mute list |
| `/warnlist` | `craftersban.warnlist` | View warn list |
| `/lockdown <on/off>` | `craftersban.lockdown` | Toggle lockdown mode |
| `/craftersban reload` | `craftersban.admin` | Reload configuration |
| `/craftersban help` | `craftersban.help` | Show help |

### Permission Groups
- `craftersban.admin` - Grants all permissions
- `craftersban.notify` - Receive staff notifications

---

## 🌐 Proxy Support

CraftersBan fully supports network setups with BungeeCord, Waterfall, and Velocity proxies.

### Features on Proxy:
- **Pre-Connection Ban Check** - Banned players are blocked before reaching backend servers
- **Network-Wide Broadcasts** - Punishments broadcast across all servers
- **Shared Database** - Synchronized punishments across the network
- **Global Lockdown** - Lockdown mode affects the entire network
- **Cross-Server Kick** - Kick banned players from all servers simultaneously

### How It Works:
1. Player attempts to connect through proxy
2. Proxy checks if player is banned (from cache or database)
3. If banned: Connection is denied with ban screen
4. If not banned: Player connects normally to backend server
5. Backend server also verifies bans as secondary protection

---

## 🔧 Troubleshooting

### Common Issues

**"No player connection available for plugin messaging"**
- This is normal when no players are online on a server
- Messages are queued and sent when a player connects

**Player connects despite being banned**
- Ensure all servers share the same MySQL database for network setups
- Verify proxy configuration is correct

**Database connection errors**
- Check database credentials in `config.yml`
- Ensure MySQL server is accessible from the Minecraft server

---

## 💡 Tips

1. **Use MySQL for Networks** - Essential for synchronized punishments across servers
2. **Regular Backups** - Backup your database regularly, especially before updates
3. **Test Punishments** - Test on a test server before applying to production
4. **Staff Training** - Ensure staff understand time formats and silent flags
5. **Appeal System** - Set up an appeal URL for banned players

---

## 📞 Support

For more information, support, and updates:

- **Website:** [https://craftersdevelopment.pages.dev/](https://craftersdevelopment.pages.dev/)
- **Documentation:** Visit our website for detailed guides
- **Issues:** Report bugs through the website contact form

---

## 📄 License

**CraftersBan** is proprietary software.

### Copyright © 2026 xUnknown (Crafters Development)

All rights reserved. This plugin and its source code are the exclusive property of the author. Unauthorized copying, distribution, modification, or use of this software, via any medium, is strictly prohibited without express written permission from the copyright holder.

### Terms of Use:
- ✅ You may use this plugin on your Minecraft server
- ✅ You may modify the configuration files
- ❌ You may not redistribute the plugin JAR
- ❌ You may not decompile or modify the source code
- ❌ You may not claim ownership of this plugin

For licensing inquiries, commercial use, or custom development, please contact through our website.

---

<p align="center">
  <strong>Crafted with ❤️ by xUnknown</strong><br>
  <a href="https://craftersdevelopment.pages.dev/">https://craftersdevelopment.pages.dev/</a>
</p>
