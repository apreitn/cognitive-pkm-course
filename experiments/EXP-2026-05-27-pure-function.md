# EXP-2026-05-27 Pure Function Experiment

## Experiment topic
Testing whether AI can generate correct feature logic when it is given structured BDD requirements, a Mermaid diagram, and a strict pure function constraint.

## Selected feature
Ticket form validation.

## Why I selected this feature
I selected ticket form validation because it is small but important for the MVP. If the user submits an incomplete ticket, the final result will not be useful for troubleshooting or escalation. This feature is also good for testing pure function logic because validation can be done without changing the page or storing data.

---

## Prompt provided to AI

```txt
I am developing a simple Service Desk Ticket Helper application.

Requirements:

User Story:
As a service desk agent, I want the ticket form to check if important fields are completed, so that the final ticket contains enough information for troubleshooting or escalation.

Acceptance Criteria:

AC1:
Given the user has opened the ticket creation form
When the user fills in all required fields and submits the form
Then the system should mark the ticket as valid

Required fields:
- user name
- device name
- issue category
- problem description
- business impact

AC2:
Given the user has opened the ticket creation form
When the user submits the form with one or more required fields empty
Then the system should return a validation result showing that the ticket is invalid and list the missing fields

AC3:
Given the user enters only spaces in a required field
When the user submits the form
Then the system should treat that field as empty and return it as a missing field

Mermaid flow:

flowchart TD
    A[User fills ticket form] --> B[User clicks submit]
    B --> C[Read ticket form data]
    C --> D[Check required fields]
    D --> E{Are all required fields completed?}
    E -->|Yes| F[Return valid result]
    F --> G[Allow ticket generation]
    E -->|No| H[Return invalid result]
    H --> I[List missing fields]
    I --> J[Show validation errors to user]

Task:
Write the logic for this feature as a Pure Function in JavaScript.
It must have no side effects, be stateless, and return a predictable output.
Do not modify the DOM, do not use localStorage, do not make API calls, and do not use global variables.
```

---

## AI output

```js
function validateTicketForm(ticketData) {
  const requiredFields = [
    "userName",
    "deviceName",
    "issueCategory",
    "problemDescription",
    "businessImpact"
  ];

  const missingFields = requiredFields.filter((field) => {
    const value = ticketData[field];
    return typeof value !== "string" || value.trim() === "";
  });

  return {
    isValid: missingFields.length === 0,
    missingFields
  };
}
```

---

## Did the AI succeed on the first try?
Yes, the AI succeeded on the first try. The generated function follows the pure function rule because it only receives input and returns output.

It does not:
- modify the DOM
- use global variables
- use localStorage
- call an API
- change external state

The same input will always return the same output.

---

## Did I have to adjust the requirements or diagram?
No major adjustment was needed. The BDD requirements were clear enough because they explained the required fields, the expected valid result, and how empty spaces should be handled.

However, I noticed that the Mermaid diagram was useful because it made the validation flow easier to understand. It also helped keep the generated function focused only on validation logic instead of UI behavior.

---

## Result of the experiment
The experiment showed that AI gives better and safer code when the task is clearly limited by:
- BDD acceptance criteria
- Mermaid logic flow
- pure function constraint
- explicit restrictions

This makes the AI output easier to review and less risky for the project.
