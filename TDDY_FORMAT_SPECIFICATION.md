# TodoDoneYet Task File Format Specification

## 1. Overview

`.tddy` is a JSON-based file format used by TodoDoneYet to exchange individual tasks.

Each `.tddy` file represents one task.

The format is designed to support task creation, exporting, sharing, importing, and interpretation by compatible applications and software systems.

## 2. File Extension

The file extension is:

`.tddy`

A `.tddy` file contains a JSON object representing one task.

## 3. Format Structure

Each `.tddy` file contains one JSON object.

The object uses a defined set of required and optional fields.

The required header value is:

`TODODONEYET_TASK`

This identifies the JSON object as a TodoDoneYet task.

## 4. Fields

The format defines the following fields:

| Field | Required | Type |
|---|---|---|
| `header` | Yes | String |
| `title` | Yes | String |
| `description` | No | String |
| `urgency` | Yes | Integer |
| `mode` | Yes | String |
| `activation` | No | Integer |
| `anchor` | No | String |

### 4.1 header

Identifies the file as a TodoDoneYet task.

Required value:

`TODODONEYET_TASK`

### 4.2 title

Contains the task title or main instruction.

Example: `"Call Dad"`

### 4.3 description

Optional additional information about the task.

Example: `"Discuss weekend plans"`

### 4.4 urgency

Defines the task's urgency level.

Accepted values are integers from 1 to 4.

### 4.5 mode

Defines the reminder behavior associated with the task.

Supported values:

- `SIMPLE_MODE`
- `DONE_YET`
- `RELENTLESS_MODE`

### 4.6 activation

Optional Unix timestamp in milliseconds representing the date and time when the task alarm activates.

TodoDoneYet uses the user's local time when interpreting and presenting the activation time.

### 4.7 anchor

An optional daily recurring reminder time.

The expected format is `HH:mm`, using the 24-hour clock.

Example: `"19:00"`

TodoDoneYet uses the user's local time.

## 5. Required Fields

The required fields are:

- `header`
- `title`
- `urgency`
- `mode`

A file missing any required field is not a valid `.tddy` task.

## 6. Optional Fields

The optional fields are:

- `description`
- `activation`
- `anchor`

Optional fields may be omitted when they are not needed.

## 7. Urgency Levels

The supported urgency levels are:

| Value | Level |
|---|---|
| 1 | Low |
| 2 | Medium |
| 3 | High |
| 4 | Extreme |

Urgency determines the pulse interval used by TodoDoneYet.

The pulse interval is calculated by TodoDoneYet and is not stored in the `.tddy` file.

## 8. Task Modes

Three reminder modes are supported.

### SIMPLE_MODE
Provides normal alarm behavior.

### DONE_YET
Provides adaptive reminders that respond to the user's behavior toward the task.

### RELENTLESS_MODE
Provides escalating reminders that continue to escalate rather than adapting to the user's behavior.

The task mode determines the reminder behavior, while urgency determines the pulse interval.

## 9. Activation

The `activation` field contains the Unix timestamp in milliseconds representing the date and time when the task alarm activates.

TodoDoneYet uses the user's local time when interpreting and displaying the activation time.

The field is optional.

## 10. Anchor

The `anchor` field contains a daily recurring reminder time.

The expected format is:

`HH:mm`

Example:

`19:00`

The time uses the 24-hour clock and is interpreted using the user's local time.

The field is optional.

## 11. Reminder Behavior

TodoDoneYet determines the pulse interval from the task's urgency.

The pulse interval is not stored in the `.tddy` file.

The reminder mode determines how the application handles reminders.

Activation and anchor provide scheduling information.

If neither activation nor anchor is provided, the pulse interval is used first.

The exact pulse intervals and reminder implementation are determined by TodoDoneYet.

## 12. Validation

TodoDoneYet validates `.tddy` files when they are opened or imported.

Validation includes:

- Checking that the file contains valid JSON.
- Checking the required header value.
- Checking that all required fields are present.
- Checking field data types.
- Checking supported urgency values.
- Checking supported task modes.
- Checking optional scheduling values when present.

The required header value is:

`TODODONEYET_TASK`

Invalid files should not be imported as valid tasks.

The published JSON Schema provides machine-readable validation rules for compatible implementations.

## 13. Privacy and Import

`.tddy` files do not require user information or device information.

They are designed for sharing individual tasks and importing them into TodoDoneYet.

A `.tddy` file represents task information rather than an entire user account or application database.

Imported tasks should be processed as task data and should not automatically overwrite unrelated user information or existing tasks.

## 14. File Sharing and Distribution

`.tddy` files are designed to be portable and shareable between users and compatible applications.

Supported distribution methods may include:

### 14.1 Bluetooth File Transfer
Users can share `.tddy` files between supported devices using Bluetooth file transfer.

The receiving device can open the transferred file with TodoDoneYet or another compatible application.

### 14.2 Social and Messaging Applications
Users can share `.tddy` files through social and messaging applications that support document or file attachments.

Examples include sharing through WhatsApp, Telegram, email, and other applications that support file transfers.

The file should be shared as an attachment so that its original contents and `.tddy` extension can be preserved.

### 14.3 Other File-Sharing Methods
The format is not restricted to Bluetooth or social applications.

It can also be distributed through:

- Cloud storage.
- Direct downloads.
- USB file transfers.
- Email attachments.
- Other file-sharing services.

Actual sharing and receiving capabilities depend on the operating system and the applications involved.

## 15. Importing Shared Tasks

Compatible applications should allow users to open or import `.tddy` files received through supported sharing methods.

A recommended import process is:

1. Receive or open the `.tddy` file.
2. Read its JSON contents.
3. Validate the JSON structure.
4. Verify the required header.
5. Validate the required fields and supported values.
6. Process the task information.
7. Present or add the task according to the application's import workflow.

Applications should provide useful feedback when an imported file is invalid or unsupported.

The file format does not require a particular sharing interface or import screen.

## 16. AI and Machine Readability

The `.tddy` format is structured to be readable by conventional software and AI systems.

Systems that understand this specification can:

- Identify TodoDoneYet task files.
- Read and interpret task fields.
- Understand urgency levels.
- Understand supported reminder modes.
- Interpret activation and anchor information.
- Generate structured `.tddy` files.
- Convert task information into other formats.
- Assist users in creating tasks from natural-language instructions.

AI systems should follow the published specification and JSON Schema when generating or interpreting `.tddy` files.

Generated files should be validated before import.

## 17. JSON Schema

The repository provides a JSON Schema for validating `.tddy` files.

Location:

`schema/tddy.schema.json`

The schema defines the machine-readable structure and validation rules for the format.

Developers building compatible applications and tools are encouraged to use it.

## 18. Compatibility and Versioning

The `.tddy` format currently does not store a version number inside individual task files.

The required header remains:

`TODODONEYET_TASK`

Future changes to the specification should preserve compatibility whenever possible.

Changes affecting field definitions, supported values, or validation rules should be reflected in the specification, JSON Schema, and relevant examples.

## 19. Example

A valid `.tddy` task file:

```json
{
  "header": "TODODONEYET_TASK",
  "title": "Meeting",
  "description": "shop meeting",
  "urgency": 1,
  "mode": "DONE_YET",
  "activation": 1790031600000,
  "anchor": "19:00"
}
