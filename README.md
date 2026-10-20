# 🎓 SnapClass

> **Smart Attendance. Made Simple.**  
> An AI-powered attendance management system that combines **face recognition, voice recognition, and cloud-based attendance tracking** in one platform.

<p align="center">
  <strong>🤖 AI Recognition</strong> &nbsp;•&nbsp;
  <strong>📊 Smart Attendance</strong> &nbsp;•&nbsp;
  <strong>☁️ Supabase</strong> &nbsp;•&nbsp;
  <strong>⚡ Streamlit</strong>
</p>

---

## 🌐 Live Demo

### 🚀 [Launch SnapClass](https://snapclass-0.streamlit.app/)

Try the deployed application directly:

**https://snapclass-0.streamlit.app/**

> The live application is deployed using Streamlit Community Cloud.

---

## 🚀 What is SnapClass?

SnapClass is an AI-powered classroom attendance platform designed to reduce the time and effort involved in traditional attendance.

Instead of relying entirely on manual roll calls, SnapClass uses **AI-based face and voice recognition pipelines** to identify registered students and connect the result with an attendance management system.

Teachers can manage subjects and attendance, while students can view their enrolled subjects and attendance history through dedicated portals.

---

## ✨ Why SnapClass?

Traditional attendance can be:

- ⏱️ Time-consuming during every class
- 📝 Difficult to maintain manually
- ❌ Prone to human errors
- 📚 Hard to analyze across multiple subjects
- 🔄 Repetitive for teachers

SnapClass aims to make the process **faster, centralized, and easier to manage**.

---

## 🎯 Core Features

| Feature | Description |
|---|---|
| 🤖 **Face Recognition** | Identifies registered students using face embeddings |
| 🎙️ **Voice Recognition** | Uses voice embeddings as an additional recognition method |
| 👨‍🏫 **Teacher Portal** | Manage subjects, students, and attendance |
| 🎓 **Student Portal** | View subjects and attendance history |
| 📊 **Attendance Records** | Timestamped present/absent records |
| ☁️ **Supabase Backend** | Centralized PostgreSQL-based data storage |
| 🔐 **Password Security** | Passwords are hashed using bcrypt |
| 📱 **Streamlit UI** | Interactive web application built with Python |

---

# 🧠 How SnapClass Works

At a high level, the system connects the **UI → ML pipelines → database**.

```text
                         ┌─────────────────────┐
                         │      SnapClass      │
                         │      Streamlit      │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┴───────────────┐
                    │                               │
             ┌──────▼──────┐                 ┌──────▼──────┐
             │   Teacher   │                 │   Student   │
             │   Portal    │                 │   Portal    │
             └──────┬──────┘                 └──────┬──────┘
                    │                               │
                    └───────────────┬───────────────┘
                                    │
                          ┌─────────▼─────────┐
                          │   ML Pipelines    │
                          │                   │
                          │ Face Recognition  │
                          │ Voice Recognition │
                          └─────────┬─────────┘
                                    │
                          ┌─────────▼─────────┐
                          │     Supabase      │
                          │    PostgreSQL     │
                          └───────────────────┘
```

---

# 🤖 Machine Learning

## 👤 Face Recognition

The face pipeline represents registered students using face embeddings and compares incoming face data against those registered representations.

```text
Camera / Image
      ↓
Face Detection
      ↓
Face Encoding / Embedding
      ↓
Compare With Registered Students
      ↓
Student Identification
      ↓
Attendance Record
```

## 🎙️ Voice Recognition

The voice pipeline processes audio and generates voice embeddings that can be compared against registered student voices.

```text
Voice Input
      ↓
Audio Processing
      ↓
Voice Embedding
      ↓
Compare With Registered Voices
      ↓
Student Identification
      ↓
Attendance Record
```

> **Design principle:** ML processing is kept in dedicated pipeline modules instead of mixing recognition logic directly into the Streamlit UI.

---

# 📊 Attendance Management

SnapClass connects recognition results with structured attendance records.

Each attendance record can contain information such as:

```text
Student
   ↓
Subject
   ↓
Timestamp
   ↓
Present / Absent
```

Teachers can view attendance records with student and subject information, while students can access their own attendance history.

---

# 🗄️ Database Architecture

SnapClass uses **Supabase / PostgreSQL** for persistent storage.

Main entities include:

```text
Teachers
   │
   └── Subjects
          │
          ├── Students
          │
          └── Attendance Logs
```

