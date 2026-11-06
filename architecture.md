Jordan Dennis

# Project 4 | Student Task Tracker architecture

CSCI4221 · Group 3 · Sprint 4

## 1. Description of the container

In Project 3, a student saved assignments in one browser. In the proposed cloud design, the student can sign in on a laptop or phone and see the same deadlines. The browser sends HTTPS requests to a cloud-hosted web application. The application checks the student's identity and reads or writes records in one shared PostgreSQL database.

The design uses three tiers. The browser displays the task form and dashboard. A Node.js application validates requests and applies the task rules. PostgreSQL stores courses, tasks and completion records. Each student can access only their own courses and tasks.

Docker builds a read-only image from the Dockerfile. The image includes the Node.js runtime, installed dependencies, server code and browser files. A container is a running instance of that image. The Docker daemon is the background service on the host that creates and runs containers. The host supplies the database connection secret at startup. PostgreSQL runs separately so replacing the app container preserves saved assignments.

## 2. Components and necessary files

Proposed component assignments carry forward the Project 3 features.

| Owner | Component | Subcomponents and files proposed | Database use |
| --- | --- | --- | --- |
| Jordan Dennis | Create and edit tasks | Task form in `public/task-form.html`, submit handler in `public/task-form.js`, request validation in `routes/tasks.js`, SQL in `data/tasks.js` | Read the student's courses, insert a task, update or delete the selected task by ID |
| Gregory Hamilton | Organize and filter tasks | Course selector and due-date list in `public/dashboard.js`, course queries in `data/courses.js` | Maintain `courses` and join to `tasks` to show one student's assignments by course and due date |
| Tyjah Banks | Track completion | Completion control in `public/completion.js`, update handler in `routes/completion.js` | Insert or remove the task's row in `task_completions` and return its status |

**Shared files.** The Dockerfile defines the build and startup command. `package.json` and `package-lock.json` define the dependencies. `server.js` serves the browser files and routes API requests. `auth.js` identifies the signed-in student. `db.js` opens the database connection using the runtime secret. `db/schema.sql` defines the three tables and their constraints.

**Example.** A student adds “Database homework,” chooses CSCI4221 and enters a due date. The server checks the title, date and ownership of the selected course before inserting a task. The dashboard shows it as incomplete until a completion row exists. If the deadline changes, the form sends the existing task ID with the new date. The server verifies ownership and updates that same row.

## 3. Structure of the related database table

Jordan's table is `tasks`. One row represents one assignment for one course.

| Column | PostgreSQL type | Rule and purpose |
| --- | --- | --- |
| task_id | BIGINT GENERATED ALWAYS AS IDENTITY | Primary key used to reopen, update or delete the assignment |
| course_id | BIGINT | Required foreign key referencing courses.course_id |
| title | VARCHAR(150) | Required and must contain at least one non-space character |
| due_date | DATE | Required calendar deadline |
| notes | TEXT | Optional assignment instructions |

**Related tables.** Gregory's `courses` table has a generated BIGINT primary key `course_id`, a required TEXT `student_id` from the sign-in system and a required TEXT `course_code`. The pair (student_id, course_code) is unique. One student can own several courses, and each course can contain several tasks. The server checks the course owner on every task operation, including any move between courses.

Tyjah's `task_completions` table has a BIGINT `task_id` that is both its primary key and a foreign key to tasks.task_id. Its required `completed_at` timestamp with time zone defaults to the current time. Marking a task complete creates its one completion row. Reopening it removes that row. Deleting a task automatically deletes its completion row through an ON DELETE CASCADE constraint.
