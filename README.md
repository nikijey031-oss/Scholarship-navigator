🎓 Scholarship Navigator

Scholarship Navigator is an AI-assisted platform that helps Indian students discover scholarships they may qualify for based on their profile, understand eligibility requirements, access document checklists, and navigate to official application portals.

🚀 Problem Statement

Many students miss scholarship opportunities because information is scattered across multiple government websites, eligibility criteria are difficult to understand, and application processes can be confusing.

Scholarship Navigator simplifies scholarship discovery by providing personalized recommendations and clear guidance in a single platform.

✨ Features


Personalized scholarship matching
Eligibility-based recommendations
"Why You're Eligible" explanations
Required document checklists
Direct links to official application portals
Central and State scholarship support
Responsive, single-page interface
AI-assisted chat for questions about your specific matches


🛠️ Tech Stack

->Frontend


HTML5
CSS3 (custom properties, no framework)
Vanilla JavaScript (hash-based router, no build step)


->Data Management


In-file structured JS dataset of 49 central and state scholarship schemes
Browser localStorage for profile/application persistence


->AI Features


Claude API (Anthropic) — powers the scoped "Ask about your matches" assistant



This is a single self-contained .html file — no Next.js, no React, no separate build step or backend. We chose this deliberately: scholarship eligibility logic is deterministic rule-matching, not something that benefits from a heavier framework, and avoiding a backend removed deployment risk without losing functionality. See Responsible AI for why we also scoped AI usage narrowly rather than wiring it into core eligibility logic.



🧠 How It Works

Input — Students provide:


State
Education level
Category
Gender
Family income
Minority status (if applicable)
Disability status (if applicable)


Processing — The platform compares student information against each scheme's published eligibility criteria (state, category, education level, income ceiling, minority/gender/disability flags) and filters to matching schemes.

Output — Students receive:


Eligible scholarship matches
Plain-language explanations of why they qualify for each one
A document checklist per scheme
Official application portal links


🤖 AI Architecture

AI capability used


Scoped conversational assistant (Claude API), grounded only in the student's own matched schemes


Eligibility matching itself is rule-based, not AI-driven — we use deterministic logic (income thresholds, category/state/level filters) rather than a model for the core matching, since it needs to be consistent, auditable, and explainable. AI is used specifically for the conversational layer on top, where natural-language Q&A adds real value without replacing the auditable matching logic underneath.

Workflow

User Profile Input
        ↓
Eligibility Filtering (rule-based)
        ↓
Scholarship Matching
        ↓
Eligibility Explanation ("Why you're eligible")
        ↓
Document Guidance
        ↓
Scholarship Results
        ↓
(optional) Scoped AI Chat — answers questions using only the matched schemes above

🛡️ Responsible AI

Human-in-the-loop decision
The platform does not make final scholarship eligibility decisions. Final verification remains with authorized scholarship providers, who review official documents and applications. Scholarship Navigator never submits applications on a student's behalf — every "Apply" action ends with a handoff to the real official portal.

Data accuracy guardrail
Risk: Government scholarship eligibility rules (income limits, benefit amounts, documents) change yearly and are not available through a unified, authoritative API — figures from secondary sources can be outdated or conflicting.
Mitigation: Every scheme card, the scholarship directory, and the application receipt carry a clear disclaimer that figures are approximate, with a direct link to the relevant official portal to confirm current rules before applying.

AI scope guardrail
Risk: A general-purpose chatbot answering from broad knowledge could state confident but inaccurate scholarship facts, undermining the platform's accuracy stance.
Mitigation: The chat assistant's system prompt is restricted to only the specific schemes the logged-in student has matched to (passed in as structured context). It is explicitly instructed to refuse questions about schemes or facts outside that data rather than guess.

📈 Future Enhancements


Verified, source-linked data coverage extended to all 29 state schemes (currently focused on central schemes)
Renewal and deadline tracking
Document upload and auto-fill across applications
Multilingual support
Application tracking and status reminders
Scholarship comparison view


🎯 Impact

Scholarship Navigator aims to reduce the gap between students and the financial aid they're already entitled to, by making scholarship discovery accessible, transparent, and easy to understand — without overstating certainty the platform doesn't have.

👥 Team

Built for hackathon submission to improve access to educational opportunities for Indian students.

📄 License

This project is intended for educational and hackathon purposes. Scholarship eligibility data shown is approximate and for guidance only — always confirm details on the relevant official government portal before applying.
