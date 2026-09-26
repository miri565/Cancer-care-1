# Cancer Care Companion

A beginner-friendly Python + JSON prototype built with Streamlit.

## What it includes

- Login and account creation
- Personal details
- Carer / trusted adult contact
- Medication list with in-app daily reminder times
- Appointments
- Approximate distance from home to appointment
- Nearby hospital search using OpenStreetMap
- Daily questionnaire:
  - sleep
  - temperature
  - mood
  - tiredness
  - symptom checkboxes
  - message to carer
- Red / amber / green temperature check-in
- Carer email alerts
- Home dashboard
- Check-in streak
- Graphs and averages
- Consistency rewards
- Breathing exercise
- Cancer support links
- JSON storage

## Important safety note

This is a school / competition prototype, not a medical device.

The default high-temperature alert is 38.0 C because the NHS generally
describes 38 C or above as a high temperature. The low threshold is included
as a configurable prototype setting. Real users should follow thresholds and
instructions given by their own treatment team.

Do not rely on this app to decide whether someone needs urgent medical help.

## How to run it

### 1. Install Python

Install Python 3.11 or newer.

### 2. Open this project folder in a terminal

### 3. Install the packages

```bash
pip install -r requirements.txt
```

### 4. Start the app

```bash
streamlit run app.py
```

Streamlit will open the app in your browser.

## Where is the JSON?

The app creates and edits:

- `data/users.json`
- `data/email_outbox.json`

You can open these files in any text editor to see exactly what is being saved.

## Real email alerts

The app is designed so passwords are NOT stored inside JSON.

Set these environment variables before starting the app:

```text
CANCERCARE_SMTP_HOST
CANCERCARE_SMTP_PORT
CANCERCARE_SMTP_USER
CANCERCARE_SMTP_PASSWORD
CANCERCARE_FROM_EMAIL
```

If email is not configured, alerts are placed in:

`data/email_outbox.json`

This makes it easy to demonstrate the feature without exposing an email password.

### Example SMTP values

For a provider that supports SMTP over SSL, the port is commonly 465.

Use the SMTP settings given by the email provider. Do not put a personal email
password directly into `app.py` or `users.json`.

## Medication reminders

This prototype shows medication alerts inside the app when the app is open.

A real phone-style push notification at a set time every day needs a deployed
server / notification service running in the background. That would be a later
version of the project.

## Distance feature

Addresses are geocoded using OpenStreetMap through GeoPy/Nominatim.

Appointment and nearby-hospital distances in this prototype are straight-line
distances, not driving times.

The nearest hospital search uses the public OpenStreetMap Overpass API, which
can occasionally be busy or unavailable.

## Privacy

`users.json` can contain personal and health information.

For a school demonstration, use fake/demo data.

A real patient-facing app would need proper authentication, encryption,
permission controls, secure databases, data protection work and clinical review.
