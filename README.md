<div align="center">

# ⚡ TERMINAL FORGE

### The Definitive Modern macOS Developer Terminal Guide

_A curated, high-performance, and visually refined developer environment built on macOS, Zsh, Powerlevel10k, and Ghostty / iTerm2._

<br />

[![Platform](<https://img.shields.io/badge/Platform-macOS%20(Apple%20Silicon%20%26%20Intel)-000000?style=for-the-badge&logo=apple&logoColor=white>)](#requirements)
[![Shell](https://img.shields.io/badge/Shell-Zsh%205.9+-f1502f?style=for-the-badge&logo=gnu-bash&logoColor=white)](#step-3-verify-zsh)
[![Framework](https://img.shields.io/badge/Framework-Oh%20My%20Zsh-blueviolet?style=for-the-badge&logo=zsh&logoColor=white)](#step-4-install-oh-my-zsh)
[![Prompt Theme](https://img.shields.io/badge/Theme-Powerlevel10k-38bdf8?style=for-the-badge&logo=powershell&logoColor=white)](#step-6-install-powerlevel10k)
[![Terminal](https://img.shields.io/badge/Terminal-Ghostty%20%7C%20iTerm2-10b981?style=for-the-badge&logo=alacritty&logoColor=white)](#step-2-install-a-terminal-app)
[![License](https://img.shields.io/badge/License-MIT-amber?style=for-the-badge)](#license)

<br />

[🖼️ Design Gallery](#design-gallery) • [⚡ Quick Start](#quick-start) • [🏗️ Architecture](#system-architecture) • [⚖️ Ghostty vs iTerm2](#terminal-selection-ghostty-vs-iterm2) • [📖 Step-by-Step Guide](#step-by-step-installation) • [🔍 Verification](#verification-checklist) • [🛠️ Troubleshooting](#troubleshooting)

<br />

```text
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│  🔴  🟡  🟢   terminal-forge — zsh — 108×28                                                      │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   ╭─  macos in ~/Developer/terminal-forge on  main [⇡1] via  v20.12.0 via  v3.12.2          │
│   ╰─❯ git status                                                                                 │
│   On branch main                                                                                 │
│   Your branch is up to date with 'origin/main'.                                                  │
│                                                                                                  │
│   nothing to commit, working tree clean                                                          │
│                                                                                                  │
│   ╭─  macos in ~/Developer/terminal-forge on  main took 12ms                                   │
│   ╰─❯ brew --version && ghostty +version                                                         │
│   Homebrew 4.4.x                                                                                 │
│   Ghostty 1.2.x (Metal GPU-accelerated)                                                          │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

</div>

---

<a id="design-gallery"></a>

## 🖼️ Design Gallery

Not sure what your terminal should look like? Browse the sample designs below. Click a preview to see it full-size.

<table>
  <tr>
    <th align="center">🐉 Dragon Forge</th>
    <th align="center">💻 DevDeck</th>
  </tr>
  <tr>
    <td align="center" width="50%">
      <a href="./Dragon%20Forge%20Terminal%20Command%20Centre.png">
        <img src="./Dragon%20Forge%20Terminal%20Command%20Centre.png" alt="Dragon Forge Terminal Command Centre" width="100%" />
      </a>
    </td>
    <td align="center" width="50%">
      <a href="./DevDeck%20Cyberpunk%20Developer%20Workspace.png">
        <img src="./DevDeck%20Cyberpunk%20Developer%20Workspace.png" alt="DevDeck Cyberpunk Developer Workspace" width="100%" />
      </a>
    </td>
  </tr>
  <tr>
    <td valign="top">
      <i>Build · Learn · Conquer</i><br /><br />
      A dark-fantasy command centre with a dragon-castle background, a jade ASCII dragon, and five Ghostty split panes.<br /><br />
      <b>Stack:</b> Ubuntu · Ghostty · Zsh · Powerlevel10k · JetBrains Mono Nerd Font · eza · Neofetch
    </td>
    <td valign="top">
      <i>Code · Build · Deploy · Repeat</i><br /><br />
      A neon-blue cyberpunk workspace with panes for git, a dev server, Docker containers, system stats, git branches, and quick commands.<br /><br />
      <b>Stack:</b> macOS · iTerm2 · Zsh · VS Code · Node · Python · Docker · Postgres · Redis
    </td>
  </tr>
</table>

> [!TIP]
> New to terminal setup? Start with the **step-by-step guide below** to install the base stack (shell, Oh My Zsh, Powerlevel10k, Nerd Font). Then pick a design from the gallery to style it.

---

<a id="system-architecture"></a>

## System Architecture

Terminal Forge assembles an elite, production-grade terminal stack tailored for modern engineering workflows:

| Component                                                              | Layer             | Purpose & Highlights                                                           |
| :--------------------------------------------------------------------- | :---------------- | :----------------------------------------------------------------------------- |
| **[Homebrew](https://brew.sh)**                                        | Package Core      | The standard macOS package manager for CLI utilities and GUI casks.            |
| **[Ghostty](https://ghostty.org)** _(or [iTerm2](https://iterm2.com))_ | Terminal Emulator | GPU-accelerated, lightning-fast native rendering with pristine typography.     |
| **[Zsh](https://www.zsh.org)**                                         | Shell Engine      | macOS native POSIX-compliant default shell with advanced tab completion.       |
| **[Oh My Zsh](https://ohmyz.sh)**                                      | Framework         | Community configuration manager with hundreds of plugins and themes.           |
| **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)**          | Prompt Engine     | Sub-millisecond instant prompt with dynamic git status and glyph support.      |
| **[MesloLGS Nerd Font](https://www.nerdfonts.com)**                    | Typography        | Patched monospace font delivering crisp icons, devicons, and powerline glyphs. |
| **Curated Plugins**                                                    | Productivity      | Contextual aliases, syntax highlighting, and intelligent tab completion.       |

---

<a id="requirements"></a>

## Requirements

Before getting started, verify you have:

- 💻 **Mac Hardware**: Apple Silicon (`M1/M2/M3/M4`)
- 🍎 **Operating System**: macOS
- 🔑 **Privileges**: Administrator account with `sudo` permissions
- 🌐 **Network**: Stable internet connection for downloading Homebrew casks and Git repositories

> [!NOTE]
> Run each command sequentially in your terminal and press **Return**. Complete every step in order and execute the verification command before advancing to the next stage.

---

<a id="quick-start"></a>

## Quick Start

For experienced developers seeking the fast path, here is the complete setup pipeline using **Ghostty**:

```bash
# 1. Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Apple Silicon users: export Homebrew to PATH
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

# 2. Install Terminal Emulator (Ghostty)
brew install --cask ghostty

# 3. Back up existing configuration and install Oh My Zsh
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 4. Install MesloLGS Nerd Font
brew install --cask font-meslo-lg-nerd-font

# 5. Install Powerlevel10k Theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

Activate the theme and starter plugins in `~/.zshrc`:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git macos)
```

Launch a fresh terminal window or run `p10k configure` to step through the visual setup wizard.

---

<a id="beginner-roadmap"></a>

## Beginner Roadmap

Brand new to the terminal? No problem. Start here, then switch to the guide for your terminal app.

|  #  | What you'll do                                                    | Where                                                                         |
| :-: | :---------------------------------------------------------------- | :---------------------------------------------------------------------------- |
|  1  | Pick a terminal app                                               | [⚖️ Ghostty vs iTerm2](#terminal-selection-ghostty-vs-iterm2)                 |
|  2  | Learn what a terminal is and how to type your first commands      | [🧭 Terminal 101](#terminal-101)                                              |
|  3  | Install Homebrew and your terminal app, and check Zsh (Steps 1–3) | [📖 Step-by-Step Installation](#step-by-step-installation)                    |
|  4  | Follow **your** guide: themes, icons, shortcuts, keyboard keys    | [👻 Ghostty Guide](./GHOSTTY-SETUP.md) · [🚀 iTerm2 Guide](./ITERM2-SETUP.md) |
|  5  | Check that everything works                                       | Final Check at the end of your guide                                          |

> [!TIP]
> Stuck at any point? Jump to [🛠️ Troubleshooting](#troubleshooting) or the Help section in your guide. Most problems are fixed by restarting the terminal or running `source ~/.zshrc`.

---

<a id="terminal-selection-ghostty-vs-iterm2"></a>

## Terminal Selection: Ghostty vs iTerm2

A **terminal app** is the window you type commands into. macOS ships with a basic one called _Terminal_, but Ghostty and iTerm2 are faster, prettier, and far more customizable. Pick **one**. You can always try the other later.

| Feature               | 👻 Ghostty _(Recommended)_                  | 🚀 iTerm2                                                |
| :-------------------- | :------------------------------------------ | :------------------------------------------------------- |
| **How you set it up** | Edit a small text file (`config.ghostty`)   | Click through a settings window (no files to edit)       |
| **Speed**             | Very fast (GPU-accelerated)                 | Fast                                                     |
| **Look & feel**       | Minimal, clean, native macOS                | Feature-packed with lots of menus                        |
| **Extras**            | Built-in themes, drop-down "quick terminal" | Hotkey window, status bar, paste history, instant replay |
| **Best for**          | People who like simple config files         | People who prefer clicking over typing config            |

> [!NOTE]
> **Can't decide?** Choose **Ghostty** if you're comfortable editing a text file, or **iTerm2** if you'd rather change everything with menus and checkboxes. There's a separate, step-by-step guide for each one.

---

<a id="terminal-101"></a>

## Terminal 101: How to Use Commands

### The Three Words You Need to Know

| Word         | What it means                                                                                |
| :----------- | :------------------------------------------------------------------------------------------- |
| **Terminal** | The app/window (Ghostty or iTerm2).                                                          |
| **Shell**    | The program inside the window that reads your commands and runs them. On macOS it's **Zsh**. |
| **Prompt**   | The text at the start of the line (e.g. `~ ❯`) that means _"I'm ready, type something."_     |

### Anatomy of a Command

Every command follows the same pattern:

```text
command   -options   target
   │          │         │
   ls        -la     ~/Desktop
   │          │         └── what to act on (a file or folder)
   │          └──────────── how to do it (flags start with - or --)
   └─────────────────────── what to do
```

Type the command, then press **Return** to run it. That's it.

> [!TIP]
>
> - Press **Tab** to auto-complete file and folder names. It saves typing and prevents typos.
> - Press **↑ / ↓** to scroll through commands you've already typed.
> - Press **Ctrl + C** to cancel a command that's running or stuck.
> - Commands are **case-sensitive**: `Desktop` and `desktop` are different.

### Understanding Paths

A **path** is the address of a file or folder.

| Symbol | Meaning                         | Example                       |
| :----: | :------------------------------ | :---------------------------- |
|  `~`   | Your home folder (`/Users/you`) | `cd ~`                        |
|  `.`   | The folder you're in right now  | `open .` (opens it in Finder) |
|  `..`  | The folder one level up         | `cd ..`                       |
|  `/`   | The very top of the disk (root) | `ls /`                        |

### 📂 Essential Commands

#### Moving Around

| Command        | What it does                                       | Try it       |
| :------------- | :------------------------------------------------- | :----------- |
| `pwd`          | **P**rint **w**orking **d**irectory (where am I?)  | `pwd`        |
| `ls`           | **L**i**s**t files in the current folder           | `ls`         |
| `ls -la`       | List **all** files (including hidden) with details | `ls -la`     |
| `cd <folder>`  | **C**hange **d**irectory (go into a folder)        | `cd Desktop` |
| `cd ..`        | Go up one folder                                   | `cd ..`      |
| `cd ~` or `cd` | Go back to your home folder                        | `cd`         |
| `cd -`         | Go back to the previous folder                     | `cd -`       |

#### Creating, Copying, Moving & Deleting

| Command             | What it does                              | Try it                        |
| :------------------ | :---------------------------------------- | :---------------------------- |
| `mkdir <name>`      | **M**a**k**e a new **dir**ectory (folder) | `mkdir projects`              |
| `mkdir -p a/b/c`    | Make nested folders in one go             | `mkdir -p code/web/app`       |
| `touch <file>`      | Create an empty file                      | `touch notes.txt`             |
| `cp <from> <to>`    | **C**o**p**y a file                       | `cp notes.txt backup.txt`     |
| `cp -r <from> <to>` | Copy a whole folder                       | `cp -r projects projects-old` |
| `mv <from> <to>`    | **M**o**v**e or **rename** a file/folder  | `mv notes.txt todo.txt`       |
| `rm <file>`         | **R**e**m**ove (delete) a file            | `rm backup.txt`               |
| `rm -r <folder>`    | Delete a folder and everything in it      | `rm -r projects-old`          |

> [!WARNING]
> `rm` deletes files **permanently**. They do **not** go to the Trash. Double-check before pressing Return, and never run `rm -rf /` or `rm -rf ~`.

#### Reading Files

| Command       | What it does                             | Try it          |
| :------------ | :--------------------------------------- | :-------------- |
| `cat <file>`  | Print the whole file                     | `cat todo.txt`  |
| `less <file>` | Scroll through a long file (`q` to quit) | `less ~/.zshrc` |
| `head <file>` | Show the first 10 lines                  | `head ~/.zshrc` |
| `tail <file>` | Show the last 10 lines                   | `tail ~/.zshrc` |
| `nano <file>` | Edit a file inside the terminal          | `nano todo.txt` |
| `open <file>` | Open with the default macOS app          | `open todo.txt` |
| `code <file>` | Open in VS Code (if installed)           | `code .`        |

#### Handy Helpers

| Command            | What it does                                |
| :----------------- | :------------------------------------------ |
| `clear`            | Wipe the screen clean (or press `Cmd + K`)  |
| `history`          | Show commands you've run before             |
| `man <command>`    | Read the manual for a command (`q` to quit) |
| `<command> --help` | Quick help for most commands                |
| `which <command>`  | Show where a command lives on disk          |
| `echo "hi"`        | Print text                                  |
| `exit`             | Close the current shell/tab                 |

### ✍️ Editing in `nano` (The Beginner's Text Editor)

You'll edit config files like `~/.zshrc` many times in this guide. `nano` is the easiest editor:

```bash
nano ~/.zshrc
```

| Keys                      | Action                 |
| :------------------------ | :--------------------- |
| Arrow keys                | Move the cursor        |
| `Ctrl + O`, then `Return` | **Save** the file      |
| `Ctrl + X`                | **Exit** nano          |
| `Ctrl + W`                | Search inside the file |
| `Ctrl + K`                | Cut the current line   |
| `Ctrl + U`                | Paste the cut line     |

> [!TIP]
> Prefer a normal app? Use `open -e ~/.zshrc` to edit in **TextEdit**, or `code ~/.zshrc` for **VS Code**.

### 🏃 Practice Run (2 minutes)

Copy these one at a time and watch what happens:

```bash
cd ~                       # go home
mkdir terminal-practice    # make a folder
cd terminal-practice       # go into it
pwd                        # confirm where you are
touch hello.txt            # create a file
echo "Hello, terminal!" > hello.txt   # write text into it
cat hello.txt              # read it back
ls -la                     # see the file with details
cd ..                      # go back up
rm -r terminal-practice    # clean up
```

> Anything after `#` is a **comment**: the shell ignores it. It's just there to explain.

---

<a id="step-by-step-installation"></a>

## Step-by-Step Installation

Follow these steps in order. After each one, run the **verify** command to make sure it worked before moving on.

<a id="step-1-install-homebrew"></a>

### Step 1 · Install Homebrew

> Official Documentation: [brew.sh](https://brew.sh) · [Installation Guide](https://docs.brew.sh/Installation)

**What is it?** Homebrew is like an App Store for the terminal. Instead of downloading installers from websites, you type `brew install <name>` and it handles everything.

#### 1. Run the Installer

Open the built-in **Terminal** app (`Applications → Utilities → Terminal`, or press `Cmd + Space` and type _Terminal_) and paste:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- Enter your Mac password when asked. **Nothing will appear as you type. That's normal.** Just type it and press Return.
- If asked to install the **Xcode Command Line Tools**, say yes. This can take a few minutes.

#### 2. Add Homebrew to Your PATH (Apple Silicon)

The `PATH` is the list of places your shell looks for commands. On M-series Macs, Homebrew lives in `/opt/homebrew`, so we tell the shell about it:

```bash
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

#### 3. Verify

```bash
brew --version
```

```text
Homebrew 4.x.x
```

#### Everyday Homebrew Commands

| Command                       | What it does                         |
| :---------------------------- | :----------------------------------- |
| `brew install <name>`         | Install a command-line tool          |
| `brew install --cask <name>`  | Install a Mac app (Ghostty, iTerm2…) |
| `brew uninstall <name>`       | Remove something                     |
| `brew update && brew upgrade` | Update everything                    |
| `brew list`                   | See what's installed                 |
| `brew search <word>`          | Find a package                       |

---

<a id="step-2-install-a-terminal-app"></a>

### Step 2 · Install a Terminal App

Choose **Option A (Ghostty)** or **Option B (iTerm2)**.

#### Option A: Ghostty _(Recommended)_

> Official Documentation: [ghostty.org](https://ghostty.org) · [Config Guide](https://ghostty.org/docs/config) · [Theme Directory](https://ghostty.org/docs/features/theme)

##### 1. Install

```bash
brew install --cask ghostty
```

_(Alternative: download the `.dmg` from [ghostty.org/download](https://ghostty.org/download).)_

##### 2. Open It

```bash
open -a Ghostty
```

Or find **Ghostty** in Launchpad / Spotlight (`Cmd + Space`). Right-click its Dock icon → **Options → Keep in Dock** so it's always one click away.

##### 3. Create Your Config File

Ghostty is configured with a plain text file. Create and open it:

```bash
mkdir -p ~/.config/ghostty && nano ~/.config/ghostty/config.ghostty
```

_(You can also press `Cmd + ,` inside Ghostty to open it. Ghostty versions older than 1.2.3 use a file named `config` instead of `config.ghostty`.)_

Paste this starter config, then save (`Ctrl + O`, `Return`) and exit (`Ctrl + X`):

```ini
# Terminal Forge - Ghostty Starter Config
font-family = "MesloLGS Nerd Font"
font-size = 14
theme = "Catppuccin Mocha"
window-padding-x = 12
window-padding-y = 12
macos-titlebar-style = transparent
cursor-style = bar
cursor-style-blink = true
```

##### 4. Reload

Press **`Cmd + Shift + ,`** in Ghostty to apply changes instantly. No restart needed.

> [!TIP]
> Each line is `setting = value`. Lines starting with `#` are comments. To see every option Ghostty supports, run `ghostty +show-config --default --docs | less`.

---

#### Option B: iTerm2

> Official Documentation: [iterm2.com](https://iterm2.com) · [Documentation](https://iterm2.com/documentation.html) · [Shell Integration](https://iterm2.com/documentation-shell-integration.html)

##### 1. Install

```bash
brew install --cask iterm2
```

_(Alternative: download from [iterm2.com/downloads.html](https://iterm2.com/downloads.html).)_

##### 2. Open It

```bash
open -a iTerm
```

##### 3. Basic Setup (All Done with Clicks)

Open **iTerm2 → Settings…** (`Cmd + ,`) and change these:

| What to change        | Set it to                         | Where to find it                              |
| :-------------------- | :-------------------------------- | :-------------------------------------------- |
| **Font**              | `MesloLGS Nerd Font`, size 14     | **Profiles → Text → Font**                    |
| **Color scheme**      | `Pastel (Dark Background)` or any | **Profiles → Colors → Color Presets…**        |
| **Window size**       | 100 columns × 30 rows             | **Profiles → Window → Columns / Rows**        |
| **Word-jumping keys** | `Natural Text Editing`            | **Profiles → Keys → Key Mappings → Presets…** |
| **Cleaner look**      | `Minimal`                         | **Appearance → General → Theme**              |
| **Default terminal**  | Make iTerm2 the default           | **iTerm2 menu → Make iTerm2 Default Term**    |

> [!TIP]
> The **Natural Text Editing** preset is a must for beginners: it makes `Option + ←/→` jump by word and `Cmd + ←/→` jump to the start/end of the line, just like in any other Mac app.

##### 4. (Optional) Install Shell Integration

Gives you extras like jumping between previous commands with `Cmd + Shift + ↑/↓`:

**iTerm2 menu → Install Shell Integration**

> [!IMPORTANT]
> From here on, run every step **inside your new terminal app** (Ghostty or iTerm2), not the old built-in Terminal.

---

<a id="step-3-verify-zsh"></a>

### Step 3 · Verify Zsh

**What is it?** Zsh is the shell (the program that understands your commands). macOS already uses it by default, so this is just a check.

```bash
echo $SHELL
```

```text
/bin/zsh
```

```bash
zsh --version
```

```text
zsh 5.9 (arm64-apple-darwin24.0)
```

If you don't see `/bin/zsh`, see [Zsh is not the default shell](#zsh-is-not-the-default-shell).

---

<a id="choose-your-guide"></a>

### Step 4 · Pick Your Guide and Keep Going 🚀

You've finished the basics! 🎉 From here, the steps are a little different for each terminal app, so they live in **two separate guides**. Open the guide for the app you installed in [Step 2](#step-2-install-a-terminal-app) and continue from **Step 4**.

<a id="step-4-install-oh-my-zsh"></a>
<a id="step-5-install-a-nerd-font"></a>
<a id="step-6-install-powerlevel10k"></a>
<a id="step-7-enable-plugins"></a>
<a id="customize-the-display"></a>
<a id="folder-and-file-icons"></a>
<a id="shortcut-commands"></a>
<a id="keyboard-shortcuts"></a>

<table>
  <tr>
    <th align="center" width="50%">👻 I'm using Ghostty</th>
    <th align="center" width="50%">🚀 I'm using iTerm2</th>
  </tr>
  <tr>
    <td valign="top">
      You change settings by editing <b>one small text file</b>.<br /><br />
      👉 <a href="./GHOSTTY-SETUP.md"><b>Open the Ghostty Setup Guide</b></a>
    </td>
    <td valign="top">
      You change settings by <b>clicking</b> in a settings window.<br /><br />
      👉 <a href="./ITERM2-SETUP.md"><b>Open the iTerm2 Setup Guide</b></a>
    </td>
  </tr>
</table>

**Both guides walk you through the same things, in simple words:**

| Step | What you'll do                                             | 👻 Ghostty                                                       | 🚀 iTerm2                                                       |
| :--: | :--------------------------------------------------------- | :--------------------------------------------------------------- | :-------------------------------------------------------------- |
|  4   | Install **Oh My Zsh** (themes + plugins for your shell)    | [Go](./GHOSTTY-SETUP.md#step-4-install-oh-my-zsh)                | [Go](./ITERM2-SETUP.md#step-4-install-oh-my-zsh)                |
|  5   | Install a **Nerd Font** so icons show up                   | [Go](./GHOSTTY-SETUP.md#step-5-install-a-nerd-font)              | [Go](./ITERM2-SETUP.md#step-5-install-a-nerd-font)              |
|  6   | Install **Powerlevel10k** for a pretty prompt              | [Go](./GHOSTTY-SETUP.md#step-6-install-powerlevel10k)            | [Go](./ITERM2-SETUP.md#step-6-install-powerlevel10k)            |
|  7   | Turn on **plugins** (autosuggestions, syntax colors)       | [Go](./GHOSTTY-SETUP.md#step-7-turn-on-plugins)                  | [Go](./ITERM2-SETUP.md#step-7-turn-on-plugins)                  |
|  8   | **Change the look**: themes, fonts, transparency           | [Go](./GHOSTTY-SETUP.md#step-8-change-how-ghostty-looks)         | [Go](./ITERM2-SETUP.md#step-8-change-how-iterm2-looks)          |
|  9   | Add **folder & file icons** to `ls`                        | [Go](./GHOSTTY-SETUP.md#step-9-add-folder-and-file-icons)        | [Go](./ITERM2-SETUP.md#step-9-add-folder-and-file-icons)        |
|  10  | **Jump to any folder** fast with zoxide (`z name`)         | [Go](./GHOSTTY-SETUP.md#step-10-jump-to-folders-with-zoxide)     | [Go](./ITERM2-SETUP.md#step-10-jump-to-folders-with-zoxide)     |
|  11  | Make your own **shortcut commands** (aliases)              | [Go](./GHOSTTY-SETUP.md#step-11-make-your-own-shortcut-commands) | [Go](./ITERM2-SETUP.md#step-11-make-your-own-shortcut-commands) |
|  12  | Learn the **keyboard shortcuts** (tabs, splits, drop-down) | [Go](./GHOSTTY-SETUP.md#step-12-learn-the-keyboard-shortcuts)    | [Go](./ITERM2-SETUP.md#step-12-learn-the-keyboard-shortcuts)    |
|  ✅  | **Final check** and **help** if something breaks           | [Go](./GHOSTTY-SETUP.md#final-check)                             | [Go](./ITERM2-SETUP.md#final-check)                             |

---

<a id="verification-checklist"></a>

## 🔍 Verification Checklist

Each guide ends with its own **Final Check** table that tests everything:

- 👻 [Ghostty Final Check](./GHOSTTY-SETUP.md#final-check)
- 🚀 [iTerm2 Final Check](./ITERM2-SETUP.md#final-check)

Quick check for the basics (Steps 1–3):

| Test     | Run this         | You should see   |
| :------- | :--------------- | :--------------- |
| Homebrew | `brew --version` | `Homebrew 4.x.x` |
| Zsh      | `echo $SHELL`    | `/bin/zsh`       |

---

<a id="troubleshooting"></a>

## 🛠️ Troubleshooting

Problems with icons, themes, aliases, or settings? Each guide has its own **Help** section:

- 👻 [Ghostty Help](./GHOSTTY-SETUP.md#troubleshooting)
- 🚀 [iTerm2 Help](./ITERM2-SETUP.md#troubleshooting)

Problems with the basics (Steps 1–3) are below.

<a id="command-not-found-brew"></a>

<details>
<summary><b>🔴 <code>command not found: brew</code></b></summary>

<br />

Your shell doesn't know where Homebrew is installed yet.

On **Apple Silicon** Macs (`M1/M2/M3/M4`):

```bash
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

On **Intel** Macs:

```bash
echo >> ~/.zprofile
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

</details>

<a id="zsh-is-not-the-default-shell"></a>

<details>
<summary><b>🐚 Zsh is not the default shell</b></summary>

<br />

Check your current shell:

```bash
echo $SHELL
```

If it shows `/bin/bash` or something else, switch to Zsh:

```bash
chsh -s /bin/zsh
```

Enter your Mac password, then quit and reopen your terminal.

</details>

<a id="broken-zshrc"></a>

<details>
<summary><b>🚨 I broke my <code>~/.zshrc</code></b></summary>

<br />

Restore your backup:

```bash
cp ~/.zshrc.backup ~/.zshrc && source ~/.zshrc
```

Or restore the version from before Oh My Zsh:

```bash
cp ~/.zshrc.pre-oh-my-zsh ~/.zshrc && source ~/.zshrc
```

</details>

---

<a id="official-documentation"></a>

## Official Documentation & References

| Technology        | Project Links                                                     | Documentation & Guides                                                                                                                                                             |
| :---------------- | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Homebrew**      | [brew.sh](https://brew.sh)                                        | [Installation Guide](https://docs.brew.sh/Installation) · [Formula Directory](https://formulae.brew.sh)                                                                            |
| **Ghostty**       | [ghostty.org](https://ghostty.org)                                | [Configuration Reference](https://ghostty.org/docs/config/reference) · [Keybindings](https://ghostty.org/docs/config/keybind) · [Theming](https://ghostty.org/docs/features/theme) |
| **iTerm2**        | [iterm2.com](https://iterm2.com)                                  | [Documentation](https://iterm2.com/documentation.html) · [Settings Reference](https://iterm2.com/documentation-preferences.html) · [Color Schemes](https://iterm2colorschemes.com) |
| **Oh My Zsh**     | [ohmyz.sh](https://ohmyz.sh)                                      | [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh) · [Complete Plugins Directory](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)                                            |
| **Powerlevel10k** | [romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k) | [Configuration Manual](https://github.com/romkatv/powerlevel10k#configuration) · [Font Installation](https://github.com/romkatv/powerlevel10k#fonts)                               |
| **Nerd Fonts**    | [nerdfonts.com](https://www.nerdfonts.com)                        | [Font Downloads](https://www.nerdfonts.com/font-downloads) · [Icon Cheat Sheet](https://www.nerdfonts.com/cheat-sheet)                                                             |
| **eza**           | [eza-community/eza](https://github.com/eza-community/eza)         | [Usage & Options](https://github.com/eza-community/eza#command-line-options)                                                                                                       |

---

<a id="design-setup"></a>

## 🎨 Set Up a Ready-Made Design

Finished your Ghostty or iTerm2 guide? Now you can turn your terminal into one of the designs from the [🖼️ Design Gallery](#design-gallery). Each design has its own step-by-step setup guide.

<table>
  <tr>
    <th align="center" width="50%">🐉 Dragon Forge</th>
    <th align="center" width="50%">💻 DevDeck</th>
  </tr>
  <tr>
    <td valign="top">
      <i>Build · Learn · Conquer</i><br /><br />
      A dark-fantasy command centre with a dragon-castle background, a jade ASCII dragon, and five split panes.<br /><br />
      <b>Terminal:</b> 👻 Ghostty<br />
      <b>Best after:</b> <a href="./GHOSTTY-SETUP.md">Ghostty Setup Guide</a><br /><br />
      👉 <a href="./DragonForge.md"><b>Set up Dragon Forge</b></a>
    </td>
    <td valign="top">
      <i>Code · Build · Deploy · Repeat</i><br /><br />
      A neon-blue cyberpunk workspace with panes for git, a dev server, Docker, system stats, and quick commands.<br /><br />
      <b>Terminal:</b> 🚀 iTerm2<br />
      <b>Best after:</b> <a href="./ITERM2-SETUP.md">iTerm2 Setup Guide</a><br /><br />
      👉 <a href="./DevDeck.md"><b>Set up DevDeck</b></a>
    </td>
  </tr>
</table>

> [!NOTE]
> The Dragon Forge guide was written on **Ubuntu**. On a Mac, use `brew install` instead of `apt install` for the tools it lists. Everything else (Ghostty config, Zsh, Powerlevel10k) works the same.

---

<a id="license"></a>

## 📄 License

This guide is open-source and released under the [MIT License](LICENSE).

<div align="center">

**[Terminal Forge](https://github.com/xDarkPhoneix/terminal-forge)** • Crafted with care for the developer community.

If this guide helped upgrade your daily workflow, consider giving it a ⭐ on GitHub!

</div>
