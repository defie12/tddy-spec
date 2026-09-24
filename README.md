# TodoDoneYet Task File Format (.tddy)

The **TodoDoneYet Task File Format (.tddy)** is an open, documented, JSON-based file format used by **TodoDoneYet** to exchange individual tasks.

## About

A `.tddy` file represents an individual TodoDoneYet task in JSON format.

The format is designed for sharing and transferring individual tasks between compatible TodoDoneYet installations.

## Example

Here is an example of a `.tddy` task file:

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

Example `.tddy` task files are available in the [`examples/`](examples/) directory.

- [`basic-task.tddy`](examples/basic-task.tddy) — Basic TodoDoneYet task
- [`modes.tddy`](examples/modes.tddy) — Example using task modes
```

## File Extension

TodoDoneYet task files use the `.tddy` file extension.

## Format

`.tddy` files use JSON.

The root element is a JSON object representing an individual task.

## Specification

This repository documents the TodoDoneYet Task File Format.

The specification will document:

- Supported fields
- Field types
- Required and optional fields
- Urgency levels
- Task modes
- Date and time representation
- Import and export behavior
- Validation
- Compatibility information

## Compatibility

Applications implementing the `.tddy` format should preserve unknown fields when possible so that future versions of the format can remain compatible with existing data.

## Official Project

The `.tddy` format is associated with **TodoDoneYet**.

The TodoDoneYet application is developed by **Future Techware Ltd.**

## Specification Status

**Initial public documentation**

This repository is the public home of the TodoDoneYet Task File Format specification.

## Specification

- [TDDY Format Specification](TDDY_FORMAT_SPECIFICATION.md)
- [JSON Schema](tddy-schema.json)

## License

The specification documentation in this repository is intended to be openly available for developers and software projects that wish to understand or implement the `.tddy` format. by
