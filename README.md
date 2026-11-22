# S.r.l.Legal Tool - Automated Privacy and Trade Secret Redaction
Legal Background

Under Art. 2476(2) c.c., non-managing shareholders of an Italian Limited Liability Company (società a responsabilità limitata – S.r.l.) have a broad right to inspect corporate books and administrative documents. Because the Civil Code does not restrict which administrative records fall within this right, corporate minutes, contracts, and correspondence frequently contain two categories of legally protected information:

Personal Data (GDPR, Reg. (EU) 2016/679, Arts. 4–5): Tax identification numbers (Codice Fiscale), IBANs, and individual monetary figures relating to directors, shareholders, or third parties.

Trade Secrets (D.Lgs. 63/2018 & Directive (EU) 2016/943): Commercially sensitive information such as patent identifiers, pricing models, strategic projects, and supplier/partner agreements.

This tool provides a two-tier redaction pipeline that sanitizes documents before disclosure while preserving the original file untouched.

How It Works

The script (legal_tool.py) uses only the Python Standard Library (os and re) and executes a four-stage workflow:

Flexible Document Ingestion (interface):

Option 1: Multiline text paste directly in the terminal (terminated by typing END on a new line).

Option 2: Loading an existing UTF-8 .txt file after verifying its path on disk.

Tier 1 — Automated RegEx Privacy Filtering (apply_privacy_filters):

Masks Italian Codice Fiscale strings with [OMISSIS_CF].

Masks Italian IBAN numbers with [OMISSIS_IBAN].

Masks euro monetary amounts formatted with Italian decimal separators (e.g., 1.500,00 €) with [VALUE_OMISSIS].

Tier 2 — Human-in-the-Loop Trade Secret Redaction (manual_redaction):

Prompts the user in an interactive loop to enter specific words or phrases containing trade secrets, replacing matches with [OMISSIS - TRADE SECRET EX ART. 2476 c.c.] until done is typed.

Preview & Compliant Export (save_compliant_document):

Displays a 500-character preview of the redacted output and asks for confirmation (yes/no).

Saves the sanitized copy as a new file prefixed with inspection_ (e.g., inspection_verbale_assemblea.txt), leaving the source document intact.

Usage

Requirements

Python 3.x (no external dependencies required)

Running the Script

python3 legal_tool.py


Follow the on-screen prompts to paste text or specify a .txt file path, enter any trade-secret terms to redact, review the preview, and confirm export.

Disclaimer & Test Data

Educational Prototype: This tool was developed as an academic legal-tech prototype and does not constitute legal advice.

Synthetic Test Data: All corporate names, individuals, fiscal codes, IBANs, and commercial projects used to test and validate this tool are entirely fictional and AI-generated.

Author

Caterina Alessandra Imbimbo

Department of Legal Studies — Alma Mater Studiorum – Università di Bologna
