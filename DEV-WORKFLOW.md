# Development Workflow

This document explains how to develop `c2pa-ts-ldr` and use it in your indicator-extractor project without rebuilding manually.

## Setup (Already Complete! ✅)

Your `indicator-extractor` project uses a `file:` link to this package:
```json
"@trustnxt/c2pa-ts": "file:../c2pa-ts-ldr"
```

This creates a symlink in `node_modules/@trustnxt/c2pa-ts` → `/Users/lrosenth/JPEGTrust/c2pa-ts-ldr`

## Development Workflow

### Start Watch Mode

In the `c2pa-ts-ldr` directory, run:

```bash
npm run dev
```

This starts `tsup` in watch mode, which will:
- ✅ Automatically recompile TypeScript when you save changes
- ✅ Update the `dist/` folder immediately
- ✅ Make changes instantly available to `indicator-extractor`

**Leave this running in a terminal while you develop!**

### Make Changes and Test

1. **Edit source files** in `c2pa-ts-ldr/src/`
2. **Save** → tsup automatically rebuilds
3. **Run tests** in indicator-extractor:
   ```bash
   cd /Users/lrosenth/JPEGTrust/indicator-extractor
   npm test
   ```

### One-Time Build

If you prefer to build manually instead of watch mode:

```bash
npm run build
```

## How It Works

- The `file:` link creates a symlink (like `npm link` but managed by npm)
- Changes to `c2pa-ts-ldr/dist/*` are immediately visible to `indicator-extractor`
- Watch mode keeps `dist/` in sync with `src/`
- No need to `npm install` after each change!

## Workflow Summary

```
Terminal 1 (c2pa-ts-ldr):
$ npm run dev
[Watching for changes...]

Terminal 2 (indicator-extractor):
$ npm test          # Run tests
$ node src/cli.js   # Test CLI
```

## Advantages of This Setup

✅ **No rebuild needed** - watch mode handles it  
✅ **Works for team** - `file:` link in package.json  
✅ **Survives npm install** - link is persistent  
✅ **Fast feedback** - changes reflect immediately  
✅ **No permissions issues** - no global npm access needed

