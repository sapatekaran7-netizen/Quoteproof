# QuoteProof AI — Pitch Deck & Executive Summary

> **The Measurable, Guardrailed Quotation Copilot for India's ₹2.5 Lakh Crore Packaging Manufacturing SMEs.**

---

## 1. The Problem: The High-Stakes WhatsApp Quotation Mess

Indian packaging manufacturers (corrugated boxes, bubble rolls, adhesive tapes, custom cartons) quote 20 to 50 bespoke inquiries daily. Inquiries arrive in unstandardized formats:
- Incomplete WhatsApp text: *"500 cartons 12x10x8 3-ply and some brown tape"*
- Urgent phone calls and Hinglish emails with embedded phone numbers and names (PII).
- Fluctuating raw material paper rates (kraft paper GSM, fluting starch, glue costs).

### The Real Cost of Today's Manual Workflow:
1. **Time Drain**: Taking 10–15 minutes per quote calculating tiers, checking stock, and drafting PDFs = 4+ hours per day lost.
2. **Hallucination / Misquoting**: Quoting based on stale price lists or forgetting minimum margin thresholds ($< 15\%$) leads to negative margin jobs.
3. **Ghost Stock Commitments**: Committing to 500 boxes when only 120 are in inventory, causing delayed deliveries and penalties.
4. **Disputes**: Sales reps changing prices ad-hoc in spreadsheets with zero auditability or accountability.

---

## 2. Why Generic GenAI Solutions Fail

| Generic AI Chatbot / Wrapper | QuoteProof AI |
| :--- | :--- |
| **Hallucinates Prices**: Invents plausible numbers. | **Deterministic Math**: AI only extracts entities; pricing is strictly calculated in Python `Decimal` using code rules. |
| **Leaks Customer PII**: Prompts sent directly to public LLMs. | **Mandatory Masking**: Phone numbers and emails are replaced with `[PHONE_1]`, `[EMAIL_1]` prior to LLM submission. |
| **Guesses Missing Specs**: Guesses box dimensions. | **Hard Guardrails**: Flags missing specs as **Blocking** flags; forbids quotation approval until resolved. |
| **Silent Discrepancies**: No log of what changed. | **Immutable Evidence Ledger**: Every draft, price edit, stock decision, and approval is logged with actor and timestamp. |

---

## 3. Product Architecture

```
[Raw WhatsApp / Email Inquiry]
              │
              ▼
   1. PII Masking Engine (Regex + Contextual Redactor)
              │
              ▼
   2. Gemini Extraction Schema (Pydantic / Structured Output)
      [Fallback: Rule-Based Basic Mode if Offline]
              │
              ▼
   3. Catalogue Matching & Stock Engine (Deterministic SKU + Fuzzy Alias)
              │
              ▼
   4. Margin Guardrails & Tier Pricing (Python Decimal Math)
              │
              ▼
   5. Validation Guardrails (Blocking vs Warning Flags)
              │
              ▼
   6. Owner Decision & Immutable Approval (Evidence Ledger Logged)
```

---

## 4. Key Metrics & Proof

1. **Measured Time Savings**:
   - Baseline Manual Quote: **10.0 minutes**
   - QuoteProof Assisted Quote: **3.2 minutes**
   - **68% reduction** in quotation turnaround time.
2. **Pricing Integrity**:
   - **0.0% pricing calculation error rate** (locked by unit tests and Decimal arithmetic).
3. **Trust & Reliability**:
   - **100% flag catch rate** on adversarial prompt injections and ambiguous descriptions across our 20-inquiry benchmark suite.
4. **Cost-per-Quote**:
   - Efficient Gemini Flash API tokens: **< ₹0.05 per quotation generated**.

---

## 5. Business Model & Roadmap

- **Target Customers**: Small & Medium Packaging converters, box makers, and packaging distributors (estimated 150,000+ units in India).
- **Pricing**: SaaS model at ₹1,499/month per plant (unlimited quotes, multi-device access).
- **Roadmap**:
  - P1: CSV price catalog bulk import, WhatsApp business API connector, print-ready PDF generator.
  - P2: Vernacular UI (Hindi, Marathi, Gujarati), supplier price feed auto-alerts.
