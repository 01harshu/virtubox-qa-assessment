# Candidate & Submission Details
* **Candidate Name:** HARSH KUMAR
* **Mobile Number:** +91 9720218944
* **Email Address:** harshkumar9720218944@gmail.com
* **Assessment Title:** QA Assessment — Task Management Application
* **Submission Date:** September 11, 2026
* **Target Role:** QA Engineer / Software Tester

---
---

---
# VirtuBox QA Assessment — Task Management Application

QA Assessment submission for VirtuBox Infotech — Comprehensive Test Scenarios, Test Cases, and Risk/Bug Identification for Task Management Application.

---

## Part 1: Test Scenarios & Test Cases

### Module 1: Task Creation & Assignment

| Test Case ID | Test Scenario | Steps | Expected Result |
|---|---|---|---|
| TC_TC_01 | Create task with all valid details | 1. Click 'Create Task'<br>2. Fill Title, Description, Priority, Due Date<br>3. Select Assignee<br>4. Click 'Save' | Task is created and displayed in task list/board. |
| TC_TC_02 | Create task without mandatory fields | 1. Click 'Create Task'<br>2. Leave Title empty<br>3. Click 'Save' | Form validation error is displayed; task is not created. |
| TC_TC_03 | Assign task to multiple users | 1. Create/edit task<br>2. Select multiple assignees<br>3. Save | Task is assigned to all selected users and appears in their dashboard. |
| TC_TC_04 | Due date in the past | 1. Create task<br>2. Set Due Date to yesterday<br>3. Save | System shows error/warning or flags task as overdue. |

### Module 2: Task Status & Workflow

| Test Case ID | Test Scenario | Steps | Expected Result |
|---|---|---|---|
| TC_TS_01 | Drag and drop task across statuses | 1. Go to Kanban Board<br>2. Drag task from 'To Do' to 'In Progress' | Task status updates immediately and persists after page refresh. |
| TC_TS_02 | Status transition restrictions | 1. Move task directly from 'To Do' to 'Completed' (if workflow restricts it) | Workflow rules enforce required intermediate steps or prompt for missing details. |

### Module 3: Notifications & Real-Time Updates

| Test Case ID | Test Scenario | Steps | Expected Result |
|---|---|---|---|
| TC_NO_01 | Email/In-app notification on assignment | 1. User A assigns task to User B | User B receives in-app/email notification instantly. |
| TC_NO_02 | Notification on status change | 1. Assignee changes status to 'In Review' | Task creator and watchers receive status update notification. |

---

## Part 2: Risk & Bug Identification

### Bug Reports

#### Bug 1: Status mismatch between Kanban Board and Task Details Page
- **Severity:** High
- **Priority:** High
- **Description:** When a task status is updated via drag-and-drop on the Kanban Board, opening the Task Details modal still shows the old status until a hard refresh.
- **Steps to Reproduce:**
  1. Drag task "Setup DB" from *To Do* to *In Progress*.
  2. Click on the task to open Details modal.
  3. Observe status field in modal.
- **Expected Result:** Status in modal should show "In Progress".
- **Actual Result:** Status in modal shows "To Do".

#### Bug 2: Due Date notification triggers at wrong timezone
- **Severity:** Medium
- **Priority:** Medium
- **Description:** Overdue task reminder emails are sent based on UTC instead of the user's configured local timezone.
- **Steps to Reproduce:**
  1. Set local timezone to IST (UTC+5:30).
  2. Set due date to today 11:59 PM IST.
  3. Observe reminder triggers.
- **Expected Result:** Reminder arrives relative to IST deadline.
- **Actual Result:** Reminder arrives 5.5 hours early (UTC midnight).

---

## Part 3: Testing Strategy & Edge Cases

### Edge Cases
1. **Concurrent Editing:** Two users editing the same task simultaneously (race condition handling).
2. **Special Characters & Large Text:** Pasting 5,000+ characters or HTML/script injection into task description.
3. **Network Interruption:** Changing task status while offline/intermittent connectivity.

### Suggested QA Tools & Frameworks
- **Functional & UI Testing:** Cypress / Playwright
- **API Testing:** Postman / RestAssured
- **Performance Testing:** JMeter
