# Resume-Based Job Recommendation System

A Python desktop prototype that compares a resume with a small job dataset, extracts listed skills, recommends matching roles, and highlights skills that may be missing.

> **Project status:** Learning prototype. The repository has been organized and documented, but the application has not yet been validated in a clean environment. Similarity scores are text-matching scores, not hiring probabilities or guarantees of job suitability.

## Features

- Select a resume in PDF or DOCX format.
- Extract text from the selected resume.
- Identify skills using a predefined keyword list.
- Rank jobs using TF-IDF vectors and cosine similarity.
- Suggest a job category based on the most similar dataset entry.
- Compare resume skills with skills listed for recommended jobs.
- View results in a Tkinter desktop interface.

## How it works

1. **Resume parsing:** `resume_parser.py` extracts text from PDF or DOCX files.
2. **Skill extraction:** `skill_extractor.py` matches text against a predefined list of skills.
3. **Job matching:** `recommender.py` builds TF-IDF representations of job records and ranks them by cosine similarity to the resume text.
4. **Role suggestion:** `classifier.py` finds the most similar job record and returns its job-role label. Despite the filename, the current implementation uses similarity matching rather than a trained Logistic Regression classifier.
5. **Skill-gap display:** the app compares detected resume skills with the skill list for each recommended job.

## Repository structure

```text
job-recommendation-system/
├── app.py                 # Tkinter desktop application
├── classifier.py          # Similarity-based role suggestion
├── dataset.csv            # Small example job dataset
├── recommender.py         # TF-IDF matching and skill-gap logic
├── resume_parser.py       # PDF/DOCX text extraction
├── sample_resume.txt      # Synthetic sample resume text
├── skill_extractor.py     # Keyword-based skill extraction
├── requirements.txt       # Python dependencies
└── README.md
```

## Requirements

- Python 3.10 or newer recommended
- Tkinter support for your Python installation
- pip

Install the Python dependencies:

```bash
python -m pip install -r requirements.txt
```

On Linux, Tkinter may need to be installed separately through your distribution's package manager (for example, `python3-tk` on Debian/Ubuntu).

## Run the application

Run these commands from the repository directory:

```bash
python app.py
```

A desktop environment is required for the Tkinter GUI. If you are using Google Colab or a headless server, the desktop window will not normally open there.

## Dataset

`dataset.csv` is a small example dataset with 25 job records and four columns:

| Column | Purpose |
|---|---|
| `Job Title` | Job title |
| `Skills` | Skills associated with the role |
| `Job Description` | Short description used for text matching |
| `Job Role` | Broad category returned for the closest match |

This dataset is suitable for experimenting with the workflow, not for real-world recruitment decisions or robust evaluation.

## Limitations and next improvements

- Keyword matching can miss synonyms, context, and skills expressed in different ways.
- The small dataset may produce weak or misleading recommendations.
- Cosine-similarity values are not calibrated probabilities.
- Scanned PDFs may require OCR; this version extracts selectable PDF text.
- Resume text is processed locally by this application, but users should only test with resumes they have permission to use.
- Add automated tests, a larger and properly sourced dataset, evaluation metrics, and clearer validation/error handling before treating this as a dependable application.

## Technologies

Python · pandas · scikit-learn · TF-IDF · cosine similarity · PyPDF2 · python-docx · Tkinter

## Run a quick manual check

Use `sample_resume.txt` as example text while developing. The current GUI accepts PDF and DOCX files, so the text sample is intended for reference rather than direct upload.

## Author

Created as a learning project to practise Python, text processing, basic machine learning concepts, and desktop GUI development.
