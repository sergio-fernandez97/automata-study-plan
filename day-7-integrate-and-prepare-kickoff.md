# Day 7 — Sunday, November 1: Integrate and prepare kickoff

[← Day 6](day-6-architecture-contracts-evaluation.md) · [Back to the plan](README.md)

## Introductory lecture (start here, 20–30 min)

- [Full Stack Deep Learning: Course materials](https://fullstackdeeplearning.com/course/) — choose an introductory lecture/module on ML systems, deployment, and testing.
- [FastAPI: First steps](https://fastapi.tiangolo.com/tutorial/first-steps/) — quick introduction to exposing a typed model/service interface.
- [Pydantic: Models](https://docs.pydantic.dev/latest/concepts/models/) — learn the basics of validating structured input/output contracts.

## Must learn

- Reproduce baselines from a clean environment; pin versions and check licenses.
- Decide batch vs. streaming and add queues/retries/backpressure only according to real requirements.
- On-prem matters for data residency and access control; GPU tuning can wait until profiling.

## Build

Create a small end-to-end demo on permitted media: tracks + optional face candidates + diarization/transcript + OCR/entity mentions + scene description. Emit a timeline/JSON artifact with evidence and unresolved links clearly marked. Prepare a kickoff brief: known system, unknowns, risks, first two-week experiment, acceptance criteria.

## Libraries

[Pydantic](https://github.com/pydantic/pydantic) for contracts, [FastAPI](https://github.com/fastapi/fastapi) for interfaces, [MLflow](https://github.com/mlflow/mlflow) for experiment tracking, [OpenTelemetry Python](https://github.com/open-telemetry/opentelemetry-python) for tracing, [Docker Compose](https://docs.docker.com/compose/) for reproducible orchestration.

## Done when

Demo or architecture walkthrough, one-page kickoff brief, and top five unknowns ranked by risk.
