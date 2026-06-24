## [4.0.0] - 2026-06-24
### Breaking Changes
- **`CreateMonitorRequestDto.webhook`** — replaced by `webhook_ids?: string[]`; pass an array of pre-registered webhook IDs (e.g. `webhook_ids: ["<id>"]`) instead of an inline `WebhookDto` object.
- **`UpdateMonitorRequestDto.webhook`** — replaced by `webhook_ids?: string[]`; update all `updateMonitor` calls to pass an array of webhook IDs instead of a `WebhookDto` object.

### Added
- **`WebhooksClient`** — new top-level client (`client.webhooks`) for creating, retrieving, updating, deleting, and test-firing reusable webhook endpoints; supports Slack, Microsoft Teams, and generic HTTP targets, plus resource assignment and delivery history retrieval.
- **`ProjectsClient`** — new top-level client (`client.projects`) for creating, retrieving, updating, deleting, and managing resource associations (jobs, monitors, datasets) for projects.
- **`JobsClient.validateQuery()`** — validates a plain-text query before job submission, returning a structured quality assessment with status, issues, and suggestions.
- **`JobsClient.getJobResultsCsv()`** and **`MonitorsClient.pullMonitorResultsCsv()`** — download completed job or monitor run results as a CSV string.
- **`project_id`** and **`webhook_ids`** optional fields — added to `SubmitRequestDto`, `CreateMonitorRequestDto`, and list-request types (`ListDatasetsRequest`, `GetUserJobsRequest`, `ListMonitorsRequest`) to scope and notify resources by project or webhook; new fields also added to `InitializeRequestDto`, `PullJobResponseDto`, `PullMonitorResponseDto`, and `CreateEntityRequest`/`EntityResponse`.
- See full changelog for all changes

### Fixed
- **`getResponseBody`** — now pins the upstream `Response` object to prevent undici's garbage collector from cancelling in-flight body streams.

## 2.0.0 - 2026-05-19
### Breaking Changes
* **`ListEntitiesInDatasetRequest`** has been renamed to `ListDatasetEntitiesRequest`; update all type references and imports to use the new name.
* **`listEntitiesInDataset`** now sends a `POST` request to `/catchAll/datasets/{id}/entities/list` instead of a `GET` to `/catchAll/datasets/{id}/entities`; any custom request interceptors or mocks targeting the old method and path must be updated.
### Added
* **`ListDatasetEntitiesRequest`** — new request type replacing `ListEntitiesInDatasetRequest`, with an additional `search` field description clarifying case-insensitive substring matching.
* **`SubmitRequestDto.ed_score_min`** — new optional field to set a minimum relevance score threshold for connected entities in Company Watchlist jobs.
* **`CreateMonitorRequestDto.timezone`** — new optional IANA timezone identifier field; the `schedule` string no longer needs to embed a timezone abbreviation.
* **`ConnectedEntity`** — gains new required `relation` and `type` fields, plus an optional `company` field (`CompanyAttributes`) for entity attribute data.
* **`AuthOption`** type and `auth` option on `BaseClientOptions` — allows overriding authentication per-client instance by passing `false`, a function, an `AuthProvider`, or auth options.

## 1.5.1 - 2026-04-30
* chore: migrate query parameter handling to queryBuilder() across all clients
* Replace the legacy `queryParameters` object spread pattern with the
* `core.url.queryBuilder()` fluent API across all resource clients
* (Datasets, Entities, Jobs, Meta, Monitors). This aligns internal HTTP
* request construction with the `queryString` field introduced alongside
* `queryBuilder()`, and deprecates the old `queryParameters` field in
* `Fetcher.Args` for custom fetcher authors.
* Key changes:
* Replace `queryParameters: { ..._queryParams, ...requestOptions?.queryParams }` with `queryString: core.url.queryBuilder().addMany(_queryParams).mergeAdditional(requestOptions?.queryParams).build()` across all clients
* Replace `queryParameters: requestOptions?.queryParams` with `queryString: core.url.queryBuilder().mergeAdditional(requestOptions?.queryParams).build()` for parameter-less endpoints
* Mark `Fetcher.Args.queryParameters` as `@deprecated` with a note to prefer `queryString`; retain field for backwards compatibility with custom fetchers
* Remove redundant `?? undefined` coercion in `listMonitorJobs` sort default and simplify `redactQueryParameters` internals
* 🌿 Generated with Fern

## 1.5.0 - 2026-04-23
### Added
* **`JobsClient.deleteJob()`** — soft-deletes a job by ID; only the owner can delete, and deleting an already-deleted job returns success.
* **`MonitorsClient.deleteMonitor()`** and **`MonitorsClient.getMonitorStatusHistory()`** — soft-delete a monitor by ID and retrieve its full lifecycle event history as `MonitorStatusEntry` records, respectively.
* **`ownership`** and **`search`** — new optional filter parameters added to `ListMonitorsRequest`, `GetUserJobsRequest`, and `ListDatasetsRequest`, accepting an `OwnershipFilter` enum (`all` | `own` | `shared`) and a search string.
* **`SharingInfo`** — new interface representing sharing metadata (shared time, permission level, sharer name) exposed via the new `sharing_info` optional field on `UserJob`, `MonitorListItemDto`, and `PullJobResponseDto`.
* **New exported types** — `UnauthorizedError`, `DeleteJobResponseDto`, `DeleteMonitorResponseDto`, `MonitorStatusEntry`, `MonitorStatusHistoryResponseDto`, `OwnershipFilter`, and `SharingInfo` are now available from the types index; `queryBuilder()` fluent utility added to `core/url` for constructing URL query strings.

