# CipherSQL Studio - Backend API

Node.js Express backend with MongoDB user authentication and PostgreSQL query execution.

## 🚀 Features

### Authentication System
- **JWT-based Authentication** with secure token generation
- **User Registration & Login** with email validation
- **Password Hashing** using bcryptjs (salt rounds = 12)
- **Protected Routes** with authentication middleware
- **User Management** with MongoDB storage

### SQL Execution Engine
- **PostgreSQL Integration** for real-time query execution
- **Assignment Management** with CRUD operations
- **Answer Validation** with intelligent feedback
- **Hint System** for guided learning
- **Schema Management** for database visualization

### API Architecture
- **RESTful Design** with proper HTTP methods
- **Error Handling** with consistent response format
- **Input Validation** for security and data integrity
- **CORS Configuration** for cross-origin requests
- **Environment-based Configuration** for different deployments

## 📁 Project Structure

```
Backend/
├── controller/              # Route controllers
│   ├── authController.js   # Authentication logic
│   ├── assignmentController.js # Assignment management
│   └── sqlController.js    # SQL execution logic
├── middleware/              # Custom middleware
│   └── authMiddleware.js   # JWT authentication
├── models/                  # MongoDB schemas
│   ├── userModel.js        # User schema
│   └── assignmentModel.js  # Assignment schema
├── routes/                  # API routes
│   ├── authRoutes.js       # Authentication endpoints
│   ├── assignmentRoutes.js # Assignment endpoints
│   └── sqlRoutes.js        # SQL execution endpoints
├── services/                # Business logic
│   ├── authService.js      # Authentication services
│   ├── answerValidationService.js # Answer validation
│   └── hintService.js      # Hint generation
├── database/                # Database connections
│   ├── db.js              # MongoDB connection
│   └── postgresql.js      # PostgreSQL connection
├── .env                     # Environment variables
├── server.js               # Application entry point
└── package.json            # Dependencies and scripts
```

## 🛠️ Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB Atlas account or local MongoDB
- PostgreSQL database
- npm package manager

### Setup Steps

1. **Install Dependencies:**
   ```bash
   npm install
   ```

2. **Environment Configuration:**
   Create `.env` file:
   ```env
   PORT=8080
   MONGODB_URL=mongodb+srv://username:password@cluster.mongodb.net/sqlEditor
   JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
   JWT_EXPIRE=7d
   
   # PostgreSQL Configuration
   PG_HOST=localhost
   PG_PORT=5432
   PG_DATABASE=ciphersqlstudio_app
   PG_USER=postgres
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

## 🔗 API Endpoints

### Authentication Routes (`/api/auth`)

#### POST `/api/auth/register`
Register a new user account.

**Request Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "user": {
      "id": "user_id",
      "name": "John Doe",
      "email": "john@example.com"
    },
    "token": "jwt_token_here"
  }
}
```

#### POST `/api/auth/login`
Authenticate user and return JWT token.

**Request Body:**
```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "user": {
      "id": "user_id",
      "name": "John Doe",
      "email": "john@example.com"
    },
    "token": "jwt_token_here"
  }
}
```

#### GET `/api/auth/me` (Protected)
Get current authenticated user information.

**Headers:**
```
Authorization: Bearer jwt_token_here
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "user_id",
      "name": "John Doe",
      "email": "john@example.com",
      "createdAt": "2024-12-28T..."
    }
  }
}
```

### Assignment Routes (`/api/assignment`)

#### GET `/api/assignment`
Get all active assignments.

**Response:**
```json
{
  "success": true,
  "allAssignment": [
    {
      "id": "assignment_id",
      "title": "Basic SELECT Queries",
      "description": "Learn fundamental SELECT operations",
      "difficulty": "Easy",
      "question": "Write a query to select all users",
      "requirements": ["Use SELECT statement", "Include all columns"],
      "hints": ["Start with SELECT *", "FROM users table"]
    }
  ]
}
```

