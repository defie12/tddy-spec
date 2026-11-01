TodoDoneYet Task File Format (.tddy)

Format: TodoDoneYet Task File Format
Extension: ".tddy"
Data Structure: JSON
Specification Version: 1.0.0
Header Identifier: "TODODONEYET_TASK"

1. Introduction

The TodoDoneYet Task File Format (".tddy") is a lightweight, structured file format designed to represent and exchange individual tasks between applications, devices, users, and compatible software systems.

A ".tddy" file contains one task represented as a JSON object.

The format is designed to support:

- Task creation and export.
- Task sharing between users.
- Importing tasks into TodoDoneYet.
- Sharing through Bluetooth file transfer and social applications.
- Machine-readable task validation.
- AI-assisted task generation and interpretation.
- Integration with third-party productivity tools.

The format is intended to remain simple, portable, and independent of any particular application or operating system.

2. File Structure

A valid ".tddy" file contains a single JSON object.

Every valid task file must include:

- "header"
- "title"
- "urgency"
- "mode"

Optional fields include:

- "description"
- "activation"
- "anchor"

The header must contain the exact identifier:

"TODODONEYET_TASK"

This identifier allows compatible applications to recognize a TodoDoneYet task file.

3. Field Definitions

3.1 header

- Type: String
- Required: Yes
- Value: "TODODONEYET_TASK"

Identifies the file as a TodoDoneYet task.

Applications should check this field before accepting an imported file.

3.2 title

- Type: String
- Required: Yes

Contains the task name or main instruction.

Example:

""title": "Call Dad""

3.3 description

- Type: String
- Required: No

Provides additional information about the task.

Example:

""description": "Discuss the weekend plans""

The field may be omitted when no additional information is needed.

3.4 urgency

- Type: Integer
- Required: Yes
- Allowed values: 1–4

Defines the urgency level of the task.

Value| Level| Meaning
1| Low| Minimal urgency
2| Medium| Moderate urgency
3| High| Important task requiring attention
4| Extreme| Highest urgency

Urgency determines the reminder pulse interval and influences the task's reminder intensity.

The exact pulse intervals and reminder algorithms are implementation-specific.

3.5 mode

- Type: String
- Required: Yes

Defines the task's reminder behavior.

Three modes are supported:

SIMPLE_MODE

Normal alarm behavior. Provides a straightforward reminder without adaptive escalation.

DONE_YET

Uses moderately escalating and adaptive reminder behavior to encourage task completion.

RELENTLESS_MODE

Uses persistent reminder behavior that can remain constant or escalate, adapting to user behavior.

Valid values:

- "SIMPLE_MODE"
- "DONE_YET"
- "RELENTLESS_MODE"

Applications should not substitute an unknown mode with a different mode without informing the user.

3.6 activation

- Type: Integer
- Required: No

Contains a Unix timestamp in milliseconds representing the task's activation date.

It determines when the task becomes active.

Example:

""activation": 1790031600000"

Applications should interpret and display the activation date using the appropriate local date and time context.

When omitted, the application may use its default activation behavior.

3.7 anchor

- Type: String
- Required: No

Defines a daily recurring local-time anchor for the task.

Format:

"HH:mm"

Uses the 24-hour clock.

Examples:

- "07:00"
- "12:30"
- "19:00"
- "21:00"

The anchor represents the daily time associated with the task's reminder schedule.

When omitted, the application may use its default scheduling behavior.

4. Task Modes and Urgency

Urgency and mode serve different purposes.

Urgency determines the task's reminder pulse interval.

Mode determines the overall reminder behavior.

Both values work together to define how an application handles task reminders.

The exact timing, escalation algorithms, and adaptation logic are implementation-specific.

The file format describes the intended behavior without requiring every compatible application to implement identical reminder algorithms.

5. Scheduling Rules

The "activation" and "anchor" fields are optional and independent.

- "activation" identifies the date from which the task becomes active.
- "anchor" identifies a recurring daily local-time reference.
- Both may be provided together.
- Either field may be omitted.
- Both may be omitted.

