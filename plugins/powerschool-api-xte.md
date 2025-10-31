
# PowerSchool XTE API

## xte

### PUT /ws/xte/score

Create or Update Scores

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Create or update assignment scores.
Plugins accessing this endpoint may save only assignment scores.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| scores | Model | body | Scores to create or update |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Success | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |
| 412 | Resubmit | [Complex Model - See API Documentation] |

### PUT /ws/xte/score/assignment

Create or Update a single Assignment Score

| Property | Value |
|----------|-------|
| Available Since | 12.0.1 |
| Accessible To | PLUGINS |

#### Description

Create or update a single assignment score.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| data | Model | body | Score to create or update |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Success | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |
| 412 | Resubmit | [Complex Model - See API Documentation] |

### DELETE /ws/xte/assignment_section/students

Delete Specified Assignment Student Associations

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Delete the assignment student associations for the given lists of Student DCID's and assignment section ID values. Note: This is a 'blind' delete. Invalid Student.DCID and assignment section ID values will not generate an error response. Deleting all students from a section results in the default condition where PTP assumes all students are selected.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| force | boolean | query | If true, forces deletion of students with scores present from the section assignment, and those students’ scores for the assignment |
| data | Model | body | Filter object used to limit underlying query |

**Model Description:**

```
ResourceFilter {
  student_ids (Array[integer], optional): Student DCIDs to filter by
  section_ids (Array[integer], optional): Assignment section IDs to filter by
}
```

**Model Schema:**

```json
{
  "student_ids": [
    0
  ],
  "section_ids": [
    0
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Success | [Complex Model - See API Documentation] |
| 400 | Validation Error | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Locked Term | [Complex Model - See API Documentation] |

### GET /ws/xte/teacher_category

Get a list of teacher categories for the current user.

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get a list of teacher categories for the current user.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |
| year_id | integer | query | Year ID that the teacher is instructing at a school. Required for OAuth clients only. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
TeacherCategory {
  id (integer, optional): Primary key.
  districtteachercategoryid (integer, optional): Foreign key if applicable.
  color (integer, optional): Color code for category.
  usersdcid (integer, optional): The users dcid for the owner of this category.
  displayposition (integer, optional): Sort order column.
  isinfinalgrades (boolean, optional): True if category is in final grades.
  isactive (boolean, optional): True if category is active.
  isusermodifiable (boolean, optional): True if user can modify this category.
  isdefaultpublishscores (boolean, optional): True if default is to publish scores.
  categorytype (string, optional): The category type is 'user' or 'district'.
  defaultDaysBeforeDue (integer, optional): The default days before assignment due date
  defaultpublishstate (string, optional): The default publish state.
  name (string, optional): The category name.
  description (string, optional): The category description.
  defaulttotalvalue (number, optional): The default total score for this category.
  defaultscoreentrypoints (number, optional): The default total score for this category.
  defaultextracreditpoints (number, optional): The default extra credit for this category.
  defaultweight (number, optional): The default total score for this category.
  _categoryschoolexcludeassocs (Array[TeacherCategoryResource.TeacherCategorySectionExcludeAssoc], optional)
}

TeacherCategorySectionExcludeAssoc {
  id (integer, optional): The primary key of the TeacherCategorySectionExcludeAssoc row.
  TeacherCategoryid (integer, optional): The ID of the associated TeacherCategory row.
  sectionsdcid (integer, optional): The sections DCID tied to this assocation.
}
```

**Response Schema:**

```json
{
  "id": 0,
  "districtteachercategoryid": 0,
  "color": 0,
  "usersdcid": 0,
  "displayposition": 0,
  "isinfinalgrades": true,
  "isactive": true,
  "isusermodifiable": true,
  "isdefaultpublishscores": true,
  "categorytype": "string",
  "defaultpublishoption": "Immediately",
  "defaultDaysBeforeDue": 0,
  "defaultpublishstate": "string",
  "name": "string",
  "description": "string",
  "defaultscoretype": "string",
  "defaulttotalvalue": 0,
  "defaultscoreentrypoints": 0,
  "defaultextracreditpoints": 0,
  "defaultweight": 0,
  "_categoryschoolexcludeassocs": [
    {
      "id": 0,
      "TeacherCategoryid": 0,
      "sectionsdcid": 0
    }
  ]
}
```

### POST /ws/xte/teacher_category

Create a teacher category.

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Create a teacher category.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |
| teachercategory | Model | body | An array of TeacherCategory records to update. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Created | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### DELETE /ws/xte/teacher_category/{teacher_category_id}

