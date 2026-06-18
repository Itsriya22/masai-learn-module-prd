# Module-wise Lecture & Session Experience for Masai Learn

## Summary
Students need a single view that groups all lectures and live sessions by module, shows progress per module, and provides upcoming session alerts. This feature improves learning clarity, engagement, and course completion tracking.

## 1. Objective

- Provide students with a clear, module-centric structure for their course content.
- Display module-level progress so learners know how far they are in each module.
- Surface upcoming live or scheduled sessions with timely alerts.
- Increase student retention, planning, and course completion.

## 2. Problem Statement

Current app experience may present lectures and sessions in a linear or disconnected way, making it hard for students to:
- understand which lectures belong to each module,
- see how much of a module they have completed,
- track upcoming live sessions and prepare in advance.

## 3. Target Users

- Students enrolled in Masai Learn programs
- Learners taking multi-module courses
- Students who attend live sessions and self-paced lectures

## 4. Key Features

1. **Module Dashboard**
   - List of all modules in the student’s course.
   - Each module shows:
     - module title
     - short description
     - progress percentage
     - number of completed items vs total items
     - status badge (Not Started / In Progress / Completed)

2. **Module Detail Page**
   - Collapsible module sections with:
     - Lectures
     - Live Sessions / Assignments / Quizzes
   - Each item shows:
     - title
     - type icon (Lecture, Live Session, Quiz, Assignment)
     - duration / scheduled time
     - completion status
     - access CTA (Play, Join, View)
     - content format indicator (video, reading, exercise)

3. **Progress Tracking**
   - Module-level progress:
     - computed from completed items over total module items
     - displayed as progress bar + percentage
   - Course-level aggregate progress:
     - overall completion for entire course
   - Item-level progress:
     - lecture watched/completed
     - session attendance confirmed
     - quiz attempted

4. **Upcoming Session Alerts**
   - Alerts/notifications for upcoming live sessions:
     - next session in module
     - session date/time
     - time until start
     - “Join Now” button when active
   - In-app alert cards on dashboard
   - Optional push/email notification triggers

5. **Module-wise clubbing**
   - Data model groups lectures, sessions, assignments by module
   - Display modules in order defined by curriculum
   - Ability to expand/collapse module content

## 5. User Stories

### Primary Stories
- As a student, I want to view all lectures and sessions grouped by module, so I can understand course structure.
- As a student, I want to see my progress for each module, so I know what I have completed and what remains.
- As a student, I want alerts for upcoming live sessions, so I don’t miss scheduled learning events.
- As a student, I want each module’s lectures and sessions visible in one place, so I can plan my study flow.

### Secondary Stories
- As an admin, I want the module sequence to be configurable, so content can map accurately to the curriculum.
- As a student, I want to filter the module content by completed, upcoming, or pending items.
- As a student, I want module alerts to surface the next session only, so I can focus on the nearest event.

## 6. Functional Requirements

### F1: Module List View
- Display all modules.
- Show module progress indicator.
- Show module status.
- Show upcoming session summary if present.

### F2: Module Details
- Show list of lectures and sessions within module.
- Support nested sections if modules include sub-topics.
- Allow marking items as completed.
- Show item metadata: duration, type, status.

### F3: Progress Computation
- Each item contributes equally or by weighted score.
- Progress = (completed items / total items) * 100.
- Completed state is persisted.

### F4: Upcoming Session Alerts
- Identify live sessions scheduled for future dates.
- Show upcoming sessions on dashboard and inside relevant module.
- Trigger in-app alert if a session starts within configurable window (e.g. 24 hours).
- Provide CTA to join or add reminder.

### F5: Notifications
- Optional: push notification for upcoming session.
- Optional: email summary for sessions scheduled within next 24 hours.
- In-app alert center displays active alerts.

### F6: Data & API
- APIs return modules with content items and completion statuses.
- Support filtering by student and module.
- Provide next upcoming sessions endpoint.

## 7. Non-Functional Requirements

- Performance: Module dashboard loads in <2 seconds for active users.
- Accuracy: Progress values must reflect latest student completion state.
- Compatibility: Works on mobile app and web app if applicable.
- Accessibility: compliant with standard accessible design patterns.
- Scalability: supports courses with many modules and items.

## 8. UX / UI Behavior

### Dashboard Behavior
- Show modules in course order.
- Provide a summary bar at top:
  - Modules completed
  - Course progress
  - Next upcoming session
- Use clear colors:
  - Green for completed
  - Blue for in progress
  - Gray for not started

### Module Expansion
- Collapsed by default for scannability.
- Expand to view full lecture/session list.
- Each item uses an icon and badge:
  - Lecture
  - Live session
  - Completed
  - Upcoming

### Alerts
- Show upcoming session alert near top if a session is the next event.
- Provide a “Remind Me” or “Join Now” action.
- Display countdown or scheduled time.

## 9. Metrics / Success Criteria

- Adoption: percentage of learners using module view within first week.
- Engagement: increase in active session attendance rate.
- Completion: improvement in module completion rate.
- Retention: reduction in drop-off between modules.
- Alert interaction: number of users clicking alerts/join buttons.

## 10. Dependencies

- Existing curriculum data model and module mapping
- Lecture/session scheduling backend
- Student progress tracking system
- Notification engine (push/email) if alerts are implemented
- UI design and frontend implementation resources

## 11. Out of Scope

- Live session scheduling tools
- Content authoring workflows
- Detailed analytics dashboard beyond progress counts
- Peer chat or collaboration features

## 12. Implementation Considerations

- Data model should support:
  - `moduleId`, `moduleName`, `moduleOrder`
  - `items[]` with type, title, duration, schedule
  - `completionStatus`
- UI components:
  - Module card
  - Collapsible module content panel
  - Progress bar & status chips
  - Alert banner
- Consider incremental rollout:
  1. Module dashboard + module detail view
  2. Progress tracking
  3. Upcoming session alerts
  4. Notifications

## 13. Risks

- Incorrect progress calculation if item types are weighted inconsistently.
- Alert fatigue if session reminders are too frequent.
- Course content changes may require module re-sync.

## 14. Future Enhancements

- Add “Resume where I left off” on module cards
- Show historical attendance and module streaks
- Enable “Study plan” scheduling based on module deadlines
- Provide coach recommendations per module

## 15. Recommendation

Build this as a module view feature first, with progress and upcoming session visibility. Once the core experience is stable, extend it to notifications and personalized reminders.
