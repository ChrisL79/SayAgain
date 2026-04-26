# SayAgain

I make programs for myself if nothing exists that i exactly want. If they turn out to be half decent, i will share them with the world.

I'm not a programmer! I just program for fun and to create something i need.

**An amateur radio voice keyer for Windows.**

Point it at any HF/VHF/UHF transceiver with a CAT capable serial port and a virtual (or physical) audio cable, and you have six instantly replayable voice macros at your fingertips.

![Main Interface](IMAGES/Main%20Interface.jpg)

---

## About SayAgain

SayAgain works with:

- Yaesu HF — FT-450 through FTDX-101, FT-817/818, FT-857, FT-897, FT-1000 series, FTX-1, and the old 5-byte protocol rigs
- Kenwood HF — TS-50 through TS-990S, including the whole TS-480/570/590/890/990 family
- Icom HF — every CI-V rig from IC-706 to IC-705, IC-7300, IC-7610, IC-7851, IC-9700, IC-905, IC-7760
- Elecraft — K2, K3, K3S, K4, KX2, KX3
- Xiegu — G90, X5105, X6100, X6200, X108G
- Alinco — DX-77, DX-SR8, DX-SR9
- Ten-Tec — Orion, Omni VII, Eagle, Jupiter, Argonaut V, Delta II, Paragon, Pegasus
- SDRs via virtual COM — FlexRadio (SmartSDR CAT / PowerSDR), Apache ANAN, Hermes-Lite 2 (Thetis), PiHPSDR, SDR Console, SparkSDR, GQRX, SDRUno, FLRig, SunSDR/ExpertSDR
- Portable / kit SDRs — Lab599 TX-500, Malachite DSP, QRPLabs QCX/QDX/QMX, (tr)uSDX, FX4 family, Commradio CTX-10, mcHF QRP, ELAD FDM-DUO, Hilberling PT-8000A, Bunzee Simple CAT
- Commercial HF — Barrett, CODAN, Harris, Rohde & Schwarz, Skanti, Micom, Vertex VX-1700
- GUOHETEC PMR-171 / Q900
- And "Generic RTS PTT" / "Generic DTR PTT" as a catch-all for anything with a SignaLink, RigBlaster, Digirig, or homebrew interface

**180+ rig entries** in the dropdown, searchable by keyword.

---

## Features

- **6 macro slots** with individual record / playback / re-record
- **One click CAT PTT** — no VOX, no extra hardware required
- **Live VU metering** for mic input and output
- **Waterfall + waveform** display of the macro audio
- **Simple Windows XP style theme** with optional dark mode
- **Window geometry remembered** across launches (clamped to current monitors)
- **Connection status bar** with live CAT link indicator and rig summary
- **Test PTT button** in the CAT Settings dialog — verify wiring in one click

---

## Screenshots

### Main interface
![Main Interface](IMAGES/Main%20Interface.jpg)

### CAT Settings — 180+ rigs, searchable
![CAT Selection](IMAGES/CAT%20Selection.jpg)

### Microphone selection
![Mic Selection](IMAGES/Mic%20Selection.jpg)

### VAC (TX audio) output selection
![VAC Selection](IMAGES/VAC%20Selection.jpg)

### Dark mode
![Dark Mode](IMAGES/Dark%20Mode.jpg)

---

## Installation

### Option 1 — Download the installer
Grab the latest `SayAgainSetup.exe` from the [Releases](../../releases) page and run it. It installs to `C:\Program Files\SayAgain`, adds Start Menu and (optional) desktop shortcuts, and registers an uninstaller.

## Quick start

1. **Wire up your audio path.** SayAgain outputs voice to a Windows audio output device.
2. **Start SayAgain** and go to **File → VAC Audio Output…** — pick the audio device that feeds your rig.
3. Go to **File → CAT Settings…** — use the filter box to find your rig, pick the COM port, click **Test PTT**. If the radio keys for one second and unkeys, you're done.
4. Click **Record** on macro slot #1, hold it until the circle completes, then talk into your mic, click **Stop** then **Save**.
5. Click **TX** on that macro to key the radio and play it out over the air.
6. **To rename a macro**, double click on the macro name. Enter your own macro name in the popup box then click OK.
7. **To delete a macro**, right click the macro name and then press Delete Recording.
8. SayAgain recorded macro location is C:\Users\**YOUR USERNAME**\SayAgain Recordings. This can be changed in **FILE**, **RECORDING FILE LOCATION**.

---


If your exact rig isn't in the dropdown, **Generic RTS PTT** or **Generic DTR PTT** will work with any rig keyed via a standard serial control line (SignaLink, RigBlaster, Digirig, homebrew USB-serial + optocoupler).

---

## Requirements

- Windows 7 or later
- A CAT capable serial or virtual COM port to your rig
- A Windows audio output device that routes to the rig's modulator (real soundcard + cable, VB Cable, VoiceMeeter Banana, SDR application's VAC, etc.)


---

## Licence

Free to use for the ham community. **NOT TO BE SOLD!!!**

---

## Author

**Chris Lawton — M7JEX**
Somerset, UK
73
