Tak, bo GitHub README musi być w czystym Markdownie. Wklej bez :::writing, bez dziwnych znaków i najlepiej z normalnymi tabelami.

# zmk-config-sofleft

## PL

Konfiguracja ZMK dla **Sofle FT** - klawiatury ergonomicznej FalbaTech z enkoderami.

## Hardware

- Shield: `sofle` (oficjalny w upstream ZMK)
- Kontrolery: 2x nice!nano v2
- Wyświetlacz: OLED SSD1306 lub nice!view, zależnie od buildu
- RGB: per-key WS2812, 30 LED na każdej połówce, bez underglow
- 2x enkoder, po jednym na każdej połówce
- 60 klawiszy, 5 rzędów x 6 kolumn + 5 thumb na stronę

## Warstwy

| # | Nazwa | Funkcja |
|---|---|---|
| 0 | `default_layer` | QWERTY base |
| 1 | `lower_layer` | Cyfry, F-keys, aktywowane lewym thumbem |
| 2 | `raise_layer` | Symbole, nawigacja, aktywowane prawym thumbem |
| 3 | `adjust_layer` | System, RGB controls, BT controls |

## Enkodery

### Warstwa BASE

- Lewy enkoder: głośność, Volume Up/Down
- Prawy enkoder: Page Up/Down

### Warstwa ADJUST

- Lewy enkoder: jasność ekranu
- Prawy enkoder: głośność

## ZMK Studio

ZMK Studio jest aktywne.

Procedura odblokowania jest taka sama we wszystkich klawiaturach FalbaTech FT:

> Trzymaj oba thumby aktywujące warstwy systemowe, LOWER + RAISE, i wciśnij skrajny lewy górny klawisz, ` / ESC.

Po odblokowaniu klawiatura jest edytowalna z poziomu przeglądarki:

https://zmk.studio

## Bluetooth - obsługa 5 urządzeń

Klawiatura obsługuje 5 niezależnych profili Bluetooth. Przełączanie odbywa się w warstwie systemowej `adjust_layer`.

| Klawisz | Funkcja |
|---|---|
| `Z` | Profil BT 0 |
| `X` | Profil BT 1 |
| `C` | Profil BT 2 |
| `V` | Profil BT 3 |
| `B` | Profil BT 4 |
| `N` | Wyczyść aktywny profil |
| `M` | Wyczyść wszystkie profile |
| `,` | Tryb USB |
| `.` | Tryb Bluetooth |

## RGB controls

Sterowanie RGB znajduje się w warstwie `adjust_layer`.

| Klawisz | Funkcja |
|---|---|
| Górny rząd F-keys / RGB | F1-F10 |
| Środkowy rząd RGB | Hue/Saturation +/- |
| `EP_TOG` | External power on/off |

## Build

GitHub Actions buduje 5 plików firmware:

- `sofle_left-OLED-zmk.uf2` - lewa połówka z OLED + Studio
- `sofle_left-niceview-zmk.uf2` - lewa połówka z nice!view + Studio
- `sofle_right-OLED-zmk.uf2` - prawa połówka z OLED
- `sofle_right-niceview-zmk.uf2` - prawa połówka z nice!view
- `settings_reset-zmk.uf2` - reset ustawień

## Flashowanie

1. Podłącz lewą połówkę przez USB.
2. Naciśnij RESET dwa razy szybko.
3. Przeciągnij odpowiedni plik `sofle_left-...uf2` na dysk `NICENANO`.
4. Podłącz prawą połówkę przez USB.
5. Naciśnij RESET dwa razy szybko.
6. Przeciągnij odpowiedni plik `sofle_right-...uf2`.
7. Połącz obie połówki przewodem TRRS.
8. Sparuj klawiaturę jako "Sofle FT" przez Bluetooth.

## Wsparcie

FalbaTech  
https://falbatech.click

---

## EN

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
