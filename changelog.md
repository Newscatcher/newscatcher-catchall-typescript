## 1.2.0 - 2026-03-19
* The SDK now includes a `fetch()` method on `CatchAllApiClient` for making passthrough requests to API endpoints not yet supported in the SDK, using the client's configured authentication and retry settings. A new `getPlanLimits()` method is available on `MetaClient` to retrieve plan features and current usage. Job submission now supports an optional `mode` parameter with 'lite' and 'base' processing options.

