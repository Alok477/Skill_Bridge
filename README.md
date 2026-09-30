# SkillBridge

**SkillBridge** is an academia–industry collaboration platform designed to connect **skills, assessments, opportunities, and employability** in one place.

The platform helps users identify their current skill levels, understand skill gaps, discover relevant internships and placement opportunities, and improve their alignment with industry requirements.


---

## 🚀 Overview

SkillBridge provides a unified platform for:

*  Skill mapping
*  Skill assessments
*  Skill-gap analysis
*  Internship discovery
*  Placement opportunities
*  Candidate–opportunity matching
*  Candidate profiles and portfolios
*  Employability insights

The project was originally developed around **Smart India Hackathon Problem Statement SIH26044 — Portal for Academia–Industry Collaboration for Skill Mapping, Internships and Placements**.

While inspired by the problem statement, SkillBridge is structured as a standalone software platform rather than being presented solely as a hackathon submission.

---

## ✨ Features

### 👤 User Profiles

Create and maintain a structured profile containing:

* Personal information
* Education
* Skills
* Skill proficiency
* Projects
* Certifications
* Career interests

### 🧩 Skill Mapping

Organize a user's technical and professional skills into a structured skill profile.

This provides a foundation for assessments, skill-gap analysis and opportunity matching.

### 📝 Skill Assessment

Users can evaluate their knowledge through skill-based assessments.

The assessment system supports:

* Multiple-choice questions
* Skill-specific evaluations
* Score calculation
* Performance tracking
* Assessment results

### 📊 Skill-Gap Analysis

Compare a user's existing skills against the requirements associated with career opportunities.

This can help identify:

* Existing strengths
* Missing skills
* Skills requiring improvement
* Areas for further learning

### 💼 Opportunities

Browse internship and placement opportunities based on available data.

Opportunities can contain information such as:

* Job/internship title
* Organization
* Required skills
* Eligibility
* Location
* Description

### 🔎 Candidate Matching

SkillBridge is designed around matching candidates with opportunities using their skill profiles and requirements.

The architecture can be extended with more advanced recommendation and AI-based matching systems.

### 📁 Portfolio

Users can maintain a centralized representation of their academic and professional profile, including projects, certifications and skills.

---

# 🛠️ Technology Stack

### Frontend

* React 18
* Vite
* Tailwind CSS
* Framer Motion

### Backend

* FastAPI
* SQLAlchemy
* JWT Authentication
* bcrypt

### Database

* MySQL 8+

### Deployment

* Vercel — Frontend
* Railway — Backend & MySQL

---

# 🏗️ Architecture

```text
                ┌─────────────────────┐
                │       Browser       │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │   Vercel Frontend   │
                │   React + Vite      │
                └──────────┬──────────┘
                           │
                           │ HTTPS API
                           ▼
                ┌─────────────────────┐
                │  Railway Backend    │
                │ FastAPI + SQLAlchemy│
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │    Railway MySQL    │
                │      Database       │
                └─────────────────────┘
```

---

# 📂 Project Structure

```text
SkillBridge/
│
├── src/                     # React frontend
│
├── backend/                 # FastAPI backend
│   ├── main.py
│   ├── schema.sql
│   └── requirements.txt
│
├── public/                  # Static frontend assets
│
├── vercel.json              # Vercel SPA configuration
├── railway.json             # Railway configuration
├── package.json
└── README.md
```

---

# ⚙️ Local Development

## Prerequisites

Make sure you have:

* Node.js
* npm
* Python 3.12+
* MySQL 8+

---

## 1. Clone the repository

```bash
git clone https://github.com/Alok477/SkillBridge-SIH_Project.git
cd SkillBridge-SIH_Project
```

---

## 2. Frontend Setup

Install dependencies:

```bash
npm install
```

Create `.env.local` from `.env.example`:

```bash
copy .env.example .env.local
```

Configure:

```env
VITE_API_BASE_URL=http://localhost:8000
```

Start the development server:

```bash
npm run dev
```

The frontend will be available through the Vite development server.

---

## 3. Backend Setup

Create a MySQL database:

```sql
CREATE DATABASE academia_portal;
```

Create a Python virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r backend/requirements.txt
```

Create:

```text
backend/.env
```

using `backend/.env.example` as the template.

Configure your local database credentials and JWT secret.

Start FastAPI:

```bash
uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
```

---

# 🔌 API

Once the backend is running:

**Health check**

```text
http://localhost:8000/health
```

**Interactive API documentation**

```text
http://localhost:8000/docs
```

The backend uses FastAPI's OpenAPI documentation for exploring and testing API endpoints.

---

# ☁️ Production Deployment

## Backend — Railway

Deploy the `backend/` directory as a Railway service.

Use:

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

Configure environment variables:

```env
ENVIRONMENT=production
JWT_SECRET=<strong-random-secret>
JWT_EXPIRE_MINUTES=1440
CORS_ORIGINS=https://<your-vercel-domain>
```

Railway's MySQL service provides the database connection variables used by the backend.

---

## Frontend — Vercel

Import the repository into Vercel.

Use the repository root as the project root.

Build command:

```bash
npm run build
```

Set:

```env
VITE_API_BASE_URL=https://<your-railway-backend-domain>
```

Redeploy after changing environment variables.

---

# 🔐 Security

Sensitive configuration should never be committed to Git.

Do **not** commit:

```text
backend/.env
.env.local
database passwords
JWT secrets
node_modules/
.venv/
dist/
```

These files and directories are excluded through `.gitignore`.

For production deployments, use strong randomly generated secrets and environment variables rather than hard-coded credentials.

---

# 🧪 Verification

Before deployment, run:

```bash
npm install
npm run build
python -m compileall -q backend
```

Then verify:

```text
http://localhost:8000/health
http://localhost:8000/docs
```

---

# 🔮 Future Development

Potential extensions for SkillBridge include:

*  AI-powered career recommendations
*  LLM-based skill-gap analysis
*  Personalized learning recommendations
*  LinkedIn/GitHub profile integration
*  Advanced candidate analytics
*  Employer dashboards
*  Semantic opportunity search
*  AI-powered candidate–job matching
*  Industry skill-demand analytics

---

# 👨‍💻 Author

**Alok Kumar**

Developer and creator of **SkillBridge**.

The project was developed as a standalone implementation inspired by:

**SIH26044 — Portal for Academia–Industry Collaboration for Skill Mapping, Internships and Placements**

---

# 📄 License

This project is licensed under the **MIT License**.

See the [`LICENSE`](LICENSE) file for details.

---

## ⭐ SkillBridge

**Map your skills. Identify your gaps. Discover your opportunities.**