#### GET `/api/assignment/:id`
Get specific assignment by ID.

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "assignment_id",
    "title": "Basic SELECT Queries",
    "description": "Learn fundamental SELECT operations",
    "difficulty": "Easy",
    "question": "Write a query to select all users",
    "sampleTables": [
      {
        "tableName": "users",
        "columns": [
          {"columnName": "id", "dataType": "INTEGER"},
          {"columnName": "name", "dataType": "VARCHAR"}
        ],
        "rows": [
          {"id": 1, "name": "John"},
          {"id": 2, "name": "Jane"}
        ]
      }
    ]
  }
}
```

### SQL Execution Routes (`/api/sql`)

#### POST `/api/sql/execute`
Execute SQL query against PostgreSQL database.

**Request Body:**
```json
{
  "query": "SELECT * FROM users;",
  "assignmentId": "assignment_id"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "results": [
      {"id": 1, "name": "John"},
      {"id": 2, "name": "Jane"}
    ],
    "executionTime": "15ms",
    "rowCount": 2
  }
}
```

## 🔐 Security Features

### Password Security
- **bcryptjs Hashing**: Salt rounds = 12 for strong password protection
- **Password Validation**: Minimum 6 characters required
- **No Plain Text Storage**: Passwords never stored in plain text

### JWT Authentication
- **Secure Token Generation**: Using strong secret keys
- **Token Expiration**: Configurable expiry (default 7 days)
- **Protected Routes**: Middleware validates tokens automatically

### Input Validation
- **Email Validation**: Using validator.js for proper email format
- **SQL Injection Protection**: Parameterized queries only
- **Request Sanitization**: Clean input data before processing

### Database Security
- **Connection Encryption**: Secure MongoDB and PostgreSQL connections
- **Environment Variables**: Sensitive data stored securely
- **Unique Constraints**: Prevent duplicate user registrations

## 🗄️ Database Schema

### User Model (MongoDB)
```javascript
{
  name: String (required, 2-50 chars),
  email: String (required, unique, validated),
  password: String (required, hashed, min 6 chars),
  createdAt: Date (auto-generated),
  updatedAt: Date (auto-generated)
}
```

### Assignment Model (MongoDB)
```javascript
{
  title: String (required),
  description: String (required),
  difficulty: String (Easy/Medium/Hard),
  question: String (required),
  requirements: [String],
  hints: [String],
  sampleTables: [{
    tableName: String,
    columns: [{columnName: String, dataType: String}],
    rows: [Mixed]
  }],
  expectedOutput: Object,
  isActive: Boolean (default: true)
}
```

## 🚀 Deployment

### Environment Setup
```env
NODE_ENV=production
PORT=8080
MONGODB_URL=your_production_mongodb_url
JWT_SECRET=your_production_jwt_secret
PG_HOST=your_production_pg_host
PG_DATABASE=your_production_database
```

### Build Commands
```bash
# Install dependencies
npm install

# Start production server
npm start

# Development with auto-reload
npm run dev
```

### Deployment Platforms
- **Heroku**: Easy deployment with MongoDB Atlas
- **Railway**: Modern deployment platform
- **DigitalOcean**: VPS deployment option
- **AWS/GCP**: Cloud platform deployment

## 🧪 Testing

### Manual Testing
```bash
# Test authentication
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","password":"password123"}'

# Test protected route
curl -X GET http://localhost:8080/api/auth/me \
  -H "Authorization: Bearer your_jwt_token"
```

## 📝 Error Handling

### Standard Error Response
```json
{
  "success": false,
  "message": "Error description",
  "error": "Detailed error information (development only)"
}
```

### Common HTTP Status Codes
- `200` - Success
- `201` - Created (registration)
- `400` - Bad Request (validation errors)
- `401` - Unauthorized (invalid credentials)
- `404` - Not Found
- `500` - Internal Server Error

## 🔧 Configuration

### Environment Variables
| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | 8080 |
| `MONGODB_URL` | MongoDB connection string | Required |
| `JWT_SECRET` | JWT signing secret | Required |
| `JWT_EXPIRE` | Token expiration time | 7d |
| `PG_HOST` | PostgreSQL host | localhost |
| `PG_PORT` | PostgreSQL port | 5432 |
| `PG_DATABASE` | PostgreSQL database name | Required |
| `PG_USER` | PostgreSQL username | Required |
| `PG_PASSWORD` | PostgreSQL password | Required |

## 🤝 Contributing

1. Follow existing code structure and naming conventions
2. Add proper error handling for new endpoints
3. Include input validation for all user inputs
4. Write clear comments for complex logic
5. Test all endpoints before submitting PR

## 📞 Support

For backend-specific issues:
- Check server logs for detailed error messages
- Verify database connections
- Ensure environment variables are properly set
- Review API endpoint documentation

---

**Backend API Ready! 🚀**
