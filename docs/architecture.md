# DocketMender — proposed AWS architecture

DocketMender runs on AWS with each matter isolated, encrypted and auditable — and AI used only to draft and extract, never to decide.

## Request flow

1. Upload
2. Amazon S3
3. Textract
4. Bedrock
5. OpenSearch
6. DynamoDB
7. Lawyer review

## Services

### Amazon Textract

**Role:** Read every page

Extracts text, tables and layout from scanned and digital court documents, so even poor-quality scans become searchable, classifiable text.

### Amazon Bedrock

**Role:** Classify, extract and summarise

Classifies documents into your taxonomy, extracts parties and administrative dates, and drafts evidence-linked summaries — with prompts that require a citation for every statement.

### Amazon S3

**Role:** Store matter documents

Holds original files in matter-specific, encrypted prefixes with versioning, so the original evidence is always preserved exactly as uploaded.

### Amazon OpenSearch Service

**Role:** Power semantic search

Indexes document text and vector embeddings so lawyers can search a matter by meaning, with results filtered by the user’s matter access.

### Amazon DynamoDB

**Role:** Track classifications and deadlines

Stores document metadata, extracted deadlines, review decisions and the audit trail with fast, predictable reads for the case workspace.

## Principles

- **Matter isolation** — Each matter has its own encrypted storage and access rules.
- **Cited or omitted** — If a statement can’t be linked to a page, it doesn’t go in the summary.
- **No training on your files** — Client documents are never used to train shared models.

## Safeguards

- **Lawyers decide** — Extracted deadlines and summaries are drafts until a lawyer approves them.
- **Always cited** — Every summary statement links to the document and page it came from.
- **No legal advice** — DocketMender organises information. Legal analysis and strategy stay with counsel.
- **Privilege respected** — Matter-level access, encryption and a full audit trail protect privileged material.

## MVP scope

We start with a handful of active matters. Your team uploads their documents, reviews classifications and deadlines, and approves the first evidence-linked summaries.

- Secure matter workspaces
- Document classification with review
- Deadline extraction and approval
- Case inventory export
- Evidence-linked summaries
