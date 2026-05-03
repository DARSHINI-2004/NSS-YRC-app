# NSS & YRC Volunteer Management App

>  Note: The source code for this project is private as the application is currently in use.  
>  The APK file is provided above — you can download and use the application directly.
>  Signup with your own credentials and login with the same (student side). Admin side is kept in private mode


---

## Overview
Android application to digitally manage NSS and YRC volunteer programs with secure attendance and contribution tracking.

---

## Features
- Dual-role system (Admin / Student)
- Geo-fenced attendance validation
- Time window-based attendance control
- QR-based authentication for indoor events
- One-time attendance per user/device
- Proof of work submission (image + description)
- Admin approval dashboard (approve/reject)
- Real-time data synchronization

---

## Tech Stack
- Kotlin (Android)
- Firebase (Backend-as-a-Service)
  - Firebase Authentication (login & role management)
  - Firebase Firestore (database)
  - Firebase Storage (image storage)
- Google Places API (location validation)
- NTP (Network Time Protocol for secure time)

---

## Workflow
1. User logs in (Firebase Authentication)
2. Role (Admin/Student) fetched from Firestore
3. Admin creates event (location, time, QR)
4. Student marks attendance:
   - Location validated (geo-fencing)
   - Time validated (NTP)
   - QR validated (if required)
5. Attendance stored in Firestore
6. Student uploads proof (image + description)
7. Image stored in Firebase Storage
8. Image URL + metadata stored in Firestore
9. Admin reviews and approves/rejects
10. Updates reflected in real time

---

## Architecture
App → Firebase Auth → Firestore → Validation (Location + Time + QR)  
→ Firebase Storage (Images) → Firestore (Metadata) → Admin Dashboard

---

## Data Model
users/{userId}
- name
- role

events/{eventId}
- location
- startTime
- endTime
- qrCode

attendance/{recordId}
- userId
- eventId
- timestamp

submissions/{submissionId}
- userId
- eventId
- imageUrl
- description
- status

---

## Security Features
- Geo-fencing for location-based validation
- Time validation using NTP (prevents device time manipulation)
- QR-based authentication for indoor events
- One-time attendance restriction
- Role-based access control

---

## Key Highlights
- Real-time updates using Firestore
- No traditional backend (Firebase handles backend services)
- Lightweight and scalable system
- Prevents proxy/fake attendance

