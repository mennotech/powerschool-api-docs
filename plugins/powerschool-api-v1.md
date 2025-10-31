
# PowerSchool V1 API

## v1

### GET /ws/v1/test_subscription

Test subscription GET

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Return static data

#### Response Class (Status 200)

```
test_subscription {
  id (integer, optional)
  content (string, optional): literal text - "Test Subscription"
}
```

**Response Schema:**

```json
{
  "id": 0,
  "content": "string"
}
```

### GET /ws/v1/course/{id}

Get a course

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get course object by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | double | path | Course record ID |
| extensions | string | query | Comma-separated list of schema extensions to return |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Request is for a resource the user is not allowed to access | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
course {
  extensions (string, optional): Comma-separated list of schema extensions available for the resource
  course_number (string, optional): Number that is used to identify the course stringMax. Length:11
  course_name (string, optional): Name of the course stringMax. Length:40
}
```

**Response Schema:**

```json
{
  "extensions": "string",
  "id": 0,
  "course_number": "string",
  "course_name": "string"
}
```

### GET /ws/v1/district

Get current district data

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns district-level configuration data

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| expansions | string | query | Comma-separated list of expansion elements to include |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
District {
  uuid (string, optional): Universally unique ID of the district
  name (string, optional): The district's complete and official name
  district_number (string, optional): The number assigned to the district by the state
  addresses (Inline Model 1, optional)
  expansions (string, optional): Comma-separated list of expansions associated with the district resource
  districts_of_residence (v1.district_districts_of_residence, optional): The districts of residence
  district_race_codes (Array[v1.district_district_race_codes], optional): The district's race categories and associated federal race codes
  entry_codes (v1.district_entry_codes, optional)
  ethnicity_race_decline_to_specify (v1.district_ethnicity_race_decline_to_specify, optional): The district's ethnicity race decline to specify settings
  exit_codes (v1.district_exit_codes, optional)
  federal_race_categories (Array[v1.district_federal_race_categories], optional): The district's federal race categories
  fees_payment_methods (v1.district_fees_payment_methods, optional): The district's payment method codes
  scheduling_reporting_ethnicities (v1.district_scheduling_reporting_ethnicities, optional)
  test_setup (Inline Model 3, optional)
}

Inline Model 1 {
  physical (v1.district_physical_address, optional)
}

Inline Model 2 {
  main (v1.district_phone_main, optional)
  fax (v1.district_phone_fax, optional)
}

district_districts_of_residence {
  district_of_residence (Array[v1.district_district_of_residence], optional)
}

district_district_race_codes {
  district_race_code (v1.district_district_race_code_item, optional)
}

district_entry_codes {
  entry_code (Array[v1.district_entry_code], optional): The district's entry codes
}

district_ethnicity_race_decline_to_specify {
  ethnicity_allow_to_decline (boolean, optional): Ethnicity allow to decline
  ethnicity_allow_to_decline_label (string, optional): Ethnicity allow to decline display label text
  race_allow_to_decline (boolean, optional): Race allow to decline
  race_allow_to_decline_label (string, optional): Race allow to decline display label text
}

district_exit_codes {
  exit_code (Array[v1.district_exit_code], optional): The district's exit codes
}

district_federal_race_categories {
  federal_race_category (Array[v1.district_federal_race_category], optional)
}

district_fees_payment_methods {
  fees_payment_method (v1.district_fees_payment_method, optional)
}

district_scheduling_reporting_ethnicities {
  scheduling_reporting_ethnicity (v1.district_scheduling_reporting_ethnicity, optional)
}

Inline Model 3 {
  tests (v1.district_tests, optional)
}

district_physical_address {
  street (string, optional): The district's street address
  city (string, optional): The city element of the district's address
  state_province (string, optional): The state/province element of the district's address
  postal_code (string, optional): The zip/postal code element of the district's address
}

district_phone_main {
  number (string, optional)
}

district_phone_fax {
  number (string, optional)
}

district_district_of_residence {
  id (integer, optional): Unique sequential number generated by the application
  code (string, optional): The district of residence code
  description (string, optional): The district of residence description
  district_boundary (Array[v1.district_boundary_points], optional)
}

district_district_race_code_item {
  id (integer, optional): Unique sequential number generated by the application
  code (string, optional): The district race code
  description (string, optional): The district race code description
  federal_race_category_code (string, optional): The district race code associated federal race category code
  federal_race_category_description (string, optional): The district race code associated federal race category description
  district_race_code_sort_order (integer, optional): The district race code sorting order
}

district_entry_code {
  id (integer, optional): Unique sequential number generated by the application
  code (string, optional): The district entry code
  description (string, optional): The district entry code description
  sort_order (integer, optional): The district entry code sorting order
}

district_exit_code {
  id (integer, optional): Unique sequential number generated by the application
  code (string, optional): The district exit code
  description (string, optional): The district exit code description
  sort_order (integer, optional): The district exit code sorting order
}

district_federal_race_category {
  id (integer, optional): Unique sequential number generated by the application
  code (string, optional): The federal race category code
  description (string, optional): The federal race category description
  sort_order (integer, optional): The federal race category sorting order
}

district_fees_payment_method {
  code (string, optional): The code of the payment method
  description (string, optional): The description of the payment method
}

district_scheduling_reporting_ethnicity {
  id (integer, optional): The unique ID of the scheduling/reporting ethnicity code
  code (string, optional): The scheduling/reporting ethnicity code
  description (string, optional): The scheduling/reporting ethnicity description
}

district_tests {
  test (v1.district_test, optional)
}

district_boundary_points {
  point (string, optional)
}

district_test {
  test_id (integer, optional): The unique ID of the test
  test_name (string, optional): The name of the test
  test_description (string, optional): The description of the test
  test_type (integer, optional): The number code that indicates the test type
  test_scores (v1.district_test_scores, optional)
}

district_test_scores {
  test_score (v1.district_test_score, optional)
}

district_test_score {
  test_id (integer, optional): The unique ID of the test score
  test_name (string, optional): The name of the test score
  test_description (string, optional): The description of the test score
}
```

**Response Schema:**

