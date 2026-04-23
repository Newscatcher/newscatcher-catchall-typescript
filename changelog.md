## 1.5.0 - 2026-04-23
### Added
* **`JobsClient.deleteJob()`** — soft-deletes a job by ID; only the owner can delete, and deleting an already-deleted job returns success.
* **`MonitorsClient.deleteMonitor()`** and **`MonitorsClient.getMonitorStatusHistory()`** — soft-delete a monitor by ID and retrieve its full lifecycle event history as `MonitorStatusEntry` records, respectively.
* **`ownership`** and **`search`** — new optional filter parameters added to `ListMonitorsRequest`, `GetUserJobsRequest`, and `ListDatasetsRequest`, accepting an `OwnershipFilter` enum (`all` | `own` | `shared`) and a search string.
* **`SharingInfo`** — new interface representing sharing metadata (shared time, permission level, sharer name) exposed via the new `sharing_info` optional field on `UserJob`, `MonitorListItemDto`, and `PullJobResponseDto`.
* **New exported types** — `UnauthorizedError`, `DeleteJobResponseDto`, `DeleteMonitorResponseDto`, `MonitorStatusEntry`, `MonitorStatusHistoryResponseDto`, `OwnershipFilter`, and `SharingInfo` are now available from the types index; `queryBuilder()` fluent utility added to `core/url` for constructing URL query strings.

