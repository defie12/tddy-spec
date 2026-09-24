# TodoDoneYet Task File Format (.tddy)

The TodoDoneYet Task File Format (.tddy) is an open, documented, JSON-based file format used by TodoDoneYet to exchange individual tasks.

## About

A `.tddy` file represents a single TodoDoneYet task in JSON format.

The format is designed for sharing tasks and importing them into TodoDoneYet.

TodoDoneYet generates `.tddy` files and validates them when they are opened or imported.

## Example

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

File Extension

TodoDoneYet task files use the .tddy file extension.

Format

.tddy files use JSON.

The root element is a JSON object representing one task.

Each .tddy file currently represents exactly one task.

Fields

header — Identifies the file as a TodoDoneYet task.

title — The task title.

description — The task description. Optional.

urgency — The task urgency level.

mode — The TodoDoneYet reminder mode.

activation — The date on which the alarm activates. Optional.

anchor — A daily time at which the task should remind the user. Optional.


Urgency Levels

Value	Level

1	Low
2	Medium
3	High
4	Extreme


Task Modes

SIMPLE_MODE

Normal alarm behavior.

DONE_YET

Adaptive reminder behavior. TodoDoneYet adapts reminders based on the user's behavior toward the task.

RELENTLESS_MODE

Escalating reminder behavior. The reminders continue to escalate rather than adapting to the user's behavior.

Validation

The header value is:

TODODONEYET_TASK

TodoDoneYet uses this value to validate that a file is a TodoDoneYet task file.

Date and Time

TodoDoneYet interprets task dates and times according to the user's local time.

The activation field represents the task's activation date.

The anchor field represents a daily recurring reminder time.

If neither activation nor anchor is provided, the pulse interval is used first.

Privacy

.tddy files do not contain user information or device information.

Versioning

There is currently no version number stored in the .tddy format.

Official Project

The .tddy format is associated with TodoDoneYet.

TodoDoneYet is developed by Future Techware Ltd.

Specification Status

Initial public specification

This repository is the public home of the TodoDoneYet Task File Format specification.

License

The specification documentation in this repository is intended to be openly available to developers and software projects that wish to understand or implement the .tddy format.