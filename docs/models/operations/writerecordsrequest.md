# WriteRecordsRequest

## Example Usage

```typescript
import { WriteRecordsRequest } from "@amp-labs/sdk-node-write/models/operations";

let value: WriteRecordsRequest = {
  projectIdOrName: "<value>",
  integrationId: "<id>",
  objectName: "<value>",
  requestBody: {
    groupRef: "<value>",
    type: "create",
    mode: "synchronous",
    record: {},
    associations: [
      {},
    ],
  },
};
```

## Fields

| Field                                                                                      | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `projectIdOrName`                                                                          | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `integrationId`                                                                            | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `objectName`                                                                               | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `requestBody`                                                                              | [operations.WriteRecordsWriteRequest](../../models/operations/writerecordswriterequest.md) | :heavy_check_mark:                                                                         | Write request                                                                              |