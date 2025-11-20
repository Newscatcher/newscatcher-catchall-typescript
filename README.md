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

// Create a job
const job = await client.jobs.createJob({
    query: "Tech company earnings this quarter",
    context: "Focus on revenue and profit margins",
    schema: "Company [NAME] earned [REVENUE] in [QUARTER]",
});
console.log(`Job created: ${job.jobId}`);

// Poll for completion with progress updates
while (true) {
    const status = await client.jobs.getJobStatus(job.jobId);

    // Check if completed
    const completed = status.steps.some(s => s.status === "completed" && s.completed);
    if (completed) {
        console.log("Job completed!");
        break;
    }

    // Show current processing step
    const currentStep = status.steps.find(s => !s.completed);
    if (currentStep) {
        console.log(`Processing: ${currentStep.status} (step ${currentStep.order}/7)`);
    }

    await new Promise(resolve => setTimeout(resolve, 60000)); // Wait 60 seconds
}

// Retrieve results
const results = await client.jobs.getJobResults(job.jobId);
console.log(`Found ${results.validRecords} valid records from ${results.candidateRecords} candidates`);

for (const record of results.allRecords) {
    console.log(record.recordTitle);
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
    referenceJobId: job.jobId,
    schedule: "every day at 12 PM UTC",
    webhook: {
        url: "https://your-endpoint.com/webhook",
        method: "POST",
        headers: { "Authorization": "Bearer YOUR_TOKEN" },
    },
});
console.log(`Monitor created: ${monitor.monitorId}`);

// List all monitors
const monitors = await client.monitors.listMonitors();
console.log(`Total monitors: ${monitors.totalMonitors}`);

// Get aggregated results
const results = await client.monitors.pullMonitorResults(monitor.monitorId);
console.log(`Collected ${results.records} records`);
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
    const results = await client.jobs.getJobResults(
        jobId,
        {
            page: page,
            pageSize: 100,
        }
    );
    
    console.log(`Page ${results.page}/${results.totalPages}: ${results.allRecords.length} records`);
    
    for (const record of results.allRecords) {
        // Process each record
        console.log(`  - ${record.recordTitle}`);
    }
    
    if (results.page >= results.totalPages) {
        break;
    }
    page++;
}

console.log(`Processed ${results.validRecords} total records`);
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