:::writing{variant=“standard” id=“46285”}

zmk-config-sofleft

PL

Konfiguracja ZMK dla Sofle FT - klawiatura ergonomiczna FalbaTech z enkoderami.

Hardware
	•	Shield: sofle (oficjalny w upstream ZMK)
	•	Kontrolery: 2× nice!nano v2
	•	Wyświetlacz: OLED SSD1306 lub nice!view (zależnie od buildu)
	•	RGB: per-key WS2812, 30 LED na każdej połówce (bez underglow)
	•	2× enkoder (po jednym na każdej połówce)
	•	60 klawiszy (5 rzędów × 6 kolumn + 5 thumb na stronę)

Warstwy

#	Nazwa	Funkcja
0	default_layer	QWERTY base
1	lower_layer	Cyfry, F-keys (lewy thumb aktywuje)
2	raise_layer	Symbole, nawigacja (prawy thumb aktywuje)
3	adjust_layer	System, RGB controls, BT controls (oba thumby + LOWER + RAISE)

Enkodery

Warstwa BASE:
	•	Lewy enkoder: głośność (Volume Up/Down)
	•	Prawy enkoder: page up/down

Warstwa ADJUST:
	•	Lewy enkoder: brightness ekranu
	•	Prawy enkoder: głośność

ZMK Studio

Aktywne. Procedura odblokowania (jednakowa we wszystkich klawiaturach FalbaTech FT):

Trzymaj oba thumby aktywujące warstwy systemowe (LOWER + RAISE) → wciśnij skrajny lewy górny klawisz (` / ESC).

Po odblokowaniu klawiatura jest edytowalna z:
zmk.studio￼

Bluetooth - obsługa 5 urządzeń

Klawiatura obsługuje 5 niezależnych profili Bluetooth. W warstwie systemowej (adjust_layer):

Klawisz	Funkcja
Z	Profil BT 0
X	Profil BT 1
C	Profil BT 2
V	Profil BT 3
B	Profil BT 4
N	Wyczyść aktywny profil
M	Wyczyść wszystkie profile
,	Tryb USB
.	Tryb Bluetooth

RGB controls (warstwa adjust_layer)

Klawisz	Funkcja
Górny rząd F-keys / RGB	F1-F10 zamapowane
Środkowy rząd RGB	Hue/Saturation +/-
EP_TOG	External power on/off

Build

GitHub Actions buduje 5 firmware:
	•	sofle_left-OLED-zmk.uf2 (lewa z OLED + Studio)
	•	sofle_left-niceview-zmk.uf2 (lewa z nice!view + Studio)
	•	sofle_right-OLED-zmk.uf2 (prawa z OLED)
	•	sofle_right-niceview-zmk.uf2 (prawa z nice!view)
	•	settings_reset-zmk.uf2

Flashowanie
	1.	Lewa USB - 2× reset - przeciągnij odpowiedni sofle_left-...uf2
	2.	Prawa USB - 2× reset - odpowiedni sofle_right-...uf2
	3.	Połącz TRRS - klawiatura “Sofle FT” w BT

Wsparcie

FalbaTech - https://falbatech.click

⸻

EN

ZMK configuration for Sofle FT - ergonomic FalbaTech keyboard with encoders.

Hardware
	•	Shield: sofle (official upstream ZMK shield)
	•	Controllers: 2× nice!nano v2
	•	Display: OLED SSD1306 or nice!view (depending on build)
	•	RGB: per-key WS2812, 30 LEDs on each half (without underglow)
	•	2× encoders (one on each half)
	•	60 keys (5 rows × 6 columns + 5 thumb keys per side)

Layers

#	Name	Function
0	default_layer	QWERTY base
1	lower_layer	Numbers, F-keys (left thumb activates)
2	raise_layer	Symbols, navigation (right thumb activates)
3	adjust_layer	System, RGB controls, BT controls (both thumbs + LOWER + RAISE)

Encoders

BASE layer:
	•	Left encoder: volume (Volume Up/Down)
	•	Right encoder: page up/down

ADJUST layer:
	•	Left encoder: screen brightness
	•	Right encoder: volume

ZMK Studio

Enabled. Unlock procedure (same across all FalbaTech FT keyboards):

Hold both thumb keys activating system layers (LOWER + RAISE) → press the top left key (` / ESC).

After unlocking, the keyboard can be configured from:
zmk.studio￼

Bluetooth - 5 device support

The keyboard supports 5 independent Bluetooth profiles. In the system layer (adjust_layer):

Key	Function
Z	BT Profile 0
X	BT Profile 1
C	BT Profile 2
V	BT Profile 3
B	BT Profile 4
N	Clear active profile
M	Clear all profiles
,	USB mode
.	Bluetooth mode

RGB controls (adjust_layer)

Key	Function
Top row F-keys / RGB	F1-F10 mapped
Middle RGB row	Hue/Saturation +/-
EP_TOG	External power on/off

Build

GitHub Actions builds 5 firmware files:
	•	sofle_left-OLED-zmk.uf2 (left with OLED + Studio)
	•	sofle_left-niceview-zmk.uf2 (left with nice!view + Studio)
	•	sofle_right-OLED-zmk.uf2 (right with OLED)
	•	sofle_right-niceview-zmk.uf2 (right with nice!view)
	•	settings_reset-zmk.uf2

Flashing
	1.	Left USB - press reset 2× - drag the appropriate sofle_left-...uf2
	2.	Right USB - press reset 2× - drag the appropriate sofle_right-...uf2
	3.	Connect TRRS - keyboard appears as “Sofle FT” over Bluetooth

Support

FalbaTech - https://falbatech.click
:::
