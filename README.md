# Traktor Live v4

Simplified setup around the Traktor Kontrol S8.

## Workflow mappings

* Left deck - ON #1 = Loop Recorder - Record loop of size  4 bars (M2 = 0 for LED)
* Left deck - ON #2 = Loop Recorder - Record loop of size  8 bars (M2 = 1 for LED)
* Left deck - ON #3 = Loop Recorder - Record loop of size 16 bars (M2 = 2 for LED)
* Left deck - ON #4 = Loop Recorder - Record loop of size 32 bars (M2 = 3 for LED)
* Left deck - SHIFT + ON #1 = Loop Recorder - delete recording (M1 = 1 for SHIFT)
* Left deck - SHIFT + ON #2 = Loop Recorder - delete recording (M1 = 1 for SHIFT)
* Left deck - SHIFT + ON #3 = Loop Recorder - delete recording (M1 = 1 for SHIFT)
* Left deck - SHIFT + ON #4 = Loop Recorder - delete recording (M1 = 1 for SHIFT)
* Left deck - Encoder #1 = Remix deck D slot 1 size adjust - /2|x2 (record double loop then halve to remove click)
* Left deck - Encoder #2 = Remix deck D slot 2 size adjust - /2|x2 (record double loop then halve to remove click)
* Left deck - Encoder #3 = Remix deck D slot 3 size adjust - /2|x2 (record double loop then halve to remove click)
* Left deck - Encoder #4 = Remix deck D slot 4 size adjust - /2|x2 (record double loop then halve to remove click)
* Left deck - Volume #1 = Loop Recorder Dry/Wet (better to dump to remix deck and visualise there, but would probably need extra mapping to cue a remix slot)

## Settings:

> MAD ZACH’S TRAKTOR PREFERENCES
>
> For this to work well, there are a few tweaks that I recommend making to Traktor’s preferences to get everything dialed:
>
> * Audio Setup>Latency: as low as you can go without overloading your CPU (mine’s at 192)
> * Transport>Loops: Set Auto Detect Size @ 0 seconds
> * Transport>Cue Play Mode: Instant
> * Loop Recorder>Record Latency: 3ms, or as low as possible without CPU overload

<https://djtechtools.com/2012/11/19/how-to-make-remix-deck-sets-with-traktor%E2%80%99s-loop-recorder/>

## Tips

1. Effects > FX Unit Routing > "Post Fader" allows FX tails to play out after the track is cross faded out, but "Insert" allows the FX to be heard when the track is Cued - and therefore also recorded to the Loop Recorder from "Cue" rather than only "Main"
2. CAPTURE + REMIX Pad to overwrite sample <https://www.native-instruments.com/forum/threads/deleting-remix-samples.229019/>
3. To capture sounds with FX, or the Juno, use the Loop Recorder.
4. To capture a raw beat, use the Remix sampling directly
5. If the recorded loop is out of synch, use Sample Offset Bwd/Fwd (non-mappable) to nudge the start point by 1/16s (<https://youtu.be/24bl9WY33fI?t=267>)
6. Set Loop Recorder "Source" to "Cue"

## Supreme Edition Mod

<https://www.patreon.com/supremeedition>

NZD $9.50 ($10.93 incl GST) per month - cancel after 1 month then only resubscribe when there's an update

### TODO

*Before installing Supreme Edition Mod, do the following so any workflow changes can be re-incorporated afterwards:*

* finish reading stock manual
* experiment with Ableton integration 
* program keyboard to pitch deck
* select deck from keyboard (AB--, Remix Slot 1234) - Deck C should send MIDI to Ableton to play Juno, Deck D should pitch individual slot
* To capture a beat with FX, use the Loop Recorder carefully - note that Quantise doesn't seem to work with the Loop Recorder start - maybe ON #1/2/3/4 could trigger Ableton to wait for the next bar then tell Traktor Loop Recorder to Record.
* Turn the loop recorder dry/wet up so you can immediately hear the recorded loop (does this go to the main out?)
* Record the mix
* Rename sample slots
* Save the remix deck afterwards - <https://youtu.be/24bl9WY33fI?t=405>

---

## Loop Recorder sync notes

### Traktor

* ON #1-4 become MIDI buttons
* On click send MIDI CC 1-4 on Channel 16

### Ableton (Ext sync, launch quantisation)

* Free ClyphX intercepts
* Map ch 16 ... ??
* At next bar 

### ClyphX (Free)

1. Download from <https://github.com/ldrolez/clyphx-live10/releases>
2. Extract zip and copy "ClyphX" folder to ~/Music/Ableton/User Library/Remote Scripts/
3. Manual: <https://raw.githubusercontent.com/ldrolez/clyphx-live10/master/ClyphX%20Manual.pdf>

The Traktor S8 allows [one or both - NO it affects both :( ] Remix deck buttons to be reassigned as MIDI controls - see "TRAKTOR KONTROL S8 - Manual" page 287

Note MIDI button must send "Hold" not "Direct", else it would only fire a MIDI message one when a transitioned from 0 to 1.

FX freeze trails are a good way to get a trail without going post fader
Actually enabling the freeze in advance and then turning on the device when you want to appy it works great
This also works on remix slots by turning the FX Send level up for the slot you want to trail out. Note: the FX switch must be engaged too

If things are hooked up properly you can check that Ableton sees the MIDI input by mapping it to a clip

Loop and Beatjump controls seem to work in Remix deck - so be careful NOT to be in Loop mode whenm trying to trigger clips

TODO ableton set orange|green|red lights on when loop is waiting / being recorded / finished recording

TODO bottom 4 pads set Ableton global quantise

* Traktor MIDI in/out - defined in TSI "Ableton Live communication"
* Ableton MIDI in/out - Control Surface: ClyphX; Input: Traktor Virtual Output (incl Sync); Output: Traktor Virtual Input
* X-Controls - defined in `USER CONTROLS` in UserSettings.txt
