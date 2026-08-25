# Capacity Connect

A Digital Capacity Building and Learning Management Portal, built for Smart India Hackathon 2026.

**Problem Statement ID:** 26075
**Organization:** Ministry of Earth Sciences (MoES)
**Department:** India Meteorological Department (IMD)
**Theme:** Smart Education

## What is this project?

Government departments like IMD constantly need to train their staff, track who has completed what training, and figure out who is qualified to teach which subject. Right now this kind of thing is scattered across emails, spreadsheets, and in-person sessions with no central record.

Capacity Connect is a single web portal that brings all of this together. It has three types of users — Trainees, Trainers, and Admins — and each one gets a different set of tools based on what they need to do.

## Who uses it and what can they do

### Trainee
This is anyone signing up to learn something. A trainee can:
- Sign up and log in securely
- Build a profile with their qualifications, work experience, interests, skills, and certificates
- Browse and enroll in available courses
- Access learning resources uploaded by trainers
- Take subject-wise MCQ tests to check their understanding
- Give feedback on courses and training sessions

### Trainer
This is the person conducting the training. A trainer can:
- Manage their own profile
- Create questionnaires/quizzes and set deadlines for them
- Keep track of which trainees are participating and how well they're doing
- Upload recorded lectures, presentations, and study material to a library that trainees can access

### Admin
This is the person running the whole platform. An admin can:
- Approve new users and assign or change their roles
- View dashboards showing courses, enrollments, certifications, assessment results, and participation numbers
- Post notifications, announcements, achievements, and new learning content that shows up on the homepage
- Use competency mapping to figure out which trainer is the best fit to teach a particular subject, based on their skills

## Tech Stack

We're keeping this simple and using things our team already knows well, so we can move fast during the hackathon:

- **Frontend:** React.js with Tailwind CSS for styling, Axios for API calls
- **Backend:** Node.js with Express.js
- **Database:** MongoDB — works well here because profiles and courses don't follow a rigid structure
- **Authentication:** JWT tokens with bcrypt for password hashing
- **File uploads:** Cloudinary (for lecture videos, presentations, certificates)
- **Charts for admin dashboard:** Recharts
- **Deployment:** Vercel for frontend, Render for backend, MongoDB Atlas for database

## How the project is organized

```
capacity-connect/
├── client/                 → React app
│   └── src/
│       ├── pages/
│       │   ├── trainee/
│       │   ├── trainer/
│       │   └── admin/
│       ├── components/
│       ├── context/        → stores logged-in user + role
│       └── services/       → API calls
│
├── server/                 → Express app
│   ├── models/             → User, Course, Questionnaire, Enrollment, Certificate, Notification
│   ├── routes/
│   ├── controllers/
│   ├── middleware/         → auth check, role check
│   └── server.js
│
└── README.md
```

## Team

We split into 6 people, grouped as 1 + 2 + 2 + 1 based on the kind of work involved:

**1 person — Team Lead / Design**
Handles the wireframes, keeps the design consistent across pages, coordinates the team, and puts together the final presentation and demo.

**2 people — Frontend**
One person builds the login/signup screens and everything a trainee sees (profile, courses, quizzes, feedback form). The other builds everything a trainer sees (questionnaire builder, upload screens) plus the admin dashboards and charts.

**2 people — Backend**
One person handles authentication, user roles, and the trainee/trainer APIs, including file uploads. The other handles courses, quizzes/assessments, admin APIs, notifications, and the competency mapping logic.

**1 person — Database, Deployment & Testing**
Designs how data is structured in MongoDB, sets up hosting for both frontend and backend, and tests the APIs with Postman to catch bugs before demo day.

## Rough plan for building this

We don't need to overthink this, just keep moving week by week:

**Week 1** — Finalize wireframes and database structure, set up the repo, get the basic React and Express apps running and talking to each other.

**Week 2** — Get signup/login working properly, including the admin approval step, and set up role-based routing so each user type sees their own pages.

**Week 3** — Build out everything for trainees: profile page, browsing and enrolling in courses, taking MCQ tests, submitting feedback.

**Week 4** — Build out everything for trainers: creating questionnaires with deadlines, uploading lecture material, viewing how their trainees are performing.

**Week 5** — Build the admin side: approving users, dashboards with real numbers, posting announcements, and the competency mapping feature.

**Week 6** — Fix bugs, make sure it looks fine on mobile too, deploy everything, and prepare the demo/presentation.

## A few things we're keeping in mind

- Passwords are never stored as plain text, they're hashed with bcrypt
- Every API route checks whether the logged-in user's role is allowed to access it
- New users can't log in until an admin approves their account
- The site needs to work reasonably well on a phone, not just a laptop

## Setting it up locally

```bash
git clone https://github.com/<your-username>/capacity-connect.git
cd capacity-connect

# backend
cd server
npm install
npm run dev

# frontend, in a separate terminal
cd client
npm install
npm start
```

You'll also need a `.env` file inside `server/` with your own values:

```
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

## Built for

Smart India Hackathon 2026, Problem Statement 26075, submitted for the Ministry of Earth Sciences (MoES) and India Meteorological Department (IMD).
