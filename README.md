# Student Course Management System

A beginner-friendly, responsive web application built for a college full-stack development lab project. This application allows college staff and administrators to manage **Student Records**, **Courses**, and **Student Course Enrollments** with full **CRUD (Create, Read, Update, Delete)** operations, form validation, search filtering, and a local **JSON Server** mock REST API.

---

## 1. Project Description

Managing student profiles, academic courses, and course enrollments manually using paper registers or spreadsheets is time-consuming and prone to human error. The **Student Course Management System** provides a clean, single-page React interface connected to a RESTful JSON Server backend (`db.json`) so administrators can add, view, search, update, and delete students, courses, and enrollments in real time.

> **Important Note on JSON Server:**
> This project uses **JSON Server** as a **mock REST API** for educational and lab demonstration purposes. JSON Server reads from and writes directly to a local `db.json` file. It is **not** a production backend framework (like Spring Boot or Express with authentication) or a relational SQL database (like MySQL or PostgreSQL).

---

## 2. Key Features

### A. Dashboard Module
- Displays live summary counters for **Total Students**, **Total Courses**, and **Total Enrollments** (with a breakdown of *Active* vs. *Cancelled* enrollments).
- Displays a table of the 5 most recent course enrollments with resolved Student Names and Course Names.
- Provides quick-navigation buttons to jump directly to the Students, Courses, or Enrollments modules.

### B. Student Management Module
- **Fields:** Student ID (unique), Full Name, Email Address, Phone Number, Department, Semester.
- **Create:** Add new student records with client-side validation for required fields, unique Student ID, valid email format, and 10-digit phone number.
- **Read & Search:** View all students in a responsive Bootstrap table and filter instantaneously by Student Name, Student ID, or Department.
- **Update:** Load any existing student into the form, edit their details, and persist changes via `PUT /students/:id`.
- **Delete:** Remove a student record after a browser confirmation prompt (`DELETE /students/:id`).

### C. Course Management Module
- **Fields:** Course ID (unique), Course Name, Course Code, Duration, Department.
- **Create:** Add new courses with validation for required fields and unique Course ID.
- **Read & Search:** Display all courses in a structured table with instant search by Course Name, Course Code, Course ID, or Department.
- **Update & Delete:** Edit course details or delete a course with confirmation.

### D. Enrollment Management Module
- **Fields:** Enrollment ID (unique), Student ID, Course ID, Enrollment Date, Status (`Active` or `Cancelled`).
- **Relational Lookups:** Dropdown menus are dynamically populated from existing Students and Courses in `db.json`.
- **Resolved Display:** Displays both the IDs and the corresponding **Student Full Name** and **Course Name + Code** in the enrollments table.
- **Duplicate Prevention:** Validates that the selected student and course exist and prevents enrolling the same student in the same course twice.
- **Quick Status Toggle:** Toggle an enrollment between `Active` and `Cancelled` with a single click or edit full details via the form.

---

## 3. Technologies Used

| Technology | Role in Project |
| :--- | :--- |
| **HTML5** | Page structure and root mount container (`index.html`) |
| **CSS3** | Custom layout, sidebar styling, and responsive adjustments (`src/index.css`) |
| **JavaScript (ES6+)** | Application logic, array filtering, async/await, and state handling |
| **React 18 (with Vite)** | Component-based frontend UI (`useState`, `useEffect`, `useCallback`) |
| **Bootstrap 5** | Responsive grid, cards, tables, badges, alerts, and form styling |
| **JSON Server** | Mock REST API serving `db.json` over HTTP on port `3000` |
| **Fetch API** | Native browser HTTP client (`src/services/api.js`) for `GET`, `POST`, `PUT`, `PATCH`, and `DELETE` requests |
| **VS Code & Git/GitHub** | Recommended code editor and version control for lab submission |

---

## 4. Project Folder Structure

```text
student-course-management/
├── index.html
├── package.json
├── vite.config.js
├── db.json
├── .gitignore
├── README.md
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── index.css
    ├── components/
    │   ├── Navbar.jsx
    │   ├── Sidebar.jsx
    │   ├── Dashboard.jsx
    │   ├── StudentManagement.jsx
    │   ├── StudentForm.jsx
    │   ├── CourseManagement.jsx
    │   ├── CourseForm.jsx
    │   ├── EnrollmentManagement.jsx
    │   └── EnrollmentForm.jsx
    └── services/
        └── api.js
```

---

## 5. Prerequisites

Before running this project on your computer, ensure you have installed:
1. **Node.js** (v18.0.0 or higher recommended) — includes `npm` (Node Package Manager). Verify with:
   ```bash
   node -v
   npm -v
   ```
2. **Visual Studio Code (VS Code)** — recommended code editor.
3. **Git** — for version control and uploading to GitHub.

---

## 6. Installation and Execution Instructions

Because this project has both a **Mock Backend (JSON Server)** and a **Frontend (React + Vite)**, you must run them **simultaneously in two separate terminals**.

### Step 1: Extract or Enter the Project Folder
Open your terminal (Command Prompt / PowerShell on Windows, or Terminal on macOS/Linux) and navigate into the project folder:
```bash
cd student-course-management
```

### Step 2: Install Dependencies
Install React, Vite, Bootstrap, and JSON Server into `node_modules`:
```bash
npm install
```

