# WriteResult

## Example Usage

```typescript
import { WriteResult } from "@amp-labs/sdk-node-write/models/errors";

let value: WriteResult = {
  success: true,
  data: {},
  recordId: "003Dp0X#@RG7IAP",
};
```

## Fields

| Field                                      | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `success`                                  | *boolean*                                  | :heavy_check_mark:                         | Whether the operation was successful       | true                                       |
| `data`                                     | [errors.Data](../../models/errors/data.md) | :heavy_minus_sign:                         | The data returned by the operation         | {<br/>"email": "david@ampersand.com"<br/>} |
| `recordId`                                 | *string*                                   | :heavy_minus_sign:                         | The ID of the object                       | 003Dp0X#@RG7IAP                            |