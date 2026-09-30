🎮 LUMIGAME v2.4 — Arduino Handheld / Arcade Console

LUMIGAME ni mfumo wa michezo ya kielektroniki wa aina ya Arcade Console, uliojengwa kwa kutumia Arduino UNO.

Mfumo huu unatumia MAX7219 Dot Matrix Modules 4× (16×16 LED Grid) kama display kuu ya michezo, pamoja na OLED SSD1306 0.96" I²C kwa ajili ya menyu, score, level, lives na taarifa nyingine za mfumo.

«🇹🇿 Built in Tanzania • Designed & Built by Ibrahim Salehe»

---

🚀 Features

🌍 Dual Language

LUMIGAME inasaidia lugha mbili:

- 🇹🇿 Kiswahili
- 🇬🇧 English

🎮 Games

LUMIGAME ina michezo 5 tofauti:

#| Game| Description
1| 🏓 PONG| Mchezo wa mpira na paddle dhidi ya AI
2| 🐍 NYOKA / SNAKE| Nyoka anayekula chakula na kukua
3| 🧱 BRICK / BREAKOUT| Kuvunja matofali kwa kutumia mpira
4| 👾 INVADERS| Kupambana na viumbe vya angani
5| 🐤 FLAPPY| Kuruka kupitia vikwazo bila kugonga

📊 OLED HUD

OLED display hutumika kuonyesha taarifa muhimu wakati wa mchezo:

- ❤️ Lives
- 🏆 Score
- 📈 Level
- 🎮 Game status
- 📋 Menus

💾 EEPROM High Score

LUMIGAME hutumia Arduino EEPROM kuhifadhi high score.

Hii inamaanisha kuwa alama ya juu inaweza kubaki kwenye mfumo hata baada ya kuzima umeme.

🕹️ Controls

Mchezaji anaweza kutumia:

- Joystick — movement
- OK — Select / Confirm
- LEFT — Menu navigation
- RIGHT — Menu navigation

---

🛠️ Hardware Requirements

Main Components

Component| Quantity| Purpose
Arduino UNO| 1×| Main controller
MAX7219 8×8 Dot Matrix Module| 4×| 16×16 game display
OLED 0.96" SSD1306| 1×| Menu, score, level and status
Joystick Module (XY + SW)| 1×| Game control
Tactile Push Buttons| 3×| OK, LEFT and RIGHT
5V 2A DC Adapter| 1×| External power supply
Jumper Wires| —| Electrical connections
Breadboard| 1×| Prototyping

MAX7219 Display Layout

The four MAX7219 modules are arranged as a 2×2 matrix:

┌─────────┬─────────┐
│ MAX #1  │ MAX #2  │
│  8 × 8  │  8 × 8  │
├─────────┼─────────┤
│ MAX #3  │ MAX #4  │
│  8 × 8  │  8 × 8  │
└─────────┴─────────┘

       16 × 16
      LED Grid

---

🔌 Wiring

«⚠️ IMPORTANT: The external 5V power supply and Arduino must share a common GND. Connect the GND of the external power supply to Arduino GND.»

1. MAX7219 Matrix — Daisy Chain

MAX7219 Pin| Connection| Arduino / Target| Wire Color
DIN| Data In| D12| 🟡 Yellow
CS| Chip Select| D10| 🟢 Green
CLK| Clock| D11| 🔵 Blue
VCC| Power| External 5V Rail| 🔴 Red
GND| Ground| External GND Rail| ⚫ Black
DOUT #1| Data Out| DIN #2| 🟣 Purple
DOUT #2| Data Out| DIN #3| 🟠 Orange
DOUT #3| Data Out| DIN #4| 🌸 Pink

Daisy Chain

Arduino D12
     │
     ▼
  DIN #1
  MAX7219
     │
    DOUT
     │
     ▼
  DIN #2
  MAX7219
     │
    DOUT
     │
     ▼
  DIN #3
  MAX7219
     │
    DOUT
     │
     ▼
  DIN #4
  MAX7219

D10 (CS) na D11 (CLK) zinashirikishwa na modules zote.

---

2. OLED Display — SSD1306 I²C

OLED Pin| Arduino Pin| Wire Color
VCC| 5V Power Rail| 🔴 Red
GND| GND Rail| ⚫ Black
SDA| A4| 🔵 Blue
SCL| A5| 🟡 Yellow

---

3. Joystick & Buttons

Device| Pin| Arduino Pin| Function
Joystick| VRx| A0| X Axis — Left / Right
Joystick| VRy| A1| Y Axis — Up / Down
Joystick| SW| D5| Joystick Button
OK Button| Terminal 1| D2| Select / Confirm
LEFT Button| Terminal 1| D3| Menu Left
RIGHT Button| Terminal 1| D4| Menu Right

All button second terminals are connected to:

GND

The digital buttons use:

INPUT_PULLUP

---

🧩 Pin Summary

