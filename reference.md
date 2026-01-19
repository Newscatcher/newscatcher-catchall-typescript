# Reference
## Jobs
<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">createJob</a>({ ...params }) -> CatchAllApi.SubmitResponseBody</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a natural language query to create a new processing job.
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
    query: "AI company acquisitions",
    context: "Focus on deal size and acquiring company details"
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
    job_id: "af7a26d6-cf0b-458c-a6ed-4b6318c74da3",
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
    job_id: "af7a26d6-cf0b-458c-a6ed-4b6318c74da3"
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

<details><summary><code>client.jobs.<a href="/src/api/resources/jobs/client/Client.ts">getUserJobs</a>() -> CatchAllApi.ListUserJobsResponseDto[]</code></summary>
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
    job_id: "af7a26d6-cf0b-458c-a6ed-4b6318c74da3"
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

Create a monitor that runs jobs based on a reference job with a specified schedule.

**Schedule requirements:**
- Minimum 24-hour interval between executions
- Natural language format (e.g., "every day at 12 PM UTC", "every 48 hours")

**Validation:**
- Schedules below minimum frequency return error with descriptive message.
- Invalid job IDs return 400 Bad Request.
- Duplicate monitors (same job already monitored) return error.
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
    reference_job_id: "reference_job_id",
    schedule: "every day at 12 PM UTC"
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

Update webhook configuration for an existing monitor without recreating it.

**Supported updates:**
- Webhook URL
- HTTP method (POST/PUT)
- Headers and authentication
- Query parameters

**Note:** Schedule and reference job cannot be modified. To change these, create a new monitor.
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

Returns all jobs associated with a monitor, sorted by start_date.
Each job includes job_id, start_date, and end_date.
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

Retrieve aggregated results from all jobs executed by this monitor.
Includes monitor configuration, execution history, and all records collected.
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

Disables a monitor to stop executing scheduled jobs.
Validates that the provided API key is associated with the monitor.
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

Enables a monitor to resume executing scheduled jobs.
Validates that the provided API key is associated with the monitor.
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

**request:** `CatchAllApi.EnableMonitorRequest` 
    
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

<details><summary><code>client.monitors.<a href="/src/api/resources/monitors/client/Client.ts">listMonitors</a>() -> CatchAllApi.ListMonitorsResponseDto</code></summary>
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