```json
{
  "uuid": "string",
  "name": "string",
  "district_number": "string",
  "addresses": {
    "physical": {
      "street": "string",
      "city": "string",
      "state_province": "string",
      "postal_code": "string"
    }
  },
  "phones": {
    "main": {
      "number": "string"
    },
    "fax": {
      "number": "string"
    }
  },
  "@expansions": "string",
  "districts_of_residence": {
    "district_of_residence": [
      {
        "id": 0,
        "code": "string",
        "description": "string",
        "district_boundary": [
          {
            "point": "string"
          }
        ]
      }
    ]
  },
  "district_race_codes": [
    {
      "district_race_code": {
        "id": 0,
        "code": "string",
        "description": "string",
        "federal_race_category_code": "string",
        "federal_race_category_description": "string",
        "district_race_code_sort_order": 0
      }
    }
  ],
  "entry_codes": {
    "entry_code": [
      {
        "id": 0,
        "code": "string",
        "description": "string",
        "sort_order": 0
      }
    ]
  },
  "ethnicity_race_decline_to_specify": {
    "ethnicity_allow_to_decline": true,
    "ethnicity_allow_to_decline_label": "string",
    "race_allow_to_decline": true,
    "race_allow_to_decline_label": "string"
  },
  "exit_codes": {
    "exit_code": [
      {
        "id": 0,
        "code": "string",
        "description": "string",
        "sort_order": 0
      }
    ]
  },
  "federal_race_categories": [
    {
      "federal_race_category": [
        {
          "id": 0,
          "code": "string",
          "description": "string",
          "sort_order": 0
        }
      ]
    }
  ],
  "fees_payment_methods": {
    "fees_payment_method": {
      "code": "string",
      "description": "string"
    }
  },
  "scheduling_reporting_ethnicities": {
    "scheduling_reporting_ethnicity": {
      "id": 0,
      "code": "string",
      "description": "string"
    }
  },
  "test_setup": {
    "tests": {
      "test": {
        "test_id": 0,
        "test_name": "string",
        "test_description": "string",
        "test_type": 0,
        "test_scores": {
          "test_score": {
            "test_id": 0,
            "test_name": "string",
            "test_description": "string"
          }
        }
      }
    }
  }
}
```

### GET /ws/v1/district/school

Get current schools in district

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns a list of schools in the district

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| expansions | string | query | Comma-separated list of expansion elements to include |
| page | string | query | Page number to retrieve. Default value is 1. |
| pagesize | string | query | The maximum number of schools on a page. This value cannot be greater than the maximum page size, which is also the default value. For more information, see Pagination Usage. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
district_schools {
  extensions (string, optional): Comma-separated list of schema extensions to the resource
  school (Array[v1.district_school], optional)
}

district_school {
  id (integer, optional): Universally unique ID of the school
  school_number (string, optional): The school number of the school.
  name (string, optional): The school's name
  state_province_id (string, optional)
  low_grade (integer, optional): The lowest grade level that will be attending this school
  high_grade (integer, optional): The highest grade level that will be attending this school
  alternate_school_number (integer, optional): The school number of the school
  addresses (Array[v1.district_school_addresses], optional): Collection of school addresses
  full_time_equivalencies (v1.district_school_full_time_equivalencies, optional): The school's full time equivalency settings
  phones (v1.district_school_phones, optional): Collection of school phone numbers
  principal (Array[v1.district_school_principal], optional): The school's principal
  assistant_principal (Array[v1.district_school_assistant_principal], optional): The school's assistant principal
  school_boundary (Array[v1.district_school_boundary_points], optional): This is the encoded data for the boundary
  school_fees_setup (Array[v1.school_fees_setup], optional): School fees setup
}

district_school_addresses {
  physical (v1.school_address_physical, optional)
}

district_school_full_time_equivalencies {
  full_time_equivalency (Array[v1.district_school_full_time_equivalency], optional)
}

district_school_phones {
  main (v1.district_school_main_number, optional)
}

district_school_principal {
  email (string, optional): The principal's email address
  name (Array[v1.district_school_principal_name], optional)
}

district_school_assistant_principal {
  email (string, optional): The assistant principal's email address
  name (Array[v1.district_school_assistant_principal_name], optional)
}

school_fees_setup {
  exemption_status (integer, optional): The exemption status of the school fee
  fee_types (Array[v1.fee_type], optional)
}

school_address_physical {
  street (string, optional): The school's street address
  city (string, optional): The city element of the school's address
  state_province (string, optional): The state/province element of the school's address
  postal_code (string, optional): The zip/postal code element of the school's address
}

district_school_full_time_equivalency {
  fteid (integer, optional): Full-time equivalency ID
  name (string, optional): Full-time equivalency name
  grade_level_defaults (Array[v1.district_school_full_time_equivalency_grade_level], optional)
}

district_school_main_number {
  number (string, optional)
}

district_school_principal_name {
  first_name (string, optional): The principal's first name
  middle_name (string, optional): The principal's middle name
  last_name (string, optional): The principal's last name
}

district_school_assistant_principal_name {
  first_name (string, optional): The assistant principal's first name
  middle_name (string, optional): The assistant principal's middle name
  last_name (string, optional): The assistant principal's last name
}

district_school_boundary_point {
  point (string, optional)
}

fee_type {
  id (integer, optional): The ID of the fee type
  name (string, optional): The name of the fee type
  description (string, optional): The description of the fee type
  category (integer, optional): The priority number of the fee type
  creation_date (string, optional): The date the fee type was created
}

district_school_full_time_equivalency_grade_level {
  grade_level (integer, optional): The grade level to which this FTE is assigned by default
}
```

**Response Schema:**

```json
{
  "@expansions": "string",
  "@extensions": "string",
  "school": [
    {
      "id": 0,
      "school_number": "string",
      "name": "string",
      "state_province_id": "string",
      "low_grade": 0,
      "high_grade": 0,
      "alternate_school_number": 0,
      "addresses": [
        {
          "physical": {
            "street": "string",
            "city": "string",
            "state_province": "string",
            "postal_code": "string"
          }
        }
      ],
      "full_time_equivalencies": {
        "full_time_equivalency": [
          {
            "fteid": 0,
            "name": "string",
            "start_year": 0,
            "grade_level_defaults": [
              {
                "grade_level": 0
              }
            ]
          }
        ]
      },
      "phones": {
        "main": {
          "number": "string"
        }
      },
      "principal": [
        {
          "email": "string",
          "name": [
            {
              "first_name": "string",
              "middle_name": "string",
              "last_name": "string"
            }
          ]
        }
      ],
      "assistant_principal": [
        {
          "email": "string",
          "name": [
            {
              "first_name": "string",
              "middle_name": "string",
              "last_name": "string"
            }
          ]
        }
      ],
      "school_boundary": [
        [
          {
            "point": "string"
          }
        ]
      ],
      "school_fees_setup": [
        {
          "exemption_status": 0,
          "fee_types": [
            {
              "id": 0,
              "name": "string",
              "description": "string",
              "category": 0,
              "creation_date": "string"
            }
          ]
        }
      ]
    }
  ]
}
```

### GET /ws/v1/district/school/count

Get number of schools in district

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Retrieve the number of schools in the current district. The result does not include the "Graduated Students" school.

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
district_schools_count_resource {
  count (integer, optional): Count of schools in the current district
}
```

**Response Schema:**

```json
{
  "count": 0
}
```

### GET /ws/v1/district/student