Delete a teacher category.

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Delete a teacher category.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| teacher_category_id | long | path | The ID of the teacher category. |
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### GET /ws/xte/teacher_category/{teacher_category_id}

Get a teacher category by ID.

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get a teacher category by ID.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| teacher_category_id | long | path | The ID of the teacher category. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
TeacherCategory {
  id (integer, optional): Primary key.
  districtteachercategoryid (integer, optional): Foreign key if applicable.
  color (integer, optional): Color code for category.
  usersdcid (integer, optional): The users dcid for the owner of this category.
  displayposition (integer, optional): Sort order column.
  isinfinalgrades (boolean, optional): True if category is in final grades.
  isactive (boolean, optional): True if category is active.
  isusermodifiable (boolean, optional): True if user can modify this category.
  isdefaultpublishscores (boolean, optional): True if default is to publish scores.
  categorytype (string, optional): The category type is 'user' or 'district'.
  defaultDaysBeforeDue (integer, optional): The default days before assignment due date
  defaultpublishstate (string, optional): The default publish state.
  name (string, optional): The category name.
  description (string, optional): The category description.
  defaulttotalvalue (number, optional): The default total score for this category.
  defaultscoreentrypoints (number, optional): The default total score for this category.
  defaultextracreditpoints (number, optional): The default extra credit for this category.
  defaultweight (number, optional): The default total score for this category.
  _categoryschoolexcludeassocs (Array[TeacherCategoryResource.TeacherCategorySectionExcludeAssoc], optional)
}

TeacherCategorySectionExcludeAssoc {
  id (integer, optional): The primary key of the TeacherCategorySectionExcludeAssoc row.
  TeacherCategoryid (integer, optional): The ID of the associated TeacherCategory row.
  sectionsdcid (integer, optional): The sections DCID tied to this assocation.
}
```

**Response Schema:**

```json
{
  "id": 0,
  "districtteachercategoryid": 0,
  "color": 0,
  "usersdcid": 0,
  "displayposition": 0,
  "isinfinalgrades": true,
  "isactive": true,
  "isusermodifiable": true,
  "isdefaultpublishscores": true,
  "categorytype": "string",
  "defaultpublishoption": "Immediately",
  "defaultDaysBeforeDue": 0,
  "defaultpublishstate": "string",
  "name": "string",
  "description": "string",
  "defaultscoretype": "string",
  "defaulttotalvalue": 0,
  "defaultscoreentrypoints": 0,
  "defaultextracreditpoints": 0,
  "defaultweight": 0,
  "_categoryschoolexcludeassocs": [
    {
      "id": 0,
      "TeacherCategoryid": 0,
      "sectionsdcid": 0
    }
  ]
}
```

### PUT /ws/xte/teacher_category/{teacher_category_id}

Update a teacher category.

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Update a teacher category.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| teacher_category_id | long | path | The id of the teacher category. |
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |
| term_id | integer | query | Term ID that the teacher is instructing at a school. Required for OAuth clients only. |
| teachercategory | Model | body | An array of TeacherCategory records to update. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | OK | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### GET /ws/xte/grade_scale/scales/{grade_scale_ids}

Get all the grade scales that match the ID list passed in

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | ADMIN,GUARDIAN,STUDENT,TEACHERS,PLUGINS |

#### Description

Returns all grade scales and grade scale items matching the input ID list

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| grade_scale_ids | string | path | IDs used to look up standards |
| include_items | boolean | query | If included and false, prevents grade scale items from being included with the scales |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
Scale {
  id (integer, optional): The ID of the Grade Scale
  istermweightingshown (boolean, optional): true to show the UI columns for term weighting
  grade_replacement_policy (number, optional): The ID of the optional grade replacement policy
  dcid (number, optional): The primary key of this row
  isforcoursegrade (boolean, optional): true if this grade is used for a Course
  isforstandards (boolean, optional): true if this grade is for a Standard
  isgpashown (boolean, optional): true if gpa is shown for this grade
  name (string, optional): The name of the Grade Scale
  Type (NUMERIC, ALPHA)
  _items (Array[GradeScaleResource.Item], optional): grade scale items for this scale
  description (string, optional): The Grade Scale description
  displayposition (integer, optional): The display position items with the same cutoff/value
  hasrelatedscales (boolean, optional): true if any other scale is related via GradeScaleRelated table
  modify_code (boolean, optional): true if you can modify the scale
}

Item {
  id (integer, optional): The ID of the Grade Scale
  graduationcredit (boolean, optional): true if this grade counts toward graduation credit
  description (string, optional): The Grade Scale Item description
  alt_grade_points (number, optional): The alternate grade points for this grade
  excludefromafg (boolean, optional): Exclude from added final grade
  _parentgradescale (GradeScaleResource.ParentScale, optional)
  cutoffpercentage (number, optional): Percent cutoff for converting from percent
  countsingpa (boolean, optional): true if this grade counts toward gpa
  dcid (integer, optional): Primary Key of this row
  teacherscale (boolean, optional): true if this is a teacher created/custom grade scale
  name (string, optional): The name of the Grade Scale
  grade_points (number, optional): The number of grade points for this grade
  addedvalue (boolean, optional): true if there can be added value for this grade
  cutoffpoints (number, optional): The point cutoff value for conversion from other scales.
  isproficient (boolean, optional): true if this grade indicates proficiency
  value (number, optional): The percent or numeric value for this grade
}

ParentScale {
  id (integer, optional): The ID of the Grade Scale
  dcid (integer, optional): Primary Key of this row
}
```

