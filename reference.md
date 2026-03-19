# Reference
## Jobs
<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">initialize</a>({ ...params }) -> CatchAllApi.InitializeResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get suggested validators, enrichments, and date ranges for a query.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.initialize({
    query: "Series B funding rounds for SaaS startups",
    context: "Focus on funding amount and company name"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.InitializeRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">createJob</a>({ ...params }) -> CatchAllApi.SubmitResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a query to create a new processing job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.createJob({
    query: "Series B funding rounds for SaaS startups",
    context: "Focus on funding amount and company name",
    limit: 10,
    start_date: "2026-02-18T00:00:00Z",
    end_date: "2026-02-23T00:00:00Z",
    mode: "base"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.SubmitRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">continueJob</a>({ ...params }) -> CatchAllApi.ContinueResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Continue an existing job to process more records beyond the initial limit.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.continueJob({
    job_id: "5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
    new_limit: 100
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.ContinueRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">getJobStatus</a>({ ...params }) -> CatchAllApi.StatusResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the current processing status of a job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.getJobStatus({
    job_id: "5f0c9087-85cb-4917-b3c7-e5a5eff73a0c"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.GetJobStatusRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">getUserJobs</a>({ ...params }) -> CatchAllApi.ListUserJobsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all jobs created by the authenticated user.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.getUserJobs();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.GetUserJobsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">getJobResults</a>({ ...params }) -> CatchAllApi.PullJobResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the final results for a completed job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.jobs.getJobResults({
    job_id: "5f0c9087-85cb-4917-b3c7-e5a5eff73a0c"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.GetJobResultsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `JobsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Monitors
<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">createMonitor</a>({ ...params }) -> CatchAllApi.CreateMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a scheduled monitor based on a reference job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.createMonitor({
    reference_job_id: "5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
    schedule: "every day at 12 PM UTC",
    webhook: {
        url: "https://your-endpoint.com/webhook",
        method: "POST",
        headers: {
            "Authorization": "Bearer your_token_here"
        }
    },
    limit: 10,
    backfill: true
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.CreateMonitorRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">updateMonitor</a>({ ...params }) -> CatchAllApi.UpdateMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update the webhook configuration for an existing monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.updateMonitor({
    monitor_id: "monitor_id",
    webhook: {
        url: "https://new-endpoint.com/webhook",
        method: "POST",
        headers: {
            "Authorization": "Bearer new_token_xyz"
        }
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.UpdateMonitorRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">listMonitorJobs</a>({ ...params }) -> CatchAllApi.ListMonitorJobsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Return all jobs executed by a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.listMonitorJobs({
    monitor_id: "monitor_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.ListMonitorJobsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">pullMonitorResults</a>({ ...params }) -> CatchAllApi.PullMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve aggregated results from all jobs executed by a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.pullMonitorResults({
    monitor_id: "monitor_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.PullMonitorResultsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">disableMonitor</a>({ ...params }) -> CatchAllApi.DisableMonitorResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Stop scheduled job execution for a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.disableMonitor({
    monitor_id: "monitor_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.DisableMonitorRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">enableMonitor</a>({ ...params }) -> CatchAllApi.EnableMonitorResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Resume scheduled job execution for a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.enableMonitor({
    monitor_id: "monitor_id",
    backfill: true
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.EnableMonitorRequestDto` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">listMonitors</a>({ ...params }) -> CatchAllApi.ListMonitorsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all monitors created by the authenticated user.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.monitors.listMonitors();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CatchAllApi.ListMonitorsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `MonitorsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Meta
<details><summary><code>client.meta.<a href="/src/api/resources/meta/client/Client.ts">healthCheck</a>() -> CatchAllApi.HealthCheckResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Check API availability.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.meta.healthCheck();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `MetaClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.meta.<a href="/src/api/resources/meta/client/Client.ts">getVersion</a>() -> CatchAllApi.GetVersionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns current API version.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.meta.getVersion();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `MetaClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.meta.<a href="/src/api/resources/meta/client/Client.ts">getPlanLimits</a>() -> CatchAllApi.GetPlanLimitsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns plan features and current usage for the authenticated organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.meta.getPlanLimits();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `MetaClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

