# FiveM Chat - No-Build Version

This is a converted version of the FiveM chat resource that **does not require compilation** or the use of yarn/webpack for making changes.

## Original Resource Credits

This resource is based on the default Cfx.re asset pack (cfx-server-data).
- **Author**: Cfx.re <root@cfx.re>
- **Description**: Provides baseline chat functionality using a NUI-based interface.
- **Repository**: https://github.com/citizenfx/cfx-server-data

## What Has Been Changed

### Original Structure
- Used TypeScript + Vue.js + Webpack
- Required `yarn install` and `yarn build` for every change
- Separate `.vue` and `.ts` files
- Build dependencies in `fxmanifest.lua`

### Converted Structure
- Pure JavaScript + Vue.js
- Direct editing of files without the need for compilation
- Single `app.js` file with all logic
- No build dependencies

## Main Files

- `fxmanifest.lua` - Updated manifest without build dependencies
- `html/index.html` - Main HTML with Vue.js included
- `html/app.js` - All chat logic in pure JavaScript
- `html/index.css` - Chat styles
- `html/vendor/**` - Local Vue.js and External fonts and CSS

## How to Use

1. Copy the `chat` folder to your FiveM resources folder
3. Add to `server.cfg`: `ensure chat`
4. Restart the server

## Editing the Chat

Now you can directly edit:

- **Styles**: Edit `html/index.css`
- **Logic**: Edit `html/app.js`
- **Layout**: Edit `html/index.html`
- **Configuration**: Modify the `CONFIG` object at the beginning of `app.js`

**No recompilation needed!** Just restart the resource in FiveM.

## Features Maintained

✅ All original functionalities have been preserved:
- Message system
- Message templates
- Command suggestions
- Chat modes
- Dynamic themes
- Message history
- Keyboard shortcuts
- Visibility states
- Animations

## Tested

- ✅ Vue.js loading
- ✅ Message rendering
- ✅ Input system
- ✅ Message events
- ✅ FiveM compatibility
- ✅ Scrollbars removed

## Advantages

- **Fast editing**: Change and test immediately
- **No dependencies**: No need to install Node.js, yarn, etc.
- **Simpler**: Fewer files to manage
- **Same result**: Identical functionalities to the original

## Pictures

### Default Theme
[Default Theme](https://imgur.com/kIowbiV)

### GTA:O Theme (chat-theme-gtao)
[GTA:O Theme](https://imgur.com/TxCmI07)