# CipherSQL Studio - Frontend

React-based frontend application with user authentication and interactive SQL learning interface.

## 🚀 Features

### Authentication System
- **User Registration & Login** with email validation
- **Toast Notifications** using react-hot-toast for user feedback
- **Form Validation** with real-time error handling
- **Automatic Redirects** after successful authentication
- **Responsive Design** for all screen sizes

### SQL Learning Interface
- **Interactive SQL Editor** powered by Monaco Editor
- **Assignment Browser** with difficulty filtering
- **Real-time Query Execution** with results display
- **Schema Visualization** for database understanding
- **Hint System** for guided learning
- **Progress Tracking** and assignment completion

### User Experience
- **Modern UI Design** with clean, intuitive interface
- **Responsive Layout** optimized for desktop and mobile
- **Loading States** and error handling throughout
- **Navigation System** with React Router DOM
- **Component-based Architecture** for maintainability

## 📁 Project Structure

```
Frontend/
├── src/
│   ├── component/           # Reusable UI components
│   │   ├── Navbar.jsx      # Navigation bar
│   │   ├── SQLEditor.jsx   # Monaco-based SQL editor
│   │   ├── ResultsDisplay.jsx # Query results viewer
│   │   ├── Schema.jsx      # Database schema display
│   │   ├── Sidebar.jsx     # Assignment navigation
│   │   ├── QueryPanel.jsx  # Query execution panel
│   │   └── Problem.jsx     # Assignment problem display
│   ├── pages/              # Page components
│   │   ├── Home.jsx        # Landing page
│   │   ├── Login.jsx       # User login form
│   │   ├── Register.jsx    # User registration form
│   │   ├── AssignmentList.jsx # Browse assignments
│   │   └── Assignment.jsx  # Individual assignment page
│   ├── styles/             # CSS stylesheets
│   │   ├── App.css         # Global styles
│   │   ├── Auth.css        # Authentication forms
│   │   ├── Navbar.css      # Navigation styling
│   │   ├── Home.css        # Landing page styles
│   │   └── [component].css # Component-specific styles
│   ├── config/             # Configuration files
│   │   └── api.js          # API configuration
│   ├── App.jsx             # Main application component
│   └── main.jsx            # Application entry point
├── public/                 # Static assets
├── index.html              # HTML template
├── package.json            # Dependencies and scripts
└── vite.config.js          # Vite configuration
```

## 🛠️ Installation

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn package manager
- Backend API running on http://localhost:8080

### Setup Steps

1. **Install Dependencies:**
   ```bash
   npm install
   ```

2. **Environment Configuration:**
   Create `.env` file:
   ```env
   VITE_API_URL=http://localhost:8080
   ```

3. **Start Development Server:**
   ```bash
   npm run dev
   ```
   Application runs on: http://localhost:5173

4. **Build for Production:**
   ```bash
   npm run build
   ```

5. **Preview Production Build:**
   ```bash
   npm run preview
   ```

## 🎯 Pages & Components

### Authentication Pages

#### Login Page (`/login`)
- Email and password input fields
- Form validation with error messages
- Success toast notifications
- Automatic redirect to home page
- Link to registration page

**Features:**
- Real-time form validation
- Loading states during authentication
- Error handling for invalid credentials
- Toast notifications for user feedback

#### Register Page (`/register`)
- Name, email, password, and confirm password fields
- Password strength validation
- Password confirmation matching
- Success toast and redirect
- Link to login page

**Features:**
- Comprehensive form validation
- Password strength requirements
- Duplicate email detection
- Success feedback with user name

### Main Application Pages

#### Home Page (`/`)
- Welcome message and platform introduction
- Call-to-action buttons
- Feature highlights
- Navigation to assignments

#### Assignment List (`/assignments`)
- Browse all available SQL assignments
- Filter by difficulty level
- Assignment cards with descriptions
- Progress indicators
- Direct links to individual assignments

#### Assignment Page (`/assignment/:id`)
- Interactive SQL editor with syntax highlighting
- Problem statement and requirements
- Database schema visualization
- Query execution and results display
- Hint system for guidance
- Answer validation feedback

### Reusable Components

#### Navbar Component
- Brand logo and navigation links
- Authentication status display
- Login/Register buttons for unauthenticated users
- User welcome message for authenticated users
- Responsive mobile menu

#### SQL Editor Component
- Monaco Editor integration
- SQL syntax highlighting
- Auto-completion features
- Query execution controls
- Error highlighting

#### Results Display Component
- Tabular data presentation
- Query execution time display
- Row count information
- Error message handling
- Export functionality

#### Schema Component
- Database table visualization
- Column information display
- Data type indicators
- Sample data preview

## 🎨 Styling & Design

