# Ploopy Knob Haptic Feedback Mod

This repository contains instructions for adding haptic feedback to the Ploopy Knob. Buzz buzz!. This mod uses a small vibration motor controlled by a MOSFET to provide tactile feedback on knob rotations, creating a "detent" feel that is configured entirely using QMK firmware.

This guide assumes you have basic soldering experience, particularly with surface-mount (SMD) components.

---

## ⚙️ Required Components

| Part | Description | Package | Example Part |
| :--- | :--- | :--- | :--- |
| **MOSFET** | N-Channel MOSFET. Used to switch the motor on and off. | `WSON-6` | [Texas Instruments `CSD16301Q2` or similar](https://mou.sr/4fb3Gdl)|
| **Quad Resistor** | 4x Resistor Network. | `1206` | [YC164-JR-071RL or similar](https://mou.sr/46wOlBU) |
| **Haptic Motor** | A small coin/pancake style vibration motor. 8mm to 10mm is ideal. | N/A | Any generic 3V coin vibration motor, like [this one from Adafruit](https://www.adafruit.com/product/1201) |

### Tools & Supplies
- [Solder](https://amzn.to/3UwkeTA)
- [flux](https://amzn.to/40BSAIC)
- [kapton tape](https://amzn.to/45pTmuI)
- [tweezers](https://amzn.to/457N2XI)
- soldering iron - [Fnirsi HS-02A](https://amzn.to/4mfQypM)
- hot plate - [T55 Hotplate](https://amzn.to/4ofEBlY)
- [isopropyl alcohol](https://amzn.to/4o0Ajyu)
- 3D printed Ploopy Knob base modified to hold the Adafruit motor

---

## 🛠️ Step 1: Board Preparation

Before placing the new components, it is critical to prepare the PCB pads. This ensures a strong and reliable solder joint.

1.  **Identify the Pads:** Locate the empty component footprints on the Ploopy Knob PCB designated for the haptic feedback mod.
2.  **Clean the Pads:** Using a cotton swab and isopropyl alcohol (90%+ recommended), thoroughly clean the PCB pads. This removes any oils, dust, or oxidation from the manufacturing process. The pads should be shiny.

![Board Preparation](https://github.com/tuxedocurly/Ploopy-Knob-Haptic-Mod/blob/main/images/board%20prep.jpg)

---

## 🔥 Step 2: Soldering the SMD Components (Hot Plate Method)

This mod requires soldering two small surface-mount components. I found using solder paste and a hot plate is often easier than using a soldering iron for parts this small.

> ⚠️ **Safety First:** Hot plates are a fire hazard and can cause severe burns. Never leave a hot plate unattended and work in a well-ventilated area.

1.  **Apply Solder Paste:** Apply a small amount of solder to each of the pads for the MOSFET and the resistor array if needed. Less is more! You only need enough to cover the pad.
2.  **Prep Board With Kapton Tape:** Tape off the board except for the areas you are working in. This will help ensure none of the other components move around as you are working to reflow the solder on the board. This is important, and I recommend you don't skip this step.
3.  **Place Components:** Using a pair of fine-tipped tweezers, carefully place the quad resistor and the MOSFET onto their respective pads. Ensure the components are oriented correctly. The MOSFET will have a small line indicating its polarity—make sure this matches the marking on the PCB silk screen.
4.  **Heat the Board:** Place the PCB onto the pre-heated hot plate. Watch the solder paste closely. It will first turn grey and "boil" as the flux activates, and then it will melt into a shiny liquid silver and flow onto the pads and component pins.
5.  **Cool Down:** As soon as the solder flows, carefully remove the PCB from the hot plate and place it on a heat-resistant surface to cool down.

![Component Placement](https://github.com/tuxedocurly/Ploopy-Knob-Haptic-Mod/blob/main/images/hot%20plate.jpg)

---

## 🔌 Step 3: Soldering the Motor

With the control components in place, the final step is to attach the haptic motor itself.

1.  **Prepare Wires:** If your motor's wires are not already tinned, apply a small amount of solder to the ends.
2.  **Attach to PCB:** Solder the motor's two wires to the designated motor pads on the PCB. Polarity usually doesn't matter for simple DC vibration motors.
3.  **Secure the Motor:** Use the motor's self-adhesive backing to stick it to the motor mount on your Ploopy Knob case. Note you will need to print a modified base to use the Adafruit motor. The files are provided in the "3d models" folder in this repo. Make sure it won't interfere with any other components or the case closing.

![Motor Soldering](https://github.com/tuxedocurly/Ploopy-Knob-Haptic-Mod/blob/main/images/motor%20soldering.jpg)

---

## ✅ Step 4: Finished Product

Once the motor is soldered and secured, the hardware modification is complete. Your board should look similar to the photo below. The final step is to flash the custom QMK firmware that includes the code to control the haptic motor.

![Finished Product](https://github.com/tuxedocurly/Ploopy-Knob-Haptic-Mod/blob/main/images/finished%20knob.jpg)

---

## Firmware

This hardware mod requires corresponding firmware to function. You will need to compile and flash a keymap that has the haptic feedback code enabled.

Please use the "haptic" keymap in my [qmk_firmware repo](https://github.com/tuxedocurly/qmk_firmware/tree/ploopy-knob-haptic/keyboards/ploopyco/knob/keymaps/haptic).