Get one or more students

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Search the current district for all students matching specified criteria. The results are not limited by a default criteria.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| expansions | string | query | Comma-separated list of expansion elements to include |
| extensions | string | query | Comma-separated list of schema extension elements to include |
| page | string | query | Page number to retrieve. Default value is 1. |
| pagesize | string | query | The maximum number of schools on a page. This value cannot be greater than the maximum page size, which is also the default value. For more information, see Pagination Usage. |
| q | string | query | Criteria for selecting a subset of students in this school. For more information, see Searching Usage. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
district_students {
  extensions (string, optional): Comma-separated list of schema extensions to the resource
  student (v1.district_student, optional)
}

district_student {
  local_id (integer, optional): The student number assigned by the school
  name (v1.district_student_name, optional)
  addresses (v1.district_student_addresses, optional)
  alerts (v1.district_student_alerts, optional)
  contact (v1.district_student_contact, optional)
  contact_info (v1.district_student_contact_info, optional)
  demographics (v1.district_student_demographics, optional)
  school_enrollment (v1.district_student_school_enrollment, optional)
  ethnicity_race (v1.district_student_ethnicity_race, optional)
  fees (v1.district_student_fees, optional)
  initial_enrollment (v1.district_student_initial_enrollment, optional)
  lunch (v1.district_student_lunch, optional)
  phones (v1.district_student_phones, optional)
  schedule_setup (v1.district_student_schedule_setup, optional)
  counselors (v1.district_student_counselors, optional)
}

district_student_name {
  first_name (string, optional): The student's first name
  middle_name (string, optional): The student's middle name
  last_name (string, optional): The student's last name
}

district_student_addresses {
  mailing (v1.district_student_mailing_address, optional)
  physical (v1.district_student_physical_address, optional)
}

district_student_alerts {
  legal (v1.legal, optional)
  discipline (v1.discipline, optional)
  medical (v1.medical, optional)
  other (v1.other, optional)
}

district_student_contact {
  emergency_contact_name1 (string, optional): The student's emergency contact
  emergency_phone1 (string, optional): The phone number of the student's emergency contact
  emergency_contact_name2 (string, optional): The student's emergency contact
  emergency_phone2 (string, optional): The phone number of the student's emergency contact
  guardian_fax (string, optional): The fax number of student's guardian
  guardian_email (string, optional): The email of student's guardian
  mother (string, optional): The name of student's mother
  father (string, optional): The name of student's father
  doctor_name (string, optional): The name of student's doctor
  doctor_phone (string, optional): The phone number of student's doctor
}

district_student_contact_info {
  email (string, optional): The student's email contact
}

district_student_demographics {
  birth_date (string, optional): The student's date of birth
  district_entry_date (string, optional): The date the student entered the district
  projected_graduation_year (integer, optional): The year the student is expected to graduate. This may change if the student does not pass or skips a grade.
  ssn (string, optional): The student's Social Security number
}

