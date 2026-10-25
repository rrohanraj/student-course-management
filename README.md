# Student Course Management System

## 1. Project Overview

The **Student Course Management System** is a web-based application developed to simplify the management of student records, academic courses, and course enrollments. It provides a centralized interface for performing CRUD (Create, Read, Update, and Delete) operations on student, course, and enrollment data.

The application consists of a React-based frontend and a REST API powered by JSON Server. The project demonstrates frontend development, API integration, data management, form validation, and basic referential integrity checks.

## 2. Objectives

- Develop a user-friendly interface for managing student information.
- Implement CRUD operations for students, courses, and enrollments.
- Integrate a React frontend with a RESTful API.
- Store and manage application data using a JSON-based data source.
- Implement input validation and duplicate enrollment checks.
- Provide search and record management functionality.
- Demonstrate the interaction between a frontend application and a mock backend service.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| React | Frontend user interface |
| Vite | Development server and build tooling |
| JavaScript | Application logic |
| Bootstrap | UI styling and responsive layout, if used in the implementation |
| JSON Server | Mock REST API backend |
| JSON | Local data storage in `db.json` |
| npm | Dependency management |

## 4. Project Structure

The project follows a frontend and backend development structure.

```text
student-course-management/
├── public/                 # Public static assets, if present
├── src/
│   ├── components/         # Reusable UI components, if present
│   ├── pages/              # Application pages, if present
│   ├── services/
│   │   └── api.js          # API configuration and service functions
│   ├── App.jsx              # Main application component, if present
│   └── main.jsx             # Frontend entry point, if present
├── db.json                  # Sample data and JSON Server database
├── index.html               # HTML entry point
├── package.json             # Dependencies and npm scripts
├── package-lock.json        # Dependency lockfile
└── README.md                # Project documentation
```

*Note: The structure above illustrates the expected organization. The actual submitted source files determine the final project structure.*

## 5. Prerequisites

The following software is required to run the project:

- **Node.js:** Version 18 or higher recommended.
- **npm:** Installed with Node.js.
- **Web browser:** A modern browser such as Google Chrome, Microsoft Edge, or Mozilla Firefox.

Visual Studio Code is recommended for inspecting and running the source code but is not mandatory.

Verify the Node.js and npm installations using:

```bash
node -v
npm -v
```

## 6. Installation and Execution

### 6.1 Extract the Project

Extract the submitted ZIP archive and open a terminal in the project root directory, where `package.json` is located.

### 6.2 Install Dependencies

Run the following command:

```bash
npm install
```

This installs the dependencies required by the frontend and backend.

### 6.3 Start the Backend Server

Open a terminal in the project root directory and execute:

```bash
npm run server
```

The JSON Server backend starts on port `3000` and reads the data from `db.json`.

Available API resources:

- `http://localhost:3000/students`
- `http://localhost:3000/courses`
- `http://localhost:3000/enrollments`

Keep the backend terminal running while using the application.

### 6.4 Start the Frontend Application

Open a second terminal in the same project directory and execute:

```bash
npm run dev
```

Vite starts the frontend development server. The default application URL is:

**Frontend:** http://localhost:5173/

**Backend base URL:** http://localhost:3000

Both servers must remain active for API-dependent features to function correctly.

## 7. API Configuration

The frontend communicates with the JSON Server backend through the API service layer.

The default API base URL is:

```javascript
http://localhost:3000
```

If the backend port is changed, the API base URL in `src/services/api.js` must be updated accordingly, provided that this file and configuration are present in the submitted implementation.

## 8. REST API Documentation

The application uses JSON Server to expose REST endpoints for student, course, and enrollment records.

| HTTP Method | Endpoint | Description |
|---|---|---|
| GET | `/students` | Retrieve all student records |
| GET | `/students/:id` | Retrieve a specific student |
| POST | `/students` | Create a student record |
| PUT | `/students/:id` | Replace an existing student record |
| PATCH | `/students/:id` | Partially update a student record |
| DELETE | `/students/:id` | Delete a student record |
| GET | `/courses` | Retrieve all courses |
| POST | `/courses` | Create a course |
| PUT | `/courses/:id` | Update a course |
| DELETE | `/courses/:id` | Delete a course |
| GET | `/enrollments` | Retrieve all enrollments |
| POST | `/enrollments` | Create an enrollment |
| PUT | `/enrollments/:id` | Update an enrollment |
| DELETE | `/enrollments/:id` | Delete an enrollment |

These endpoints are available at `http://localhost:3000` when the backend is running. The operations listed describe the intended API interface; their implementation should be verified against the submitted source code.

## 9. Sample Data

The `db.json` file serves as the initial data source for the application.

The provided sample dataset is intended to demonstrate:

- Student information and academic departments.
- Course information, including course identifiers and names.
- Enrollment records linking students to courses.
- Enrollment statuses, such as Active and Cancelled.

The application can be tested using the supplied records. New records created during testing are stored in `db.json` by JSON Server.

## 10. Testing and Verification

The following test cases can be used to evaluate the application.

| Test Case | Expected Result |
|---|---|
| Launch the application | Dashboard loads successfully |
| Retrieve student records | Student records are displayed |
| Add a student | A valid new record is created |
| Submit an invalid student form | Appropriate validation feedback is displayed, if implemented |
| Search for a student | Matching records are displayed, if search is implemented |
| Edit a student | Updated information is saved |
| Delete a student | The selected record is removed |
| Retrieve course records | Course records are displayed |
| Create or update a course | Changes are reflected in the data source |
| Create an enrollment | A valid enrollment record is created |
| Attempt a duplicate enrollment | Duplicate
