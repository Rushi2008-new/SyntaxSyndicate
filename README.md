 # Syntax Syndicate

An interactive multi-level debugging challenge where participants diagnose bugs, submit corrected code, and justify each solution.

## What It Includes

- C and Java debugging scenarios
- Four progressive levels: Beginner, Intermediate, Hard, and Extreme
- Three randomly selected tasks per language and level
- A 15-minute timer for every level
- Required responses for the bug, corrected code, and justification
- Anti-refresh and tab-switch detection for controlled submissions
- Google Sheets submission through a Google Apps Script web app
- A dedicated submission-complete confirmation page



## Submission Configuration

The form posts responses to the Google Apps Script URL stored in `Syntax Syndicate.html` in the `GOOGLE_APPS_SCRIPT_URL` constant.

To connect the project to a different Google Apps Script deployment:

1. Deploy the Apps Script as a web app.
2. Copy its `/exec` URL.
3. Replace the value of `GOOGLE_APPS_SCRIPT_URL`.
4. Confirm that the script accepts `POST` requests and writes the received fields to the intended Google Sheet.

The form submits through a hidden iframe and then redirects to `Submission Completed.html`, so participants see a clear completion message without leaving the challenge workflow.

Each final submission includes a unique `Submission_ID` and `Submitted_At` value. The Apps Script should store `Submission_ID` as a column and use it to detect duplicate deliveries when handling retries or high-concurrency traffic.

The completion page now waits for the hidden iframe response instead of redirecting after a fixed 250 ms delay. The 30-second fallback prevents a participant from being stuck if the endpoint does not return a load event, but it cannot guarantee storage by itself; the Apps Script must still write each POST atomically and handle concurrent requests.

## Important Behavior

- Refreshing the challenge page blocks the current submission.
- Switching tabs, minimizing the browser, or hiding the page triggers the anti-cheat submission flow.
- The timer starts when a language is selected and resets when a new level begins.
- Responses from completed levels are preserved as hidden form fields until the final submission.

## Browser Support

Use a current version of Chrome, Edge, Firefox, or Safari with JavaScript enabled.

## Project Goal

Syntax Syndicate is designed to test practical debugging ability, code correction, and technical reasoning in a structured competition format.

