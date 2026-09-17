# 🛡️ TrapShield
 
**Don't wait until it's too late — read the shape of a conversation, not just one message.**
 ### Conversation-Based Grooming, Manipulation & Online Scam Risk Detector

TrapShield is a privacy-focused web application that analyzes text conversations for patterns associated with **online grooming, manipulation, coercion, sextortion, financial scams, and other unsafe behaviors**.

Instead of judging a conversation from a single suspicious message, TrapShield looks at the **progression of the conversation** and identifies how different manipulation tactics appear and escalate over time.

> **TrapShield doesn't just ask "Is this message suspicious?" — it asks "What pattern is this conversation forming?"**

---

## ✨ Features

- 🔍 **Conversation Analysis**
  - Paste a conversation and analyze it on demand.
  - Supports messages formatted as `Sender: message`.

- 🧠 **Explainable Detection Engine**
  - Uses a transparent, rule-based detection system.
  - Every detected pattern can be traced back to the phrase that triggered it.
  - No black-box ML model is required.

- 🚩 **Multiple Manipulation Categories**
  - Isolation from support networks
  - Secrecy pressure
  - Love bombing
  - Moving conversations off-platform
  - Photo/sensitive-media requests
  - Financial requests
  - Threats, coercion & blackmail
  - Urgency and emotional pressure
  - Pressure to meet offline

- 📈 **Manipulation Journey**
  - Visualizes how risk changes throughout the conversation.
  - Displays cumulative risk across messages.
  - Highlights messages where manipulation patterns were detected.

- 📊 **Risk Classification**
  - `No signal`
  - `Low risk`
  - `Elevated risk`
  - `High risk`
  - `Critical risk`

- 📋 **Annotated Conversation**
  - Shows the original messages.
  - Flags individual messages containing detected patterns.
  - Explains which manipulation categories were triggered.

- 📉 **Escalation Detection**
  - Compares early and late portions of a conversation.
  - Identifies whether detected behavior is:
    - Escalating
    - Steady
    - De-escalating
    - Insufficient data

- 🛟 **Safety Guidance**
  - Provides contextual safety advice based on the patterns detected.
  - Includes guidance for situations involving secrecy, threats, photo requests, financial scams, and other risks.

- 🔒 **Privacy-Oriented Design**
  - Conversations are submitted for analysis on demand.
  - The application does not implement a conversation database or history system.

---


## 🧩 How It Works

TrapShield follows a simple analysis pipeline:

```text
User Conversation
       │
       ▼
Conversation Parser
       │
       ▼
Message-by-Message Analysis
       │
       ▼
Pattern Detection
       │
       ├── Isolation
       ├── Secrecy
       ├── Love Bombing
       ├── Off-Platform Push
       ├── Photo Requests
       ├── Financial Requests
       ├── Threats / Coercion
       ├── Urgency
       └── Offline Meeting
       │
       ▼
Risk Scoring
       │
       ▼
Conversation-Level Analysis
       │
       ├── Overall Risk
       ├── Risk Trend
       ├── Category Tally
       └── Flagged Messages
       │
       ▼
Interactive Dashboard
```
---

## 1. Conversation Input

The user enters a conversation one message per line:

Jordan: hey! I saw your comment
You: oh thank you!
Jordan: you're really mature for your age
Jordan: what's your snapchat?
Jordan: don't tell your parents we talk

TrapShield converts the conversation into structured messages containing:

sender
text
message index

## 2. Pattern Detection

The backend analyzes every message against predefined behavioral patterns.

For example:

"don't tell your parents we talk"

can trigger:

Isolation from support network

while:

"send me a pic right now"

can trigger:

Request for photos / sensitive media
Urgency / pressure tactics

## 3. Explainable Scoring

Each category has a severity weight.

Pattern	Weight
Love bombing	2
Secrecy pressure	3
Off-platform movement	3
Urgency / pressure	3
Isolation	4
Financial request	4
Photo request	5
Offline meeting	5
Threat / coercion	6

A message can trigger multiple categories, but the same category is only counted once for that message.

## 4. Risk Classification

Individual message scores are mapped to risk levels:

Score	Risk Level
0	No signal
1–2	Low
3–6	Elevated
7–11	High
12+	Critical

