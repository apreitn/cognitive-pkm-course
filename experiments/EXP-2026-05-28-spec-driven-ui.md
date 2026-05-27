# EXP-2026-05-28 Spec-Driven UI

## Experiment topic
Using Spec-Driven Development to generate a frontend UI based on a strict design contract.

## Project
Service Desk Ticket Helper

## Selected feature
Ticket form validation

## Goal
The goal was to generate a simple UI that connects to the existing ticket validation module created in the previous task.

The UI should not be a generic dashboard. It should follow the rules from `docs/DESIGN.md`.

---

## Design contract used
The UI was generated using a design contract with the following rules:

- Framework: HTML, CSS, Vanilla JavaScript
- Primary color: `#1E3A8A`
- Secondary color: `#64748B`
- Background color: `#F8FAFC`
- Text color: `#0F172A`
- Error color: `#DC2626`
- Success color: `#16A34A`
- Use visible labels for all form fields
- Buttons must have rounded corners
- Keep the UI simple and practical
- Do not use random colors
- Do not create an unnecessary dashboard

---

## Prompt provided to AI

```txt
I am developing a Service Desk Ticket Helper application.

Use the following design contract from docs/DESIGN.md:
- Framework: HTML, CSS, Vanilla JavaScript
- Primary color: #1E3A8A
- Secondary color: #64748B
- Background color: #F8FAFC
- Text color: #0F172A
- Error color: #DC2626
- Success color: #16A34A
- Buttons must have rounded corners
- Forms must have visible labels
- UI must be simple and accessible
- Do not create a generic dashboard
- Do not use random colors
- Do not use unnecessary animations

Generate frontend code for the ticket validation feature.

The UI must connect to the existing module:
src/modules/ticket-validation/ticketValidator.js

The button click must call:
createDefaultTicketValidator().validate(ticketData)

The UI must show either:
- valid ticket message
- validation errors

Use clean HTML, CSS, and JavaScript.
```

---

## Result
The AI generated a simple frontend with:

- `index.html`
- `src/styles.css`
- `src/app.js`

The UI includes a ticket form with fields for:

- user name
- device name
- issue category
- problem description
- business impact

The submit button calls the existing validation module and displays either a success message or a list of validation errors.

---

## Did the AI follow DESIGN.md?
Mostly yes.

The generated UI followed the required color palette, used simple spacing, visible labels, rounded buttons, and clear form structure.

It did not create a random dashboard or use generic bright blue styles outside the selected design system.

---

## How many prompts were needed?
One main prompt was enough to get the first working version.

Small manual review was still needed to confirm that the JavaScript import path matched the existing project structure.

---

## Was the UI connected to the existing backend/module?
Yes.

The UI imports the existing validator:

```js
import { createDefaultTicketValidator } from "./modules/ticket-validation/ticketValidator.js";
```

Then it uses the validator when the form is submitted:

```js
const result = validator.validate(ticketData);
```

This means the interface is connected to the validation logic created in the previous task.

---

## Was the UI accessible and structurally sound?
Mostly yes.

Good points:
- All form fields have labels.
- Text contrast is clear.
- Error messages are shown in readable text.
- The form has a simple structure.
- The button action is clear.

Possible future improvements:
- Add `aria-live` to the validation result area.
- Add inline error messages near each field.
- Add keyboard focus improvements.

---

## What I learned
Spec-Driven Development helps control AI output. Instead of asking AI to “make a UI”, I gave it design rules, colors, component rules, and integration requirements.

This made the result more consistent and easier to connect to the existing module.

The design contract reduced the risk of generic AI-generated UI and helped keep the project aligned with the MVP.
