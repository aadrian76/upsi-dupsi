🕵️‍♂️ VAmPI — Final Project ( SCA + SAST + DAST + Presentation)
================================================================================

![68747470733a2f2f692e696d6775722e636f6d2f7a523071754b662e6a7067.jpg](/.attachments/68747470733a2f2f692e696d6775722e636f6d2f7a523071754b662e6a7067-8c19b8ee-d96f-4fb2-b2a0-25080cdc5429.jpg)

This guide explains how to set up **VAmPI** for the final project inside **WSL**, run it with **Docker**, and perform the required analyses: **SCA (Software Composition Analysis)**, **SAST (Static Application Security Testing)** and **DAST (Dynamic Application Security Testing)**. It also includes what to include in your presentation/finding defence.

> **Assumption:** VAmPI is a purposely-vulnerable application/API used for security training



What is VAmPI (API) — Endpoints & Actions
=========================================

VAmPI is a purposely vulnerable **RESTful API** used for security training. It exposes endpoints for user management, book data and admin operations. The API accepts and returns JSON and implements basic authentication flows (login/register). Below is a concise reference of the available actions you will test during the SCA / SAST / DAST exercise.

| Action | Path | Details |
| --- | --- | --- |
| GET | `/createdb` | Creates and populates the database with dummy data (use once to bootstrap test data). |
| GET | `/` | VAmPI home (basic landing/info). |
| GET | `/me` | Displays the user that is logged in (requires authentication / session). |
| GET | `/users/v1` | Displays all users with basic information (likely public or semi-public). |
| GET | `/users/v1/_debug` | Displays full details for all users — highly sensitive debug endpoint (exposes PII / secrets). |
| POST | `/users/v1/register` | Register a new user (accepts JSON body with username/email/password). |
| POST | `/users/v1/login` | Login to VAmPI (accepts credentials, returns session token/cookie). |
| GET | `/users/v1/{username}` | Displays user by `username` (path parameter). |
| DELETE | `/users/v1/{username}` | Deletes a user by `username` — **Admin only** (authorization required). |
| PUT | `/users/v1/{username}/email` | Update a single user’s email (expects JSON with new email). |
| PUT | `/users/v1/{username}/password` | Update user password (expects old/new password fields). |
| GET | `/books/v1` | Retrieves all books (list endpoint). |
| POST | `/books/v1` | Add new book (expects JSON with title, author, maybe content/secret). |
| GET | `/books/v1/{book}` | Retrieves a book by title — **returns book details along with a secret** (sensitive data exposure). |


🛠 Installation Guide 
=========================================================


1️⃣ Open WSL
------------

From **Windows Terminal** or **PowerShell**:


<code>wsl</code>

2️⃣ Update the system
-----------------

<code> sudo apt update && sudo apt upgrade -y</code>

3️⃣ Install Docker
-------------------
<code>sudo apt install docker.io</code>

## 4️⃣ Download and run VAmPI 
-

<code>docker run -p 5000:5000 erev0s/vampi:latest</code>

Access from Windows: <code>http://127.0.0.1:5000/</code>

Available Swagger UI 🚀
-----------------------

Visit the path `/ui` where you are running the API and a Swagger UI will be available to help you get started!

    http://127.0.0.1:5000/ui/


## Code & Report Template 

Below are the links to the VAmPI source code and to the findings template you should use to fill the final report.  
Replace the placeholder links with the actual URLs or paths before submitting.

- **VAmPI source code**  
  [VAmPI-master.zip](/.attachments/VAmPI-master-c1b38a90-1334-46b8-a646-5e0d0a49ed9f.zip)

- **Report template** — use this to document each finding (title, severity, evidence, remediation):  
  [Plantilla Report.docx](/.attachments/Plantilla%20Report-7ff11049-aa8e-4023-9c2d-a78e99e7d38b.docx)

