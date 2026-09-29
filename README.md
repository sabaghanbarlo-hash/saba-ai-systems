# SABA AI — AI Business Systems Landing Page

A standalone, static landing page for an AI business automation service: AI Customer Assistant, AI Booking System and AI Lead Follow-Up (Capture, Book, Follow Up). It is fully separate from the portfolio site and shares no code with it.

Files: `index.html`, `styles.css`, `script.js`, `README.md`. Vanilla HTML/CSS/JS, no build step, no backend, no API keys, no external scripts.

## Run locally

Open `index.html` in a browser, or run `python3 -m http.server 8000` in this folder and visit http://localhost:8000.

## Deploy to GitHub Pages

1. Push this folder to a public repo (for example `saba-ai-systems`).
2. Repo Settings > Pages > Source: Deploy from a branch > `main` / `(root)`.
3. The site appears at `https://<username>.github.io/<repo>/`. All links are relative, so renaming the repo is safe.

## Connect the lead form to Google Forms (free)

The form validates on its own. Until configured it runs in configuration mode: it shows a notice and never claims a submission was saved.

1. Create a Google Form with short-answer/dropdown questions: Name, Business name, Business type, Website/Instagram, Email, Interested system, What to automate.
2. Link the Form to a Google Sheet (Responses tab).
3. Form menu (three dots) > Get pre-filled link. Fill every question with a sample value, click Get link, and copy the URL. Each `entry.NNNNNNNN=` in it is a field ID.
4. In `script.js`, edit the `CONFIG` block at the top:
   - `formAction`: the form URL ending in `/formResponse` (replace `/viewform...` with `/formResponse`).
   - `fields`: replace each `entry.YOUR_..._FIELD_ID` with the matching entry ID.
5. Commit. Submissions now go to your Sheet and the visitor sees Request Received.

Placeholders to change: `YOUR_GOOGLE_FORM_ACTION_URL` and the seven `entry.YOUR_..._FIELD_ID` values. No credentials are needed or stored. Note: the browser cannot read Google's response (no-cors), so test by checking your Sheet.

## How the demos work (all simulated)

- **Assistant chat:** keyword-matched scripted replies in `script.js` (`KB` list). No AI service is called.
- **Booking:** four steps (service, date/time, details, confirmation). Availability is generated locally; nothing touches a calendar.
- **Lead follow-up:** four example leads with history and timeline. Generate Follow-Up builds a message from a template; Send Demo Message only updates the local timeline.

Every demo is labeled Interactive Demo, Simulated Workflow or Portfolio Demonstration.

## Customize

- Copy and use cases: edit `index.html`.
- Colors and spacing: CSS variables at the top of `styles.css`.
- Demo business info, replies, services, times and leads: `script.js` (`KB`, `svcs`, `times`, `L`).
- Portfolio link: footer in `index.html`.
