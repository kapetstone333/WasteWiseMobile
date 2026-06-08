# WASTEWISE

## Development of a Web and Mobile-Based Waste Collection Monitoring and Management System for Local Government Units

WasteWise is a Waste Collection Monitoring and Management System developed for Ormoc City. The platform streamlines waste collection operations through real-time truck tracking, route management, attendance monitoring, schedule management, complaint reporting, and operational analytics.

The system consists of a web application for System Administrators, ENRO Staff, and Barangay Officials, and a mobile application for Garbage Collectors and Residents. WasteWise utilizes real-time communication technologies to provide live updates on collection activities, route progress, attendance status, and community reports.

### System Installation and Deployment Guide

---

### Platform

Web and Mobile-Based Application

### Technologies Used

* Node.js
* Express.js
* React.js
* React Native / Expo
* MongoDB Atlas
* Google Maps API
* Gmail SMTP
* WebSocket Technology

---

# WasteWise System Installation and Deployment Guide

## 1. System Overview

WasteWise is composed of three separate applications:

* Backend (Node.js / Express.js)
* Frontend (Web Application)
* Mobile Application (React Native / Expo)

The system uses:

* MongoDB Atlas for database storage
* Google Maps API for map functionality
* Gmail SMTP for OTP email notifications

---

# 2. GitHub Repositories

## Backend Repository

```text
https://github.com/kapetstone333/WasteWiseBackend.git
```

## Frontend Repository

```text
https://github.com/kapetstone333/WasteWiseFrontend.git
```

## Mobile Repository

```text
https://github.com/kapetstone333/WasteWiseMobile.git
```

---

# 3. Database Configuration

## MongoDB Compass Installation

Download MongoDB Compass:

```text
https://www.mongodb.com/try/download/compass
```

## Connect to the Database

1. Open MongoDB Compass.
2. Click Add New Connection (+).
3. Enter the following URI:

```text
mongodb+srv://kapetstone_db_user:test@cluster0.kz4wjgy.mongodb.net/
```

4. Click Save & Connect.
5. Verify that the database named `waste_wise` is accessible.

---

## MongoDB Connection Used by the System

Create a `.env` file in the root directory of the Backend project.

File Location:

```text
WasteWiseBackend/.env
```

Add the following:

```env
MONGO_URI=mongodb+srv://kapetstone_db_user:test@cluster0.kz4wjgy.mongodb.net/waste_wise?retryWrites=true&w=majority&appName=Cluster0

PORT=5000

EMAIL_USER=kapetstone@gmail.com

EMAIL_PASS=zeozlrodklfwbslz
```

### MongoDB Connection Source Code

File:

```text
WasteWiseBackend/src/config/connect.js
```

Connection Code:

```javascript
mongoose.connect(process.env.MONGO_URI)
```

### If Migrating to Another Database Server

Only update:

```env
MONGO_URI=
```

inside:

```text
WasteWiseBackend/.env
```

---

# 4. Email OTP Configuration

The WasteWise system sends OTP emails using Gmail SMTP.

## Configuration File

```text
WasteWiseBackend/.env
```

Variables:

```env
EMAIL_USER=kapetstone@gmail.com
EMAIL_PASS=zeozlrodklfwbslz
```

## OTP Mailer Source Code

File:

```text
WasteWiseBackend/src/mailer/otp_mailer.js
```

Uses:

```javascript
process.env.EMAIL_USER
process.env.EMAIL_PASS
```

### If Changing the Email Account

Update:

```env
EMAIL_USER=
EMAIL_PASS=
```

with the new Gmail account credentials and App Password.

---

# 5. Backend Installation

## Clone the Repository

```bash
git clone https://github.com/kapetstone333/WasteWiseBackend.git
```

## Install Dependencies

```bash
npm install
```

## Configure Environment Variables

Create:

```text
.env
```

inside:

```text
WasteWiseBackend
```

Add:

```env
MONGO_URI=mongodb+srv://kapetstone_db_user:test@cluster0.kz4wjgy.mongodb.net/waste_wise?retryWrites=true&w=majority&appName=Cluster0

PORT=5000

EMAIL_USER=kapetstone@gmail.com

EMAIL_PASS=zeozlrodklfwbslz
```

## Run Backend

```bash
npm run dev
```

Backend Entry Point:

```text
WasteWiseBackend/src/server.js
```

Expected URL:

```text
http://localhost:5000
```

---

# 6. Frontend Installation

## Clone the Repository

```bash
git clone https://github.com/kapetstone333/WasteWiseFrontend.git
```

## Install Dependencies

```bash
npm install
```

## Configure Backend URL

File:

```text
WasteWiseFrontend/src/services/axios_instance.js
```

Current Configuration:

```javascript
baseURL: 'http://localhost:5000'
```

