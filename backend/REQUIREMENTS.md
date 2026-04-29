# Backend Requirements & Setup Guide

## System Requirements

### 1. **Node.js & npm**
- **Node.js**: Version 14.0.0 or higher
- **npm**: Version 6.0.0 or higher
- Download from: https://nodejs.org/

Verify installation:
```bash
node --version
npm --version
```

### 2. **MongoDB**
- **MongoDB Community Edition**: Latest version recommended
- Download from: https://www.mongodb.com/try/download/community
- Must be running on `localhost:27017` (default port)

Start MongoDB:
- **Windows**: Use MongoDB Compass or Command Prompt: `mongod`
- **macOS**: `brew services start mongodb-community`
- **Linux**: `sudo systemctl start mongod`

Verify connection:
```bash
mongosh  # or mongo in older versions
```

## Project Dependencies

All dependencies are listed in `package.json`:

```json
{
  "dependencies": {
    "express": "^5.2.1",        // Web framework
    "mongoose": "^9.3.2",       // MongoDB ODM
    "bcryptjs": "^3.0.3",       // Password hashing
    "jsonwebtoken": "^9.0.3",   // JWT authentication
    "cors": "^2.8.6",           // Cross-Origin Resource Sharing
    "multer": "^2.1.1",         // File upload handling
    "qrcode": "^1.5.4"          // QR code generation
  }
}
```

## Installation Steps

### 1. Install Node Modules
```bash
npm install
```

### 2. Start MongoDB
Ensure MongoDB is running before starting the server.

### 3. Start the Backend Server
```bash
npm start
```

Expected output:
```
Auth routes loaded
Server running on 5000
MongoDB Connected
Default Admin Created
✅ Admin already exists
```

## Server Details

- **Port**: 5000
- **Host**: 0.0.0.0 (accessible from any network interface)
- **Database**: MongoDB at `mongodb://127.0.0.1:27017/hostelDB`

## Default Admin Credentials

Created automatically on first run:
- **Email**: `admin123@gmail.com`
- **Password**: `adminpass123`

## API Endpoints

Base URL: `http://localhost:5000`

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/create-warden` - Create warden (admin only)
- `GET /api/auth/students` - Get all students
- `GET /api/attendance/*` - Attendance endpoints
- `GET /api/leave/*` - Leave request endpoints
- `GET /api/qr/*` - QR code endpoints
- `GET /api/hostel/*` - Hostel endpoints
- `GET /api/room/*` - Room endpoints

## Troubleshooting

### Error: "MongoDB Connected" not showing
- **Issue**: MongoDB is not running
- **Solution**: Start MongoDB with `mongod` command

### Error: "EADDRINUSE :::5000"
- **Issue**: Port 5000 is already in use
- **Solution**: Kill the process or use a different port

### Error: "Cannot find module"
- **Issue**: Dependencies not installed
- **Solution**: Run `npm install`

### npm audit vulnerabilities
Fix vulnerabilities with:
```bash
npm audit fix
```

## Environment Setup (Optional)

For production, consider using environment variables. Create a `.env` file:
```
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/hostelDB
JWT_SECRET=your_secret_key_here
```

Then update `server.js` to use these variables.

## Security Notes

- Change default admin password after first login
- Use strong JWT secrets in production
- Implement rate limiting for API endpoints
- Validate all user inputs
- Use HTTPS in production

## Next Steps

1. Install all requirements (Node.js, MongoDB)
2. Run `npm install` in the backend folder
3. Start MongoDB
4. Run `npm start` to start the server
5. Serve the frontend (see `../frontend` folder)
