# System Analysis and Design Assignment

**Name:** Justice Stephen Nkum  
**Student ID:** 226054683  

## Scenario: University Student Management System

The University Student Management System is designed to help a university manage student information, course registration, and student fee payments through an online platform.

---

# 1. Domain Context Mapping

## 1.1 Student Management Context

### Primary Entities
- Student
- Student Profile
- Programme
- Academic Record

### Responsibilities
- Create and update student profiles
- Store student information
- Manage programme information
- Maintain academic records

---

## 1.2 Course Registration Context

### Primary Entities
- Course
- Course Registration
- Semester
- Course Prerequisite
- Student

### Responsibilities
- Display available courses
- Check course prerequisites
- Register students for courses
- Allow students to add or drop courses
- Maintain students' registered courses

---

## 1.3 Fees and Payment Context

### Primary Entities
- Student
- Invoice
- Fee
- Payment
- Payment Receipt

### Responsibilities
- Generate student fee invoices
- Record student payments
- Check outstanding balances
- Generate payment receipts
- Update payment status

---

# 2. Mermaid Context Diagram

```mermaid
graph TD

    Student((Student))
    Admin((Academic Administrator))
    Finance((Finance Officer))

    SM[Student Management Context]
    CR[Course Registration Context]
    FP[Fees & Payment Context]

    Student -->|View and update profile| SM
    Admin -->|Manage student records| SM

    Student -->|Register or drop courses| CR
    Admin -->|Manage courses| CR

    Student -->|View fees and make payments| FP
    Finance -->|Manage fees and verify payments| FP

    SM -->|Student information| CR
    SM -->|Student information| FP

    CR -->|Registration information| FP
    FP -->|Payment status| Feature: Course Registration

Scenario: Student successfully registers for an available course

Given a student is logged into the university portal
And the student is eligible to register for the semester
And the course "Discrete Mathematics" is available
And the student has satisfied the course prerequisites
When the student selects "Discrete Mathematics"
And submits the course registration
Then the system should register the student for the course
And display a registration confirmation message
And add the course to the student's registered Feature: Course Registration

Scenario: Student successfully drops a registered course

Given a student is logged into the university portal
And the student is registered for "Database Systems"
And the course registration deadline has not passed
When the student requests to drop "Database Systems"
Then the system should remove the course from the student's registered courses
And update the student's registration record
And display a confirmation message
