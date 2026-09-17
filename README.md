# Student-Management-System
Title and project overview Problem statement Objectives Technology stack System architecture Database/ER diagram UI screenshots API endpoint documentation CRUD implementation details Testing results Installation and execution steps Challenges and solutions Future enhancements Git repository/reference details
# Student Management System

A complete, lightweight, full-stack **Student Management System** developed as a college mini-project using **Python Flask**, **SQLite**, **HTML5**, **CSS3**, and **Vanilla JavaScript**.

---

## 📌 Project Overview
The Student Management System demonstrates fundamental **CRUD** (Create, Read, Update, Delete) operations over HTTP REST APIs. It provides a clean, responsive web interface allowing college administrators or faculty to manage student profiles, perform real-time search filtering, and view metrics.

---

## ✨ Features
- ➕ **Create Student**: Add new student details with client-side & server-side validation.
- 📋 **Read Students**: Display live student records from SQLite database in a styled table.
- ✏️ **Update Student**: Pre-fill selected student data into form and save updates seamlessly.
- 🗑️ **Delete Student**: Remove student records with confirmation dialogs.
- 🔍 **Real-time Search**: Search students dynamically by **Name**, **Register Number**, or **Department**.
- 📊 **Dashboard Metrics**: Real-time cards showing **Total Students**, **Total Departments**, and **4th Year Students**.
- ⚠️ **Validation & Error Handling**: Checks for missing fields, unique register number conflicts, email format, and numeric year values.
- 💾 **Sample Data Auto-Population**: Pre-loads 5 realistic sample students (CSE, IT, ECE, AIDS, CCE) if database is empty.

---

## 🛠️ Technology Stack
- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES6+ `fetch()` API)
- **Backend**: Python 3, Flask framework
- **Database**: SQLite3 (`students.db`)

---

## 📂 Project Structure
```text
StudentManagementSystem/
│
├── app.py                  # Main Flask backend server & REST API endpoints
├── students.db             # SQLite database file (Auto-generated on launch)
├── requirements.txt        # Python dependency specifications
├── README.md               # Project documentation & college guide
│
├── templates/
│   └── index.html          # Responsive single-page application UI
│
└── static/
    ├── style.css           # Custom modern CSS stylesheet
    └── script.js            # Frontend JavaScript CRUD & fetch logic
```

---

## 🗄️ Database Schema (`students.db`)

Table Name: **`students`**

| Column Field | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `id` | `INTEGER` | `PRIMARY KEY AUTOINCREMENT` | Unique Record ID |
| `name` | `TEXT` | `NOT NULL` | Full Name of Student |
| `register_number` | `TEXT` | `NOT NULL UNIQUE` | College Registration Number |
| `department` | `TEXT` | `NOT NULL` | Department Code (CSE, IT, etc.) |
| `year` | `INTEGER` | `NOT NULL` | Academic Year (1 to 4) |
| `email` | `TEXT` | Optional | Student Email Address |
| `phone` | `TEXT` | Optional | Contact Phone Number |

---

## 🚀 REST API Endpoints

All API endpoints return JSON data and use standard HTTP status codes:

| Method | Endpoint | Description | Expected Status |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/students` | Retrieve all student records | `200 OK` |
| `GET` | `/api/students/<id>` | Retrieve a single student by ID | `200 OK` / `404 Not Found` |
| `POST` | `/api/students` | Create a new student record | `201 Created` / `400 Bad Request` |
| `PUT` | `/api/students/<id>` | Update an existing student record | `200 OK` / `400` / `404` |
| `DELETE` | `/api/students/<id>` | Delete a student record by ID | `200 OK` / `404 Not Found` |

---

## 💻 Installation & Setup Guide

### Prerequisites
- Python 3.8 or higher installed on your computer.

### Step 1: Open Terminal / Command Prompt
Navigate to the project directory:
```bash
cd StudentManagementSystem
```

### Step 2: Install Dependencies
```bash
py -m pip install -r requirements.txt
```
*(Or `pip install -r requirements.txt`)*

### Step 3: Run the Application
```bash
python app.py
```

### Step 4: Open in Web Browser
Open your browser and navigate to:
```text
http://127.0.0.1:5000
```

---

## 🧪 Testing CRUD Operations

1. **Test READ**:
   - Open `http://127.0.0.1:5000`. You will immediately see 5 pre-populated sample students in the table and metrics on top.

2. **Test CREATE**:
   - Fill out the form on the left:
     - Name: `Rahul V`
     - Register Number: `7376211CS200`
     - Department: `CSE`
     - Year: `2nd Year`
     - Email: `rahul@example.com`
     - Phone: `9876543299`
   - Click **Add Student**.
   - Verify that a success alert appears and the new record is added to the table.
   - **Validation Test**: Try submitting with an existing Register Number to test duplicate handling.

3. **Test UPDATE**:
   - Click the **Edit** (blue pencil) icon next to any student.
   - Modify any field (e.g. change Department to `AIDS`).
   - Click **Update Student**.
   - Verify the table updates instantly.

4. **Test DELETE**:
   - Click the **Delete** (red trash can) icon next to a student.
   - Confirm the browser prompt.
   - Verify the record is deleted and stats cards update automatically.

5. **Test SEARCH**:
   - Type `CSE` or a student's name into the search bar.
   - Notice the table filters instantly.

---

## 📸 Recommended Screenshots for College Project Report

1. **Dashboard & Main Directory UI**: Showing navigation bar, dashboard cards, student form, and student table with sample data.
2. **Create Operation Success**: Showing form populated, success toast notification, and new row added.
3. **Validation / Error Handling**: Showing alert when register number is duplicated or required field is left blank.
4. **Update Operation**: Showing student data populated into form with button changed to "Update Student".
5. **Delete Confirmation Dialog**: Showing browser confirmation modal when clicking Delete.
6. **Search Feature**: Showing table filtered by keyword in search input.
7. **SQLite Database Verification**: Showing `students.db` data using DB Browser for SQLite or Python script.

---

## 🎓 Viva Presentation Guide & Quick Answers

- **Q: What architecture does this project use?**
  *A: It uses a 3-Tier Web Architecture: HTML/CSS/JS frontend (Presentation Layer), Python Flask backend (Application/Logic Layer), and SQLite relational database (Data Layer).*

- **Q: How does the Frontend talk to the Backend?**
  *A: The frontend uses JavaScript's asynchronous `fetch()` API to issue HTTP REST calls (`GET`, `POST`, `PUT`, `DELETE`) with JSON payloads to Flask endpoints.*

- **Q: How is data persistence handled?**
  *A: Data is saved permanently in an SQLite database file (`students.db`) using Python's standard `sqlite3` library with parametrized SQL queries to prevent SQL injection.*

- **Q: How are unique register numbers enforced?**
  *A: Both in backend validation logic and at the SQLite table schema level using the `UNIQUE` keyword constraint on `register_number`.*
