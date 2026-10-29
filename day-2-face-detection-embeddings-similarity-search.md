# Day 2 — Tuesday, October 27: Face detection, embeddings, and similarity search

[← Day 1](day-1-mot-and-problem-framing.md) · [Back to the plan](README.md) · [Next: Day 3 →](day-3-audio-diarization-asr-speaker-embeddings.md)

## Introductory lecture (start here, 25–40 min)

- [ArcFace paper](https://arxiv.org/abs/1801.07698) — read the abstract, introduction, and figure explaining angular margin; focus on what an embedding represents.
- [InsightFace project](https://insightface.ai/) — overview of face analysis and recognition components.
- [FAISS getting started](https://github.com/facebookresearch/faiss/wiki/Getting-started) — introductory guide to nearest-neighbor similarity search.

## Must learn

- Face detection/alignment → quality filtering → embedding → vector search → calibrated threshold → review/abstention.
- Verification (same/different pair) differs from identification (search against a gallery). Nearest neighbor is not automatically a correct match.
- Pose, lighting, blur, resolution, occlusion, and domain mismatch affect scores.
- Store provenance and permissions; minimize biometric retention and restrict access.

## Build

Create a toy gallery with permitted, consented/public benchmark data. Compare cosine similarity for same/different pairs and discuss false-match vs. false-non-match trade-offs. Define an API returning candidate IDs, score, quality flags, model version, and review outcome.

## Libraries

[InsightFace](https://github.com/deepinsight/insightface) (check model/dataset license), [FAISS](https://github.com/facebookresearch/faiss), [OpenCV](https://github.com/opencv/opencv), [scikit-learn evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html).

## Models/methods

ArcFace-style embeddings as a baseline; FAISS exact similarity search first, approximate indexing only if gallery size/latency needs it. Consider aggregating high-quality face observations across a track.

## Papers/resources

[ArcFace (CVPR 2019)](https://arxiv.org/abs/1801.07698), [InsightFace](https://insightface.ai/), [NIST Face Recognition Technology Evaluation](https://www.nist.gov/programs-projects/face-recognition-technology-evaluation-frte).

## Repositories

[InsightFace](https://github.com/deepinsight/insightface), [FAISS](https://github.com/facebookresearch/faiss).

## Done when

Similarity-search prototype/pseudocode, threshold explanation, and biometric data checklist.
