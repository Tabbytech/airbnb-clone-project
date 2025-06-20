# airbnb-clone-project
Overview<b> <br/>
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.<br/>
Project Goals<br/>
User Management: Implement a secure system for user registration, authentication, and profile management.<br/>
Property Management: Develop features for property listing creation, updates, and retrieval.<br/>
Booking System: Create a booking mechanism for users to reserve properties and manage booking details.<br/>
Payment Processing: Integrate a payment system to handle transactions and record payment details.<br/>
Review System: Allow users to leave reviews and ratings for properties.<br/>
Data Optimization: Ensure efficient data retrieval and storage through database optimizations.<br/>

Technology Stack.<br/>
Django: A high-level Python web framework used for building the RESTful API.<br/>
Django REST Framework: Provides tools for creating and managing RESTful APIs.<br/>
PostgreSQL: A powerful relational database used for data storage.<br/>
GraphQL: Allows for flexible and efficient querying of data.<br/>
Celery: For handling asynchronous tasks such as sending notifications or processing payments.<br/>
Redis: Used for caching and session management.<br/>
Docker: Containerization tool for consistent development and deployment environments.<br/>
CI/CD Pipelines: Automated pipelines for testing and deploying code changes.<br/>

Team Roles and Responsibilities<br/>
Business analyst (BA): A business analyst dives deep into a customer’s workflows and analyzes stakeholder feedback to help a client formulate what their wants look like and align a customer’s vision with what a development team is producing. They translate an abstract product idea into a set of tangible requirements. <br/>
Product owner (PO): Holds responsibility for a product vision and evolution and Makes sure the final product meets customer requirements.<br>
Project manager (PM): Makes sure a product or its part is delivered on time and within budget and Manages and motivates the software development team.<br>
UI/UX designer: Transforms a product vision into user-friendly designs and Creates user journeys for the best user experience and highest conversion rates.<br/>
Software architect: Designs a high-level software architecture,Selects appropriate tools and platforms to implement the product vision and Sets up code quality standards and performs code reviews.<br/>
Software developer: Engineers and stabilizes the product and solves any technical problems emerging during the development lifecycle.<br>
Quality assurance (QA) engineer: Makes sure an application performs according to requirements and Spots functional and non-functional defects<br>
Test automation engineer: Designs a test automation ecosystem and Writes and maintains test scripts for automated testing.<br/>
DevOps engineer: Facilitates cooperation between development and operations teams and Builds continuous integration and continuous delivery (CI/CD) pipelines for faster delivery.<br/>

 Database Design<br>
 1. Users
Represents people using the platform.
Key fields:
user_id (Primary Key)
name
email
password_hash
role (e.g., host or guest)
Relationships:
A user can own multiple properties (if they’re a host).
A user can make multiple bookings (if they’re a guest).
A user can leave multiple reviews.
A user makes payments for bookings.

2. Properties
Listings that are available for booking.
Key fields:
property_id (Primary Key)
owner_id (Foreign Key → Users)
title
location
price_per_night
Relationships:
Each property belongs to one user (host).
A property can have multiple bookings.
A property can have multiple reviews from different guests.

3. Bookings
Reservations made by guests.
Key fields:
booking_id (Primary Key)
user_id (Foreign Key → Users)
property_id (Foreign Key → Properties)
check_in_date
check_out_date
status (e.g., confirmed, canceled)
Relationships:
Each booking is made by one user.
Each booking is for one property.
Each booking can have one associated payment.<br/>

4. Reviews<br/>
Feedback left by users about properties.
Key fields:
review_id (Primary Key)
user_id (Foreign Key → Users)
property_id (Foreign Key → Properties)
rating (e.g., 1–5)
comment
timestamp
Relationships:
A review is written by a user for a specific property.
A property can have many reviews.<br/>

5. Payments<br/>
Financial transactions tied to bookings.
Key fields:
payment_id (Primary Key)
booking_id (Foreign Key → Bookings)
user_id (Foreign Key → Users)
amount
payment_date
payment_method
Relationships:
A payment is linked to one booking.
A user makes the payment for the booking.<br/>
