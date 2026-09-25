# 6n8n Data Sanitization

## Project 06: Legacy Data Sanitization Pipeline

## 📖 Overview

This project demonstrates an automated data transformation pipeline built with **n8n**. It is designed to ingest messy, unstructured string data from legacy systems and sanitize it using core JavaScript techniques.

## 🏢 Business Problem

Legacy systems often export data in poorly formatted strings, for example:

```text
"  andi, SITI  , , Budi ,  "
```

This can lead to:

- Time-consuming manual cleanup in spreadsheets.
- Downstream automation failures caused by empty values or inconsistent casing.
- Inconsistent data formatting across business operations.

## 💡 Proposed Solution

This project uses an n8n **Code Node** to perform rapid data extraction, filtering, and transformation with JavaScript.

### Workflow Architecture

1. **Input (Mock Data Node)**

   Receives the raw string payload.

   <img width="643" height="308" alt="Workflow input node" src="https://github.com/user-attachments/assets/ec2079fc-0a4a-416f-814e-29e509767c68" />

2. **Processing (Code Node)**

   The Code Node:

   - Splits the string using a comma (`,`) as the delimiter.
   - Filters out empty or whitespace-only elements.
   - Trims extra spaces.
   - Standardizes the casing by converting values to uppercase.
   - Structures the output in the JSON array format required by n8n.

## 🛠️ Technical Specifications

- **Tools:** n8n and JavaScript
- **Methods:** `.split()`, `.filter()`, `.trim()`, `.toUpperCase()`, and a `for...of` loop

## 🔄 Before and After

### Raw Input

```json
{
  "daftar_peserta": "  andi, SITI  , , Budi ,  "
}
```

### Sanitized Output

```json
[
  { "nama_peserta": "ANDI" },
  { "nama_peserta": "SITI" },
  { "nama_peserta": "BUDI" }
]
```

<img width="890" height="823" alt="Workflow output" src="https://github.com/user-attachments/assets/5b6f4aef-725c-4927-90ed-417d73e4da51" />

## ⚠️ Error Handling and Edge Cases

### Empty Value Rejection

The script includes a logical check, `nama.trim() !== ""`, to ensure that double commas or trailing commas in the legacy data do not create empty database rows.

## 📈 Business Value

- **Data accuracy:** Reduces human error in manual data formatting.
- **Time savings:** Saves approximately 2–3 hours of manual administrative work per data batch.
- **Scalability:** Processes hundreds of names in milliseconds.

## 🙏 Acknowledgements

Developed in collaboration with **Gemini Pro**.
