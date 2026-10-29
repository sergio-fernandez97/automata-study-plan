# 🧭 One-Week Study Plan — Intelligent Multimodal Perception

> **Goal:** Be ready to contribute to an existing intelligent perception service by Monday, November 2, 2026. Prioritize the end-to-end system, missing modules, contracts, and evaluation—not GPU administration.

> [!IMPORTANT]
> 🎯 This is an entity-centric perception and resolution system, not simply an object detector or a VLM prompt. Separate detection, within-stream tracking, attribute/event extraction, and cross-modal entity resolution. A face or voice similarity score is not verified identity.

## Daily plan

| Day | Date | Topic |
|---|---|---|
| [Day 1](day-1-mot-and-problem-framing.md) | Monday, October 26 | MOT and problem framing |
| [Day 2](day-2-face-detection-embeddings-similarity-search.md) | Tuesday, October 27 | Face detection, embeddings, and similarity search |
| [Day 3](day-3-audio-diarization-asr-speaker-embeddings.md) | Wednesday, October 28 | Audio, diarization, ASR, speaker embeddings |
| [Day 4](day-4-entity-extraction-ocr-documents.md) | Thursday, October 29 | Entity extraction, OCR, and documents |
| [Day 5](day-5-vlms-scene-descriptions-av-association.md) | Friday, October 30 | VLMs, scene descriptions, audio-video association |
| [Day 6](day-6-architecture-contracts-evaluation.md) | Saturday, October 31 | Architecture, contracts, evaluation |
| [Day 7](day-7-integrate-and-prepare-kickoff.md) | Sunday, November 1 | Integrate and prepare kickoff |

## Success criteria for November 2

- Explain MOT and why a track ID is not a real-world identity.
- Explain face embeddings, similarity search, thresholds, and failure modes.
- Distinguish diarization, ASR, and speaker identity embeddings.
- Propose an entity schema linking tracks, face crops, audio segments, transcript spans, OCR/document mentions, timestamps, confidence, and provenance.
- Identify existing service gaps and define a baseline plus metrics for each.
- Recommend evaluation and a safe review path for uncertain matches.

## Time budget

Aim for 3–4 focused hours per day (22–26 hours total). If time is tight, do the Must learn and small deliverable first. Ask the team for the current architecture, input/output examples, latency and volume targets, supported languages, and rules for biometric data.

## How to use this plan

Read one paper and inspect one runnable repository per day, then spend the remaining time running a baseline and writing down errors. Check current model cards, licenses, language support, access requirements, and hardware needs before selecting checkpoints; repository popularity alone is not a deployment criterion.

## Reference architecture (starting hypothesis)

Media/document ingestion → timestamping/decoding → parallel branches:

- Video frames → person detection → MOT tracklets → face detection/quality/embeddings → similarity candidates.
- Audio → VAD/diarization → ASR and timestamped transcript → speaker clusters.
- Images/documents → OCR/layout → text entity extraction and mentions.
- Tracklets → grounded VLM descriptions and scene context.
- All branches → candidate association/entity resolution with evidence → canonical entities plus confidence/uncertainty → policy-controlled downstream decision system.

This is a hypothesis, not a mandate to rebuild. Map the existing service first and reuse components that meet acceptance criteria.

## Suggested data contract

Each observation should preserve:

- observation ID, source ID, modality, start/end time
- track ID / speaker cluster ID / document ID as distinct fields
- bounding box or text offsets/page region
- labels, attributes, transcript, optional embedding reference
- confidence, quality flags, model name/version
- evidence references, creation time, processing status
- candidate entity IDs, match score/method, decision: matched, unresolved, rejected, needs review

Keep embeddings/raw biometrics out of general logs; apply access controls, retention rules, encryption, and audit trails.

## Evaluation and safety checklist

- **Detection:** precision/recall by lighting, blur, occlusion, and camera angle.
- **MOT:** HOTA, IDF1, ID switches, fragmentation; crowded/occluded scenes.
- **Face:** ROC/DET, TAR at fixed FAR, false-match analysis, quality filtering, open-set behavior.
- **Audio:** DER, WER, timestamp alignment, overlap, per-language performance.
- **Extraction:** precision/recall/F1 by entity type, normalization errors, evidence completeness.
- **Cross-modal resolution:** accepted-link precision, false-match rate, abstention rate, calibration; include ambiguous and negative pairs.
- **VLM:** grounded attribute accuracy, unsupported claims, completeness, reviewer agreement.
- **Product:** p50/p95 latency, throughput, failure/retry rate, VRAM, cold start, reproducibility.
- **Governance:** permitted data use, consent/legal basis, retention, access, deletion, auditability, human review for consequential decisions.

## Follow-up roadmap after November 2

### Week 1: discover and baseline

- Walk the existing service end-to-end with a maintainer; document modules, models, contracts, dependencies, deployment boundaries.
- Agree on approved sample inputs, expected outputs, use cases, and acceptance metrics.
- Run baselines and error analysis before replacing models.
- Prioritize the two highest-value missing modules.

### Week 2: implement one gap

- Implement one module behind a stable contract with tests, provenance, structured logs, and failure handling.
- Compare baseline vs candidate on agreed metrics and edge cases.
- Support unresolved/needs-review for ambiguous matches.

### Weeks 3–4: integration and reliability

- Integrate; measure end-to-end latency, queueing, memory, and concurrency on the on-prem environment.
- Build regression tests from observed failures; add model/version tracking and evaluation dashboard.
- Review privacy/security for biometric and document data.

### Weeks 5–6: optimize and harden

- Profile first; then consider batching, frame sampling, caching, index choice, quantization, and GPU utilization.
- Test robustness across camera, audio, language, and document conditions.
- Formalize model release gates, rollback, monitoring, and retention workflows.

### Later: improve entity resolution

- Build labeled same-entity / different-entity / uncertain pairs across modalities.
- Compare rules, calibrated similarity scoring, and graph-based evidence aggregation.
- Consider learned fusion only if simpler interpretable baselines do not meet requirements.

## Questions for the team

- What does the existing service already do, and which modules are explicitly missing?
- Is scope same-person tracking within one video, across videos/cameras, or cross-modal resolution across audio/video/documents? These are different problems.
- Are face/voice biometrics permitted? What are consent, retention, and access requirements?
- What are video duration, camera count, languages, concurrency, latency, and on-prem GPU/VRAM?
- Which downstream decisions consume the result, and what false-match risk is acceptable?
- Which data/model licenses are acceptable for commercial on-prem use?
