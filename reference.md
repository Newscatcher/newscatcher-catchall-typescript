# Reference
## Jobs
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

## Monitors
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

## Entities
<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">listEntities</a>({ ...params }) -> CatchAllApi.EntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities belonging to the authenticated
organization. Supports filtering by status and entity type, and
sorting by name, status, or creation date.
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
await client.entities.listEntities({
    search: "NewsCatcher"
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

**request:** `CatchAllApi.ListEntitiesRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">createEntity</a>({ ...params }) -> CatchAllApi.CreateEntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new company entity and begins background enrichment.

The entity status starts as `pending` and transitions to `ready` once
enrichment completes. Provide as much identifying information as
possible — `domain` is the highest-signal field because it is
unambiguous.
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
await client.entities.createEntity({
    name: "NewsCatcher",
    entity_type: "company",
    description: "AI-powered news data provider",
    additional_attributes: {
        company_attributes: {
            domain: "newscatcherapi.com",
            key_persons: ["Artem Bugara", "Maksym Sugonyaka"],
            alternative_names: ["NC", "NewsCatcher API"]
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

**request:** `CatchAllApi.CreateEntityRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">createEntitiesBatch</a>({ ...params }) -> CatchAllApi.CreateEntitiesBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates multiple entities in a single request. Each entity is
processed independently — a failure in one does not affect others.

Returns an array of `{id, status}` objects in the same order as
the input array.
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
await client.entities.createEntitiesBatch({
    entities: [{
            name: "OpenAI",
            entity_type: "company",
            description: "Artificial intelligence research company",
            additional_attributes: {
                company_attributes: {
                    domain: "openai.com",
                    key_persons: ["Sam Altman"],
                    alternative_names: ["Open AI"]
                }
            }
        }, {
            name: "Stripe",
            entity_type: "company",
            description: "Online payment processing platform",
            additional_attributes: {
                company_attributes: {
                    domain: "stripe.com",
                    key_persons: ["Patrick Collison", "John Collison"]
                }
            }
        }]
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

**request:** `CatchAllApi.CreateEntitiesBatchRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">getEntity</a>({ ...params }) -> CatchAllApi.EntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single entity by ID with all attributes and current status.
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
await client.entities.getEntity({
    entity_id: "854198fa-f702-49db-a381-0427fa87f173"
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

**request:** `CatchAllApi.GetEntityRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">deleteEntity</a>({ ...params }) -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes an entity. The entity is removed from all
datasets and the search index. This operation cannot be undone.
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
await client.entities.deleteEntity({
    entity_id: "854198fa-f702-49db-a381-0427fa87f173"
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

**request:** `CatchAllApi.DeleteEntityRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="/src/api/resources/entities/client/Client.ts">updateEntity</a>({ ...params }) -> CatchAllApi.EntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates one or more fields of an existing entity.
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
await client.entities.updateEntity({
    entity_id: "854198fa-f702-49db-a381-0427fa87f173",
    description: "Updated description",
    additional_attributes: {
        company_attributes: {
            alternative_names: ["NC", "NewsCatcher API", "NCA"]
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

**request:** `CatchAllApi.UpdateEntityRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `EntitiesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Datasets
<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">listDatasets</a>({ ...params }) -> CatchAllApi.DatasetListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of datasets belonging to the authenticated
organization. Supports filtering by status and sorting by name,
status, or creation date.
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
await client.datasets.listDatasets({
    search: "Portfolio"
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

**request:** `CatchAllApi.ListDatasetsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">createDataset</a>({ ...params }) -> CatchAllApi.DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new dataset from a list of existing entity IDs.

If any of the provided entity IDs do not exist or do not belong to
your organization, the request fails with `400`. All entity IDs must
be valid before the dataset is created.

To create a dataset and entities in one step, use the [`Create dataset from CSV`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/datasets/create-dataset-from-csv)
endpoint instead.
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
await client.datasets.createDataset({
    name: "My Portfolio",
    description: "Companies in our investment portfolio",
    entity_ids: ["854198fa-f702-49db-a381-0427fa87f173", "a1b2c3d4-e5f6-7890-abcd-ef1234567890"]
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

**request:** `CatchAllApi.CreateDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">createDatasetFromCsv</a>({ ...params }) -> CatchAllApi.CreateDatasetCsvResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new dataset by uploading a CSV file. Each row in the CSV
becomes an entity. The `name` column is required; all other columns
are optional.

**CSV format:**
```csv
name,description,domain,alternative_names,key_persons
NewsCatcher,"AI-powered news data provider",newscatcherapi.com,"NC;NewsCatcher API","Artem Bugara;Maksym Sugonyaka"
OpenAI,"Artificial intelligence research company",openai.com,"Open AI","Sam Altman"
```

Use semicolons (`;`) to separate multiple values in `alternative_names` and `key_persons`. Rows with empty `name` are skipped and reported in `validation_report`. 

**Note**: The response shape differs from the JSON dataset creation endpoint: it returns `dataset_id` (not `id`) and includes a `validation_report` with details on skipped rows.
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
await client.datasets.createDatasetFromCsv({
    file: fs.createReadStream("/path/to/your/file"),
    name: "name"
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

**request:** `CatchAllApi.CreateDatasetFromCsvRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">getDataset</a>({ ...params }) -> CatchAllApi.DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single dataset by ID including entity count and current status.
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
await client.datasets.getDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2"
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

**request:** `CatchAllApi.GetDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">deleteDataset</a>({ ...params }) -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a dataset. The entities within the dataset are
not deleted — only the dataset itself. This operation cannot be
undone.
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
await client.datasets.deleteDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2"
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

**request:** `CatchAllApi.DeleteDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">updateDataset</a>({ ...params }) -> CatchAllApi.DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates the name or description of a dataset.
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
await client.datasets.updateDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2",
    name: "My Portfolio (updated)",
    description: "Updated Q1 2026 watchlist"
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

**request:** `CatchAllApi.UpdateDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">listEntitiesInDataset</a>({ ...params }) -> CatchAllApi.DatasetEntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities in a dataset. Supports filtering by status and entity type.
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
await client.datasets.listEntitiesInDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2"
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

**request:** `CatchAllApi.ListEntitiesInDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">addEntitiesToDataset</a>({ ...params }) -> CatchAllApi.ManageEntitiesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Adds one or more existing entities to a dataset. Returns the number of entities added.
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
await client.datasets.addEntitiesToDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2",
    body: {
        entity_ids: ["854198fa-f702-49db-a381-0427fa87f173"]
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

**request:** `CatchAllApi.AddEntitiesToDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">removeEntitiesFromDataset</a>({ ...params }) -> CatchAllApi.ManageEntitiesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Removes one or more entities from a dataset. The entities themselves
are not deleted — they are only removed from this dataset. Returns
the number of entities removed.
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
await client.datasets.removeEntitiesFromDataset({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2",
    body: {
        entity_ids: ["854198fa-f702-49db-a381-0427fa87f173"]
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

**request:** `CatchAllApi.RemoveEntitiesFromDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">getDatasetStatusHistory</a>({ ...params }) -> CatchAllApi.DatasetStatusHistoryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full status change history for a dataset, ordered
chronologically from oldest to newest.
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
await client.datasets.getDatasetStatusHistory({
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2"
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

**request:** `CatchAllApi.GetDatasetStatusHistoryRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="/src/api/resources/datasets/client/Client.ts">uploadCsvToDataset</a>({ ...params }) -> CatchAllApi.UploadCsvToDatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Appends new companies to an existing dataset by uploading a CSV file.
Uses the same CSV format as the dataset creation endpoint.

The response omits `dataset_name` compared to the create-from-CSV
endpoint since the dataset already exists.
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
await client.datasets.uploadCsvToDataset({
    file: fs.createReadStream("/path/to/your/file"),
    dataset_id: "ccabb755-afc2-4047-b84c-78d1f23d49b2"
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

**request:** `CatchAllApi.UploadCsvToDatasetRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DatasetsClient.RequestOptions` 
    
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

