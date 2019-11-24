C------------------------------------------------------------------------------
C  			        turingTest0Coast                
C------------------------------------------------------------------------------
C
C  This pd patch creates "generative music" in conjunction with a electronic
C  synthesizer.
C
C  It uses a Pure Data patch to model Music Thing Modular's Turing Machine 
C  and create melodic sequences.  https://www.thonk.co.uk/shop/turingmkii/
C
C  The Turing machine is a pseudorandom looping sequencer. It generates strings 
C  of pseudorandom numbers that can be locked into looping sequences. These 
C  sequences can be allowed to slip, changing gradually over time.  Mapping
C  these strings of numbers onto scales create melodic sequences.
C
C  In this patch, Pure Data sends a midi clock out to the Digitone and also bangs 
C  out a Euclidian rhythm. On each bang, the Turing machine patch creates a pseudo 
C  random number which is then mapped onto a major pentatonic scale. 
C
C
C  Please see https://www.youtube.com/watch?v=VGIkW4UEqdg for an example of it's use.
C
C------------------------------------------------------------------------------
C  Requirements:   Pure Data <https://puredata.info/downloads/pure-data>
C------------------------------------------------------------------------------
C
Usage:  The file turingTest0Coast.pd is the parent patch which contains the 
        rest of the modules.

               Explanation of the primary patches:
midiClockOut:  Sends midi clock pulses from the Pure Data to the Digitakt at 1/96th note
               intervals.  It provides the euclidRhythm patch with a 1/16th note clock.
euclidRhythm:  Bangs out a randomly varying euclidian rhythm.  This patch uses the 
               patches eSeq, euclidR, expDist, and setctl.
randScales:    This patch selects a scale that the Turing sequence is mapped onto.
turingSeq:     This patch models the Turing machine. On each clock interval, it "bit
               shifts" the previously generated number one bit to the left.  The bit 
               shifted number then undergoes a Digital-to-Analog conversion and the 
               output is normalize to be between zero and one. At user defined intervals,
               the least significant bit of the number is "flipped" to create a pattern 
               that gradually changes over time.  The user also has the option of locking
               in the current pattern.

Contributions: Any contributions to this project are welcome.

Acknowledgements: I'd like to thank Acreil for his inspiring Pure Data patches. 


