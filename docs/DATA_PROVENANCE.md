# Data Provenance and Use Policy

## Current evaluation data

ASA5 public demonstrations and current internal calibration runs use controlled
synthetic dialogue trajectories. Evaluation inputs are separated from hidden
ground truth, and public materials do not contain raw private or identifying
conversation content.

Synthetic or authorized telemetry does not automatically constitute validation
evidence. Governance claims require a frozen protocol, declared negative controls,
predefined failure criteria, and results that can be reviewed independently.

## Early exploratory public-dialogue pilot

During an early engineering pilot, ASA5 processed a limited public X dataset
consisting predominantly of the author's own public interactions with Grok. The
pilot covered 193 collected source records, 48 working TDB conversation groupings,
and 40 dialogue pairs imported into an operational test pipeline.

The material was used to test ingestion, ordering, provenance handling, and
trajectory-processing mechanics. It was not used to train ASA5, and it was not
accepted as ground truth or as evidence of governance-detection performance.

The project concluded that public dialogue without independently established
provenance, authorization boundaries, a frozen reference label, and suitable
negative controls is not governance-eligible. The collected records and their
derived database entries, caches, fixtures, validation outputs, and associated
screenshots were removed from the product and public repository.

## Policy resulting from the pilot

Future experiments must follow these rules:

- use synthetic, explicitly authorized, or appropriately licensed telemetry;
- keep source provenance and authorization status auditable;
- separate observable input from hidden ground truth;
- include clean negative-control trajectories;
- declare metrics and failure criteria before evaluation;
- keep exploratory evidence separate from governance-qualified evidence;
- publish only public-safe aggregate reports without raw identifying content.

Provider-specific connector code may be retained as an inactive technical
capability. Its presence does not indicate that provider data is bundled,
collected by default, governance-eligible, or used to train ASA5.

## Public claim boundary

ASA5 remains a working prototype and partner-evaluation system. It has not yet
completed independent statistical validation and must not be presented as a
certified safety-critical control.
