# Smart Meal Selection with Secure Verification

## Objective:
This project is a Java-based console application that allows hostel students to securely book a special meal token for their mess. The system ensures:

- User authentication before booking a meal.
- Each student can book only one meal per day to prevent duplicate bookings.
- The meal cost (₹80.0) is automatically added to the student's mess bill.

## Tech Stack Used:
- **Java** (for core application logic)
- **JDBC** (Java Database Connectivity for database operations)
- **MySQL** (for storing student and meal booking details)

## Features and Workflow:
### Secure User Verification:
- The system prompts the user to enter their email and password.
- It checks the `students` table to validate the credentials.

### Meal Selection and Booking:
- After successful login, the system verifies if the student has already booked a meal for the day.
- If eligible, a new meal booking entry is created in the `tokens` table, storing:
  - The student’s ID (retrieved using their email)
  - The current date (to ensure a single booking per day)
  - The meal charge (₹80.0) added to their bill

### Prevention of Duplicate Bookings:
- If a student has already booked a meal, the system restricts multiple bookings for the same day.

## Database Schema:
### 1. `students` Table:
Stores student details.

| Column Name  | Data Type      | Description            |
|-------------|--------------|------------------------|
| id          | INT (Primary Key) | Unique Student ID    |
| name        | VARCHAR(100)  | Student's Name        |
| emailid     | VARCHAR(100)  | Student's Email (Unique) |
| password    | VARCHAR(100)  | Encrypted Password    |

### 2. `tokens` Table:
Stores meal booking records.

| Column Name | Data Type  | Description               |
|------------|----------|---------------------------|
| token_id   | INT (Primary Key) | Unique Token ID    |
| student_id | INT (Foreign Key) | Refers to `students.id` |
| date       | DATE     | Date of Booking          |
| amount     | FLOAT    | Amount Charged (₹80.0)   |

## Main Functionalities in Code:
### `verifyUser(email, password)`
- Validates the entered email and password against records in the `students` table.

### `canBookToken(email)`
- Checks whether the student has already booked a meal for the current date.

### `addToken(email)`
- If eligible, inserts a new meal booking record into the `tokens` table and adds the charge to their bill.

## Potential Enhancements:
✅ Implement a GUI-based interface using Swing or JavaFX.
✅ Use password encryption for better security.
✅ Provide custom meal options instead of a fixed meal price.
✅ Send email/SMS confirmations upon successful booking.
✅ Generate monthly meal usage reports for students.

This project enhances hostel mess management by ensuring secure verification and smart meal booking, making the process efficient and user-friendly. 🚀

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

