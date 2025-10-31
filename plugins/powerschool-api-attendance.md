
# PowerSchool ATTENDANCE API

## attendance

### POST /ws/attendance/batch_daily_time

Create or update daily or time attendance record in batches

| Property | Value |
|----------|-------|
| Available Since | 25.3.0 |
| Accessible To | PLUGINS |

#### Description

Create or update daily or time attendance record in a batch. Maximum of 200 attendance daily or time record may be submitted in the payload.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert or update. The data must include STUDENTID, ATT_DATE, SCHOOLID, YEARID, ATT_MODE_CODE, ATTENDANCE_CODEID. |

**Model Description:**

```
dailyTimeAttendanceList {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  record (Array[dailyTimeAttendance], optional)
}

dailyTimeAttendance {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  tables (Inline Model 1, optional)
}

Inline Model 1 {
  attendance (Inline Model 2, optional)
}

Inline Model 2 {
  attendance_codeid (string, optional): The internal id of the attendance code (ATTENDANCE_CODE.ID).
  calendar_dayid (string, optional): The internal id of the calendary day (CALENDAR_DAY.ID).
  schoolid (string, optional): The internal id of school (SCHOOLS.SCHOOL_NUMBER).
  studentid (string, optional): The internal id of the student (STUDENTS.ID).
  att_comment (string, optional): Free form text that can be entered for this attendance record.
  total_minutes (string, optional): Total minutes of attendance for this record. This is only needed for att_mode_code ATT_ModeTime.
  programid (string, optional): Program under which attendance is taken. The list of valid programs can be queried using com.pearson.core.attendance.special_program.
  dcid (string, optional): The internal DCID of the inserted attendance record. Primarily used for updates to attendance records with the att_mode_code set to ATT_ModeTime.
}
```

**Model Schema:**

```json
{
  "name": "string",
  "record": [
    {
      "name": "string",
      "tables": {
        "attendance": {
          "attendance_codeid": "string",
          "calendar_dayid": "string",
          "schoolid": "string",
          "yearid": "string",
          "studentid": "string",
          "att_mode_code": "string",
          "att_comment": "string",
          "total_minutes": "string",
          "att_date": "string",
          "programid": "string",
          "dcid": "string"
        }
      }
    }
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Attendance records were inserted or updated. The body will include a list of URIs for the records that were inserted or updated. | [Complex Model - See API Documentation] |
| 400 | Bad Request. The body may include errors that were identified in the payload. | [Complex Model - See API Documentation] |
| 403 | Forbidden. The body may include the security errors encountered. | [Complex Model - See API Documentation] |
| 500 | Internal Server Error. An unknown error occurred. If the problem persists after retrying, this may need to be reported to PowerSchool support. | [Complex Model - See API Documentation] |

### POST /ws/attendance/daily_time

Create or update daily or time attendance record

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Create or update daily or time attendance record. Only a single attendance daily or time record may be submitted in the payload.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert or update. The data must include STUDENTID, ATT_DATE, SCHOOLID, YEARID, ATT_MODE_CODE, ATTENDANCE_CODEID. |

**Model Description:**

```
dailyTimeAttendanceList {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  record (Array[dailyTimeAttendance], optional)
}

dailyTimeAttendance {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  tables (Inline Model 1, optional)
}

Inline Model 1 {
  attendance (Inline Model 2, optional)
}

