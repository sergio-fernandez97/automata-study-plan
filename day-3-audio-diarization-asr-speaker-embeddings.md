# Day 3 — Wednesday, October 28: Audio, diarization, ASR, speaker embeddings

[← Day 2](day-2-face-detection-embeddings-similarity-search.md) · [Back to the plan](README.md) · [Next: Day 4 →](day-4-entity-extraction-ocr-documents.md)

## Introductory lecture (start here, 25–40 min)

- [AssemblyAI: What is speaker diarization?](https://www.assemblyai.com/blog/speaker-diarization/) — accessible explanation of assigning speaker labels over time.
- [Whisper paper](https://arxiv.org/abs/2212.04356) — start with the abstract and overview to understand ASR and its limits.
- [pyannote.audio](https://github.com/pyannote/pyannote-audio) — inspect the project overview and diarization examples.

## Must learn

- VAD detects speech regions; diarization estimates who spoke when; ASR transcribes words; speaker recognition compares voice samples.
- Labels like `SPEAKER_00` are recording-local clusters, not real-world identities.
- Overlap, short utterances, noise, channel changes, language/accent, and cross-talk are failure cases.
- Preserve segment timestamps and confidence for alignment with video.

## Build

Run diarization and transcription on permitted audio. Output timestamped speaker segments and transcript spans. Keep speaker cluster, transcript span, and cross-modal identity candidate as separate concepts.

## Libraries

[pyannote.audio](https://github.com/pyannote/pyannote-audio), [Whisper](https://github.com/openai/whisper), [WhisperX](https://github.com/m-bain/whisperX), [SpeechBrain](https://github.com/speechbrain/speechbrain).

## Models/methods

[pyannote speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1) (check access/terms), [Whisper large-v3](https://huggingface.co/openai/whisper-large-v3), ECAPA-TDNN speaker embeddings via SpeechBrain. Voice similarity is candidate evidence, not proof of identity.

## Papers

[pyannote.audio 2.1](https://arxiv.org/abs/2210.01477), [Whisper](https://arxiv.org/abs/2212.04356), [SpeechBrain](https://arxiv.org/abs/2106.04624).

## Done when

Timestamped diarization/transcript output and a note explaining clustering versus identity.
