# Newscatcher CatchAll TypeScript Library

[![fern shield](https://img.shields.io/badge/%F0%9F%8C%BF-Built%20with%20Fern-brightgreen)](https://buildwithfern.com?utm_source=github&utm_medium=github&utm_campaign=readme&utm_source=https%3A%2F%2Fgithub.com%2FNewscatcher%2Fnewscatcher-catchall-typescript)
[![npm shield](https://img.shields.io/npm/v/newscatcher-catchall-sdk)](https://www.npmjs.com/package/newscatcher-catchall-sdk)

The Newscatcher CatchAll TypeScript library provides access to the [CatchAll API](https://www.newscatcherapi.com/docs/v3/catch-all/overview/introduction), which transforms natural language queries into structured data extracted from web sources.

## Installation

```sh
npm install newscatcher-catchall-sdk
```

## Reference

A full reference for this library is available [here](./reference.md).

## Usage

### Jobs

Submit a query and retrieve structured results:

```typescript
import { CatchAllApiClient } from "newscatcher-catchall-sdk";

const client = new CatchAllApiClient({ apiKey: "YOUR_API_KEY" });

// Create a job with optional limit for testing
const job = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
    context: "Focus on revenue and profit margins",
    limit: 10, // Start with 10 records for quick testing
});
console.log(`Job created: ${job.job_id}`);

// Poll for completion with progress updates
while (true) {
    const status = await client.jobs.getJobStatus({ job_id: job.job_id });

    // Check if completed or enriching (early access)
    const currentStatus = status.status;
    if (currentStatus === "completed" || currentStatus === "enriching") {
        console.log(`Job ${currentStatus}!`);
        break;
    }

    // Show current processing step
    const currentStep = status.steps.find(s => !s.completed);
    if (currentStep) {
        console.log(`Processing: ${currentStep.status} (step ${currentStep.order}/7)`);
    }

    await new Promise(resolve => setTimeout(resolve, 60000)); // Wait 60 seconds
}

// Retrieve initial results (available during enriching stage)
const results = await client.jobs.getJobResults({ job_id: job.job_id });
console.log(`Found ${results.valid_records} valid records`);
console.log(`Progress: ${results.progress_validated}/${results.candidate_records} validated`);

// Continue job to process more records
if (results.valid_records >= 10) {
    const continued = await client.jobs.continueJob({
        job_id: job.job_id,
        new_limit: 50, // Increase to 50 records
    });
    console.log(`Job continued: ${continued.job_id}`);
    
    // Wait for completion
    while (true) {
        const status = await client.jobs.getJobStatus({ job_id: job.job_id });
        if (status.status === "completed") {
            break;
        }
        await new Promise(resolve => setTimeout(resolve, 60000));
    }
    
    // Get final results
    const finalResults = await client.jobs.getJobResults({ job_id: job.job_id });
    console.log(`Final: ${finalResults.valid_records} records`);
}
```

Jobs process asynchronously and typically complete in 10-15 minutes. To learn more, see the [Quickstart](https://www.newscatcherapi.com/docs/v3/catch-all/overview/quickstart).

### Monitors

Automate recurring queries with scheduled execution:

```typescript
import { CatchAllApiClient } from "newscatcher-catchall-sdk";

const client = new CatchAllApiClient({ apiKey: "YOUR_API_KEY" });

// Create a monitor from a completed job
const monitor = await client.monitors.createMonitor({
    reference_job_id: job.job_id,
    schedule: "every day at 12 PM UTC",
    webhook: {
        url: "https://your-endpoint.com/webhook",
        method: "POST",
        headers: { "Authorization": "Bearer YOUR_TOKEN" },
    },
});
console.log(`Monitor created: ${monitor.monitor_id}`);

// Update webhook configuration without recreating monitor
const updated = await client.monitors.updateMonitor({
    monitor_id: monitor.monitor_id,
    webhook: {
        url: "https://new-endpoint.com/webhook",
        method: "POST",
        headers: { "Authorization": "Bearer NEW_TOKEN" },
    },
});

// Pause monitor execution
await client.monitors.disableMonitor({ monitor_id: monitor.monitor_id });
console.log("Monitor paused");

// Resume monitor execution
await client.monitors.enableMonitor({ monitor_id: monitor.monitor_id });
console.log("Monitor resumed");

// List monitor execution history
const jobs = await client.monitors.listMonitorJobs({
    monitor_id: monitor.monitor_id,
    sort: "desc", // Most recent first
});
console.log(`Monitor has executed ${jobs.total_jobs} jobs`);
for (const job of jobs.jobs) {
    console.log(`  Job ${job.job_id}: ${job.start_date} to ${job.end_date}`);
}

// Get aggregated results
const results = await client.monitors.pullMonitorResults({ monitor_id: monitor.monitor_id });
console.log(`Collected ${results.records} records across all executions`);
```

Monitors run jobs on your schedule and send webhook notifications when complete. See the [Monitors documentation](https://www.newscatcherapi.com/docs/v3/catch-all/overview/monitors) for setup and configuration.

## Request and response types

The SDK exports all request and response types as TypeScript interfaces:

```typescript
import { CatchAllApi } from "newscatcher-catchall-sdk";

const request: CatchAllApi.SubmitRequestDto = {
    query: "Tech company earnings this quarter",
    context: "Focus on revenue and profit margins",
};
```

## Exception handling

Handle API errors with the `CatchAllApiError` exception:

```typescript
import { CatchAllApiError } from "newscatcher-catchall-sdk";

try {
    await client.jobs.createJob({
        query: "Tech company earnings this quarter",
    });
} catch (err) {
    if (err instanceof CatchAllApiError) {
        console.log(`Status: ${err.statusCode}`);
        console.log(`Message: ${err.message}`);
        console.log(`Body: ${JSON.stringify(err.body)}`);
    }
}
```

## Advanced

### Pagination

Retrieve large result sets with pagination:

```typescript
// Retrieve large result sets with pagination
let page = 1;
while (true) {
    const results = await client.jobs.getJobResults({
        job_id: jobId,
        page: page,
        page_size: 100,
    });
    
    console.log(`Page ${results.page}/${results.total_pages}: ${results.all_records.length} records`);
    
    for (const record of results.all_records) {
        // Process each record
        console.log(`  - ${record.record_title}`);
    }
    
    if (results.page >= results.total_pages) {
        break;
    }
    page++;
}

console.log(`Processed ${results.valid_records} total records`);
```

### Access raw response data

Access response headers and raw data:

```typescript
const { data, rawResponse } = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
}).withRawResponse();

console.log(data);
console.log(rawResponse.headers.get('X-Custom-Header'));
```

### Additional headers

Send custom headers with your request:

```typescript
const response = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
}, {
    headers: {
        'X-Custom-Header': 'custom value'
    }
});
```

### Retries

The SDK retries failed requests automatically with exponential backoff. Configure retry behavior:

```typescript
const response = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
}, {
    maxRetries: 3, // override maxRetries at the request level (default: 2)
});
```

A request is retried when any of these HTTP status codes is returned:

- [408](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/408) (Timeout)
- [429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) (Too Many Requests)
- [5XX](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/500) (Internal Server Errors)

### Timeouts

Set custom timeouts at the request level:

```typescript
const response = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
}, {
    timeoutInSeconds: 30, // override timeout to 30s (default: 60s)
});
```

### Aborting requests

Cancel requests using an abort signal:

```typescript
const controller = new AbortController();
const response = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
}, {
    abortSignal: controller.signal
});
controller.abort(); // cancels the request
```

### Logging

Configure logging to debug SDK behavior:

```typescript
import { CatchAllApiClient, logging } from "newscatcher-catchall-sdk";

const client = new CatchAllApiClient({
    apiKey: "YOUR_API_KEY",
    logging: {
        level: logging.LogLevel.Debug, // defaults to logging.LogLevel.Info
        logger: new logging.ConsoleLogger(), // defaults to ConsoleLogger
        silent: false, // defaults to true, set to false to enable logging
    }
});
```

Available log levels:

- `logging.LogLevel.Debug`
- `logging.LogLevel.Info`
- `logging.LogLevel.Warn`
- `logging.LogLevel.Error`

<details>
<summary>Custom logger examples</summary>

Using Winston:

```typescript
import winston from 'winston';

const winstonLogger = winston.createLogger({...});

const logger: logging.ILogger = {
    debug: (msg, ...args) => winstonLogger.debug(msg, ...args),
    info: (msg, ...args) => winstonLogger.info(msg, ...args),
    warn: (msg, ...args) => winstonLogger.warn(msg, ...args),
    error: (msg, ...args) => winstonLogger.error(msg, ...args),
};
```

Using Pino:

```typescript
import pino from 'pino';

const pinoLogger = pino({...});

const logger: logging.ILogger = {
    debug: (msg, ...args) => pinoLogger.debug(args, msg),
    info: (msg, ...args) => pinoLogger.info(args, msg),
    warn: (msg, ...args) => pinoLogger.warn(args, msg),
    error: (msg, ...args) => pinoLogger.error(args, msg),
};
```

</details>

### Runtime compatibility

The SDK works in the following runtimes:

- Node.js 18+
- Vercel
- Cloudflare Workers
- Deno v1.25+
- Bun 1.0+
- React Native

### Custom fetch client

Customize the underlying HTTP client for unsupported environments:

```typescript
import { CatchAllApiClient } from "newscatcher-catchall-sdk";

const client = new CatchAllApiClient({
    apiKey: "YOUR_API_KEY",
    fetcher: // provide your implementation here
});
```

## Beta status

CatchAll API is in beta. Breaking changes may occur in minor version updates. See the [Changelog](https://www.newscatcherapi.com/docs/v3/catch-all/overview/changelog) for updates.

## Contributing

This library is generated programmatically from our API specification. Direct contributions to the generated code cannot be merged, but README improvements are welcome. To suggest SDK changes, please [open an issue](https://github.com/Newscatcher/newscatcher-catchall-typescript/issues).

## Support

- Documentation: [https://www.newscatcherapi.com/docs/v3/catch-all](https://www.newscatcherapi.com/docs/v3/catch-all)
- Support: <support@newscatcherapi.com>
