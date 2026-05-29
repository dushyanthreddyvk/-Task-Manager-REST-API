# Task Manager REST API

[![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=flat-square&logo=java)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.5-6DB33F?style=flat-square&logo=spring-boot)](https://spring.io/projects/spring-boot)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?style=flat-square&logo=mysql)](https://www.mysql.com/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=flat-square&logo=docker)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=flat-square&logo=github-actions)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 📋 Project Overview

**Task Manager REST API** is a production-grade backend application that provides comprehensive task management capabilities through a well-designed RESTful API. Built with **Spring Boot 3.1.5**, this project demonstrates modern enterprise-level backend engineering practices, including layered architecture, dependency injection, JPA/Hibernate ORM, and containerization.

### Why Task Management Systems?

Task management systems are fundamental to organizational efficiency and project delivery. They provide:
- **Centralized task tracking** across teams and projects
- **Improved productivity** through organized workflows
- **Accountability** via assignment and status tracking
- **Scalability** for growing teams and complexity

### Backend Engineering Concepts

This project showcases key backend engineering principles:
- **RESTful API Design**: Proper HTTP methods, status codes, and resource-oriented endpoints
- **Layered Architecture**: Clean separation of concerns (Controller → Service → Repository)
- **Object-Relational Mapping**: Efficient database interaction using Spring Data JPA and Hibernate
- **Data Transfer Objects (DTOs)**: Decoupling API contracts from internal entities
- **Global Exception Handling**: Centralized error management and consistent error responses
- **Validation**: Input validation using Jakarta Bean Validation
- **Containerization**: Docker support for consistent deployment across environments
- **CI/CD Integration**: Automated testing and deployment workflows with GitHub Actions

---

## ✨ Features

### Core Functionality
- ✅ **Create Task** - Add new tasks with title, description, priority, and due date
- ✅ **View All Tasks** - Retrieve all tasks with comprehensive filtering
- ✅ **View Task by ID** - Fetch specific task details
- ✅ **Update Task** - Modify task attributes dynamically
- ✅ **Delete Task** - Remove completed or obsolete tasks
- ✅ **Mark as Completed** - Change task status to completed

### Advanced Features
- 📊 **Task Priority Support** - LOW, MEDIUM, HIGH priority levels
- 📅 **Due Date Management** - Track task deadlines
- ✔️ **Task Status Tracking** - TODO, IN_PROGRESS, COMPLETED states
- 🔍 **Input Validation** - Comprehensive validation with descriptive error messages
- 🛡️ **Exception Handling** - Global error handling with custom exception classes
- 🐳 **Docker Support** - Containerized deployment with Docker and Docker Compose
- 🚀 **CI/CD Pipeline** - Automated build, test, and deployment workflows
- 📝 **API Documentation** - Swagger UI and OpenAPI integration
- ⚙️ **Hibernate Auto Schema Management** - Automatic database table creation

---

## 🛠️ Tech Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Language** | Java | 17+ |
| **Framework** | Spring Boot | 3.1.5 |
| **ORM** | Spring Data JPA / Hibernate | 6.2.13 |
| **Database** | MySQL | 8.0+ / H2 (In-Memory) |
| **Build Tool** | Maven | 3.9.15+ |
| **Containerization** | Docker | Latest |
| **CI/CD** | GitHub Actions | Native |
| **API Documentation** | Springdoc OpenAPI | 2.0+ |
| **Validation** | Jakarta Bean Validation | 3.0+ |

---

## 🏗️ Project Architecture

The application follows a **layered architecture pattern** ensuring clear separation of concerns and maintainability:

```
┌─────────────────────────────────────────────────┐
│         REST API Client (Postman/Browser)       │
└──────────────────┬──────────────────────────────┘
                   │ HTTP Request
                   ▼
┌─────────────────────────────────────────────────┐
│      Controller Layer (REST Endpoints)          │
│   • TaskController - Handles HTTP requests      │
└──────────────────┬──────────────────────────────┘
                   │ Business Logic Call
                   ▼
┌─────────────────────────────────────────────────┐
│       Service Layer (Business Logic)            │
│   • TaskService - Core business logic           │
│   • TaskServiceImpl - Implementation             │
└──────────────────┬──────────────────────────────┘
                   │ Data Access Call
                   ▼
┌─────────────────────────────────────────────────┐
│  Repository Layer (Data Persistence)            │
│   • TaskRepository - JPA Repository interface   │
└──────────────────┬──────────────────────────────┘
                   │ SQL Query
                   ▼
┌─────────────────────────────────────────────────┐
│    Database Layer (MySQL/H2)                    │
│   • tasks table with all task records           │
└─────────────────────────────────────────────────┘
```

### Layer Responsibilities

- **Controller**: Receives HTTP requests, validates input, delegates to service
- **Service**: Implements business logic, transaction management, data transformation
- **Repository**: Abstracts database operations, provides CRUD operations
- **Entity**: Domain model representing database tables
- **DTO**: Data Transfer Objects for API contracts

---

## 📁 Project Structure

```
task-manager-api/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/taskmanager/
│   │   │       ├── TaskManagerApplication.java          # Spring Boot entry point
│   │   │       ├── controller/
│   │   │       │   └── TaskController.java              # REST endpoints
│   │   │       ├── service/
│   │   │       │   ├── TaskService.java                 # Service interface
│   │   │       │   └── TaskServiceImpl.java              # Service implementation
│   │   │       ├── repository/
│   │   │       │   └── TaskRepository.java              # JPA repository
│   │   │       ├── entity/
│   │   │       │   ├── Task.java                        # Task entity
│   │   │       │   ├── TaskStatus.java                  # Status enum
│   │   │       │   └── TaskPriority.java                # Priority enum
│   │   │       ├── dto/
│   │   │       │   ├── TaskRequestDTO.java              # Request DTO
│   │   │       │   ├── TaskResponseDTO.java             # Response DTO
│   │   │       │   └── ApiResponse.java                 # Generic response wrapper
│   │   │       ├── exception/
│   │   │       │   ├── GlobalExceptionHandler.java      # Exception handler
│   │   │       │   ├── TaskNotFoundException.java       # Custom exception
│   │   │       │   └── InvalidTaskException.java        # Custom exception
│   │   │       └── config/                              # Configuration classes
│   │   └── resources/
│   │       ├── application.properties                   # Application configuration
│   │       └── static/
│   │           └── index.html                           # Frontend (if exists)
│   └── test/
│       ├── java/com/taskmanager/                        # Unit tests
│       └── resources/
│           └── application-test.properties              # Test configuration
├── pom.xml                                               # Maven dependencies
├── Dockerfile                                            # Docker image definition
├── docker-compose.yml                                   # Docker Compose setup
├── .github/
│   └── workflows/
│       └── ci-cd.yml                                    # GitHub Actions workflow
├── API_REFERENCE.md                                      # API documentation
├── README.md                                             # This file
├── LICENSE                                               # MIT License
└── .gitignore                                            # Git ignore rules
```

---

## 🔌 REST API Endpoints

### Base URL
```
http://localhost:8080/api/tasks
```

| Method | Endpoint | Description | Status Code |
|--------|----------|-------------|-------------|
| `POST` | `/api/tasks` | Create a new task | 201 Created |
| `GET` | `/api/tasks` | Retrieve all tasks | 200 OK |
| `GET` | `/api/tasks/{id}` | Get task by ID | 200 OK |
| `PUT` | `/api/tasks/{id}` | Update an existing task | 200 OK |
| `DELETE` | `/api/tasks/{id}` | Delete a task | 200 OK |
| `PUT` | `/api/tasks/{id}/complete` | Mark task as completed | 200 OK |
| `GET` | `/api/tasks/status/completed` | Get all completed tasks | 200 OK |

---

## 💾 Database Schema

### Tasks Table

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| `id` | BIGINT | PRIMARY KEY, AUTO_INCREMENT | Unique task identifier |
| `title` | VARCHAR(255) | NOT NULL | Task title/name |
| `description` | TEXT | NULLABLE | Detailed task description |
| `status` | VARCHAR(50) | NOT NULL, ENUM | Task status (TODO, IN_PROGRESS, COMPLETED) |
| `priority` | VARCHAR(50) | NOT NULL, ENUM | Priority level (LOW, MEDIUM, HIGH) |
| `due_date` | DATE | NULLABLE | Task deadline |
| `created_at` | TIMESTAMP | NOT NULL | Creation timestamp |
| `updated_at` | TIMESTAMP | NOT NULL | Last update timestamp |

### SQL Definition
```sql
CREATE TABLE tasks (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    status VARCHAR(50) NOT NULL CHECK (status IN ('TODO', 'IN_PROGRESS', 'COMPLETED')),
    priority VARCHAR(50) NOT NULL CHECK (priority IN ('LOW', 'MEDIUM', 'HIGH')),
    due_date DATE,
    created_at TIMESTAMP NOT NULL,
    updated_at TIMESTAMP NOT NULL
);
```

---

## 🚀 How to Run the Project

### Prerequisites
- **Java 17+** installed
- **Maven 3.9.15+** installed
- **MySQL 8.0+** (optional - H2 in-memory database included)
- **Docker** (optional - for containerized deployment)

### Option 1: Direct Execution

#### 1. Clone the Repository
```bash
git clone https://github.com/dushyanthreddyvk/-Task-Manager-REST-API.git
cd task-manager-api
```

#### 2. Build the Project
```bash
mvn clean install -DskipTests
```

#### 3. Run Spring Boot Application
```bash
mvn spring-boot:run
```

Or build and run the JAR directly:
```bash
mvn clean package -DskipTests
java -jar target/task-manager-api-1.0.0.jar
```

#### 4. Access the Application
- **API Base URL**: `http://localhost:8080/api/tasks`
- **API Documentation**: `http://localhost:8080/swagger-ui.html`
- **Welcome Page**: `http://localhost:8080/`

### Option 2: Using Docker

#### 1. Build Docker Image
```bash
docker build -t task-manager-api:latest .
```

#### 2. Run Docker Container
```bash
docker run -p 8080:8080 \
  -e SPRING_DATASOURCE_URL=jdbc:mysql://host.docker.internal:3306/task_manager_db \
  -e SPRING_DATASOURCE_USERNAME=root \
  -e SPRING_DATASOURCE_PASSWORD=root \
  task-manager-api:latest
```

### Option 3: Using Docker Compose

#### 1. Start Services
```bash
docker-compose up --build
```

This will start:
- Spring Boot Application on `http://localhost:8080`
- MySQL Database on `localhost:3306`

#### 2. View Logs
```bash
docker-compose logs -f app
```

#### 3. Stop Services
```bash
docker-compose down
```

---

## 🗄️ MySQL Setup

### 1. Create Database

```sql
CREATE DATABASE task_manager_db;
USE task_manager_db;
```

### 2. Configure Application

Update `src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=8080

# MySQL Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/task_manager_db
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate Configuration
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=false

# Connection Pool
spring.datasource.hikari.maximum-pool-size=10
spring.datasource.hikari.minimum-idle=5

# Logging
logging.level.root=INFO
logging.level.com.taskmanager=DEBUG
```

### 3. Start MySQL Server

**macOS (Homebrew):**
```bash
brew services start mysql
```

**Linux (systemctl):**
```bash
sudo systemctl start mysql
```

**Docker:**
```bash
docker run -p 3306:3306 \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=task_manager_db \
  mysql:8.0
```

---

## 🐳 Docker Setup

### Dockerfile

The project includes a production-ready `Dockerfile`:

```dockerfile
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY target/task-manager-api-1.0.0.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
EXPOSE 8080
```

### Docker Compose Configuration

The `docker-compose.yml` orchestrates the application and database:

```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "8080:8080"
    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://mysql:3306/task_manager_db
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: root
    depends_on:
      - mysql
    networks:
      - app-network

  mysql:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: task_manager_db
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql
    networks:
      - app-network

volumes:
  mysql_data:

networks:
  app-network:
```

---

## 🔄 GitHub Actions / CI-CD Pipeline

### GitHub Actions Workflow

The project includes an automated CI/CD pipeline (`.github/workflows/ci-cd.yml`):

```yaml
name: Build and Deploy

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'adopt'
      
      - name: Build with Maven
        run: mvn clean package -DskipTests
      
      - name: Run Tests
        run: mvn test
      
      - name: Build Docker Image
        run: docker build -t task-manager-api:latest .
```

### Workflow Stages

1. **Build**: Compiles source code and runs Maven build
2. **Test**: Executes unit and integration tests
3. **Package**: Creates JAR and Docker image
4. **Deploy**: (Optional) Deploy to cloud platform

### Benefits

- ✅ Automated testing on every push
- ✅ Consistent build environment
- ✅ Early bug detection
- ✅ Code quality assurance
- ✅ Streamlined deployment process

---

## 🧪 API Testing

### Using cURL

#### Create a Task
```bash
curl -X POST http://localhost:8080/api/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Complete Project Documentation",
    "description": "Write comprehensive README and API documentation",
    "status": "IN_PROGRESS",
    "priority": "HIGH",
    "dueDate": "2026-06-15"
  }'
```

#### Get All Tasks
```bash
curl http://localhost:8080/api/tasks
```

#### Get Task by ID
```bash
curl http://localhost:8080/api/tasks/1
```

#### Update Task
```bash
curl -X PUT http://localhost:8080/api/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Updated Task Title",
    "description": "Updated description",
    "status": "COMPLETED",
    "priority": "MEDIUM"
  }'
```

#### Mark Task as Completed
```bash
curl -X PUT http://localhost:8080/api/tasks/1/complete
```

#### Delete Task
```bash
curl -X DELETE http://localhost:8080/api/tasks/1
```

### Using Postman

1. **Import Collection**: Create a Postman collection with the endpoints
2. **Set Environment Variables**: Configure base URL and headers
3. **Test Requests**: Execute requests with sample data

#### Sample JSON Request
```json
{
  "title": "Implement Authentication",
  "description": "Add JWT authentication to secure API endpoints",
  "status": "TODO",
  "priority": "HIGH",
  "dueDate": "2026-06-30"
}
```

#### Sample Response
```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "id": 1,
    "title": "Implement Authentication",
    "description": "Add JWT authentication to secure API endpoints",
    "status": "TODO",
    "priority": "HIGH",
    "dueDate": "2026-06-30",
    "createdAt": "2026-05-29T16:53:14",
    "updatedAt": "2026-05-29T16:53:14"
  },
  "timestamp": "2026-05-29T16:53:14"
}
```

### Using Swagger UI

1. Start the application
2. Navigate to `http://localhost:8080/swagger-ui.html`
3. Explore and test all endpoints interactively
4. View detailed request/response schemas

---

## 📚 Concepts Covered

This project demonstrates proficiency in key backend engineering concepts:

### Architecture & Design Patterns
- 🏗️ **Layered Architecture**: Separation of concerns across layers
- 🔄 **Repository Pattern**: Data access abstraction
- 🎯 **Dependency Injection**: Loose coupling via Spring IoC
- 📦 **Data Transfer Objects (DTO)**: API contract decoupling
- 🛡️ **Global Exception Handling**: Centralized error management

### Spring Ecosystem
- 🌱 **Spring Boot**: Rapid application development
- 🔗 **Spring Data JPA**: Simplified data access layer
- 🎛️ **Spring MVC**: Request handling and routing
- ⚙️ **Spring Configuration**: Bean management and configuration

### Database Technologies
- 🗄️ **ORM with Hibernate**: Object-relational mapping
- 💾 **JPA (Java Persistence API)**: Standard ORM specification
- 🔑 **ACID Transactions**: Data integrity and consistency
- 📊 **SQL & Database Design**: Schema design and optimization

### API Design
- 🔌 **REST Principles**: Resource-oriented architecture
- 📝 **HTTP Methods**: GET, POST, PUT, DELETE semantics
- 🎯 **Status Codes**: Appropriate HTTP response codes
- 📋 **JSON Serialization**: Request/response formatting

### Development Practices
- ✅ **Input Validation**: Data integrity checks
- 🔍 **Logging & Monitoring**: Application visibility
- 🧪 **Unit Testing**: Code reliability
- 📦 **Build Tools**: Maven for dependency management
- 🐳 **Containerization**: Docker for consistency
- 🔄 **CI/CD Pipelines**: Automated deployment workflows

### Enterprise Features
- 🔐 **Security**: Input sanitization and validation
- 📈 **Scalability**: Connection pooling and optimization
- 🎛️ **Configuration Management**: Environment-specific settings
- 📊 **Monitoring**: Performance tracking and logging

---

## 🚀 Future Improvements

### Security Enhancements
- 🔐 **JWT Authentication**: Stateless authentication with tokens
- 👥 **Role-Based Access Control (RBAC)**: User roles and permissions
- 🔒 **OAuth2 Integration**: Third-party authentication support
- 🛡️ **CORS Configuration**: Cross-origin request handling

### Performance Optimization
- ⚡ **Redis Caching**: In-memory caching for frequently accessed data
- 🔍 **Database Indexing**: Optimized query performance
- 📄 **Pagination**: Efficient large dataset handling
- 🔄 **Query Optimization**: Lazy/eager loading strategies

### API Enhancements
- 📖 **Swagger/OpenAPI**: Interactive API documentation
- 🔍 **Advanced Filtering**: Search and filter tasks
- 📊 **Task Analytics**: Statistics and insights
- 📧 **Email Notifications**: Task reminders and updates

### Data Management
- 🗂️ **User Profiles**: Multi-user task management
- 👥 **Team Collaboration**: Shared tasks and projects
- 📅 **Recurring Tasks**: Automated task generation
- 📎 **Task Dependencies**: Task relationship management

### Infrastructure
- ☁️ **Cloud Deployment**: AWS/Azure integration
- 📊 **Monitoring & Logging**: ELK stack or similar
- 🚀 **Kubernetes**: Container orchestration
- 🔄 **Message Queues**: Async task processing

---

## 📸 Screenshots

### Home Page
```
[Add screenshot of home page here - placeholder for future image]
```

### Create Task API
```
[Add screenshot of POST /api/tasks request/response - placeholder for future image]
```

### Get All Tasks API
```
[Add screenshot of GET /api/tasks response - placeholder for future image]
```

### Get Task by ID
```
[Add screenshot of GET /api/tasks/{id} response - placeholder for future image]
```

### Update Task API
```
[Add screenshot of PUT /api/tasks/{id} request/response - placeholder for future image]
```

### Delete Task API
```
[Add screenshot of DELETE /api/tasks/{id} response - placeholder for future image]
```

### Swagger UI Documentation
```
[Add screenshot of Swagger UI interface - placeholder for future image]
```

### Docker Container Running
```
[Add screenshot of Docker container logs - placeholder for future image]
```

### Docker Compose Setup
```
[Add screenshot of docker-compose logs - placeholder for future image]
```

### GitHub Actions Workflow
```
[Add screenshot of GitHub Actions CI/CD workflow - placeholder for future image]
```

### MySQL Database Schema
```
[Add screenshot of database structure - placeholder for future image]
```

### Frontend UI (if applicable)
```
[Add screenshot of task management interface - placeholder for future image]
```

---

## 📖 Conclusion

The **Task Manager REST API** is a comprehensive demonstration of modern backend engineering practices and enterprise-level software development. This project showcases:

- **Clean Architecture**: Well-organized, maintainable codebase following SOLID principles
- **Production-Ready Code**: Professional standards for scalability and reliability
- **Modern Tech Stack**: Latest versions of Spring Boot and industry-standard tools
- **DevOps Integration**: Containerization and CI/CD automation
- **Best Practices**: Input validation, exception handling, and security considerations

### Key Takeaways

1. **RESTful API Design**: Implemented proper REST principles with appropriate HTTP methods and status codes
2. **Layered Architecture**: Clear separation between controllers, services, and repositories
3. **Data Management**: Efficient database operations using JPA and Hibernate
4. **Error Handling**: Global exception handling with meaningful error messages
5. **Docker & DevOps**: Containerized deployment ready for production environments
6. **CI/CD Pipeline**: Automated build and testing workflows for reliability

### Learning Path

This project is ideal for developers looking to understand:
- How to build scalable REST APIs
- Spring Boot framework best practices
- Database design and ORM concepts
- Docker containerization
- CI/CD pipeline implementation

### Use Cases

- **Portfolio Project**: Demonstrate backend engineering skills to employers
- **Learning Resource**: Understand enterprise Java development patterns
- **Template Project**: Starting point for task management systems
- **Interview Preparation**: Technical foundation for backend engineering roles

---

## 📞 Support & Contributions

### Getting Help

- **Issues**: Report bugs or request features via GitHub Issues
- **Documentation**: Refer to [API_REFERENCE.md](API_REFERENCE.md) for detailed API documentation
- **Spring Boot Docs**: https://spring.io/projects/spring-boot

### Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### MIT License Summary
- ✅ Commercial use permitted
- ✅ Modification permitted
- ✅ Distribution permitted
- ✅ Private use permitted
- ⚠️ Liability not assumed
- ⚠️ Warranty not provided

---

## 👨‍💻 Author

**VK Dushyanth Reddy**

- GitHub: [@dushyanthreddyvk](https://github.com/dushyanthreddyvk)
- Repository: [Task-Manager-REST-API](https://github.com/dushyanthreddyvk/-Task-Manager-REST-API)

---

## 🙏 Acknowledgments

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Hibernate ORM](https://hibernate.org/)
- [Docker](https://www.docker.com/)
- [GitHub Actions](https://github.com/features/actions)

---

**Last Updated**: May 29, 2026
**Project Status**: ✅ Production Ready

---

*For questions, suggestions, or collaboration inquiries, feel free to reach out or open an issue on GitHub.*