### If Backend is Deployed on Another Server

Example:

```javascript
baseURL: 'https://your-backend-domain.com'
```

Replace the URL with the actual backend server URL.

---

## Configure Google Maps API

File:

```text
WasteWiseFrontend/index.html
```

Locate:

```html
<script
src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=marker&loading=async"
async
defer>
</script>
```

Replace:

```text
YOUR_API_KEY
```

with the active Google Maps API key.

---

## Run Frontend

```bash
npm run dev
```

---

# 7. Mobile Application Installation

## Clone the Repository

```bash
git clone https://github.com/kapetstone333/WasteWiseMobile.git
```

## Install Dependencies

```bash
npm install
```

## Configure Backend URL

File:

```text
WasteWiseMobile/services/axios_instance.js
```

Current Configuration:

```javascript
baseURL: 'http://localhost:5000'
```

### If Backend is Deployed on Another Server

Example:

```javascript
baseURL: 'https://your-backend-domain.com'
```

Replace the URL with the actual backend server URL.

---

## Configure Google Maps API

File:

```text
WasteWiseMobile/app.json
```

Locate:

```json
"apiKey": "YOUR_API_KEY"
```

Replace:

```text
YOUR_API_KEY
```

with the active Google Maps API key.

---

## Run Mobile Application

```bash
npm run start
```

---

# 8. Files to Update When Migrating to Another Server

| Configuration            | File Location                                    |
| ------------------------ | ------------------------------------------------ |
| MongoDB Connection       | WasteWiseBackend/.env                            |
| Email OTP Configuration  | WasteWiseBackend/.env                            |
| Frontend Backend URL     | WasteWiseFrontend/src/services/axios_instance.js |
| Mobile Backend URL       | WasteWiseMobile/services/axios_instance.js       |
| Frontend Google Maps API | WasteWiseFrontend/index.html                     |
| Mobile Google Maps API   | WasteWiseMobile/app.json                         |

---

# 9. Deployment Checklist

```text
✓ MongoDB Atlas is accessible
✓ MongoDB URI is configured
✓ .env file exists
✓ EMAIL_USER is configured
✓ EMAIL_PASS is configured
✓ Backend server is running
✓ Frontend baseURL is correct
✓ Mobile baseURL is correct
✓ Google Maps API key is configured
✓ npm dependencies are installed
✓ No startup errors are present
```

---

# 10. Troubleshooting Guide

## MongoDB Connection Error

Possible Causes:

* Invalid MONGO_URI
* Database server unavailable
* MongoDB Atlas network restrictions

Solution:

```text
1. Verify MONGO_URI.
2. Verify internet connection.
3. Verify Atlas Network Access settings.
4. Verify MongoDB Atlas cluster is running.
```

---

## Backend Not Starting

Possible Causes:

* Missing .env file
* Invalid environment variables
* Missing npm packages

Solution:

```text
1. Verify .env file exists.
2. Verify MONGO_URI, EMAIL_USER, and EMAIL_PASS.
3. Run npm install.
4. Check terminal logs for errors.
```

---

## Frontend Cannot Connect to Backend

Possible Causes:

* Backend not running
* Incorrect baseURL

Solution:

```text
1. Verify backend server is running.
2. Verify src/services/axios_instance.js.
3. Verify the backend URL is accessible.
```

---

## Mobile Cannot Connect to Backend

Possible Causes:

* Incorrect baseURL
* Backend unavailable

Solution:

```text
1. Verify services/axios_instance.js.
2. Verify backend URL is accessible.
3. Verify backend service is online.
```

---

## Google Maps Not Loading

Possible Causes:

* Invalid API key
* Google Maps API not enabled

Solution:

```text
1. Verify Google Maps API key.
2. Enable Maps JavaScript API.
3. Verify Google Cloud billing configuration.
```

---

## OTP Email Not Sending

Possible Causes:

* Invalid EMAIL_USER
* Invalid EMAIL_PASS
* Expired Gmail App Password

Solution:

```text
1. Verify EMAIL_USER.
2. Verify EMAIL_PASS.
3. Generate a new Gmail App Password if necessary.
4. Restart the backend service.
```

---

# 11. Turnover Notes

For future maintenance or deployment, the following configurations are the most important:

* MongoDB Connection → `WasteWiseBackend/.env`
* Email OTP Configuration → `WasteWiseBackend/.env`
* Frontend API Connection → `WasteWiseFrontend/src/services/axios_instance.js`
* Mobile API Connection → `WasteWiseMobile/services/axios_instance.js`
* Frontend Google Maps API → `WasteWiseFrontend/index.html`
* Mobile Google Maps API → `WasteWiseMobile/app.json`

If the system is moved to a new server, update these files first before running the application.

---

**@2026**
