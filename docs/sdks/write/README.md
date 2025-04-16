# Write
(*write*)

## Overview

### Available Operations

* [records](#records) - Write records

## records

Write records

### Example Usage

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
      record: {
        "email": "david@withampersand.com",
        "warmthScore": "ready-for-close",
      },
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

### Standalone function

The standalone function version of this method:

```typescript
import { SDKNodeWriteCore } from "@amp-labs/sdk-node-write/core.js";
import { writeRecords } from "@amp-labs/sdk-node-write/funcs/writeRecords.js";

// Use `SDKNodeWriteCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const sdkNodeWrite = new SDKNodeWriteCore({
  apiKeyHeader: process.env["SDKNODEWRITE_API_KEY_HEADER"] ?? "",
});

async function run() {
  const res = await writeRecords(sdkNodeWrite, {
    projectIdOrName: "<value>",
    integrationId: "<id>",
    objectName: "<value>",
    requestBody: {
      groupRef: "<value>",
      type: "create",
      mode: "synchronous",
      record: {
        "email": "david@withampersand.com",
        "warmthScore": "ready-for-close",
      },
      associations: [
        {},
      ],
    },
  });

  if (!res.ok) {
    throw res.error;
  }

  const { value: result } = res;

  // Handle the result
  console.log(result);
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.WriteRecordsRequest](../../models/operations/writerecordsrequest.md)                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.WriteRecordsResponse](../../models/operations/writerecordsresponse.md)\>**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.WriteRecordsSyncWriteResponseFailure | 422                                         | application/json                            |
| errors.APIError                             | 4XX, 5XX                                    | \*/\*                                       |