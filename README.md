Smart Resume Analyzer API

📖 Overview
The Smart Resume Analyzer API is an AI-powered backend service designed to streamline the hiring process by analyzing resumes against job descriptions. It parses PDF resumes, extracts skills using NLP, and evaluates compatibility through skills matching, keyword density, and semantic similarity. The API returns a detailed report with scores and actionable suggestions to improve the resume, making it valuable for HR professionals and job seekers.
Built with modern Python tools and containerized with Docker, this project is scalable, easy to deploy, and ready for integration into larger HR tech solutions.
✨ Features

Resume Parsing: Extracts text from PDF resumes using PyMuPDF.
Skills Extraction: Identifies skills with spaCy and a predefined skills database.
Job Description Matching: Computes skills match and semantic similarity using SentenceTransformers.
Keyword Density Analysis: Measures the presence of job-relevant keywords.
Actionable Suggestions: Provides feedback (e.g., "Add experience in Python").
RESTful API: Built with FastAPI for high performance and easy integration.
Docker Support: Containerized for deployment on platforms like Render or Railway.

🛠 Tech Stack

Component
Technology

Backend
FastAPI (0.115.0)

NLP
spaCy (en_core_web_sm)

Text Embeddings
SentenceTransformers (all-MiniLM-L6-v2)

PDF Parsing
PyMuPDF (1.24.10)

Tokenizer
NLTK (3.9.1)

Form Handling
python-multipart (0.0.12)

Containerization
Docker

Runtime
Python 3.10

🚀 Getting Started
Prerequisites

Python 3.10+: Download Python
Docker: Install Docker (optional for containerized deployment)
Git: Install Git
pip: For installing Python dependencies

Installation

Clone the Repository:
git clone https://github.com/your-username/smart-resume-analyzer.git
cd smart-resume-analyzer

Set Up a Virtual Environment:
python -m venv env
source env/bin/activate # On Windows: env\Scripts\activate

Install Dependencies:
pip install -r requirements.txt
python -m spacy download en_core_web_sm

Run the API Locally:
uvicorn main:app --reload

The API will be available at http://localhost:8000. Access the interactive Swagger UI at http://localhost:8000/docs.

Docker Setup

Build the Docker Image:
docker build -t resume-analyzer .

Run the Container:
docker run -p 8000:8000 resume-analyzer

📡 Usage
Analyze a Resume
Send a POST request to /analyze-resume/ with a PDF resume and job description:
curl -X POST "http://localhost:8000/analyze-resume/" \
 -F "resume=@/path/to/resume.pdf" \
 -F "job_description=Looking for a Python developer with experience in FastAPI and machine learning."

Example Response:
{
"skills_match_score": 66.67,
"keyword_density_score": 5.23,
"similarity_score": 85.12,
"final_score": 71.45,
"extracted_skills": ["python", "fastapi"],
"suggestions": ["Consider adding experience or certification in 'machine learning' to strengthen your resume."]
}

API Endpoints

Endpoint
Method
Description

/
GET
Health check for the API

/analyze-resume/
POST
Analyze a resume against a job description
