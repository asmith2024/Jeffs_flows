# Online Forms System – Flow Diagrams

The following Mermaid diagrams describe the key user journeys in an online forms system.

---

## 1. User Registration & Login Flow

```mermaid
flowchart TD
    A([Start]) --> B{Have an account?}
    B -- No --> C[Go to Sign-Up page]
    C --> D[Enter name, email & password]
    D --> E[Submit registration]
    E --> F{Valid details?}
    F -- No --> G[Show validation errors]
    G --> D
    F -- Yes --> H[Send verification email]
    H --> I[User clicks verification link]
    I --> J[Account activated]
    J --> K[Redirect to Dashboard]
    B -- Yes --> L[Go to Login page]
    L --> M[Enter email & password]
    M --> N{Credentials correct?}
    N -- No --> O[Show error message]
    O --> M
    N -- Yes --> K
    K([Dashboard])
```

---

## 2. Form Creation Flow

```mermaid
flowchart TD
    A([Dashboard]) --> B[Click 'Create New Form']
    B --> C[Enter form title & description]
    C --> D[Add a question]
    D --> E{Choose question type}
    E -- Short answer --> F1[Configure short-answer field]
    E -- Multiple choice --> F2[Add answer options]
    E -- Checkboxes --> F3[Add checkbox options]
    E -- Dropdown --> F4[Add dropdown options]
    E -- Date / Time --> F5[Configure date-time field]
    E -- File upload --> F6[Configure file-upload field]
    F1 & F2 & F3 & F4 & F5 & F6 --> G[Mark question as required / optional]
    G --> H{Add another question?}
    H -- Yes --> D
    H -- No --> I[Review form layout]
    I --> J{Save or discard?}
    J -- Discard --> K[Delete draft]
    J -- Save draft --> L[Form saved as Draft]
    L --> M([End – form ready for publishing])
    K --> N([End – no form saved])
```

---

## 3. Form Publishing Flow

```mermaid
flowchart TD
    A([Dashboard]) --> B[Open a Draft form]
    B --> C[Preview form]
    C --> D{Ready to publish?}
    D -- No --> E[Edit form]
    E --> C
    D -- Yes --> F[Configure publish settings]
    F --> G{Restrict responses?}
    G -- Yes --> H[Set allowed email domains or specific users]
    G -- No --> I[Leave form open / public]
    H & I --> J{Set response deadline?}
    J -- Yes --> K[Choose closing date & time]
    J -- No --> L[No deadline set]
    K & L --> M[Click 'Publish']
    M --> N[System generates unique form URL]
    N --> O[Form status changes to Published]
    O --> P{Notify respondents?}
    P -- Yes --> Q[Send email invitations with link]
    P -- No --> R[Copy & share link manually]
    Q & R --> S([Form is live and accepting responses])
```

---

## 4. Form Submission Flow (Respondent)

```mermaid
flowchart TD
    A([Respondent receives / finds form link]) --> B[Open form URL in browser]
    B --> C{Form still accepting responses?}
    C -- No --> D[Show 'Form closed' message]
    D --> E([End])
    C -- Yes --> F{Login required?}
    F -- Yes --> G[Prompt respondent to sign in]
    G --> H{Authorised?}
    H -- No --> I[Show access-denied message]
    I --> E
    H -- Yes --> J[Display form questions]
    F -- No --> J
    J --> K[Respondent fills in answers]
    K --> L{All required fields completed?}
    L -- No --> M[Highlight missing required fields]
    M --> K
    L -- Yes --> N[Click 'Submit']
    N --> O[System records response with timestamp]
    O --> P{Confirmation message configured?}
    P -- Yes --> Q[Show custom confirmation message]
    P -- No --> R[Show default thank-you message]
    Q & R --> S([End – response recorded])
```

---

## 5. Form Results Retrieval Flow (Form Owner)

```mermaid
flowchart TD
    A([Dashboard]) --> B[Select a Published form]
    B --> C[Open 'Responses' tab]
    C --> D{Any responses received?}
    D -- No --> E[Show 'No responses yet' message]
    E --> F([End])
    D -- Yes --> G[View response summary & charts]
    G --> H{Need individual responses?}
    H -- Yes --> I[Browse individual response detail view]
    H -- No --> J{Export data?}
    I --> J
    J -- No --> K([End – review complete])
    J -- Yes --> L{Choose export format}
    L -- CSV --> M[Download CSV file]
    L -- Excel --> N[Download Excel file]
    L -- PDF report --> O[Generate & download PDF report]
    M & N & O --> P{Apply filters before export?}
    P -- Yes --> Q[Filter by date range / question answer]
    Q --> R[Download filtered export]
    P -- No --> R[Download full export]
    R --> K
```

---

## 6. End-to-End Overview

```mermaid
flowchart LR
    A([Form Owner\nRegisters & Logs In]) --> B[Creates Form]
    B --> C[Publishes Form]
    C --> D([Respondents\nSubmit Responses])
    D --> E[Responses stored in system]
    E --> F[Form Owner\nRetrieves Results]
    F --> G{Analyse or Export?}
    G -- Analyse --> H[View summary charts\non dashboard]
    G -- Export --> I[Download CSV / Excel / PDF]
    H & I --> J([Insights gained])
```