district_student_school_enrollment {
  status_code (integer
  optional): The student's enrollment status. Valid values: 0=Active
  -1=Pre-Registered
  2=Transferred-Out
  3=Graduated
  4=Historical
  Any other integer=Inactive.
  enroll_status (string
  optional): The student's enrollment status. Valid values: A=Active
  P=Pre-Registered
  T=Transferred-Out
  G=Graduated
  H=Historical
  I=Inactive.
  enroll_status_description (string
  optional): The student's enrollment status description. This field is a textual representation of the enroll_status. Status 0 has description Active
  -1=Pre-Registered
  2=Transferred-Out
  3=Graduated
  4=Historical
  Any other integer=Inactive.
  grade_level (string
  optional): The grade the student is in. Valid values: {-1
  -2
  etc.
}

district_student_ethnicity_race {
  scheduling_reporting_ethnicity (string, optional): The student's heritage background
  federal_ethnicity (string, optional): Is the student Hispanic or Latino?
  federal_race_decline_indicator (string, optional): The student may decline to state their race. Can only have the value DECLINE_TO_SPECIFY.
  races (Array[v1.district_student_ethnicity_race_races], optional)
}

district_student_fees {
  fee (Array[v1.district_student_fee], optional)
}

district_student_initial_enrollment {
  district_entry_date (string, optional): The student's district entry date
  district_entry_grade_level (integer, optional): The student's district entry grade level
  school_entry_date (string, optional): The student's school entry date
  school_entry_grade_level (integer, optional): The student's school entry grade level
}

district_student_lunch {
  id (integer, optional): The student's lunch ID
  balance1 (number, optional): The student's current lunch account balance
  balance2 (number, optional): The student's previous lunch account balance
  balance3 (number, optional): The student's lunch account balance
  balance4 (number, optional): The student's lunch account balance
  last_meal (string, optional): The student's last meal
}

district_student_phones {
  main (v1.district_student_phone_main, optional)
}

district_student_schedule_setup {
  home_room (string, optional): The student's homeroom
  next_school (integer, optional): The school the student is going to go to next year
  sched_next_year_grade (integer, optional): The grade level the student is going to be in next year
}

district_student_counselors {
  counselor (Array[v1.district_student_counselor], optional)
}

district_student_mailing_address {
  street (string, optional): The student's mailing street address
  city (string, optional): The city element of the student's mailing address.
  state_province (string, optional): The state/province element of the student's mailing address.
  postal_code (string, optional): The zip/postal code element of the student's mailing address.
  grid_location (string, optional): The latitude/longitude coordinates of the student's mailing address
}

district_student_physical_address {
  street (string, optional): The student's street address
  city (string, optional): The city element of the student's address.
  state_province (string, optional): The state/province element of the student's address.
  postal_code (string, optional): The zip/postal code element of the student's address.
  grid_location (string, optional): The latitude/longitude coordinates of the student's physical address
}

legal {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

discipline {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

medical {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

other {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

district_student_full_time_equivelancy {
  fteid (integer, optional): The student's full-time equivalency ID
  name (string, optional): The student's full-time equivalency associated name
}

district_student_ethnicity_race_races {
  district_race_code (string, optional): The student's race code
  district_race_code_dsescription (string, optional): The description of the race code
  federal_race_code_category (string, optional): The federal race category associated to the race code
}

district_student_fee {
  id (integer, optional): The fee ID
  fee_amount (number, optional): The fee amount
  fee_balance (number, optional): The fee balance formatted as #.##.
  fee_dcscription (string, optional): The fee description
  date_created (string, optional): The date the fee was created formatted as YYYY-MM-DD
  date_modified (string, optional): The date the fee was last modified formatted as YYYY-MM-DD
  transaction_date (string, optional): The date of the transaction formatted as YYYY-MM-DD
  department_name (string, optional): The name of the department
  priority (number, optional): The fee priority order
  pro_ratable_indicator (number, optional): The fee pro-rated indicator
  group_transaction_id (number, optional): The fee group transaction ID
  school_id (number, optional): The school ID for the fee
  school_fee_id (number, optional): The school fee ID for the fee
  term_id (number, optional): The term ID
  year_id (number, optional): The year ID
  course_name (string, optional): The course name
  course_number (integer, optional): The course number
  category_name (string, optional): The fee category name
  type_id (number, optional): The fee type ID
  type_name (string, optional): The fee type name
  fee_transaction (v1.district_student_fee_transaction, optional)
}

district_student_phone_main {
  number (string, optional): The student's home phone number
}

district_student_counselor {
  id (integer, optional): The student counselor ID
  userDcid (integer, optional): The dcid of the user
  firstName (string, optional): The first name of the counselor
  lastName (string, optional): The last name of the counselor
  isPrimary (boolean, optional): True if the this is the primary counselor for the student.
}

district_student_fee_transaction {
  id (number, optional): The fee transaction ID
  transaction_amount (number, optional): The fee transaction amount formatted as #.##
  global_starting_balance (number, optional): The fee global starting balance formatted as #.##
  transaction_date (string, optional): The fee transaction date formatted as YYYY-MM-DD
  transaction_description (string, optional): The fee transaction description
  group_transaction_id (number, optional): The fee transaction group ID
  payment_method (string, optional): The fee transaction payment method
  school_id (number, optional): The school ID for the fee
  year_id (number, optional): The year ID
  starting_balance (number, optional): The fee transaction starting balance formatted as #.##
  global_net_balance (number, optional): The fee transaction global net balance formatted as #.##
  transaction_type (string, optional): The fee transaction type
  payment_reference_number (number, optional): The payment reference number
}
```

**Response Schema:**

```json
{
  "@expansions": "string",
  "@extensions": "string",
  "student": {
    "id": 0,
    "local_id": 0,
    "state_province_id": "string",
    "name": {
      "first_name": "string",
      "middle_name": "string",
      "last_name": "string"
    },
    "addresses": {
      "mailing": {
        "street": "string",
        "city": "string",
        "state_province": "string",
        "postal_code": "string",
        "grid_location": "string"
      },
      "physical": {
        "street": "string",
        "city": "string",
        "state_province": "string",
        "postal_code": "string",
        "grid_location": "string"
      }
    },
    "alerts": {
      "legal": {
        "description": "string",
        "expires_date": "string"
      },
      "discipline": {
        "description": "string",
        "expires_date": "string"
      },
      "medical": {
        "description": "string",
        "expires_date": "string"
      },
      "other": {
        "description": "string",
        "expires_date": "string"
      }
    },
    "contact": {
      "emergency_contact_name1": "string",
      "emergency_phone1": "string",
      "emergency_contact_name2": "string",
      "emergency_phone2": "string",
      "guardian_fax": "string",
      "guardian_email": "string",
      "mother": "string",
      "father": "string",
      "doctor_name": "string",
      "doctor_phone": "string"
    },
    "contact_info": {
      "email": "string"
    },
    "demographics": {
      "gender": "string",
      "birth_date": "string",
      "district_entry_date": "string",
      "projected_graduation_year": 0,
      "ssn": "string"
    },
    "school_enrollment": {
      "status_code": 0,
      "enroll_status": "string",
      "enroll_status_description": "string",
      "grade_level": "string",
      "entry_date": "string",
      "exit_date": "string",
      "school_number": 0,
      "entry_code": "string",
      "entry_comment": "string",
      "exit_code": "string",
      "exit_comment": "string",
      "district_of_residence": "string",
      "track": "string",
      "full_time_equivelancy": [
        {
          "fteid": 0,
          "name": "string"
        }
      ]
    },
    "ethnicity_race": {
      "scheduling_reporting_ethnicity": "string",
      "federal_ethnicity": "string",
      "federal_race_decline_indicator": "string",
      "races": [
        {
          "district_race_code": "string",
          "district_race_code_dsescription": "string",
          "federal_race_code_category": "string"
        }
      ]
    },
    "fees": {
      "fee": [
        {
          "id": 0,
          "fee_amount": 0,
          "fee_balance": 0,
          "fee_dcscription": "string",
          "date_created": "2025-10-29",
          "date_modified": "string",
          "transaction_date": "string",
          "department_name": "string",
          "priority": 0,
          "pro_ratable_indicator": 0,
          "group_transaction_id": 0,
          "school_id": 0,
          "school_fee_id": 0,
          "term_id": 0,
          "year_id": 0,
          "course_name": "string",
          "course_number": 0,
          "category_name": "string",
          "type_id": 0,
          "type_name": "string",
          "fee_transaction": {
            "id": 0,
            "transaction_amount": 0,
            "global_starting_balance": 0,
            "transaction_date": "string",
            "transaction_description": "string",
            "group_transaction_id": 0,
            "payment_method": "string",
            "school_id": 0,
            "year_id": 0,
            "starting_balance": 0,
            "global_net_balance": 0,
            "transaction_type": "string",
            "payment_reference_number": 0
          }
        }
      ]
    },
    "initial_enrollment": {
      "district_entry_date": "string",
      "district_entry_grade_level": 0,
      "school_entry_date": "string",
      "school_entry_grade_level": 0
    },
    "lunch": {
      "id": 0,
      "balance1": 0,
      "balance2": 0,
      "balance3": 0,
      "balance4": 0,
      "last_meal": "string"
    },
    "phones": {
      "main": {
        "number": "string"
      }
    },
    "schedule_setup": {
      "home_room": "string",
      "next_school": 0,
      "sched_next_year_grade": 0
    },
    "counselors": {
      "counselor": [
        {
          "id": 0,
          "userDcid": 0,
          "firstName": "string",
          "lastName": "string",
          "isPrimary": true
        }
      ]
    }
  }
}
```

### DELETE /ws/v1/event_subscription

Delete all event subscriptions

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Delete all subscriptions

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | The event subscriptions entity was successfully deleted | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | The event subscriptions entity doesn't exist | [Complex Model - See API Documentation] |
| 500 | Might be due to missing or malformed content type | [Complex Model - See API Documentation] |

### GET /ws/v1/event_subscription

Get event subscriptions

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

The root element that represents the data change event types that you want to subscribe to

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
event_subscriptions {
  key (string, optional): You can provide a key for identifying a particular instance of PowerSchool. PowerSchool will send the value to your webhook server along with the notification message indicating where the message came from.
  callback_url (string, optional): The URL of your webhook server that will handle events
  event_subscription (object, optional)
}
```

**Response Schema:**

```json
{
  "key": "string",
  "callback_url": "string",
  "event_subscription": {}
}
```

### PUT /ws/v1/event_subscription

Create or replace event subscriptions

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Create or replace your current subscription settings. Any update to the subscriptions will overwrite all existing subscriptions.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| event_subscriptions | Model | body | Subscriptions to add |

**Model Description:**

```
event_subscriptions {
  key (string, optional): You can provide a key for identifying a particular instance of PowerSchool. PowerSchool will send the value to your webhook server along with the notification message indicating where the message came from.
  callback_url (string, optional): The URL of your webhook server that will handle events
  event_subscription (object, optional)
}
```

**Model Schema:**

```json
{
  "key": "string",
  "callback_url": "string",
  "event_subscription": {}
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 201 | The event subscriptions entity was successfully created | [Complex Model - See API Documentation] |
| 204 | The event subscriptions entity was successfully replaced | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 415 | Invalid content-type | [Complex Model - See API Documentation] |
| 500 | Might be due to missing or malformed content type | [Complex Model - See API Documentation] |

### POST /ws/v1/fee/transaction

Post Fee Transaction

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Apply a fee transaction to a student fee, such as a payment, credit or void.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| fee_transaction | Model | body | Transaction to add |

**Model Description:**

```
fee_transaction {
  student_id (integer, optional): Student record's DCID
  fee_id (integer, optional): Fee record's DCID
  school_id (integer, optional): School record's DCID
  transaction_amount (number, optional): The transaction amount
  payment_method (string, optional): The payment method for the transaction
  date (string, optional): The optional transaction date
  description (string, optional): A brief description
}
```

**Model Schema:**

```json
{
  "student_id": 0,
  "fee_id": 0,
  "fee_start_year": 0,
  "school_id": 0,
  "transaction_amount": 0,
  "transaction_type": "string",
  "payment_method": "string",
  "date": "2025-10-29",
  "description": "string"
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Invalid payload structure | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 415 | Invalid content-type | [Complex Model - See API Documentation] |
| 500 | Might be due to missing or malformed content type | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
result_code_200 {}
```

**Response Schema:**

```json
{}
```

### POST /ws/v1/fee/transactions

Post Fee Transactions

| Property | Value |
|----------|-------|
| Available Since | 25.2.0 |
| Accessible To | PLUGINS |

#### Description

Apply multiple fee transactions to a student fee, such as a payment, credit or void.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| fee_transactions | Model | body | Transactions to add |

**Model Description:**

```
fee_transactions {
  fee_transactions (v1.fee_transaction_array, optional)
}

fee_transaction_array {
  fee_transaction (Array[v1.fee_transaction], optional)
}

fee_transaction {
  student_id (integer, optional): Student record's DCID
  fee_id (integer, optional): Fee record's DCID
  school_id (integer, optional): School record's DCID
  transaction_amount (number, optional): The transaction amount
  payment_method (string, optional): The payment method for the transaction
  date (string, optional): The optional transaction date
  description (string, optional): A brief description
}
```

**Model Schema:**

```json
{
  "fee_transactions": {
    "fee_transaction": [
      {
        "student_id": 0,
        "fee_id": 0,
        "fee_start_year": 0,
        "school_id": 0,
        "transaction_amount": 0,
        "transaction_type": "string",
        "payment_method": "string",
        "date": "2025-10-29",
        "description": "string"
      }
    ]
  }
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Invalid payload structure | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 415 | Invalid content-type | [Complex Model - See API Documentation] |
| 500 | Might be due to missing or malformed content type | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
result_code_200 {}
```

**Response Schema:**

```json
{}
```

### GET /ws/v1/metadata

Get powerschool metadata and maximum page size for resources.

| Property | Value |
|----------|-------|
| Available Since | 7.8.0, 9.0.0 includes PS/PTG/State version metadata, 12.0.1 includes Unified Classroom status |
| Accessible To | NONE,ADMIN,GUARDIAN,STUDENT,TEACHERS,SUBS,PLUGINS |

#### Description

List PowerSchool metadata and maximum page sizes of each resources. Maximum page size is a plugin-specific value that determines the maximum number of records allowed on a page. The plugin-specific value is entered by the PowerSchool Administrator in System > System Settings > Plugin Management Configuration > [Select Plugin] > Data Configuration.

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
metadata {
  course_max_page_size (integer, optional): Maximum page size for course record requests
  machine_uptime (string, optional): Server uptime
  mobile_api_version (string, optional): Mobile API version number
  plugin_id (integer, optional): PluginDef table id field
  powerschool_uptime (string, optional): PowerSchool uptime
  powerschool_version (string, optional): PowerSchool version number
  school_max_page_size (integer, optional): Maximum page size for school record requests
  schema_table_query_max_page_size (integer, optional): Maximum page size for table query record requests
  section_max_page_size (integer, optional): Maximum page size for section record requests
  section_enrollment_max_page_size (integer, optional): Maximum page size for section enrollment record requests
  state_reporting_version (string, optional): State reporting version number
  staff_max_page_size (integer, optional): Maximum page size for staff record requests
  state (string, optional): PowerSchool district state
  student_max_page_size (integer, optional): Maximum page size for student record requests
  term_max_page_size (integer, optional): Maximum page size for term record requests
  district_timezone (string, optional): The timezone of district
  district_uuid (string, optional): The district UID mapped to districtuuid
}
```

**Response Schema:**

```json
{
  "course_max_page_size": 0,
  "machine_uptime": "string",
  "mobile_api_version": "string",
  "plugin_id": 0,
  "powerschool_uptime": "string",
  "powerschool_version": "string",
  "school_max_page_size": 0,
  "schema_table_query_max_page_size": 0,
  "section_max_page_size": 0,
  "section_enrollment_max_page_size": 0,
  "state_reporting_version": "string",
  "staff_max_page_size": 0,
  "state": "string",
  "student_max_page_size": 0,
  "term_max_page_size": 0,
  "district_timezone": "string",
  "district_uuid": "string",
  "sso_enabled_admin": "false",
  "sso_enabled_guardian": "false",
  "sso_enabled_student": "false",
  "sso_enabled_teacher": "false"
}
```

### GET /ws/v1/school

Get current schools in district

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns a list of schools in the district

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| expansions | string | query | Comma-separated list of expansion elements to include |
| page | string | query | Page number to retrieve. Default value is 1. |
| pagesize | string | query | The maximum number of schools on a page. This value cannot be greater than the maximum page size, which is also the default value. For more information, see Pagination Usage. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
schools {
  extensions (string, optional): Comma-separated list of schema extensions to the resource
  school (Array[v1.school], optional)
}

school {
  id (integer, optional): Universally unique ID of the school
  school_number (string, optional): The school number of the school
  name (string, optional): The school's name
  state_province_id (string, optional)
  low_grade (integer, optional): The lowest grade level that will be attending this school
  high_grade (integer, optional): The highest grade level that will be attending this school
  alternate_school_number (integer, optional): The school number of the school
  addresses (Array[v1.Physical], optional): Collection of school addresses
  phones (Array[v1.main], optional): Collection of school phone numbers
  principal (Array[v1.principal], optional): The school's principal
  assistant_principal (v1.assistant_principal, optional)
  school_boundary (Array[v1.schoolBoundaryPoints], optional): The encoded data for the boundary
}

Physical {
  street (string, optional): The school's street address
  city (string, optional): The city element of the school's address
  state_province (string, optional): The state/province element of the school's address
  postal_code (string, optional): The zip/postal code element of the school's address
}

main {
  v1.Number
}

principal {
  email (string, optional): The principal's email address
  name (v1.principalName, optional)
}

assistant_principal {
  email (string, optional): The assistant principal's email address
  name (v1.assistantPrincipalName, optional)
}

schoolBoundaryPoints {
  point (string, optional)
}

Number {
  number (string, optional)
}

principalName {
  first_name (string, optional): The principal's first name
  middle_name (string, optional): The principal's middle name
  last_name (string, optional): The principal's last name
}

assistantPrincipalName {
  first_name (string, optional): The assistant principal's first name
  middle_name (string, optional): The assistant principal's middle name
  last_name (string, optional): The assistant principal's last name
}
```

**Response Schema:**

```json
{
  "@expansions": "string",
  "@extensions": "string",
  "school": [
    {
      "id": 0,
      "school_number": "string",
      "name": "string",
      "state_province_id": "string",
      "low_grade": 0,
      "high_grade": 0,
      "alternate_school_number": 0,
      "addresses": [
        {
          "street": "string",
          "city": "string",
          "state_province": "string",
          "postal_code": "string"
        }
      ],
      "phones": [
        {
          "number": "string"
        }
      ],
      "principal": [
        {
          "email": "string",
          "name": {
            "first_name": "string",
            "middle_name": "string",
            "last_name": "string"
          }
        }
      ],
      "assistant_principal": {
        "email": "string",
        "name": {
          "first_name": "string",
          "middle_name": "string",
          "last_name": "string"
        }
      },
      "school_boundary": [
        {
          "point": "string"
        }
      ]
    }
  ]
}
```

### GET /ws/v1/section_enrollment/{id}

Get a section enrollment

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get a section enrollment by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Unique database identifier for section enrollment, CC.DCID |
| extensions | string | query | Comma-separated list of schema extensions to include |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
id {
  id (integer, optional): Equivalent to CC.DCID
  section_id (integer, optional): Equivalent to SECTIONS.DCID
  student_id (integer, optional): Equivalent to STUDENTS.DCID
  entry_date (integer, optional): Equivalent to CC.DATEENROLLED
  exit_date (integer, optional): Equivalent to CC.DATELEFT
  dropped (boolean, optional): True if the student dropped the class
}
```

**Response Schema:**

```json
{
  "id": 0,
  "section_id": 0,
  "student_id": 0,
  "entry_date": 0,
  "exit_date": 0,
  "dropped": true
}
```

### GET /ws/v1/section/{id}

Get a section

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get a section by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Unique database identifier for section, SECTIONS.DCID |
| expansions | string | query | Comma-separated list of expansions to include. Available expansions are: term, user-defined. |
| extensions | string | query | Comma-separated list of schema extensions to include |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
section {
  id (integer, optional): Equivalent to SECTIONS.DCID
  school_id (integer, optional): Equivalent to SCHOOLS.DCID
  course_id (integer, optional): Equivalent to COURSES.DCID
  staff_id (integer, optional): Equivalent to SCHOOLSTAFF.DCID
  term_id (integer, optional): Equivalent to TERMS.DCID
}
```

**Response Schema:**

```json
{
  "id": 0,
  "school_id": 0,
  "course_id": 0,
  "staff_id": 0,
  "term_id": 0,
  "section_number": "string",
  "expression": "string"
}
```

### GET /ws/v1/section/{id}/section_enrollment

Get student enrollment for a section

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get student enrollment for a section. The enrollments are sorted by student_id and entry_date.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Unique database identifier for section, SECTIONS.DCID |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
section_enrollments {
  section_enrollments (Array[v1.section.id.section_enrollment], optional)
}

section_enrollment {
  id (integer, optional): Equivalent to CC.DCID
  section_id (integer, optional): Equivalent to SECTIONS.DCID
  student_id (integer, optional): Equivalent to STUDENTS.DCID
  entry_date (integer, optional): Equivalent to CC.DATEENROLLED
  exit_date (integer, optional): Equivalent to CC.DATELEFT
  dropped (boolean, optional): True if the student dropped the class
}
```

**Response Schema:**

```json
{
  "section_enrollments": [
    {
      "id": 0,
      "section_id": 0,
      "student_id": 0,
      "entry_date": 0,
      "exit_date": 0,
      "dropped": true
    }
  ]
}
```

### GET /ws/v1/section/{id}/section_enrollment/count

Get student enrollment count for a section

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get student enrollment count for a section. The enrollments are sorted by student_id and entry_date.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Unique database identifier for section, SECTIONS.DCID |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
count {
  count (integer, optional): Row count
}
```

**Response Schema:**

```json
{
  "count": 0
}
```

### GET /ws/v1/staff/{id}

Get a staff record

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Return a staff record

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | double | path | Staff record ID |
| expansions | string | query | Comma-separated list of expansions to return |
| extensions | string | query | Comma-separated list of schema extensions to return |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
staff {
  extensions (string, optional): Comma-separated list of schema extensions to the resource
  local_id (string, optional): The teacher number assigned by the school
  admin_username (string, optional): The administrator's username for signing into PowerSchool
  teacher_username (string, optional): The teacher's username for signing into PowerTeacher
  name (Array[v1.staff_name], optional)
  addresses (Array[v1.staff_addresses], optional)
  emails (Array[v1.staff_emails], optional)
  phones (Array[v1.staff_phones], optional)
  school_affiliations (Array[v1.school_affiliations], optional)
  school_counselors (Array[v1.school_counselors], optional)
  teacher_global_id (string, optional): The identity provider global ID for teacher for signing into PowerSchool
  staff_global_id (string, optional): The identity provider global ID for admin for signing into PowerSchool
}

staff_name {
  first_name (string, optional): The staff member's first name
  middle_name (string, optional): The staff member's middle name
  last_name (string, optional): The staff member's last name
}

staff_addresses {
  home (v1.staff_address_home, optional)
}

staff_phones {
  home_phone (string, optional): The staff member's home phone number
}

school_affiliations {
  school_affiliation (v1.school_affiliation, optional)
}

school_counselors {
  school_counselor (v1.school_counselor, optional)
}

staff_address_home {
  street (string, optional): The staff member's street address
  city (string, optional): The city element of the staff member's address
  state_province (string, optional): The state/province element of the staff member's address
  postal_code (string, optional): The zip/postal code element of the staff member's address
}

school_affiliation {
  school_id (integer, optional): The ID of the school
}

school_counselor {
  school_id (integer, optional): The ID of the school
  counselor (boolean, optional): True if the staff has a counselor role.
}
```

**Response Schema:**

```json
{
  "@expansions": "string",
  "@extensions": "string",
  "id": 0,
  "local_id": "string",
  "admin_username": "string",
  "teacher_username": "string",
  "name": [
    {
      "first_name": "string",
      "middle_name": "string",
      "last_name": "string"
    }
  ],
  "addresses": [
    {
      "home": {
        "street": "string",
        "city": "string",
        "state_province": "string",
        "postal_code": "string"
      }
    }
  ],
  "emails": [
    null
  ],
  "phones": [
    {
      "home_phone": "string"
    }
  ],
  "school_affiliations": [
    {
      "school_affiliation": {
        "school_id": 0,
        "type": 0,
        "status": 0
      }
    }
  ],
  "school_counselors": [
    {
      "school_counselor": {
        "school_id": 0,
        "counselor": true
      }
    }
  ],
  "users_dcid": 0,
  "teacher_global_id": "string",
  "staff_global_id": "string"
}
```

### GET /ws/v1/student/{id}

Get a student by ID

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Endpoint returns a student record

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Student record's DCID |
| expansions | string | query | Comma-separated list of expansion elements to include |
| extensions | string | query | Comma-separated list of extension elements to include |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Forbidden | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
student {
  extensions (string, optional): Comma-separated list of schema extensions to the resource
  local_id (integer, optional): The student number assigned by the school
  student_username (string, optional)
  name (v1.student_name, optional)
  addresses (v1.student_addresses, optional)
  alerts (Array[v1.student_alerts], optional)
  phones (Array[v1.student_phones], optional)
  school_enrollment (Array[v1.student_school_enrollment], optional)
  ethnicity_race (Array[v1.student_ethnicity_race], optional)
  contact (v1.student_contact, optional)
  contact_info (v1.student_contact_info, optional)
  initial_enrollment (v1.student_initial_enrollment, optional)
  schedule_setup (v1.student_schedule_setup, optional)
  fees (v1.student_fees, optional)
  lunch (v1.student_lunch, optional)
  counselors (v1.student_counselors, optional)
  global_id (string, optional): The identity provider global ID for students for signing into PowerSchool
}

student_name {
  first_name (string, optional): The student's first name
  middle_name (string, optional): The student's middle name
  last_name (string, optional): The student's last name
}

student_addresses {
  physical (v1.student_address_physical, optional)
  mailing (v1.student_address_mailing, optional)
}

student_alerts {
  legal (v1.student_alert_legal, optional)
  discipline (v1.student_alert_discipline, optional)
  medical (v1.student_alert_medical, optional)
  other (v1.student_alert_other, optional)
}

student_phones {
  main (v1.student_phone_main, optional)
}

student_school_enrollment {
  status_code (integer
  optional): The student's enrollment status. Valid values: 0=Active
  -1=Pre-Registered
  2=Transferred-Out
  3=Graduated
  4=Historical
  Any other integer=Inactive
  enroll_status (string
  optional): The student's enrollment status. Valid values: A=Active
  P=Pre-Registered
  T=Transferred-Out
  G=Graduated
  H=Historical
  I=Inactive.
  enroll_status_description (string
  optional): The student's enrollment status description. This field is a textual representation of the enroll_status. Status 0 has description Active
  -1=Pre-Registered
  2=Transferred-Out
  3=Graduated
  4=Historical
  Any other integer=Inactive.
  grade_level (string
  optional): The grade the student is in. Valid values: {-1
  -2
  etc.
}

student_ethnicity_race {
  scheduling_reporting_ethnicity (string, optional): The student's heritage background
  federal_ethnicity (string, optional): Is the student Hispanic or Latino?
  federal_race_decline_indicator (string, optional): The student may decline to state their race. Can only have the value DECLINE_TO_SPECIFY.
  races (Array[v1.student_ethnicity_race_races], optional)
}

student_contact {
  emergency_contact_name1 (string, optional): The student's emergency contact
  emergency_phone1 (string, optional): The phone number of the student's emergency contact
  emergency_contact_name2 (string, optional): The student's emergency contact
  emergency_phone2 (string, optional): The phone number of the student's emergency contact
  guardian_fax (string, optional): The fax number of student's guardian
  guardian_email (string, optional): The email of student's guardian
  mother (string, optional): The name of student's mother
  father (string, optional): The name of student's father
  doctor_name (string, optional): The name of student's doctor
  doctor_phone (string, optional): The phone number of student's doctor
}

student_contact_info {
  email (string, optional): The student's email contact
}

student_initial_enrollment {
  district_entry_date (string, optional): The student's district entry date
  district_entry_grade_level (integer, optional): The student's district entry grade level
  school_entry_date (string, optional): The student's school entry date
  school_entry_grade_level (integer, optional): The student's school entry grade level
}

student_schedule_setup {
  home_room (string, optional): The student's homeroom
  next_school (integer, optional): The school the student is going to go to next year
  sched_next_year_grade (integer, optional): The grade level the student is going to be in next year
}

student_fees {
  fee (Array[v1.student_fee], optional)
}

student_lunch {
  id (integer, optional): The student's lunch ID
  balance1 (number, optional): The student's current lunch account balance
  balance2 (number, optional): The student's previous lunch account balance
  balance3 (number, optional): The student's lunch account balance
  balance4 (number, optional): The student's lunch account balance
  last_meal (string, optional): The student's last meal
}

student_counselors {
  counselor (Array[v1.student_counselor], optional)
}

student_address_physical {
  street (string, optional): The student's street address
  city (string, optional): The city element of the student's address
  state_province (string, optional): The state/province element of the student's address
  postal_code (string, optional): The zip/postal code element of the student's address
  grid_location (string, optional): The latitude/longitude coordinates of the student's physical address
}

student_address_mailing {
  street (string, optional): The student's mailing street address
  city (string, optional): The city element of the student's mailing address
  state_province (string, optional): The state/province element of the student's mailing address
  postal_code (string, optional): The zip/postal code element of the student's mailing address
  grid_location (string, optional): The latitude/longitude coordinates of the student's mailing address
}

student_alert_legal {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

student_alert_discipline {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

student_alert_medical {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

student_alert_other {
  description (string, optional): One of many various alerts in PowerSchool. This field stores the text associated to the alert.
  expires_date (string, optional): One of many various alerts in PowerSchool. This field stores the expiration date associated to the alert.
}

student_phone_main {
  number (string, optional): Student's main phone number
}

student_full_time_equivelancy {
  fteid (integer, optional): The student's full-time equivalency ID
  name (string, optional): The student's full-time equivalency associated name
}

student_ethnicity_race_races {
  district_race_code (string, optional): The student's race code
  district_race_code_dsescription (string, optional): The description of the race code
  federal_race_code_category (string, optional): The federal race category associated to the race code
}

student_fee {
  id (integer, optional): The fee ID
  fee_amount (number, optional): The fee amount
  fee_balance (number, optional): The fee balance formatted as #.##.
  fee_dcscription (string, optional): The fee description
  date_created (string, optional): The date the fee was created formatted as YYYY-MM-DD
  date_modified (string, optional): The date the fee was last modified formatted as YYYY-MM-DD
  transaction_date (string, optional): The date of the transaction formatted as YYYY-MM-DD
  department_name (string, optional): The name of the departement
  priority (number, optional): The fee priority order
  pro_ratable_indicator (number, optional): The fee pro-rated indicator
  group_transaction_id (number, optional): The fee group transaction ID
  school_id (number, optional): The school ID for the fee
  school_fee_id (number, optional): The school fee ID for the fee
  term_id (number, optional): The term ID
  year_id (number, optional): The year ID
  course_name (string, optional): The course name
  course_number (integer, optional): The course number
  category_name (string, optional): The fee category name
  type_id (number, optional): The fee type ID
  type_name (string, optional): The fee type name
  fee_transaction (v1.student_fee_transaction, optional)
}

student_counselor {
  id (integer, optional): The student counselor ID
  userDcid (integer, optional): The dcid of the user
  firstName (string, optional): The first name of the counselor
  lastName (string, optional): The last name of the counselor
  isPrimary (boolean, optional): True if the this is the primary counselor for the student.
}

student_fee_transaction {
  id (number, optional): The fee transaction ID
  transaction_amount (number, optional): The fee transaction amount formatted as #.##
  global_starting_balance (number, optional): The fee global starting balance formatted as #.##
  transaction_date (string, optional): The fee transaction date formatted as YYYY-MM-DD
  transaction_description (string, optional): The fee transaction description
  group_transaction_id (number, optional): The fee transaction group ID
  payment_method (string, optional): The fee transaction payment method
  school_id (number, optional): The school ID for the fee
  year_id (number, optional): The year ID
  starting_balance (number, optional): The fee transaction starting balance formatted as #.##
  global_net_balance (number, optional): The fee transaction global net balance formatted as #.##
  transaction_type (string, optional): The fee transaction type
  payment_reference_number (number, optional): The payment reference number
}
```

**Response Schema:**

```json
{
  "@expansions": "string",
  "@extensions": "string",
  "id": 0,
  "local_id": 0,
  "state_province_id": "string",
  "student_username": "string",
  "name": {
    "first_name": "string",
    "middle_name": "string",
    "last_name": "string"
  },
  "addresses": {
    "physical": {
      "street": "string",
      "city": "string",
      "state_province": "string",
      "postal_code": "string",
      "grid_location": "string"
    },
    "mailing": {
      "street": "string",
      "city": "string",
      "state_province": "string",
      "postal_code": "string",
      "grid_location": "string"
    }
  },
  "alerts": [
    {
      "legal": {
        "description": "string",
        "expires_date": "string"
      },
      "discipline": {
        "description": "string",
        "expires_date": "string"
      },
      "medical": {
        "description": "string",
        "expires_date": "string"
      },
      "other": {
        "description": "string",
        "expires_date": "string"
      }
    }
  ],
  "phones": [
    {
      "main": {
        "number": "string"
      }
    }
  ],
  "school_enrollment": [
    {
      "status_code": 0,
      "enroll_status": "string",
      "enroll_status_description": "string",
      "grade_level": "string",
      "entry_date": "string",
      "exit_date": "string",
      "school_number": 0,
      "entry_code": "string",
      "entry_comment": "string",
      "exit_code": "string",
      "exit_comment": "string",
      "district_of_residence": "string",
      "track": "string",
      "full_time_equivelancy": [
        {
          "fteid": 0,
          "name": "string"
        }
      ]
    }
  ],
  "ethnicity_race": [
    {
      "scheduling_reporting_ethnicity": "string",
      "federal_ethnicity": "string",
      "federal_race_decline_indicator": "string",
      "races": [
        {
          "district_race_code": "string",
          "district_race_code_dsescription": "string",
          "federal_race_code_category": "string"
        }
      ]
    }
  ],
  "contact": {
    "emergency_contact_name1": "string",
    "emergency_phone1": "string",
    "emergency_contact_name2": "string",
    "emergency_phone2": "string",
    "guardian_fax": "string",
    "guardian_email": "string",
    "mother": "string",
    "father": "string",
    "doctor_name": "string",
    "doctor_phone": "string"
  },
  "contact_info": {
    "email": "string"
  },
  "initial_enrollment": {
    "district_entry_date": "string",
    "district_entry_grade_level": 0,
    "school_entry_date": "string",
    "school_entry_grade_level": 0
  },
  "schedule_setup": {
    "home_room": "string",
    "next_school": 0,
    "sched_next_year_grade": 0
  },
  "fees": {
    "fee": [
      {
        "id": 0,
        "fee_amount": 0,
        "fee_balance": 0,
        "fee_dcscription": "string",
        "date_created": "string",
        "date_modified": "string",
        "transaction_date": "string",
        "department_name": "string",
        "priority": 0,
        "pro_ratable_indicator": 0,
        "group_transaction_id": 0,
        "school_id": 0,
        "school_fee_id": 0,
        "term_id": 0,
        "year_id": 0,
        "course_name": "string",
        "course_number": 0,
        "category_name": "string",
        "type_id": 0,
        "type_name": "string",
        "fee_transaction": {
          "id": 0,
          "transaction_amount": 0,
          "global_starting_balance": 0,
          "transaction_date": "string",
          "transaction_description": "string",
          "group_transaction_id": 0,
          "payment_method": "string",
          "school_id": 0,
          "year_id": 0,
          "starting_balance": 0,
          "global_net_balance": 0,
          "transaction_type": "string",
          "payment_reference_number": 0
        }
      }
    ]
  },
  "lunch": {
    "id": 0,
    "balance1": 0,
    "balance2": 0,
    "balance3": 0,
    "balance4": 0,
    "last_meal": "string"
  },
  "counselors": {
    "counselor": [
      {
        "id": 0,
        "userDcid": 0,
        "firstName": "string",
        "lastName": "string",
        "isPrimary": true
      }
    ]
  },
  "global_id": "string"
}
```

### GET /ws/v1/term/{id}

Get a term

| Property | Value |
|----------|-------|
| Available Since | 7.8.0 |
| Accessible To | PLUGINS |

#### Description

Get a term by ID

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| id | integer | path | Unique database identifier for terms, TERMS.DCID |
| extensions | string | query | Comma-separated list of schema extensions to include |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 403 | Insufficient permission | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
term {
  id (string, optional): Equivalent to TERMS.DCID
  school_id (string, optional): Equivalent to SCHOOLS.DCID
  start_year (string, optional): Starting year for the school year
  portion (integer, optional): Portion for the term
  start_date (string, optional): Starting date for the term
  end_date (string, optional): Ending date for the term
  abbreviation (string, optional): Term abbreviation
  name (string, optional): Term name
}
```

**Response Schema:**

```json
{
  "id": "string",
  "school_id": "string",
  "start_year": "string",
  "portion": 0,
  "start_date": "2025-10-29",
  "end_date": "2025-10-29",
  "abbreviation": "string",
  "name": "string"
}
```
