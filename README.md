# EZtest
This is an assessment given to the candidates of EZ recruitment drive.
- Secure File Sharing System

A secure file-sharing backend system built with **FastAPI** and **SQLite**, designed to allow two different types of users — **Operation Users** and **Client Users** — to manage file uploads and secure downloads through encrypted URLs.

- 📖 Project Overview

This system provides a REST API to enable:

* Operation Users (Ops Users) to:

  * Log in to the system
  * Upload files (only `.pptx`, `.docx`, `.xlsx`)

* Client Users to:

  * Sign up (receive an encrypted URL)
  * Verify their email (via a verification link)
  * Log in
  * List all available uploaded files
  * Download files securely via a time-based encrypted URL, accessible only to Client Users

All download links are encrypted and access-controlled to prevent unauthorized downloads.



- Tech Stack

| Purpose           | Technology   |
| :---------------- | :----------- |
| Backend Framework | FastAPI      |
| Database          | SQLite       |
| Encryption        | itsdangerous |
| Testing Framework | Pytest       |
| API Testing       | Postman      |

- API Endpoints

-  Ops User

| Method | Endpoint           | Description                                  |
| :----- | :----------------- | :------------------------------------------- |
| `POST` | `/ops/login`       | Login as an Ops User                         |
| `POST` | `/ops/upload-file` | Upload file (only `.pptx`, `.docx`, `.xlsx`) |

---

-👤 Client User

| Method | Endpoint                       | Description                                        |
| :----- | :----------------------------- | :------------------------------------------------- |
| `POST` | `/client/signup`               | Register a new client user (returns encrypted URL) |
| `GET`  | `/client/verify-email/{token}` | Verify email using encrypted token                 |
| `POST` | `/client/login`                | Login as a Client User                             |
| `GET`  | `/client/files`                | List all available uploaded files                  |
| `GET`  | `/client/download-file/{id}`   | Generate secure, encrypted download link           |

---

## 🗂️ Project Structure

```
secure-file-sharing/
├── app/
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   ├── schemas.py
│   ├── routers/
│   │   ├── ops_user.py
│   │   └── client_user.py
│   ├── utils/
│   │   ├── encryption.py
│   │   └── email_service.py
│   └── uploads/
├── postman/
│   └── file_sharing_api.postman_collection.json
├── tests/
│   └── test_client_user.py
├── requirements.txt
└── README.md
```

---

-Installation & Running Instructions

-Clone the repository

```bash
git clone https://github.com/yourusername/secure-file-sharing.git
cd secure-file-sharing
```

-Install dependencies

```bash
pip install -r requirements.txt
```

-Run the application

```bash
uvicorn app.main:app --reload
```

-Test APIs using Postman

* Import the Postman collection from `/postman/file_sharing_api.postman_collection.json`
* Use the API endpoints as per the documentation above.

-Postman Collection

Postman Collection JSON file is available inside the `postman/` folder:

* `file_sharing_api.postman_collection.json`

Import this into Postman to directly test all API routes.

- Test Cases

* Written using pytest
* To run all tests:

```bash
pytest
```
-Deployment Plan

In a production environment:

* Dockerize the application with a `Dockerfile`
* Host on  Render, Railway, Fly.io, or Heroku
* Use `.env` files for sensitive environment variables like DB credentials and encryption keys
* Configure a real SMTP service for actual email verification
* Optionally, store files on a cloud storage service (like AWS S3 or Azure Blob Storage)

Mihika Jain
B.Tech CSE (AI) | NIET | 2026 Batch
