# AI Document Intelligence and Resume Shortlisting System

A browser-based tool that reads documents, extracts structured information from them, and shortlists resumes against a job description.

## Features

- **Upload** PDF, DOCX and TXT files (drag and drop supported)
- **Classify** documents as invoice, resume, contract, purchase order, report or other, with a confidence score
- **Extract** key fields such as invoice number, date, total amount, email, phone, parties and skills
- **Validate** each document against the required fields for its type and flag what is missing
- **Summarize** long text using extractive summarization
- **Ask questions** about a document using TF-IDF sentence retrieval
- **Export** results as structured JSON (copy or download)
- **Resume shortlisting:** rank uploaded resumes against a job description using skill match (70%) and text similarity (30%), with a Shortlist / Review / Reject decision
- **Dashboard** showing document counts, valid documents, missing fields and type breakdown

## Tech stack

- JavaScript, HTML, CSS
- NLP: TF-IDF, keyword scoring, regex-based field extraction
- PDF.js for PDF parsing, Mammoth.js for DOCX parsing

## How it works

1. The file is read and its text is extracted in the browser.
2. The classifier scores the text against keyword sets for each document type.
3. Regex rules extract fields, and a validator checks them against the required fields for that type.
4. Sentences are scored by term frequency for summaries and by TF-IDF for question answering.
5. For shortlisting, skills found in the job description are matched against each resume, and cosine similarity of the text adds to the score.

## How to run

1. Download `document-intelligence.html`.
2. Open it in a browser (an internet connection is needed to load PDF.js and Mammoth.js).
3. Upload a file, or click **Load sample invoice**.
4. For shortlisting, upload resumes, choose a role template or paste a job description, and click **Rank resumes**.

## Limitations

- Rule-based NLP, with no LLM yet
- Scanned PDFs without a text layer are not supported (no OCR)
- Skill matching uses a fixed skill list

## Future work

- Python FastAPI backend with REST endpoints
- MongoDB storage for processed documents
- LLM-based summarization and question answering
- OCR for scanned documents

