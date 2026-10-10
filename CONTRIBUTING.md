# Contributing a profile

A profile is one folder with one WAV file plus a short README.

## File format
- WAV, 32-bit float, **48 kHz**, **16 channels**, about 0.6 s long.
- Channel order (input channel → ear):
  `FL.L FL.R FR.L FR.R FC.L FC.R LFE.L LFE.R RL.L RL.R RR.L RR.R SL.L SL.R SR.L SR.R`
- Gains exactly as the driver applies them in its default/"game" setting, so that convolving a
  7.1 signal with the file gives the same stereo the driver sends to the dongle.

## How the GSP 350 profile was measured
1. Original Windows driver installed, virtual surround on.
2. A logarithmic sine sweep was played into each of the 8 channels of the driver's 7.1 device,
   one at a time.
3. The stereo PCM the driver sent to the dongle was recorded **digitally on the USB bus**
   (USBPcap, isochronous OUT endpoint of the main audio interface), not with a microphone.
4. Each recording was deconvolved with the sweep, giving one response per channel and ear.
5. Checked: linearity, time invariance and superposition (all better than −54 dB), then a null
   test of real program material against the driver: −46 dB below 16 kHz.

Measuring through a microphone or an analog loopback is **not** good enough: the point is to get
exactly the bits the driver produces, before the dongle's own EQ.

## Adding it
1. New folder `<profile>/` with `<profile>_16ch.wav` and a `README.md` stating headset, dongle
   USB ID (`lsusb`), driver and app versions, and how it was measured.
2. Add the profile to `index.json` (with `sha256sum`) and a row to the table in `README.md`.
3. Open a pull request. Also open an issue in gsp-surround-linux with the USB ID so the app can
   recognise the dongle.
