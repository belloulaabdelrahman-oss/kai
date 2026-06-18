# NexPOS Desktop Application - Build Instructions

## Prerequisites

Before building the executable, ensure you have installed:

1. **Node.js** (v14 or higher)
   - Download: https://nodejs.org/
   - Verify installation: `node --version` and `npm --version`

2. **Git** (optional, for version control)
   - Download: https://git-scm.com/

## Step-by-Step Build Process

### Step 1: Clone or Navigate to Repository

```bash
cd kai
git checkout electron-desktop-build
```

### Step 2: Install Dependencies

```bash
npm install
```

This will install:
- `electron` - Desktop application framework
- `electron-builder` - Tool to build and package the app
- `react` and `react-dom` - Required dependencies

### Step 3: Test the App (Optional)

To test before building:

```bash
npm start
```

This launches the app in development mode.

### Step 4: Build the Windows Executable

#### Option A: Build Installer (Recommended)

Creates an NSIS installer that users can run to install NexPOS:

```bash
npm run build:win
```

Output location: `dist/NexPOS Setup 1.0.0.exe`

#### Option B: Build Portable Executable

Creates a standalone .exe that doesn't require installation:

```bash
npm run build:win-portable
```

Output location: `dist/NexPOS 1.0.0.exe`

#### Option C: Build Both

```bash
npm run build
```

This creates both installer and portable versions.

### Step 5: Locate Your Executable

After the build completes, your executables will be in the `dist/` folder:

```
dist/
├── NexPOS Setup 1.0.0.exe          (Installer - recommended for users)
├── NexPOS 1.0.0.exe                (Portable - standalone executable)
└── builder-effective-config.yaml   (Build configuration)
```

## Distribution

### For End Users (Recommended: Installer)

1. Send `dist/NexPOS Setup 1.0.0.exe` to users
2. Users double-click and follow the installer wizard
3. Creates Start Menu shortcuts and desktop shortcut
4. Can be uninstalled via Control Panel > Programs

### For Quick Testing (Portable)

1. Send `dist/NexPOS 1.0.0.exe` to users
2. Users can run it directly - no installation required
3. App stores data in `%APPDATA%/NexPOS/`

## Customization

### Change App Icon

1. Replace `assets/icon.ico` with your own icon
2. Icon should be 256x256 pixels
3. Rebuild: `npm run build:win`

### Change App Name

Edit `package.json`:

```json
"productName": "YourAppName"
```

Then rebuild.

### Change Version Number

Edit `package.json`:

```json
"version": "1.1.0"
```

## Troubleshooting

### Build fails with "icon.ico not found"

- Ensure `assets/icon.ico` exists
- If not, create a basic one or remove the icon line from `package.json`

### App won't start

- Check that `trickle/` folder contains your HTML files
- Verify file paths in `electron/main.js` are correct

### Build is very slow

- This is normal for the first build (downloads dependencies)
- Subsequent builds are faster

## File Structure

```
kai/
├── electron/
│   ├── main.js           (Electron main process)
│   └── preload.js        (Security context)
├── trickle/              (Your POS application files)
│   ├── index.html
│   ├── pos.html
│   ├── products.html
│   └── ...
├── assets/
│   └── icon.ico          (App icon)
├── package.json          (Dependencies & build config)
├── BUILD_INSTRUCTIONS.md (This file)
└── dist/                 (Output: your .exe files)
```

## Next Steps

1. **For Distribution**: Use the Installer version (`Setup .exe`)
2. **For Testing**: Use the Portable version (`.exe`)
3. **For Updates**: Increment version in `package.json` and rebuild

## Additional Resources

- Electron Documentation: https://www.electronjs.org/docs
- Electron Builder: https://www.electron.build/
- Package.json Reference: https://docs.npmjs.com/cli/v8/configuring-npm/package-json

## Support

If you encounter issues:
1. Check the troubleshooting section above
2. Verify all prerequisites are installed
3. Ensure file paths match your directory structure
