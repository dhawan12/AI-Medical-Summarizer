# AI-Medical-Summarizer



# 🧠 AI-Powered Medical Report Generator Workflow (n8n + Gemini + OCR)

This project is an **end-to-end AI-based Medical Report Generator** built using [n8n](https://n8n.io/), [Google Gemini](https://ai.google), and integrated email automation. It enables clinical teams to upload patient documents and receive a professionally formatted, medically accurate summary via email.

---

## 🚀 Overview

The workflow enables automation of the following:

1. ✅ Accepting a **PDF upload** of patient data through a web form.
2. 📄 Extracting text from the uploaded medical file using **n8n’s Extract From File** node.
3. 🧠 Passing the raw text into a **Large Language Model (LLM)** (Google Gemini via LangChain) with a strict **clinical prompt**.
4. 📝 Generating a clean, structured medical summary in markdown format.
5. 🧾 Converting the markdown into HTML.
6. 📧 Emailing the final medical summary report to a predefined recipient.

---



---

## 🧩 Workflow Components

| Node Name             | Description |
|----------------------|-------------|
| **Form Trigger**      | A user-facing form titled `AI Report Generator Form` that accepts a PDF file. |
| **Extract from File** | Extracts text from the uploaded PDF document. |
| **Edit Fields**       | Maps the raw text to a new field `maindata` for further processing. |
| **Google Gemini Chat Model** | Connects to Google's Gemini LLM via LangChain to enable medical text understanding. |
| **AI Agent**          | Processes the extracted data using a highly structured clinical prompt. |
| **Markdown to HTML**  | Converts AI output from Markdown to HTML for email formatting. |
| **Gmail Node**        | Sends the structured summary via email to a healthcare recipient. |

---

## 📄 Medical Report Format

The AI Agent generates reports in the following format:

- **Patient Information**  
  Full Name, DOB, Gender, Address, Contact  
- **Medical History & Comorbidities**  
  Chronic Conditions, Hospitalizations, Limitations  
- **Current Diagnoses**  
  Primary & Other Diagnoses  
- **Vital Signs & Observations**  
  BP, HR, RR, Temp, Mental Status  
- **Mobility & Daily Living**  
  Ambulation, ADL Support  
- **Summary of Findings and Diagnosis**  
  Clinical insights, risks, recommendations  

---

## 🔐 Compliance & Security

- ❌ No hallucinated data – if something is missing in the document, the AI says: `"Not documented"` or `"Unknown"`.
- 🔐 Does **NOT** include sensitive identifiers like SSNs, Medicare IDs, or contact numbers.
- ✅ Output is written with clinical accuracy, tone, and usability for care coordination or physician review.

---

## ⚙️ Prerequisites

- [n8n](https://n8n.io/) instance (local or hosted)
- Google Gemini API Key (via Google PaLM credentials)
- Gmail OAuth2 Credentials (to send email)
- n8n nodes:
  - `n8n-nodes-base.extractFromFile`
  - `@n8n/n8n-nodes-langchain.agent`
  - `@n8n/n8n-nodes-langchain.lmChatGoogleGemini`
  - `n8n-nodes-base.markdown`
  - `n8n-nodes-base.gmail`

---

## 📥 How to Use

1. Clone this repo:
   ```bash
   git clone https://github.com/yourusername/n8n-medical-report-generator.git
````

2. Import `medical_report_workflow.json` into your n8n instance.

3. Set up credentials for:

   * **Google Gemini API** (PaLM/Gemini Key)
   * **Gmail OAuth2** (for sending mail)

4. Deploy and access the generated public webhook form URL.

5. Upload a patient report (PDF) using the form.

6. Check the configured email inbox for the AI-generated medical report.

---

## 📌 Limitations & Notes

* The workflow assumes the uploaded file is semi-structured or unstructured medical text.
* Accuracy depends on text clarity (avoid scanned PDFs with handwriting).
* Token limits apply — longer documents may be truncated.

---

## 👨‍⚕️ Made For

* Healthcare Providers & Clinics
* Telemedicine Startups
* Clinical Data Analysts
* AI + Healthcare Hackathons

---

## 📫 Contact

Made with ❤️ by [Dhawan Kumar Nama](mailto:namadhawan@gmail.com)
Automation Engineer | RPA + AI Enthusiast

---

## 📃 License

This project is licensed under the MIT License - feel free to use and customize for your clinic or business.

```
