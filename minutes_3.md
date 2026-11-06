Jordan Dennis

# Project 4 | Meeting 3 | Review the container and submission

Group 3 · Student Task Tracker · Sprint 4


**Date, time and meeting method:** [Enter details]  
**Attendees:** [Enter names of those present]

## Discussion guide

Ask each owner to report progress since meeting 2. Review what Docker builds, what its daemon runs and which files belong in the app image. Check that replacing the container preserves the shared database. Review the three architecture sections against the rubric.

## Sprint backlog

Proposed owners, reviewers and estimates. Update them to match the meeting.

| PBI | Status | Sprint | Estimate | Assigned | Reviewer |
| --- | --- | --- | --- | --- | --- |
| Task entry files and tasks table | [Actual status] | 4 | 2 hours | Jordan Dennis | Gregory Hamilton |
| Course filter files and courses table | [Actual status] | 4 | 2 hours | Gregory Hamilton | Tyjah Banks |
| Completion files and task_completions table | [Actual status] | 4 | 2 hours | Tyjah Banks | Jordan Dennis |

## Meeting record
- Jordan: I reviewed the task form and update flow. The server checks the required fields and confirms the student owns the course before saving.
- Gregory: Gregory checked how the dashboard would find one student’s assignments and sort them by due date.
- Tyjah: Tyjah checked how reopening a task would remove its completion record while keeping the assignment on the dashboard.
- Proposed decision: Package the server code and browser files in the Docker container. Keep PostgreSQL separate so replacing the container preserves assignments.
- Next step: Save the architecture document and all three minutes files in Project4, then upload the folder to GitHub.