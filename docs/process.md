# Process

This repo is organized around versioned schema releases.

1. NLM provides an updated DATMM spreadsheet.
2. A maintainer adds it under `schema/<version>/excel/incoming/` for review.
3. Once approved, the exact spreadsheet is copied into `schema/<version>/excel/released/`.
4. RDF/XML for the same version is produced and added under `schema/<version>/rdf/rdfxml/`.
5. Update `CHANGELOG.md`.
6. Tag a release `v<version>`.

See `docs/release-checklist.md` for the release gate checklist.
