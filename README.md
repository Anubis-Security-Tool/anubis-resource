# 🎨 Anubis brand resources

Cross-platform application icons, logos and build assets for Anubis-Security-Tool,
published under `@ai-security-tool/resource`. Existing asset filenames and layouts
are retained for compatibility.

[Website](https://anubis.locker) · [Wiki](https://github.com/Anubis-Security-Tool/anubis/wiki) · [Desktop](https://github.com/Anubis-Security-Tool/anubis) · [Web](https://github.com/Anubis-Security-Tool/anubis-web)

> The new artwork is a source candidate, not confirmation of an updated installed
> client or a newly published resource package.

## Package and source status

`@ai-security-tool/resource@2.2.3` is the release candidate for the branding
assets from source commit `7ee004769d437e7f17c85a45cf561ce54b2122d0`.
It contains the same 47 generated resource files across the `build`, `build-res`
and `res` layouts, without artwork changes. The asset descriptions below refer
to this candidate, not a verified inventory of an earlier `2.2.2` package.
The version in `package.json` alone does not establish registry publication.

The canonical product documentation is the [Anubis Wiki](https://github.com/Anubis-Security-Tool/anubis/wiki).
These resources do not establish that native bootstrap, an installed client
update or a release has been completed.

## Artwork and attribution

The generated monogram and vector wordmark are original Anubis artwork (MIT).
The separately supplied PNG has its own provenance below.

Design: a white angular A monogram on a charcoal `#111111` rounded tile,
with no gradients or decorative shield. The reusable master is `src/icon.svg`.
Small navigation icons remain the application's existing Lucide monoline set
(ISC); no third-party icons are redrawn or relicensed here.

The MIT original-artwork statement does not apply to the separately supplied
logo. `src/background-logo.png`
is the unmodified, user-provided image downloaded from
https://loader-api.com/logo.png (1113x224 RGBA; SHA-256
`0f9bb589b8dbc1d8d6f05141a5b23ec354d4d60fccec29d8e72f3862937a30e8`).
It is retained as provided, without a new licensing assertion.

The logo is contained, without stretching, in the existing 766x266 canvas.
Only its alpha channel is multiplied by 0.7 for the default background; RGB
values are unchanged. The about/loading lockup uses the full-opacity logo on
a dark plate for contrast. User background, window-opacity and filter settings
are not changed. Both App and Web resolve/copy these same local `res/imgs`
files through `BRAND_RES_DIR`; no runtime network request is required.

## Build / verify
```
npm run build     # bin/build-assets.js from src/icon.svg
npm run build:icons # platform icons, tray and NSIS bitmaps
npm run verify    # file list + dimensions vs original inventory
```

## Asset → usage
| File | Size | Usage |
|---|---|---|
| res/imgs/electerm.png | 766x266 | Logo lockup (about/welcome) |
| res/imgs/electerm.svg | 766x266 | Self-contained lockup with embedded supplied PNG |
| res/imgs/electerm-watermark.png | 766x266 | Supplied logo at 70% source alpha |
| res/imgs/electerm-round-128x128.png | 766x766 | App icon (legacy filename; window/tray/web) |
| build/icons-win.ico, build/icons.ico | multi-size | Windows exe/installer |
| build/icons.icns | multi-size | macOS |
| build-res/linux/{16,24,32,48,64,128,256,512,1024}x*.png | square | Linux packages |
| build-res/appx/Square150x150Logo.png, Square44x44Logo.png, StoreLogo.png (1080), Wide310x150Logo.png | as named | Windows Store/appx |

`npm pack` and `npm publish` generate and verify both asset sets automatically.
The `res/icons` layout supplies Windows ICO, macOS ICNS, Linux and tray PNGs,
plus 24-bit NSIS header/sidebar BMPs. These files must be included in the
published package; checking only the legacy `build` layout is insufficient.
Verification also compares every background pixel against the resized source
(unchanged RGB, rounded 70% alpha) and checks that generated platform PNGs are
monochrome. No downloads are performed by the generator.
