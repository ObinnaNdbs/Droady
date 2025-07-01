![Droady (1)](https://github.com/user-attachments/assets/7c12fa90-0ccc-4aa5-b4d7-ad8b52584b63)

# 🏃‍♀️ DROADY — *Hope-Driven AI Fitness Platform*

> “Give people a glimpse of who they **could** become, and they’ll keep swimming.”

Welcome to the **public-facing blueprint** of DROADY.  
This repository **does not** contain proprietary code, model weights, or private datasets. Instead, it lays out the mental model, folder scaffolding, and cross-agency workflows that power the platform. Each sub-folder contains a dedicated `README.md` (coming soon) with sanitized diagrams and early-draft screenshots.

> **Status:** 🚧 *Stealth-mode build in progress — information intentionally redacted.*

---

## ✨ Vision

DROADY is a **multi-agentic, AI-powered ecosystem** that helps users transform their physiques while empowering real coaches to scale themselves digitally.  
We combine computer-vision analysis, diffusion-based physique generation, LLM-driven planning, and fully automated company ops (ads → onboarding → revenue share) — all orchestrated in **n8n**.

- **Hope-Driven Visual Progress**: Users upload images and instantly see idealised, achievable versions of themselves.
- **Coach Digitalisation**: Trainers clone their voice & style to earn passive income via AI avatars.
- **Full-Stack Automation**: Every recurring task — ads, email, finance — is wired into n8n so the company runs on autopilot.

---

## 📂 Repo Structure (High-Level)

```text
DROADY/
├── rater/          # Muscle-group scoring agency
├── planner/        # Workout & nutrition plan generator
├── avatar/         # Voice/LLM coach avatars (default + custom)
├── generator/      # Diffusion & video synthesis service
├── advertiser/     # Ad-buy optimiser & creative engine
├── emailer/        # Transactional + drip email flows
├── finance/        # Revenue share & payout analytics
├── automation/     # n8n JSON workflows (glue layer)
│   ├── intake.json       # Upload → Rating → Generator → Video
│   ├── weekly_report.json
│   └── ad_launch.json
├── docs/           # Architecture diagrams & compliance notes
├── LICENSE.txt     # Custom license (non-OSS)
└── README.md       # ← you are here
```
> Each top-level folder is an **agency** — a self-contained service (logic, prompts, n8n nodes) that collaborates with its peers via HTTP/webhook calls and Supabase tables.

---

## 🛠️ Core Technologies

| Layer                | Stack / Tools                                                |
|----------------------|--------------------------------------------------------------|
| **Automation Engine**| n8n (self-hosted)                                            |
| **Database & Auth**  | Supabase (Postgres + Row Level Security)                     |
| **Vector Store**     | Supabase Vector (pgvector)                                   |
| **LLMs**             | OpenAI GPT-4 / GPT-4o-mini (via OpenRouter), Claude, local fallback |
| **Diffusion Models** | Stable Diffusion XL + ControlNet (inference API)             |
| **Voice Avatars**    | ElevenLabs / PlayHT                                          |
| **Cloud Infra**      | Render / Railway (preview), AWS (scaling)                    |
| **Mobile Client**    | React Native (Expo) — *details withheld*                     |

---

## 🔄 End-to-End Workflow

1. **Intake** [`automation/intake.json`]  
   User submits **Front / Back / Legs / Face** images → Stored in **Supabase Storage** → Public URLs forwarded.

2. **Rating** [`rater/`]  
   GPT-driven evaluator scores **body fat %**, **FFMI**, and **muscle symmetry** → JSON results stored for embedding and coach memory.

3. **Prompt Generation** [`planner/`, `avatar/`]  
   Context-aware LLM agents build **personalized prompts** for both **image refinement** and **weekly fitness plans**.

4. **Physique Generation** [`generator/`]  
   SDXL-based Diffusion API returns refined physique imagery → 5-second **video flex** is auto-generated.

5. **Embedding & Memory**  
   Results embedded into **Supabase Vector (pgvector)** for **long-term tracking**, goal comparison, and RAG-enhanced personalization.

6. **Report & Coach Feedback**  
   Weekly email report sent to user → Coach avatar (voice clone) delivers verbal feedback using ElevenLabs.

7. **Ad & Growth Loop** [`advertiser/`]  
   Budget-aware agents launch **A/B creatives** on TikTok, Instagram, and YouTube → leads funnel directly into intake.

8. **Finance & Payouts** [`finance/`]  
   Stripe-based revenue share triggers payouts to coaches → Payout forecasts & analytics managed via a financial agent.

> ⚙️ All steps are orchestrated via **n8n** with nodes, delays, branches, and subflows. The system is built to run **end-to-end without manual input**.

---

## 🛰️ Agencies at a Glance

| Agency        | Mission                                                   | Key Endpoints / Artifacts                   |
|---------------|-----------------------------------------------------------|---------------------------------------------|
| `rater/`      | Objective physique scoring from images & stats            | `/rate`, `schema/body_score.json`          |
| `planner/`    | Adaptive training & nutrition plan generator              | `/plan`, `templates/*.yaml`                |
| `avatar/`     | Coach voice cloning, AI personalities & delivery agents   | `/synthesize`, `manifest.json`             |
| `generator/`  | Physique image enhancement & flex video generation        | `/image`, `/video`                         |
| `advertiser/` | Ad campaign launch + creative A/B testing (multi-platform)| `/launch`, `creative/*.md`                 |
| `emailer/`    | Drip campaigns, progress reports, onboarding series       | `/send`, `templates/*`                     |
| `finance/`    | Subscription management, revenue tracking & payouts       | `/ledger`, `scripts/stripe_sync.ts`        |

> Each folder has a `README.md` with:  
> - Workflow logic (redacted)  
> - Sanitized screenshots (early n8n flow states)  
> - Sample input/output schema (for demo purposes only)

---

## 🔐 Privacy & Licensing

- **User Data**: Stored in Supabase with strict **Row-Level Security (RLS)**.
- **Coach IP**: Voice models, embeddings, and training knowledge are encrypted and off-repo.
- **License**: This repo is **not open-source**. We will use a **custom license** forbidding any commercial reuse or model replication.

---

## 🚧 Roadmap (Public Milestones)

- [ ] Add `README.md` to each agency folder with redacted screenshots and early flows  
- [ ] Draft & apply **custom LICENSE.txt**  
- [ ] Publish high-level **architecture diagram** to `docs/architecture/`  
- [ ] Begin alpha testing of **intake → generation → report** with real users  
- [ ] Build & integrate long-term memory agent for evolving personalized coaching

> Internal roadmap is tracked privately (model training, feedback loop tuning, voice agent optimization, etc.)

---

## 🤝 Contributors & Contact

**Primary contact:**  
**Obinna Ndubuisi** — [LinkedIn](https://linkedin.com/in/obinna-ndubuisi)  
Discussions and requests are invite-only during stealth phase.

---

> *“Autonomy is not a feature, it’s an ecosystem.”* — **DROADY Core Team**
