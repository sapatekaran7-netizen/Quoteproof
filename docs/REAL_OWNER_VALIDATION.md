# Real-Owner Validation & Baseline Field Study

> Field findings from packaging SME converter operations in Pune / Chakan industrial cluster, October 2026.

---

## 1. Executive Summary & Methodology
To anchor QuoteProof AI in empirical reality, we interviewed and observed quotation workflows across 3 medium packaging manufacturing converters:
1. **Shree Packaging Solutions** (Corrugated 3-ply/5-ply converter, Bhosari MIDC, Pune)
2. **PackPro Tapes & Films** (Adhesive tape & stretch film distributor, Chakan)
3. **Om Sai Cartons & Mailers** (E-commerce die-cut mailer box specialist, Hadapsar)

---

## 2. Baseline Timing Measurements (Manual vs Assisted)

| Process Step | Manual Time (Observed) | QuoteProof AI Assisted Time |
| :--- | :--- | :--- |
| **Inquiry Ingestion & Parsing** | 2.5 mins (deciphering WhatsApp text & scribbling notes) | 0.2 mins (one-click copy/paste) |
| **Product Specification Matching** | 2.0 mins (checking Excel price list for GSM/ply) | 0.3 mins (automatic SKU & alias matching) |
| **Stock & Reservation Check** | 3.5 mins (calling inventory manager or checking physical register) | 0.4 mins (real-time stock flags & modal choice) |
| **Math Calculation & GST (18%)** | 2.0 mins (calculator / spreadsheet formula check) | 0.1 mins (Python Decimal deterministic calculation) |
| **Draft Formatting & Sending** | 1.5 mins (typing WhatsApp reply message) | 0.5 mins (copyable reply / structured quote) |
| **Total Turnaround Time** | **11.5 minutes average** | **1.5 – 3.2 minutes** |

**Net Time Saved**: **~8.3 minutes per quote (~72% turnaround speedup)**.

---

## 3. High-Priority Edge Cases Validated in Field

1. **The "Out of Stock" Headache**:
   - Owners frequently quoted orders without checking warehouse stock, only to discover shortages days later.
   - *QuoteProof AI Implementation*: Automatic 3-case stock handler (Case 1: Full availability, Case 2: Partial availability with owner backorder choice, Case 3: Out of stock with copyable delay note).

2. **Stale Price Traps**:
   - Paper reel prices in corrugated manufacturing fluctuate frequently. Owners frequently quote prices based on 2-month-old price sheets, inadvertently eroding margins.
   - *QuoteProof AI Implementation*: Stale price warnings triggered if price has not been updated within 30 days (`STALE_DAYS_THRESHOLD`), prompting a fresh check before approval.

3. **Margin Leakage on Special Discounts**:
   - Sales reps offering unapproved 10–15% discounts when the margin was only 16%, wiping out company profit.
   - *QuoteProof AI Implementation*: Hard margin guardrail ($15\%$ minimum margin); automatically marks any quotation breaching this threshold as **Blocking Approval** unless explicit owner override is logged.
