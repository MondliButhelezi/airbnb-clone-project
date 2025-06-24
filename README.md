# Airbnb Clone Project

## 🏁 Project Overview
This project is a backend clone of Airbnb. It simulates a real-world booking platform where users can list, book, and review properties. The project is built to mirror production-level development practices, including API creation, database design, and CI/CD integration.

## 🎯 Project Goals
- Develop a robust backend system for a property booking platform
- Implement user management, property listings, bookings, reviews, and payments
- Use modern tools and best practices in backend development

## 🧰 Technology Stack
- **Django** – Python web framework for building the backend
- **Django REST Framework** – For RESTful API development
- **GraphQL** – Flexible querying of backend data
- **MySQL** – Relational database for storing project data
- **Docker** – Containerized development and deployment
- **GitHub Actions** – Continuous integration and testing

## 👥 Team Roles

This project simulates a collaborative development team structure. Each role is critical in building, testing, and deploying a scalable Airbnb-like backend platform.

### 🔧 Backend Developer
Responsible for implementing the core application logic, REST and GraphQL APIs, authentication systems, and feature modules like bookings, reviews, and payments.

### 🗃️ Database Administrator (DBA)
Designs and maintains the database schema, enforces data integrity, creates indexes for optimisation, and ensures data backups and security policies are in place.

### 🚀 DevOps Engineer
Sets up and maintains the infrastructure for continuous integration and delivery (CI/CD), manages containerization with Docker, and handles deployment and environment monitoring.

### 🧪 QA Engineer
Tests all backend features to ensure they meet quality and functionality standards. Creates automated test cases and conducts manual testing to catch edge-case bugs and ensure stability.

### 📑 Project Manager (Optional/Support Role)
Coordinates the work between team members, sets milestones, manages documentation, and ensures timely delivery of tasks.

## 🗃️ Database Design

This section outlines the core database structure for the Airbnb Clone project. It defines the primary entities and their relationships, which reflect real-world interactions between users, properties, bookings, payments, and reviews.

### 📌 Key Entities and Fields

---

### 👤 Users
- `id` (Primary Key): Unique identifier for each user.
- `name`: Full name of the user.
- `email`: Unique email address.
- `password_hash`: Securely stored password hash.
- `is_host`: Boolean indicating if the user is a property host.

A **User** can:
- Create multiple **Properties**.
- Make multiple **Bookings**.
- Write multiple **Reviews**.

---

### 🏠 Properties
- `id` (Primary Key): Unique identifier for each property.
- `host_id` (Foreign Key to Users): The user who owns the property.
- `title`: Title or name of the property.
- `description`: Details about the property.
- `price_per_night`: Cost of staying per night.

A **Property**:
- Belongs to one **User** (host).
- Can have many **Bookings**.
- Can receive many **Reviews**.

---

### 📅 Bookings
- `id` (Primary Key): Unique booking ID.
- `user_id` (Foreign Key to Users): The guest making the booking.
- `property_id` (Foreign Key to Properties): Property being booked.
- `check_in_date`: Start date of stay.
- `check_out_date`: End date of stay.

A **Booking**:
- Is made by one **User**.
- Belongs to one **Property**.
- May trigger a **Payment**.

---

### 💳 Payments
- `id` (Primary Key): Unique payment ID.
- `booking_id` (Foreign Key to Bookings): Booking linked to the payment.
- `amount`: Total amount charged.
- `payment_date`: Timestamp of transaction.
- `status`: Payment status (e.g., "paid", "pending").

A **Payment**:
- Is tied to one **Booking**.
- Must reflect accurate **amount** and **status**.

---

### ⭐ Reviews
- `id` (Primary Key): Unique review ID.
- `user_id` (Foreign Key to Users): The reviewer.
- `property_id` (Foreign Key to Properties): Reviewed property.
- `rating`: Numeric score (e.g., 1–5).
- `comment`: User's written feedback.

A **Review**:
- Is written by one **User**.
- Belongs to one **Property**.

---

### 🔗 Relationships Summary

- **One User → Many Properties**
- **One User → Many Bookings**
- **One User → Many Reviews**
- **One Property → Many Bookings**
- **One Property → Many Reviews**
- **One Booking → One Payment**

