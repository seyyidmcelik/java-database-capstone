# Smart Clinic Management System – Architecture Design

## 1. Architecture Summary
The Smart Clinic Management System follows a **three-tier architecture** that separates concerns into Presentation, Application, and Data layers.  
- The **Presentation layer** uses HTML, CSS, JavaScript, and Thymeleaf templates to provide dashboards for admins, doctors, and patients.  
- The **Application layer** is powered by Spring Boot, implementing both MVC controllers for web pages and RESTful APIs for external clients. It handles authentication with JWT, business logic, and validation.  
- The **Data layer** integrates two databases: **MySQL** (relational, managed via JPA) for structured entities such as users, doctors, patients, and appointments; and **MongoDB** (document-oriented, via Spring Data MongoDB) for flexible data like prescriptions.  

This layered design ensures scalability, modularity, and secure access while supporting both interactive dashboards and external API integrations.

---

## 2. Numbered Flow – Request/Response Cycle

1. **User Action**  
   A user (admin, doctor, or patient) interacts with the system through a web browser (Thymeleaf-based dashboard) or a REST client (API call).

2. **Frontend Request**  
   - For dashboards: the browser sends an HTTP request to the MVC controller.  
   - For APIs: the client sends a JSON payload to the REST endpoint.

3. **Spring Boot Controller**  
   - MVC controllers render Thymeleaf views.  
   - REST controllers process API requests and return JSON responses.

4. **Service Layer**  
   Business logic is executed here. Services validate inputs, enforce role-based access, and coordinate database calls.

5. **Data Access Layer**  
   - Spring Data JPA repositories handle CRUD operations on MySQL tables (users, doctors, patients, appointments).  
   - Spring Data MongoDB repositories handle prescriptions and other flexible data.

6. **Database Operations**  
   - MySQL stores relational data with relationships and constraints.  
   - MongoDB stores JSON-like prescription documents.

7. **Response Assembly**  
   The service layer collects data, applies transformations, and prepares the output.

8. **Controller Response**  
   - MVC controllers pass data to Thymeleaf templates for rendering dynamic HTML.  
   - REST controllers return JSON payloads.

9. **User View**  
   The frontend displays updated dashboards or REST clients consume the JSON, completing the cycle.

---

✅ **Deliverable:** Save this file as `schema-architecture.md` in your repository `java-database-capstone`.  
✅ **Commit message:** `"Added architecture design for Smart Clinic app"`.  
