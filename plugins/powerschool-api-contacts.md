
# PowerSchool CONTACTS API

## contacts

### GET /ws/contacts/{contactid}/addresses

Get contact addresses by contactid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact address records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which address records to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactsAddressId": 0,
  "sequence": 0,
  "addressId": 0,
  "addressType": "string",
  "street": "string",
  "linetwo": "string",
  "unit": "string",
  "city": "string",
  "state": 0,
  "country": 0,
  "postalcode": "string",
  "startDate": "2025-10-29",
  "endDate": "2025-10-29",
  "contactAddressAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### POST /ws/contacts/{contactid}/addresses

Insert a new contact address.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save new contact address record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which address record to add. |
| contactAddress | contactAddress | body | Contact address record to insert |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactid}/addresses/{contactaddressid}

Delete a contact address.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Delete a contactaddress by contact ID and contact address id.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact. |
| contactaddressid | integer | path | ID of the contact address for which address record to be deleted. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
deleted {
  action (string, optional): Always DELETE
  _success_message (contact.deleted.success, optional)
  _error_message (contact.deleted.errorMessage, optional)
}

success {
  Id (integer, optional): Contact ID
  _success (contact.deleted.success.array, optional): TBD
  ref (string, optional): Always /ws/contacts/
}

errorMessage {
  _error (Array[contact.deleted.error], optional)
}

error {
  field (string, optional): Operation - Delete Contact
  error_code (string, optional)
  error_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "string",
  "_success_message": {
    "Id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_error": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  }
}
```

### GET /ws/contacts/{contactid}/addresses/{contactaddressid}

Get contact address by contactid and contactaddressid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact address record for a contactid and contactaddressid.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which address record to retrieve. |
| contactaddressid | integer | path | ID of the contact address for which address record to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactsAddressId": 0,
  "sequence": 0,
  "addressId": 0,
  "addressType": "string",
  "street": "string",
  "linetwo": "string",
  "unit": "string",
  "city": "string",
  "state": 0,
  "country": 0,
  "postalcode": "string",
  "startDate": "2025-10-29",
  "endDate": "2025-10-29",
  "contactAddressAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### PUT /ws/contacts/{contactid}/addresses/{contactaddressid}

Update a contact address

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save contactaddress record

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which address record to update. |
| contactaddressid | integer | path | ID of the contact address for which address record to update. |
| contactAddress | contactAddress | body | Contact address record to update. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/demographics

Gets top level contact information. Contact child elements will not be included in the response.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns the name, gender, employer values plus the exclude from state reporting and active boolean values.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contact {
  contactId (integer)
  firstName (string, optional)
  middleName (string, optional)
  lastName (string, optional)
  prefix (string, optional): Codeset code where CodeType 'Prefix'
  suffix (string, optional): Codeset code where CodeType 'Suffix'
  gender (string, optional): Codeset code where CodeType = 'Gender'
  employer (string, optional)
  stateContactNumber (string, optional)
  contactNumber (string, optional)
  stateExcludeFromReporting (boolean, optional)
  active (boolean, optional)
  emails (Array[contactEmail], optional)
  phones (Array[contactPhone], optional)
  languages (Array[contact.language], optional): Field unused at this time
  contactAccount (contactAccount, optional)
  addresses (Array[contactAddress], optional)
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactAccount {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  enabled (boolean, optional): Is account enabled
  userName (string, optional): Users sign in ID
  password (string, optional): Always 'null' for security reasons
  extensions (Array[contact.extension], optional)
}

contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

extension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "contactId": 0,
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "prefix": "string",
  "suffix": "string",
  "gender": "string",
  "employer": "string",
  "stateContactNumber": "string",
  "contactNumber": "string",
  "stateExcludeFromReporting": true,
  "active": true,
  "emails": [
    {
      "deleted": false,
      "contactEmailId": 0,
      "primary": true,
      "emailId": 0,
      "type": "string",
      "address": "string",
      "contactEmailAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "phones": [
    {
      "deleted": false,
      "contactsPhoneId": 0,
      "sequence": 0,
      "preferred": true,
      "phoneType": "string",
      "phoneNumberId": 0,
      "phoneNumber": "string",
      "extension": "string",
      "sms": true,
      "contactPhoneAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "languages": [
    null
  ],
  "contactAccount": {
    "deleted": false,
    "enabled": true,
    "userName": "string",
    "password": "string",
    "extensions": [
      {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    ]
  },
  "addresses": [
    {
      "deleted": false,
      "contactsAddressId": 0,
      "sequence": 0,
      "addressId": 0,
      "addressType": "string",
      "street": "string",
      "linetwo": "string",
      "unit": "string",
      "city": "string",
      "state": 0,
      "country": 0,
      "postalcode": "string",
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "contactAddressAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "contactStudents": [
    {
      "deleted": false,
      "studentContactId": 0,
      "sequence": 0,
      "dcid": 0,
      "studentNumber": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "schoolAbbr": "string",
      "schoolNumber": 0,
      "originalContactType": "string",
      "autosendHowOften": 0,
      "emailSummary": true,
      "assignmentDetails": true,
      "attendanceDetails": true,
      "schoolAnnouncements": true,
      "balanceAlert": true,
      "guardianId": 0,
      "canAccessData": true,
      "restrictions": [
        {
          "restrictionId": 0,
          "pluginDefId": 0,
          "pluginName": "string",
          "guardianStudentId": 0,
          "restricted": true
        }
      ],
      "notificationEmails": "string",
      "contactStudentAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      },
      "studentDetails": [
        {
          "deleted": false,
          "studentContactDetailId": 0,
          "studentContactId": 0,
          "relationship": "string",
          "relationshipNote": "string",
          "custodial": true,
          "emergency": true,
          "livesWith": true,
          "schoolPickup": true,
          "startDate": "2025-10-29",
          "endDate": "2025-10-29",
          "receivesMail": true,
          "excludeFromStateReporting": true,
          "active": true,
          "contactStudentDetailExtension": {
            "id": 0,
            "@extensions": "",
            "_extension_data": {
              "_table_extension": [
                {
                  "name": "string",
                  "_field": [
                    {
                      "name": "string",
                      "type": "string",
                      "value": "string"
                    }
                  ]
                }
              ]
            }
          }
        }
      ]
    }
  ],
  "@extensions": "",
  "_extension_data": {
    "_table_extension": [
      {
        "name": "string",
        "_field": [
          {
            "name": "string",
            "type": "string",
            "value": "string"
          }
        ]
      }
    ]
  }
}
```

