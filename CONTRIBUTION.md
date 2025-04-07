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

**Example:** *Task creation endpoint (taskRoutes.js)*
```javascript
    router.post('/', async (req, res) => {
    try {
        const task = new Task(req.body);
        await task.save();
        res.status(201).json(task);
    } catch (err) {
        res.status(500).json({ error: 'Failed to create task' });
    }
    });
```

**Example:** *Login controller*
```javascript
    const handleLogin = async (req, res) => {
    const { name, email } = req.body;
    let user = await User.findOne({ email });

    if (!user) {
        user = new User({ name, email, role: 'teammember' });
        await user.save();
    }

    res.json({ success: true, user });
    };
```

---

### Frontend Integration
- Implemented functionality to fetch data from the backend APIs to the React frontend.
- Ensured seamless integration between the frontend and backend, providing a smooth user experience and making sure everything works correct.

**Example:** *Fetching tasks (ViewTasks.js)*
```javascript
    useEffect(() => {
    axios.get('http://localhost:3001/api/tasks')
        .then(res => setTasks(res.data))
        .catch(err => console.error("Failed to fetch tasks", err));
    }, []);
```

### Design Patterns Implemented
- **Factory Pattern:** For creating and managing various types of tasks and components efficiently.
- **Observer Pattern:** For real-time notifications and updates when task statuses change.
- **Singleton Pattern:** Ensured a single instance of critical resources like database connections.
- Some other patterns such as **Decorator** and **Strategy** were implemented by Hardik.

**Example:** *Factory pattern (userFactory.js) - short snippet*
```javascript
    class Admin {
    constructor(name, email) {
        this.name = name;
        this.email = email;
        this.role = 'admin';
    }
    }

    class UserFactory {
    createUser(role, name, email) {
        switch (role) {
        case 'admin': return new Admin(name, email);
        // other roles...
        }
    }
    }
```

**Example:** *Observer Pattern: Logs notifications where a task changes*
```javascript
    class Subject {
    constructor() {
      this.observers = [];
    }
  
    attach(observer) {
      this.observers.push(observer);
    }
  
    notify(data) {
      this.observers.forEach(observer => observer.update(data));
    }
    }   

    class NotificationObserver {
        update(data) {
        // Placeholder logic for notification
        console.log(`Notification: Task ${data.taskId} changed to ${data.status}`);
        }
    }
    
    // Create a shared subject instance
    const subject = new Subject();
    const notificationObserver = new NotificationObserver();
    subject.attach(notificationObserver);
    
    module.exports = subject;
```

**Example:** *Singleton Pattern: Ensured only one MongoDB connection using a singleton database file*
```javascript
    const dotenv = require('dotenv').config();
    const mongoose = require('mongoose');

    let instance = null;

    class Database {
    constructor() {
        // Check that only one instance of db class is created
        if (!instance) {
        console.log('Initializing new database connection.'); // will be printed only once when the instance is created
        instance = this;
        this._connect();
        }
        return instance;
    }

    _connect() {
        mongoose.connect(process.env.MONGO_URI)
        .then(() => {
        console.log("MongoDB connection successful!!!");
        })
        .catch((err) => {
        console.error("MongoDB connection error:", err);
        process.exit(1);
        });
    }
    }

    module.exports = new Database();
```

### Development Tools & Testing
- Used **nodemon** to enhance development workflow and automatically restart the server during development.
- Created and executed unit tests with **Jest** to ensure API endpoints and server logic functioned correctly.
- Set up basic testing routines to validate task management functionalities, ensuring reliability and stability of the backend code.

```javascript
    test('should create a new task', async () => {
    const res = await request(app).post('/api/tasks').send({
        title: "Test Task", priority: "Medium"
    });
    expect(res.statusCode).toEqual(201);
    });
```

### CI/CD Pipeline
- Set up **GitHub Actions** for continuous integration to run unit tests and linting on every Pull Request.

**Example:** *(.github/workflows/node.yml)*
```yaml
    jobs:
    test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm install
      - run: npm test
```

### Core Features Implemented
- User roles and permissions (Admin, Team Lead, Team Member).
- Task creation, assignment, editing, and status tracking (To Do, In Progress, Completed).
- Basic collaboration features, including comments and notifications.
- Task priority levels (High, Medium, Low) and deadline management.

**Example:** *Redirect by role*
```javascript
    switch (role) {
    case 'admin': return <Navigate to="/admin" />;
    case 'teamlead': return <Navigate to="/team-lead" />;
    }
```

## Future Enhancements
- Adding more js features to the project.
- A.I. integration

---

My contributions helped establish a robust backend and streamlined integration with the frontend, ensuring core functionalities were reliable and performant.
