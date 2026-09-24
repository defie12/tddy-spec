# TodoDoneYet Task File Format (.tddy)

The **TodoDoneYet Task File Format (`.tddy`)** is an open, documented, JSON-based file format used by **TodoDoneYet** to exchange individual tasks.

## About

A `.tddy` file represents a TodoDoneYet task in a portable JSON format.

The format is designed to allow individual tasks to be shared, transferred, backed up, and imported between compatible TodoDoneYet installations.

## Example

A `.tddy` file may contain a task such as:

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

TodoDoneYet task files use:

.tddy

Format

.tddy files use UTF-8 encoded JSON.

The root element is a JSON object representing an individual task.

Current Specification

The .tddy specification is being documented and versioned publicly in this repository.

As the format evolves, this repository will document:

Supported fields

Field types

Required and optional fields

Urgency levels

Task modes

Date and time representation

Import and export behavior

Compatibility rules

Version history

JSON Schema


Compatibility

Applications implementing the .tddy format should preserve unknown fields when possible so that future versions of the format can remain compatible with existing data.

Official Project

.tddy is the task file format associated with TodoDoneYet.

The TodoDoneYet application is developed by Future Techware Ltd.

Specification Status

Status: Initial public documentation

This repository is the authoritative public location for the .tddy format specification.


---

License

The specification documentation in this repository is intended to be openly available for developers and software projects that wish to understand or implement the .tddy format.