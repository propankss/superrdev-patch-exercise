# Patch Exercise Notes

## Summary
I fixed four high-value issues across SQL, backend, and frontend layers:
1. Incorrect SQL AND/OR precedence caused incorrect status filtering and archived-task leakage.
2. An artificial Thread.sleep() blocked request threads and added unnecessary latency.
3. Search/status changes did not reset pagination to page 1.
4. Frontend fetch responses could race, allowing stale results to overwrite newer results; API errors could also leave loading stuck.

## What I chose not to change
I did not fix invalid pagination/status parameters, add debounce, or refactor the pagination architecture. I prioritized correctness and user-facing impact while keeping the patch focused and within the exercise scope.

## Biggest remaining risk
The API still relies on in-memory pagination and accepts pagination/filter inputs without explicit validation. With more time, I would add request validation and consider database-level pagination for larger datasets.

## AI/tools used
I used Antigravity and ChatGPT to inspect the codebase, identify and implement focused fixes, and reason about testing. I reviewed the generated changes myself, inspected the final diff, ran backend/frontend builds, tested the API, and manually verified pagination behavior.