### Design System
- **Color Palette**: Modern blue and gray tones
- **Typography**: Clean, readable fonts
- **Spacing**: Consistent margin and padding system
- **Components**: Reusable UI elements
- **Responsive**: Mobile-first design approach

### CSS Architecture
- **Component-scoped styles** for maintainability
- **Global styles** for common elements
- **Responsive breakpoints** for different screen sizes
- **CSS custom properties** for theming
- **Flexbox and Grid** for layouts

### Authentication UI
- **Gradient backgrounds** for visual appeal
- **Card-based layouts** for form containers
- **Smooth transitions** and hover effects
- **Loading states** with disabled buttons
- **Error styling** with red color scheme

## 🔧 Configuration

### Environment Variables
| Variable | Description | Default |
|----------|-------------|---------|
| `VITE_API_URL` | Backend API base URL | http://localhost:8080 |

### Vite Configuration
```javascript
// vite.config.js
export default {
  plugins: [react()],
  server: {
    port: 5173,
    proxy: {
      '/api': 'http://localhost:8080'
    }
  }
}
```

## 📱 Responsive Design

### Breakpoints
- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

### Mobile Optimizations
- Touch-friendly button sizes
- Collapsible navigation menu
- Optimized form layouts
- Readable font sizes
- Proper viewport configuration

## 🔗 API Integration

### Authentication Endpoints
```javascript
// Login
POST /api/auth/login
{
  email: "user@example.com",
  password: "password123"
}

// Register
POST /api/auth/register
{
  name: "John Doe",
  email: "user@example.com",
  password: "password123"
}
```

### Assignment Endpoints
```javascript
// Get all assignments
GET /api/assignment

// Get specific assignment
GET /api/assignment/:id

// Execute SQL query
POST /api/sql/execute
{
  query: "SELECT * FROM users;",
  assignmentId: "assignment_id"
}
```

## 🚀 Deployment

### Build Process
```bash
# Install dependencies
npm install

# Build for production
npm run build

# Preview production build
npm run preview
```

### Deployment Platforms
- **Vercel**: Automatic deployments from Git
- **Netlify**: Static site hosting with CI/CD
- **GitHub Pages**: Free hosting for static sites
- **AWS S3**: Scalable static website hosting

### Environment Setup for Production
```env
VITE_API_URL=https://your-backend-api.com
```

## 🧪 Testing

### Manual Testing Checklist
- [ ] User registration with valid data
- [ ] User login with correct credentials
- [ ] Form validation with invalid inputs
- [ ] Toast notifications display correctly
- [ ] Navigation between pages works
- [ ] SQL editor functionality
- [ ] Query execution and results display
- [ ] Responsive design on different screen sizes

### Browser Compatibility
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 🔧 Development Tools

### Dependencies
```json
{
  "react": "^19.2.0",
  "react-dom": "^19.2.0",
  "react-router-dom": "^7.11.0",
  "axios": "^1.13.2",
  "react-hot-toast": "^2.4.1",
  "@monaco-editor/react": "^4.7.0"
}
```

### Dev Dependencies
```json
{
  "vite": "^7.2.4",
  "@vitejs/plugin-react": "^5.1.1",
  "eslint": "^9.39.1"
}
```

## 🎯 User Flow

### New User Registration
1. Visit `/register` page
2. Fill in name, email, password, confirm password
3. Submit form with validation
4. See success toast notification
5. Automatic redirect to home page
6. User data stored in localStorage

### Existing User Login
1. Visit `/login` page
2. Enter email and password
3. Submit form with validation
4. See welcome toast with user name
5. Automatic redirect to home page
6. Authentication token stored

### SQL Learning Flow
1. Browse assignments at `/assignments`
2. Select assignment by difficulty
3. Read problem statement and requirements
4. View database schema and sample data
5. Write SQL query in editor
6. Execute query and view results
7. Get hints if needed
8. Validate answer and get feedback

## 🤝 Contributing

### Development Guidelines
1. Follow React best practices and hooks patterns
2. Use functional components with hooks
3. Implement proper error boundaries
4. Add loading states for async operations
5. Ensure responsive design for all components
6. Write clean, readable CSS with proper naming
7. Test components across different browsers

### Code Style
- Use ES6+ features and modern JavaScript
- Follow consistent naming conventions
- Add comments for complex logic
- Use proper component structure
- Implement proper prop validation

## 📞 Support

### Common Issues
- **API Connection**: Verify backend is running on correct port
- **CORS Errors**: Check backend CORS configuration
- **Build Errors**: Clear node_modules and reinstall dependencies
- **Styling Issues**: Check CSS import paths and class names

### Debugging
- Use React Developer Tools browser extension
- Check browser console for JavaScript errors
- Verify network requests in browser DevTools
- Test API endpoints with tools like Postman

---

**Frontend Ready for SQL Learning! 🎓**
