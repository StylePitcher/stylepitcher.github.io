---
layout: home
title: StylePitcher
description: Generating Style-Following, Expressive Pitch Curves for Versatile Singing Tasks
---

# Introduction

In this paper, we propose **StylePitcher**, the first general-purpose pitch curve generation model that learns to follow singing styles from reference audio. We formulate pitch generation as a masked infilling task: given surrounding pitch context and musical scores, StylePitcher learns to generate missing pitch segments that naturally continue the style patterns. 

Once trained, StylePitcher serves as a plug-and-play module for diverse applications: enhancing **pitch correction with style preservation**, enabling **style transfer in SVS systems**, and improving **expressiveness in SVC**.

<div align="center">
  <img src="figures/models.png" width=800 alt="">
  <figcaption><strong>Fig.1</strong> Illustration of the model architecture of (a) StylePitcher and (b) Applications.</figcaption>
</div>

# Generation Examples

We present audio examples from baselines and our methods in this section, including following applications:
* Automatic Pitch Correction
* Style Transfer for Singing Voice Synthesis
* Style-informed Singing Voice Conversion

## Automatic Pitch Correction (APC)

Given a detuned singing voice and a target note sequence, APC aims to generate an in-tune pitch contour that aligns with the target notes while preserving the singer's original style. 

<table class="audio-table">
  <thead>
    <tr class="header">
    <th>Off-key Singing</th>
    <th>Target Notes</th>
    <th>Diff-Pitcher</th>
    <th>StylePitcher</th>
    <th>StylePitcher (w/o smooth)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><audio controls=""><source src="assets/demos/APC/f1_0.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f1_0_midi.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f1_0_tuned.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f1_0_tnued_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f1_0_tnued_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/APC/f3_16.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f3_16_midi.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f3_16_tuned.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f3_16_tnued_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/f3_16_tnued_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/APC/m2_1.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_1_midi.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_1_tuned.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_1_tnued_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_1_tnued_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/APC/m2_9.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_9_midi.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_9_tuned.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_9_tnued_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/APC/m2_9_tnued_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
  </tbody>
</table>

## Style Transfer for Singing Voice Synthesis (SVS)

Given target lyrics, musical score and a reference singing voice, style transfer for SVS aims to synthesize vocals that match the target content while resembling the singing styles of the reference. Our methods support both parallel and non-parallel style transfer.

### Parallel Style Transfer
In the parallel style transfer setting, the content of the reference singing voice is the same as the target lyrics and musical scores. We show the reference audio here for both the singing content (lyrics and musical scores) and the reference singing styles.

<table class="audio-table">
  <thead>
    <tr class="header">
    <th>Reference</th>
    <th>StyleSinger</th>
    <th>StylePitcher</th>
    <th>StylePitcher (w/o smooth)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS/data_3020_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_3020_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_3020_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_3020_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS/data_1110_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_1110_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_1110_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_1110_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS/data_4230_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_4230_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_4230_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_4230_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS/data_6900_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_6900_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_6900_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS/data_6900_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
  </tbody>
</table>

### Non-Parallel Style Transfer
In the non-parallel style transfer setting, the content of the reference singing voice is different as the target lyrics and musical scores. 

**Example 1**

* Target lyrics: 离别没说再见<AP>你是否心酸
* Target Phoneme: l i b ie m ei ei sh uo z ai j ian <AP> n i sh i f ou x in s uan uan
* Target Notes: 60 60 58 58 59 59 60 63 63 63 63 58 58 0 55 55 55 55 56 56 58 58 59 59 60

<table class="audio-table">
  <thead>
    <tr class="header">
    <th>Reference</th>
    <th>StyleSinger</th>
    <th>StylePitcher</th>
    <th>StylePitcher (w/o smooth)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_3450_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_0_gen_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_0_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_0_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
  </tbody>
</table>

**Example 2**
* Target lyrics: 无法遗忘
* Target Phoneme: u u f a a i i i uang uang uang
* Target Notes: 61 62 64 64 66 72 73 74 72 73 70

<table class="audio-table">
  <thead>
    <tr class="header">
    <th>Reference</th>
    <th>StyleSinger</th>
    <th>StylePitcher</th>
    <th>StylePitcher (w/o smooth)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/f5_arpeggios_vibrato_a.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_240_gen_stylesinger.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_240_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVS_non_parallel/data_240_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
  </tbody>
</table>

## Style-informed Singing Voice Conversion (SVC)
While most existing SVC methods use the unchanged F0 from the target audio to generate vocals with the reference singer's timbre, StylePitcher can modify the F0 to also capture the singing styles of the target singer. In the following examples, target audio provides the singing content, and reference audio indicates the timbre and styles to converted.

<table class="audio-table">
  <thead>
    <tr class="header">
    <th>Target</th>
    <th>Reference</th>
    <th>In-house SVC</th>
    <th>StylePitcher</th>
    <th>StylePitcher (w/o smooth)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVC/data_6330_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_6980_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_6330_singer=6980.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_6330_singer=6980_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_6330_singer=6980_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVC/data_4740_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_6770_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_4740_singer=6770.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_4740_singer=6770_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_4740_singer=6770_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVC/data_480_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_3450_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_480_singer=3450.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_480_singer=3450_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_480_singer=3450_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
    <tr>
      <td><audio controls=""><source src="assets/demos/SVC/data_300_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_vibrato_original.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_300_singer=vibrato.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_300_singer=vibrato_ours.wav" type="audio/mpeg" /></audio></td>
      <td><audio controls=""><source src="assets/demos/SVC/data_300_singer=vibrato_ours_unsmooth.wav" type="audio/mpeg" /></audio></td>
    </tr>
  </tbody>
</table>

[jekyll-organization]: https://github.com/jekyll