The application also calculates an overall conversation-level risk using a normalized combination of the conversation's average message score and accumulated score.

## 5. Conversation Trend

For conversations containing enough messages, TrapShield compares the beginning and end of the conversation.

This helps identify whether suspicious behavior is:

Early conversation
       ↓
Initial interaction
       ↓
Trust building
       ↓
Boundary pushing
       ↓
Pressure / requests
       ↓
Threats or coercion
       ↓
Later conversation

---

## 🏗️ Project Architecture
```
TrapShield/
│
├── backend/
│   ├── server.js
│   ├── detectionEngine.js
│   ├── package.json
│   └── package-lock.json
│
└── frontend/
    ├── index.html
    ├── package.json
    ├── vite.config.js
    │
    └── src/
        ├── App.jsx
        ├── App.css
        ├── index.css
        │
        ├── components/
        │   └── RiskTimeline.jsx
        │
        └── assets/
            └── ...
```
---

## ⚙️ Technology Stack

### Frontend

- React 19
- Vite
- Tailwind CSS
- Recharts
- JavaScript / JSX
- HTML / CSS

### Backend

- Node.js
- Express 5
- CORS
- JavaScript ES Modules

### Detection Engine

- Custom rule-based detection engine
- Regular-expression pattern matching
- Weighted risk scoring
- Conversation trend analysis

---

## 🔬 Detection Engine

The core of TrapShield is detectionEngine.js.
The engine contains a collection of categories, each with:
```
Category
    │
    ├── Label
    ├── Severity Weight
    ├── Explanation
    └── Detection Patterns
```
When a pattern matches, TrapShield records:

- Category
- Explanation
- Severity weight
- Exact matching snippet
This makes the detection process auditable and explainable.

---

## 🌐 API
The backend exposes two main endpoints.

POST /api/analyze

Analyzes a conversation.
### Request
```json
{
  "messages": [
    {
      "sender": "Jordan",
      "text": "Don't tell your parents we talk."
    },
    {
      "sender": "You",
      "text": "Why?"
    }
  ]
}
```
### Response
The API returns information including:
```json
{
  "messages": [],
  "flaggedMessages": [],
  "totalScore": 0,
  "overallRisk": "low",
  "trend": "steady",
  "categoryTally": {},
  "messageCount": 2,
  "guidance": []
}
```
GET /api/health

Basic backend health check.

### Response
```json
{
  "ok": true
}
```

---

## 📸 Project Screenshots

### Landing Page
<img width="852" height="914" alt="Trap1" src="https://github.com/user-attachments/assets/6630cfd0-8269-4703-9e66-515df2c0cf7b" />

### Analysis Report
<img width="879" height="999" alt="Trap2" src="https://github.com/user-attachments/assets/3560936d-a9d3-4fb7-928e-5d72e90b07cf" />
<img width="877" height="1017" alt="Trap3" src="https://github.com/user-attachments/assets/63e00ed6-f86f-42a7-ab86-aa6b2045274b" />
<img width="876" height="1007" alt="Trap4" src="https://github.com/user-attachments/assets/c67abdf4-e76b-420f-80bc-8db495fed3f4" />
 
### History Tab
<img width="1388" height="959" alt="Trap5" src="https://github.com/user-attachments/assets/93a67c0b-e041-4a27-b28f-9781b9716179" />

### The Guide
<img width="857" height="512" alt="Trap6" src="https://github.com/user-attachments/assets/0feea25d-fe52-4de2-9080-f584382e0a7f" />

### Downloaded Analysis Report PDF
<img width="985" height="955" alt="Trap7" src="https://github.com/user-attachments/assets/e395ffe7-c366-4713-91f6-b42be46ab9cd" />
<img width="983" height="964" alt="Trap8" src="https://github.com/user-attachments/assets/d80059a4-8c84-491a-a37e-d60adfb7a35c" />

---

## 🚀 Getting Started

### Prerequisites
Make sure you have installed:

- Node.js
- npm

Check your versions:
```bash
node --version
npm --version
```

## 1. Clone the Repository
```bash
git clone <YOUR_REPOSITORY_URL>
cd TrapShield
```

## 2. Start the Backend
Open a terminal:
```bash
cd backend
npm install
npm run dev
```
The backend runs on:
```text
http://localhost:4000
```
You can verify it with:
```text
cd frontend
npm install
npm run dev
```
Vite will provide a local development URL, normally:
```text
http://localhost:5173
```

