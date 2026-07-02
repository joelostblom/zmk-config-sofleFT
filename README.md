# zmk-config-sofleft

ZMK configuration for **Sofle FT** - ergonomic FalbaTech keyboard with encoders.

## Hardware

- Shield: `sofle` (official upstream ZMK shield)
- Controllers: 2x nice!nano v2
- Display: OLED SSD1306 or nice!view, depending on build
- RGB: per-key WS2812, 30 LEDs on each half, without underglow
- 2x encoders, one on each half
- 60 keys, 5 rows x 6 columns + 5 thumb keys per side

## Layers

| # | Name | Function |
|---|---|---|
| 0 | `default_layer` | QWERTY base |
| 1 | `lower_layer` | Numbers, F-keys, activated by left thumb |
| 2 | `raise_layer` | Symbols, navigation, activated by right thumb |
| 3 | `adjust_layer` | System, RGB controls, BT controls |

## Encoders

### BASE layer

- Left encoder: volume, Volume Up/Down
- Right encoder: Page Up/Down

### ADJUST layer

- Left encoder: screen brightness
- Right encoder: volume

## ZMK Studio

ZMK Studio is enabled.

The unlock procedure is the same across all FalbaTech FT keyboards:

> Hold both thumb keys activating system layers, LOWER + RAISE, and press the top left key, ` / ESC.

After unlocking, the keyboard can be configured from your browser:

https://zmk.studio

## Bluetooth - 5 device support

The keyboard supports 5 independent Bluetooth profiles. Switching is done in the system layer `adjust_layer`.

| Key | Function |
|---|---|
| `Z` | BT Profile 0 |
| `X` | BT Profile 1 |
| `C` | BT Profile 2 |
| `V` | BT Profile 3 |
| `B` | BT Profile 4 |
| `N` | Clear active profile |
| `M` | Clear all profiles |
| `,` | USB mode |
| `.` | Bluetooth mode |

## RGB controls

RGB controls are located in the `adjust_layer`.

| Key | Function |
|---|---|
| Top F-key / RGB row | F1-F10 |
| Middle RGB row | Hue/Saturation +/- |
| `EP_TOG` | External power on/off |

## Build

GitHub Actions builds 5 firmware files:

- `sofle_left-OLED-zmk.uf2` - left half with OLED + Studio
- `sofle_left-niceview-zmk.uf2` - left half with nice!view + Studio
- `sofle_right-OLED-zmk.uf2` - right half with OLED
- `sofle_right-niceview-zmk.uf2` - right half with nice!view
- `settings_reset-zmk.uf2` - settings reset

## Flashing

1. Connect the left half via USB.
2. Press RESET twice quickly.
3. Drag the appropriate `sofle_left-...uf2` file onto the `NICENANO` drive.
4. Connect the right half via USB.
5. Press RESET twice quickly.
6. Drag the appropriate `sofle_right-...uf2` file.
7. Connect both halves using a TRRS cable.
8. Pair the keyboard as "Sofle FT" over Bluetooth.

## Support

FalbaTech  
https://falbatech.click
