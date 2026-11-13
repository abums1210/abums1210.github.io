---
layout: post
title: "[ASI/III/VC/SA] EasyFont v1.2 - TTF/OTF Font Replacement System"
date: 2026-07-26 12:00:00 +0530
category: gtamodding
tags: gta3 gtavc gtasa font text modding
---

To read the original GTAForums post, [click here](https://gtaforums.com/topic/1006726-asiiiivcsa-easyfont-v10-ttfotf-font-replacement-system/).
If you like my work and want to support my mods, consider donating to [my Ko-fi page](https://ko-fi.com/abums1210) or my [Patreon](https://patreon.com/cw/abums1210). My mods will always be free to use.

**EasyFont v1.2** — TTF/OTF Font Rendering System that replaces existing bitmap system for GTA III, VC and SA.

<!--more-->

### Downloads:
- [NexusMods (latest version)](https://www.nexusmods.com/gtasanandreas/mods/3045)
- [Liberty City (latest version)](https://libertycity.net/files/247316-easyfont-ttfotf-font-replacement-system.html)
- [GTAInside (latest version)](https://www.gtainside.com/sanandreas/mods/modifications/224398-easyfont-v1-2-ttf-otf-hd-font-system-for-sa-vc-iii)
- [Mediafire Mirror (v1.2 III/VC/SA)](https://www.mediafire.com/file/y7o19cvirxwgmj0/III_VC_SA_EasyFont_v1dot2.zip/file)
- [Dropbox Mirror (v1.0 III/VC/SA)](https://www.dropbox.com/scl/fi/t1yw2ufkb4ijzddl756vz/III_VC_SA_EasyFont-v1.7z?rlkey=tcbbmtczg82ure8et621khtpc&st=xe9rjyri&dl=0)
- [Dropbox Link (Details PDF)](https://www.dropbox.com/scl/fi/cxymeylztf374aajfdafx/EasyFont-v1.0.pdf?rlkey=38zxy6wvisdbu425uyyep9bjr&st=a14vm370&dl=0)

### Changelog v1.2 (last updated on 11/11/2026 20:00 IST):
- Added GTAVI font presets.
- Added DirectImageRasterizer integration to render button sprites and symbols directly from .png.
- Fixed y-axis alignment issues.
- Fixed certain config preset values.

### Overview:
* Replace the bitmap font system used in the OG GTA Trilogy with high-quality replaceable TTF/OTF font equivalents!
* Try GTA game fontstyle defaults (or) Try your favourite custom font styles!
* Game specific buttons – now PC buttons get their dedicated button sprites like console. Each game gets their own styled buttons.
* GInput support for controller buttons.
* Complex Unicode character support – upto 40 language character sets tested. Screenshots below.
* FontStyleHooks – mapped the complete 60+ CFont::SetFontStyle calls in GTA3/VC/SA. Adjust their font styles on the go during runtime!
* Using FontStyleHooks – enable VCFontStyleHooks in GTA3 – allowing usage of 3 different fonts for HUD elements. You must enable this to use VC/SA/etc font style defaults correctly in GTA3.
* With help of EasyGXT, bring localization support to any language across the globe. Latin and Unicode, Left to Right or Right to Left – both supported.

### Configurable Features:
- Assign upto 4 fonts across games.
- Button icons in place of button text.
- Blip icons in place of blip descriptions. (VC/SA)
- Key to reload font settings in-game on the fly (Virtual Key code)
- Choose a Rendering method (1 = D3DX font sprite, 2 = GDI sprite)
- Replace text shadow with outline (1 = shadow size, >1 = exact thickness)
- Force uniform scaling for all fonts (1 = enable, 0 = disable)
- Force preconfigure default settings override for game style (-1 = off, 0 = GTA III, 1 = GTA VC, 2 = GTA SA, 3 = GTA IV, 4 = GTA V, 5 = GTA LCS, 6 = GTA VCS)
- Smooth outline quality (number of sampling points in a circle, e.g. 16)
- Outline size multiplier (defaults: 1.0f for III/VC, 2.0f for SA)
- Size scale multiplier of prompt buttons (default: 0.85)
- Override outline thickness (GTA SA only, -1 to disable)
- Enable Bidirectional & RTL layout support for Arabic/Hebrew/Urdu/Farsi (1 = enable, 0 = disable)
- Position offset (X Y) for Health/Armor HUD symbols
- Position offset (X Y) for Wanted star HUD symbols
- Scale multiplier (X Y) for Health/Armor symbols
- Scale multiplier (X Y) for Wanted star symbols
- Disable character slant/italic slant rendering (VC slanted location/vehicle texts)
- Follow natural character widths globally (1 = enable, 0 = disable) (useful for Unicode languages)
- Global Y coordinate offset for text rendering (tweak to adjust y-coord of PrintString)
- TrueType Font (.ttf or .otf) file name (give the correct file name – otherwise Arial will appear as fallback font)
- Font character set index (choose the character set in the .ttf/.otf file)
- Font size (height in pixels)
- Font width in pixels (0 for default)
- Antialiasing quality setting
- Width of space character (0 for default)
- Render font in italic (1 = enable, 0 = disable)
- Font weight (e.g. 400 = Normal, 700 = Bold)
- Line height spacing multiplier (0.0 for default)
- GXT token color adjustments – adjust the colors that modify text color when a GXT token like ~q~ is used.
- Font Style numbers for various calls (0,1,2,3) in font_styles.ini.

### Using system fonts:
You can also use preinstalled system fonts. Just replace the font file name in font_ttf.ini with the one present in C:/Windows/Fonts folder. I have given 3 samples.
- **Segoe UI** – Windows UI font.
- **Comic Sans MS** – popular goofy design font.
- **Determination** (not a system font, not a GTA font) – a pixel font used in popular indie games Undertale and Deltarune. This font is used in place of Pager font as default in GTA3.

### Blip icons in place of text:
Certain text describing blips are now replaced with actual blip sprites present in models/blips.txd. Square, triangle blips are drawn at runtime. This feature is only present in GTAVC/SA. III doesn't have a proper blip description as far as I saw.

### Localization with [EasyGXT](https://gtaforums.com/topic/1006231-asiiiivcsa-easygxt-v12/):
Due to TTF font support with Windows native font system, EasyFont allows usage of Unicode supported language characters. I have tested upto 40 non-Latin script languages all over the world and EasyFont can accurately draw the characters. You need to manually adjust the dimensions to suit your taste though. By default, these language characters will be drawn using standard system fonts – you can also name a specific font – if you have a copy of the .ttf/.otf or its installed in the system.

For SA, adjust encoding to UTF8 before trying a Unicode language. Native ANSI 1252 encoding is necessary to display accented characters correctly – so switch that if you want to run Spanish GXT.

I also provided a custom Beckett font containing accented chars for Spanish GXT.

III and VC come with wide character support – so they natively support UTF16-LE encoding.

For more details on localization, read this [blog post](/gtamodding/2026/07/29/GXT-CSV-Localization-Guide/).

### AddOns included:
- **UITweaks (III/VC/SA)**: Plugin which patches key HUD elements to be more like Definitive Edition. Generates config to adjust values of those elements. Used in the demo video and screenshots.
- **ReMessages.VC.asi**: Fixes a stack queue corruption associated with CMessages in GTAVC. Don’t remove this or you will get a crash while riding an ambulance.

### Screenshots:
![Screenshot 1](https://gtaforums.com/uploads/monthly_2026_07/image.png.c7064f143de5ef873b1fdc53fcae9b3a.png)
![Screenshot 2](https://gtaforums.com/uploads/monthly_2026_07/image.png.5b84f0245ae869eff3ff3874e13beb23.png)
![Font Styles](https://gtaforums.com/uploads/monthly_2026_07/image.jpeg.ca029686a7e59b5e5f3ef3b0fc2409ba.jpeg)
![System Fonts](https://gtaforums.com/uploads/monthly_2026_07/image.jpeg.270a9495c4934704c791bdee0783544b.jpeg)
![Blip Icons](https://gtaforums.com/uploads/monthly_2026_07/image.jpeg.98aa97c4fc620bc127f1e1c1035cbfa6.jpeg)
![Tamil Translation](https://gtaforums.com/uploads/monthly_2026_07/image.png.8961c1b831ba1a4b2934081c30f231cc.png)
