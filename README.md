# Ampersand write SDK

<br/>
<div align="center">
    <a href="https://www.withampersand.com/?utm_source=github&utm_medium=readme&utm_campaign=connectors-repo&utm_content=logo">
    <img src="https://res.cloudinary.com/dycvts6vp/image/upload/v1723671980/ampersand-logo-black.svg" height="30" align="center" alt="Ampersand logo" >
    </a>
<br/>
<br/>

<div align="center">

[![Star us on GitHub](https://img.shields.io/github/stars/amp-labs/connectors?color=FFD700&label=Stars&logo=Github)](https://github.com/amp-labs/connectors) [![Discord](https://img.shields.io/badge/Join%20The%20Community-black?logo=discord)](https://discord.gg/BWP4BpKHvf) [![Documentation](https://img.shields.io/badge/Read%20our%20Documentation-black?logo=book)](https://docs.withampersand.com) ![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg) <img src="https://img.shields.io/static/v1?label=license&message=MIT&color=white" alt="License">
</div>

</div>

# Overview

[Ampersand](https://withampersand.com?trk=readme-github) is a declarative platform for SaaS builders who are creating product integrations. It allows you to:

* Read data from your customer’s SaaS
* Write data to your customer’s SaaS
* Subscribe to events (creates, deletes, and field changes) in your customer’s SaaS

<!-- Start SDK Installation [installation] -->
## SDK Installation

The SDK can be installed with either [npm](https://www.npmjs.com/), [pnpm](https://pnpm.io/), [bun](https://bun.sh/) or [yarn](https://classic.yarnpkg.com/en/) package managers.

### NPM

```bash
npm add @amp-labs/sdk-node-write
```

### PNPM

```bash
pnpm add @amp-labs/sdk-node-write
```

### Bun

```bash
bun add @amp-labs/sdk-node-write
```

### Yarn

```bash
yarn add @amp-labs/sdk-node-write zod

# Note that Yarn does not install peer dependencies automatically. You will need
# to install zod as shown above.
```



### Model Context Protocol (MCP) Server

This SDK is also an installable MCP server where the various SDK methods are
exposed as tools that can be invoked by AI applications.

> Node.js v20 or greater is required to run the MCP server from npm.

<details>
<summary>Claude installation steps</summary>

Add the following server definition to your `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "SDKNodeWrite": {
      "command": "npx",
      "args": [
        "-y", "--package", "@amp-labs/sdk-node-write",
        "--",
        "mcp", "start",
        "--api-key-header", "..."
      ]
    }
  }
}
```

</details>

<details>
<summary>Cursor installation steps</summary>

Create a `.cursor/mcp.json` file in your project root with the following content:

```json
{
  "mcpServers": {
    "SDKNodeWrite": {
      "command": "npx",
      "args": [
        "-y", "--package", "@amp-labs/sdk-node-write",
        "--",
        "mcp", "start",
        "--api-key-header", "..."
      ]
    }
  }
}
```

</details>

You can also run MCP servers as a standalone binary with no additional dependencies. You must pull these binaries from available Github releases:

```bash
curl -L -o mcp-server \
    https://github.com/{org}/{repo}/releases/download/{tag}/mcp-server-bun-darwin-arm64 && \
chmod +x mcp-server
```

If the repo is a private repo you must add your Github PAT to download a release `-H "Authorization: Bearer {GITHUB_PAT}"`.


```json
{
  "mcpServers": {
    "Todos": {
      "command": "./DOWNLOAD/PATH/mcp-server",
      "args": [
        "start"
      ]
    }
  }
}
```

For a full list of server arguments, run:

```sh
npx -y --package @amp-labs/sdk-node-write -- mcp start --help
```
<!-- End SDK Installation [installation] -->

<!-- Start Requirements [requirements] -->
## Requirements

For supported JavaScript runtimes, please consult [RUNTIMES.md](RUNTIMES.md).
<!-- End Requirements [requirements] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdkNodeWrite = new SDKNodeWrite({
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const result = await sdkNodeWrite.write.records({
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      associations: [
        {},
      ],
    },
  });

  // Handle the result
  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name           | Type   | Scheme  | Environment Variable          |
| -------------- | ------ | ------- | ----------------------------- |
| `apiKeyHeader` | apiKey | API key | `SDKNODEWRITE_API_KEY_HEADER` |

To authenticate with the API the `apiKeyHeader` parameter must be set when initializing the SDK client instance. For example:
```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdkNodeWrite = new SDKNodeWrite({
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const result = await sdkNodeWrite.write.records({
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      associations: [
        {},
      ],
    },
  });

  // Handle the result
  console.log(result);
}

run();

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>


### [write](docs/sdks/write/README.md)

* [records](docs/sdks/write/README.md#records) - Write records

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Standalone functions [standalone-funcs] -->
## Standalone functions

All the methods listed above are available as standalone functions. These
functions are ideal for use in applications running in the browser, serverless
runtimes or other environments where application bundle size is a primary
concern. When using a bundler to build your application, all unused
functionality will be either excluded from the final bundle or tree-shaken away.

To read more about standalone functions, check [FUNCTIONS.md](./FUNCTIONS.md).

<details>

<summary>Available standalone functions</summary>

- [`writeRecords`](docs/sdks/write/README.md#records) - Write records

</details>
<!-- End Standalone functions [standalone-funcs] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries.  If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API.  However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a retryConfig object to the call:
```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdkNodeWrite = new SDKNodeWrite({
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const result = await sdkNodeWrite.write.records({
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      associations: [
        {},
      ],
    },
  }, {
    retries: {
      strategy: "backoff",
      backoff: {
        initialInterval: 1,
        maxInterval: 50,
        exponent: 1.1,
        maxElapsedTime: 100,
      },
      retryConnectionErrors: false,
    },
  });

  // Handle the result
  console.log(result);
}

run();

```

If you'd like to override the default retry strategy for all operations that support retries, you can provide a retryConfig at SDK initialization:
```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdkNodeWrite = new SDKNodeWrite({
  retryConfig: {
    strategy: "backoff",
    backoff: {
      initialInterval: 1,
      maxInterval: 50,
      exponent: 1.1,
      maxElapsedTime: 100,
    },
    retryConnectionErrors: false,
  },
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const result = await sdkNodeWrite.write.records({
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      associations: [
        {},
      ],
    },
  });

  // Handle the result
  console.log(result);
}

run();

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Some methods specify known errors which can be thrown. All the known errors are enumerated in the `models/errors/errors.ts` module. The known errors for a method are documented under the *Errors* tables in SDK docs. For example, the `records` method may throw the following errors:

| Error Type                                  | Status Code | Content Type     |
| ------------------------------------------- | ----------- | ---------------- |
| errors.WriteRecordsSyncWriteResponseFailure | 422         | application/json |
| errors.APIError                             | 4XX, 5XX    | \*/\*            |

If the method throws an error and it is not captured by the known errors, it will default to throwing a `APIError`.

```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";
import {
  SDKValidationError,
  WriteRecordsSyncWriteResponseFailure,
} from "@amp-labs/sdk-node-write/models/errors";

const sdkNodeWrite = new SDKNodeWrite({
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  let result;
  try {
    result = await sdkNodeWrite.write.records({
      projectIdOrName: "<value>",
      integrationId: "<id>",
      objectName: "<value>",
      requestBody: {
        groupRef: "<value>",
        type: "create",
        mode: "synchronous",
        associations: [
          {},
        ],
      },
    });

    // Handle the result
    console.log(result);
  } catch (err) {
    switch (true) {
      // The server response does not match the expected SDK schema
      case (err instanceof SDKValidationError): {
        // Pretty-print will provide a human-readable multi-line error message
        console.error(err.pretty());
        // Raw value may also be inspected
        console.error(err.rawValue);
        return;
      }
      case (err instanceof WriteRecordsSyncWriteResponseFailure): {
        // Handle err.data$: WriteRecordsSyncWriteResponseFailureData
        console.error(err);
        return;
      }
      default: {
        // Other errors such as network errors, see HTTPClientErrors for more details
        throw err;
      }
    }
  }
}

run();

```

Validation errors can also occur when either method arguments or data returned from the server do not match the expected format. The `SDKValidationError` that is thrown as a result will capture the raw value that failed validation in an attribute called `rawValue`. Additionally, a `pretty()` method is available on this error that can be used to log a nicely formatted multi-line string since validation errors can list many issues and the plain error string may be difficult read when debugging.

In some rare cases, the SDK can fail to get a response from the server or even make the request due to unexpected circumstances such as network conditions. These types of errors are captured in the `models/errors/httpclienterrors.ts` module:

| HTTP Client Error                                    | Description                                          |
| ---------------------------------------------------- | ---------------------------------------------------- |
| RequestAbortedError                                  | HTTP request was aborted by the client               |
| RequestTimeoutError                                  | HTTP request timed out due to an AbortSignal signal  |
| ConnectionError                                      | HTTP client was unable to make a request to a server |
| InvalidRequestError                                  | Any input used to create a request is invalid        |
| UnexpectedClientError                                | Unrecognised or unexpected error                     |
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `serverURL: string` optional parameter when initializing the SDK client instance. For example:
```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdkNodeWrite = new SDKNodeWrite({
  serverURL: "https://write.withampersand.com/v1",
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const result = await sdkNodeWrite.write.records({
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      associations: [
        {},
      ],
    },
  });

  // Handle the result
  console.log(result);
}

run();

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The TypeScript SDK makes API calls using an `HTTPClient` that wraps the native
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). This
client is a thin wrapper around `fetch` and provides the ability to attach hooks
around the request lifecycle that can be used to modify the request or handle
errors and response.

The `HTTPClient` constructor takes an optional `fetcher` argument that can be
used to integrate a third-party HTTP client or when writing tests to mock out
the HTTP client and feed in fixtures.

The following example shows how to use the `"beforeRequest"` hook to to add a
custom header and a timeout to requests and how to use the `"requestError"` hook
to log errors:

```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";
import { HTTPClient } from "@amp-labs/sdk-node-write/lib/http";

const httpClient = new HTTPClient({
  // fetcher takes a function that has the same signature as native `fetch`.
  fetcher: (request) => {
    return fetch(request);
  }
});

httpClient.addHook("beforeRequest", (request) => {
  const nextRequest = new Request(request, {
    signal: request.signal || AbortSignal.timeout(5000)
  });

  nextRequest.headers.set("x-custom-header", "custom value");

  return nextRequest;
});

httpClient.addHook("requestError", (error, request) => {
  console.group("Request Error");
  console.log("Reason:", `${error}`);
  console.log("Endpoint:", `${request.method} ${request.url}`);
  console.groupEnd();
});

const sdk = new SDKNodeWrite({ httpClient });
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass a logger that matches `console`'s interface as an SDK option.

> [!WARNING]
> Beware that debug logging will reveal secrets, like API tokens in headers, in log messages printed to a console or files. It's recommended to use this feature only during local development and not in production.

```typescript
import { SDKNodeWrite } from "@amp-labs/sdk-node-write";

const sdk = new SDKNodeWrite({ debugLogger: console });
```

You can also enable a default debug logger by setting an environment variable `SDKNODEWRITE_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=sdk-node-write&utm_campaign=typescript)
