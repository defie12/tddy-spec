TodoDoneYet Task File Format (.tddy)
The TodoDoneYet Task File Format (.tddy) is an open, documented, JSON-based file format used by TodoDoneYet to exchange individual tasks.
About
A .tddy file represents an individual TodoDoneYet task in JSON format.
The format is designed for sharing and transferring individual tasks between compatible TodoDoneYet installations.
Example
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
The root element is a JSON object representing an individual task.
Specification
This repository documents the TodoDoneYet Task File Format.
The specification documents:
Supported fields
Field types
Required and optional fields
Urgency levels
Task modes
Date and time representation
Import and export behavior
Validation
Compatibility information
Official Project
The .tddy format is associated with TodoDoneYet.
The TodoDoneYet application is developed by Future Techware Ltd.
Specification Status
Initial public documentation
This repository is the public home of the TodoDoneYet Task File Format specification.
License
The specification documentation in this repository is intended to be openly available to developers and software projects that wish to understand or implement the .tddy format.