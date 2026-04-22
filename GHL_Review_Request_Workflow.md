# USS Academy — GHL Review Request Workflow (Ready to Build)

**Location:** `G0Bk9IDY9xnt7JJeDYsI` (USS Academy sub-account)
**PIT:** `pit-9e399bf9-3376-444e-9588-c41bff1f5899`
**Review link:** `https://g.page/r/CTZkhM-DO9ZwEBM/review`

---

## Workflow Overview

**Name:** `Review Request — Certificate Being Prepared`

**Purpose:** The moment Josh (or any instructor) marks a student's appointment as **complete** in GHL, the student receives an immediate SMS asking for a Google review while they're still physically in the room waiting for their paper Certificate of Completion. This is the single highest-conversion window for reviews — students are present, fresh off the training experience, and have an unavoidable few-minute wait.

Replaces the prior concept of a 2-hour delayed automation and the prior concept of a "while training is happening" automation. This is the only review automation USS Academy runs, and it fires once per completed appointment.

---

## Trigger

- **Trigger type:** Appointment Status
- **Status filter:** `Complete` (aka "Showed & Finished" depending on GHL calendar nomenclature)
- **Calendar filter:** All USS Academy class calendars (CWP, Beginner, Ladies Day, Law Update, etc.) — apply globally, not per-calendar, so every completed class appointment triggers

---

## Actions (in order)

### Action 1 — Send SMS

- **To:** `{{contact.phone}}`
- **From:** USS Academy registered A2P number (321-878-8089 once A2P approval lands; fallback to the GHL default registered number)
- **Body:**

```
Hi {{contact.first_name}}! Your certificate of completion is being prepared. While you wait — would you take 30 seconds to leave USS Academy a Google review? It means the world to us: https://g.page/r/CTZkhM-DO9ZwEBM/review — Thank you! USS Academy Team
```

### Action 2 — Tag contact

- **Tag:** `review-request-sent`
- **Why:** prevents the same student from receiving a second review request if they re-enroll in another class later; enables dashboard filtering on who has and has not been asked.

### Action 3 — Add note to contact

- **Note body:** `Review request SMS sent on {{workflow.execution_date}} — triggered by completed appointment.`

---

## Wiring (as soon as Josh's workflow builder is open)

1. GHL → USS Academy sub-account → Automation → Workflows → Create New Workflow
2. Name it exactly: `Review Request — Certificate Being Prepared`
3. Add Trigger: `Appointment` → status = `Complete`
4. Add Action 1: Send SMS with the body above
5. Add Action 2: Add tag `review-request-sent`
6. Add Action 3: Add Note with merge tag body
7. Toggle `Allow Multiple` OFF (one fire per contact per appointment)
8. Publish the workflow

---

## QA — test before activating

1. Create a test contact in GHL
2. Book the test contact into a test appointment on any USS Academy calendar (e.g. CWP Permit Course)
3. Mark the appointment status `Complete`
4. Confirm the SMS lands on the test phone within 60 seconds
5. Confirm `review-request-sent` tag applied
6. Confirm note written on the contact
7. Delete the test contact and test appointment
8. Flip the workflow live

---

## TCPA note

This SMS is transactional (post-service follow-up tied to the specific booked appointment and sent only once). It falls under the SMS consent checkbox every student accepts at booking. The review link is a plain `g.page/r/...` URL — do not wrap in a redirector that might be flagged as promotional marketing.

---

## Why this is the highest-converting window

- Student is physically present in the room waiting for their paper certificate (5-15 minute window)
- Emotional peak — they just finished a training they paid for and chose to be at
- Their phone is already in hand
- The SMS lands with a single tap to open the review widget
- No friction, no decision fatigue, no "I'll do it later"

Prior approaches (2-hour delay, 3-day delay, next-day email) all suffered from state decay. This single automation fires at the peak moment and nowhere else.

---

**Status:** Ready to build in the GHL UI. All copy, trigger logic, and tag/note actions are locked.
