# Patch Notes

## Changes made
- Corrected task-search SQL grouping so archived tasks are excluded and title/description matches are evaluated together with the optional status filter.
- Added validation for pagination: page must be at least 1, and page size must be between 1 and 100.
- Added handling for invalid task status values, returning HTTP 400 instead of an unhandled exception.
- Normalized search and status inputs using `Locale.ROOT`.
- Removed artificial request delay and made pagination offset calculations safer.

## What I did not change
- Kept the existing React UI, API response shape, data model, and overall application structure.
- Retained in-memory pagination after filtering to keep this patch focused.

## Remaining risk
- All matching tasks are still loaded before pagination, which may not scale for a large dataset. Database-level pagination would be a future improvement.
- Search and status-filter behavior should be verified together against the seeded dataset.

## Tools used
- Java 17, Spring Boot, H2, React/Vite, VS Code, PowerShell, Git, and ChatGPT for debugging guidance.
- Manually tested the API's search and invalid-input responses.
