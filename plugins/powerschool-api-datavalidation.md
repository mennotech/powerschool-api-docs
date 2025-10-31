
# PowerSchool DATAVALIDATION API

## datavalidation

### POST /ws/datavalidation/rules

Get list of data validation rules

| Property | Value |
|----------|-------|
| Available Since | 8.0.0 |
| Accessible To | ADMIN,GUARDIAN,STUDENT,TEACHERS,SUBS,PLUGINS |

#### Description

Get list of data validation rules, filtered by the criteria in the list parameter

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | List of filter criteria |

**Model Description:**

```
ValidationKey {
  recordid (integer, optional): Optional argument to indicate a record number (DCID) for context based data validation rules
}
```

**Model Schema:**

```json
{
  "ldvkey": "string",
  "recordid": 0
}
```


#### Response Class (Status 200)

```
ValidationAttribute {
  key (string, optional): Data validation key
  rule (string, optional): Data validation attribute
}
```

**Response Schema:**

```json
{
  "key": "string",
  "rule": "string"
}
```
