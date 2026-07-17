# Demo and release testing checklist

## Automated checks

- [ ] `npm run lint`
- [ ] `npm run test`
- [ ] `YOUCAM_MOCK_MODE=true npm run build`
- [ ] No credential-like values in `git diff` or repository history

## Consent and privacy

- [ ] Photo selector cannot be reached until consent is checked
- [ ] Consent mentions YouCam processing, 30-day provider retention, and non-medical status
- [ ] Privacy page matches the implemented data flow
- [ ] Removing a selected photo clears the preview
- [ ] Saved local history contains no photo/data URL/file ID/task ID
- [ ] Delete-all removes local history and returns the empty state

## Photo validation

- [ ] Valid portrait JPG passes
- [ ] Valid portrait PNG passes
- [ ] GIF/HEIC/PDF/executable is rejected
- [ ] Empty file is rejected
- [ ] File over 8 MB is rejected
- [ ] Image under 640 Ã— 640 is rejected
- [ ] Extreme aspect ratio is rejected
- [ ] Very dark/bright image receives an advisory warning
- [ ] Multiple faces, no face, and large face angle show useful provider errors in live mode

## API and resilience

- [ ] Health endpoint reports mock/live mode without exposing secrets
- [ ] Mock mode result has a visible â€œDemo dataâ€ badge
- [ ] Missing live API key returns a safe configuration error
- [ ] Invalid API key returns a safe authentication error
- [ ] 429 returns a retryable busy message and `Retry-After`
- [ ] Poll timeout returns a retryable timeout message
- [ ] Provider empty result gives a clear retake action
- [ ] Browser never receives API key, file ID, task ID, presigned URL, or raw payload

## Results and safety

- [ ] All scores have labels, `/100`, and a text levelâ€”not color alone
- [ ] Lower priorities generate no more than two targeted routine additions
- [ ] Product recommendations are categories rather than unsupported product claims
- [ ] Patch-testing and product-label guidance are visible
- [ ] Symptom flag produces professional-review guidance and avoids strong-actives advice
- [ ] Non-medical disclaimer is visible on result screen
- [ ] Mock and live sources are distinguishable

## Accessibility and responsive QA

- [ ] Complete the flow using keyboard only
- [ ] Visible focus appears on every interactive control
- [ ] Labels are associated with checkboxes and file input
- [ ] Loading and errors are announced through status/alert semantics
- [ ] 200% zoom does not hide controls or require horizontal scrolling
- [ ] Test 320 px, 390 px, 768 px, 1024 px, and 1440 px widths
- [ ] Check light/dark OS contrast behavior and reduced-motion preference
- [ ] Run Lighthouse accessibility audit and resolve high-impact findings

## Live demo rehearsal

- [ ] Use a participant-approved test imageâ€”never an unconsented third-party face
- [ ] Confirm API units and key validity
- [ ] Confirm actions enabled on the account
- [ ] Run one full live analysis immediately before recording
- [ ] Keep a clearly labelled mock-mode deployment as contingency
- [ ] Ensure browser/terminal/API console contains no visible secrets in the recording
Explain