**Response Schema:**

```json
{
  "id": 0,
  "istermweightingshown": true,
  "grade_replacement_policy": 0,
  "dcid": 0,
  "isforcoursegrade": true,
  "isforstandards": true,
  "isgpashown": true,
  "name": "string",
  "gradescaletype": "string",
  "_items": [
    {
      "id": 0,
      "graduationcredit": true,
      "description": "string",
      "alt_grade_points": 0,
      "excludefromafg": true,
      "_parentgradescale": {
        "id": 0,
        "dcid": 0
      },
      "cutoffpercentage": 0,
      "countsingpa": true,
      "dcid": 0,
      "teacherscale": true,
      "name": "string",
      "grade_points": 0,
      "addedvalue": true,
      "cutoffpoints": 0,
      "isproficient": true,
      "value": 0
    }
  ],
  "description": "string",
  "displayposition": 0,
  "hasrelatedscales": true,
  "modify_code": true
}
```

### DELETE /ws/xte/assignment_section/students

Delete Specified Assignment Student Associations

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Delete the assignment student associations for the given lists of Student DCID's and assignment section ID values. Note: This is a 'blind' delete. Invalid Student.DCID and assignment section ID values will not generate an error response. Deleting all students from a section results in the default condition where PTP assumes all students are selected.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| force | boolean | query | If true, forces deletion of students with scores present from the section assignment, and those students’ scores for the assignment |
| data | Model | body | Filter object used to limit underlying query |

**Model Description:**

```
ResourceFilter {
  student_ids (Array[integer], optional): Student DCIDs to filter by
  section_ids (Array[integer], optional): Assignment section IDs to filter by
}
```

**Model Schema:**

```json
{
  "student_ids": [
    0
  ],
  "section_ids": [
    0
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Success | [Complex Model - See API Documentation] |
| 400 | Validation Error | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Locked Term | [Complex Model - See API Documentation] |

### DELETE /ws/xte/assignment/{assignment_id}/assignmentstandards

Delete Assignment Standard Association

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Delete standard association items and optionally any standard scores associated to them. Note - This is a 'blind' delete. StandardIDs that are not linked to the assignment will not trigger an error return.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| assignment_id | long | path | ID of the assignment |
| standard_ids | string | query | Comma-separated list of standard ID values to be deleted from the assignment |
| force | boolean | query | If true, forces deletion of dependent standard scores that are not empty along with the standard from the assignment |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | Standard Deleted OK | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Validation Error, StandardScore Rows Exist or Locked Term | [Complex Model - See API Documentation] |

### GET /ws/xte/section/assignment/

Get Assignments by Section

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get assignment data for the specified sections.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |
| section_ids | long | query | Comma-separated list of section_dcid values. Corresponds to SECTIONS.DCID in the database. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
Assignment {
  id (integer, optional): Primary key
  name (string, optional): Name of the assignment
  due_date (string, optional): Due date of the assignment
}
```

**Response Schema:**

```json
{
  "id": 0,
  "name": "string",
  "due_date": "2025-10-29"
}
```

### POST /ws/xte/section/assignment/

Create a Section Assignment

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Creates an assignment with embedded assignment_section, assignmentstandardassociations, assignmentstudentassociations and assignmentcategoryassociations records. All values (except DueDate and the student lists) must be identical across all section assignment records within an assignment.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| users_dcid | long | query | User's DCID of the teacher requesting the assignments. Required for OAuth clients only. |
| assignment | Model | body | The Assignment being created. NOTE - If standard associations are included, then standard scoring method must be included and set to Grade Scale. |

**Model Description:**

