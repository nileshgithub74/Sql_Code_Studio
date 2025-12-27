# SQL Editor Backend

Node.js/Express backend API for the SQL Editor application.

## 🛠️ Tech Stack

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - Assignment and user data storage
- **PostgreSQL** - SQL query execution sandbox
- **Mongoose** - MongoDB ODM
- **pg** - PostgreSQL client

## 📁 Project Structure

```
Backend/
├── controller/              # Request handlers
│   ├── assignmentController.js
│   └── sqlController.js
├── database/               # Database connections
│   ├── db.js              # MongoDB connection
│   └── postgresql.js      # PostgreSQL operations
├── models/                # Database models
│   └── assignmentModel.js
├── routes/                # API routes
│   ├── assignmentRoutes.js
│   └── sqlRoutes.js
├── services/              # Business logic
│   ├── answerValidationService.js
│   └── hintService.js
├── .env                   # Environment variables
├── .gitignore
├── package.json
└── server.js              # Main server file
```

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- MongoDB Atlas account or local MongoDB
- PostgreSQL database

### Installation

1. **Install dependencies:**
```bash
npm install
```

2. **Environment Setup:**
Create `.env` file:
```env
PORT=8080
MONGODB_URL=mongodb+srv://username:password@cluster.mongodb.net/database
PG_HOST=localhost
PG_PORT=5432
PG_DATABASE=your_database
PG_USER=your_username
PG_PASSWORD=your_password
```

3. **Start Development Server:**
```bash
npm run dev
```

4. **Start Production Server:**
```bash
npm start
```

## 📡 API Endpoints

### Assignment Management
```
GET    /api/assignment           # Get all assignments
GET    /api/assignment/:id       # Get assignment by ID
POST   /api/assignment           # Create new assignment
PUT    /api/assignment/:id       # Update assignment
DELETE /api/assignment/:id       # Delete assignment
```

### SQL Query Operations
```
POST   /api/sql/assignment/load  # Load assignment into PostgreSQL sandbox
POST   /api/sql/query/execute    # Execute SQL query
POST   /api/sql/query/validate   # Validate query results
```

## 🔧 Core Features

### 1. Assignment Management
- CRUD operations for SQL assignments
- MongoDB storage for assignment metadata
- Sample table data and expected results

### 2. SQL Execution Engine
- Dynamic PostgreSQL schema creation
- Isolated query execution environments
- Real-time query result processing

### 3. Answer Validation System
- Compares user query results with expected results
- Validates row count, column names, and data values
- Provides detailed feedback messages

### 4. Database Operations
- **MongoDB**: Stores assignments, user data
- **PostgreSQL**: Executes user SQL queries in isolated schemas

## 🏗️ Architecture

### Request Flow
```
Client Request → Express Router → Controller → Service → Database → Response
```

### Database Schema Management
```
1. User starts assignment
2. Create isolated PostgreSQL schema
3. Load sample data into schema
4. Execute user queries in isolation
5. Compare results with expected output
```

## 🔒 Security Features

- Environment variable protection
- Database connection pooling
- SQL injection prevention through parameterized queries
- CORS configuration for frontend integration



## 📊 Database Models

### Assignment Model
```javascript
{
  title: String,
  description: String,
  difficulty: String,
  question: String,
  requirements: [String],
  hints: [String],
  sampleTables: [{
    tableName: String,
    columns: [{ columnName: String, dataType: String }],
    rows: [Object]
  }],
  expectedOutput: Object,
  isActive: Boolean
}
```

## 🚀 Deployment

### Environment Variables
Ensure all required environment variables are set:
- `PORT` - Server port (default: 8080)
- `MONGODB_URL` - MongoDB connection string
- `PG_HOST`, `PG_PORT`, `PG_DATABASE`, `PG_USER`, `PG_PASSWORD` - PostgreSQL config

### Production Build
```bash
npm start
```

## 🤝 Contributing

1. Follow existing code structure
2. Add proper error handling
3. Update API documentation
4. Test all endpoints before submitting

## 📝 Scripts

- `npm start` - Start production server
- `npm run dev` - Start development server with nodemon
- `npm test` - Run tests (placeholder)

---

For frontend integration, see [Frontend README](../Frontend/README.md)
