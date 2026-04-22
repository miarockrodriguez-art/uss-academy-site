# USS Academy — GHL Review Request & Post-Class Workflows (Ready to Build)

**Location:** `G0Bk9IDY9xnt7JJeDYsI` (USS Academy sub-account)
**PIT:** `pit-9e399bf9-3376-444e-9588-c41bff1f5899`
**Review link:** `https://g.page/r/CTZkhM-DO9ZwEBM/review`

---

## System Overview — Two Different Completion Models

USS Academy class calendars run **two different completion models** depending on class type.

### Model A — Pass / Fail (CWP Concealed Carry Permit Class only)

The CWP class includes a state-required live-fire qualification. Students who pass receive their state-approved Certificate of Completion. Students who fail do not — they are invited to rebook and re-qualify. Because the two outcomes are operationally and emotionally very different, the CWP calendar uses custom **Passed** and **Failed** appointment statuses that branch the post-class communication.

| Status | Effect |
|---|---|
| **Passed** | Certificate issued flow + review request SMS fires immediately |
| **Failed** | Rebook follow-up SMS fires immediately. **No review request.** |

### Model B — Complete (every other class calendar)

Every other class calendar (Beginner, Basic Firearm Safety, Self-Defense Seminar / Street Legal™, Ladies Arsenal™, Law Enforcement, Military, Class G, Active Shooter, Skill Building, Tactical, Precision, Night Vision, etc.) uses the standard **Complete** appointment status. One SMS fires immediately: the review request.

This two-model distinction is canonical. Do not mix them. CWP is pass/fail. Everything else is complete.

---

## STEP 0 — Create the Custom Appointment Statuses (CWP calendar only)

The CWP calendar (calendar ID `PxMj2lH3dOGCLXR0vRsj`, slug `cwp-permit-course`) needs two custom appointment statuses added:

1. **Passed** — color: green
2. **Failed** — color: red

Where to add in GHL:
- GHL → USS Academy sub-account → Calendars → **CWP Permit Course** → Advanced settings → Appointment Statuses
- Add custom status `Passed`
- Add custom status `Failed`
- Save

Every other class calendar keeps the default statuses only. Do not add Passed/Failed to non-CWP calendars.

---

## WORKFLOW 1 — Review Request (Complete trigger) — every non-CWP class

**Name:** `Review Request — Certificate Being Prepared`

**Trigger:**
- Appointment Status = `Complete`
- Calendar filter: **exclude** CWP Permit Course calendar (`PxMj2lH3dOGCLXR0vRsj`). Apply to all other USS Academy class calendars.

**Actions:**

1. **Send SMS** to `{{contact.phone}}`:
   ```
   Hi {{contact.first_name}}! Your certificate of completion is being prepared. While you wait — would you take 30 seconds to leave USS Academy a Google review? It means the world to us: https://g.page/r/CTZkhM-DO9ZwEBM/review — Thank you! USS Academy Team
   ```
2. **Add tag:** `review-request-sent`
3. **Add note:** `Review request SMS sent {{workflow.execution_date}} — triggered by completed appointment.`
4. `Allow Multiple` = OFF (one fire per contact per appointment)

---

## WORKFLOW 2 — CWP Passed (review request)

**Name:** `CWP Passed — Certificate Issued + Review Request`

**Trigger:**
- Appointment Status = `Passed` (custom status)
- Calendar filter: CWP Permit Course (`PxMj2lH3dOGCLXR0vRsj`) only

**Actions:**

1. **Send SMS** to `{{contact.phone}}`:
   ```
   Hi {{contact.first_name}}! Congratulations — you passed your CWP qualification today. Your state-approved Certificate of Completion is being prepared. While you wait — would you take 30 seconds to leave USS Academy a Google review? It means the world to us: https://g.page/r/CTZkhM-DO9ZwEBM/review — Thank you! USS Academy Team
   ```
2. **Add tag:** `cwp-passed` + `review-request-sent`
3. **Add note:** `CWP Passed. Review request SMS sent {{workflow.execution_date}}.`
4. `Allow Multiple` = OFF

*Optional second step (manual toggle once FDACS flow is live):* an internal notification to the instructor queue that a certificate needs physical printing + signature.

---

## WORKFLOW 3 — CWP Failed (rebook follow-up, NO review request)

**Name:** `CWP Failed — Rebook Encouragement`

**Trigger:**
- Appointment Status = `Failed` (custom status)
- Calendar filter: CWP Permit Course (`PxMj2lH3dOGCLXR0vRsj`) only

**Actions:**

1. **Send SMS** to `{{contact.phone}}`:
   ```
   Hi {{contact.first_name}}, thank you for attending today's CWP class with USS Academy. We know this can be challenging — we'd love to help you prepare and try again. Reply to this message or call 407-305-8335 to schedule your next attempt. We believe in you! — USS Academy Team
   ```
2. **Add tag:** `cwp-failed` + `rebook-follow-up-sent`
3. **Add note:** `CWP qualification not passed. Rebook encouragement SMS sent {{workflow.execution_date}}. Do not add to review request queue.`
4. **Critical:** do NOT add `review-request-sent` tag. A failed student must not land in any review-request drip, ever.
5. `Allow Multiple` = OFF per appointment, but the student may re-appear on future CWP bookings — the workflow must re-fire cleanly on each new Failed status.

---

## Wiring Order (fastest path in the UI)

1. Confirm CWP calendar `PxMj2lH3dOGCLXR0vRsj` exists, then add `Passed` + `Failed` custom appointment statuses.
2. Build Workflow 1 (`Review Request — Certificate Being Prepared`) with calendar-exclude filter on CWP.
3. Build Workflow 2 (`CWP Passed`) filtered to CWP calendar + Passed status.
4. Build Workflow 3 (`CWP Failed`) filtered to CWP calendar + Failed status.
5. Publish all three workflows.

---

## QA — test sequence before activating

1. Create a test contact.
2. Book test contact into a test Beginner appointment → mark `Complete` → confirm Workflow 1 fires, Workflow 2/3 do not.
3. Book test contact into a test CWP appointment → mark `Passed` → confirm Workflow 2 fires, 1 and 3 do not.
4. Book test contact into another test CWP appointment → mark `Failed` → confirm Workflow 3 fires, 1 and 2 do not. Confirm `review-request-sent` tag is NOT applied.
5. Delete test contact and test appointments.
6. Flip all three workflows live.

---

## TCPA

All three SMS messages are transactional post-service follow-ups tied to specific booked appointments, sent once per appointment, covered by the SMS consent every student accepts at booking. Review link is the plain `g.page/r/.../review` URL — no tracking redirector.

---

## Why this split matters

- **Failed CWP students are vulnerable.** They just didn't pass a qualification on a high-stakes class. Asking them for a public Google review the same day is tone-deaf at best and 1-star-bait at worst.
- **Passed CWP students are euphoric.** They just cleared a live-fire qualification and are about to carry legally in Florida. Peak review conversion.
- **All other classes don't carry the same pass/fail pressure.** A Beginner class or a Ladies Arsenal™ event is "did you show up and engage." `Complete` status is sufficient.

This is a one-time setup. Once wired, it runs forever and scales to every future CWP class Josh runs.

---

**Status:** Ready to build in the GHL UI. All copy, trigger logic, calendar filters, tag/note actions, and pass/fail split are locked.
