# Day 4 — Thursday, October 29: Entity extraction, OCR, and documents

[← Day 3](day-3-audio-diarization-asr-speaker-embeddings.md) · [Back to the plan](README.md) · [Next: Day 5 →](day-5-vlms-scene-descriptions-av-association.md)

## Introductory lecture (start here, 25–40 min)

- [spaCy: Linguistic features and named entities](https://spacy.io/usage/linguistic-features#named-entities) — practical introduction to NER and entity spans.
- [Hugging Face: Token classification](https://huggingface.co/docs/transformers/tasks/token_classification) — see how a model labels entities token by token.
- [PaddleOCR documentation](https://paddlepaddle.github.io/PaddleOCR/latest/en/index.html) — introductory view of OCR and document text extraction.

## Must learn

- Entity extraction/NER finds typed mentions; entity resolution decides which mentions refer to the same real entity.
- OCR extracts text; document understanding may also need layout, tables, key-value pairs, and source coordinates.
- Preserve original text, source/page/offset/bounding box, and confidence. Never merge entities by name alone.
- Separate a mention from a canonical entity; keep evidence links reversible.

## Build

Extract text and 3–5 entity types from a permitted sample. Design schemas for entity mention, canonical entity, source document, and evidence link. Draft conservative rules for identifiers, normalized names, context, and ambiguous candidates.

## Libraries

[spaCy](https://github.com/explosion/spaCy), [Transformers](https://github.com/huggingface/transformers), [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR), [docTR](https://github.com/mindee/doctr), [Presidio](https://github.com/microsoft/presidio).

## Models/methods

spaCy NER or a token-classification model; PaddleOCR/docTR baseline; rules and candidate generation before training a learned entity-resolution model.

## Papers/docs

[spaCy EntityRecognizer](https://spacy.io/api/entityrecognizer), [Hugging Face token classification](https://huggingface.co/docs/transformers/tasks/token_classification), [LayoutLMv3](https://arxiv.org/abs/2204.08387), [Presidio docs](https://microsoft.github.io/presidio/).

## Done when

Structured extraction JSON with source evidence and a clear distinction among extraction, normalization, and resolution.