### Main Tables

| Table | Purpose |
|---|---|
| `teachers` | Teacher accounts and information |
| `students` | Student information and recognition data |
| `subjects` | Subjects created by teachers |
| `subject_students` | Student ↔ subject enrollment |
| `attendance_logs` | Attendance events and timestamps |

---

# 🖥️ Application Modules

### 👨‍🏫 Teacher

```text
Login / Register
       ↓
Teacher Dashboard
       ↓
Create Subject
       ↓
Enroll Students
       ↓
Run Attendance
       ↓
View Attendance Records
```

### 🎓 Student

```text
Login
  ↓
Student Dashboard
  ↓
View Subjects
  ↓
View Attendance
  ↓
Track Attendance History
```

---

# 🛠️ Tech Stack

### Application

- 🐍 **Python**
- ⚡ **Streamlit**

### AI / ML

- 👤 **dlib**
- 🧠 **Face Recognition Models**
- 📈 **scikit-learn**
- 🎙️ **Librosa**
- 🔊 **Resemblyzer**
- 🔥 **PyTorch**
- 🔢 **NumPy**

### Data & Backend

- ☁️ **Supabase**
- 🐘 **PostgreSQL**
- 🐼 **Pandas**

### Utilities

- 🔐 **bcrypt**
- 🖼️ **Pillow**
- 🔳 **Segno**
- 📦 **uv**

---

# 📁 Project Structure

```text
Snap_Class/
│
├── app.py                    # Main Streamlit entry point
├── main.py
│
├── src/
│   │
│   ├── components/           # Reusable UI components
│   │
│   ├── database/             # Supabase configuration & DB operations
│   │
│   ├── pipelines/            # ML / recognition pipelines
│   │
│   ├── screens/              # Student, teacher & home screens
│   │
│   └── ui/                   # Shared UI/layout styling
│
├── pyproject.toml            # Project dependencies
├── requirements.txt          # Deployment dependencies
├── uv.lock                   # Locked dependency versions
└── README.md
```

---

# ⚙️ Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/choubey-git/Snap_Class.git
cd Snap_Class
```

## 2. Install Dependencies

SnapClass uses `uv` for dependency management.

```bash
uv sync
```

## 3. Configure Supabase

Add your Supabase configuration through your local environment or Streamlit secrets.

**Never commit private keys, passwords, or secret credentials to GitHub.**

For Streamlit Cloud, configure the required secrets through the application's Secrets settings.

## 4. Run SnapClass

```bash
uv run streamlit run app.py
```

Then open:

```text
http://localhost:8501
```

---

# ☁️ Deployment

SnapClass is deployed using **Streamlit Community Cloud**.

### Live Application

🔗 **https://snapclass-0.streamlit.app/**

Deployment flow:

```text
GitHub
   ↓
Streamlit Community Cloud
   ↓
Install Dependencies
   ↓
Run app.py
   ↓
🌐 Live SnapClass Application
```

The main entry point is:

```text
app.py
```

---

# 🔐 Security

SnapClass uses `bcrypt` for password hashing.

Keep sensitive information such as:

- Supabase credentials
- API keys
- Passwords
- Environment variables
- Streamlit secrets

outside the public repository.

> **Never commit secrets directly to GitHub.**

---

# 🚧 Future Improvements

SnapClass can be extended with:

- 🎥 Real-time multi-face classroom recognition
- 🛡️ Liveness / anti-spoofing detection
- 📈 Attendance analytics and visual dashboards
- 🔔 Low-attendance notifications
- 🏫 Better large-classroom handling
- 📱 Improved mobile experience
- ⚡ More scalable ML inference
- 🗓️ Better classroom session management
- 🎯 Improved recognition accuracy

---

# 💡 Project Highlights

SnapClass demonstrates how multiple components can be combined into one practical application:

```text
Python
  +
Machine Learning
  +
Face Recognition
  +
Voice Recognition
  +
Database Design
  +
Streamlit
  =
SnapClass
```

The project separates the **ML pipelines**, **database layer**, and **presentation layer**, making the application easier to understand and extend.

---

# 👨‍💻 Project

### SnapClass — Smart Attendance. Made Simple.

Built with ❤️ using **Python, Streamlit, Supabase, Face Recognition & Voice Recognition**.

---

> ⭐ If you find this project interesting, consider giving the repository a star!