Development note: The current frontend calls /api/analyze using a relative URL. If the frontend and backend are running on separate development ports, configure a Vite proxy or otherwise route /api requests to the backend at localhost:4000.

---

## 🧪 Example

You can use the built-in sample conversation from the interface.

A simplified example:
```text
Jordan: you're way more mature than most people your age
Jordan: nobody gets me like you do
Jordan: what's your snapchat?
Jordan: don't tell your parents we talk
Jordan: send me a pic right now
Jordan: why aren't you answering?
Jordan: if you really liked me you'd send it
Jordan: everyone will see it if you don't
```
TrapShield can identify a progression involving:
```text
Love bombing
      ↓
Off-platform movement
      ↓
Isolation
      ↓
Photo request
      ↓
Urgency / pressure
      ↓
Threat / coercion
```
The interface then presents the detected patterns, risk level, conversation trend, and safety guidance.

---

## 🎯 Why Rule-Based Detection?
TrapShield intentionally uses an explainable rule-based engine instead of an opaque machine-learning model.

This provides several advantages:

### Explainability

Every detection can be connected to a specific phrase and category.

### Transparency

Users can understand why a message was flagged.

### Auditability

Detection rules can be inspected and updated directly.

### No Training Dataset Required

The current system does not require a machine-learning training dataset to perform its analysis.

### Privacy

The application can analyze a conversation without requiring a persistent user profile or stored conversation history.

---

## 🛡️ Safety & Privacy
- TrapShield is intended as a support and awareness tool, not a replacement for human judgment, platform moderation, law enforcement, or professional support.
- A risk result does not prove that a person is a groomer, scammer, or criminal.
- Similarly, a conversation receiving no detected signals does not guarantee that it is safe.
- The detection engine only identifies patterns covered by its current rules.
- Users should consider the broader context and seek help from a trusted adult or appropriate support service when something feels unsafe.

---

## 🔮 Future Improvements
Potential future development includes:

 - Larger and more diverse pattern library
 - Context-aware detection
 - Multilingual conversation analysis
 - Detection of obfuscated/slang language
 - Platform-specific conversation import
 - Screenshot/OCR analysis
 - Improved contextual risk scoring
 - False-positive feedback mechanism
 - Anonymous analytics for improving detection rules
 - Browser extension integration
 - Local/offline analysis
 - More detailed safety-resource integration

---

## 📌 Current LimitationsTrapShield's current detection engine is rule-based.

Therefore:

- It can miss manipulation that is expressed using language outside its predefined patterns.
- A phrase can have different meanings depending on context.
- Detection does not establish malicious intent.
- The current system does not perform semantic understanding like a large language model.
- The quality of detection depends on the patterns defined in the detection engine.
- Long conversations can produce higher cumulative scores, although the overall risk calculation includes normalization.

These limitations are important when interpreting the result.

---

## 💡 Project Objective
TrapShield aims to make potentially harmful online conversations easier to recognize by turning subtle behavioral patterns into visible, explainable signals.

Rather than focusing exclusively on individual keywords, the project emphasizes the journey of manipulation:
```
Trust Building
      ↓
Boundary Testing
      ↓
Isolation / Secrecy
      ↓
Escalating Requests
      ↓
Pressure
      ↓
Coercion / Threats
```
The goal is to help users recognize warning signs before a situation becomes more serious.

---

## 👥 Intended Users
TrapShield can be useful as an awareness and educational prototype for:

- Teenagers and young internet users
- Parents and guardians
- Educators
- Online safety organizations
- Cybersecurity awareness programs
- Digital-safety researchers

---

## 📄 Disclaimer
- TrapShield is an experimental online-safety project.

- Its results should be treated as risk indicators, not definitive conclusions. The system does not determine whether a person is guilty of wrongdoing and should not be used as the sole basis for legal, disciplinary, or safety-critical decisions.

- If someone is experiencing threats, blackmail, sexual exploitation, or another immediate safety concern, they should seek help from a trusted adult or appropriate local authorities/support services.

---

## ⭐ Project Vision
Recognize the pattern. Understand the risk. Take action before it escalates.

## TrapShield — See the trap before it closes.
