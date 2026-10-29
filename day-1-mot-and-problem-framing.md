# Day 1 — Monday, October 26: MOT and problem framing

[← Back to the plan](README.md) · [Next: Day 2 →](day-2-face-detection-embeddings-similarity-search.md)

## Introductory lecture (start here, 20–35 min)

- [Roboflow: Object Tracking Explained](https://blog.roboflow.com/what-is-object-tracking-computer-vision/) — an accessible visual introduction to detections, track IDs, and tracking pipelines.
- [Roboflow: Comprehensive Guide to Multiple Object Tracking](https://roboflow.com/blog/multiple-object-tracking)
- [Ultralytics: Track mode](https://docs.ultralytics.com/modes/track/) — follow the concepts in a practical implementation and inspect the annotated examples.
- Then skim the [ByteTrack paper](https://arxiv.org/abs/2110.06864) for the core idea; don't aim to understand every equation on the first pass.

## Must learn

- Detection is frame-level; tracking links detections across frames. Track IDs are not identity across videos/cameras.
- Pipeline: decode/sample frames → person detection → association/tracker → track management → tracklet metadata → optional re-identification.
- Learn boxes, confidence, occlusion, ID switches, fragmentation, false positives/negatives.
- Keep labels conservative and observable; avoid inferring sensitive traits.

## Build (60–90 min)

Run a pretrained person detector and tracker on a short permitted clip. Save an annotated video and JSONL observations with timestamps, track IDs, boxes, and confidence. Sketch the existing/target pipeline.

## Libraries

[Ultralytics YOLO tracking](https://docs.ultralytics.com/modes/track/), [Ultralytics repo](https://github.com/ultralytics/ultralytics), [BoxMOT](https://github.com/mikel-brostrom/boxmot), [OpenCV](https://github.com/opencv/opencv), [PyTorch](https://github.com/pytorch/pytorch).

## Models/methods

YOLO-family person detector; ByteTrack or BoT-SORT tracker. ReID embeddings can reconnect tracklets but do not prove identity.

## Papers

[ByteTrack (ECCV 2022)](https://arxiv.org/abs/2110.06864), [BoT-SORT](https://arxiv.org/abs/2206.14651), [MOTChallenge](https://motchallenge.net/).

## Repositories

[ByteTrack](https://github.com/FoundationVision/ByteTrack), [BoT-SORT](https://github.com/NirAharon/BoT-SORT), [BoxMOT](https://github.com/mikel-brostrom/boxmot).

## Done when

Annotated clip, one-page MOT diagram, and questions for the service maintainer.
