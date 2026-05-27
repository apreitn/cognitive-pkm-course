# EXP-2026-05-28 Pattern Implementation

## Experiment topic
Using a classical design pattern to implement the ticket validation feature in an AI-assisted software project.

## Selected feature
Ticket form validation.

## Selected pattern
Strategy Pattern.

## Why I selected this pattern
I selected the Strategy Pattern because validation logic can grow over time. At the beginning, the project only needs required field validation. Later, it may need minimum length validation, email validation, category validation, or business impact validation.

The Strategy Pattern allows each validation rule to be implemented separately. This helps avoid one large function with too many conditions.

## Prompt provided to AI

```txt
I am developing a Service Desk Ticket Helper application.

Selected feature:
Ticket form validation.

Existing requirements:
The system must validate required ticket fields:
- userName
- deviceName
- issueCategory
- problemDescription
- businessImpact

The system must treat empty strings and strings with only spaces as invalid.

Task:
Implement this feature as a clean JavaScript module using the Strategy Pattern.

Requirements:
- Use modular JavaScript.
- Create separate validation strategies.
- Create a TicketValidator class that runs multiple strategies.
- Keep the code simple and readable.
- Do not use backend frameworks.
- Do not use localStorage.
- Do not modify the DOM inside validation logic.
- The validation logic should return predictable results.
- Follow the project AGENTS.md instruction: keep MVP code simple and avoid overengineering.
```

## Result
The AI produced a modular validation implementation with:
- RequiredFieldValidationStrategy
- MinimumLengthValidationStrategy
- TicketValidator
- createDefaultTicketValidator function

## Did the AI apply the pattern correctly?
Mostly yes. The AI applied the Strategy Pattern correctly because each validation rule was separated into its own class, and the main TicketValidator class did not contain all validation logic directly.

The validator only coordinates the strategies and combines their results.

## Did the pattern help?
Yes, the pattern made the code easier to understand and extend. If I need to add another validation rule later, I can create a new strategy instead of rewriting the whole validator.

## Was there any overengineering?
A little bit, but it is acceptable for this assignment. For a very small project, a simple function could be enough. However, because the task is specifically about design patterns and AI engineering harnesses, the Strategy Pattern is a reasonable choice.

## What I learned
Design patterns can help control AI-generated code by giving it a clear structure. Instead of asking AI to “make validation,” the pattern forces the AI to create separate responsibilities.

This makes the result easier to review and less likely to become spaghetti code.
