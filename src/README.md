# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities
- Data persists across server restarts with SQLite

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   uvicorn app:app --reload
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity                                             |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student from an activity                            |

## Data Model

The application now uses SQLite (`school.db`) and initializes schema on startup.

Tables:

1. **activities**

   - Description
   - Schedule
   - Maximum number of participants allowed
   - Unique activity name

2. **users**

   - Email (primary key)

3. **registrations**

   - Many-to-many link between activities and users

## Database Initialization and Reset

- On first startup, the app creates tables and seeds default activities.
- DB file location: `src/school.db`
- To reset to a clean seeded state, stop the server and delete `src/school.db`, then restart.

