# 3DS Bluetooth Audio Mod

A Bluetooth audio mod for the Nintendo 3DS XL (3DS LL) built around the KCX_BT_EMITTER module, with no extra holes cut in the shell for switches or buttons.

**[View the wiring reference](https://skecchu.github.io/3ds-bluetooth-mod/)** · [PDF](3DS-BT-Power-Gate-RevD.pdf) · [PNG](3DS-BT-Power-Gate-RevD.png)

![3DS Bluetooth power gate wiring reference](3DS-BT-Power-Gate-RevD.png)

## What it does

The Bluetooth module only gets power when all three of these are true:

- The 3DS is powered on.
- The clamshell is open.
- Headphones or a metal 3.5mm plug are in the jack.

So there's no power switch to add, and the module can't drain the battery while the 3DS is off or closed. Two load-switch ICs in series do the gating (NCP380H for the hinge, NCP380L for the headphone jack), which makes a hardware AND gate with no microcontroller.

Other changes in this build:

- **Status LED:** A green LED is routed to the charging indicator window in the bottom-right corner. It's green so the pairing light doesn't get mistaken for the red low-battery light.
- **Antenna:** The onboard antenna is snapped off and replaced with an external antenna that runs parallel to the stylus cover.

## KCX_BT_EMITTER fixes

- **Muffled sound:** Remove the two SMD capacitors in series with the AudioL and AudioR inputs and bridge the pads.
- **Static:** Wire the module's AGND to headphone jack **pin 4**, not pin 1. Keep AGND and PGND separate.

The wiring reference has full steps, the node table, expected on/off states, a parts list, and the checks to run after wiring.

## Turning on Bluetooth

Plug a **metal** 3.5mm plug into the headphone jack (a bare 3-pole TRS plug or a metal dust plug) and open the lid. A plastic dummy plug won't work: the jack only registers a plug when the metal barrel bridges the detect contact to ground, and pin 4 doubles as the module's audio ground.

## Parts

| Ref | Part | Value | Package |
|---|---|---|---|
| U1 | NCP380HSN05AAT1G | Active-high load switch | TSOP-5 |
| U2 | NCP380LSN05AAT1G | Active-low load switch | TSOP-5 |
| R2 | RMCF0805JT10K0 | 10kΩ | 0805 |
| C1 to C3 | C0805C105K4RACTU | 1µF, X7R, 16V | 0805 |
| P1 | Any metal 3.5mm plug | 3-pole TRS, to turn on Bluetooth | 3.5mm |
| Module | KCX_BT_EMITTER | Bluetooth 5.3 audio transmitter | |

## Disclaimer

This involves soldering to test points on the 3DS mainboard. I'm not a professional, so do this at your own risk and double-check measurements on your own unit before wiring anything.

## Credits

Mod and documentation by **u/skecchi_** ([Reddit](https://www.reddit.com/user/skecchi_/)) · IG [@skecchu_](https://www.instagram.com/skecchu_/)
