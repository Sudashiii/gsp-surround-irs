# gsp-surround-irs

Measured impulse responses (filter files) for [gsp-surround-linux](https://github.com/Sudashiii/gsp-surround-linux),
which recreates the virtual 7.1 surround sound of GSP-family gaming headset dongles on Linux.

Each profile is one WAV file that describes how the original Windows driver turns 7.1 audio into
headphone stereo: for each of the 8 input channels, one response for the left ear and one for the
right ear (16 channels in total). `index.json` lists the profiles, their SHA-256 hashes, channel
order and the driver versions they were measured from. The app downloads files from the `v1` tag
and checks the hash.

| profile | headset / dongle | USB ID | folder |
|---|---|---|---|
| `gsp350` | Sennheiser GSP 350 | `1395:005d` | [`gsp350/`](gsp350/) |

Want to add your headset? See [CONTRIBUTING.md](CONTRIBUTING.md).

## Legal
- This project is not affiliated with, endorsed by or connected to Sennheiser, EPOS, Conexant or
  Dolby Laboratories. Product names are only used to say which hardware a file belongs to.
- The files are measurements of the audio output of the original Windows drivers, provided for
  personal use and interoperability with hardware the user owns. No driver code is included.
- If you are a rights holder and want a file removed, open an issue and it will be taken down.
