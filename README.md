# EasyModeBtw

**Play any scale on the white keys.** A MIDI effect for Linux: the white keys play the
notes of the scale you pick, the black keys are silent, and the scale's root sits on middle C.
CLAP and VST3 for Linux.

![EasyModeBtw in F minor, with E3 and G3 held: they sound as Ab3 and C4](images/screenshot.png)

Pick F minor, and the white keys from C3 upwards play F G Ab Bb C Db Eb F. Put EasyModeBtw in
front of any instrument and you can't play a wrong note. It works like the Easy Mode of Native
Instruments' Smart Play. It has no audio inputs or outputs: it only rewrites MIDI notes.

It runs natively on Linux, with no network access and no telemetry.

**[Read the manual](manual.md)** for every control and how to use it.

## Features

- **14 scales on 12 keys:** Chromatic, Major, Natural, Harmonic and Melodic Minor, Dorian, Phrygian, Lydian, Mixolydian, Locrian, Major and Minor Pentatonic, Blues and Whole Tone.
- **No stuck notes:** a note-off always ends the note its note-on started, even if you change the key or scale while holding it.
- **Everything else passes through:** pitch bend, mod wheel and other CCs, channel pressure and program changes are untouched.
- **Keyboard display:** shows the scale, its root and the notes sounding right now. Click a key to make it the root.
- **No network access and no telemetry.**

## Install

Download the latest version from the [Releases page](https://github.com/PluginsBTW/EasyModeBtw-release/releases),
or with these commands:

```bash
curl -LO https://github.com/PluginsBTW/EasyModeBtw-release/releases/download/v0.1.3/EasyModeBtw-0.1.3-linux-x86_64.tar.gz
curl -LO https://github.com/PluginsBTW/EasyModeBtw-release/releases/download/v0.1.3/EasyModeBtw-0.1.3-linux-x86_64.tar.gz.sha256
sha256sum -c EasyModeBtw-0.1.3-linux-x86_64.tar.gz.sha256 && tar xzf EasyModeBtw-0.1.3-linux-x86_64.tar.gz
cd EasyModeBtw-0.1.3-linux-x86_64
```

Install for your user:

```bash
mkdir -p ~/.clap ~/.vst3
rm -f ~/.clap/easymodebtw.clap && cp easymodebtw.clap ~/.clap/
rm -rf ~/.vst3/easymodebtw.vst3 && cp -r easymodebtw.vst3 ~/.vst3/
```

Or for all users:

```bash
sudo mkdir -p /usr/lib/clap /usr/lib/vst3
sudo rm -f /usr/lib/clap/easymodebtw.clap && sudo cp easymodebtw.clap /usr/lib/clap/
sudo rm -rf /usr/lib/vst3/easymodebtw.vst3 && sudo cp -r easymodebtw.vst3 /usr/lib/vst3/
```

Removing the old copy first avoids overwriting a file a running host has loaded. Then rescan plugins
in your DAW.

To uninstall:

```bash
rm -rf ~/.clap/easymodebtw.clap ~/.vst3/easymodebtw.vst3
```

## Requirements

- Linux x86-64 with glibc 2.31 or newer (Ubuntu 20.04, Debian 11, Fedora 32 and newer)
- A CLAP or VST3 host
- X11 or XWayland, and a Vulkan driver for the editor

Releases contain the CLAP and VST3 plugins only.

## License

MIT, see [LICENSE](LICENSE). The licenses of the third-party code in the binaries are in
`THIRD-PARTY-LICENSES.txt` in each release archive.

VST is a registered trademark of Steinberg Media Technologies GmbH. CLAP is an open standard
by the free-audio project. Smart Play is a product feature of Native Instruments. EasyModeBtw is
an independent project, not affiliated with or endorsed by Steinberg or Native Instruments.
