# OCTVision

OCTVision is an AI-powered medical diagnostic platform designed to revolutionize the early diagnosis of retinal diseases using Optical Coherence Tomography (OCT) imaging technology. The system leverages Inception V3 model, Explainable AI Visualizations, and LLM Report Generation to assist medical professionals in clinical decision-making Developed by a team of Computer Science students:

- **Sibt E Hassan - FA21-BCS-132**: Group Member - Fast APIs, Explainable AI, LLM Integration, Binary Model 
- **Syed Ebraheem Hammad Gillani - FA21-BCS-143**: Group Member - AI Model Development for classification
- **Muhammad Farooq Sheikh - FA21-BCS-074**: Group Member - Full-Stack Web Development (Backend + Frontend + Auth)


## Features

- **AI-Powered Disease Diagnosis:** Upload OCT scans for automatic classification (CNV, DME, DRUSEN, NORMAL) using Inception V3.
- **Explainable AI:** Visual explanations (Grad-CAM heatmaps and animations) highlight disease regions in scans.
- **LLM Report Generation:** Integrated LLaMA 3.1 via GROQ API to generate structured, human-readable diagnostic reports that can be modified by doctors, saved and sent to the patient in the clinical SOAP format.
- **Role-Based Access:**
  - **Admin:** Approve/reject doctors, manage marketplace, view statistics.
  - **Doctor:** Register/login, manage patients, upload scans, view and generate reports, add SOAP notes.
  - **Patient:** Login with contact and access key, view/download medical reports and scan history.
- **Marketplace:** Doctors can add/view medical products and services.
- **Secure Authentication:** JWT-based login for all roles.
- **Responsive UI:** Modern and responsive React interface.

## Tech Stack

- **Frontend:**
  - React, Material-UI, Bootstrap, Axios, React Router
- **Backend (Node.js):**
  - Express, MongoDB (Mongoose), JWT, Multer, Nodemailer, Joi, Twilio
- **AI/ML Backend (Python):**
  - FastAPI, PyTorch, TorchVision, OpenAI API, PIL, NumPy, OpenCV, python-dotenv

## Project Structure

```
FA24CS22_OCTVision Project Code/
  client/         # React frontend
  server/         # Node.js backend
    flask_model/  # FastAPI + PyTorch AI/ML service
```

## Setup Instructions

### Prerequisites

- Node.js
- Python
- MongoDB

### 2. Make sure that you are in the directory "FA24CS22_OCTVision Project Code"

If not in the directory "FA24CS22_OCTVision Project Code", then do:

```bash
cd "FA24CS22_OCTVision Project Code"
```

### 2. Install Frontend Dependencies

```bash
cd client
npm install
```

### 3. Install Backend Dependencies

```bash
cd ../server
npm install
```

### 4. Install Python AI/ML Dependencies

```bash
cd flask_model
pip install torch torchvision fastapi uvicorn python-dotenv pillow numpy opencv-python requests
```

### 5. Start the Services

- **MongoDB:** Ensure MongoDB is running locally or update the connection string.
- **AI/ML Service:**

  ```bash
  cd venv/Bin
  ./activate
  cd ..
  cd ..
  uvicorn main:app --reload
  ```

  or

  ```bash
  cd server/flask_model/venv/Scripts
  ./activate
  cd ..
  cd ..
  uvicorn main:app --reload
  ```

- **Backend:**
  ```bash
  cd server
  npm start
  ```
- **Frontend:**
  ```bash
  cd client
  npm start
  ```

## Usage

- Visit `http://localhost:3000` to access the web app.
- Register as a doctor by entering the details at SignUp page.
- Then access the admin login page by visiting `http://localhost:3000/adminlogin` and enter the credentials: {Email: itsmuhammadfaiz.2000@gmail.com, Password: Faiz123@}
- Approve/Disapprove the account created for the doctor.
- After approving the doctor account, you can login as a doctor by visiting `http://localhost:3000/login` , selecting doctor and then entering the doctor credentials.
- Doctors can upload OCT scans, view results, save SOAP notes, and manage patients.
- Patients can view/download their reports by visiting login page `http://localhost:3000/login`, selecting patient, and then using contact and access key, that is being recieved by the patient at his contact number.
- Admins manage doctor approvals and marketplace.

## API Endpoints (Summary)

- **Backend (Node.js):**
  - `/api/auth` - Login (doctor/patient)
  - `/api/users` - Doctor registration
  - `/api/patients` - Patient management
  - `/api/marketplace` - Marketplace management
  - `/api/admin` - Admin actions
  - `/api/reports` - Patient reports
  - `/api/predict` - Proxy to AI/ML service
- **AI/ML Service (FastAPI):**
  - `POST /predict/` - Predict disease from OCT scan, return class, confidence, heatmap, animation, and report

