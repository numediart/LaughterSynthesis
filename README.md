# LaughterSynthesis

This repository contains implementations of laughter synthesis systems. And the samples used for the MOS test in [[2]](#2).

### For reproducibility of the ICASSP 2015 paper [[1]](#1).

* The HTS demo found [here](http://hts.sp.nitech.ac.jp/hts-users/spool/2012/msg00113.html) can be used to replicate the results described in this work.
* The SpkB-Fr subject of the AmuS dataset was used to train this system
* For the AmuS dataset, please contact kevin [dot] elhaddad [at] umons [dot] ac [dot] be

### For reproducibility of the Interspeech 2020 paper [[2]](#2):

* Training process:
    * The DCTTS system is first trained using the speech from Acapela, the smiled speech and laughs from AmuS (preferably coming from the subject SpkB).
    * The same system is then fine-tuned using the same smiled speech and laughs of the AmuS dataset.
    * The MelGAN system is used without (re-)training.
    
* Run time:
    * a sequence of laughter labels are given at the input of the DCTTS which generates a somewhat noisy waveform.
    * this waveform is then passed by the MelGAN system, which generated a "cleaned" version of this waveform.

* DCTTS-MelGAN implementations:
    * The DCTTS implementation used in this project was: https://github.com/CSTR-Edinburgh/ophelia
    This system generates audio signals. These signals are then passed to the MelGAN system.
    * The MelGAN implementation used in this project was: https://github.com/descriptinc/melgan-neurips
    The model used is the models/multi_speaker.pt
    This will remove the artifacts and other noises that might be generated in the DCTTS system.

* Concerning the data used in this work:
    * The Acapela voice used is a propriatary dataset and can therefore, unfortunately not be distributed. But this system should work when pre-trained with other voices as well in a similar way as described in [[2]](#2).
    * For the AmuS dataset, please contact kevin [dot] elhaddad [at] umons [dot] ac [dot] be

* The HTS based system was the same as the one from for ICASSP 2015 article [[1]](#1) [1]

## References
<a id="1">[1]</a> 
Kevin El Haddad, Stephane Dupont, Jerome Urbain, Thierry Dutoit "Speech-laughs: an HMM-based approach for amused speech synthesis." 2015 ICASSP.

<a id="2">[2]</a> 
Noe Tits, Kevin El Haddad, Thierry Dutoit, "Laughter Synthesis: Combining Seq2seq modeling with Transfer Learning" 2020 Interspeech (In press)
