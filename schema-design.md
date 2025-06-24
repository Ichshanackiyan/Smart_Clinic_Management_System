## MySQL Database Design
### Table: patients
- id: INT, Primary Key, AUTO_INCREMENT
- name: VARCHAR(100), NOT NULL
- email: VARCHAR(100), UNIQUE, NOT NULL
- phone: VARCHAR(15), NOT NULL
- date_of_birth: DATE
- gender: ENUM('Male', 'Female', 'Other')
- created_at: DATETIME DEFAULT CURRENT_TIMESTAMP

### Table: doctors
- id: INT, Primary Key, AUTO_INCREMENT
- name: VARCHAR(100), NOT NULL
- email: VARCHAR(100), UNIQUE, NOT NULL
- specialization: VARCHAR(100), NOT NULL
- contact_number: VARCHAR(15)
- available_from: TIME
- available_to: TIME

### Table: appointments
- id: INT, Primary Key, AUTO_INCREMENT
- doctor_id: INT, Foreign Key → doctors(id)
- patient_id: INT, Foreign Key → patients(id)
- appointment_time: DATETIME, NOT NULL
- status: ENUM('Scheduled', 'Completed', 'Cancelled'), DEFAULT 'Scheduled'

### Table: admin
- id: INT, Primary Key, AUTO_INCREMENT
- username: VARCHAR(50), UNIQUE, NOT NULL
- password: VARCHAR(255), NOT NULL

### Table: payments (optional)
- id: INT, Primary Key, AUTO_INCREMENT
- patient_id: INT, Foreign Key → patients(id)
- amount: DECIMAL(10,2)
- payment_date: DATETIME DEFAULT CURRENT_TIMESTAMP
- method: ENUM('Card', 'Cash', 'UPI')
- appointment_id: INT, Foreign Key → appointments(id)


## MongoDB Collection Design

### Collection: prescriptions

```json
{
  "_id": "ObjectId('64abc123456')",
  "appointmentId": 51,
  "patientId": 22,
  "doctorId": 13,
  "medication": ["Paracetamol 500mg", "Ibuprofen 200mg"],
  "dosageInstructions": "Take after food, 3 times a day",
  "doctorNotes": "Drink plenty of fluids and rest",
  "refillCount": 1,
  "createdAt": "2025-06-24T10:30:00Z"
}

{
  "_id": "ObjectId('64fed567891')",
  "patientId": 22,
  "doctorId": 13,
  "appointmentId": 51,
  "rating": 4,
  "comments": "Doctor was helpful and listened well",
  "submittedAt": "2025-06-24T11:00:00Z"
}


---


