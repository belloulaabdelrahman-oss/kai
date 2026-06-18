# Quick Start Guide - Build NexPOS Executable

## 🚀 Fastest Way to Build Your EXE

### On Windows:

```bash
# 1. Open Command Prompt or PowerShell
# 2. Navigate to your project folder
cd path\to\kai
git checkout electron-desktop-build

# 3. Install dependencies (one-time only)
npm install

# 4. Build your executable
npm run build:win

# ✅ Your EXE is ready in: dist\NexPOS Setup 1.0.0.exe
```

### That's it! 🎉

You now have:
- **NexPOS Setup 1.0.0.exe** - Installer for end users
- **NexPOS 1.0.0.exe** - Portable version (if you ran `npm run build`)

## 📦 What You're Getting

| File | Type | Use Case |
|------|------|----------|
| `NexPOS Setup 1.0.0.exe` | Installer | Share with users - they install it normally |
| `NexPOS 1.0.0.exe` | Portable | Run directly - no installation needed |

## ⚙️ System Requirements

- Windows 7 or later
- 200 MB free disk space
- No internet required after installation

## 🔧 If Something Goes Wrong

```bash
# Clear cache and rebuild
rm -r node_modules dist
npm install
npm run build:win
```

## 📖 Full Instructions

See `BUILD_INSTRUCTIONS.md` for detailed setup, customization, and troubleshooting.

---

**Questions?** Check the BUILD_INSTRUCTIONS.md file for comprehensive documentation.
