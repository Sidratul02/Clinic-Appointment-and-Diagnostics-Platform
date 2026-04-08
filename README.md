# Clinic Appointment and Diagnostics Platform

This repository contains the ER diagram for a clinic system that manages patients, doctors, appointments, consultations, diagnostics, reports, and payments.

## Diagram

- ER MODEL 03.png — the exported ER diagram image for the clinic platform.

## Key Entities and Relationships

- **patients**
  - patient_id (PK)
  - tracks patient demographics and contact details.
  - One patient can book many appointments and have many visits.

- **doctors**
  - doctor_id (PK)
  - stores doctor identity, specialty, and contact details.
  - One doctor can attend many appointments.

- **appointments**
  - Appointment_id (PK)
  - patient_id and doctor_id are FKs.
  - stores scheduled date, time, status, and notes.
  - separates booking from the actual consultation/visit.

- **consultations**
  - consultation_id (PK)
  - Appointment_id is an FK.
  - stores diagnosis, symptoms, consultation notes, and timestamp.
  - models the actual medical visit resulting from an appointment.

- **diagnostic_tests**
  - 	est_id (PK)
  - stores test name, description, and cost.
  - reused across multiple prescribed test records.

- **prescribed_tests**
  - prescribed_test_id (PK)
  - consultation_id and 	est_id are FKs.
  - represents tests ordered during a consultation.
  - includes prescription date and test status.

- **reports**
  - 
eport_id (PK)
  - prescribed_test_id is an FK.
  - stores test result, remarks, and generation timestamp.
  - links test outcomes back to the consultation and patient.

- **payments**
  - payment_id (PK)
  - Appointment_id is an FK.
  - stores amount, payment method, payment status, and date.
  - connects billing to the appointment.

## Business Logic in the Design

- Appointment and consultation are distinct: an appointment schedules a visit, while consultation captures the actual doctor encounter and clinical findings.
- A consultation may result in multiple diagnostic test prescriptions.
- Reports are generated for prescribed tests and linked back through prescribed_tests.
- Payments are tied to appointments for clinic billing, ensuring clear connection to the visit request.
- Doctor specialties are stored as an attribute in doctors for simplicity, matching clinic-scale requirements.

## Notes

- This design supports multiple visits per patient and multiple patients per doctor.
- The model keeps tests and reports separate from patient master data while preserving the consultation workflow.

