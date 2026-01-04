<p align="center">
  <img src="logo.png" alt="PocketCode" width="600">
</p>

# 📱 PocketCode

**Build apps using AI right from your Android phone.**

> Works with **OpenCode**, **Claude Code**, **Codex**, and **Gemini CLI**.  
> This guide uses [OpenCode](https://opencode.ai).

---

## What You Need

- Android phone (6GB+ RAM, 5GB free storage)
- [Termux](https://play.google.com/store/apps/details?id=com.termux) from Play Store

---

## ⚡ Option A: Quick Setup (2 Commands)

> **Choose this OR Option B below — not both!**

**In Termux, run:**
```
pkg update -y && pkg upgrade -y && pkg install proot-distro -y && proot-distro install debian && proot-distro login debian
```

**Inside Linux (after prompt shows `root@localhost`), run:**
```
apt update && apt install curl git build-essential python3 -y && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt install nodejs -y && curl -fsSL https://opencode.ai/install | bash && echo 'alias opencode-web="opencode web --hostname 127.0.0.1 --port 4096"' >> ~/.bashrc && source ~/.bashrc
```

✅ **Done!** Skip to [How to Use](#how-to-use).

---

## 📝 Option B: Step-by-Step Setup

> **Skip this if you already did Option A above.**

Open Termux and run each command. Copy one block at a time.

**Step 1: Update Termux**
```
pkg update -y && pkg upgrade -y
```

**Step 2: Install Linux**
```
pkg install proot-distro -y && proot-distro install debian
```

**Step 3: Enter Linux**
```
proot-distro login debian
```
Your prompt should now show `root@localhost`

**Step 4: Install Tools**
```
apt update && apt install curl git build-essential python3 -y
```

```
curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt install nodejs -y
```

**Step 5: Install OpenCode**
```
curl -fsSL https://opencode.ai/install | bash
```

**Step 6: Create Shortcut**
```
echo 'alias opencode-web="opencode web --hostname 127.0.0.1 --port 4096"' >> ~/.bashrc && source ~/.bashrc
```

✅ **Setup complete!**

---

## How to Use

Every time you open Termux, run:
```
proot-distro login debian
```

Then start the AI:

| Mode | Command | Access |
|------|---------|--------|
| Web | `opencode-web` | Chrome → `localhost:4096` |
| Terminal | `opencode` | Direct in Termux |

**Try it:** Tell the AI *"Create a website with a blue background"*

**Preview websites:**
```
python3 -m http.server 8080
```
Then open Chrome → `localhost:8080`

---

## File Management (Optional)

**Using Acode App:**
1. Install [Acode](https://play.google.com/store/apps/details?id=com.foxdebug.acode)
2. Open Acode → Files → Add Path → Termux → home
3. Edit files visually

---

## Saving Your Work

⚠️ **Uninstalling Termux deletes everything.**

**Local Backup** (run from Termux, not inside Linux):
```
exit
```
```
termux-setup-storage
```
```
tar -czvf ~/storage/downloads/pocketcode-backup.tar.gz ~/.proot-distro/
```

**GitHub Sync:**
```
ssh-keygen -t ed25519 && cat ~/.ssh/id_ed25519.pub
```
Add the key to [GitHub](https://github.com/settings/keys), then:
```
cd ~/my-project && git init && git add . && git commit -m "save" && git remote add origin git@github.com:YOU/project.git && git push -u origin main
```

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "Address already in use" | `pkill node` |
| Commands not found | `source ~/.bashrc` |
| Termux closes randomly | Settings → Apps → Termux → Battery → Unrestricted |

---

**Made with ❤️ for mobile developers.**
