# 📄 Resume-Checker (CareerPulse)

> **InnoHack Project** — An AI-powered full-stack career platform designed to help job seekers optimize their resumes, pass ATS filters, stay informed with real-time tech news, and generate polished professional resumes.

---

## ✨ Features

- **🔍 AI Resume Analysis & ATS Checker**: Upload your resume (PDF/DOCX) to get instant scoring, detailed ATS breakdown, keyword matching, format evaluation, and personalized suggestions.
- **🛠️ Interactive Resume Builder**: Create professional, formatted resumes with custom sections, preview templates, and export directly.
- **📰 Tech & Job Market News**: Live feed of developer jobs, tech hiring trends, internship opportunities, and upskilling news powered by News API.
- **🤖 AI Career Assistant**: Built-in chatbot powered by Google Gemini to answer resume queries, interview preparation tips, and career questions.
- **📝 Personal Notes**: Save key insights, interview prep notes, and application reminders.
- **🔐 Secure Authentication**: JWT-based authentication for user registration, login, and protected profiles.

---

## 🛠️ Tech Stack

### Backend
- **Framework**: Django 5.x & Django REST Framework (DRF)
- **Authentication**: JWT (`djangorestframework-simplejwt`)
- **AI & NLP**: Google Gemini AI (`google-generativeai`), Scikit-learn, NLTK, Textstat
- **Document Processing**: `python-docx`, `PyMuPDF` (fitz), `pdf2docx`, `fpdf2`, `Pillow`
- **Database**: SQLite (default, zero-setup) / PostgreSQL (supported via configuration)
- **CORS**: `django-cors-headers`

### Frontend
- **Framework**: React 19 + Vite
- **Routing**: React Router v7
- **Styling**: Modern responsive CSS & animations (`framer-motion`, `vanilla-tilt`)
- **Visuals & Icons**: Lucide React, React Icons, Chart.js (`react-chartjs-2`)
- **Markdown & Code**: `react-markdown`, `react-syntax-highlighter`
- **HTTP Client**: Axios with JWT interceptors

---

## 📁 Project Structure

```text
Resume-Checker/
├── backend/
│   ├── api/                      # Django App (Views, Models, Serializers)
│   │   ├── analysis_core.py      # Core NLP & ML resume scoring logic
│   │   ├── resume_generator.py   # PDF & DOCX export generator
│   │   ├── resume_service.py     # Gemini AI assistant integration
│   │   ├── news_service.py       # News API integration
│   │   ├── models.py             # Database schemas
│   │   └── urls.py               # REST API endpoints
│   ├── backend/                  # Django project configuration
│   │   ├── settings.py           # Configured for environment variables & SQLite/Postgres
│   │   └── urls.py               # Root URL configuration
│   ├── .env.example              # Template for environment variables
│   ├── requirements.txt          # Python dependencies
│   └── manage.py
├── frontend/
│   ├── src/
│   │   ├── components/           # Navbar, Form, Protected Routes, Profile Overlay
│   │   ├── features/             # ResumeAnalyzer, ResumeBuilder, Chatbot, News, Notes
│   │   ├── pages/                # Home, Login, Register, NotFound
│   │   ├── styles/               # Component-specific stylesheets
│   │   ├── api.js                # Axios configuration
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
├── .gitignore                    # Protects secrets, DB, and uploaded files
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- **Python 3.10+** (Tested on Python 3.11 & 3.13)
- **Node.js 18+** and **npm**

---

### 1. Backend Setup

1. **Navigate to the backend directory**:
   ```bash
   cd backend
   ```

2. **Create and activate a virtual environment** (optional but recommended):
   ```bash
   python -m venv .venv
   # Windows PowerShell:
   .\.venv\Scripts\Activate.ps1
   # macOS / Linux:
   source .venv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**:
   Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   # On Windows:
   copy .env.example .env
   ```
   Open `.env` and fill in your API keys:
   ```env
   SECRET_KEY=your-django-secret-key
   DEBUG=True
   ALLOWED_HOSTS=*

   # AI & News Keys
   GEMINI_API_KEY=your_gemini_api_key_here
   NEWS_API_KEY=your_news_api_key_here

   # Database (defaults to SQLite if USE_POSTGRES=False)
   USE_POSTGRES=False
   ```

5. **Run migrations**:
   ```bash
   python manage.py migrate
   ```

6. **Start the Django development server**:
   ```bash
   python manage.py runserver
   ```
   The backend will start at `http://127.0.0.1:8000/`.

---

### 2. Frontend Setup

1. **Navigate to the frontend directory** (in a new terminal):
   ```bash
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start the Vite development server**:
   ```bash
   npm run dev
   ```
   The frontend will be available at `http://localhost:5173/`.

---

## 🔑 Environment Variables Reference

| Variable | Description | Default |
|---|---|---|
| `SECRET_KEY` | Django application secret key | Fallback provided for dev |
| `DEBUG` | Enable/disable debug mode | `True` |
| `ALLOWED_HOSTS` | Comma-separated allowed hosts | `*` |
| `GEMINI_API_KEY` | Google Gemini API key for AI assistant | *Required for Chatbot* |
| `NEWS_API_KEY` | NewsAPI.org key for tech & job news | *Required for Live News* |
| `USE_POSTGRES` | Toggle between SQLite (`False`) and PostgreSQL (`True`) | `False` |

---

## 🔒 Security Best Practices

- **Never commit `.env` files** to GitHub. The included `.gitignore` protects secrets, local databases, and temporary uploaded files.
- Sample configs are safely provided in `.env.example`.
- Uploaded resumes in `backend/resumes/` are ignored to prevent committing personal user data.

---

## 📄 License
This project was developed for **InnoHack**. All rights reserved.
