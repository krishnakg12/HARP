# RFP Information Extraction

A Python notebook that extracts structured information from RFP (Request for Proposal) documents using Google's Gemini API. Supports both PDF and HTML file formats.

## Description

This project automates the extraction of key information from RFP documents, including bid numbers, due dates, payment terms, product specifications, and other relevant details. The extracted data is output in JSON format for easy integration into other systems.

## Prerequisites

- Python 3.7 or higher
- Google Colab account (recommended) or local Python environment
- Google Gemini API key ([Get one here](https://aistudio.google.com/app/apikey))

## Installation

### For Google Colab (Recommended)

1. Open the notebook in Google Colab
2. Run the first cell to install dependencies:


## Setup

### API Key Configuration

**In Google Colab:**
1. Click the key icon (🔑) in the left sidebar
2. Add a new secret named `GOOGLE_API_KEY`
3. Paste your Gemini API key as the value
4. Toggle the notebook access switch to enable

**For Local Environment:**
Set your API key as an environment variable:


## Usage

1. **Run Setup Cells**: Execute the first three cells to install libraries and configure the API
2. **Define Functions**: Run cells that define `upload_file()`, `extract_text_from_file()`, and `process_with_gemini()`
3. **Upload Document**: Run the final cell and upload your RFP document (PDF or HTML)
4. **View Results**: The extracted information will be displayed in JSON format and saved to `extracted_info.json`

## Supported File Formats

- PDF (.pdf)
- HTML (.html)

## Output Structure

The tool extracts the following fields:
- Bid Number
- Title
- Due Date
- Bid Submission Type
- Term of Bid
- Pre Bid Meeting
- Installation
- Bid Bond Requirement
- Delivery Date
- Payment Terms
- Any Additional Documentation Required
- MFG for Registration
- Contract or Cooperative to use
- Model_no
- Part_no
- Product
- Contact Info
- Company Name
- Bid Summary
- Product Specification

## Output Files

- `extracted_info.json` - Contains the structured information extracted from the uploaded document

## Troubleshooting

**Issue:** API key not found
- Ensure you've correctly set up the API key in Colab secrets or environment variables

**Issue:** Unsupported file type
- Only PDF and HTML files are supported. Ensure your file has the correct extension

**Issue:** Extraction failed
- Check that your document contains the relevant RFP information
- Verify your internet connection for API calls

## Dependencies

- `google-generativeai` - For Gemini API integration
- `PyMuPDF` - For PDF text extraction
- `beautifulsoup4` - For HTML parsing

## License

This project is for educational and assignment purposes.
