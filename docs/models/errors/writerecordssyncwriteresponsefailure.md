# WriteRecordsSyncWriteResponseFailure

Error encountered while creating records

## Example Usage

```typescript
import { WriteRecordsSyncWriteResponseFailure } from "sdk-node-write/models/errors";

// No examples available for this model
```

## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      | Example                                                                          |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `errors`                                                                         | [errors.Errors](../../models/errors/errors.md)[]                                 | :heavy_check_mark:                                                               | Error messages resulted in failures                                              |                                                                                  |
| `result`                                                                         | [errors.WriteResult](../../models/errors/writeresult.md)                         | :heavy_minus_sign:                                                               | N/A                                                                              |                                                                                  |
| `warnings`                                                                       | [errors.Warnings](../../models/errors/warnings.md)[]                             | :heavy_minus_sign:                                                               | Warnings messages when some unexpected event happened, but not blocking failures |                                                                                  |
| `operationId`                                                                    | *string*                                                                         | :heavy_check_mark:                                                               | The operation ID                                                                 | acb0d75a-1b59-4aad-a191-48c5b75ea9e4                                             |