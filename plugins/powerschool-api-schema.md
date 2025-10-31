
# PowerSchool SCHEMA API

## schema

### POST /ws/schema/table/storedgrades

Create a single historical grade

| Property | Value |
|----------|-------|
| Available Since | 12.0.1.0 |
| Accessible To | PLUGINS |

#### Description

Create a single historical grade

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert. Payload must include schoolid, schoolyear, storecode, studentid, coursename or section_number and course_number together, and either grade or percent. |

**Model Description:**

```
storedgrades_insertTableRecord {
  tables (storedgrades_insertSchemaRecord, optional)
}

storedgrades_insertSchemaRecord {
  storedgrades (storedgrades_insert, optional)
}

storedgrades_insert {
  schoolname (string, optional): Name of the school in which the historical grade applies
  schoolid (number, optional): The School_Number of the associated Schools record
  grade (string, optional): Letter grade the student has received
  schoolyear (number, optional): Year for which the historical grade applies
  storecode (string, optional): Code for the historical grade
  student (8th grade, 9th grade, etc.)
  course_number (string, optional): Course number of the course to which the course pertains
  course_name (string, optional): Name of the course to which the course pertains
  teacher_name (string, optional): Name of the teacher of the section
  gpa_points (number, optional): If the class counts in the GPA it figures how many points this is worth based on the points in the grade scale
  gpa_addedvalue (number, optional): Number to be added to GPA for this course
  percent (number, optional): The percentage grade earned at the time
  behavior (string, optional): The student's citezenship
  earnedcrhrs (number, optional): The amount of credit based on the grade in the gradescale
  potentialcrhrs (number, optional): The amount of credit based on the course
  gradereplacementpolicy_id (number, optional): ID of the grade replacement policy that corresponds to the course
  excludefromgradesuppression (boolean, optional): True if this grade is excluded from grade suppression calculation
  excludefromgpa (boolean, optional): True if this grade is excluded from GPA calculations
  excludefromclassrank (boolean, optional): True if this course grade should be excluded during class ranking
  excludefromhonorroll (boolean, optional): True if this course grade should be excluded during Honor Roll calculations
  excludefromtranscripts (boolean, optional): True if this course grade should be excluded from transcripts
  excludefromgraduation (boolean, optional): True if this course grade should be excluded from graduation calculation
  comment_value (string, optional): Teacher comment
  studentid (number, optional): ID of the student to which the grade applies
}
```

**Model Schema:**

```json
{
  "tables": {
    "storedgrades": {
      "schoolname": "string",
      "schoolid": 0,
      "grade": "string",
      "schoolyear": 0,
      "storecode": "string",
      "grade_level": 0,
      "course_number": "string",
      "course_name": "string",
      "teacher_name": "string",
      "gpa_points": 0,
      "gpa_addedvalue": 0,
      "percent": 0,
      "behavior": "string",
      "earnedcrhrs": 0,
      "potentialcrhrs": 0,
      "credit_type": "string",
      "gradereplacementpolicy_id": 0,
      "excludefromgradesuppression": true,
      "excludefromgpa": true,
      "excludefromclassrank": true,
      "excludefromhonorroll": true,
      "excludefromtranscripts": true,
      "excludefromgraduation": true,
      "comment_value": "string",
      "studentid": 0
    }
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Created | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |

### DELETE /ws/schema/table/storedgrades/{id}

Delete a single historical grade by ID

| Property | Value |
|----------|-------|
| Available Since | 12.0.1.0 |
| Accessible To | PLUGINS |

#### Description

Delete a single record in the STOREDGRADES table by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Historical identifier, STOREDGRADES.DCID |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | No Content | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Conflict | [Complex Model - See API Documentation] |
| 500 | Internal Server Error | [Complex Model - See API Documentation] |

### GET /ws/schema/table/storedgrades/{id}

Get a single historical grade record

| Property | Value |
|----------|-------|
| Available Since | 12.0.1.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns a single row from STOREDGRADES table

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Historical grade identifier, STOREDGRADES.DCID |
| projection | string | query | Comma-separated list of fields to be projected in results. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Historical specified by the URI not found | [Complex Model - See API Documentation] |

### PUT /ws/schema/table/storedgrades/{id}

Update a single special historical record

| Property | Value |
|----------|-------|
| Available Since | 12.0.1.0 |
| Accessible To | PLUGINS |

#### Description

Update a single record in the STOREDGRADES table

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Historical grade identifier, STOREDGRADES.DCID |
| body | Model | body | Data to update. |

**Model Description:**

```
storedgrades_updateTableRecord {
  tables (storedgrades_insertSchemaRecord, optional)
}

