# CraftersLogin

**Advanced Authentication System for Minecraft Servers**

[![Version](https://img.shields.io/badge/version-1.6-blue.svg)](https://www.spigotmc.org/resources/crafterslogin.134395/)
[![Spigot](https://img.shields.io/badge/Spigot-1.8--1.21-orange.svg)](https://www.spigotmc.org/)
[![Velocity](https://img.shields.io/badge/Velocity-3.x-green.svg)](https://velocitypowered.com/)

---

## 📋 Table of Contents

- [What is CraftersLogin?](#what-is-crafterslogin)
- [Features](#features)
- [Compatibility](#compatibility)
- [Downloads](#downloads)
- [Installation](#installation)
- [Configuration](#configuration)
- [Commands](#commands)
- [Permissions](#permissions)
- [How It Works](#how-it-works)
- [Premium Auto-Login System](#premium-auto-login-system)
- [Standalone vs Proxy Mode](#standalone-vs-proxy-mode)
- [Database Options](#database-options)
- [Support & Information](#support--information)
- [License & Copyright](#license--copyright)

---

## What is CraftersLogin?

**CraftersLogin** is a comprehensive authentication plugin designed for Minecraft servers running Spigot/Paper and Velocity proxy. It provides secure player authentication with support for both **offline-mode** (password-based) and **premium-mode** (Mojang/Microsoft account auto-login) players.

The plugin is ideal for:
- **Cracked servers** requiring password protection
- **Hybrid servers** supporting both cracked and premium players
- **Proxy networks** (Velocity) needing centralized authentication
- **Standalone servers** wanting flexible authentication options

---

## Features

### Core Authentication
- 🔐 **Secure Password Authentication** - SHA-256 hashed passwords with salt
- ⚡ **Premium Auto-Login** - Automatic authentication for legitimate Minecraft accounts
- 🔄 **Session Management** - Configurable session persistence
- 🚫 **Login Protection** - Blocks commands, chat, movement, and damage during authentication
- ⏱️ **Countdown Timer** - Configurable time limit for login/registration

### Advanced Features
- 🌐 **Velocity Proxy Support** - Full integration with Velocity proxy
- 🗄️ **Multiple Database Support** - H2 (default) or MySQL
- 📊 **Admin Tools** - Player info, force login/logout, password changes, account management
- 🎯 **Spawn Management** - Separate spawn points for registration, login, and lobby
- 🔍 **Duplicate Account Detection** - Find alt accounts by IP
- 🧹 **Account Purging** - Remove inactive accounts automatically
- 💬 **Fully Customizable Messages** - All messages in configuration files

### Security
- 🛡️ **Password Requirements** - Enforce minimum password length
- 🔒 **Rate Limiting** - Configurable login attempt limits with auto-kick
- 📡 **Secure Plugin Messaging** - Encrypted communication between proxy and backend
- 🎭 **UUID Protection** - Proper handling of online/offline UUIDs

---

## Compatibility

### Server Software
| Platform | Versions | Status |
|----------|----------|--------|
| Spigot | 1.8 - 1.21 | ✅ Supported |
| Paper | 1.8 - 1.21 | ✅ Supported |
| Velocity | 3.x | ✅ Supported |
| BungeeCord | Any | ❌ Not Supported |

### Database Systems
| Database | Recommended Use | Status |
|----------|----------------|--------|
| H2 | Default, local servers | ✅ Included |
| MySQL | Shared/external databases | ✅ Provided |
| SQLite | Legacy (removed v1.6) | ❌ Removed |

### Proxy Compatibility
- ✅ **Velocity** - Full support with dedicated plugin
- ❌ **BungeeCord** - Not supported (use Velocity instead)

---

## Downloads

### Current Version: 1.6

| Platform | Download Link |
|----------|---------------|
| **Spigot** | [Download on SpigotMC](https://www.spigotmc.org/resources/crafterslogin.134395/) |
| **Modrinth** | *Coming Soon* |
| **GitHub Releases** | Check releases page |

### Build from Source
```bash
git clone https://github.com/yourusername/CraftersLogin.git
cd CraftersLogin
mvn clean package -DskipTests
```

---

## Installation

### Standalone Server (Spigot/Paper only)

1. Download the latest JAR from [SpigotMC](https://www.spigotmc.org/resources/crafterslogin.134395/)
2. Place the JAR in your `plugins/` folder
3. Start your server to generate configuration files
4. Edit `plugins/CraftersLogin/config.yml` to your preferences
5. Restart or use `/cl reload`

### Proxy Setup (Velocity + Spigot)

#### Velocity (Proxy)
1. Download the CraftersLogin JAR (contains both Spigot and Velocity components)
2. Place the JAR in your Velocity `plugins/` folder
3. Start Velocity to generate `proxy-config.yml`
4. Configure database settings in `proxy-config.yml`
5. Restart Velocity

#### Backend Servers (Spigot/Paper)
1. Install the same JAR on all backend servers
2. The plugin automatically detects Velocity presence
3. Configure `config.yml` on each backend (local database settings)
4. Restart backend servers

---

## Configuration

### Main Configuration (`plugins/CraftersLogin/config.yml`)

```yaml
# ===========================================
# CraftersLogin Configuration
# ===========================================

# Database Settings
# Options: H2 (default), MySQL
database:
  type: H2
  # MySQL settings (only used if type is MySQL)
  mysql:
    host: localhost
    port: 3306
    database: crafterslogin
    username: root
    password: password
    pool-size: 10

# Security Settings
security:
  # Minimum password length
  min-password-length: 5
  # Maximum login attempts before kick
  max-login-attempts: 3
  # Session timeout in minutes (0 = disable)
  session-timeout: 30
  # Time to login/register in seconds
  login-timeout: 60

# Feature Settings
settings:
  # Enable premium auto-login system
  enable-premium: true
  # Allow offline mode players
  allow-offline: true
  # Teleport players during auth
  teleport-enabled: true

# Spawn Locations
# Players will be teleported to these locations during authentication
spawn:
  # Location for unregistered players (first join)
  register:
    world: world
    x: 0.0
    y: 100.0
    z: 0.0
    yaw: 0.0
    pitch: 0.0
  # Location for registered but unauthenticated players
  login:
    world: world
    x: 10.0
    y: 100.0
    z: 10.0
    yaw: 90.0
    pitch: 0.0
  # Location after successful authentication
  lobby:
    world: world
    x: 100.0
    y: 64.0
    z: 100.0
    yaw: 180.0
    pitch: 0.0

# Message Configuration
# All messages are customizable in messages.yml
```

### Proxy Configuration (`plugins/CraftersLogin/proxy-config.yml`)

```yaml
# ===========================================
# CraftersLogin Proxy Configuration (Velocity)
# ===========================================

# Database for storing premium user data
database:
  type: H2
  h2:
    # Database file location (relative to Velocity folder)
    file: plugins/CraftersLogin/premium_data
  mysql:
    host: localhost
    port: 3306
    database: crafterslogin_velocity
    username: root
    password: password
    pool-size: 10

# Premium Authentication Settings
premium:
  # Enable premium auto-login on proxy
  enabled: true
  # Message shown when premium auth fails
  not-logged-in-message: "&cCould not authenticate your premium account. Please login manually."
```

### Messages Configuration

All user-facing messages can be customized in:
- **Spigot**: `plugins/CraftersLogin/messages.yml`
- **Velocity**: `plugins/CraftersLogin/messages-proxy.yml`

Example messages structure:
```yaml
# Player commands
login:
  usage: "&cUsage: /login <password>"
  success: "&aYou have been logged in successfully!"
  wrong-password: "&cIncorrect password! Attempts left: {attempts}/{max_attempts}"

register:
  usage: "&cUsage: /register <password> <confirmPassword>"
  success: "&aYou have been registered successfully!"
  passwords-dont-match: "&cPasswords do not match!"

# Admin commands
admin:
  reload: "&aConfiguration reloaded successfully."
  player-not-found: "&cPlayer {player} not found in database."
```

---

## Commands

### Player Commands

| Command | Description | Usage |
|---------|-------------|-------|
| `/login <password>` | Authenticate with your password | `/login mypassword123` |
| `/register <password> <confirm>` | Create a new account | `/register pass123 pass123` |
| `/changepassword <old> <new> <confirm>` | Change your password | `/changepassword old123 new123 new123` |
| `/premium` | Enable premium auto-login for your account | `/premium` |
| `/offline` | Disable premium mode (contact admin) | `/offline` |

### Admin Commands (`/cl`)

| Subcommand | Permission | Description |
|------------|------------|-------------|
| `/cl reload` | `crafterslogin.admin` | Reload configuration |
| `/cl version` | `crafterslogin.admin` | Show version info |
| `/cl info <player>` | `crafterslogin.admin` | Show player account info |
| `/cl accounts` | `crafterslogin.admin` | Show total registered accounts |
| `/cl forcelogin <player>` | `crafterslogin.admin` | Force login a player |
| `/cl forcelogout <player>` | `crafterslogin.admin` | Force logout a player |
| `/cl changepass <player> <pass>` | `crafterslogin.admin` | Change player password |
| `/cl unregister <player>` | `crafterslogin.admin` | Unregister a player |
| `/cl delete <player>` | `crafterslogin.admin` | Delete player account |
| `/cl dupeip <player/ip>` | `crafterslogin.admin` | Find duplicate accounts |
| `/cl purge <days>` | `crafterslogin.admin` | Purge inactive accounts |
| `/cl spawn setspawnregister` | `crafterslogin.admin` | Set registration spawn |
| `/cl spawn setspawnlogin` | `crafterslogin.admin` | Set login spawn |
| `/cl spawn setspawn` | `crafterslogin.admin` | Set lobby spawn |

---

## Permissions

| Permission | Default | Description |
|------------|---------|-------------|
| `crafterslogin.login` | Everyone | Use `/login` command |
| `crafterslogin.register` | Everyone | Use `/register` command |
| `crafterslogin.changepassword` | Everyone | Use `/changepassword` command |
| `crafterslogin.premium` | Everyone | Use `/premium` command |
| `crafterslogin.offline` | Everyone | Use `/offline` command |
| `crafterslogin.admin` | OP | Access to all admin commands |

---

## How It Works

### Authentication Flow

1. **Player Joins**
   - Player connects to the server
   - Plugin checks if player is registered
   - Premium status is verified (if enabled)

2. **For Premium Players** (when enabled)
   - If player has activated `/premium` before → **Auto-login**
   - Player skips password authentication entirely
   - Session is established automatically

3. **For Regular/Cracked Players**
   - Unregistered players → Must `/register`
   - Registered players → Must `/login`
   - Player is teleported to secure spawn during auth

4. **After Authentication**
   - Player is teleported to lobby spawn
   - Full server access granted
   - Session created (if enabled)

### Security Measures

During authentication, players **CANNOT**:
- Send chat messages
- Execute commands (except auth commands)
- Move, jump, or look around
- Take or deal damage
- Drop or pick up items
- Interact with blocks/entities
- Access inventories

---

## Premium Auto-Login System

The premium system allows legitimate Minecraft account owners to bypass password authentication.

### How to Enable Premium

1. Player joins with premium Minecraft account
2. Executes `/premium` command
3. Plugin verifies account with Mojang API
4. Account is marked as premium in database
5. Player is kicked to reconnect with auto-login

### Proxy Mode (Velocity)

When using Velocity:
- Premium verification happens at proxy level
- Backend servers receive authenticated premium users
- Single sign-on across all backend servers

### Standalone Mode

When using Spigot only:
- Premium verification happens locally
- Requires `online-mode: true` in `server.properties`
- Database stores premium status locally

---

## Standalone vs Proxy Mode

### Standalone Mode

**Best for:** Single servers, testing, small communities

**Features:**
- Local H2 database (default)
- Optional MySQL for external storage
- Premium auto-login works with `online-mode: true`
- All authentication handled by Spigot plugin

**Configuration:**
```yaml
# config.yml - Standalone setup
database:
  type: H2  # or MySQL for shared storage
```

### Proxy Mode (Velocity)

**Best for:** Multi-server networks, large communities

**Features:**
- Centralized authentication at proxy level
- Premium data shared across all backend servers
- Seamless server switching without re-authentication
- Velocity handles online/offline mode switching

**Configuration:**
```yaml
# proxy-config.yml - Velocity setup
database:
  type: H2  # Central premium data storage
premium:
  enabled: true
```

---

## Database Options

### H2 (Default)

**Pros:**
- ✅ Zero configuration required
- ✅ Fast, embedded database
- ✅ No external dependencies
- ✅ Perfect for single servers

**Cons:**
- ❌ Not shared between servers
- ❌ File-based (needs backups)

**Use when:** Running a single server or testing

### MySQL

**Pros:**
- ✅ Shared between multiple servers
- ✅ Professional-grade reliability
- ✅ Centralized backups
- ✅ Better for large networks

**Cons:**
- ❌ Requires MySQL server setup
- ❌ More complex configuration

**Use when:** Running a network with multiple backend servers

---

## Support & Information

### Documentation
- **Website:** https://craftersdevelopment.pages.dev/
- **Spigot Page:** https://www.spigotmc.org/resources/crafterslogin.134395/
- **Modrinth:** *Coming Soon*

### Getting Help
- Check configuration examples above
- Review server logs for error messages
- Ensure correct plugin versions for your server software
- Verify database connectivity (especially for MySQL)

### Common Issues

**"Failed to connect to database"**
- Verify MySQL credentials and server is running
- Check firewall rules for port 3306
- Ensure database exists with proper permissions

**"Premium auto-login not working"**
- Verify `enable-premium: true` in config
- Ensure player executed `/premium` successfully
- Check Velocity is properly configured (if using proxy)

**"Players can move during authentication"**
- Check for conflicting plugins
- Verify `teleport-enabled: true` in config
- Ensure spawn locations are properly set

---

## License & Copyright

### Copyright

**© 2024-2026 Crafters Development. All rights reserved.**

CraftersLogin is proprietary software. Unauthorized distribution, modification, or reverse engineering is prohibited without explicit permission from the author.

### Terms of Use

- ✅ **Allowed:** Personal use, server use, modification for personal use
- ✅ **Allowed:** Sharing the official download links
- ❌ **Prohibited:** Redistributing modified versions
- ❌ **Prohibited:** Selling the plugin or its derivatives
- ❌ **Prohibited:** Removing copyright notices

### Third-Party Libraries

This plugin uses the following open-source libraries:
- **H2 Database Engine** (MPL 2.0/EPL 1.0)
- **HikariCP** (Apache License 2.0)
- **MySQL Connector/J** (GPL 2.0 with FOSS Exception)

### Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

---

## Changelog

### Version 1.6 (21/04/2026)
- Optimized JAR size: H2 is now the default database
- Added Velocity database factory support
- Removed all hardcoded messages (now fully configurable)
- Removed `/cl ban` and `/cl unban` commands
- Implemented `/cl spawn` with new subcommands
- Fixed premium auto-login issues
- Added AsyncPreLoginListener for early validation
- Improved database compatibility

### Version 1.5 (19/04/2026)
- Fixed Velocity support
- Fixed ClassNotFoundException issues
- Improved JAR shading

---

**Made with ❤️ by Crafters Development**

For more information, visit: **https://craftersdevelopment.pages.dev/**
