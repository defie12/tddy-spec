# TodoDoneYet Task File Format Specification

## 1. Overview

`.tddy` is a JSON-based file format used by TodoDoneYet to exchange individual tasks.

Each `.tddy` file represents one task.

## 2. File Extension

The file extension is `.tddy`.

## 3. Format

A `.tddy` file contains a JSON object representing one task.

## 4. Fields

`header` — Required. Identifies the file as a TodoDoneYet task.

`title` — Required. The task title.

`description` — Optional. The task description.

`urgency` — Required. The task urgency level.

`mode` — Required. The reminder mode.

`activation` — Optional. The date the alarm activates.

`anchor` — Optional. A daily recurring reminder time.

## 5. Required Fields

The required fields are:

- `header`
- `title`
- `urgency`
- `mode`

## 6. Optional Fields

The optional fields are:

- `description`
- `activation`
- `anchor`

## 7. Urgency Levels

`1` = Low  
`2` = Medium  
`3` = High  
`4` = Extreme

Urgency determines the pulse interval used by TodoDoneYet.

## 8. Task Modes

`SIMPLE_MODE` — Normal alarm behavior.

`DONE_YET` — Adaptive reminders that respond to the user's behavior toward the task.

`RELENTLESS_MODE` — Escalating reminders that continue to escalate rather than adapting to user behavior.

## 9. Activation

The `activation` field contains the date on which the task alarm activates.

TodoDoneYet uses the user's local time.

## 10. Anchor

The `anchor` field contains a daily recurring reminder time.

Example: `19:00`

TodoDoneYet uses the user's local time.

## 11. Reminder Behavior

The pulse interval is determined by TodoDoneYet from the task's urgency.

The pulse interval is not stored in the `.tddy` file.

If there is no activation or anchor, the pulse interval is used first.

## 12. Validation

TodoDoneYet validates `.tddy` files when they are opened or imported.

The required header value is:

`TODODONEYET_TASK`

## 13. Privacy and Import

`.tddy` files do not contain user information or device information.

They are designed for sharing individual tasks and importing them into TodoDoneYet.

There is currently no version number stored in the format.

## 14. Example

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