storedgrades_insertSchemaRecord {
  storedgrades (storedgrades_insert, optional)
}

storedgrades_insert {
  schoolname (string, optional): Name of the school in which the historical grade applies
  schoolid (number, optional): The School_Number of the associated Schools record
  grade (string, optional): Letter grade the student has received
  schoolyear (number, optional): Year for which the historical grade applies
  storecode (string, optional): Code for the historical grade
  student (8th grade, 9th grade, etc.)
  course_number (string, optional): Course number of the course to which the course pertains
  course_name (string, optional): Name of the course to which the course pertains
  teacher_name (string, optional): Name of the teacher of the section
  gpa_points (number, optional): If the class counts in the GPA it figures how many points this is worth based on the points in the grade scale
  gpa_addedvalue (number, optional): Number to be added to GPA for this course
  percent (number, optional): The percentage grade earned at the time
  behavior (string, optional): The student's citezenship
  earnedcrhrs (number, optional): The amount of credit based on the grade in the gradescale
  potentialcrhrs (number, optional): The amount of credit based on the course
  gradereplacementpolicy_id (number, optional): ID of the grade replacement policy that corresponds to the course
  excludefromgradesuppression (boolean, optional): True if this grade is excluded from grade suppression calculation
  excludefromgpa (boolean, optional): True if this grade is excluded from GPA calculations
  excludefromclassrank (boolean, optional): True if this course grade should be excluded during class ranking
  excludefromhonorroll (boolean, optional): True if this course grade should be excluded during Honor Roll calculations
  excludefromtranscripts (boolean, optional): True if this course grade should be excluded from transcripts
  excludefromgraduation (boolean, optional): True if this course grade should be excluded from graduation calculation
  comment_value (string, optional): Teacher comment
  studentid (number, optional): ID of the student to which the grade applies
}
```

**Model Schema:**

```json
{
  "tables": {
    "storedgrades": {
      "schoolname": "string",
      "schoolid": 0,
      "grade": "string",
      "schoolyear": 0,
      "storecode": "string",
      "grade_level": 0,
      "course_number": "string",
      "course_name": "string",
      "teacher_name": "string",
      "gpa_points": 0,
      "gpa_addedvalue": 0,
      "percent": 0,
      "behavior": "string",
      "earnedcrhrs": 0,
      "potentialcrhrs": 0,
      "credit_type": "string",
      "gradereplacementpolicy_id": 0,
      "excludefromgradesuppression": true,
      "excludefromgpa": true,
      "excludefromclassrank": true,
      "excludefromhonorroll": true,
      "excludefromtranscripts": true,
      "excludefromgraduation": true,
      "comment_value": "string",
      "studentid": 0
    }
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |

### POST /ws/schema/query/{queryname}

Execute a named query

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,GUARDIAN,STUDENT,TEACHERS,PLUGINS |

#### Description

Execute a named query, which is an Oracle prepared statement preprocessed by PS-HTML. Paging and extended schema extensions parameters are supported. Extended field data is not returned for the fields that do not have read access.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| queryname | string | path | Name of query to execute |
| body | Model | body | Arguments to apply passed in payload as JSON |

**Model Description:**

```
schema.nq.NamedQueryParams {}
```

**Model Schema:**

```json
{}
```

| extensions | string | query | Comma-separated list of schema extensions to return |
| page | string | query | Page number of results |
| pagesize | string | query | Number of results per page |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request: returned if some error with the query, such as invalid argument or invalid data type | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
SchemaRecordList {
  record (Array[schema.nq.SchemaRecord], optional): List of records returned
}

SchemaRecord {
  tables (string, optional): Set of tables returned
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource
}
```

**Response Schema:**

```json
{
  "name": "string",
  "message": "string",
  "record": [
    {
      "name": "string",
      "message": "string",
      "id": "string",
      "tables": "string",
      "_extension_data": "string",
      "@extensions": "string"
    }
  ]
}
```

### POST /ws/schema/query/{queryname}/count

Get row count from a named query

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,GUARDIAN,STUDENT,TEACHERS,PLUGINS |

#### Description

Execute a named query and return row count. Useful for building paging.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| queryname | string | path | Name of query to execute |
| body | Model | body | Arguments to apply passed in payload as JSON |

**Model Description:**

```
schema.nq.NamedQueryParams {}
```

**Model Schema:**

```json
{}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request: returned if some error with the query, such as invalid argument or invalid data type | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
RecordCount {
  count (integer, optional): The record count
}
```

**Response Schema:**

```json
{
  "count": 0
}
```

### GET /ws/schema/plugin/{id}/validate

Get plugin validation errors

| Property | Value |
|----------|-------|
| Available Since | 9.2.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get list of plugin validation errors.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | PluginDef table identifier |

#### Response Class (Status 200)

```
errors {
  results (Array[plugin.validation.errorItem], optional): List of validation error items.
  maxLevel (string, optional): Maximum error level
}

errorItem {
  level (string, optional): Error level
  file (string, optional): File associated with validation error
  code (string, optional): Message key associated with validation error message
  message (string, optional): Validation error message
  categoryShortName (string, optional): Short category name for plugin file that has errors
}
```

**Response Schema:**

```json
{
  "results": [
    {
      "level": "string",
      "file": "string",
      "code": "string",
      "message": "string",
      "categoryShortName": "string"
    }
  ],
  "maxLevel": "string"
}
```

### GET /ws/schema/area

Get functional areas

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get list of functional areas in the database. Each table may belong to zero or more functional areas.

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
FunctionalAreas {
  areas (Array[schema.area.FunctionalArea], optional): List of functional areas
}

FunctionalArea {
  name (string, optional): Functional area internal name
  userVisible (boolean, optional): true if table is user visible
  display (string, optional): Functional area display name
  comment (string, optional): Functional area comment
}
```

**Response Schema:**

```json
{
  "areas": [
    {
      "name": "string",
      "userVisible": true,
      "display": "string",
      "comment": "string",
      "subareas": [
        {}
      ]
    }
  ]
}
```

### GET /ws/schema/area/{area}/table

Get tables for functional area

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get list of all tables in a functional areas. Each table may belong to zero or more functional areas.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| area | string | path | Functional area |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Functional area was not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
TablesList {
  area (string, optional): Functional area name
  tables (Array[schema.area.Table], optional): Tables in functional area
}

Table {
  name (string, optional): Database table name
  comment (string, optional): Database table comment
  primaryKey (string, optional): Database column primary key for table
  userVisible (boolean, optional): True if table is user visible
}
```

**Response Schema:**

```json
{
  "area": "string",
  "tables": [
    {
      "name": "string",
      "comment": "string",
      "primaryKey": "string",
      "userVisible": true
    }
  ]
}
```

### GET /ws/schema/table

Get all tables in the database

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get list of all tables in the database

#### Response Class (Status 200)

```
TablesList {
  record (Array[schema.table.SchemaRecord], optional): List of records returned
}

SchemaRecord {
  tables (Array[schema.table.SchemaRecordTables], optional): Set of tables returned
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource
}

ExtensionData {
  empty (boolean, optional)
}
```

**Response Schema:**

```json
{
  "name": "string",
  "message": "string",
  "record": [
    {
      "name": "string",
      "message": "string",
      "id": "string",
      "tables": [
        {}
      ],
      "_extension_data": {
        "empty": true
      },
      "@extensions": "string"
    }
  ]
}
```

### GET /ws/schema/table/{tablename}

Query multiple rows from a table

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint performs a query on a table and returns paged results. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| q | string | query | Query for database tables using modified FIQL language |
| projection | string | query | comma-separated list of fields to be projected in results. An asterisk () or tablename. with an asterisk (tablename.) are acceptable parameters in addition to field names |
| page | string | query | Page number of results |
| pagesize | string | query | Number of results per page |
| students_to_include | string | query | Indicates whether to use current student selection. This parameter has no effect for public callers. |
| teachers_to_include | string | query | Indicates whether to use current teacher selection. This parameter has no effect for public callers. |
| sort | string | query | Column name to sort results by |
| sortdescending | string | query | Sort results descending |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database table specified by the URI not found | [Complex Model - See API Documentation] |

### POST /ws/schema/table/{tablename}

Insert a single row into a database table

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint inserts a single row into a table. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| body | Model | body | Data to insert |

**Model Description:**

```
SchemaRecord {
  tables (Array[schema.table.SchemaRecordTables], optional): Set of tables returned
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource
}

ExtensionData {
  empty (boolean, optional)
}
```

**Model Schema:**

```json
{
  "name": "string",
  "message": "string",
  "id": "string",
  "tables": [
    {}
  ],
  "_extension_data": {
    "empty": true
  },
  "@extensions": "string"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database table specified by the URI not found | [Complex Model - See API Documentation] |

### DELETE /ws/schema/table/{tablename}/{id}

Delete a single row from a database table

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Delete a single row from a database table. Only available to extension tables and a few core tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| id | integer | path | Unique database identifier |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | Success with no content returned | [Complex Model - See API Documentation] |
| 403 | Forbidden when the user lacks full access permissions to all fields in the table. The response body will include a list of all fields with the needed permission. | [Complex Model - See API Documentation] |
| 404 | Database row or table specified by the URI not found | [Complex Model - See API Documentation] |

### GET /ws/schema/table/{tablename}/{id}

Get a single row from a database table

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint returns a single row from a table. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| id | integer | path | Unique database identifier |
| projection | string | query | Comma-separated list of fields to be projected in results. An asterisk () or tablename. with an asterisk (tablename.) are acceptable parameters in addition to field names. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database row or table specified by the URI not found | [Complex Model - See API Documentation] |

### PUT /ws/schema/table/{tablename}/{id}

Update a single row into a database table

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint updates a single row into a table. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| id | integer | path |  |
| body | Model | body | Data to update |

**Model Description:**

```
SchemaRecord {
  tables (Array[schema.table.SchemaRecordTables], optional): Set of tables returned
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource
}

ExtensionData {
  empty (boolean, optional)
}
```

**Model Schema:**

```json
{
  "name": "string",
  "message": "string",
  "id": "string",
  "tables": [
    {}
  ],
  "_extension_data": {
    "empty": true
  },
  "@extensions": "string"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database table specified by the URI not found | [Complex Model - See API Documentation] |

### GET /ws/schema/table/{tablename}/count

Get row count from a table based on criteria

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint calculates a row count for a table based on given criteria and returns it. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| q | string | query | Query for database tables using modified FIQL language |
| students_to_include | string | query | Indicates whether to use current student selection. This parameter has no effect for public callers. |
| teachers_to_include | string | query | Indicates whether to use current teacher selection. This parameter has no effect for public callers. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database table specified by the URI not found | [Complex Model - See API Documentation] |

### POST /ws/schema/table/{tablename}/massupdatebycriteria

Update multiple rows in a table based on criteria

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Endpoint updates a column with a supplied value for records matching the given criteria. Currently, the tables are limited to extended schema tables, table extensions, child tables, and standalone tables.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| body | Model | body | Data to insert |

**Model Description:**

```
SchemaRecord {
  tables (Array[schema.table.SchemaRecordTables], optional): Set of tables returned
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource
}

ExtensionData {
  empty (boolean, optional)
}
```

**Model Schema:**

```json
{
  "name": "string",
  "message": "string",
  "id": "string",
  "tables": [
    {}
  ],
  "_extension_data": {
    "empty": true
  },
  "@extensions": "string"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Database table specified by the URI not found | [Complex Model - See API Documentation] |

### GET /ws/schema/table/{tablename}/metadata

Get table metadata

| Property | Value |
|----------|-------|
| Available Since | 8.1.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get metadata for a table

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| tablename | string | path | Table name in PowerSchool schema |
| expansions | string | query | Expansions: actions, attrs, backRels, fwdRels, userVisible |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient Permission | [Complex Model - See API Documentation] |
| 404 | Table was not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
TableInfo {
  name (string, optional): Database table name
  comment (string, optional): Database table comment
  primaryKey (string, optional): Database column that is table primary key
  queries (object, optional): List of named queries that involve this table
  collection (string, optional): What extended schema collection this table is referenced by
  columns (Array[schema.table.TableInfo.Column], optional): Database columns in this table
}
```

**Response Schema:**

```json
{
  "name": "string",
  "comment": "string",
  "primaryKey": "string",
  "queries": {},
  "schemaType": "string",
  "coreTable": "string",
  "collection": "string",
  "columns": [
    {}
  ]
}
```

### POST /ws/schema/table/spenrollments

Create a single special program enrollment

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Create a single special program enrollment

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert. Payload must include entry_date, studentid and programid. |

**Model Description:**

```
spenrollments_insertTableRecord {
  tables (spenrollments_insertSchemaRecord, optional)
}

spenrollments_insertSchemaRecord {
  spenrollments (spenrollments_insert, optional)
}

spenrollments_insert {
  programid (integer): Special program enrollment ID
  enter_date (string): Special program enrollments entry date
  exit_date (string, optional): Special program enrollments exit date
  code1 (string, optional): SEOP self-contained code
  code2 (string, optional): SEOP setting code
  exitcode (string, optional): Code/reason for exiting the special program
  schoolid (integer, optional): ID of the school the student enrolled into the special program
  studentid (integer): ID of the student who enrolled into the special program
  gradelevel (integer, optional): Grade level of the student who enrolled into the special program
  sp_comment (string, optional): Comment section
}
```

**Model Schema:**

```json
{
  "tables": {
    "spenrollments": {
      "programid": 0,
      "enter_date": "2025-10-29",
      "exit_date": "2025-10-29",
      "code1": "string",
      "code2": "string",
      "exitcode": "string",
      "schoolid": 0,
      "studentid": 0,
      "gradelevel": 0,
      "sp_comment": "string"
    }
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Created | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |

### DELETE /ws/schema/table/spenrollments/{id}

Delete a single special program enrollment by ID

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Delete a single record in the SPENROLLMENTS table by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Special program enrollment identifier, SPENROLLMENTS.DCID |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | No Content | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Conflict | [Complex Model - See API Documentation] |
| 500 | Internal Server Error | [Complex Model - See API Documentation] |

### GET /ws/schema/table/spenrollments/{id}

Get a single special program enrollment record

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns a single row from SPENROLLMENTS table

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Special program enrollment identifier, SPENROLLMENTS.DCID |
| projection | string | query | Comma-separated list of fields to be projected in results. An asterisk () or spenrollments. with an asterisk (spenrollments.) are acceptable parameters in addition to field names. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 404 | Special program enrollment specified by the URI not found | [Complex Model - See API Documentation] |

### PUT /ws/schema/table/spenrollments/{id}

Update a single special program enrollment record

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Update a single record in the SPENROLLMENTS table

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Special program enrollment identifier,SPENROLLMENTS.DCID |
| body | Model | body | Data to update. Payload must include entry_date, studentid and programid. |

**Model Description:**

```
spenrollments_updateTableRecord {
  tables (spenrollments_insertSchemaRecord, optional)
}

spenrollments_insertSchemaRecord {
  spenrollments (spenrollments_insert, optional)
}

spenrollments_insert {
  programid (integer): Special program enrollment ID
  enter_date (string): Special program enrollments entry date
  exit_date (string, optional): Special program enrollments exit date
  code1 (string, optional): SEOP self-contained code
  code2 (string, optional): SEOP setting code
  exitcode (string, optional): Code/reason for exiting the special program
  schoolid (integer, optional): ID of the school the student enrolled into the special program
  studentid (integer): ID of the student who enrolled into the special program
  gradelevel (integer, optional): Grade level of the student who enrolled into the special program
  sp_comment (string, optional): Comment section
}
```

**Model Schema:**

```json
{
  "tables": {
    "spenrollments": {
      "programid": 0,
      "enter_date": "2025-10-29",
      "exit_date": "2025-10-29",
      "code1": "string",
      "code2": "string",
      "exitcode": "string",
      "schoolid": 0,
      "studentid": 0,
      "gradelevel": 0,
      "sp_comment": "string"
    }
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |

### POST /ws/schema/table/transportation

Create a single Transportation Record

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | PLUGINS |

#### Description

Create a single transportation record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert. Payload must include Student ID. |

**Model Description:**

```
transportationTableRecord {
  tables (transportationSchemaRecord, optional)
}

transportationSchemaRecord {
  transportation (transportation, optional)
}

transportation {
  studentid (integer, optional): ID of the student associated to the transportation record
  description (string, optional): Description of the transportation record
  schoolid (integer, optional): The school number of the school associated to the transportation record
  startdate (string, optional): Start date for the transportation record
  enddate (string, optional): End date for the transportation record
  departuretime (string, optional): String indicating arrival time of day in seconds after midnight
  arrivaltime (string, optional): String indicating arrival time of day in seconds after midnight
  fromto (string, optional): String value indicating route direction
  type (string, optional): String value indicating type of transportation
  monday (integer, optional): Number value of 0/1 indicating whether transportation record applies to Monday
  tuesday (integer, optional): Number value of 0/1 indicating whether transportation record applies to Tuesday
  wednesday (integer, optional): Number value of 0/1 indicating whether transportation record applies to Wednesday
  thursday (integer, optional): Number value of 0/1 indicating whether transportation record applies to Thursday
  friday (integer, optional): Number value of 0/1 indicating whether transportation record applies to Friday
  distance (number, optional): Number indicating the distance of the transportation record route
  distanceindicator (string, optional): String indicating unit type for 'distance' value
  linkingcode (string, optional): Linking code for transportation record
  routenumber (string, optional): Route number for the transportation record
  busnumber (string, optional): Bus number for the transportation record
  drivername (string, optional): Driver name for the transportation record
  contactnumber (string, optional): Contact number for the transportation record
  stopnumber (string, optional): Stop number for the transportation record
  address (string, optional): Address for the transportation record
  specialinstructions (string, optional): Special instructions for the transportation record
}
```

**Model Schema:**

```json
{
  "tables": {
    "transportation": {
      "studentid": 0,
      "description": "string",
      "schoolid": 0,
      "startdate": "2025-10-29",
      "enddate": "2025-10-29",
      "departuretime": "string",
      "arrivaltime": "string",
      "fromto": "string",
      "type": "string",
      "monday": 0,
      "tuesday": 0,
      "wednesday": 0,
      "thursday": 0,
      "friday": 0,
      "distance": 0,
      "distanceindicator": "string",
      "linkingcode": "string",
      "routenumber": "string",
      "busnumber": "string",
      "drivername": "string",
      "contactnumber": "string",
      "stopnumber": "string",
      "address": "string",
      "specialinstructions": "string"
    }
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Created | [Complex Model - See API Documentation] |

### DELETE /ws/schema/table/transportation/{id}

Delete Transportation Record

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | PLUGINS |

#### Description

Delete a single transportation record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Transportation record identifier, TRANSPORTATION.DCID |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | No Content | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Conflict | [Complex Model - See API Documentation] |
| 500 | Internal Server Error | [Complex Model - See API Documentation] |
