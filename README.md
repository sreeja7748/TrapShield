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

1. Conversation Input

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
2. Pattern Detection

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
3. Explainable Scoring

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

4. Risk Classification

Individual message scores are mapped to risk levels:

Score	Risk Level
0	No signal
1–2	Low
3–6	Elevated
7–11	High
12+	Critical

The application also calculates an overall conversation-level risk using a normalized combination of the conversation's average message score and accumulated score.

5. Conversation Trend

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






