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

