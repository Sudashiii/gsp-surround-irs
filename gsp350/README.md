# gsp350: Sennheiser GSP 350

`gsp350_16ch.wav`: 48 kHz, 32-bit float, 16 channels, 0.6 s (28 800 samples, 50 ms fade-out).
Channel order as in `../CONTRIBUTING.md`.

## Measured from
| component | version |
|---|---|
| Dongle | USB `1395:005D`, bcdDevice 0x0007 |
| Driver package | Conexant "USB Audio" 1.31.35.10 (2016-05-20) |
| Driver file | `usbaud64.sys` 1.31.36.6 |
| Control app | Sennheiser SmartAudio3 2.1.4.0 |
| OS | Windows 11 23H2 |

Driver settings: virtual surround (Dolby Headphone) on, default room, 7.1 input, preset "Game".

## What is in the file and what is not
- Included: the full 7.1 → headphone filter, with the driver's −3 dB surround gain and its +3 dB
  LFE gain of the "Game" preset.
- Not included: the Off/Music/eSports presets differ in the driver only by the LFE level
  (−3 dB vs. Game). The app applies that as a gain (`lfe_gain` in `index.json`).
- Not included: the EQ of each preset. It runs inside the dongle's firmware, after USB. The app
  selects it with the same 2-byte HID command the Windows app sends (`23 00`..`23 03`).

## Accuracy
Null test of the recreation against the real driver output, captured on the USB bus:
median residual **−46 dB** below 16 kHz; the remaining error is above 22 kHz, where the
measurement sweep fades out.
