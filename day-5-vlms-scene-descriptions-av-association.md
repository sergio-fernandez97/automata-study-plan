# Day 5 — Friday, October 30: VLMs, scene descriptions, audio-video association

[← Day 4](day-4-entity-extraction-ocr-documents.md) · [Back to the plan](README.md) · [Next: Day 6 →](day-6-architecture-contracts-evaluation.md)

## Introductory lecture (start here, 25–40 min)

- [Hugging Face: Image-text-to-text / vision-language models](https://huggingface.co/docs/transformers/tasks/image_text_to_text) — introductory walkthrough of feeding images and prompts to a VLM.
- [CLIP paper](https://arxiv.org/abs/2103.00020) — read the abstract and figures to understand joint image/text representations; CLIP is not a person-identity model.
- [TalkNet paper](https://arxiv.org/abs/2107.06592) — use the abstract and method overview to introduce active-speaker detection.

## Must learn

- Ground VLM prompts in selected frames/tracks and timestamps; don't ask a VLM to infer every identity/count from a long video in one free-form answer.
- VLMs can hallucinate, miscount, or confuse people. Require evidence and constrain descriptions to observable attributes.
- Temporal overlap alone does not establish that a visible person and voice are the same person.
- Keep descriptions separate from identity matching and downstream decisions.

## Build

Generate structured descriptions for selected keyframes/track crops: clothing, carried objects, visible actions, scene context, uncertainty. Audit unsupported claims. Draft an interpretable association score with an "unknown" outcome.

## Libraries/serving

[Transformers vision-language tasks](https://huggingface.co/docs/transformers/tasks/image_text_to_text), [vLLM](https://github.com/vllm-project/vllm), [OpenCLIP](https://github.com/mlfoundations/open_clip), [LLaVA](https://github.com/haotian-liu/LLaVA) (check licenses).

## Models/methods

Choose a locally deployable VLM only after checking license, VRAM, quantization, language, frame/video support, and structured output. Use CV for counts and track IDs; VLM descriptions enrich rather than overwrite these outputs. Research active-speaker detection separately.

## Papers

[CLIP](https://arxiv.org/abs/2103.00020), [LLaVA](https://arxiv.org/abs/2304.08485), [TalkNet active speaker detection](https://arxiv.org/abs/2107.06592).

## Done when

Grounded descriptions for a small clip and a list of VLM failure modes.
