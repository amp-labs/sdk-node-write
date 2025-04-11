# WriteRecordsSyncWriteResponseSuccess

The success response

## Example Usage

```typescript
import { WriteRecordsSyncWriteResponseSuccess } from "@amp-labs/sdk-node-write/models/operations";

let value: WriteRecordsSyncWriteResponseSuccess = {
  result: {
    success: true,
    data: {},
    recordId: "003Dp0X#@RG7IAP",
  },
  operationId: "acb0d75a-1b59-4aad-a191-48c5b75ea9e4",
};
```

## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      | Example                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `result`                                                         | [operations.WriteResult](../../models/operations/writeresult.md) | :heavy_check_mark:                                               | N/A                                                              |                                                                  |
| `operationId`                                                    | *string*                                                         | :heavy_check_mark:                                               | The operation ID                                                 | acb0d75a-1b59-4aad-a191-48c5b75ea9e4                             |