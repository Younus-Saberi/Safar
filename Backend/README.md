# Safar App Database Schema 🚍🛣️

This document outlines the database schema and relationships used in the Safar App, built using Spring Boot. The app manages users, bus reservations, routes, and feedback. Let's dive into how the tables are linked up! 🌟

## Database Tables and Relationships 🛠️

### 1. **User Table 👤**
- **Fields**:
    - `userID` (Primary Key)
    - `firstName`, `lastName`, `mobile`, `email`, `password`

- **Relationships**:
    - One-to-Many with **Reservation** (A user can have multiple reservations)
    - One-to-Many with **Feedback** (A user can leave multiple feedback entries)

### 2. **Reservation Table 🎫**
- **Fields**:
    - `reservationID` (Primary Key)
    - `status`, `date`, `time`, `source`, `destination`, `journeyDate`, `bookedSeat`, `fare`

- **Relationships**:
    - Many-to-One with **User** (Each reservation is linked to a single user)
    - Many-to-One with **Bus** (Each reservation is linked to a specific bus)

### 3. **Bus Table 🚌**
- **Fields**:
    - `busID` (Primary Key)
    - `busName`, `driverName`, `busType`, `routeFrom`, `routeTo`, `busJourneyDate`, `arrivalTime`, `departureTime`, `seats`, `availableSeats`, `fare`

- **Relationships**:
    - Many-to-One with **Route** (Multiple buses can follow the same route)
    - One-to-Many with **Reservation** (A bus can have multiple reservations)
    - One-to-One with **Feedback** (Each bus can receive one feedback per user)

### 4. **Route Table 🛤️**
- **Fields**:
    - `routeID` (Primary Key)
    - `routeFrom`, `routeTo`, `distance`

- **Relationships**:
    - One-to-Many with **Bus** (A route can be used by multiple buses)

### 5. **Feedback Table 💬**
- **Fields**:
    - `feedbackID` (Primary Key)
    - `driverRating`, `serviceRating`, `overallRating`, `comments`, `feedbackDateTime`

- **Relationships**:
    - One-to-One with **User** (Each feedback is linked to one user)
    - One-to-One with **Bus** (Each feedback is linked to a specific bus)

## Schema Visualization 🗺️

- **User ⇔ Reservation**: A user can have multiple reservations, but each reservation belongs to a single user.
- **Reservation ⇔ Bus**: Each reservation is linked to one bus, and each bus can have multiple reservations.
- **Bus ⇔ Route**: A route can have multiple buses running on it.
- **Feedback ⇔ User & Bus**: Feedback connects a user to a specific bus journey.

## Future Improvements
Add more validation and security checks for critical fields like passwords.
Enhance the relationship between Reservation and Feedback for better user experience and data integrity.

## Conclusion 🎉
This database schema covers all the core entities involved in managing users, buses, reservations, routes, and feedback. With these mappings, the system ensures a well-structured flow of data and relationships across different entities. Happy coding! 🤓

