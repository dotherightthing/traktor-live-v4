# Traktor Live v4

Simplified setup around the Traktor Kontrol S8.

See also <https://github.com/dotherightthing/m4l-helpers>

## Traktor Pro

### Settings

Settings are saved in `tl4.tsi`.

<https://djtechtools.com/2012/11/19/how-to-make-remix-deck-sets-with-traktor%E2%80%99s-loop-recorder/>:

> * Audio Setup>Latency: as low as you can go without overloading your CPU (mine’s at 192)
> * Transport>Loops: Set Auto Detect Size @ 0 seconds
> * Transport>Cue Play Mode: Instant
> * Loop Recorder>Record Latency: 3ms, or as low as possible without CPU overload

* Loop Recorder > Source > Cue
* MIDI in/out - defined in TSI "TL4 Ableton I/O"
* Effects > FX Unit Routing > "Insert". "Post Fader" allows FX tails to play out after the track is cross faded out, but "Insert" allows the FX to be heard when the track is Cued - and therefore also recorded to the Loop Recorder from "Cue" rather than only "Main"

## Traktor Kontrol S8

Settings are saved in `tl4.tsi` and `tl4-s8.tsi`.

### MIDI controls

While initially being excited by the prospect of fully remappable controls (to control Ableton Live in NHL mode), I learned that these came with caveats:

* 'Enable MIDI controls' in Traktor's S8 preferences just adds a MIDI menu to the display
* The associated display is only affected by the 12 controls below each screen (4 encoders/ON buttons/faders)
* The actual state of the control is not reflected on the screen, only the MIDI control's position (i.e. not bi-directional)
* There's no option to set the encoder behaviour (e.g. 360 or 180 degrees)
* Mapping of the intended MIDI controls can conflict with advanced functionality, e.g. encoder/button control of FX 3 or 4
* Use of a mapping modifier can prevent functional conflicts, but the display will still update as if the control was enabled leading to a visual disconnect
* Use of a mapping modifier requires two hands which makes it even more difficult to perform live MIDI control during a set
* The 4 ON buttons only have 1 colour option (red) so different states are difficult to convey
* Mapping of any other controls conflicts with basic functionality and persists over both decks controlled by that side of the S8 (and there's no modifier for the focussed deck)

Therefore I've moved MIDI mappings to my KORG nanoKEY studio, where knobs provide instant visual feedback of pan and keys of key adjust.

I still intend to develop a Remote MIDI map (bankable automapping) for the S8, but this will be used exclusively with Ableton Live.

### Tips

* CAPTURE + REMIX Pad to overwrite sample <https://www.native-instruments.com/forum/threads/deleting-remix-samples.229019/>
* To capture sounds with FX, or the Juno, use the Loop Recorder.
* To capture a raw beat, use the Remix sampling directly
* If the recorded loop is out of synch, use Sample Offset Bwd/Fwd (non-mappable) to nudge the start point by 1/16s (<https://youtu.be/24bl9WY33fI?t=267>)
* To toggle FX 3/4, hold down shift then push the usual FX 1/2 arrows
* To set FX 3/4, press FX Select > ON #1 - note that this doesn't work if the buttons are MIDI mapped
* To control FX 3/4, use the encoders above ON
* When browsing for a track on the 'Y' deck, the track and loop playing on deck 'X' will be the default selection
* FX: on the delay, turn the filter up for a fade-out to occur when freezing the effect
* FX: freeze trails are a good way to get a cut-n-tail without requiring FX to be post fader. Enable the freeze in advance and then turn on the device to apply. This also works on remix slots by turning the FX Send level up for the slot you want to trail out (the FX switch must be engaged too).
* Loop and Beatjump controls seem to work in Remix deck - so be careful NOT to be in Loop mode when trying to trigger clips
* Shift + Remix to open the pre-installed sequencer

### Supreme Edition Mod

<https://www.patreon.com/supremeedition>

NZD $9.50 ($10.93 incl GST) per month - cancel after 1 month then only resubscribe when there's an update

## KORG nanoKEY Studio

Settings are saved in `tl4.tsi` and `tl4-nanokey-studio.tsi`.

See also mappings in the Live Set, plus the Korg templates.

### MIDI controls

| Function                                             | Deck C (Input) | Deck A     | Dec B      | Deck D (Remix) |
|------------------------------------------------------|----------------|------------|------------|----------------|
| Pan                                                  | Knob 1         | Knob 2     | Knob 3     | Knob 4         |
| JU-06A (Noise/H Frq/V Frq/V Res)                     | Knob 5         | Knob 6     | Knob 7     | Knob 8         |
| Focus                                                | Pad 1          | Pad 2      | Pad 3      | Pad 4          |
| Loop Record (4/8/16/32)                              | Pad 5          | Pad 6      | Pad 7      | Pad 8          |
| Pitch                                                | Keys + M4L     | Keys + M4L | Keys + M4L | Keys + M4L     |
| Clock sync                                           | Tap XY pad     | Tap XY pad | Tap XY pad | Tap XY pad     |

## Ableton Live

* MIDI in/out - Control Surface: ClyphX; Input: Traktor Virtual Output (incl Sync); Output: Traktor Virtual Input

Used to:

* route MIDI to external hardware (JU-06A)
* route nanoKey control to JU-06A and/or a deck (Max4Live)
* ensure that loop recording starts on-beat (note that this requires the clock to be in sync)

### M4L (Max4Live) Device

I adapted <https://maxforlive.com/library/device/2593/midi-filter>, see the device for an explanation.

JU-06A controls can be identified for mapping by using MIDI Monitor app. See also Live Project where I experimented with this.

### ClyphX (Free)

ClyphX Pro doesn't work with Live 11. ClyphX is an older version but has core functionality.

1. Download from <https://github.com/ldrolez/clyphx-live10/releases>
2. Extract zip and copy `ClyphX` folder to `~/Music/Ableton/User Library/Remote Scripts/`
3. Manual: <https://raw.githubusercontent.com/ldrolez/clyphx-live10/master/ClyphX%20Manual.pdf>

* X-Controls - historically defined in `USER CONTROLS` in UserSettings.txt - but this wasn't working so I used X-Clips instead

Note MIDI button must send "Hold" not "Direct", else it would only fire a MIDI message one when a transitioned from 0 to 1. (Also?) "Direct" seemed to just not work, maybe because of this?

If things are hooked up properly you can check that Ableton sees the MIDI input by mapping it to a clip

---

## TODO

*Before installing Supreme Edition Mod, do the following so any workflow changes can be re-incorporated afterwards:*

* Finish reading stock manual
* Record the mix
* Rename sample slots
* Save the remix deck afterwards - <https://youtu.be/24bl9WY33fI?t=405>
* Assign different scene of pads to set Ableton global quantise
* Remove the 8 bar count in -> 8 bar record isn't working for sample-this-right-now situations
* Add Live Project where I experimented with JU-06A mappings

### Things I hope the Supreme Mod will address

Edit > BPM adjust is fiddly - the 'coarse' adjust is not integers. This means that for songs that are 50%/200% rather than 100% it's easier to fix them in the software
