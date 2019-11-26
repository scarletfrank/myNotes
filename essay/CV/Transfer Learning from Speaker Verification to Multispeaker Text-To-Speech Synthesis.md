# Transfer Learning from Speaker Verification to Multispeaker Text-To-Speech Synthesis
## Abstract
**TTS system**
- *speaker encoder network* : generate a fixed-dimension embedding vector
- *synthesis network* : generate a mel spectrogram from text
- *vocoder network*: convert the mel spectrogram into time domain waveform samples
## Introduction
A zero-shot learning setting, where a few seconds of untranscribed reference audio from a target speaker is used to synthesize new speech in that speaker's voice, without updating any model parameters.
帮助失声人士（只能提供只言片语，无法提供大量的新样本）| 跨语言但同语音的翻译
Training on a large number of high-quality speech-transcript pairs is required for synthesization of natural speech.
Our approach: to decouple speaker modeling from speech synthesis by independently training a speaker-discriminative embedding network that captures the space of speaker characteristics and training a high quality TTS model on a smaller dataset conditioned on the representation learned by the first network.
**Related Works**
## Multispeaker speech synthesis model
1. Speaker encoder
[GE2Loss]() : a highly scalable and accurate neural network framework for speaker verification. The network maps a sequence of log-mel spectrogram frames computed from a speech utterance of arbitrary length, to a fixed-dimensional embedding vector, known as *d-vector*
2. Synthesizer
We extend the recurrent sequence-to-sequence with attention Tacotron 2 architecture to support multiple speakers following a scheme similar to [..]
The synthesizer is trained on pairs of text transcript and target audio.
3. Neural vocoder
sample-by-sample autoregressive WaveNet as a vocoder to invert synthesized mel spectrograms emitted by the synthesis network into time-domain waveforms.
4. Inference and zero-shot speaker adaptation
arbitrary untranscribed speech audio
## Experiments
Datasets: (1) VCTK 109 speakers (2) LibriSpeech (contain noticeable environmental and stationary background noise) 1172 speakers
split into three subsets: train, validation (contain the same speaker as the train set) and test (contain speakers held out from the train and validation sets)
Seen: in the train set | Unseen: held out
**Mean opinion score**： $MOS=\frac {\sum_{n-1}^N R_n} {N}$
1. Speech naturalness
Natural for both seen set and unseen set.
2. Speaker similarity
The proposed model is able to transfer the broad strokes of the speaker characteristics for unseen speakers, clearly reflecting the correct gender, pitch, and formant ranges. But some nuances.
3. Speaker verification
*eval-only* speaker encoder (a different training set)
**SV-EERs**: Speaker verification equal error rates
4. Speaker embedding space
Visualization: PCA t-NSE
5. Number of speaker encoder training speakers
The data requirement for the speaker encoder is much cheaper than full TTS training since no transcripts are necessary, and the audio quality can be lower than for TTS training.
6. Fictitious speakers
## Conclusion
