<!-- Start SDK Example Usage [usage] -->
```typescript
import { SDKNodeWrite } from "sdk-node-write";

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