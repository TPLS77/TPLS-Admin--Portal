TPLS ADMIN PORTAL — TEACHER MANAGEMENT UPDATE

This version keeps the working Admin login and adds separate teacher-management pages:

1. Leave Applications
   - Separate page for teacher leave requests
   - Pending / Approved / Rejected counts
   - Review request and approve or not approve
   - Admin response is saved for the teacher

2. Teacher Suggestions
   - Separate page for teacher suggestions
   - Search and status filters
   - Review and respond

3. Lesson Plans
   - Separate page for all submitted lesson plans
   - Filter by class and subject
   - Open full plan

4. Student Results
   - Separate page for student academic results
   - Groups results by student
   - Shows subject-wise percentage and grade
   - Shows WAITING when an assigned subject has no uploaded result
   - Combines uploaded marks for the total percentage and overall grade
   - Supports class, term and assessment filters

5. Teacher Notifications
   - Separate page for sending notifications to all or one teacher
   - Shows sent notification history

IMPORTANT
- Do not upload this version to GitHub until you have tested it locally.
- Run TPLS_ADMIN_TEACHER_INBOX_SETUP.sql in the same Supabase project. If you already ran the previous version, run this updated SQL again; it is safe because policies are dropped/recreated.
- Keep assets/school-logo.jpg in the same folder.


AUTOMATIC TEACHER REMINDERS
- When the Admin Portal loads or refreshes teacher-management data, it checks active teacher assignments.
- Result reminders: a teacher receives one daily reminder for an assigned class/subject when one or more active students still have no result uploaded by that teacher.
- Lesson-plan reminders: a teacher receives a reminder when no lesson plan exists for an assigned class/subject within the previous 7 days.
- Reminders are saved in teacher_notifications and appear in the Teacher Portal notification area.
- The system prevents duplicate reminders for the same assignment during the same day (results) or 7-day reminder window (lesson plans).
- Automatic reminders use the existing admin notification INSERT policy in TPLS_ADMIN_TEACHER_INBOX_SETUP.sql.

LAYOUT FIX
- Main content now stays within the available screen width.
- New Teacher Management pages use responsive layouts and horizontal scrolling only inside wide tables.
- Sidebar and Sign Out remain separated.


Notification attachments: run the updated TPLS_ADMIN_TEACHER_INBOX_SETUP.sql once in Supabase to create the secure notification-attachments bucket and attachment columns. Admin can attach one file up to 10 MB; teachers can open it from Notifications.


Updated behavior: All personnel are added through the same Add Teacher form. There is no separate Staff category. Designation is optional and may be an administrative leadership role while the person remains a Teacher with class/subject assignments.
