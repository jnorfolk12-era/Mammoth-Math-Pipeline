# Quality-Pipelines 📈  
*Google Sheets + Apps Script automation for Extractions → Solutions workflows*

Automates the **refresh → clean → dedupe → route** loop so humans spend time on judgement calls, not plumbing.

| Pipeline | Button / Trigger (menu **Task Tools**) | Raw Connected Sheets | Primary Outputs |
|----------|----------------------------------------|----------------------|-----------------|
| **Completed Extractions** | `runAllExtractions()` | *All Problems in Solutions – Ext* (corpus) <br> *Completed Extractions* (pending) | *Completed Extractions – Cleaned* → partitions to **Audit for delivery** (AA-AC overrides) / **Solutions** / **Holding** |
| **Approved & Completed Solutions** | `runSolutions()` | *Delivered Solutions – Ext* (corpus) <br> *Approved and Completed Solutions – Ext* (pending) | *Approved and Completed Solutions – Cleaned* → partitions to **Clean Solutions Audit** (U-W overrides) / **Solutions → Pause** |

---

## ✨ Features
* **One click** or **scheduled trigger** fully refreshes data.
* Exact-ID and near-text duplicate detection (Jaccard ≥ 0 . 90).
* Diagnostic columns **P-T** (`is_exact_duplicate_id` … `similarity`).
* Auditor-friendly override columns that *never* get overwritten:
  * Extractions AA–AC | Solutions U–W
* 50 000-character truncator keeps Sheets within cell-size limits.
* Everything configurable in a single `CFG` object.

---

## 🔧 Installation

1. **Google Sheet setup**  
   * Add Connected Sheets for the four BigQuery queries listed above.  
   * Name each tab exactly as in the table.
2. **Apps Script**  
   * Open **Extensions → Apps Script**.  
   * Replace the boilerplate with [`MASTER PIPELINE SCRIPT v 5.6`](./script.js) (see below).  
   * Authorize BigQuery access the first time you run a pipeline.
3. **Buttons / Menu**  
   * The script auto-creates a custom menu **Task Tools**.  
   * Optionally draw shapes and assign `runAllExtractions` / `runSolutions`.

---

## 🏃‍♂️ Running

```text
Task Tools → Run Completed Extractions Pipeline
Task Tools → Run Approved & Completed Solutions Pipeline
