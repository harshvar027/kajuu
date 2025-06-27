# Memory Page Image Loading Troubleshooting Guide

## Issue: Pictures not showing in memory.html

### Step 1: Check if Backend Server is Running

1. **Open a terminal/command prompt**
2. **Navigate to the backend directory:**
   ```bash
   cd backend
   ```
3. **Start the server:**
   ```bash
   node server.js
   ```
4. **You should see:**
   ```
   Connected to MongoDB
   Server running on port 3000
   ```

### Step 2: Check MongoDB Connection

The backend requires MongoDB to be running. If you don't have MongoDB installed:

1. **Install MongoDB Community Edition** from https://www.mongodb.com/try/download/community
2. **Or use MongoDB Atlas** (cloud version) - update the connection string in backend/.env

### Step 3: Test the Connection

1. **Open test-images.html** in your browser
2. **Click "Test Server Connection"** - should show ✅ Server is running
3. **Click "Load Memories"** - should show your memories
4. **Click "Test Image URLs"** - should show images loading

### Step 4: Common Issues and Solutions

#### Issue: "Cannot connect to server"
**Solution:** Make sure the backend server is running on port 3000

#### Issue: "MongoDB connection error"
**Solution:** 
- Install MongoDB locally, OR
- Create a .env file in backend/ with:
  ```
  MONGODB_URI=mongodb://localhost:27017/romantic-website
  ```

#### Issue: Images show as broken
**Solution:** 
- Check browser console for CORS errors
- Ensure backend server is running
- Check if image files exist in backend/uploads/

#### Issue: "No memories found"
**Solution:** 
- Add some memories first using the "Add Memory" button
- Check if the form submission is working

### Step 5: Manual Test

1. **Open browser developer tools** (F12)
2. **Go to Console tab**
3. **Try accessing:** http://localhost:3000/api/memories
4. **You should see JSON data with your memories**

### Step 6: Image URL Format

Images should be accessible at:
- `http://localhost:3000/uploads/filename.jpg`

If you see URLs like `/uploads/1750188512711.jpg`, they should work when the server is running.

### Step 7: Browser CORS Issues

If you see CORS errors in console:
1. Make sure you're accessing memory.html through a web server (not file://)
2. Use a local server like Live Server in VS Code
3. Or access via http://localhost:3000 (if you serve the frontend from backend)

### Step 8: File Permissions

Make sure the backend/uploads/ directory has read permissions for the web server.

### Still Having Issues?

1. **Check the browser console** for specific error messages
2. **Check the backend console** for server errors
3. **Try the test-images.html** file to isolate the issue
4. **Restart the backend server** after making changes

### Quick Fix Checklist

- [ ] Backend server running on port 3000
- [ ] MongoDB connected
- [ ] Images exist in backend/uploads/
- [ ] No CORS errors in browser console
- [ ] Accessing via web server (not file://)
- [ ] API_URL is correct in memory.html (http://localhost:3000) 