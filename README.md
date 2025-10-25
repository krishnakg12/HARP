RFP Document Information Extraction Using Google Gemini
Project Objective

This project extracts structured information from unstructured Request for Proposal (RFP) documents in PDF and HTML formats.
It leverages Natural Language Processing (NLP) and Google Gemini LLM to automate reading, interpreting, and structuring RFP content into a predefined JSON format.

Key features:

Parses RFPs in PDF & HTML formats

Extracts key fields like Bid Number, Title, Due Date, etc.

Uses Gemini to map extracted text into structured JSON

Outputs clean, machine-readable data for downstream use

Expected Structured Output

Example JSON:

{
  "Bid Number": "RFP-2025-012",
  "Title": "IT Infrastructure Upgrade",
  "Due Date": "2025-11-30",
  "Bid Submission Type": "Online",
  "Term of Bid": "3 years",
  "Pre Bid Meeting": "2025-11-10",
  "Installation": "Included",
  "Bid Bond Requirement": "Yes",
  "Delivery Date": "2025-12-20",
  "Payment Terms": "Net 30",
  "Additional Documentation Required": "Insurance Certificate",
  "MFG for Registration": "ABC Tech Ltd.",
  "Contract or Cooperative to Use": "State Procurement Alliance",
  "Model_no": "X1000",
  "Part_no": "PRT-345",
  "Product": "Server Rack System",
  "contact_info": "procurement@abctech.com",
  "company_name": "ABC Technologies",
  "Bid Summary": "Upgrade of existing server infrastructure with modern systems.",
  "Product Specification": "Rackmount server, 64-core CPU, 256GB RAM, dual PSU"
}

Installation

Install dependencies using pip:

pip install -r requirements.txt


Example requirements.txt:

google-generativeai
PyMuPDF
beautifulsoup4
pandas

Setting Up the Gemini API Key (Securely)

In Google Colab:

from google.colab import userdata
userdata.set('GOOGLE_API_KEY', 'your_api_key_here')


Configure Gemini:

import google.generativeai as genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
if not api_key:
    raise ValueError("❌ Missing API key. Please set it using userdata.set('GOOGLE_API_KEY', 'your_key').")

genai.configure(api_key=api_key)
print("✅ Gemini API configured successfully.")


This keeps your API key secure and hidden from notebook viewers.

Step-by-Step Usage
Step 1: Upload a File
file_data, file_name = upload_file()


Supported formats: .pdf, .html

Returns: file bytes and filename

Step 2: Extract Text
text = extract_text_from_file(file_data, file_name)
print(text[:500])  # Preview first 500 characters

Step 3: Use Gemini to Structure Information
import google.generativeai as genai

model = genai.GenerativeModel("gemini-1.5-pro")

prompt = f"""
Extract and structure the following RFP text into a JSON with these fields:
Bid Number, Title, Due Date, Bid Submission Type, Term of Bid,
Pre Bid Meeting, Installation, Bid Bond Requirement, Delivery Date,
Payment Terms, Any Additional Documentation Required, MFG for Registration,
Contract or Cooperative to use, Model_no, Part_no, Product,
contact_info, company_name, Bid Summary, Product Specification.

Text:
{text[:6000]}
"""

response = model.generate_content(prompt)
print(response.text)

Step 4: Save Output as JSON
import json

structured_data = response.text
with open("structured_output.json", "w") as f:
    json.dump(structured_data, f, indent=4)
print("✅ Structured data saved to structured_output.json")
