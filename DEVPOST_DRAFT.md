# Devpost submission draft

## Project name

API Skin AI

## Tagline

Understand today. Track what changes.

## Inspiration

Skincare decisions usually happen at a specific moment: before buying a product, after a frustrating change, or when someone wonders whether a routine is working. Raw AI scores do not answer the question users actually have—“What does this mean, what should I do next, and how can I compare responsibly?” API Skin AI was built to close that gap while treating a face photo, uncertainty, and user safety as first-class product concerns.

## What it does

API Skin AI guides a user through explicit consent and photo requirements, checks the selected image for basic suitability, and securely sends it to the YouCam Skin Analysis API. It converts returned visible skin indicators into plain-language scores and labels, then builds a focused AM/PM skincare plan using conservative product categories.

The experience also asks whether the user has a persistent painful, bleeding, open, or rapidly changing area. If selected, the app stops short of normal product experimentation and recommends qualified professional review. Users can optionally save a score-only summary in their browser, compare it with a later check-in, and delete the history at any time. Photos are never included in local history.

## How we built it

The application uses Next.js App Router, React, and TypeScript. The browser owns consent, local preview, quality feedback, and optional local history. A protected server route owns the YouCam credential and implements the complete asynchronous v2 workflow:

1. initialise the file with YouCam;
2. upload image bytes to the returned presigned URL;
3. create a Skin Analysis task with selected indicator actions; and
4. poll until the task succeeds or returns a usable error.

The server normalizes provider output into a stable consumer-facing contract and never returns the API key, file ID, task ID, presigned URL, raw photo, or raw provider payload. Mock mode is available for development but is labelled visibly in the interface.

## Challenges

The main challenge was designing around an asynchronous multi-step API without exposing sensitive provider details in the browser. We also had to translate cosmetic scores without implying diagnosis or creating appearance shame. Finally, privacy language had to be exact: the app itself does not add photo storage, while YouCam’s documentation states that provider-side uploaded files are removed automatically after 30 days.

## Accomplishments

- Complete YouCam file-upload, task-creation, and polling integration
- Consent before image selection rather than a buried checkbox at submission
- Visible retention, limitations, and local deletion controls
- Inclusive indicator language and conservative action-plan rules
- User-reported symptom escalation
- Score-only progress comparison with photo-free local storage
- Graceful handling for unsuitable images, API failures, rate limits, timeouts, and empty results
- Responsive and keyboard-accessible prototype with automated tests and CI

## What we learned

The difficult part of consumer AI is rarely the model call. Trust comes from everything around it: whether input is suitable, whether users understand data handling, whether a score is explained without overclaiming, and whether the next step is proportionate. The YouCam API provides the computer-vision foundation; the surrounding product logic turns it into a useful decision experience.

## What’s next

Next steps include controlled progress photography, optional user-defined skincare goals, retailer-catalog matching with transparent ingredient/category rules, signed-in encrypted sync with export/deletion controls, localisation, and a professional handoff summary. Before public release we would complete formal privacy, data-processing, security, accessibility, and clinical-claims reviews.

## Built with

Next.js, React, TypeScript, YouCam Skin Analysis API, Vitest, Vercel-ready server routes.

## Submission assets still required

- Public repository URL or private repository shared with `contact_event@PerfectCorp.com`
- Deployed web app URL
- 3–5 product screenshots
- Public 1–3 minute YouTube/Vimeo/Youku demo URL
