## 1.1.0 - 2026-03-09
* feat: add support for jobs, monitors, and meta API exports
* Expand SDK API coverage by adding modular exports for specific resource domains and improving type definitions for enhanced developer experience.
* Key changes:
* Add package.json exports for `./jobs`, `./monitors`, and `./meta` modules
* Remove deprecated `schema` parameter from job submission interface
* Update job response types from `SubmitResponseBody` to `SubmitResponseDto`
* Enhance monitor creation with `limit` and `backfill` parameters
* Add pagination support to monitor listing with `page` and `page_size`
* Update enrichment types to include structured `CompanyEnrichmentOutput`
* Improve type safety with explicit undefined unions and nullable types
* Add SSE (Server-Sent Events) support in fetcher with cache-control options
* Upgrade development dependencies including Biome formatter
* 🌿 Generated with Fern