### Step 3: Start JSON Server (Terminal 1)
In your first terminal window, start the mock REST API server watching `db.json` on port `3000`:
```bash
npm run server
```
*(Alternatively, you can run `npx json-server@0.17.4 --watch db.json --port 3000`)*

Leave this terminal running. You will see endpoints exposed at:
- `http://localhost:3000/students`
- `http://localhost:3000/courses`
- `http://localhost:3000/enrollments`

### Step 4: Start the React Development Server (Terminal 2)
Open a **second terminal window** in the same `student-course-management` folder and start Vite:
```bash
npm run dev
```

### Step 5: Open the Application in Your Browser
Open your web browser (Chrome, Edge, or Firefox) and visit:
- **Frontend Application URL:** `http://localhost:5173`
- **Mock REST API Base URL:** `http://localhost:3000`

### How to Change the API Base URL
If port `3000` is busy on your computer and you start JSON Server on another port (for example, `--port 4000`), open `src/services/api.js` and update line 10:
```javascript
export const API_BASE_URL = 'http://localhost:4000';
```

---

## 7. REST API Endpoint Documentation

All CRUD operations in `src/services/api.js` communicate with JSON Server at `http://localhost:3000`:

| HTTP Method | Endpoint | Description | Request Body Required |
| :--- | :--- | :--- | :--- |
| `GET` | `/students` | Fetch all student records | No |
| `GET` | `/students/:id` | Fetch a single student by ID | No |
| `POST` | `/students` | Create a new student record | Yes (JSON) |
| `PUT` | `/students/:id` | Replace/update a student record | Yes (JSON) |
| `PATCH` | `/students/:id` | Partially update a student record | Yes (JSON) |
| `DELETE` | `/students/:id` | Delete a student record by ID | No |
| `GET` | `/courses` | Fetch all course records | No |
| `POST` | `/courses` | Create a new course record | Yes (JSON) |
| `PUT` | `/courses/:id` | Update an existing course record | Yes (JSON) |
| `DELETE` | `/courses/:id` | Delete a course record by ID | No |
| `GET` | `/enrollments` | Fetch all enrollment records | No |
| `POST` | `/enrollments` | Create a new course enrollment | Yes (JSON) |
| `PUT` | `/enrollments/:id` | Update an enrollment record or status | Yes (JSON) |
| `DELETE` | `/enrollments/:id` | Delete an enrollment record by ID | No |

### Testing the API Independently
With `npm run server` running, you can test the REST API directly in a browser or terminal:
```bash
# Fetch all students
curl http://localhost:3000/students

# Fetch a single student by ID
curl http://localhost:3000/students/STU-101
```

---

## 8. Sample Data Description (`db.json`)

The included `db.json` file comes pre-populated with realistic sample data so the application works out of the box:
- **6 Students (`STU-101` to `STU-106`):** Aarav Sharma, Priya Nair, Rohan Verma, Sneha Kulkarni, Karthik Reddy, and Ananya Iyer across Computer Science, Information Technology, Electronics & Communication, Mechanical Engineering, and Data Science.
- **6 Courses (`CRS-201` to `CRS-206`):** Database Management Systems (`CS301`), Full-Stack Web Development (`IT304`), Digital Signal Processing (`EC205`), Data Structures and Algorithms (`CS201`), Machine Learning Foundations (`DS401`), and Robotics and Automation (`ME310`).
- **6 Enrollments (`ENR-301` to `ENR-306`):** Valid enrollment mappings linking students to courses with `Active` and `Cancelled` statuses.

---

## 9. Testing Instructions

1. Start both servers (`npm run server` and `npm run dev`).
2. Verify that the **Dashboard** displays `6` Students, `6` Courses, and `6` Enrollments, and the top bar shows `JSON Server: Online`.
3. Navigate to **Students**, try submitting an empty form to verify validation errors, then add a new student (`STU-107`), search for them, edit their semester, and delete a test record.
4. Navigate to **Courses**, create a new course (`CRS-207`), edit its duration, and verify `db.json` updates automatically.
5. Navigate to **Enrollments**, enroll a student in a course, verify that attempting to enroll the exact same student and course again triggers the **Duplicate Warning**, and toggle an enrollment status between `Active` and `Cancelled`.

---

## 10. Known Limitations

1. **Mock Backend Only:** JSON Server stores data in a flat JSON file (`db.json`) and lacks multi-user concurrency locks, SQL joins, or database transactions.
2. **No Authentication / Role-Based Access:** Designed for a beginner lab demonstration, the app does not require login credentials or JWT authentication.
3. **Client-Side Referential Checks:** Foreign key lookups (`studentId` and `courseId`) are resolved in React rather than enforced by a relational database engine.

---

## 11. Git and GitHub Submission Guide (Beginner Step-by-Step)

Follow these commands inside the `student-course-management` folder to upload your source code to GitHub (the `.gitignore` file automatically excludes `node_modules/`, `dist/`, and `.env` files):

```bash
# 1. Initialize a local Git repository
git init

# 2. Check which files will be tracked (verify node_modules is NOT listed)
git status

# 3. Stage all project files
git add .

# 4. Create your first commit
git commit -m "Initial commit: Complete Student Course Management System lab project"

# 5. Rename default branch to main
git branch -M main

# 6. Link to your empty GitHub repository (replace <YOUR-USERNAME> with your GitHub username)
git remote add origin https://github.com/<YOUR-USERNAME>/student-course-management.git

# 7. Push your code to GitHub
git push -u origin main
```
