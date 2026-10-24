# QuoteProof AI

> **The Measurable, Guardrailed Quotation Co-Pilot for SME Packaging Manufacturers.**  
> Built for **PRAGYAN 2K26** (Track 4, Problem Statement 4-01).  
> **Core Principle**: *AI reads, code calculates, human approves, ledger proves.*

---

## 🚀 Key Features

1. **PII Masking & Privacy Shield**:
   - Automatically redacts Indian phone numbers (`+91`), email addresses, and personal signoffs before LLM submission.
   - Prevents confidential customer lead leaks when operating on public free-tier models.

2. **Deterministic Pricing Engine & Guardrails**:
   - Zero pricing hallucination: AI only extracts entities; all prices, bulk discount tiers, and 18% GST are calculated in Python `Decimal`.
   - **Margin Guardrail**: Blocks approval if profit margin falls below the 15% threshold.
   - **Stale Price Alert**: Warns when catalogue prices have not been reviewed in $>30$ days.

3. **Three-Case Stock Decision Engine**:
   - **Full Stock**: Seamless quotation generation.
   - **Partial Shortage**: Intercepts quotation and prompts owner to choose between partial shipment, backorder delivery date, alternative SKU, or decline.
   - **Out of Stock**: Provides an instant, copyable delayed dispatch reply.

4. **Immutable Evidence Ledger & Immutable Approvals**:
   - Every draft creation, human price revision, stock choice, and manager approval is permanently recorded in the audit trail.
   - Approved quotes are sealed and read-only to prevent unauthorized tampering.

5. **Empirical ROI Meter & 20-Inquiry Trust Scorecard**:
   - Live timer records time-per-quote comparing against real field baseline (10 mins manual vs 3 mins assisted).
   - Automated Trust Scorecard runner tests Hinglish, adversarial prompt injections, and missing specifications with 100% flag catch rate.

---

## 🛠️ Tech Stack

- **Backend**: Python 3.12+, FastAPI, SQLAlchemy, Pydantic v2, Google Gen AI SDK (Gemini Flash), Pytest.
- **Frontend**: React 18, Vite, Tailwind CSS, Lucide Icons, Vitest.
- **Database**: PostgreSQL (Supabase in production per `CONTEXT.md` Section 8) with automatic local SQLite fallback for developer agility.

---

## 🧪 Verification & Test Suite

The entire application is covered by unit, integration, and endpoint tests:

- **Backend (Pytest)**: **65 / 65 tests passing** (100%)
  ```bash
  cd backend
  python -m pytest app/tests -v
  ```
- **Frontend (Vitest)**: **11 / 11 tests passing** (100%)
  ```bash
  cd frontend
  npm test
  ```
- **Frontend Production Build**: **Clean build, 0 errors**
  ```bash
  cd frontend
  npm run build
  ```

---

## 🏃 Quick Start (Run Locally)

### 1. Backend Setup
```bash
cd backend
python -m venv venv
# Windows:
.\venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```
Backend will be live at `http://localhost:8000` with interactive docs at `http://localhost:8000/docs`.

### 2. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```
Frontend will be live at `http://localhost:5173`.

---

## 📚 Project Documentation

- [Live 3-Minute Demo Script](docs/DEMO_SCRIPT.md)
- [Pitch Deck & Problem Statement](docs/PITCH.md)
- [Judge Q&A Guide](docs/JUDGE_QA.md)
- [Real-Owner Field Validation & Baseline Timing](docs/REAL_OWNER_VALIDATION.md)
- [Project Specifications & Architecture Contract](CONTEXT.md)
