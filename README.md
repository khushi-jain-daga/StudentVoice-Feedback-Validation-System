# StudentVoice — Student Feedback & Validation System
**Khushi Jain Daga | 23bcon1665 | Web Development Using AI | VII semester**

## Aim
Create a multi-page website with navigation menu, forms, validation, and responsive layouts using AI-assisted development tools.

## Project overview
A fictional student academic feedback portal with four separate HTML pages, a shared navigation menu, course directory, validated review form and local review dashboard. No backend or real university affiliation. Use fictional details only; contact details are validated but not persisted.

## Tools
HTML5, CSS3 Grid/Flexbox, JavaScript, DOM API, regular expressions, FormData, localStorage. AI assistant: ChatGPT.

## Architecture
![Architecture](architecture.svg)

## Procedure
1. Define four pages and shared responsive shell.
2. Render searchable demo course directory and prefill selected course via URL parameters.
3. Validate identity, contact, course, two ratings, feedback length and declaration on the client.
4. Show inline errors, valid-field progress, character count and preview dialog.
5. Save non-contact review fields only after confirmation; read saved reviews to calculate averages and filter results.

## AI development brief
Build a responsive four-page student feedback portal in HTML/CSS/vanilla JS. Include meaningful navigation, real-time regex validation, accessible rating controls, review preview, local persistence and a searchable dashboard. Highlight student attribution on each page.

## Project structure

```text
StudentVoice/
├── index.html          # Overview
├── courses.html        # Searchable faculty and course directory
├── review.html         # Validated feedback form
├── dashboard.html      # Local review analytics
├── style.css           # Shared responsive styling
├── script.js           # Validation, DOM events and persistence
├── architecture.svg    # Workflow diagram
├── screenshots/        # Output evidence instructions
└── README.md
```

## Run
From this folder: `python -m http.server 8003` then open http://localhost:8003. No npm or API key needed. Use the same origin on every page.

## Testing checklist (manual browser verification pending)
- Navigate all four pages; check 360, 768 and 1440 px widths.
- Submit blank form; verify errors and focus on first invalid field.
- Enter malformed roll number, email and phone; verify rejection.
- Select two ratings, enter sufficient feedback and confirm declaration.
- Preview, edit and confirm a valid review; verify dashboard and reload persistence.
- Search, filter and delete a local review.
- Verify no name, roll, email or phone is stored in localStorage.

## Result
Source implements multi-page navigation and client-side form validation with a local feedback demonstration. Browser verification and genuine output screenshots are still required.

## Page and feature reference

| Page | Functionality |
| --- | --- |
| Overview | Introduces the academic feedback workflow |
| Faculty & courses | Search and department filter; course selection prefills the review form via URL parameters |
| Submit review | Field-specific validation, two star ratings, progress, character count and confirmation dialog |
| Review dashboard | Total reviews, average teaching and satisfaction ratings, search, department and minimum teaching rating filters, deletion |

## Validation rules

| Field | Accepted input |
| --- | --- |
| Student and faculty names | 2–80 characters, starting with a Unicode letter; permitted name punctuation and spaces |
| Roll number | Two digits, 2–6 letters, four digits; case insensitive |
| Email | Basic email-format regular expression |
| Phone | Exactly ten digits |
| Department | CSE, ECE, ME or CE |
| Semester | 1–8 |
| Subject | One of the demo courses |
| Teaching and satisfaction | Each 1–5 |
| Feedback | 30–500 characters after trimming |
| Suggestions | Optional; textarea limited to 300 characters |
| Declaration | Must be checked |

## Data flow and implementation

The shared JavaScript detects the active page and attaches the relevant event handlers. FormData reads values; regular expressions and explicit allowed-value checks validate them. Input, change and focusout events update errors and readiness. On submit, the first invalid field receives focus. Valid entries open a native dialog for confirmation. Confirmed review data is stored under `studentvoice-reviews-v1` in localStorage. Name, roll number, email and phone fields are excluded from the saved object; users should also avoid putting personal information in free-text feedback. The dashboard computes averages across all saved reviews and filters the visible list. DOM text is inserted with textContent.

## Output evidence

Add genuine browser screenshots to the screenshots directory after local testing: overview, course search, invalid form, valid review preview and populated dashboard. No fabricated output screenshots are included.

## Conclusion

StudentVoice demonstrates a responsive multi-page website with shared navigation and client-side form validation, meeting the stated Experiment 04 objective. The review dashboard illustrates how validated data can be used for local analytics. This is a frontend academic prototype, not an authenticated or server-backed university feedback service. Browser acceptance testing remains pending.
