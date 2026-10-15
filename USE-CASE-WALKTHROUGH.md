# RudraHealth AI — Provider Portal
## Complete End-to-End Use-Case Walkthrough

> A single realistic scenario that touches **every major flow** in the portal, from login to outcomes. Use it as a product walkthrough, QA script, or onboarding guide.

---

## 1. The Scenario & Cast

**Clinic:** Demo Clinic — an OUD (Opioid Use Disorder) treatment practice in Venice, CA, running a panel of **248 patients** across 5 providers.

**People:**
| Role | Name | What they do in this story |
|---|---|---|
| Clinical Provider | **Dr. Rivera** | Runs a daily panel, acts on high-risk patients, books visits, reviews outcomes |
| Clinic Admin | **Demo Clinic admin** | Oversees all locations, sets up automations and integrations |
| Patient (hero) | **J. Davis** | 34, OUD + AUD, on Suboxone 16mg, recovery score 12/100 — the highest-risk patient |
| Patients (supporting) | Marcus T., Maria O., Kevin W., Amy L. | Appear across appointments, surveys, and messaging |

**The week's goal:** Catch the deteriorating patient early, keep the panel engaged, automate re-engagement of alumni, and prove retention to stakeholders.

---

## 2. Flow 1 — Login & Role Selection

1. Open the portal. The **sign-in screen** shows the brand hero ("Care that *connects*, not a leaderboard") and the **Predict / Prevent / Retain / Recover** pillars.
2. Pick an **Organization type** (Clinical Provider) and **Sign in as**: **Doctor** or **Clinic Admin**.
   - **Doctor** → sees their own panel; location is a read-only pill (Venice, CA).
   - **Clinic Admin** → the location becomes a **dropdown** to switch between the clinic's locations (Venice, Santa Monica, Long Beach, Pasadena, Glendale), one at a time.
3. Work email pre-fills for the chosen role. Click **Sign in**.

**Result:** Lands on the Dashboard greeting **"Demo Clinic"**.

---

## 3. Flow 2 — The Daily High-Risk Alert

On the **first login of each day**, a modal automatically surfaces the single most at-risk patient:

