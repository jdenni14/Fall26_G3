Jordan Dennis

# Project 4 | Meeting 2 | Review components and database use

Group 3 · Student Task Tracker · Sprint 4


**Date, time and meeting method:** [Enter details]  
**Attendees:** [Enter names of those present]

## Discussion guide

Ask each owner to report progress since meeting 1. Trace adding an assignment, filtering by course and marking work complete. Check the proposed files, table keys and how the server restricts access to the student who owns the course.

## Sprint backlog

Proposed owners, reviewers and estimates. Update them to match the meeting.

| PBI | Status | Sprint | Estimate | Assigned | Reviewer |
| --- | --- | --- | --- | --- | --- |
| Task entry files and tasks table | [Actual status] | 4 | 2 hours | Jordan Dennis | Gregory Hamilton |
| Course filter files and courses table | [Actual status] | 4 | 2 hours | Gregory Hamilton | Tyjah Banks |
| Completion files and task_completions table | [Actual status] | 4 | 2 hours | Tyjah Banks | Jordan Dennis |

## Meeting record

Jordan: I drafted the tasks table. Each assignment gets a task ID so changing a due date updates the same assignment.
Gregory: Gregory drafted the courses table. Each task uses a course ID so the dashboard can show assignments for the selected course.
Tyjah: Tyjah drafted the task_completions table. Marking a task complete records its ID and the time it was finished.
Proposed decision: Connect tasks to courses by course_id and completion records to tasks by task_id.
Next step: Check that one assignment can be added, filtered by course, and marked complete using the proposed design.