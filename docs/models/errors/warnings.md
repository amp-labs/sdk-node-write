# Warnings

## Example Usage

```typescript
import { Warnings } from "@amp-labs/sdk-node-write/models/errors";

let value: Warnings = {
  message: "The record with ID 003Dp0X#@RG7IAP was not found",
};
```

## Fields

| Field                                                                                     | Type                                                                                      | Required                                                                                  | Description                                                                               | Example                                                                                   |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `message`                                                                                 | *string*                                                                                  | :heavy_minus_sign:                                                                        | errors messages when some unexpected event happened, but write to provider was successful | The record with ID 003Dp0X#@RG7IAP was not found                                          |