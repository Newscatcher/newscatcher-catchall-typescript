## 0.3.0 - 2026-01-19
* feat: add job continuation and monitor update capabilities
* Add new functionality to extend job processing limits and update monitor webhooks without recreating resources.
* Key changes:
* Add job continuation endpoint to process more records beyond initial limit
* Add monitor update endpoint for webhook configuration changes
* Update SDK generator versions (CLI 3.32.0→3.47.0, TS SDK 3.42.8→3.43.13)
* Upgrade @biomejs/biome dependency from 2.3.1 to 2.3.11
* Add BadRequestError exception type for 400 status codes
* Update test helpers with ignored fields support for dynamic values
* Enhance job status tracking with progress_validated field
* 🌿 Generated with Fern

