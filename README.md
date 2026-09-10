# MoneyMind 💸📈
### Smart Personal Finance & Multi-Account IPO Tracker
**Made with ❤️ by Chitranshu Shrivastava**

A high-performance, automated personal finance and IPO tracking system built **100% on free-tier tools**:
- **Database**: Google Sheets (cloud storage, zero cost, 100% data ownership)
- **Backend / API**: Google Apps Script (`Code.gs` v3.5)
- **Frontend / UI**: GitHub Pages (`index.html` / `webapp.html`) — Luxury Dark Fintech Design
- **AI Intelligence**: Google Gemini API (Structured JSON parsing, Hinglish Q&A, Multi-Key Rotation)
- **Vision OCR**: Direct client-side Gemini Vision for receipts, handwritten notes, and IPO screenshots
- **Multi-Account Automation**: Family PAN profiles, linked Gmail inboxes, iPhone Back Tap & Android PWA support

---

## 🏗️ Architecture & Why This Design Exists

```
iPhone Shortcuts (Back Tap / SMS)
  └── POST (Native iOS app, no browser CORS limitations) ──┐
                                                            ├──> Google Apps Script (Code.gs)
GitHub Pages (webapp.html / index.html)                    │      ├──> Google Sheets (Database)
  └── GET only (?action=X&...) (Browser CORS workaround) ──┘      └──> Gemini API (Multi-Key Rotation)
Client Browser (Camera / Screenshots)
  └── Direct Gemini Vision API call ───────────────────────────> Gemini 2.5 Flash
```

### Critical Design Rationale:

1. **GitHub Pages Hosting vs Apps Script `HtmlService`**:
   - Apps Script's `HtmlService` embeds pages inside a sandboxed iframe that permanently blocks browser microphone and camera access.
   - Hosting on GitHub Pages provides a secure top-level HTTPS origin, enabling live voice dictation and camera OCR across Safari and Chrome.

2. **GET-only Web App Communication (CORS Fix)**:
   - Apps Script `ContentService` cannot emit CORS preflight headers for browser `POST` requests.
   - All web app actions run cleanly via `GET` (`?action=X&...`), while native iPhone Shortcuts utilize `POST`.

3. **Client-Side Gemini Vision OCR**:
   - Heavy Base64 receipt images cannot be passed via GET URLs.
   - Images are processed directly from the client browser to Google Gemini API, and only the structured JSON result is written to Sheets.

4. **Multi-Key Gemini Rotation**:
   - Free-tier rate limits apply per Google Cloud project.
   - Storing 3 keys from 3 separate GCP projects in `GEMINI_API_KEYS` enables automatic rotation on HTTP 429 (`RESOURCE_EXHAUSTED`).

---

## 📊 Google Sheets Structure

Spreadsheet Name: **`Expense Tracker`**

| Tab | Name | Purpose |
|---|---|---|
| 1 | `Expenses` | Daily expense records (Date, Amount, Category, Method, UPI App, Bank, Note) |
| 2 | `Pending` | Async queue for iPhone Back Tap voice notes |
| 3 | `IPOs` | IPO applications (Company, Account, Amount, App No, Status, Member, Registrar) |
| 4 | `UPI Map` | Bank SMS and UPI handle mapping rules |
| 5 | `Budgets` | Monthly budget limits and spent tracking per category |
| 6 | `Config` | App configuration (stuck days threshold, budget alert %, AI custom rules) |
| 7 | `Family Profiles` | **Family PAN Cards, Demat Brokers (Zerodha, Groww), and linked bank accounts** |
| 8 | `Linked Gmails` | **Connected family Gmail IDs for automated IPO mandate scan** |

---

## 🎛️ MoneyMind Control Hub

The web app includes an interactive **Control Hub (🎛️)** with 6 self-service tabs:
1. **🆔 PAN Cards & Demats**: Add/manage family PAN cards (with privacy masking: `ABCDE••••F`), broker profiles, and primary banks.
2. **📧 Connected Gmails**: Link family Gmail IDs, copy auto-forwarding filter rules with 1 tap, and trigger instant inbox scans (`Scan Inboxes Now 🔄`).
3. **🏦 Banks & Accounts**: Dynamically add and manage bank accounts without touching any code.
4. **🏷️ Categories & Limits**: Set monthly category budget limits with live progress bars and alert warnings.
5. **🧠 Smart AI Rules**: Inject personalized rules for Gemini (e.g. merchant preferences, local slang).
6. **⚙️ Settings & Alerts**: Configure stuck mandate days, budget alert thresholds, and your custom display name.

---

## 🚀 Key Capabilities

### 1. Expense Tracking & OCR
- **Hinglish Voice / Text Parsing**: Natural inputs like *"Chai nashta 120 GPay SBI"* or *"dedh sau petrol auto"*.
- **Camera & Screenshot OCR (📷 / 📎)**: Click a photo of a handwritten diary, receipt, or UPI confirmation — Gemini parses it instantly.
- **Interactive Step-by-Step Tray**: Chip-based picker for hands-on expense entry without typing.
- **Analytics & Trends**: Monthly spend trend charts, doughnut category distribution, and live KPI cards.
- **Undo Capability**: 1-tap delete of the last logged expense directly from the chat feed.

### 2. Family IPO Tracker
- **PAN-Wise Allocation & Luck Scores**: Track applications per PAN profile with automatic allotment win-rate calculations.
- **Mandate Expiry & Stuck Money Alerts**: Automatic warning banner for any mandate pending for more than 7 days.
- **SMS Pattern Learner**: Paste any bank SMS to auto-teach AI new mandate formats.
- **Registrar Deep Links**: 1-tap lookup links for Link Intime, KFintech, and Bigshare.

---

## 📱 Mobile Compatibility

- **Android**: Open in Chrome ➔ Tap `⋮` ➔ Select **"Add to Home screen"** or **"Install App"**.
- **iOS**: Open in Safari ➔ Tap Share ➔ Select **"Add to Home Screen"**.
- **iPhone Shortcuts**: Works with Double Tap / Triple Tap Back Tap gestures and automatic Bank SMS triggers.

---

## 📂 Repository Contents
- **`Code.gs`**: Google Apps Script backend v3.5.
- **`index.html`** / **`webapp.html`**: Luxury dark fintech web app.
- **`SETUP_GUIDE.md`**: Step-by-step non-technical setup guide.
- **`README.md`**: Architectural documentation.
