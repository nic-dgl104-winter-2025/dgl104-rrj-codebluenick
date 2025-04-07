# Contribution to Smart Task Management System (STMS)

## Project Overview
This document summarizes my contributions to the **Smart Task Management System (STMS)**, a group project developed for the DGL-104 web application course.

**Project Repository:** (https://github.com/codebluenick/dgl104-appdevproj-groupWHPH.git)

## Team Information
- **Group Name:** WHPH (Work Hard, Play Hard)
- **Members:**
  - Hardik Vaghasiya
  - Varunkanth Arani Pannerselvam
  - Nikhil Chhetri

## My Contributions

### Backend Development
- Designed and implemented the backend logic using **Node.js and Express**.
- Developed RESTful API endpoints to handle CRUD operations related to tasks, users, and authentication.
- Integrated **MongoDB** for data storage, managing schemas, and handling secure database queries efficiently.
- Managed Cross-Origin Resource Sharing (**CORS**) to securely handle frontend-backend communication.
- Utilized **jsonwebtoken** for secure authentication and authorization.
- Implemented comprehensive error handling and debugging techniques to enhance application reliability.

### Frontend Integration
- Implemented functionality to fetch data from the backend APIs to the React frontend.
- Ensured seamless integration between the frontend and backend, providing a smooth user experience and making sure everything works correct.

### Design Patterns Implemented
- **Factory Pattern:** For creating and managing various types of tasks and components efficiently.
- **Observer Pattern:** For real-time notifications and updates when task statuses change.
- **Singleton Pattern:** Ensured a single instance of critical resources like database connections.
- Some other patterns such as **Decorator** and **Strategy** were implemented by Hardik.

### Development Tools & Testing
- Used **nodemon** to enhance development workflow and automatically restart the server during development.
- Created and executed unit tests with **Jest** to ensure API endpoints and server logic functioned correctly.
- Set up basic testing routines to validate task management functionalities, ensuring reliability and stability of the backend code.

### CI/CD Pipeline
- Set up **GitHub Actions** for continuous integration to run unit tests and linting on every Pull Request.
- Implemented automated deployment pipelines to deploy the application to platforms like Heroku, Netlify, or Vercel upon passing tests.

### Core Features Implemented
- User roles and permissions (Admin, Team Lead, Team Member).
- Task creation, assignment, editing, and status tracking (To Do, In Progress, Completed).
- Basic collaboration features, including comments and notifications.
- Task priority levels (High, Medium, Low) and deadline management.

## Future Enhancements
- Adding more js features to the project.
- A.I. integration

---

My contributions helped establish a robust backend and streamlined integration with the frontend, ensuring core functionalities were reliable and performant.
