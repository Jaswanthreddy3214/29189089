# Clinic Management System

This is a console-based application for managing a clinic's operations, including patient<br>
management, appointment scheduling, and medical record maintenance. The application<br>
is developed using Core Java, MySQL, and JDBC to interact with the database.<br>

## Features

1. Patient Management<br>
- Add a new patient
- View patient details
- Update patient information
- Delete a patient
2.  Appointment Management<br>
- Schedule a new appointment
- View appointment details
- Update appointment information
- Cancel an appointment
3.  Medical Record Management<br>
- Add a new medical record
- View medical record details
- Update medical record information
- Delete a medical record

4. Custom Exceptions
- Custom exceptions are implemented for specific error handling, such as PatientNotFoundException,<br> AppointmentNotFoundException, InvalidAppointmentDateException, and more.<br>
  
## Technologies Used
**Java:** Core Java for implementing the business logic.<br>
**MySQL:** Database for storing patient, appointment, and medical record information.<br>
**JDBC:** Java Database Connectivity (JDBC) for interacting with the MySQL database.<br>

## Database Schema
### Patient Table
```sql
CREATE TABLE Patient (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    Age int NOT NULL,
    gender VARCHAR(10) NOT NULL,
    contact_info VARCHAR(255) NOT NULL
);
```
### Appointment Table
```sql

CREATE TABLE Appointment (
    appointment_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    appointment_date DATE NOT NULL,
    doctor_name VARCHAR(100) NOT NULL,
    status VARCHAR(20) CHECK (status IN ('scheduled', 'completed', 'cancelled')),
    FOREIGN KEY (patient_id) REFERENCES Patient(patient_id)
);
```
### MedicalRecord Table
```sql
CREATE TABLE MedicalRecord (
    record_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    diagnosis TEXT NOT NULL,
    treatment TEXT NOT NULL,
    date DATE NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES Patient(patient_id)
);
```
## Setup Instructions
### Pre-requisites
- Java: JDK 8 or above
- MySQL: MySQL Server
- JDBC Driver: MySQL Connector/J (JDBC driver)
## Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/clinic-management-system.git
cd clinic-management-system
```
## Step 2: Configure the Database
### 1. Create a MySQL database for the project:
```sql
CREATE DATABASE clinic_management;
```
### 2.Update the database connection settings in the DatabaseConnection.java file:
```java
private static final String URL = "jdbc:mysql://localhost:3306/clinic_management";
private static final String USER = "yourusername";
private static final String PASSWORD = "yourpassword";
```
### Step 3: implement the CRUD OPERATIONS ON every functions.
```java
add();
viewAll();
update();
delete();
```

## Step 4: Compile and Run the Application
### 1.Compile the Java files:
```bash
javac -cp .:mysql-connector-java-X.X.X.jar *.java
```
### 2.Run the application:
```bash
java -cp .:mysql-connector-java-X.X.X.jar Main
```
## Step 5: Use the Application
- Follow the on-screen menu to manage patients, appointments, and medical records.
# Custom Exceptions

The application uses custom exceptions to handle specific error scenarios:

- **PatientNotFoundException:** Thrown when a patient is not found in the database.
- **AppointmentNotFoundException:** Thrown when an appointment is not found.
- **MedicalRecordNotFoundException:** Thrown when a medical record is not found.
These exceptions improve error handling and provide meaningful messages to the user.

# Future Enhancements
- **User Authentication:** Implement a login system for clinic staff.
- **Advanced Reporting:** Generate reports for patients, appointments, and medical records.
- **GUI Interface:** Develop a graphical user interface (GUI) using JavaFX or Swing.
