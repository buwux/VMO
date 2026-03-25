"""
# VMO Spider Bot 🕷️
 
A WiFi-controlled spider robot pet with personality, emotions, and an IGCSE teaching mode — built from scratch by Buwuz.
 
![VMO Front](VMO-SpiderBot/images/ Actual VMO)
 
## What is VMO?
 
VMO is a quadruped spider robot powered by an ESP32-WROOM-DA. It has 8 servo-driven legs, an OLED face that displays 16 animated expressions, a speaker that produces Animal Crossing-style robot sounds, and a touch sensor for physical interaction. VMO develops a personality over time based on how you interact with it (playful, cuddly, chaotic, or chill), maintains mood/energy/XP stats, and can even teach IGCSE Further Math, Chemistry, and Physics through animated diagrams on its 1.3" OLED screen.
 
Everything is controllable from your iPhone via a built-in WiFi web interface.
 
## Why I made this
 
I wanted to build a robot that felt alive — not just a servo test or a remote control car, but something with genuine personality that reacts to touch, has emotions, sleeps, dreams, dances, and can even help me study for my IGCSE exams. I designed and 3D printed the entire body on my Ender 3 V3 KE, hand-wired all the electronics on a breadboard, and wrote every line of firmware from scratch.
 
## Features
 
- **16 animated OLED faces**: UwU, OwO, ^w^, T-T, *o*, - -, <3, :D, #!?, @_@, >:[, hehe, o.O, B), 0w0, ^o^
- **30+ synthesized sounds**: Robot babble voice, chords, pitch slides, melodies, lullaby, purring
- **8 servo legs** via PCA9685 I2C PWM driver — calibrated with custom min/max/center per servo
- **WiFi control**: ESP32 hosts a web server at 192.168.4.1 with full phone UI
- **Phone UI includes**: Face selector, 10 action buttons, D-pad walking, 12 sound buttons, live stats, IGCSE teaching mode
- **Touch sensor**: 1 tap = wave, 2 = dance, 3 = party, 5 = easter egg, hold = pet with purring
- **Personality AI**: Develops preferences based on interaction (playful/cuddly/chaotic/chill)
- **Mood, Energy, XP system** with level progression (Lv1-5)
- **Sleep mode**: Auto-sleeps after 2 min idle, snores, dreams (thought bubbles), cute wake-up sequence
- **IGCSE Teaching Mode**: 12 animated topic explainers across Further Math, Chemistry, Physics
- **Cinematic boot**: Scanline wipe → matrix rain → spider build with heartbeat → glitch → typewriter → diagnostics
- **Rare events**: Random lullaby singing, sparkle bursts, level-up celebrations
- **Walking gaits**: Forward, backward, left, right via phone D-pad
- **Brownout protected** for LiPo battery operation
 
## How to use
 
1. Power VMO via LiPo battery (2S or 4S through LM2596 set to 5V) or USB
2. On your phone, connect to WiFi network "VMO-Spider" (password: buwuz2026)
3. Open Safari and go to 192.168.4.1
4. Use the web UI to control faces, actions, walking, sounds, and teaching mode
5. Or interact physically — touch the sensor to pet, tap patterns for commands
 
## Hardware
 
| Component | Details |
|---|---|
| MCU | ESP32-WROOM-DA |
| Display | 1.3" SSH1106 OLED (I2C, 0x3C) |
| Servo Driver | PCA9685 16-ch PWM (I2C, 0x40) |
| Servos | 8x MG90S (7 working + 1 continuous rotation disabled) |
| Speaker Amp | MAX98357A I2S |
| Speaker | 4/8 ohm |
| Touch Sensor | Digital touch module |
| Power | LiPo battery → BMS → LM2596 DC-DC (set to 5V) |
| Body | 3D printed on Ender 3 V3 KE |
 
## Wiring
 
| Device | ESP32 Pin |
|---|---|
| OLED SDA + PCA9685 SDA | GPIO 21 (shared I2C) |
| OLED SCL + PCA9685 SCL | GPIO 22 (shared I2C) |
| MAX98357A BCLK | GPIO 14 |
| MAX98357A LRC | GPIO 27 |
| MAX98357A DIN | GPIO 25 |
| Touch Sensor Signal | GPIO 4 |
| PCA9685 V+ | 5V from LM2596 |
| PCA9685 VCC | 3.3V |
| PCA9685 OE | GND |
| Everything VCC (3.3V devices) | ESP32 3.3V rail |
| All GND | Common ground |
 
![Wiring Diagram](wiring/wiring_diagram.png)
 
## Servo Calibration
 
Each servo was individually calibrated using a custom WiFi calibration tool:
 
| Channel | Joint | Min | Center | Max | Mirrored |
|---|---|---|---|---|---|
| 0 | FL Hip | 94 | 160 | 250 | No |
| 1 | FL Knee | 0 | 131 | 250 | No |
| 2 | FR Hip | 65 | 133 | 250 | Yes |
| 3 | FR Knee | 40 | 130 | 210 | Yes (disabled - continuous rotation) |
| 4 | BL Hip | 0 | 135 | 250 | Yes |
| 5 | BL Knee | 44 | 168 | 250 | No |
| 6 | BR Hip | 4 | 140 | 240 | Yes |
| 7 | BR Knee | 0 | 125 | 220 | Yes |
 
## IGCSE Teaching Topics
 
**Further Math**: Differentiation, Integration, Matrices, Vectors
**Chemistry**: Bonding, Moles, Equations, Organic Chemistry
**Physics**: Circuits, Forces, Waves, Energy
 
Each topic has 3-4 animated pages with diagrams, formulas, and visual explanations on the OLED.
 
## 3D Model
 
![3D Model](images/vmo_cad.png)
 
The full STEP file is in the `cad/` folder. Designed in Fusion 360 and printed on an Ender 3 V3 KE in PLA.
 
## Phone UI
 
![Phone UI](images/vmo_phone.jpg)
 
## BOM
 
| Part | Quantity | Cost (USD) | Link |
|---|---|---|---|
| ESP32-WROOM-DA Module | 1 | $6 | [Shopee](https://shopee.co.th) |
| PCA9685 16-ch PWM Driver | 1 | $3 | [Shopee](https://shopee.co.th) |
| MG90S Servo | 8 | $16 | [Shopee](https://shopee.co.th) |
| SSH1106 1.3" OLED I2C | 1 | $4 | [Shopee](https://shopee.co.th) |
| MAX98357A I2S Amp | 1 | $3 | [Shopee](https://shopee.co.th) |
| Small Speaker (4/8 ohm) | 1 | $1 | [Shopee](https://shopee.co.th) |
| Touch Sensor Module | 1 | $1 | [Shopee](https://shopee.co.th) |
| LM2596 DC-DC Buck | 1 | $2 | [Shopee](https://shopee.co.th) |
| 2S BMS Board | 1 | $2 | [Shopee](https://shopee.co.th) |
| Li-ion 18650 Cells (2S) | 2 | $8 | [Shopee](https://shopee.co.th) |
| Breadboard + Jumper Wires | 1 set | $3 | [Shopee](https://shopee.co.th) |
| PLA Filament (3D print) | ~100g | $3 | Already owned |
| **TOTAL** | | **~$52** | |
 
## License
 
MIT
"""