### PUT /ws/contacts/{contactid}/demographics

Updates top level contact information. Contact child elements will be not be updated.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Updates the name, gender, employer values plus the exclude from state reporting and active boolean values.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contact | contact | body | Contact record to update. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contact {
  contactId (integer)
  firstName (string, optional)
  middleName (string, optional)
  lastName (string, optional)
  prefix (string, optional): Codeset code where CodeType 'Prefix'
  suffix (string, optional): Codeset code where CodeType 'Suffix'
  gender (string, optional): Codeset code where CodeType = 'Gender'
  employer (string, optional)
  stateContactNumber (string, optional)
  contactNumber (string, optional)
  stateExcludeFromReporting (boolean, optional)
  active (boolean, optional)
  emails (Array[contactEmail], optional)
  phones (Array[contactPhone], optional)
  languages (Array[contact.language], optional): Field unused at this time
  contactAccount (contactAccount, optional)
  addresses (Array[contactAddress], optional)
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactAccount {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  enabled (boolean, optional): Is account enabled
  userName (string, optional): Users sign in ID
  password (string, optional): Always 'null' for security reasons
  extensions (Array[contact.extension], optional)
}

contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

extension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "contactId": 0,
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "prefix": "string",
  "suffix": "string",
  "gender": "string",
  "employer": "string",
  "stateContactNumber": "string",
  "contactNumber": "string",
  "stateExcludeFromReporting": true,
  "active": true,
  "emails": [
    {
      "deleted": false,
      "contactEmailId": 0,
      "primary": true,
      "emailId": 0,
      "type": "string",
      "address": "string",
      "contactEmailAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "phones": [
    {
      "deleted": false,
      "contactsPhoneId": 0,
      "sequence": 0,
      "preferred": true,
      "phoneType": "string",
      "phoneNumberId": 0,
      "phoneNumber": "string",
      "extension": "string",
      "sms": true,
      "contactPhoneAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "languages": [
    null
  ],
  "contactAccount": {
    "deleted": false,
    "enabled": true,
    "userName": "string",
    "password": "string",
    "extensions": [
      {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    ]
  },
  "addresses": [
    {
      "deleted": false,
      "contactsAddressId": 0,
      "sequence": 0,
      "addressId": 0,
      "addressType": "string",
      "street": "string",
      "linetwo": "string",
      "unit": "string",
      "city": "string",
      "state": 0,
      "country": 0,
      "postalcode": "string",
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "contactAddressAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "contactStudents": [
    {
      "deleted": false,
      "studentContactId": 0,
      "sequence": 0,
      "dcid": 0,
      "studentNumber": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "schoolAbbr": "string",
      "schoolNumber": 0,
      "originalContactType": "string",
      "autosendHowOften": 0,
      "emailSummary": true,
      "assignmentDetails": true,
      "attendanceDetails": true,
      "schoolAnnouncements": true,
      "balanceAlert": true,
      "guardianId": 0,
      "canAccessData": true,
      "restrictions": [
        {
          "restrictionId": 0,
          "pluginDefId": 0,
          "pluginName": "string",
          "guardianStudentId": 0,
          "restricted": true
        }
      ],
      "notificationEmails": "string",
      "contactStudentAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      },
      "studentDetails": [
        {
          "deleted": false,
          "studentContactDetailId": 0,
          "studentContactId": 0,
          "relationship": "string",
          "relationshipNote": "string",
          "custodial": true,
          "emergency": true,
          "livesWith": true,
          "schoolPickup": true,
          "startDate": "2025-10-29",
          "endDate": "2025-10-29",
          "receivesMail": true,
          "excludeFromStateReporting": true,
          "active": true,
          "contactStudentDetailExtension": {
            "id": 0,
            "@extensions": "",
            "_extension_data": {
              "_table_extension": [
                {
                  "name": "string",
                  "_field": [
                    {
                      "name": "string",
                      "type": "string",
                      "value": "string"
                    }
                  ]
                }
              ]
            }
          }
        }
      ]
    }
  ],
  "@extensions": "",
  "_extension_data": {
    "_table_extension": [
      {
        "name": "string",
        "_field": [
          {
            "name": "string",
            "type": "string",
            "value": "string"
          }
        ]
      }
    ]
  }
}
```

### GET /ws/contacts/{contactid}/emails

Get contact emails by contactid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact email records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which email records to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactEmailId": 0,
  "primary": true,
  "emailId": 0,
  "type": "string",
  "address": "string",
  "contactEmailAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### POST /ws/contacts/{contactid}/emails

Insert a new contact email

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save new contact email record

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which email record to add. |
| contactEmail | contactEmail | body | Contact email record to insert |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactid}/emails/{contactemailid}

Delete a contact email address.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Delete a contact email address by contact ID and contact email address id.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact. |
| contactemailid | integer | path | ID of the contact email address for which email record to be deleted. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
deleted {
  action (string, optional): Always DELETE
  _success_message (contact.deleted.success, optional)
  _error_message (contact.deleted.errorMessage, optional)
}

success {
  Id (integer, optional): Contact ID
  _success (contact.deleted.success.array, optional): TBD
  ref (string, optional): Always /ws/contacts/
}

errorMessage {
  _error (Array[contact.deleted.error], optional)
}

error {
  field (string, optional): Operation - Delete Contact
  error_code (string, optional)
  error_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "string",
  "_success_message": {
    "Id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_error": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  }
}
```

### GET /ws/contacts/{contactid}/emails/{contactemailid}

Get contact email by contactid and contactemailid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact email record for a contactid and contactphoneid.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which email record to retrieve. |
| contactemailid | integer | path | ID of the contact email for which email record to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactEmailId": 0,
  "primary": true,
  "emailId": 0,
  "type": "string",
  "address": "string",
  "contactEmailAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### PUT /ws/contacts/{contactid}/emails/{contactemailid}

Update a contact email.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save contact email record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | ID of the contact for which email record to update. |
| contactemailid | integer | path | ID of the contact email for which email record to update. |
| contactEmail | contactEmail | body | Contact email record to update. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/phones

Gets a list of all phone numbers for a contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns all contact phone numbers.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactsPhoneId": 0,
  "sequence": 0,
  "preferred": true,
  "phoneType": "string",
  "phoneNumberId": 0,
  "phoneNumber": "string",
  "extension": "string",
  "sms": true,
  "contactPhoneAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### POST /ws/contacts/{contactid}/phones

Add a phone number to a contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save new contact phone number.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactStudent | contactPhone | body | Contact student relationship to create. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactid}/phones/{contactphoneid}

Deletes a single contact phone number.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Deletes a single student contact phone number association.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactphoneid | integer | path | The ID of the student contact association. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/phones/{contactphoneid}

Gets a single contact phone number.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns a single phone number from a contact.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactphoneid | integer | path | The ID of the contact phone number association. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "contactsPhoneId": 0,
  "sequence": 0,
  "preferred": true,
  "phoneType": "string",
  "phoneNumberId": 0,
  "phoneNumber": "string",
  "extension": "string",
  "sms": true,
  "contactPhoneAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### PUT /ws/contacts/{contactid}/phones/{contactphoneid}

Update a student phone number.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save changes to an existing student phone number association.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactphoneid | integer | path | The ID of the student contact association. |
| contactPhone | contactPhone | body | Modified student contact association. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactId}

Delete a contact

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Delete a contact by contact ID.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactId | long | path | ID of the contact to delete. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
deleted {
  action (string, optional): Always DELETE
  _success_message (contact.deleted.success, optional)
  _error_message (contact.deleted.errorMessage, optional)
}

success {
  Id (integer, optional): Contact ID
  _success (contact.deleted.success.array, optional): TBD
  ref (string, optional): Always /ws/contacts/
}

errorMessage {
  _error (Array[contact.deleted.error], optional)
}

error {
  field (string, optional): Operation - Delete Contact
  error_code (string, optional)
  error_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "string",
  "_success_message": {
    "Id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_error": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  }
}
```

### POST /ws/contacts/contact

Insert a new contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | PLUGINS |

#### Description

Save new contact record. Creation of access account for contact is not supported.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contact | contact | body | Contact record to insert. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/contact/{contactId}

Get contact by contactid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactId | integer | path | ID of the contact record to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contact {
  contactId (integer)
  firstName (string, optional)
  middleName (string, optional)
  lastName (string, optional)
  prefix (string, optional): Codeset code where CodeType 'Prefix'
  suffix (string, optional): Codeset code where CodeType 'Suffix'
  gender (string, optional): Codeset code where CodeType = 'Gender'
  employer (string, optional)
  stateContactNumber (string, optional)
  contactNumber (string, optional)
  stateExcludeFromReporting (boolean, optional)
  active (boolean, optional)
  emails (Array[contactEmail], optional)
  phones (Array[contactPhone], optional)
  languages (Array[contact.language], optional): Field unused at this time
  contactAccount (contactAccount, optional)
  addresses (Array[contactAddress], optional)
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactAccount {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  enabled (boolean, optional): Is account enabled
  userName (string, optional): Users sign in ID
  password (string, optional): Always 'null' for security reasons
  extensions (Array[contact.extension], optional)
}

contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

extension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "contactId": 0,
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "prefix": "string",
  "suffix": "string",
  "gender": "string",
  "employer": "string",
  "stateContactNumber": "string",
  "contactNumber": "string",
  "stateExcludeFromReporting": true,
  "active": true,
  "emails": [
    {
      "deleted": false,
      "contactEmailId": 0,
      "primary": true,
      "emailId": 0,
      "type": "string",
      "address": "string",
      "contactEmailAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "phones": [
    {
      "deleted": false,
      "contactsPhoneId": 0,
      "sequence": 0,
      "preferred": true,
      "phoneType": "string",
      "phoneNumberId": 0,
      "phoneNumber": "string",
      "extension": "string",
      "sms": true,
      "contactPhoneAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "languages": [
    null
  ],
  "contactAccount": {
    "deleted": false,
    "enabled": true,
    "userName": "string",
    "password": "string",
    "extensions": [
      {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    ]
  },
  "addresses": [
    {
      "deleted": false,
      "contactsAddressId": 0,
      "sequence": 0,
      "addressId": 0,
      "addressType": "string",
      "street": "string",
      "linetwo": "string",
      "unit": "string",
      "city": "string",
      "state": 0,
      "country": 0,
      "postalcode": "string",
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "contactAddressAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "contactStudents": [
    {
      "deleted": false,
      "studentContactId": 0,
      "sequence": 0,
      "dcid": 0,
      "studentNumber": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "schoolAbbr": "string",
      "schoolNumber": 0,
      "originalContactType": "string",
      "autosendHowOften": 0,
      "emailSummary": true,
      "assignmentDetails": true,
      "attendanceDetails": true,
      "schoolAnnouncements": true,
      "balanceAlert": true,
      "guardianId": 0,
      "canAccessData": true,
      "restrictions": [
        {
          "restrictionId": 0,
          "pluginDefId": 0,
          "pluginName": "string",
          "guardianStudentId": 0,
          "restricted": true
        }
      ],
      "notificationEmails": "string",
      "contactStudentAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      },
      "studentDetails": [
        {
          "deleted": false,
          "studentContactDetailId": 0,
          "studentContactId": 0,
          "relationship": "string",
          "relationshipNote": "string",
          "custodial": true,
          "emergency": true,
          "livesWith": true,
          "schoolPickup": true,
          "startDate": "2025-10-29",
          "endDate": "2025-10-29",
          "receivesMail": true,
          "excludeFromStateReporting": true,
          "active": true,
          "contactStudentDetailExtension": {
            "id": 0,
            "@extensions": "",
            "_extension_data": {
              "_table_extension": [
                {
                  "name": "string",
                  "_field": [
                    {
                      "name": "string",
                      "type": "string",
                      "value": "string"
                    }
                  ]
                }
              ]
            }
          }
        }
      ]
    }
  ],
  "@extensions": "",
  "_extension_data": {
    "_table_extension": [
      {
        "name": "string",
        "_field": [
          {
            "name": "string",
            "type": "string",
            "value": "string"
          }
        ]
      }
    ]
  }
}
```

### GET /ws/contacts/contacts

Get contacts by contactIds.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Get contact records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactids | Array[integer] | query | A list of ID of the contacts to retrieve. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contact {
  contactId (integer)
  firstName (string, optional)
  middleName (string, optional)
  lastName (string, optional)
  prefix (string, optional): Codeset code where CodeType 'Prefix'
  suffix (string, optional): Codeset code where CodeType 'Suffix'
  gender (string, optional): Codeset code where CodeType = 'Gender'
  employer (string, optional)
  stateContactNumber (string, optional)
  contactNumber (string, optional)
  stateExcludeFromReporting (boolean, optional)
  active (boolean, optional)
  emails (Array[contactEmail], optional)
  phones (Array[contactPhone], optional)
  languages (Array[contact.language], optional): Field unused at this time
  contactAccount (contactAccount, optional)
  addresses (Array[contactAddress], optional)
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactAccount {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  enabled (boolean, optional): Is account enabled
  userName (string, optional): Users sign in ID
  password (string, optional): Always 'null' for security reasons
  extensions (Array[contact.extension], optional)
}

contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

extension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "contactId": 0,
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "prefix": "string",
  "suffix": "string",
  "gender": "string",
  "employer": "string",
  "stateContactNumber": "string",
  "contactNumber": "string",
  "stateExcludeFromReporting": true,
  "active": true,
  "emails": [
    {
      "deleted": false,
      "contactEmailId": 0,
      "primary": true,
      "emailId": 0,
      "type": "string",
      "address": "string",
      "contactEmailAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "phones": [
    {
      "deleted": false,
      "contactsPhoneId": 0,
      "sequence": 0,
      "preferred": true,
      "phoneType": "string",
      "phoneNumberId": 0,
      "phoneNumber": "string",
      "extension": "string",
      "sms": true,
      "contactPhoneAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "languages": [
    null
  ],
  "contactAccount": {
    "deleted": false,
    "enabled": true,
    "userName": "string",
    "password": "string",
    "extensions": [
      {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    ]
  },
  "addresses": [
    {
      "deleted": false,
      "contactsAddressId": 0,
      "sequence": 0,
      "addressId": 0,
      "addressType": "string",
      "street": "string",
      "linetwo": "string",
      "unit": "string",
      "city": "string",
      "state": 0,
      "country": 0,
      "postalcode": "string",
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "contactAddressAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "contactStudents": [
    {
      "deleted": false,
      "studentContactId": 0,
      "sequence": 0,
      "dcid": 0,
      "studentNumber": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "schoolAbbr": "string",
      "schoolNumber": 0,
      "originalContactType": "string",
      "autosendHowOften": 0,
      "emailSummary": true,
      "assignmentDetails": true,
      "attendanceDetails": true,
      "schoolAnnouncements": true,
      "balanceAlert": true,
      "guardianId": 0,
      "canAccessData": true,
      "restrictions": [
        {
          "restrictionId": 0,
          "pluginDefId": 0,
          "pluginName": "string",
          "guardianStudentId": 0,
          "restricted": true
        }
      ],
      "notificationEmails": "string",
      "contactStudentAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      },
      "studentDetails": [
        {
          "deleted": false,
          "studentContactDetailId": 0,
          "studentContactId": 0,
          "relationship": "string",
          "relationshipNote": "string",
          "custodial": true,
          "emergency": true,
          "livesWith": true,
          "schoolPickup": true,
          "startDate": "2025-10-29",
          "endDate": "2025-10-29",
          "receivesMail": true,
          "excludeFromStateReporting": true,
          "active": true,
          "contactStudentDetailExtension": {
            "id": 0,
            "@extensions": "",
            "_extension_data": {
              "_table_extension": [
                {
                  "name": "string",
                  "_field": [
                    {
                      "name": "string",
                      "type": "string",
                      "value": "string"
                    }
                  ]
                }
              ]
            }
          }
        }
      ]
    }
  ],
  "@extensions": "",
  "_extension_data": {
    "_table_extension": [
      {
        "name": "string",
        "_field": [
          {
            "name": "string",
            "type": "string",
            "value": "string"
          }
        ]
      }
    ]
  }
}
```

### GET /ws/contacts/student/original_contact_types/in_use/{studentdcid}

Gets a list of each of the six original contact types that are already in use for the specified student.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns each original contact type that is already associated with a contact for the student.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| studentdcid | integer | path | The DCID of the student. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
Inline Model [string]
```

**Response Schema:**

```json
"string"
```

### GET /ws/contacts/{contactid}/students

Gets a list of all contact student associations for a contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns all student contact associations plus the list of student contact details for each of them.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "studentContactId": 0,
  "sequence": 0,
  "dcid": 0,
  "studentNumber": "string",
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "schoolAbbr": "string",
  "schoolNumber": 0,
  "originalContactType": "string",
  "autosendHowOften": 0,
  "emailSummary": true,
  "assignmentDetails": true,
  "attendanceDetails": true,
  "schoolAnnouncements": true,
  "balanceAlert": true,
  "guardianId": 0,
  "canAccessData": true,
  "restrictions": [
    {
      "restrictionId": 0,
      "pluginDefId": 0,
      "pluginName": "string",
      "guardianStudentId": 0,
      "restricted": true
    }
  ],
  "notificationEmails": "string",
  "contactStudentAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  },
  "studentDetails": [
    {
      "deleted": false,
      "studentContactDetailId": 0,
      "studentContactId": 0,
      "relationship": "string",
      "relationshipNote": "string",
      "custodial": true,
      "emergency": true,
      "livesWith": true,
      "schoolPickup": true,
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "receivesMail": true,
      "excludeFromStateReporting": true,
      "active": true,
      "contactStudentDetailExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ]
}
```

### POST /ws/contacts/{contactid}/students

Add a student to a contact. Student contact details can be included but must not contain overlapping date ranges. If no details are specified, one will be created using default values.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save new student contact association.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactStudent | contactStudent | body | Contact student relationship to create. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactid}/students/{contactstudentid}

Deletes a single contact student associations for a contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Deletes a single student contact association and any associated student contact details.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/students/{contactstudentid}

Gets a single contact student association for a contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns a single student contact association plus the list of student contact details.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "studentContactId": 0,
  "sequence": 0,
  "dcid": 0,
  "studentNumber": "string",
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "schoolAbbr": "string",
  "schoolNumber": 0,
  "originalContactType": "string",
  "autosendHowOften": 0,
  "emailSummary": true,
  "assignmentDetails": true,
  "attendanceDetails": true,
  "schoolAnnouncements": true,
  "balanceAlert": true,
  "guardianId": 0,
  "canAccessData": true,
  "restrictions": [
    {
      "restrictionId": 0,
      "pluginDefId": 0,
      "pluginName": "string",
      "guardianStudentId": 0,
      "restricted": true
    }
  ],
  "notificationEmails": "string",
  "contactStudentAssocExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  },
  "studentDetails": [
    {
      "deleted": false,
      "studentContactDetailId": 0,
      "studentContactId": 0,
      "relationship": "string",
      "relationshipNote": "string",
      "custodial": true,
      "emergency": true,
      "livesWith": true,
      "schoolPickup": true,
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "receivesMail": true,
      "excludeFromStateReporting": true,
      "active": true,
      "contactStudentDetailExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ]
}
```

### PUT /ws/contacts/{contactid}/students/{contactstudentid}

Update a student contact association. Any student contact detail included in the request will be ignored.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save changes to an existing student contact association.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| contactStudent | contactStudent | body | Modified student contact association. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/students/{contactstudentid}/studentdetails

Gets a list of all student contact details for a student contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns all student contact details for a student contact.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "studentContactDetailId": 0,
  "studentContactId": 0,
  "relationship": "string",
  "relationshipNote": "string",
  "custodial": true,
  "emergency": true,
  "livesWith": true,
  "schoolPickup": true,
  "startDate": "2025-10-29",
  "endDate": "2025-10-29",
  "receivesMail": true,
  "excludeFromStateReporting": true,
  "active": true,
  "contactStudentDetailExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### POST /ws/contacts/{contactid}/students/{contactstudentid}/studentdetails

Add a student contact detail record to an existing student contact association.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save new student contact detail. New record must not result in overlapping date ranges between any of the student contact's detail records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| contactStudentDetail | contactStudentDetail | body | Contact student detail to create. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### DELETE /ws/contacts/{contactid}/students/{contactstudentid}/studentdetails/{contactstudentdetailid}

Deletes a single student contact detail record.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Deletes a student contact detail. Deleting the only student contact detail for the student contact is not allowed.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| contactstudentdetailid | integer | path | The ID of the student contact detail. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/{contactid}/students/{contactstudentid}/studentdetails/{contactstudentdetailid}

Gets a single contact student detail for a student contact.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Returns a single student contact detail record.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| contactstudentdetailid | integer | path | The ID of the student contact detail. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "deleted": false,
  "studentContactDetailId": 0,
  "studentContactId": 0,
  "relationship": "string",
  "relationshipNote": "string",
  "custodial": true,
  "emergency": true,
  "livesWith": true,
  "schoolPickup": true,
  "startDate": "2025-10-29",
  "endDate": "2025-10-29",
  "receivesMail": true,
  "excludeFromStateReporting": true,
  "active": true,
  "contactStudentDetailExtension": {
    "id": 0,
    "@extensions": "",
    "_extension_data": {
      "_table_extension": [
        {
          "name": "string",
          "_field": [
            {
              "name": "string",
              "type": "string",
              "value": "string"
            }
          ]
        }
      ]
    }
  }
}
```

### PUT /ws/contacts/{contactid}/students/{contactstudentid}/studentdetails/{contactstudentdetailid}

Update a student contact detail.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,PLUGINS |

#### Description

Save changes to an existing student contact detail record. Updated record must not result in overlapping date ranges between any of the student contact's detail records.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| contactid | integer | path | The ID of the contact person. |
| contactstudentid | integer | path | The ID of the student contact association. |
| contactstudentdetailid | integer | path | The ID of the student contact detail. |
| contactStudentDetail | contactStudentDetail | body | Modified student contact detail record. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 400 | Bad Request |  |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not Found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
saved {
  _success_message (contact.update.successMessage, optional)
  _error_message (contact.update.errorMessages, optional)
  _warning_message (contact.update.warningMessages, optional)
  savedObject (object, optional): The saved item after successful insert or update
}

successMessage {
  id (integer, optional): Contact ID (Person.id) inserted or updated
  success (contact.update.success, optional)
  ref (string, optional): /ws/contacts/insertUpdateContact
}

errorMessages {
  _warning (Array[contact.update.errorMessage], optional)
}

warningMessages {
  _warning (Array[contact.update.warningMessage], optional)
}

errorMessage {
  field (string, optional)
  error_code (string, optional)
  error_description (string, optional)
}

warningMessage {
  field (string, optional)
  warning_code (string, optional)
  warning_description (string, optional)
}
```

**Response Schema:**

```json
{
  "status": "VALID",
  "action": "UPDATE",
  "_success_message": {
    "id": 0,
    "ref": "string"
  },
  "_error_message": {
    "_warning": [
      {
        "field": "string",
        "error_code": "string",
        "error_description": "string"
      }
    ]
  },
  "_warning_message": {
    "_warning": [
      {
        "field": "string",
        "warning_code": "string",
        "warning_description": "string"
      }
    ]
  },
  "savedObject": {}
}
```

### GET /ws/contacts/student/{studentdcid}

Get student contacts by studentDcid.

| Property | Value |
|----------|-------|
| Available Since | 12.0.0.0 |
| Accessible To | ADMIN,GUARDIAN,STUDENT,TEACHERS,PLUGINS |

#### Description

Get a list of contacts for a student.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| studentdcid | integer | path | DCID of the student. |
| extensions | Array[] | query | A comma-delimited list of table extensions to retrieve. |

#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 204 | No Contents | [Complex Model - See API Documentation] |
| 400 | Bad Request | [Complex Model - See API Documentation] |
| 401 | Unauthorized | [Complex Model - See API Documentation] |
| 403 | Forbidden | [Complex Model - See API Documentation] |
| 404 | Not found | [Complex Model - See API Documentation] |

#### Response Class (Status 200)

```
contact {
  contactId (integer)
  firstName (string, optional)
  middleName (string, optional)
  lastName (string, optional)
  prefix (string, optional): Codeset code where CodeType 'Prefix'
  suffix (string, optional): Codeset code where CodeType 'Suffix'
  gender (string, optional): Codeset code where CodeType = 'Gender'
  employer (string, optional)
  stateContactNumber (string, optional)
  contactNumber (string, optional)
  stateExcludeFromReporting (boolean, optional)
  active (boolean, optional)
  emails (Array[contactEmail], optional)
  phones (Array[contactPhone], optional)
  languages (Array[contact.language], optional): Field unused at this time
  contactAccount (contactAccount, optional)
  addresses (Array[contactAddress], optional)
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactEmail {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactEmailId (integer, optional)
  primary (boolean, optional): Is primary email address
  emailId (integer, optional)
  type (string, optional): Codeset code where CodeType = 'Email'
  address (string, optional): Email address
  contactEmailAssocExtension (contactEmailAssocExtension, optional): Person email address assoc extensions
}

contactPhone {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsPhoneId (integer, optional)
  sequence (integer, optional): Sort order when presented in a list
  preferred (boolean, optional): Is the preferred phone number
  phoneType (string, optional): CodeSet code where CodeType = 'Phone'
  phoneNumberId (integer, optional): PhoenNumberId of associated record in PhoneNumber table
  phoneNumber (string, optional): Phone number with user entered formatting
  extension (string, optional)
  sms (boolean, optional)
  contactPhoneAssocExtension (contactPhoneAssocExtension, optional): Person phone number assoc extensions
}

contactAccount {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  enabled (boolean, optional): Is account enabled
  userName (string, optional): Users sign in ID
  password (string, optional): Always 'null' for security reasons
  extensions (Array[contact.extension], optional)
}

contactAddress {
  deleted (boolean, optional): Field unused at this time booleanDefault:false
  contactsAddressId (integer, optional)
  sequence (integer, optional): Sort order when displayed
  addressId (integer, optional)
  addressType (string, optional): CodeSet code where CodeType = 'Address'
  street (string, optional)
  linetwo (string, optional)
  unit (string, optional)
  city (string, optional)
  state (integer, optional): CodeSet code where CodeType = 'State'
  country (integer, optional): CodeSet code where CodeType = 'Country'
  postalcode (string, optional)
  startDate (string, optional): When this address became effective
  endDate (string, optional): When this address is no longer effective - Returnes 'null' if no date is set
  contactAddressAssocExtension (contactAddressAssocExtension, optional): Person address assoc extensions
}

contactStudent {
  deleted (boolean, optional): Delete the student contact association. UI use only. booleanDefault:false
  studentContactId (integer, optional): Read-only
  sequence (integer, optional): Priority order for the student contact association from the student perspective.
  dcid (integer, optional): Read-only
  studentNumber (string, optional): Required when adding a new student contact association. Read-only for all other cases.
  firstName (string, optional): Read-only
  middleName (string, optional): Read-only
  lastName (string, optional): Read-only
  schoolAbbr (string, optional): Read-only
  schoolNumber (integer, optional): Read-only
  originalContactType (string, optional): Describes the type of a contact that is visible on legacy student pages.
  autosendHowOften (integer, optional): Number of days between autosends. Should be value of 0 (never)
  1 (daily)
  7 (weekly)
  30 (montly)
  emailSummary (boolean, optional)
  assignmentDetails (boolean, optional)
  attendanceDetails (boolean, optional)
  schoolAnnouncements (boolean, optional)
  balanceAlert (boolean, optional)
  guardianId (integer, optional)
  canAccessData (boolean, optional): Read-only
  restrictions (Array[guardianPluginRestriction], optional)
  notificationEmails (string, optional): Comma-delimited list of email addresses where reports are sent. Not modifiable by plug-in clients.
  contactStudentAssocExtension (contactStudentAssocExtension, optional): Student detail extensions
  studentDetails (Array[contactStudentDetail], optional)
}

ExtensionData {
  _table_extension (Array[contact.extension.tableExtension], optional)
}

contactEmailAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactPhoneAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

extension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactAddressAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

guardianPluginRestriction {
  restrictionId (integer, optional)
  pluginDefId (integer, optional)
  pluginName (string, optional)
  guardianStudentId (integer, optional)
  restricted (boolean, optional)
}

contactStudentAssocExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

contactStudentDetail {
  deleted (boolean, optional): Delete the student contact association detail record. UI use only. booleanDefault:false
  studentContactDetailId (integer, optional)
  studentContactId (integer, optional)
  relationship (string, optional): CodeSet code where CodeType = 'Relationship'
  relationshipNote (string, optional)
  custodial (boolean, optional)
  emergency (boolean, optional)
  livesWith (boolean, optional)
  schoolPickup (boolean, optional)
  startDate (string, optional): When this contact became effective
  endDate (string, optional): When this contact is no longer effective - Returnes 'null' if no date is set
  receivesMail (boolean, optional)
  excludeFromStateReporting (boolean, optional)
  active (boolean, optional)
  contactStudentDetailExtension (contactStudentDetailExtension, optional): Student detail extensions
}

tableExtension {
  name (string, optional): extension table name
  _field (Array[contact.extension.field], optional): extension table fields
}

contactStudentDetailExtension {
  extensions (string, optional): Comma-separated list of schema extensions associated with the base resource stringDefault:
  _extension_data (contact.ExtensionData, optional): Extended schema data associated with the base resource
}

field {
  name (string, optional): name of the field
  type (string, optional): data type of field
  value (string, optional): value of field
}
```

**Response Schema:**

```json
{
  "contactId": 0,
  "firstName": "string",
  "middleName": "string",
  "lastName": "string",
  "prefix": "string",
  "suffix": "string",
  "gender": "string",
  "employer": "string",
  "stateContactNumber": "string",
  "contactNumber": "string",
  "stateExcludeFromReporting": true,
  "active": true,
  "emails": [
    {
      "deleted": false,
      "contactEmailId": 0,
      "primary": true,
      "emailId": 0,
      "type": "string",
      "address": "string",
      "contactEmailAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "phones": [
    {
      "deleted": false,
      "contactsPhoneId": 0,
      "sequence": 0,
      "preferred": true,
      "phoneType": "string",
      "phoneNumberId": 0,
      "phoneNumber": "string",
      "extension": "string",
      "sms": true,
      "contactPhoneAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "languages": [
    null
  ],
  "contactAccount": {
    "deleted": false,
    "enabled": true,
    "userName": "string",
    "password": "string",
    "extensions": [
      {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    ]
  },
  "addresses": [
    {
      "deleted": false,
      "contactsAddressId": 0,
      "sequence": 0,
      "addressId": 0,
      "addressType": "string",
      "street": "string",
      "linetwo": "string",
      "unit": "string",
      "city": "string",
      "state": 0,
      "country": 0,
      "postalcode": "string",
      "startDate": "2025-10-29",
      "endDate": "2025-10-29",
      "contactAddressAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      }
    }
  ],
  "contactStudents": [
    {
      "deleted": false,
      "studentContactId": 0,
      "sequence": 0,
      "dcid": 0,
      "studentNumber": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "schoolAbbr": "string",
      "schoolNumber": 0,
      "originalContactType": "string",
      "autosendHowOften": 0,
      "emailSummary": true,
      "assignmentDetails": true,
      "attendanceDetails": true,
      "schoolAnnouncements": true,
      "balanceAlert": true,
      "guardianId": 0,
      "canAccessData": true,
      "restrictions": [
        {
          "restrictionId": 0,
          "pluginDefId": 0,
          "pluginName": "string",
          "guardianStudentId": 0,
          "restricted": true
        }
      ],
      "notificationEmails": "string",
      "contactStudentAssocExtension": {
        "id": 0,
        "@extensions": "",
        "_extension_data": {
          "_table_extension": [
            {
              "name": "string",
              "_field": [
                {
                  "name": "string",
                  "type": "string",
                  "value": "string"
                }
              ]
            }
          ]
        }
      },
      "studentDetails": [
        {
          "deleted": false,
          "studentContactDetailId": 0,
          "studentContactId": 0,
          "relationship": "string",
          "relationshipNote": "string",
          "custodial": true,
          "emergency": true,
          "livesWith": true,
          "schoolPickup": true,
          "startDate": "2025-10-29",
          "endDate": "2025-10-29",
          "receivesMail": true,
          "excludeFromStateReporting": true,
          "active": true,
          "contactStudentDetailExtension": {
            "id": 0,
            "@extensions": "",
            "_extension_data": {
              "_table_extension": [
                {
                  "name": "string",
                  "_field": [
                    {
                      "name": "string",
                      "type": "string",
                      "value": "string"
                    }
                  ]
                }
              ]
            }
          }
        }
      ]
    }
  ],
  "@extensions": "",
  "_extension_data": {
    "_table_extension": [
      {
        "name": "string",
        "_field": [
          {
            "name": "string",
            "type": "string",
            "value": "string"
          }
        ]
      }
    ]
  }
}
```
