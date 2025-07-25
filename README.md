# BoM_Table_Extraction
#  PDF BoM Table Extraction & Excel Export

This project solves the problem of extracting Bill of Materials (BoM) tables from scanned or digital engineering drawing PDFs. It supports:

-  Automated table extraction via OCR
-  Manual BoM creation for Excel export
-  Clean tabular formatting with spacing and labels
-  No use of LLMs, APIs, or cloud services

---

##  Table of Contents

- [ Features](#-features)
- [ Technologies Used](#-technologies-used)
- [ Installation](#-installation)
- [ How to Use](#-how-to-use)
- [ Sample Input & Output](#-sample-input--output)
- [ Project Structure](#-project-structure)
- [ Constraints & Design Decisions](#-constraints--design-decisions)
- [ Future Improvements](#-future-improvements)
- [ Author](#-author)
- [ License](#-license)

---

##  Features

###  OCR-Based BoM Table Extraction
- Converts PDF pages to images
- Extracts BoM tables using keyword detection: `"Part Number"`, `"Description"`, `"Qty"`
- Cleans, structures, and formats tables using `pandas`
- Displays organized tables in console using `tabulate`

###  Manual Table Entry & Excel Export
- Accepts manual entry of two tables
- Saves both tables to a single Excel sheet using `xlsxwriter`
- Adds a 2-row gap for readability
- Great for noisy scans or handwritten tables

---

##  Technologies Used

- **Python 3.x**
- **pdf2image** – convert PDFs to image pages
- **pytesseract** – OCR text from image
- **pandas** – structure and manipulate tabular data
- **tabulate** – print clean CLI tables
- **xlsxwriter** – export Excel files
- **poppler-utils** – required for PDF rasterization

---

##  Installation,How to use,Project Structure and Constraints.

Run the following in Google Colab or your local terminal:

```bash
pip install pdf2image pytesseract pandas tabulate xlsxwriter
sudo apt-get install poppler-utils tesseract-ocr

---

**##  How to Use (with Sample Input & Output)

###  A. Extract BoM from PDF using OCR

1. Upload a PDF file containing a scanned or digital BoM table (e.g., `drawing+bom.pdf`)
2. The script will:
   - Convert each page to an image
   - Apply OCR to extract all text
   - Search for lines containing keywords like `"Part Number"`, `"Description"`, `"Qty"`
   - Parse and align the extracted data into structured rows

>  Tip: Best results come from clean, high-contrast PDF scans with horizontal BoM tables.

---

###  B. Manually Enter BoM Tables and Export to Excel

1. Use the script to define two BoM tables manually using `pandas.DataFrame`
2. Each table supports:
   - Columns like `ITEM`, `PART NUMBER`, `DESCRIPTION`, `MATERIAL`, `SOURCE`, `QTY`
3. The script:
   - Prints both tables using `tabulate`
   - Saves them to `Combined_BoM.xlsx` with a 2-row gap between them
**PROJECT STRUCTURE**
├── bom_ocr_extractor.ipynb        # Extract BoM tables from PDF via OCR
├── manual_bom_writer.ipynb        # Define manual tables and export to Excel
├── Combined_BoM.xlsx              # Final combined table output (auto-generated)
└── README.md                      # This file
 How to Use (with Sample Input & Output)
 A. Extract BoM from PDF using OCR
Upload a scanned or digital engineering drawing PDF (e.g. drawing+bom.pdf)

The script will:
              1- Convert pages to images
              2- Use OCR to extract text
              3- Identify BoM headers by keywords: "Part Number", "Description", "Qty"
              4- Parse rows into structured columns
##Sample Output
+------------------+-----------+------------------------------------------+----------+
| Part Number      | Part Name | Description                              | Quantity |
+------------------+-----------+------------------------------------------+----------+
| UCP21-AST        | PILLOW    | BLOCK BEARING AST - METRIC SERIES        | 1        |
| 3GAA103001-BSE   | ELECTRIC  | MOTOR 1.5KW ABB M2AA100L 6               | 1        |
| 7493250          | BEARING   | MOUNTING PAD MACHINED                    | 1        |

 Tip: Best results come from high-contrast, clean, horizontal BoM layouts.

B. Manually Enter BoM Tables and Export to Excel
Two sample tables are created using pandas.DataFrame

Columns supported:

Table 1: ITEM, PART NUMBER, DESCRIPTION, MATERIAL, QTY
Table 2: ITEM, PART NUMBER, DESCRIPTION, MATERIAL, SOURCE, QTY

The script:
            1-Prints both tables using tabulate
            2-Writes both into Combined_BoM.xlsx with a 2-row gap
Excel file structure:
Table 1 → e.g. Cast Iron Base, Bracket, Bush...
[2 empty rows]
Table 2 → Purchased parts like Bearings, Motors, Screws...

 Project Structure
├── bom_ocr_extractor.ipynb        # Extract BoM tables from PDF via OCR
├── manual_bom_writer.ipynb        # Define manual tables and export to Excel
├── Combined_BoM.xlsx              # Final combined table output (auto-generated)
└── README.md                      # This file

** Constraints & Design Decisions**
 No use of LLMs (Large Language Models)
 No cloud-based APIs or OCR services
 Rule-based parsing using text position and spacing
 All logic is explainable and reproducible
 Does not detect visual grid lines (yet)

** Future Improvements**
OpenCV-based visual table detection using grid lines
 AI/ML model (TableNet or CascadeTabNet) for complex layouts
 Support for multiline cells and wrapped text
 Auto-export to CSV, JSON, or REST API
 Web UI for drag-and-drop PDF uploads

**Author**
Shreeya Santhoshi Srinath
Contributor – Pre-Intern Hiring Project
GitHub: shreeya0106






