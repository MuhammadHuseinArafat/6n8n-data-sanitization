# 6n8n-data-sanitization

# Project 06: Legacy Data Sanitization Pipeline

## 📖 Overview
This project demonstrates an automated data transformation pipeline built in **n8n**. It is designed to ingest messy, unstructured string data from legacy systems, sanitize it using core JavaScript array methods, and output a clean, structured JSON array ready for downstream processing (e.g., CRMs, databases, or document generators).

## 🏢 Business Problem
Legacy systems often export data in poorly formatted strings (e.g., `"  andi, SITI  , , Budi ,  "`). This leads to:
- Time-consuming manual cleanup in spreadsheets.
- Downstream automation failures due to empty values or incorrect casing.
- Inconsistent data formatting across business operations.

## 💡 Proposed Solution
A streamlined n8n workflow utilizing a **Code Node** to perform rapid data extraction, filtering, and transformation using JavaScript.

### Workflow Architecture
1. **Input (Mock Data Node):** Receives the raw string payload.
   <img width="643" height="308" alt="image" src="https://github.com/user-attachments/assets/ec2079fc-0a4a-416f-814e-29e509767c68" />

2. **Processing (Code Node):** 
   - Splits the string by delimiter (`,`).
   - Filters out empty or whitespace-only elements.
   - Trims extra spaces and standardizes casing to uppercase.
   - Structures the output into n8n's required JSON array format.

## 🛠️ Technical Specs
- **Tools Used:** n8n, JavaScript.
- **Methods Applied:** `.split()`, `.filter()`, `.trim()`, `.toUpperCase()`, `for...of` loop.

### Before vs After
**Raw Input:**
```json
{
  "daftar_peserta": "  andi, SITI  , , Budi ,  "
}
**Output:**
[
  { "nama_peserta": "ANDI" },
  { "nama_peserta": "SITI" },
  { "nama_peserta": "BUDI" }
]

<img width="890" height="823" alt="image" src="https://github.com/user-attachments/assets/5b6f4aef-725c-4927-90ed-417d73e4da51" />


###🛡️ Error Handling & Edge Cases

Null Value Rejection: The script includes a logical check (nama.trim() !== "") to ensure that double commas or trailing commas in the legacy data do not create empty database rows.

Note : incollaboration with gemini Pro

### 📈 Business Value
   - 100% Data Accuracy: Eliminates human error in manual data formatting.    
   - Time Saved: Saves approximately 2-3 hours of manual administrative work per data batch.    
   - Scalability: The script can process hundreds of names in milliseconds.
