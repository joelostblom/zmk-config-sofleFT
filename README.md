# zmk-config-sofleft

Konfiguracja ZMK dla **Sofle FT** - klasyczny Sofle 58/60 klawiszy z enkoderami i RGB.

## Hardware

- Shield: `sofle` (oficjalny w upstream ZMK)
- Kontrolery: 2× nice!nano v2
- Wyświetlacz: **OLED LUB nice!view** (firmware buduje obie wersje)
- Enkodery: oba (lewy i prawy)
- Per-key RGB: 30 LED WS2812 na każdej połówce (bez underglow)
- 60 klawiszy (5 rzędów + 5 thumb cluster na stronę)

## Wybór wyświetlacza

Repo buduje **5 firmware'ów** - wybierasz UF2 do flashowania zależnie od tego co masz fizycznie:

| Plik UF2 | Co flashujesz |
|---|---|
| `sofle_left_oled-...uf2` | Lewa, masz OLED |
| `sofle_left_niceview-...uf2` | Lewa, masz nice!view |
| `sofle_right_oled-...uf2` | Prawa, masz OLED |
| `sofle_right_niceview-...uf2` | Prawa, masz nice!view |
| `settings_reset-...uf2` | Reset BLE settings (gdyby były problemy) |

**OLED** = standard Sofle (4 piny I2C: SDA/SCL/VCC/GND), tańszy, ale na BT zżera baterię (~20 mA).
**nice!view** = LCD niskiego poboru (~50 µA), znacznie dłuższa bateria, ale droższy i wymaga adapter PCB.

## Warstwy

| # | Nazwa | Aktywacja | Funkcja |
|---|-------|-----------|---------|
| 0 | BASE | bazowa | QWERTY |
| 1 | LOWER | lewy thumb (LOWER) | F-keys, cyfry, symbole |
| 2 | RAISE | prawy thumb (RAISE) | BT, strzałki, edit (cut/copy/paste) |
| 3 | ADJUST | LOWER + RAISE | RGB, ext_power, studio_unlock, bootloader |

## Enkodery

| Warstwa | Lewy enkoder | Prawy enkoder |
|---------|--------------|---------------|
| BASE | Volume +/- | PgUp / PgDn |
| LOWER | Volume +/- | PgUp / PgDn |
| RAISE | Volume +/- | PgUp / PgDn |
| ADJUST | Brightness display | Volume +/- |

## RGB w warstwie ADJUST (lewa ręka)

| Pozycja | Funkcja |
|---------|---------|
| `1` (rząd cyfr) | EXT_POWER toggle |
| `2/3` (rząd cyfr) | Hue −/+ (kolor) |
| `4/5` | Saturation −/+ |
| `6` | Następny efekt |
| `Q/W` (rząd QWERTY) | Brightness −/+ |
| `E/R` | Speed −/+ |
| `T` (Q rząd) | Sys reset |
| Thumb (LOWER) | RGB toggle ON/OFF |

`studio_unlock` = ESC (lewa górna pozycja w ADJUST).
`bootloader` = TAB (lewa, środkowy rząd w ADJUST).

## ZMK Studio

Aktywne. Lewa połówka ma snippet `studio-rpc-usb-uart`.

**Aby odblokować:**
1. Trzymaj `mo LOWER` + `mo RAISE` (oba thumby) → jesteś w ADJUST
2. Naciśnij `ESC` (lewa górna pozycja - to `studio_unlock`)
3. Na https://zmk.studio kliknij Connect

## Build

GitHub Actions buduje 5 firmware'ów automatycznie po każdym pushu. Czas pierwszego buildu ~25-30 min (5 firmware'ów to dłużej niż 3).

## Flashowanie

1. Wybierz lewy UF2 (oled lub niceview) → lewa USB → 2× reset → drag&drop
2. Wybierz prawy UF2 (taki sam wariant) → prawa USB → 2× reset → drag&drop
3. Połącz TRRS, podłącz lewą do USB → klawiatura **"Sofle FT"** w BT