Inline Model 2 {
  attendance_codeid (string, optional): The internal id of the attendance code (ATTENDANCE_CODE.ID).
  calendar_dayid (string, optional): The internal id of the calendary day (CALENDAR_DAY.ID).
  schoolid (string, optional): The internal id of school (SCHOOLS.SCHOOL_NUMBER).
  studentid (string, optional): The internal id of the student (STUDENTS.ID).
  att_comment (string, optional): Free form text that can be entered for this attendance record.
  total_minutes (string, optional): Total minutes of attendance for this record. This is only needed for att_mode_code ATT_ModeTime.
  programid (string, optional): Program under which attendance is taken. The list of valid programs can be queried using com.pearson.core.attendance.special_program.
  dcid (string, optional): The internal DCID of the inserted attendance record. Primarily used for updates to attendance records with the att_mode_code set to ATT_ModeTime.
}
```

**Model Schema:**

```json
{
  "name": "string",
  "record": [
    {
      "name": "string",
      "tables": {
        "attendance": {
          "attendance_codeid": "string",
          "calendar_dayid": "string",
          "schoolid": "string",
          "yearid": "string",
          "studentid": "string",
          "att_mode_code": "string",
          "att_comment": "string",
          "total_minutes": "string",
          "att_date": "string",
          "programid": "string",
          "dcid": "string"
        }
      }
    }
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Attendance records were inserted or updated. The body will include a list of URIs for the records that were inserted or updated. | [Complex Model - See API Documentation] |
| 400 | Bad Request. The body may include errors that were identified in the payload. | [Complex Model - See API Documentation] |
| 403 | Forbidden. The body may include the security errors encountered. | [Complex Model - See API Documentation] |
| 500 | Internal Server Error. An unknown error occurred. If the problem persists after retrying, this may need to be reported to PowerSchool support. | [Complex Model - See API Documentation] |

### POST /ws/attendance/meeting_interval

Create or update meeting or interval attendance record

| Property | Value |
|----------|-------|
| Available Since | 9.0.0 |
| Accessible To | PLUGINS |

#### Description

Create or update meeting or interval attendance record. Multiple attendance records may be submitted in the payload, but they must all be for a single student for a single day. A student may have both meeting and interval attendance in the same day.

#### Parameters

| Name | Type | Parameter Type | Description |
|------|------|----------------|-------------|
| body | Model | body | Data to insert or update. The data must include STUDENTID, ATT_DATE, SCHOOLID, YEARID, ATT_MODE_CODE, ATTENDANCE_CODEID and ATT_INTERVAL or START_TIME and END_TIME depending on the mode. |

**Model Description:**

```
meetingIntervalAttendanceList {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  record (Array[meetingIntervalAttendance], optional)
}

meetingIntervalAttendance {
  name (string, optional): Tablename. Should be set to "ATTENDANCE".
  tables (Inline Model 1, optional)
}

Inline Model 1 {
  attendance (Inline Model 2, optional)
}

Inline Model 2 {
  attendance_codeid (string, optional): The internal id of the attendance code (ATTENDANCE_CODE.ID).
  calendar_dayid (string, optional): The internal id of the calendary day (CALENDAR_DAY.ID).
  schoolid (string, optional): The internal id of school (SCHOOLS.SCHOOL_NUMBER).
  studentid (string, optional): The internal id of the student (STUDENTS.ID).
  ccid (string, optional): The internal id of the class enrollment record (CC.ID).
  periodid (string, optional): The internal id of the period (PERIOD.ID).
  att_comment (string, optional): Free form text that can be entered for this attendance record.
  att_interval (string, optional): The interval number for the attendance record. This is only needed if the att_mode_code is ATT_ModeInterval.
  start_time (integer, optional): Start time in seconds since midnight. This is only needed if the att_mode_code is ATT_ModeMeeting.
  end_time (integer, optional): End time in seconds since midnight. This is only needed if the att_mode_code is ATT_ModeMeeting.
  programid (string, optional): Program under which attendance is taken. The list of valid programs can be queried using com.pearson.core.attendance.special_program.
}
```

**Model Schema:**

```json
{
  "name": "string",
  "record": [
    {
      "name": "string",
      "tables": {
        "attendance": {
          "attendance_codeid": "string",
          "calendar_dayid": "string",
          "schoolid": "string",
          "yearid": "string",
          "studentid": "string",
          "ccid": "string",
          "periodid": "string",
          "att_mode_code": "string",
          "att_comment": "string",
          "att_interval": "string",
          "start_time": 0,
          "end_time": 0,
          "att_date": "string",
          "programid": "string"
        }
      }
    }
  ]
}
```


#### Response Messages

| Status Code | Message | Response Model |
|-------------|---------|----------------|
| 200 | Attendance records were inserted or updated. The body will include a list of URIs for the records that were inserted or updated. | [Complex Model - See API Documentation] |
| 400 | Bad Request. The body may include errors that were identified in the payload. | [Complex Model - See API Documentation] |
| 403 | Forbidden. The body may include the security errors encountered. | [Complex Model - See API Documentation] |
| 500 | Internal Server Error. An unknown error occurred. If the problem persists after retrying, this may need to be reported to PowerSchool support. | [Complex Model - See API Documentation] |