## ✨ Feature Breakdown

This section outlines the major features implemented in the backend of the Airbnb Clone project. Each feature is designed to support real-world functionality, contributing to a fully operational and scalable booking platform.

### 👤 User Management
Handles user registration, login, and profile management. It ensures secure authentication and allows users to manage their roles as guests or property hosts.

### 🏘️ Property Management
Enables hosts to create, update, and manage property listings. Each property includes details such as title, description, price, and availability, allowing guests to explore accommodation options.

### 📅 Booking System
Allows guests to book available properties for specific dates. It ensures no overlapping bookings and maintains check-in/check-out data for both guests and hosts.

### 💳 Payment Processing
Simulates a payment system that processes transactions related to bookings. This feature helps ensure that each booking is confirmed only after successful payment.

### ⭐ Review System
Allows guests to leave reviews and star ratings for properties they’ve stayed at. This builds trust in the platform and helps future guests make informed decisions.

### 🔐 API Security
Implements token-based authentication and secure access control to protect user data and ensure that only authorized users can access or modify sensitive information.

### 🚀 CI/CD Integration
Automates testing and deployment through CI/CD pipelines using GitHub Actions. This ensures code quality, rapid delivery, and reliable production environments.

### 🧠 Data Optimization
Utilizes indexing and caching strategies to improve performance and reduce database load. This enables fast and efficient data retrieval in high-traffic scenarios.

## 🔐 API Security

Security is a top priority in the development of the Airbnb Clone backend. The system includes several key security measures to protect user data, ensure safe transactions, and maintain the integrity of the platform.

### 🔑 Authentication
We use token-based authentication (e.g., JWT or Django Token Auth) to verify the identity of users. This prevents unauthorized access to sensitive operations such as booking, editing listings, or posting reviews.

### 👮 Authorization
Access control is enforced to ensure that only users with the correct permissions can perform specific actions. For example, only property owners can edit or delete their own listings, and users cannot access or modify others’ bookings or payments.

### ⏱️ Rate Limiting
Rate limiting is implemented to prevent abuse and brute-force attacks. It helps protect endpoints such as login and payment processing from being overwhelmed by malicious or repeated requests.

### 🧊 Password Security
User passwords are stored as secure hashes using industry-standard algorithms (e.g., PBKDF2, bcrypt). This ensures that even if the database is compromised, raw passwords are not exposed.

### 💳 Payment Protection
All payment-related data is secured through validation, encryption (if applicable), and restricted endpoint access. Although payments are simulated in this clone, proper security practices are modeled as in real-world payment systems.

### 🧯 Error Handling
Sensitive error messages are suppressed in production to avoid leaking internal logic or stack traces, which could be exploited by attackers.

### 🔍 Why Security Matters
- **User Data**: Protects personal information such as email, password, and booking history.
- **Host Properties**: Prevents unauthorized modifications or deletions of property listings.
- **Transactions**: Ensures trust by securing the booking and payment workflow.
- **Platform Integrity**: Guards against abuse, spam, and malicious attacks.

## ⚙️ CI/CD Pipeline

CI/CD (Continuous Integration and Continuous Deployment) is a development practice that automates the process of testing, building, and deploying code. It helps ensure that new changes can be integrated and released quickly, reliably, and safely.

### 🚀 Why CI/CD Matters for This Project
In the Airbnb Clone project, CI/CD ensures that all code changes are automatically tested and validated before being deployed. This reduces bugs, improves code quality, and supports rapid, collaborative development among team members. It also enforces best practices by automating key workflows such as testing, linting, and deployment.

### 🛠️ Tools Used in the CI/CD Pipeline

- **GitHub Actions**: Automates workflows like running tests, checking code quality, and deploying to a server or platform.
- **Docker**: Ensures that the application runs consistently across different environments (development, staging, production).
- **pytest / unittest**: Used for automated testing of Django views, models, and API endpoints.
- **Black & Flake8**: Code formatters and linters to maintain code quality and consistency.

A typical CI/CD workflow for this project might include:
1. Running tests on every push or pull request.
2. Linting code for styling and formatting errors.
3. Building and packaging the Docker container.
4. Optionally deploying to a cloud environment (e.g., Heroku, Railway, Render).

