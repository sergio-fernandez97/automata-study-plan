# Day 6 — Saturday, October 31: Architecture, contracts, evaluation

[← Day 5](day-5-vlms-scene-descriptions-av-association.md) · [Back to the plan](README.md) · [Next: Day 7 →](day-7-integrate-and-prepare-kickoff.md)

## Introductory lecture (start here, 20–35 min)

- [Google ML: Rules of ML](https://developers.google.com/machine-learning/guides/rules-of-ml) — practical principles for building reliable ML products around models.
- [HOTA paper](https://arxiv.org/abs/2009.07736) — read the abstract and metric intuition for tracking evaluation.
- [scikit-learn: Model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html) — a reference for classification metrics, calibration, and thresholding.

## Must learn

- Versioned modules need typed inputs/outputs, timestamps, confidence, provenance, model version, errors, and latency.
- Keep observations, tracklets, mentions, candidate matches, and canonical entities distinct.
- Evaluate modules independently and end-to-end; strong detection does not guarantee correct resolution.
- Use calibrated thresholds, abstention, audit trails, and human review for uncertain/high-impact identity matches.

## Build

Draft a schema and tiny labeled set containing positive, negative, and ambiguous examples. Create a module gap matrix: current capability, missing capability, baseline, evidence, acceptance metric, dependency/owner.

## Metrics

- Detection precision/recall
- MOT HOTA/IDF1/ID switches
- Face verification ROC/DET and TAR at fixed FAR
- Diarization DER; ASR WER
- Extraction entity-level precision/recall/F1
- Resolution false-match rate, accepted-link precision, abstention rate and calibration
- VLM grounded attribute accuracy/unsupported-claim rate
- Product p50/p95 latency, throughput, failures, and VRAM

## References

[HOTA paper](https://arxiv.org/abs/2009.07736), [TrackEval](https://github.com/JonathonLuiten/TrackEval), [pyannote metrics](https://github.com/pyannote/pyannote-metrics), [NIST FRTE](https://www.nist.gov/programs-projects/face-recognition-technology-evaluation-frte), [scikit-learn evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html).

## Done when

Module diagram, JSON schema, evaluation checklist, and prioritized gap matrix.