Arduino Pin| Function
D2| OK Button
D3| LEFT Button
D4| RIGHT Button
D5| Joystick SW
D10| MAX7219 CS
D11| MAX7219 CLK
D12| MAX7219 DIN
A0| Joystick VRx
A1| Joystick VRy
A4| OLED SDA
A5| OLED SCL

---

📚 Required Arduino Libraries

Install the following libraries through the Arduino IDE Library Manager:

1. Adafruit GFX Library
2. Adafruit SSD1306
3. LedControl — by Eberhard Fahle

Library Installation

Open:

Arduino IDE
    ↓
Library Manager
    ↓
Search Library
    ↓
Install

---

⚙️ Installation & Setup

1. Clone the Repository

git clone https://github.com/luminexa-creator/LUMIGAME.git

Then enter the project directory:

cd LUMIGAME

2. Open the Project

Open the Arduino source code in:

- Arduino IDE
- Arduino IDE 2.x

3. Install Required Libraries

Install all libraries listed in the Required Arduino Libraries section.

4. Connect the Hardware

Connect:

Arduino UNO
     │
     ├── MAX7219 ×4
     ├── OLED SSD1306
     ├── Joystick
     └── Push Buttons

Connect the external 5V 2A supply to the MAX7219 power rail and ensure that all components share a common GND.

5. Select Arduino Board

In Arduino IDE:

Tools
  → Board
    → Arduino AVR Boards
      → Arduino UNO

Select the correct COM/serial port.

6. Upload

Click:

Upload

After uploading, LUMIGAME should start automatically.

---

🎮 Controls

Control| Action
🕹️ Joystick Up| Move Up
🕹️ Joystick Down| Move Down
🕹️ Joystick Left| Move Left
🕹️ Joystick Right| Move Right
🕹️ Joystick SW| Additional action
OK| Select / Confirm
LEFT| Navigate Left
RIGHT| Navigate Right

Controls may vary depending on the selected game.

---

🏗️ System Architecture

                    ┌────────────────────┐
                    │    Arduino UNO     │
                    │   Main Controller  │
                    └─────────┬──────────┘
                              │
            ┌─────────────────┼─────────────────┐
            │                 │                 │
            ▼                 ▼                 ▼
     ┌────────────┐    ┌────────────┐    ┌────────────┐
     │ MAX7219 ×4 │    │ OLED 0.96" │    │  Controls  │
     │  16×16 LED │    │  SSD1306   │    │ Joystick + │
     │   Matrix   │    │    I²C     │    │  Buttons   │
     └────────────┘    └────────────┘    └────────────┘

---

🔋 Power Architecture

             5V 2A DC Adapter
                     │
                     ▼
             ┌───────────────┐
             │ Power Rail    │
             └───────┬───────┘
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
      MAX7219 ×4   OLED      Arduino*
          │          │          │
          └──────────┴──────────┘
                     │
                    GND
                     │
             Common Ground

«Note: Ensure the power arrangement is appropriate for the exact Arduino UNO board and modules being used. Avoid drawing excessive current through the Arduino's 5V regulator.»

---

📁 Suggested Project Structure

LUMIGAME/
│
├── LUMIGAME.ino
├── README.md
├── LICENSE
│
├── src/
│   ├── menu.ino
│   ├── pong.ino
│   ├── snake.ino
│   ├── brick.ino
│   ├── invaders.ino
│   └── flappy.ino
│
├── docs/
│   ├── wiring.md
│   └── pinout.md
│
└── images/
    ├── lumigame.jpg
    ├── wiring.jpg
    └── gameplay.jpg

---

🧪 Project Status

Version: "v2.4"

Platform: Arduino UNO

Display: 16×16 MAX7219 Matrix + OLED SSD1306

Games: 5

Language: Kiswahili / English

Storage: EEPROM High Score

Status: 🚧 Active Development

---

🔮 Future Improvements

Possible future versions may include:

- 🔊 Sound effects
- 🎵 Game music
- 🎮 More games
- 💾 Multiple saved profiles
- 🏆 Multiple high-score tables
- 🔋 Rechargeable battery system
- 🔌 USB charging
- 🎨 Improved graphics
- 🕹️ Custom handheld enclosure
- 📦 3D-printed console body
- ⚡ Improved power management
- 🖥️ Larger display support

---

👨‍💻 Creator

Ibrahim Salehe

Founder & Builder — LUMINEXA

🇹🇿 Tanzania, East Africa

LUMIGAME is an independent electronics and embedded-systems project focused on learning, experimentation, game development, and hardware engineering.

---

📜 License

This project is intended for educational, experimental, and personal maker use.

See the ""LICENSE"" (LICENSE) file for the complete license terms.

---

⭐ Support the Project

If you find LUMIGAME interesting:

⭐ Star the repository
🍴 Fork the project
🐛 Report bugs
💡 Suggest improvements
🔧 Build your own version

LUMIGAME — Small Hardware. Big Ideas. 🇹🇿
