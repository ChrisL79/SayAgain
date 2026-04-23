# SayAgain

**A rig-agnostic voice keyer for Windows.**
Point it at any HF/VHF transceiver with a CAT-capable serial port and a virtual (or physical) audio cable, and you have six instantly-replayable voice macros at your fingertips.

Built in Python / PyQt5 by **Chris Lawton (M7JEX)**.

![Main Interface](IMAGES/Main%20Interface.jpg)

---

## Why another voice keyer?

Most voice keyers are tied to one radio family (SunKeyer → SunSDR, the Heil CL-something, the rig's own built-in memories). SayAgain deliberately doesn't care what rig you own. If the radio can be keyed over a serial port — via RTS, DTR, or a native CAT PTT command — and audio can reach its microphone input via a Windows audio device, SayAgain will drive it.

That means it works with:

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

- **6 macro slots** with individual record / playback / re-record / arm-hold behaviour
- **One-click CAT PTT** — no VOX, no extra hardware required
- **Optional hold-to-arm** per macro (prevents accidental transmission)
- **Live VU metering** for mic input and output
- **Waterfall + waveform** display of the macro audio
- **Windows XP-style theme** with optional dark mode
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

### Option 2 — Run from source
Requires Python 3.10 or later.

```bash
pip install PyQt5 pyaudio numpy pyserial
python SayAgain.py
```

If `pyaudio` fails to install on Windows:
```bash
pip install pipwin
pipwin install pyaudio
```

---

## Quick start

1. **Wire up your audio path.** SayAgain outputs voice to a Windows audio output device. Most users pipe that through a virtual audio cable (VB-Cable, VoiceMeeter Banana, etc.) into their rig's modulation input (Thetis VAC1, SmartSDR DAX TX, ExpertSDR Mic In PC, etc.).
2. **Start SayAgain** and go to **File → VAC Audio Output…** — pick the audio device that feeds your rig.
3. Go to **File → CAT Settings…** — use the filter box to find your rig, pick the COM port, click **Test PTT**. If the radio keys for one second and unkeys, you're done.
4. Click **Record** on macro slot #1, talk into your mic, click **Stop**.
5. Click **TX** on that macro to key the radio and play it out.

---

## Building your own installer

You need [PyInstaller](https://pyinstaller.org) and [Inno Setup 6](https://jrsoftware.org/isdl.php).

```bash
pip install pyinstaller
pyinstaller SayAgain.spec
```
That produces `dist\SayAgain\SayAgain.exe`.

Open `SayAgain.iss` in Inno Setup Compiler and press **F9** / Build. The signed installer lands in `Output\SayAgainSetup.exe`.

---

## Rig configuration notes

A few rigs have quirks worth knowing about:

- **Alinco DX-SR8 / DX-SR9** — CAT PTT only keys the transmitter when the radio is in SDR mode, due to a firmware 1.03 bug Alinco never fixed.
- **Yaesu FT-817 / 818** — use the dedicated 5-byte binary entry, not the modern TX1/TX0 Yaesu entry.
- **Xiegu G90 / X5105 / X6100 / X6200 / X108G** — all emulate Icom CI-V at address 0xA4, 19200 baud.
- **FlexRadio 6000 / 8000** — configure SmartSDR CAT to create a virtual COM port emulating a TS-2000, then pick that port in SayAgain with the "FlexRadio (via SmartSDR CAT virtual COM)" profile.
- **Hermes-Lite 2 / ANAN via Thetis** — same pattern. Use Thetis's virtual-COM CAT emulator and SayAgain's "Thetis — any ANAN / Hermes / Hermes-Lite 2" profile. In Thetis, on the VAC tab, make sure **"Allow PTT to override/bypass VAC for Phone"** is **unchecked**, otherwise CAT-keyed PTT silently bypasses the VAC audio you're feeding in.
- **SunSDR / ExpertSDR** — same trap. ExpertSDR's "Smart PTT" routes audio from MIC inputs rather than VAC when PTT arrives from a non-VAC source; check the ExpertSDR audio documentation and set Mic Input = PC if needed.

If your exact rig isn't in the dropdown, **Generic RTS PTT** or **Generic DTR PTT** will work with any rig keyed via a standard serial control line (SignaLink, RigBlaster, Digirig, homebrew USB-serial + optocoupler).

---

## Requirements

- Windows 10 or later (tested on Windows 11)
- A CAT-capable serial or virtual COM port to your rig
- A Windows audio output device that routes to the rig's modulator (real soundcard + cable, VB-Cable, VoiceMeeter Banana, SDR application's VAC, etc.)
- Python 3.10+ (only if running from source)

---

## Licence

See `LICENSE` in the repo root.

---

## Author

**Chris Lawton — M7JEX**
Somerset, UK
73
