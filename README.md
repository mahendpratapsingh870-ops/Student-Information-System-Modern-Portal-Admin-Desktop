# Student Information System

Advanced Java project with Modern Web Portal and Desktop Admin Application

## 📋 Project Overview

A comprehensive student management system with the following features:
- Student login & profile management
- Marks and attendance tracking
- Admin CRUD operations
- RESTful API endpoints
- H2 in-memory database (no setup needed)
- Clean MVC architecture

## 🛠️ Technology Stack

- **Language:** Java 17+
- **Framework:** Spring Boot 3.2.0
- **Database:** H2 (in-memory) / MySQL / PostgreSQL
- **ORM:** JPA/Hibernate
- **Build:** Maven
- **API:** REST

## 📦 Prerequisites

- Java 17 or higher installed
- Maven 3.6+ installed
- VS Code or any Java IDE

## 🚀 Quick Start

### 1. Open in VS Code

```bash
# Extract the folder and open in VS Code
code StudentInfoSystem
```

### 2. Install Required Extensions

In VS Code, install:
- **Extension Pack for Java** (Microsoft)
- **Maven for Java** (Microsoft)

### 3. Run the Application

**Option A: Using VS Code Terminal**
```bash
mvn clean install
mvn spring-boot:run
```

**Option B: Using Maven Command Line**
```bash
cd StudentInfoSystem
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

## 📡 API Endpoints

### Student Endpoints
```
POST   /api/students/register          - Register a new student
POST   /api/students/login             - Student login
GET    /api/students/{id}              - Get student profile
GET    /api/students/all               - Get all students
PUT    /api/students/{id}              - Update student
DELETE /api/students/{id}              - Deactivate student
```

### Marks Endpoints
```
POST   /api/marks/add                  - Add marks for a student
GET    /api/marks/student/{studentId}  - Get marks by student
GET    /api/marks/{marksId}            - Get specific mark record
GET    /api/marks/all                  - Get all marks
PUT    /api/marks/{marksId}            - Update marks
DELETE /api/marks/{marksId}            - Delete marks
```

### Attendance Endpoints
```
POST   /api/attendance/mark            - Mark attendance
GET    /api/attendance/student/{id}    - Get student attendance
GET    /api/attendance/{attendanceId}  - Get specific attendance
GET    /api/attendance/all             - Get all attendance
PUT    /api/attendance/{id}            - Update attendance
DELETE /api/attendance/{id}            - Delete attendance
```

### Admin Endpoints
```
POST   /api/admins/register            - Register admin
POST   /api/admins/login               - Admin login
GET    /api/admins/{id}                - Get admin details
GET    /api/admins/all                 - Get all admins
PUT    /api/admins/{id}                - Update admin
DELETE /api/admins/{id}                - Deactivate admin
```

## 💾 Database

The project uses **H2 in-memory database** by default (requires no setup).

### H2 Console Access
- URL: `http://localhost:8080/api/h2-console`
- JDBC URL: `jdbc:h2:mem:studentdb`
- Username: `sa`
- Password: (leave blank)

### Switch to MySQL (Optional)

Edit `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/student_info_system
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=your_password
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
spring.jpa.hibernate.ddl-auto=update
```

### Switch to PostgreSQL (Optional)

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/student_info_system
spring.datasource.driverClassName=org.postgresql.Driver
spring.datasource.username=postgres
spring.datasource.password=your_password
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
```

## 📝 Sample API Requests

### Register Student
```json
POST /api/students/register
Content-Type: application/json

{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "phone": "9876543210",
  "password": "password123",
  "enrollmentNumber": "STU001",
  "dateOfBirth": "2000-01-15",
  "address": "123 Main St"
}
```

### Student Login
```json
POST /api/students/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

### Add Marks
```json
POST /api/marks/add
Content-Type: application/json

{
  "studentId": 1,
  "subject": "Mathematics",
  "marksObtained": 85,
  "examDate": "2024-04-20",
  "examType": "Midterm"
}
```

### Mark Attendance
```json
POST /api/attendance/mark
Content-Type: application/json

{
  "studentId": 1,
  "attendanceDate": "2024-04-20",
  "isPresent": true,
  "remarks": "Present"
}
```

## 📁 Project Structure

```
StudentInfoSystem/
├── pom.xml                          # Maven configuration
├── .gitignore                       # Git ignore rules
├── README.md                        # This file
└── src/
    ├── main/
    │   ├── java/com/studentinfo/
    │   │   ├── StudentInfoSystemApplication.java   # Main class
    │   │   ├── controller/
    │   │   │   ├── StudentController.java
    │   │   │   ├── AdminController.java
    │   │   │   ├── MarksController.java
    │   │   │   └── AttendanceController.java
    │   │   ├── service/
    │   │   │   ├── StudentService.java
    │   │   │   ├── AdminService.java
    │   │   │   ├── MarksService.java
    │   │   │   └── AttendanceService.java
    │   │   ├── repository/
    │   │   │   ├── StudentRepository.java
    │   │   │   ├── AdminRepository.java
    │   │   │   ├── MarksRepository.java
    │   │   │   └── AttendanceRepository.java
    │   │   ├── entity/
    │   │   │   ├── Student.java
    │   │   │   ├── Admin.java
    │   │   │   ├── Marks.java
    │   │   │   └── Attendance.java
    │   │   └── dto/
    │   │       ├── StudentDTO.java
    │   │       ├── LoginDTO.java
    │   │       └── ApiResponse.java
    │   └── resources/
    │       └── application.properties        # Configuration
    └── test/
        └── java/                             # Unit tests (optional)
```

## ✨ Features Implemented

✅ Student Registration & Login
✅ Student Profile View
✅ Marks Management (Add, Update, Delete, View)
✅ Attendance Tracking (Mark, Update, Delete, View)
✅ Admin Management
✅ Input Validation
✅ Error Handling
✅ RESTful API Design
✅ MVC Architecture
✅ Database Persistence
✅ CORS Enabled

## 🔧 Development Tips

### Adding New Features

1. Create Entity class in `entity/`
2. Create Repository interface in `repository/`
3. Create Service class in `service/`
4. Create Controller in `controller/`
5. Create DTO in `dto/` if needed

### Testing API Endpoints

Use tools like:
- **Postman** - Desktop app for API testing
- **Thunder Client** - VS Code extension
- **REST Client** - VS Code extension

### Troubleshooting

**Port Already in Use:**
```bash
# Change port in application.properties
server.port=8081
```

**Build Issues:**
```bash
mvn clean install
mvn -U clean install  # Update dependencies
```

**Database Issues:**
Check `application.properties` for correct database configuration

## 📚 Additional Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Maven Documentation](https://maven.apache.org/)

## 📄 License

This project is for educational purposes.

## ✍️ Author Notes

This is a complete, production-ready project following best practices:
- Clean Code principles
- SOLID design patterns
- Proper error handling
- Input validation
- Scalable architecture

---

**Happy Coding! 🚀**
