# Crafters Development

> **Professional Minecraft Moderation & Administration Plugins**

[![Website](https://img.shields.io/badge/Website-craftersdevelopment.pages.dev-orange?style=flat-square)](https://craftersdevelopment.pages.dev/)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/k6KNKPXsUb)
[![Donate](https://img.shields.io/badge/PayPal-Donate-00457C?style=flat-square&logo=paypal&logoColor=white)](https://www.paypal.com/donate/?hosted_button_id=LWM2RD6DEJZHL)

---

## 📋 Table of Contents

- [What is Crafters Development?](#what-is-crafters-development)
- [Our Plugins](#our-plugins)
  - [CraftersStaff](#-craftersstaff)
  - [CraftersBan](#-craftersban)
  - [CraftersLogin](#-crafterslogin)
- [General Features](#general-features)
- [Compatibility](#compatibility)
- [Download & Installation](#download--installation)
- [Support & Community](#support--community)
- [Contributing](#contributing)
- [License](#license)

---

## What is Crafters Development?

**Crafters Development** is a specialized development team focused on creating professional-grade plugins for Minecraft servers. Founded by **xUnknowns**, our mission is to provide high-quality moderation, administration, and authentication tools for servers seeking exceptional performance and superior user experience.

We focus on three fundamental pillars:

- **🛡️ Security**: We implement the highest security standards across all our plugins
- **⚡ Performance**: Extreme optimization to guarantee zero lag on your servers
- **🎯 User Experience**: Intuitive and fully customizable interfaces

Our plugins are built for **production environments** — reliable, configurable, and network-ready. Whether you run a single server or a complex proxy network, Crafters Development plugins scale to meet your needs.

---

## 🚀 Our Plugins

---

### 🎖️ CraftersStaff

**The Ultimate Staff Management System for Minecraft**

*Current Version: v12.0.0*

CraftersStaff is the definitive solution for moderation team management on Minecraft servers. Designed for production environments, it offers a complete set of tools that facilitate staff workflow and enhance server security.

#### ✨ Key Features

| Feature | Description |
|---------|-------------|
| **Vanish Mode** | Become completely invisible with multiple visibility levels. Perfect for silent monitoring and catching rule-breakers |
| **Freeze System** | Freeze suspicious players for investigation. Prevents movement, interactions, and commands |
| **Private Staff Chat** | Exclusive communication channel for staff members with `/staffchat` or `/sc` |
| **Player Notes** | Attach structured notes to players with statuses (PENDING, IN_PROGRESS, COMPLETED). Includes attention requests and admin override support |
| **Staff Pass** | Secure authentication system for administrative access with web panel integration |
| **Activity Logging** | Complete logging of all staff actions for accountability |
| **Player Reports** | Integrated reporting system with case management |
| **Chat Management** | `/clearchat`, `/mute`, and other moderation commands |
| **GUI Interface** | Modern inventory-based interfaces for intuitive management |

#### 📋 Main Commands

**Player Commands:**
```
/report <player> <reason>    - Submit a player report to staff
```

**Staff Commands:**
```
/staff                        - Open the main staff GUI
/vanish                       - Toggle vanish mode
/vanish <player>              - Toggle another player's vanish
/freeze <player>              - Freeze a player for investigation
/unfreeze <player>            - Unfreeze a player
/staffchat                    - Toggle staff chat channel
/sc <message>                 - Send a message to staff chat
/clearchat                    - Clear global chat
/note <add|remove|list>       - Manage player notes
/staffpass                    - Authentication command
/craftersstaff                - Main management command (reload, info)
```

#### 🔐 Permissions

```
craftersstaff.staff           - Base staff permissions
craftersstaff.vanish          - Access to vanish feature
craftersstaff.freeze          - Access to freeze commands
craftersstaff.chat            - Access to staff chat
craftersstaff.note            - Base note permissions
craftersstaff.note.add        - Add notes to players
craftersstaff.note.list       - List player notes
craftersstaff.note.admin      - Remove any note regardless of creator
craftersstaff.admin           - Full access to all plugin functions
craftersstaff.staffpass.log   - View staff activity logs and web panel
```

#### 📥 Downloads

- **SpigotMC**: [craftersstaff.132281](https://www.spigotmc.org/resources/craftersstaff.132281/)
- **Modrinth**: [craftersstaff](https://modrinth.com/plugin/craftersstaff)
- **BuiltByBit**: Coming Soon
- **Bukkit**: Coming Soon

---

### 🔨 CraftersBan

**Advanced Punishment System for Minecraft Networks**

*Current Version: v1.0.0*

CraftersBan is a professional punishment and moderation system designed for Minecraft servers and proxy networks. It provides comprehensive ban, mute, and warning management with full network synchronization.

#### ✨ Key Features

| Feature | Description |
|---------|-------------|
| **Ban System** | Full ban management with temporary and permanent options |
| **Mute System** | Chat mutes with configurable durations and reasons |
| **Warn System** | Warning accumulation with automatic action triggers |
| **IP Banning** | Ban by IP address to prevent evasion |
| **Network Sync** | Punishments synchronized across all backend servers via proxy |
| **Revocation System** | Unban and unmute with full audit trail |
| **Lookup Command** | Check player punishment history instantly |
| **Time Format Support** | Flexible duration formats (1h30m, 2d, permanent, etc.) |
| **Silent Mode** | Execute punishments without broadcast messages |
| **Admin Override** | Staff with proper permissions can override restrictions |

#### 📋 Command Structure

CraftersBan uses a hierarchical command structure:

```
/craftersban (or /cb)
  ├── ban <player> <duration> <reason>
  ├── tempban <player> <duration> <reason>
  ├── ipban <player/ip> <duration> <reason>
  ├── mute <player> <duration> <reason>
  ├── tempmute <player> <duration> <reason>
  ├── warn <player> <reason>
  ├── unban <player>
  ├── unmute <player>
  ├── unpardon <player>
  └── lookup <player>
```

**Alternative Direct Commands:**
```
/ban <player> [duration] [reason]
/tempban <player> <duration> [reason]
/mute <player> [duration] [reason]
/unban <player>
/unmute <player>
/warn <player> <reason>
/banlookup <player>
```

#### 🔐 Permissions

```
craftersban.ban               - Access to ban commands
craftersban.tempban           - Access to temporary bans
craftersban.ipban             - Access to IP bans
craftersban.mute              - Access to mute commands
craftersban.warn              - Access to warning commands
craftersban.unban             - Access to unban commands
craftersban.unmute            - Access to unmute commands
craftersban.lookup            - Access to punishment lookup
craftersban.lookup.others     - Lookup other players' history
craftersban.silent            - Execute punishments silently
craftersban.admin             - Full administrative access
```

#### 📥 Downloads

- **SpigotMC**: [craftersban.133875](https://www.spigotmc.org/resources/craftersban.133875/)
- **Modrinth**: [craftersban](https://modrinth.com/plugin/craftersban)
- **BuiltByBit**: Coming Soon
- **Bukkit**: Coming Soon

---

### 🔐 CraftersLogin

**The Ultimate Authentication System for Minecraft Networks**

*Status: COMING SOON*

CraftersLogin is a professional, robust, and highly configurable authentication solution designed for servers that require full control over player access. Whether you manage a single server or a complex proxy network, CraftersLogin delivers a complete, secure, and easy-to-deploy solution.

#### 🎯 Core Philosophy

Built around three core pillars:
- **🔒 Security**: Modern hashing algorithms, brute-force protection, session hijacking prevention
- **⚡ Performance**: Minimal resource footprint with async database operations
- **🎨 User Experience**: Fully customizable titles, action bars, sound effects, and messages

#### ✨ Key Features

**Authentication System:**
- **Secure Registration** - Password confirmation with strength requirements
- **Secure Login** - Industry-standard password hashing (BCrypt, Argon2)
- **Password Change** - Self-service password modification
- **Account Deletion** - GDPR-compliant account removal
- **Premium Auto-Login** - Automatic verification for Mojang/Microsoft accounts
- **Offline Mode Toggle** - Revert to cracked mode when needed

**Proxy & Network Support:**
- **Velocity Support** - Full integration with Velocity proxy
- **BungeeCord Support** - Compatible with BungeeCord and Waterfall
- **Cross-Server Auth** - Authentication status shared across all backend servers
- **Proxy Communication** - Automatic backend notification of auth status
- **Spawn Management** - Auto-teleport to auth area, then lobby after login

**Database Options:**
- **SQLite** - Default option for single servers
- **MySQL** - Recommended for networks with high player counts
- **MongoDB** - Modern NoSQL option for enterprise deployments

**Security Features:**
- **Modern Hashing** - BCrypt and Argon2 algorithms
- **Brute-Force Protection** - IP-based rate limiting for login attempts
- **Session Hijacking Prevention** - Secure session token management
- **Case Spoofing Prevention** - Protection against username exploitation
- **UUID Validation** - Premium UUID verification
- **Max Accounts per IP** - Configurable limit to prevent abuse
- **Password Strength Requirements** - Enforce secure passwords

**User Experience:**
- **Customizable Titles** - Server-side title and subtitle messages
- **Action Bar Support** - Persistent status messages
- **Sound Effects** - Configurable sounds for all actions
- **Message Customization** - Full localization support
- **Login Messages** - Customizable broadcast options
- **Visual Effects** - Optional blindness effect while unauthenticated

#### 📋 Commands

**Player Commands:**
```
/register <password> <confirm>    - Create a new account
/login <password>               - Log in to the server
/changepassword <old> <new> <confirm> - Change your password
/unregister <password>         - Delete your account
/premium                         - Enable automatic verification
/offline                         - Revert to cracked mode
```

**Admin Commands** (`/crafterslogin` or `/cl`):
```
/cl reload                       - Reload plugin configuration
/cl version                      - Display current version
/cl info <player>                - View account information
/cl accounts                     - Show total registered accounts
/cl forcelogin <player>          - Force a player to be logged in
/cl forcelogout <player>         - Force a player to be logged out
/cl changepass <player> <newpass> - Change another player's password
/cl unregister <player>         - Unregister a player's account
/cl delete <player>              - Permanently delete an account
/cl dupeip <ip>                  - View accounts under an IP
/cl purge <days>                 - Remove inactive accounts
/cl convert <plugin>             - Migrate from another auth plugin
/cl spawns setspawnregistred     - Set authentication spawn
/cl spawns setspawn              - Set lobby spawn point
```

#### 🔐 Permissions

```
crafterslogin.admin             - Full administrator access
crafterslogin.admin.reload      - Reload configuration
crafterslogin.admin.version     - View version info
crafterslogin.admin.info        - View player account info
crafterslogin.admin.accounts    - View account statistics
crafterslogin.admin.forcelogin  - Force login players
crafterslogin.admin.forcelogout - Force logout players
crafterslogin.admin.changepass  - Change player passwords
crafterslogin.admin.unregister  - Unregister accounts
crafterslogin.admin.delete      - Permanently delete accounts
crafterslogin.admin.dupeip      - Check accounts by IP
crafterslogin.admin.purge       - Purge inactive accounts
crafterslogin.admin.convert     - Data migration access
crafterslogin.admin.spawns      - Manage spawn locations
```

#### 📥 Downloads

*Coming Soon - Currently in Development*

- **SpigotMC**: Coming Soon
- **Modrinth**: Coming Soon
- **BuiltByBit**: Coming Soon
- **Bukkit**: Coming Soon

---

## 🌟 General Features

All Crafters Development plugins share these common characteristics:

### 🎨 Modern Design
- Clean, intuitive interfaces using Minecraft's inventory GUI system
- Customizable colors, messages, and visual elements
- Responsive design that works on all screen sizes

### 🔧 Configurability
- Extensive configuration files (config.yml, messages.yml)
- Per-world and per-group permissions support
- MySQL/SQLite/MongoDB database options

### 📊 Monitoring & Analytics
- Download statistics tracking via Modrinth API
- Real-time version checking
- Changelog integration with Modrinth

### 🌍 Multi-Language Support
- Message files for easy translation
- Community-driven localization
- UTF-8 support for all characters

### 📱 Web Integration
- Discord community server
- Web-based admin panels (where applicable)
- Feedback system for community input

---

## 🔧 Compatibility

| Plugin | Minecraft Version | Server Software | Java Version | Proxy Support |
|--------|-------------------|-----------------|--------------|---------------|
| **CraftersStaff** | 1.13 - 1.21.x | Paper, Spigot, Bukkit | Java 17+ | ✅ Velocity, BungeeCord, Waterfall |
| **CraftersBan** | 1.13 - 1.21.x | Paper, Spigot, Bukkit | Java 17+ | ✅ Velocity, BungeeCord, Waterfall |
| **CraftersLogin** | 1.13 - 1.21.x | Paper, Spigot, Bukkit | Java 17+ | ✅ Velocity, BungeeCord, Waterfall |

### Tested Environments
- ✅ Paper 1.20.4+
- ✅ Spigot 1.20+
- ✅ Velocity 3.x
- ✅ BungeeCord (latest)
- ✅ Waterfall (latest)

---

## 📥 Download & Installation

### Step 1: Download

Choose your preferred platform:

1. **Modrinth** (Recommended): Fast downloads, automatic updates
2. **SpigotMC**: Official resource pages with community reviews
3. **BuiltByBit**: Coming Soon
4. **Bukkit Dev**: Coming Soon

### Step 2: Installation

**For Single Servers:**
```bash
1. Download the .jar file
2. Place it in your server's /plugins folder
3. Restart the server
4. Configure the plugin in /plugins/<PluginName>/config.yml
5. Reload or restart to apply changes
```

**For Proxy Networks (Velocity/BungeeCord):**

*CraftersStaff & CraftersBan:*
```bash
1. Install on the proxy (Velocity/BungeeCord)
2. Install on all backend servers
3. Configure database connection in config.yml (MySQL recommended)
4. Enable proxy mode in configuration
5. Restart all servers
```

*CraftersLogin:*
```bash
1. Install on all backend servers
2. Install on proxy (optional, for enhanced features)
3. Configure database (MySQL or MongoDB required for networks)
4. Set up proxy communication in config.yml
5. Define spawn locations with /cl spawns commands
6. Restart all servers
```

### Step 3: Configuration

Each plugin generates configuration files on first run:

```
/plugins/
├── CraftersStaff/
│   ├── config.yml
│   ├── messages.yml
│   └── data/
├── CraftersBan/
│   ├── config.yml
│   ├── messages.yml
│   └── data/
└── CraftersLogin/
    ├── config.yml
    ├── messages.yml
    └── data/
```

Refer to the in-game documentation or our website for detailed configuration guides.

---

## 💬 Support & Community

### 🤝 Get Help

- **Discord**: [discord.gg/k6KNKPXsUb](https://discord.gg/k6KNKPXsUb) - Join our active community for support, suggestions, and updates
- **GitHub Issues**: Report bugs and request features
- **Documentation**: [craftersdevelopment.pages.dev](https://craftersdevelopment.pages.dev/) - Complete plugin documentation

### 📢 Stay Updated

Follow us for the latest news, updates, and releases:

- 🌐 **Website**: [craftersdevelopment.pages.dev](https://craftersdevelopment.pages.dev/)
- 💬 **Discord**: [discord.gg/k6KNKPXsUb](https://discord.gg/k6KNKPXsUb)
- 🐦 **Twitter/X**: Coming Soon
- 📺 **YouTube**: Coming Soon

### 📝 Feedback

Have suggestions or found a bug? We value your input!

- Use our **Feedback System**: Available on our website
- Join **Discord** and share in the #suggestions or #bug-reports channels

---

## 💝 Support the Project

Crafters Development is developed by **xUnknowns** with love and dedication. If you find our plugins useful, consider supporting development:

[![Donate](https://img.shields.io/badge/PayPal-Donate-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://www.paypal.com/donate/?hosted_button_id=LWM2RD6DEJZHL)

Your donations help us:
- 🚀 Develop new features faster
- 🐛 Fix bugs promptly
- 📚 Maintain comprehensive documentation
- 🎨 Create new plugins
- 🌐 Keep services running

---

## 🤝 Contributing

We welcome contributions from the community!

### Ways to Contribute:

1. **Bug Reports**: Help us identify and fix issues
2. **Feature Suggestions**: Share your ideas for new features
3. **Translations**: Help localize plugins to your language
4. **Documentation**: Improve our guides and documentation
5. **Code Contributions**: Submit PRs for improvements (contact us first)

### Code of Conduct

- Be respectful and constructive
- Follow Minecraft EULA
- Respect intellectual property rights
- Help others in the community

---

## 📜 License

**Crafters Development - All Rights Reserved**

```
Copyright © 2026 Crafters Development. All rights reserved.

Redistribution, copying, or modification of this software is prohibited 
without the express written permission of Crafters Development.

This code is intellectual property protected by:
- Chilean Intellectual Property Law 17.336
- International copyright treaties

Unauthorized use, reproduction, or distribution is strictly prohibited.
For licensing inquiries, contact us through Discord or our website.
```

---

## 🙏 Acknowledgments

Special thanks to:
- Our amazing **Discord community** for testing, feedback, and support
- **PaperMC** and **SpigotMC** teams for their incredible server software
- **Modrinth** for providing an excellent plugin distribution platform
- All **server owners** who trust our plugins for their communities

---

<div align="center">

**Made with ❤️ by xUnknowns | Crafters Development © 2026**

[![Website](https://img.shields.io/badge/Visit%20Our%20Website-craftersdevelopment.pages.dev-orange?style=for-the-badge)](https://craftersdevelopment.pages.dev/)

</div>