Applications should preserve supplied scheduling information when importing and exporting tasks.

6. File Sharing

The ".tddy" format is designed to support portable task sharing.

A ".tddy" file can be distributed as a normal file attachment through supported sharing methods.

6.1 Bluetooth Sharing

Users can share ".tddy" files between compatible devices using Bluetooth file transfer where supported by the operating system.

The receiving device should retain the ".tddy" file extension and its original JSON contents.

6.2 Social Applications

Users can share ".tddy" files through social and messaging applications that support document or file attachments.

Examples include applications that allow users to send documents rather than only text or images.

The file should preferably be shared as an attachment instead of copying its JSON contents into a message.

Some platforms may modify filenames or prevent certain file attachments. Compatible applications should account for these limitations.

6.3 Other Sharing Methods

The format is not restricted to Bluetooth or social applications.

Other supported methods may include:

- Email attachments.
- Cloud storage.
- File transfer applications.
- USB file transfer.
- Direct downloads.
- Other compatible file-sharing services.

The ".tddy" format does not depend on a particular transfer method.

7. Importing and Validation

A compatible application should support the following import process:

1. Receive or open a ".tddy" file.
2. Read its JSON contents.
3. Confirm that the contents form a valid JSON object.
4. Verify the "header" identifier.
5. Validate required fields and data types.
6. Check urgency and mode values.
7. Validate optional scheduling fields when present.
8. Present the task for import or process it according to the application's import workflow.

Invalid files should be rejected with a useful error message.

Applications should not silently accept invalid required fields or unsupported mode values.

The published JSON Schema should be used for machine-readable validation.

8. AI and Machine Readability

The ".tddy" format is designed to be readable by humans, conventional software, and AI systems.

An AI system with access to this specification can:

- Recognize a TodoDoneYet task file.
- Interpret its task fields.
- Understand urgency levels.
- Understand supported task modes.
- Interpret activation and anchor information.
- Generate valid ".tddy" task files.
- Convert task information into other supported formats.
- Assist with task creation from natural-language instructions.

AI systems should follow the published specification and JSON Schema rather than guessing the meaning of fields.

The file extension alone does not guarantee validity.

Generated files should be validated before being imported into a compatible application.

9. Privacy and Data Structure

The ".tddy" format represents an individual task.

It does not require:

- User identification.
- Device identification.
- Account credentials.
- Passwords.
- Personal profile information.
- Device-specific configuration.

Applications should manage user identity, account information, and device-specific settings separately from the task file.

This keeps shared task files portable and reduces unnecessary exposure of personal information.

10. JSON Schema

A machine-readable JSON Schema is provided in:

"schema/tddy.schema.json"

The schema defines the structure, required properties, supported values, and validation rules for ".tddy" files.

Developers should use the published schema when implementing importers, exporters, validators, and other compatible tools.

11. Examples

Example files are available in the "examples/" directory.

- "basic-task.tddy" — Basic task example.
- "modes.tddy" — Example using RELENTLESS_MODE.

These examples demonstrate how valid task files should be structured.

12. Compatibility and Implementation

The ".tddy" format is intended to be application-independent.

Developers may implement support in:

- Android applications.
- iOS applications.
- Desktop applications.
- Web applications.
- AI-powered productivity tools.
- Task management systems.
- Automation and productivity software.

Compatible implementations should preserve the defined field meanings and validation requirements.

Applications may implement their own reminder interfaces and scheduling algorithms while respecting the meaning of the supplied task data.

13. Specification Evolution

This document describes version 1.0.0 of the TodoDoneYet Task File Format.

Changes to the format should be documented and reflected in the JSON Schema and relevant examples.

Changes should prioritize backward compatibility whenever possible.

The format should remain lightweight and focused on representing one task per file.

14. License

The specification is published under the license included in this repository.

Developers are encouraged to implement, integrate, and support the ".tddy" format in their own applications in accordance with that license.

---

TodoDoneYet Task File Format (.tddy)

A portable task format designed for sharing, importing, interpreting, and exchanging tasks across compatible applications and systems.