- **J. Davis — 12/100**, 82% relapse risk (trending down), craving check-in overdue, last visit today.
- Two actions:
  - **View patient** → deep-links straight into J. Davis's detail page.
  - **Dismiss** → closes it (won't show again until tomorrow).

> This is the "don't make the clinician hunt for the priority" moment. It appears once per day, desktop only.

---

## 4. Flow 3 — The Dashboard

The command center. Top to bottom:

- **Header:** Demo Clinic + location, and a **Daily / Weekly / Monthly** time toggle.
- **High-Risk Patients** table (17 flagged) — each row shows recovery score (color gauge), diagnosis, MOUD, last check-in, days sober, care team, plus **Call / Message / Assign** quick actions. "View All" jumps to Patients & Care.
- **30-Day Retention in Care** — a light-blue bar chart rising to **76%**, well above the **42% national average** (dashed reference line).
- **Panel Risk Distribution** — High / Medium / Low split across 248 patients.
- **Recovery & Adherence** — panel median score (71/100) with MOUD adherence and check-in completion meters.

**Action taken:** Dr. Rivera sees J. Davis at the top, clicks the row → patient detail.

---

## 5. Flow 4 — Patients & Care → Patient Detail

1. **Patients & Care** lists the full panel as a searchable/filterable table (on mobile each row becomes a card).
2. Opening **J. Davis** shows the detail page:
   - Header card: avatar, **HIGH RISK** tag, diagnosis chip, today's focus ("Craving check-in"), and **Call / Message / Assign** buttons.
   - **Overview** tab: a recovery-health **gauge (12)**, a plain-language narrative of where the patient stands and today's focus, streak/milestone progress, and MOUD adherence.
   - **Progress** tab: trend charts over time.
   - **Rewards** tab: the patient-facing gamification (points store, bonus wheel, weekly goal, challenges, badges).

**Action taken:** Dr. Rivera clicks **Call**, logs the outreach, then **books a follow-up** → Appointments.

---

## 6. Flow 5 — Appointments

Three tabs: **Upcoming**, **Calendar**, **Past**.

- **Summary cards:** Today (8), This week (32), Confirmed (27), Telehealth (11) — each with a tinted icon and soft accent.
- **Upcoming list:** every row has a **patient avatar**, a prominent **date / time** block, a **type chip** (Telehealth / In-person / Phone), provider, reason, a **status pill** (Confirmed / Pending), and a clear **action hierarchy**: a primary action (**Join / Check-in / Call**) plus **Reschedule** and **Cancel**.
  - **Reschedule** → opens a modal to pick a new date/time.
  - **Cancel** → asks for **confirmation** before cancelling.
- **Calendar:** a month grid; **today** is marked with a blue date badge, and each day shows event chips color-coded by visit type (blue = Telehealth, green = In-person, amber = Phone). A legend sits below.
- **+ New Appointment:** opens a **full-screen modal** (Book Appointment) — patient, provider, type, date/time, duration, location, reason, reminders, and channels — then **Book Appointment**.

**Action taken:** Dr. Rivera books J. Davis's follow-up as a Telehealth visit with a 1-day SMS reminder.

---

## 7. Flow 6 — Survey Scheduling

Automate check-in surveys to patients.

1. **Active Schedules** lists running schedules (Edit / Pause on each).
2. **+ New Schedule** (or **Edit**) opens a **full-screen modal**:
   - Left: **Schedule name**, **Reminder Type** (Daily Check-In, COWS, PHQ-9, GAD-7, DAST-10…), **Send to** audience, **Frequency** (Every day / week / 2 weeks / Monthly / After appointment / Custom), **Send time**, **Delivery channels** (SMS / Email / WhatsApp / Push), and reminder messages.
   - Right: a **live phone mockup** showing exactly how the SMS lands on the patient's device (contact header "RudraHealth AI", the message bubble, and the opt-out line).
3. **Save & Activate Schedule** → returns to the list with a confirmation toast.
4. **Delivery History** tab shows sent / delivered / completed counts and completion rate per send.

**Action taken:** The clinic activates a **Daily Recovery Check-In** to all active patients at 8:00 AM via SMS + Email.

---

## 8. Flow 7 — Survey Management

The question-set builder.

1. The library lists every survey (STAR Daily Check-In, COWS, PHQ-9, GAD-7, SDOH…) with question count, types, and **Published / Draft** status. Each has **Edit**, **Preview**, and **Delete** (Delete asks for **confirmation** first).
2. **+ Create Survey** opens the **SurveyJS-style creator** (full screen):
   - **Designer** tab: drag question types from the left toolbox (Single/Multiple choice, Dropdown, Yes/No, Ranking, Short/Open text, Number, Rating, Scale, Signature, File…) onto the canvas.
   - Each **question card** has an editable title, options (add/remove), a type selector, and **Duplicate / Required / Delete**. Selecting a card opens a property panel on the right.
   - **Preview** tab renders the live patient form; **JSON Editor** shows the schema.
3. Save as **Draft** or **Publish**.

**Action taken:** The clinic tweaks the STAR check-in and publishes it.

---

## 9. Flow 8 — Notification Events (Automated Triggers)

The heart of engagement automation. **+ New Trigger** opens a 4-step **wizard** (full-screen modal with a stepper):

### Step 1 — Details
Name the trigger and pick a **type**:
| Type | Purpose |
|---|---|
| **Birthday** | Celebrate the patient's birthday |
| **Reward Milestone** | Fire when a patient hits a reward level |
| **Broadcast** | One-off or recurring message to a segment |
| **Wellness Check** | ~24h post-discharge "how are you?" |
| **Rating Request** | Post-visit 1–5 / 1–10 / emoji rating |
| **Post-Discharge Reminder** | Follow-up appointment reminder (7/14/30-day cadence) |

### Step 2 — Audience
Selectable pill-cards: **All Patients**, All Active, All High-Risk, All Sober 90+ days, Custom segment, and **Discharged alumni**.
- **Discharged alumni** reveals a timeframe picker — *"Reconnect with patients discharged [3 months / 6 months / 1 year / 18 months / 2 years] ago or longer"* — for alumni re-engagement.
- Type-specific timing also appears here (e.g., "Send X days after discharge", birthday timing, broadcast schedule: **Send now / Scheduled date & time / Recurring weekly / Recurring monthly**).

**Rating Request** adds response routing: a **rating scale** whose preview updates live (1–5 numeric, 1–10 numeric, or emoji), a **positive threshold**, and a **Review platform** (Google / Yelp / Healthgrades / Facebook / Trustpilot / Custom):
- Happy patients (4–5) → invited to post a public review on the chosen platform.
- Unhappy patients (1–3) → kept **private**; feedback captured internally and the **care team is alerted**.

### Step 3 — Message
Write the message with **personalization tokens** ({first_name}, {days_sober}, {level}, {provider}, {clinic}, {appt_date}…). A live **personalized preview** renders as you type.

### Step 4 — Delivery
Pick channels (SMS / Email / WhatsApp / Push). **Preview** shows the message in a phone mockup. **Save & Activate**.

**Action taken:** The clinic creates a **Broadcast** to **Discharged alumni (1 year ago or longer)**, scheduled, personalized with {first_name}, delivered via SMS + Email.

---

## 10. Flow 9 — Messaging Setup

Connect the actual delivery providers. Tabs for **Twilio**, **Bandwidth.com**, and **WhatsApp** — each with credentials/config and a test send. Templates are managed and approved here.

---

## 11. Flow 10 — Integrations

- **API Keys:** generate/revoke keys for external systems.
- **CRM Import:** pull historic records and waitlisted individuals from **Salesforce / HubSpot / services.io**.
- Provider connection status and feature comparison.

**Action taken:** The admin imports a waitlist from HubSpot so those contacts can be enrolled and messaged.

---

## 12. Flow 11 — User Management

Invite and manage team members with **roles**, **organization**, **data access**, and **status**. Each user row has edit controls. This is where the Doctor vs. Clinic Admin permissions are assigned.

---

## 13. Flow 12 — Communication Engagement

A funnel dashboard: **Sent → Opened → Responded** across channels, with open rates and response rates per communication type — so the clinic sees which automations actually land.

---

## 14. Flow 13 — Outcomes Data

The proof-of-value report: outcome metrics broken down by **OUD / AUD / Co-occurring / Total**, retention and recovery trends, and a **CSV export** for payers and quality reporting.

---

## 15. The Week, Tied Together (the "one complete use case")

> **Monday, 9:00 AM.** Dr. Rivera logs in. The **daily high-risk modal** flags **J. Davis (12/100)**. She clicks **View patient**, reads the recovery narrative, **calls** him, and **books** a Telehealth follow-up with an SMS reminder.
>
> **Monday, 9:20 AM.** On the **Dashboard**, retention is holding at **76%** vs. the 42% national average. She scans the high-risk table and assigns two patients to counselors.
>
> **Tuesday.** The clinic admin activates a **Daily Recovery Check-In survey** (SMS + Email, 8 AM) and tweaks the STAR question set in **Survey Management**.
>
> **Wednesday.** To win back people who fell out of care, the admin builds a **Broadcast** trigger to **Discharged alumni (1 year+)**, personalized and scheduled — then wires up delivery in **Messaging Setup** and imports a **HubSpot** waitlist via **Integrations**.
>
> **Thursday.** A **Rating Request** goes out after visits; 4–5★ patients are routed to **Google reviews**, while 1–3★ feedback stays internal and pings the care team.
>
> **Friday.** The admin opens **Communication Engagement** (opens/responses are healthy) and **Outcomes Data**, exports the CSV, and sends the retention story to the payer.

**Every major flow — login, alert, dashboard, patients, appointments, surveys, automations, messaging, integrations, users, engagement, outcomes — exercised in one coherent week.**

---

## 16. Cross-Cutting Behaviors (apply everywhere)

- **Confirmations** guard destructive actions (cancel appointment, delete survey).
- **Full-screen modals** are used for create/edit flows (New Appointment, New Trigger, Create Schedule, Create Survey).
- **Live previews** (phone mockups, personalized message preview, survey preview) show patient-facing output before anything sends.
- **Fully responsive:** on phones the sidebar collapses to a hamburger, data tables reflow into labeled cards, and layouts stack — no horizontal scrolling.
- **Consistent theming:** logo-blue (`#6C9FCC`) primary actions and active states; semantic green for recovery/positive, amber for pending, red for risk.

---

*Prototype v1.3 · Demo Clinic · for walkthrough and QA use.*
