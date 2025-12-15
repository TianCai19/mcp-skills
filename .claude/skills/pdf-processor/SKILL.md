---
name: pdf-processor
description: Extract text, tables, and data from PDF files. Fill PDF forms, merge multiple PDFs, split documents, and convert PDFs to images. Use when working with PDF files, forms, document extraction, or when user mentions PDFs.
allowed-tools: Read, Grep, Glob, Bash
---

# PDF Processor

Extract text, tables, and data from PDF files, fill forms, merge documents, and convert formats.

## What this Skill does

- Extract text content from PDF pages
- Extract tables and structured data from PDFs
- Fill PDF forms with provided data
- Merge multiple PDF documents into one
- Split large PDFs into smaller documents
- Convert PDF pages to images (PNG, JPEG)
- Search for specific content within PDFs

## Requirements

Install required packages:
```bash
pip install pypdf pdfplumber PyPDF2
```

For advanced features (OCR, image conversion):
```bash
pip install pdf2image Pillow pytesseract
```

## How to use

### Extract text from a PDF
```python
import pdfplumber

with pdfplumber.open("document.pdf") as pdf:
    for page in pdf.pages:
        text = page.extract_text()
        print(text)
```

### Extract tables from a PDF
```python
import pdfplumber

with pdfplumber.open("document.pdf") as pdf:
    for page in pdf.pages:
        tables = page.extract_tables()
        for table in tables:
            print(table)
```

### Merge PDFs
```bash
pip install pypdf
python -c "
from pypdf import PdfWriter
writer = PdfWriter()
for pdf_file in ['file1.pdf', 'file2.pdf']:
    with open(pdf_file, 'rb') as f:
        writer.append(f)
with open('merged.pdf', 'wb') as output:
    writer.write(output)
"
```

### Fill PDF forms
```bash
pip install pypdf
python scripts/fill_form.py input.pdf filled.pdf
```

## Examples

When to use this Skill:
- "Extract all text from this PDF document"
- "Find specific information in this PDF"
- "Extract tables from this PDF report"
- "Merge these PDF files into one document"
- "Fill out this PDF form with data"
- "Convert PDF pages to images"

## Tips

- For scanned PDFs (images), use OCR with pytesseract
- Large PDFs may require splitting for better performance
- Table extraction works best with well-formatted PDFs
- Always handle PDF passwords if documents are encrypted
