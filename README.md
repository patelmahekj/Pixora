# 📄 Pixora

## Instant, Field-Driven Document Generation

> **Fill in your details. Preview live. Print or export instantly.**

Pixora is a Flask-based web application that generates ten different
types of printable documents from user-entered data, with a live
preview and one-click print/export. It includes secure OTP-based
account verification and a separate admin dashboard for user
management.

Pixora was built as a **group project**.

---

## 📌 Table of Contents

- [Key Features](#-key-features)
- [Document Types](#-document-types)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Running the Application](#-running-the-application)
- [Security Notes](#-security-notes)
- [My Contribution](#-my-contribution)
- [Current Limitations](#-current-limitations)
- [License](#-license)

---

## ✨ Key Features

### 🔐 Authentication & Account Security
- Email-based OTP verification during signup
- Password-strength validation at registration
- Account lockout after repeated failed login attempts
- Session-based login for verified users

### 📝 Document Generation
- Ten printable document types, each with a live, field-driven preview
- One-click print-to-PDF export via the browser print dialog
- Dynamic form fields tailored to each document type

### 🛠️ Admin Dashboard
- View all registered users and their verification status
- Block or unblock user accounts
- Delete user accounts
- Backed by a dedicated SQLite data layer for user and OTP records

---

## 📁 Document Types

| # | Document |
|---|---|
| 1 | Resume |
| 2 | Certificate |
| 3 | Cover Letter |
| 4 | Invoice |
| 5 | Business Card |
| 6 | ID Card |
| 7 | Newsletter |
| 8 | Receipt |
| 9 | Invitation |
| 10 | Thank-You Letter |

---

## 🛠️ Technology Stack

### Backend
- Python
- Flask
- SQLite

### Authentication & Email
- SMTP-based email delivery for OTP verification

### Frontend
- HTML / CSS / JavaScript (server-rendered templates)

### Development Tools
- Git and GitHub

---

## 📁 Project Structure

```text
project/
│
├── app.py                # Main Flask application (routes, auth, admin logic)
├── users.db               # SQLite database (user accounts, OTP records)
├── static/                 # CSS, JS, and static assets
├── templates/               # HTML templates
│   ├── home.html
│   ├── login.html
│   ├── register.html
│   ├── otp.html
│   ├── admindashboard.html
│   └── ...                 # Document-type templates
└── requirements.txt
```

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd pixora
```

### 2. Create a Python Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

Activate it on Linux or macOS:

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🔧 Configuration

Pixora requires SMTP credentials to send OTP verification emails, and
an admin username/password for the admin dashboard.

Create a `.env` file in the project root (never commit this file):

```env
SMTP_EMAIL=your-email@example.com
SMTP_PASSWORD=your-app-password
ADMIN_USERNAME=your-admin-username
ADMIN_PASSWORD=your-admin-password
```

> **Important:** Credentials must never be hardcoded in source files or
> committed to version control. Use an app-specific password for the
> email account rather than a personal account password, and add `.env`
> to `.gitignore`.

---

## ▶️ Running the Application

```bash
python app.py
```

The application will be available at:

```text
http://127.0.0.1:5000
```

---

## 🔐 Security Notes

- OTP codes are time-limited and tracked per account to prevent misuse.
- Accounts are locked after repeated failed login attempts to reduce
  brute-force risk.
- Passwords should be stored using a proper hashing function (e.g.
  `werkzeug.security.generate_password_hash`) rather than in plain
  text.
- All SMTP and admin credentials must be supplied via environment
  variables, never committed to the repository.

---

## ⚠️ Current Limitations

- Password storage and credential management should follow the
  security practices noted above before any production or public
  deployment.
- Document templates are currently fixed; further customization
  options could be added in future iterations.

---

## 📄 License

Add the appropriate project license before public distribution.
