# MERN Blog Application

A full-stack blog application built with MongoDB, Express, React, and Node.js. This application allows users to register, login, create, read, update, and delete blog posts with full authentication and authorization.

## Features

- ✅ User Authentication (Register, Login, Logout)
- ✅ JWT-based Authentication
- ✅ Password Hashing with bcrypt
- ✅ Create, Read, Update, Delete (CRUD) Posts
- ✅ Post Search by Title
- ✅ Filter Posts by Author
- ✅ Only Authors Can Edit/Delete Their Posts
- ✅ Responsive Design
- ✅ Clean and Intuitive UI
- ✅ Post Creation/Editing for Authenticated Users

## Project Structure

```
mern-blog/
├── backend/
│   ├── models/
│   │   ├── User.js           # User Schema
│   │   └── Post.js           # Post Schema
│   ├── controllers/
│   │   ├── authController.js # Authentication logic
│   │   └── postController.js # Post operations
│   ├── routes/
│   │   ├── authRoutes.js     # Auth endpoints
│   │   └── postRoutes.js     # Post endpoints
│   ├── middleware/
│   │   ├── authMiddleware.js # JWT verification
│   │   └── authorize.js      # Authorization check
│   ├── .env                  # Environment variables
│   ├── package.json          # Dependencies
│   └── server.js             # Express server entry point
│
└── frontend/
    ├── public/
    │   └── index.html        # HTML template
    ├── src/
    │   ├── components/
    │   │   ├── Navbar.js     # Navigation component
    │   │   ├── PostCard.js   # Post display card
    │   │   └── Loading.js    # Loading spinner
    │   ├── pages/
    │   │   ├── HomePage.js          # Home page
    │   │   ├── RegisterPage.js      # Registration page
    │   │   ├── LoginPage.js         # Login page
    │   │   ├── PostDetailPage.js    # Single post view
    │   │   ├── CreatePostPage.js    # Create new post
    │   │   └── EditPostPage.js      # Edit post
    │   ├── services/
    │   │   └── api.js        # API calls with Axios
    │   ├── styles/
    │   │   ├── App.css
    │   │   ├── Navbar.css
    │   │   ├── PostCard.css
    │   │   ├── Loading.css
    │   │   ├── Auth.css
    │   │   ├── HomePage.css
    │   │   ├── PostDetail.css
    │   │   └── CreatePost.css
    │   ├── App.js           # Main React component
    │   └── index.js         # React entry point
    ├── .env                 # Environment variables
    └── package.json         # Dependencies
```

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14 or higher): [Download here](https://nodejs.org/)
- **MongoDB**: [Download Community Edition](https://www.mongodb.com/try/download/community)
  - Or use **MongoDB Atlas** (Cloud): [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
- **npm** (comes with Node.js)

## Installation & Setup

### 1. MongoDB Setup

#### Option A: Local MongoDB
1. Install MongoDB Community Edition
2. Make sure MongoDB is running on `localhost:27017`
3. Create a database named `mern-blog` (or change the URI in `.env`)

#### Option B: MongoDB Atlas (Cloud)
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free account
3. Create a cluster
4. Get your connection string: `mongodb+srv://username:password@cluster.mongodb.net/mern-blog?retryWrites=true&w=majority`
5. Copy this to the backend `.env` file

### 2. Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd mern-blog/backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create/Update the `.env` file with your configuration:
   ```
   MONGO_URI=mongodb://localhost:27017/mern-blog
   JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
   PORT=5000
   NODE_ENV=development
   ```

   **Important**: Change `JWT_SECRET` to a strong random string in production!

4. Start the backend server:
   ```bash
   npm start
   ```
   
   Or for development with auto-reload:
   ```bash
   npm run dev
   ```

   You should see: `Server running on port 5000`

### 3. Frontend Setup

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd mern-blog/frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. The `.env` file is already configured:
   ```
   REACT_APP_API_URL=http://localhost:5000/api
   ```

4. Start the React development server:
   ```bash
   npm start
   ```

   This will automatically open `http://localhost:3000` in your browser.

## Testing the Application

### 1. Register a New User
- Click "Register" in the navbar
- Fill in your name, email, and password
- Click "Register"

### 2. Create a Blog Post
- After logging in, click "➕ New Post"
- Enter a title and content
- Click "Publish Post"

### 3. View Posts
- Posts are displayed on the home page
- Click "Read More" to view the full post
- Search posts by title or filter by author

### 4. Edit/Delete Your Posts
- View your post
- Click "✏️ Edit" to modify it
- Click "🗑️ Delete" to remove it

### 5. Logout
- Click "Logout" in the navbar
- You'll be redirected to the home page

## API Endpoints

### Authentication Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login user |

#### Register Request:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "confirmPassword": "password123"
}
```

#### Login Request:
```json
{
  "email": "john@example.com",
  "password": "password123"
}
```

### Post Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/posts` | Get all posts (with search/filter) | No |
| GET | `/api/posts/:id` | Get single post | No |
| POST | `/api/posts` | Create new post | Yes |
| PUT | `/api/posts/:id` | Update post | Yes (Author only) |
| DELETE | `/api/posts/:id` | Delete post | Yes (Author only) |

#### Create/Update Post Request:
```json
{
  "title": "My First Blog Post",
  "content": "This is the content of my blog post..."
}
```

#### Query Parameters for GET /api/posts:
- `search`: Search by title (e.g., `/api/posts?search=javascript`)
- `author`: Filter by author name (e.g., `/api/posts?author=john`)

## Technologies Used

### Backend
- **Node.js**: JavaScript runtime
- **Express.js**: Web framework
- **MongoDB**: NoSQL database
- **Mongoose**: MongoDB object modeling
- **bcryptjs**: Password hashing
- **jsonwebtoken**: JWT authentication
- **CORS**: Cross-origin resource sharing

### Frontend
- **React**: UI library
- **React Router**: Client-side routing
- **Axios**: HTTP client
- **CSS**: Styling (vanilla CSS)

## Folder Structure Explanation

### Backend Folders

- **models/**: Database schemas (User, Post)
- **controllers/**: Business logic for requests
- **routes/**: API endpoint definitions
- **middleware/**: JWT verification and authorization

### Frontend Folders

- **components/**: Reusable React components
- **pages/**: Full page components
- **services/**: API communication (Axios)
- **styles/**: CSS stylesheets

## Key Features Explained

### 1. Authentication Flow
1. User registers with email and password
2. Password is hashed using bcrypt
3. User logs in and receives JWT token
4. Token is stored in localStorage
5. Token is sent with every authenticated request

### 2. Authorization
- Only logged-in users can create posts
- Only the post author can edit/delete their posts
- Middleware checks JWT token validity
- Authorization middleware checks if user is the author

### 3. Search & Filter
- Search posts by title (case-insensitive regex)
- Filter posts by author name
- Multiple filters can be combined

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running: `mongod` (Windows) or `brew services start mongodb-community` (Mac)
- Check `MONGO_URI` in `.env` file
- If using MongoDB Atlas, ensure your IP is whitelisted

### Port Already in Use
- Change `PORT` in backend `.env` (e.g., `PORT=5001`)
- React uses port 3000 by default, change with: `PORT=3001 npm start`

### Token Errors
- Clear localStorage: Open DevTools → Application → localStorage → Clear
- Log out and log back in
- Generate a new strong JWT_SECRET

### CORS Errors
- Ensure backend is running on `http://localhost:5000`
- Check `proxy` in frontend `package.json`

### Dependencies Issues
- Clear cache: `npm cache clean --force`
- Delete node_modules and lock file
- Reinstall: `npm install`

## Production Deployment

### Backend (using Heroku as example)
1. Create `Procfile`: `web: node server.js`
2. Update `JWT_SECRET` to strong random string
3. Use MongoDB Atlas for database
4. Deploy to Heroku

### Frontend (using Netlify as example)
1. Update `REACT_APP_API_URL` to your deployed backend URL
2. Run: `npm run build`
3. Deploy the `build` folder to Netlify

## Security Best Practices

1. **Change JWT_SECRET** in production to a strong, random string
2. **Use HTTPS** in production
3. **Validate input** on both frontend and backend
4. **Use environment variables** for sensitive data
5. **Implement rate limiting** for API endpoints
6. **Use strong passwords** (enforce password requirements)
7. **Add HTTPS redirect** in production

## Future Enhancements

- [ ] Add comments system
- [ ] Add post categories/tags
- [ ] Add user profiles
- [ ] Add post likes/reactions
- [ ] Add email verification
- [ ] Add password reset functionality
- [ ] Add admin panel
- [ ] Add pagination
- [ ] Add sorting options
- [ ] Add markdown support in posts
- [ ] Add image uploads
- [ ] Add dark mode

## Troubleshooting Commands

```bash
# Clear npm cache
npm cache clean --force

# Check if port is in use (Windows)
netstat -ano | findstr :5000

# Kill process on port (Windows)
taskkill /PID <PID> /F

# Check if MongoDB is running
mongosh

# Reset database (delete all data)
# Connect to MongoDB and run: db.dropDatabase()
```

## License

This project is open source and available for educational purposes.

## Support

If you encounter any issues, please check:
1. All prerequisites are installed
2. `.env` files are correctly configured
3. MongoDB is running
4. Both backend and frontend servers are running
5. Check browser console and server logs for errors

## Author

Created as a comprehensive MERN stack learning project.

Happy blogging! 📝
#   B l o g p o s t  
 #   B l o g p o s t  
 