Jordan Dennis

# Project 3 — Student Task Tracker

**Course:** CSCI4221  
**Group:** 3  
**Team:** Jordan Dennis, Gregory Hamilton, Tyjah Banks  
**Sprint:** 3 — Project 3  
**Product owners and development team:** All three members  
**ScrumMaster:** Course instructor

## Section 1: Feature

### F1: Create and Edit Tasks

**Assigned:** Jordan Dennis  
**Proposed reviewer:** Gregory Hamilton

Students can create a task with a title, course, due date, and optional notes. They can reopen a saved task to correct its information. This keeps assignment information in one place and reduces the chance of forgetting work.

**Expected behavior:**

- Title, course, and a valid due date are required. Missing or invalid information produces a clear message without saving an incomplete task.
- Saving adds the task to the dashboard with an Incomplete status.
- Editing updates the existing task instead of creating a duplicate.
- Tasks are stored in the current browser and remain available after a page refresh.

## Section 2: Persona

### P1: Maya Brooks — Student balancing several courses

Maya is a 20-year-old sophomore taking five classes. She is comfortable using basic websites and usually checks assignments on her laptop. Her goal is to record assignments quickly and remember each deadline. Her main frustration is having due dates scattered across class announcements and handwritten notes. She needs a short form with clear labels and a way to correct mistakes.

This is a fictional representative user for product design.

## Section 3: Scenario

### S1: Recording and updating an assignment

**Related feature:** F1  
**User:** P1  
**Starting condition:** The user can open the app in a browser; tasks already exist where needed.

After class, Maya learns that a database assignment is due next Friday. She opens the Student Task Tracker on her laptop and selects Add Task. She enters the assignment title, selects or enters the course, sets the due date, and adds a note about the instructions. When she saves, the assignment appears on the dashboard as Incomplete. Later, the instructor changes the deadline. Maya opens the task details, edits the due date, and saves again. The same task now shows the updated deadline. If she leaves a required field blank, the app tells her what to fill in before saving.

## Section 4: User Story

### US1: Add an assignment

As a student taking several courses, I want to add an assignment with its course and due date so that I can keep track of upcoming work.

**Acceptance criteria:**

- Given I am on the Add Task page, when I enter a title, course, and valid due date and select Save, then the task appears on the dashboard as Incomplete.
- Given a required field is missing, when I select Save, then the app identifies the missing field and does not create a task.
- Given I saved a task, when I refresh the page in the same browser, then the task is still available.
