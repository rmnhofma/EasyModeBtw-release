# EasyModeBtw manual

**Play any scale on the white keys.** A MIDI effect for Linux: the white keys play the
notes of the scale you pick, the black keys are silent, and the scale's root sits on middle C.

Version 0.1.5. To install it, see the [README](README.md).

## Getting started

EasyModeBtw goes **in front of an instrument**, because it changes the notes the instrument
receives.

- **Bitwig Studio:** put it in the Note FX slot of an instrument track, or anywhere before the
  instrument in the device chain. Use the CLAP version.
- **Other hosts:** use it as a MIDI effect in front of an instrument. VST3 has no MIDI-effect
  category, so a host that only routes MIDI between MIDI effects may not accept the VST3 there.
  The CLAP version is declared as a note effect.

Choose a KEY and a SCALE, then play the white keys from middle C upwards. That's all of it.

![EasyModeBtw in F minor](images/screenshot.png)

## The controls

| Control | Range | Default | What it does |
| --- | --- | --- | --- |
| **Power switch** (top right) | On / Off | On | Easy Mode on, or every event passes through unchanged. |
| **KEY** | C to B | C | The scale's root: the note middle C plays. Clicking a key of the keyboard sets it too. |
| **SCALE** | 14 scales | Major | The scale the white keys walk through. |

The status line in the header says what middle C plays and the scale, for example
`C3 = F · F minor`, or `bypassed` when the power switch is off. The version is in the bottom-right
corner, and clicking the logo opens [the plugin's page](https://rmnhofma.github.io/plugins/easymodebtw/).

## How to use it

### What the white keys play

Every white key is one step of the scale. Middle C (C3, MIDI note 60) plays the root, the next
white key up plays the next note of the scale, and white keys below middle C walk down it. Black
keys play nothing.

| Scale | White keys C3 D3 E3 F3 G3 A3 B3 C4 play |
| --- | --- |
| C Major | C3 D3 E3 F3 G3 A3 B3 C4 (unchanged) |
| F Natural Minor | F3 G3 Ab3 Bb3 C4 Db4 Eb4 F4 |
| G Major | G2 A2 B2 C3 D3 E3 F#3 G3 |

Roots C to F sit on or above middle C, and F# to B just below it, so the playable range stays
centred.

### Scales with fewer or more notes

The octave no longer lines up with seven white keys when a scale doesn't have seven notes. A
five-note pentatonic repeats every five white keys, and Chromatic every twelve. So on a pentatonic
your hands cover more than an octave of pitch for the same reach, which makes fast runs easy.

### Changing key while you play

You can change the key, the scale or the power switch while holding notes. A held note keeps
sounding until you let go of its key, and then the right note ends, so nothing gets stuck.

## Good to know

- **Other MIDI:** pitch bend, mod wheel and other CCs, channel pressure and program changes pass
  through untouched. Poly aftertouch and per-note expressions follow their note.
- **Two keys, one note:** if two keys would play the same note on one channel, the second is
  ignored. Notes that would land outside MIDI's 0 to 127 are dropped.
- **Latency:** none. There is no audio in it at all.
- **Hosts:** the CLAP passes `clap-validator`, and the VST3 loads in Carla's plugin scanner.
- **Display:** X11, or XWayland on a Wayland desktop, with a Vulkan driver.

## Troubleshooting

- **The plugin doesn't show up:** check that the bundle is in `~/.clap`, `~/.vst3`,
  `/usr/lib/clap` or `/usr/lib/vst3`, then rescan plugins in your DAW.
- **The editor window stays black or doesn't open:** check that a Vulkan driver is installed.
  The `vulkaninfo` tool from `vulkan-tools` should list your GPU. Bitwig Studio writes plugin
  errors to `~/.BitwigStudio/log/engine.log`.
