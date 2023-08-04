# M7EPL's GNURadio Experiments

My experiments with gnuradio.

## How to use the diversity model

1. Open, and run `mrc.grc`.  (looks like a play icon on the toolbar) This will
   compile then finish immediately.
1. Open, and run `phase_match.grc`.  (looks like a play icon on the toolbar)
   This will compile then finish immediately.
1. Open, and run `fmaudiosink.grc`.  (looks like a play icon on the toolbar)
   This will compile then finish immediately.
1. Use "Reload Blocks" (looks like two arrows in a circle icon on the toolbar)
   * A new "E7EPL" section should appear on the right hand side, containing
     both blocks above, if not repeat the process above for the missing block.
1. Open diversity2.grc and hit "Play".
   1. Remember to change the volume and source if you want to hear anything.
   * It's likely you don't have the same SDR setup as me, you'll need to
     replace the SDR block with some other source.

## Experiments

### mrc: Maximum Ratio Combining

See [Wikipedia](https://en.wikipedia.org/wiki/Maximal-ratio_combining)

I'm not sure I've quite got this right yet.  I'm currently using the 2nd and
4th moments to estimate SNR.  But it seems to work in the small test cases I've
tried.

### phase\_match: Phase Matching

This takes two signals, cross correlates them, converts the correlation to a
phase offset, and applies it to the signal so they should both be in phase.

### diversity2: Antenna Diversity Combining

This is for experiments around taking signals from two different antenna, phase
matching them and combining them hopefully removing/reducing QRM
(Interference), while increasing the signal.

Currently a work in progress.

### fmaudiosink: FM Audio Sink

This is just a trivial FM audio sink as one block, so I don't have to keep
copying and pasting it everywhere.

### saverawtofile: Saves raw samples from the SDR to a file

This is used to create reproduciable test cases for experimentation.

The file written by this will be in cs16 format.
 * c (complex. pairs of numbers representing the I/Q sample)
 * s (signed) u (unsigned) or f (floating point)
 * 8, 16, or 32 the bitwidth of the numbers in the pair.

They are just raw samples written to the file one after the other with no
header, footer, framing, or checksum.

### fileplayback: Playback a file previously created with saverawtofile

This is mostly used to make sure the data written out by the previous
experiment worked and is reasonable.