```
Assignment {
  id (integer, optional): Primary key
  name (string, optional): Name of the assignment
  due_date (string, optional): Due date of the assignment
}
```

**Model Schema:**

```json
{
  "id": 0,
  "name": "string",
  "due_date": "2025-10-29"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Assignment created | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | not found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### DELETE /ws/xte/section/assignment/{id}

Delete a Section Assignment by ID

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Deletes an assignment and embedded assignment_section, assignmentstandardassociations, assignmentstudentassociations and assignmentcategoryassociations records

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | long | path | ID of the Section Assignment record. |
| users_dcid | long | query | User's DCID of the teacher responsible for the deletion. Required for OAuth clinets only. |
| force | boolean | query | When set to true an assignment with grades associated will be deleted along with the grades |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | Assignment deleted | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 412 | Validation Error - Assignment has grades associated | [Complex Model - See API Documentation] |

### GET /ws/xte/section/assignment/{id}

Get a Section Assignment

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get an assignment along with embedded assignment_section, assignmentstandardassociations, assignmentstudentassociations, and assignmentcategoryassociations records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | long | path | ID of the section assignment record. |
| users_dcid | long | query | User's DCID of the teacher requesting the assignment. Required for OAuth clinets only. |
| assignment | Model | body | The complete assignment being updated. |

**Model Description:**

```
Assignment {
  id (integer, optional): Primary key
  name (string, optional): Name of the assignment
  due_date (string, optional): Due date of the assignment
}
```

**Model Schema:**

```json
{
  "id": 0,
  "name": "string",
  "due_date": "2025-10-29"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Assignment Created | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### PUT /ws/xte/section/assignment/{id}

Update a Section Assignment

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Update an assignment along with embedded assignment_section, assignmentstandardassociations, assignmentstudentassociations, and assignmentcategoryassociations records. All values submmitted overwrite the existing values. All sections must be included in multi-section assignment updates. All values (except DueDate and the student lists) must be identical across all section assignment records within an assignment.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | long | path | ID of the section assignment record. |
| users_dcid | long | query | User's DCID of the teacher responsible for the change. Required for OAuth clients only. |
| update_scores | boolean | query | Signals weather or not to update scores if a scoring configuration change could cause a score change. Optional with no default. If there are existing scores and scoring is changed, this must be specified. |
| assignment | Model | body | The complete assignment being updated. Note - To remain consistent with the UI, in assignments containing multiple AssignmentSection records, the AssignmentSection records should all be identical aside from IDs and DueDates. |

**Model Description:**

```
Assignment {
  id (integer, optional): Primary key
  name (string, optional): Name of the assignment
  due_date (string, optional): Due date of the assignment
}
```

**Model Schema:**

```json
{
  "id": 0,
  "name": "string",
  "due_date": "2025-10-29"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | Assignment Created | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

### DELETE /ws/xte/assignment/{assignment_id}/assignmentstandards

Delete Assignment Standard Association

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | TEACHERS,PLUGINS |

#### Description

Delete standard association items and optionally any standard scores associated to them. Note - This is a 'blind' delete. StandardIDs that are not linked to the assignment will not trigger an error return.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| assignment_id | long | path | ID of the assignment |
| standard_ids | string | query | Comma-separated list of standard ID values to be deleted from the assignment |
| force | boolean | query | If true, forces deletion of dependent standard scores that are not empty along with the standard from the assignment |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | Standard Deleted OK | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 409 | Validation Error, StandardScore Rows Exist or Locked Term | [Complex Model - See API Documentation] |

### GET /ws/xte/section/standard

Get the Standards for assignments based on a list of section IDs

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get the Standards for a list of section IDs. Remove items not active or not allowing assignment scores unless asked for.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| section_ids | string | query | Comma-separated list of section unique IDs; corresponds to SECTIONS.DCID in the database |
| include_inactive | boolean | query | If true, will include isactive = 0 rows |
| include_nonassigment | boolean | query | If true, will include isassignmentallowed = 0 rows |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
Standard {
  standardid (integer, optional): The ID of the standard
  longitudinalid (integer, optional): The longitudinal ID of the standard
  yearid (integer, optional): The year ID of the standard
  identifier (string, optional): The unique standard identifier
  displayposition (integer, optional): The display position of the standard
  conversionscale (integer, optional): The conversion scale associated to the standard
  gradescaleitemdcid (integer, optional): The grade scale associated to the standard
  name (string, optional): The name of the standard
  description (string, optional): The description of the standard
  subjectarea (string, optional): The subject area of the standard
  isactive (boolean, optional): True if the status of the standard is active
  iscommentincluded (boolean, optional): True if the standard is allowed to have comments
  maxcommentlength (integer, optional): The maximum length of the standard's comment
  isassignmentallowed (boolean, optional): True if the standard is allowed to be associated to an assignment
  externalid (string, optional): The external ID of the standard
  isexcludedfromreports (boolean, optional): True if the standard is excluded from appearing on reports
  _level (integer, optional): The calculated level of the standard
}
```

**Response Schema:**

```json
{
  "standardid": 0,
  "longitudinalid": 0,
  "yearid": 0,
  "identifier": "string",
  "displayposition": 0,
  "conversionscale": 0,
  "gradescaleitemdcid": 0,
  "name": "string",
  "description": "string",
  "subjectarea": "string",
  "isactive": true,
  "iscommentincluded": true,
  "maxcommentlength": 0,
  "isassignmentallowed": true,
  "externalid": "string",
  "isexcludedfromreports": true,
  "_level": 0
}
```

### POST /ws/xte/standard/score

Get standard scores

| Property | Value |
|----------|-------|
| Available Since | 10.0.0 |
| Accessible To | ADMIN,TEACHERS,PLUGINS |

#### Description

Get a list of standard scores based on a filter of section(s) and assignment(s).

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| assignment_ids | Model | body |  |

**Model Description:**

```
StandardScoreFilter {
  assignment_ids (Array[integer], optional): The assignment id(s) to filter by
  standard_ids (Array[integer], optional): The standard id(s) to filter by
  section_ids (Array[integer], optional): The section dcid(s) to filter by
}
```

**Model Schema:**

```json
{
  "assignment_ids": [
    0
  ],
  "standard_ids": [
    0
  ],
  "section_ids": [
    0
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |
| 409 | Validation Error | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
StandardScore {
  assignmentscoreid (integer, optional): Primary key
  yearid (integer, optional): Year ID
  _assignmentsection (ScoreResource.AssignmentSection, optional)
  studentsdcid (integer, optional): Students DCID
  isLate (boolean, optional): Whether score is flagged as late
  isCollected (string, optional): Whether score is flagged as collected
  isExempt (string, optional): Whether score is flagged as exempt
  isMissing (string, optional): Whether score is flagged as missing
  isAbsent (string, optional): Whether score is flagged as absent
  isIncomplete (string, optional): Whether score is flagged as incomplete
  actualscoreentered (string, optional): Score entered by the teacher
  actualscoregradescaledcid (integer, optional): Gradescale used on this score
  scorepercent (number, optional): Percent student got on this assignment
  scorepoints (number, optional): Total score points student got on this assignment
  scorelettergrade (string, optional): Letter grade of this score if gradescale is alpha type
  scorenumericgrade (number, optional): Numeric grade of this score if gradescale is numeric type
  scoreentrydate (string, optional): Timestamp when this score was last updated
  altnumericgrade (number, optional): Alternate numeric grade if has alternate gradescale and its a numeric scale
  altalphagrade (string, optional): Alternate letter grade if has alternate gradescale and its an alpha scale
  altscoregradescaledcid (integer, optional): Alternate gradescale assignment to this score
  hasretake (boolean, optional): Does this score have retakes assigned to it
  _assignmentstandardassociation (ScoreResource.AssignmentStandardAssoc, optional)
}

AssignmentSection {
  assignmentsectionid (integer, optional): Primary key
}

AssignmentStandardAssoc {
  assignmentstandardassocid (integer, optional): Primary key
  standardid (integer, optional): Primary key of Standard record
  assignmentid (integer, optional): Primary key of Assignment record
}
```

**Response Schema:**

```json
{
  "assignmentscoreid": 0,
  "yearid": 0,
  "_assignmentsection": {
    "assignmentsectionid": 0
  },
  "studentsdcid": 0,
  "isLate": true,
  "isCollected": "string",
  "isExempt": "string",
  "isMissing": "string",
  "isAbsent": "string",
  "isIncomplete": "string",
  "actualscoreentered": "string",
  "ActualScoreKind": "REAL_SCORE",
  "actualscoregradescaledcid": 0,
  "scorepercent": 0,
  "scorepoints": 0,
  "scorelettergrade": "string",
  "scorenumericgrade": 0,
  "scoreentrydate": "2025-10-29T20:11:32.009Z",
  "altnumericgrade": 0,
  "altalphagrade": "string",
  "altscoregradescaledcid": 0,
  "hasretake": true,
  "_assignmentstandardassociation": {
    "assignmentstandardassocid": 0,
    "standardid": 0,
    "assignmentid": 0
  }
}
```
