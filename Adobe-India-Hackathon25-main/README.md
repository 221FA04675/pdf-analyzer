# Adobe-India-Hackathon25
# Challenge 1A – PDF Structure Extraction

This is my solution for Challenge 1A of the Adobe Hackathon.  
The goal was to extract the structural outline (like headings and subheadings) from a given PDF file and convert it into a clean, hierarchical JSON format.

---

##  What I Did

I used **PyMuPDF** to read the PDF and analyze the font size and weight of each text block to identify headings.

- Larger fonts and bold styles are treated as higher-level headings (like H1, H2, etc.)
- The script processes each page and captures all meaningful structure
- Output is saved in a simple JSON format with the page number, heading level, and text

---

## 📁 Input Format

All input PDFs are placed in the `/input` directory.

---

## 🧾 Output Format

The output for each PDF is saved in `/output/filename.json` with this structure:

```json
{
  "title": "E0H1CM114",
  "outline": [
    {
      "level": "H1",
      "text": "Executive Summary",
      "page": 2
    },
    {
      "level": "H2",
      "text": "Goals and Objectives",
      "page": 3
    }
  ]
}


How to Run It (Docker)
 docker build --platform linux/amd64 -t heading_extractor:1a .
docker run --rm -v ${PWD}/Datasets/input:/app/input -v ${PWD}/Datasets/output:/app/output --network none heading_extractor:1a


Challenge - 1(a)/
├── Datasets/
│   ├── input/
│   └── output/
├── process_pdfs.py
├── Dockerfile
├── requirements.txt
├── README.md






---

## 🟦 `Challenge_1b/Collection 1/README.md`

```markdown
# Challenge 1B – Persona-Based Document Analysis

This is my submission for Challenge 1B of the Adobe Hackathon.  
Here, the task was to simulate a smart assistant that understands the user's intent (persona + task) and extracts the most relevant information from several PDFs.

---

## 🧠 What I Built

The system:
- Reads a `persona.json` describing who the user is and what they want to do
- Analyzes all the PDFs in the input folder
- Ranks the most relevant pages or sections using a transformer model
- Generates short summaries of those key sections
- Saves everything in a structured `output.json`

---

## 🛠 Tools I Used

- `PyMuPDF` for PDF parsing
- `sentence-transformers (MiniLM)` to match the user’s intent with PDF content
- `nltk` for basic text summarization
- Docker to make sure everything runs offline and reproducibly

---

## 📁 Input Format

Put the following in the `input/` folder:
- One `persona.json` file
- 3–10 PDF files

```json
{
  "persona": "Digital Strategy Consultant",
  "job_to_be_done": "Evaluate government and education digital transformation plans"
}


Folder structure

Collection 1b/
├── input/
│   ├── persona.json
│   └── *.pdf
├── output/
│   └── output.json
├── app/
│   ├── main.py
│   └── requirements.txt
├── Dockerfile
├── README.md

How to run
docker build --platform linux/amd64 -t persona_analyzer:1b .
docker run --rm -v ${PWD}/input:/app/input -v ${PWD}/output:/app/output --network none persona_analyzer:1b



This round was really interesting because we had to think about the user's intent and match it with dense PDF content using embeddings.
It was a good balance of NLP, PDF parsing, and logic structuring — and a fun challenge overall.