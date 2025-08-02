# Weka File Storage System

A modern web-based file storage system built with FastAPI, React, and MySQL.

## 🚀 Features

- **User Authentication**: Secure registration and login system
- **File Upload & Download**: Drag-and-drop file upload with progress tracking
- **Folder Management**: Create, organize, and manage folders
- **File Sharing**: Share files with other users via email
- **Security**: Password hashing, session management, and file access control
- **Modern UI**: Responsive React interface with Vite for fast development
- **Database**: MySQL database for reliable data storage
- **Environment Configuration**: Secure database credentials using .env files

## 🛠️ Technology Stack

- **Backend**: FastAPI (Python)
- **Frontend**: React + Vite (JavaScript)
- **Database**: MySQL
- **Authentication**: Session-based with password hashing
- **File Storage**: Local file system with database tracking
- **Configuration**: Environment variables with python-dotenv

## 📁 Project Structure

```
weka-ojt-filesystem/
├── client/                 # React frontend
│   ├── src/
│   ├── package.json
│   └── vite.config.js
├── server/                 # FastAPI backend
│   ├── dal/               # Data access layer
│   ├── routes/            # API routes
│   ├── uploads/           # File storage directory
│   ├── main.py            # FastAPI application
│   ├── requirements.txt   # Python dependencies
│   └── mysql_details.py   # Database configuration (legacy)
├── .env                   # Environment variables (auto-generated)
├── setup_mysql.py         # Database setup script
├── database_setup.sql     # SQL schema
└── README.md
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Node.js 16+
- MySQL 8.0+

### 1. Clone the Repository

```bash
git clone <repository-url>
cd weka-ojt-filesystem
```

### 2. Set Up MySQL Database

1. **Install MySQL** if not already installed
2. **Run the setup script**:
   ```bash
   python setup_mysql.py
   ```
   - Enter your MySQL root password when prompted
   - The script will create the database, tables, and `.env` file automatically

### 3. Install Dependencies

**Backend (Python)**:

```bash
cd server
pip install -r requirements.txt
```

**Frontend (Node.js)**:

```bash
cd client
npm install
```

### 4. Run the Application

**Start the Backend Server**:

```bash
cd server
python main.py
```

The FastAPI server will start on `http://localhost:8000`

**Start the Frontend Server** (in a new terminal):

```bash
cd client
npm run dev
```

The React app will start on `http://localhost:5173`

### 5. Access the Application

- **Frontend**: Open `http://localhost:5173` in your browser
- **API Documentation**: Visit `http://localhost:8000/docs` for interactive API docs

## 🔧 Configuration

### Environment Variables

The application uses environment variables for secure configuration. The `.env` file is automatically created by the setup script and contains:

```env
# MySQL Database Configuration
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=filesystem

# Application Configuration
APP_HOST=0.0.0.0
APP_PORT=8000
SECRET_KEY=your-secret-key-here-change-in-production
```

**Security Note**: The `.env` file is automatically added to `.gitignore` to prevent committing sensitive information to version control.

### Database Configuration

The MySQL connection details are automatically loaded from environment variables. The legacy `server/mysql_details.py` file is kept for backward compatibility but is no longer used.

### File Storage

Files are stored locally in the `server/uploads/` directory and referenced in the database.

## 🧪 Testing

### API Testing

You can test the API endpoints using the interactive documentation at `http://localhost:8000/docs` or use curl:

```bash
# Test signup
curl -X POST "http://localhost:8000/signup" \
  -H "Content-Type: application/json" \
  -d '{"username":"TestUser","email":"test@example.com","password":"Password123"}'

# Test login
curl -X POST "http://localhost:8000/login" \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"Password123"}'
```

## 🛡️ Security Features

- **Password Hashing**: Passwords are hashed using bcrypt
- **Session Management**: Secure session handling with cookies
- **Input Validation**: Comprehensive validation for all user inputs
- **File Access Control**: Users can only access their own files
- **SQL Injection Protection**: Parameterized queries prevent SQL injection

## 📝 API Endpoints

### Authentication

- `POST /signup` - User registration
- `POST /login` - User login
- `POST /logout` - User logout

### File Management

- `POST /upload` - Upload files
- `GET /files` - List user files
- `GET /download/{file_id}` - Download files
- `DELETE /files/{file_id}` - Delete files

### Folder Management

- `POST /folders` - Create folders
- `GET /folders` - List user folders
- `DELETE /folders/{folder_id}` - Delete folders

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Troubleshooting

### Common Issues

1. **MySQL Connection Error**: Ensure MySQL is running and the password in `mysql_details.py` is correct
2. **Port Already in Use**: Kill processes using ports 8000 or 5173
3. **Missing Dependencies**: Run `pip install -r requirements.txt` and `npm install`

### Getting Help

If you encounter issues:

1. Check the console output for error messages
2. Verify all prerequisites are installed
3. Ensure MySQL is running and accessible
4. Check that all dependencies are installed correctly
