# PortaPack Mayhem — Custom Splash Screens

A collection of custom splash screens for the **HackRF One + PortaPack** running [Mayhem firmware](https://github.com/portapack-mayhem/mayhem-firmware).



## Preview

> 

| Screen | Preview |
|--------|---------|
| `splash_name.bmp` | ![preview](previews/splash_name.png) |

---

## What Is a Splash Screen?

The PortaPack displays a splash screen image on boot before loading the Mayhem UI. It is a **240×320 pixel BMP file** stored on the SD card. Swapping it out is one of the easiest ways to personalise your device.

---

## Requirements

- HackRF One
- PortaPack H1 or H2
- [Mayhem firmware](https://github.com/portapack-mayhem/mayhem-firmware) installed
- MicroSD card (FAT32 formatted)
- A way to write to the SD card (card reader / OTG adapter)

---

## Installation

### 1. Download

Clone the repo or download the `.bmp` file you want:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
```

Or download a single file directly from the **Releases** tab.

### 2. Copy to SD Card

Place the splash screen BMP on the **root** of your PortaPack's SD card and rename it:

```
/splash.bmp
```

Your SD card root should look like this:

```
SD Card (root)
├── splash.bmp        ← your custom splash screen
├── FIRMWARE/
├── APPS/
└── ...
```

### 3. Boot

Eject the SD card, insert it into the PortaPack, and power on. Your custom splash screen will display on startup.

---

## Image Specifications

All splash screens in this repo conform to the PortaPack Mayhem standard:

| Property | Value |
|----------|-------|
| Format | BMP (Windows Bitmap) |
| Width | 240 px |
| Height | 320 px |
| Color Depth | 24-bit RGB |
| File name | `splash.bmp` |

> **Note:** The PortaPack screen is 240×320 portrait orientation. Images that don't match this exact resolution may display incorrectly or fail to load.

---

## Creating Your Own

### Using GIMP

1. Open or create your image
2. **Image → Scale Image** → set to `240 × 320 px`
3. **File → Export As** → name it `splash.bmp`
4. In the BMP export dialog select **24 bit** color, no RLE compression
5. Copy to SD card root

### Using ImageMagick (CLI)

```bash
# Convert any image to the correct format
convert input.png -resize 240x320! -type TrueColor splash.bmp
```

### Using Python (Pillow)

```python
from PIL import Image

img = Image.open("input.png").resize((240, 320))
img.convert("RGB").save("splash.bmp")
```

---

## Reverting to Default

Delete `splash.bmp` from the SD card root. Mayhem will fall back to the built-in default splash on next boot.

---

## Compatibility

| Firmware | Compatible |
|----------|-----------|
| Mayhem v1.x | Yes |
| Mayhem v2.x | Yes |
| Mayhem nightly | Yes |
| Stock HackRF firmware | No (PortaPack only) |

Tested on **PortaPack H2** with Mayhem firmware. Should work on H1 as well — open an issue if you encounter problems.

---

## Contributing

Contributions welcome. If you have a splash screen to share:

1. Fork the repo
2. Add your `.bmp` file (240×320, 24-bit)
3. Add a preview image to `/previews/`
4. Update the preview table in this README
5. Open a pull request

Please keep submissions clean — no offensive imagery.

---

## License

All splash screens in this repository are released under [Creative Commons CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) unless otherwise noted in the file's folder.

Do whatever you want with them.

---

## Related Projects

- [Mayhem Firmware](https://github.com/portapack-mayhem/mayhem-firmware) — the PortaPack firmware these are made for
- [HackRF One](https://greatscottgadgets.com/hackrf/) — the SDR hardware
- [PortaPack](https://github.com/jboone/portapack) — the companion hardware

---

*Made for the HackRF / PortaPack community.*
