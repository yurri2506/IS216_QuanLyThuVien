
# [IS216.P23] - LIBRARY MANAGEMENT WEBSITE PROJECT

The library management website supports efficient management of books, users, and borrowing/returning transactions, with separate interfaces for users and administrators.

> 🔗 GitHub repository: [https://github.com/yurri2506/IS216_QuanLyThuVien](https://github.com/yurri2506/IS216_QuanLyThuVien)

---

## 📋 Table of Contents

- Team Introduction
- Members
- Technologies Used
- Prerequisites
- Installation Guide
- Database Configuration
- Additional Configuration
- Project Running Notes

---

## 🎓 Team Introduction

- **University**: University of Information Technology, VNU-HCM
- **Faculty**: Information Systems
- **Supervisor**: MSc. Ta Viet Phuong
- **Student Group**: Group 8386

---

## 👥 Members

| No. | Name                    | Student ID | Role         |
|-----|-------------------------|------------|--------------|
| 1   | Nguyen Le Thanh Huyen   | 22520590   | Group Leader |
| 2   | Le Thi Phuong Thao      | 23521468   | Member       |
| 3   | Le Thi Thuy Trang       | 23521627   | Member       |
| 4   | Nguyen Thanh Tri        | 23521645   | Member       |

---

## 🛠️ Technologies Used

# LIBRARY MANAGEMENT SYSTEM - IS203

## Full Code Demo Video

👉 [Watch the full code demo video here](https://drive.google.com/file/d/1Jw40BYpVS6QfkU7XH8G8jOz8oaa1mFdb/view?usp=drive_link)

---

## Table of Contents
- [Introduction](#introduction)
- [System Architecture](#system-architecture)
- [Key Features](#key-features)
  - [Frontend User](#frontend-user)
  - [Frontend Admin](#frontend-admin)
  - [Frontend General](#frontend-general)
  - [Backend](#backend)
- [Setup & Run Project](#setup--run-project)
- [Technologies Used](#technologies-used)
- [Contribution](#contribution)

---

## Introduction

The Library Management System supports managing books, users, borrowing/returning, fines, notifications, online payments, and many other modern features. The system includes 1 backend (Spring Boot) and 3 frontends (Next.js) for admin, user, and general interface.

---

## System Architecture

- **Backend**: Spring Boot RESTful API, database connection, JWT authentication, Cloudinary integration, email sending, Momo payment.
- **Frontend**:
  - **Admin**: Administrators manage the entire library.
  - **User**: Users search, borrow/return books, manage accounts.
  - **General**: General interface, quick search, QR code scanning.

---


## Key Features

### Frontend User

- Register, login, change password, forgot password via email.
- View book list, book details, search, filter by category.
- Borrow books, return books, extend borrowing, view borrowing/return history.
- Manage book cart, add/remove books from cart.
- View and pay fines online (Momo).
- Receive notifications (overdue, fines, new books, etc.).
- Update personal information, avatar.
- Scan QR code for quick borrow/return.
- User support chatbox.
- View system and personal notifications.

### Frontend Admin

- Admin login.
- Manage books: add, edit, delete, import/export files, upload images.
- Manage categories, manage book children (book child).
- Manage users: approve accounts, lock/unlock, statistics.
- Manage borrow/return, fines, extensions, confirm returns.
- Manage notifications, send notifications to users.
- Manage system settings (borrowing rules, fines, time, etc.).
- General statistics: number of books, users, borrowings, fine revenue.
- Manage image uploads (Cloudinary).
- Manage fine payments (Momo).
- Manage admin accounts.

### Frontend General

- Homepage introducing the library.
- Quick book search, view book information.
- Scan QR code for quick search/borrow/return.
- Beautiful, friendly, responsive interface.

### Backend

- RESTful API for all above features.
- Authentication, authorization (JWT, role-based).
- Manage data: books, users, borrow/return, fines, notifications.
- Integrate Cloudinary for image uploads.
- Integrate email sending (forgot password, notifications).
- Integrate Momo payment.
- Statistics, reporting.
- Business logic: auto-calculate fines, send overdue notifications, etc.
- Support import/export data for books, users.

---

## Setup & Run Project

### Backend

```bash
cd backend2/library
# Configure .env, application.properties as needed
./mvnw spring-boot:run
```

### Frontend

```bash
# Example for frontend-user
cd frontend-user
npm install
npm run dev

# Similarly for frontend-admin, frontend-general
```

---

## Technologies Used

- **Backend**: Java, Spring Boot, Spring Security, JPA, JWT, Cloudinary, Momo API, Email SMTP.
- **Frontend**: Next.js, React, Redux, TailwindCSS, Axios, Cloudinary, Momo.
- **Database**: MySQL/PostgreSQL (configurable).

---

## Contribution

All contributions, bug reports, or suggestions are welcome via issues or pull requests.

---

If you need more details about the API or usage instructions for each feature, feel free to ask!
---

## 🔧 Additional Configuration

### 1. Cloudinary (Image Storage)

The project uses Cloudinary to store book images. Update Cloudinary info in `application.properties`:

```properties
cloudinary.cloud-name=<YOUR_CLOUDINARY_CLOUD_NAME>
cloudinary.api-key=<YOUR_CLOUDINARY_API_KEY>
cloudinary.api-secret=<YOUR_CLOUDINARY_API_SECRET>
```
- Register a [Cloudinary](https://cloudinary.com/) account and get the above values from your dashboard.
- Replace the <YOUR_...> placeholders with your Cloudinary dashboard values.
- Ensure all image upload APIs are called correctly.

### 2. Email (Notification Sending)

The project uses Gmail SMTP to send notification emails. Update info in `application.properties`:

```properties
# Gmail SMTP
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=<YOUR_GMAIL_ADDRESS>
spring.mail.password=<YOUR_GMAIL_APP_PASSWORD>
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

- <YOUR_GMAIL_ADDRESS>: Gmail address used to send emails.
- <YOUR_GMAIL_APP_PASSWORD>: App Password generated from Google Account management (enable 2-step verification first).

### 3. OAuth2 (Optional)

The project supports Google OAuth2 login. Update info in `application.properties`:

```properties
spring.security.oauth2.client.registration.google.client-id=<YOUR_GOOGLE_CLIENT_ID>
spring.security.oauth2.client.registration.google.client-secret=<YOUR_GOOGLE_CLIENT_SECRET>
spring.security.oauth2.client.registration.google.scope=email,profile
```

- Get `client-id` and `client-secret` from [Google Cloud Console](https://console.cloud.google.com/).
- Set redirect URI: `{baseUrl}/login/oauth2/code/google`.

---

## 📌 Project Running Notes

- **Run concurrently**: Make sure backend and both frontends (user, admin) are running for full functionality.
- **CORS**: If you encounter CORS errors, check and update `allowed-origins` in `application.properties`:
  ```properties
  spring.web.cors.allowed-origins=http://localhost:3000,http://localhost:3001
  spring.web.cors.allowed-methods=GET,POST,PUT,DELETE
  spring.web.cors.allowed-headers=Authorization,Content-Type
  spring.web.cors.allow-credentials=true
  ```
- **Check connections**: Ensure database and Cloudinary URLs, usernames, and passwords are correct before running.
- **Environment**: Set environment variables for `${MAIL_USERNAME}` and `${MAIL_PASSWORD}` if needed.

---




