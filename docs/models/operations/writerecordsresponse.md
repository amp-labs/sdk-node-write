# WriteRecordsResponse


## Supported Types

### `operations.WriteRecordsSyncWriteResponseSuccess`

```typescript
const value: operations.WriteRecordsSyncWriteResponseSuccess = {
  result: {
    success: true,
    data: {},
    recordId: "003Dp0X#@RG7IAP",
  },
  operationId: "acb0d75a-1b59-4aad-a191-48c5b75ea9e4",
};
```

### `operations.WriteRecordsAPIProblem`

```typescript
const value: operations.WriteRecordsAPIProblem = {
  type: "urn:problem-type:exampleOrganization:exampleProblem",
  href:
    "https://www.belgif.be/specification/rest/api-guide/#standardized-problem-types",
  title: "Description of the type of problem that occurred",
  status: 400,
  detail: "Description of specific occurrence of the problem",
  instance: "urn:uuid:123e4567-e89b-12d3-a456-426614174000",
};
```

