
# PowerSchool DATAVERSION API

## dataversion

### GET /ws/dataversion/{applicationName}/{dataVersion}

Get IDs of changed records according to data version subscription.

| Property | Value |
|----------|-------|
| Available Since | 9.3 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns IDs of record changed for data version subscription tables

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| applicationName | string | path | Data version application name |
| dataVersion | integer | path | Records changed since data version value. The value must be greater than or equal to 0. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
data_version_response {
  dataversion (integer, optional): Data version for subsequent request.
  tables (Array[table_name], optional)
}
```

**Response Schema:**

```json
{
  "$dataversion": 0,
  "tables": [
    [
      {}
    ]
  ]
}
```
