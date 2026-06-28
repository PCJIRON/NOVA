# NOVA GLOSSARY
*Strict global data types. The compiler MUST NOT invent fields or types not listed here.*

---

## User
- **id** is string. Required is true. Must be unique.
- **email** is string. Required is true. Must be unique.
- **name** is string. Required is true.
- **password** is string. Required is true.
- **role** is Role. Default is "member".
- **createdAt** is date. Automatically set to current time.

## Task
- **id** is string. Required is true. Must be unique.
- **title** is string. Required is true.
- **description** is string.
- **status** is TaskStatus. Default is "todo".
- **priority** is Priority. Default is "medium".
- **assignee** is User. *Reference to a User.*
- **teamId** is string. Required is true.
- **createdBy** is User. Required is true.
- **createdAt** is date. Automatically set to current time.
- **updatedAt** is date. Automatically set to current time on update.

## Team
- **id** is string. Required is true. Must be unique.
- **name** is string. Required is true.
- **members** is array of User.
- **owner** is User. Required is true.
- **createdAt** is date. Automatically set to current time.

---

## VOCABULARIES

### VOCABULARY: Role
→ admin, member, viewer.

### VOCABULARY: TaskStatus
→ todo, in-progress, review, done, cancelled.

### VOCABULARY: Priority
→ low, medium, high, critical.

---

## AXIOMS

- AXIOM: MAX_TEAM_SIZE is 50.
- AXIOM: MAX_TITLE_LENGTH is 200.
- AXIOM: SESSION_EXPIRY_HOURS is 24.
