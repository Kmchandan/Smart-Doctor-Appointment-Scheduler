OpenCare -  Doctor Appointment Scheduler

1. Problem Statement

Patients often struggle to find available doctors and book appointments efficiently. 
OpenCare is a fully open-source appointment scheduling platform that simplifies the process while ensuring privacy, interoperability,
and offline support.

---

2. Features (MVP)

For Patients
✅ FOSS-Compliant User Authentication (Self-hosted JWT-based, No Google/Facebook)
✅ Search doctors by specialization & location (OpenStreetMap + Leaflet.js)
✅ View available time slots
✅ Book an appointment
✅ Offline Booking Support (PWA with Workbox)
✅ View appointment history

For Doctors
✅ User authentication (Signup/Login)
✅ Manage available time slots
✅ Accept or reject appointments
✅ View upcoming appointments


---

3. Tech Stack (FOSS-Compliant)

Frontend: React.js (PWA) + Leaflet.js (OpenStreetMap)
Backend: Node.js (Express)
Database: PostgreSQL / Supabase (FOSS alternative to Firebase)
Authentication: JWT (Self-hosted)
Offline Mode: Service Workers (Workbox)

---

4. System Design (Basic Flow)

*. User Authentication → Patients & doctors register and log in.

*. Doctor Profile Setup → Doctors enter their specialization and availability.

*. Search & View Doctors → Patients filter doctors by specialty & location (using OpenStreetMap).

*. Appointment Booking → Patients select a time slot and confirm the booking.

*. Doctor approval → Doctors can accept or reject bookings.

---

5. Database Schema (Example - PostgreSQL/Supabase)

Users Table (Doctors & Patients)

CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL,
  role TEXT CHECK (role IN ('doctor', 'patient')),
  specialization TEXT DEFAULT NULL,
  available_slots TEXT[]
);

Appointments Table

CREATE TABLE appointments (
  id SERIAL PRIMARY KEY,
  doctor_id INTEGER REFERENCES users(id),
  patient_id INTEGER REFERENCES users(id),
  date_time TIMESTAMP NOT NULL,
  status TEXT CHECK (status IN ('pending', 'confirmed', 'canceled'))
);

---

6. Deployment (FOSS-Friendly Hosting)

Frontend: Vercel / Netlify
Backend: Railway.app / Render.com
Database: Supabase (FOSS alternative to Firebase)

7. Future Enhancements (Beyond MVP - Post Hackathon)

🚀 AI-based Doctor Recommendations (Using TensorFlow.js)
📞 Encrypted Messaging Between Doctors & Patients (WebSockets)
💳 Payment Gateway for Paid Consultations (Only using Open-Source Payment Systems)
📱 Mobile App Version (React Native / Flutter with FOSS Plugins)

---

Why OpenCare is FOSS-Compliant for the Hackathon?

✔ No proprietary APIs or services used
✔ Fully open-source & licensed under MIT
✔ Beyond simple CRUD (Offline mode, AI, Video Calls)
✔ Self-hosted authentication & video consultations
✔ Clear documentation & demo video for evaluation

---

8. Submission Requirements Checklist

✅ Well-structured README.md (Clear project overview, setup, usage)
✅ Plagiarism-free code with proper credits
✅ GitHub Repository with commits showing progress

---
AI-based doctor recommendations (using TensorFlow.js)
Offline-first support (PWA with Workbox)
Self-hosted video consultation (Jitsi Meet)
FOSS-based map integration (Leaflet.js + OpenStreetMap)
Well-structured README
---
