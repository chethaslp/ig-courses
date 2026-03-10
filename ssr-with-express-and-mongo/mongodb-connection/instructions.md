# MongoDB Connection

MongoDB is a NoSQL database that stores data in JSON-like documents. Mongoose is a library that makes working with MongoDB in Node.js easier.

## Steps

1.  **Setup MongoDB**:
    *   You can install MongoDB locally or use MongoDB Atlas (cloud).
    *   For this course, we recommend creating a free cluster on [MongoDB Atlas](https://www.mongodb.com/atlas).
    *   Get your connection string (e.g., `mongodb+srv://<user>:<password>@cluster...`).

2.  **Install Mongoose**:
    ```bash
    npm install mongoose
    ```

3.  **Connect in Code**:
    In your `server.js`:
    ```javascript
    const mongoose = require('mongoose');

    // Replace with your actual connection string
    const dbURI = 'mongodb+srv://...'; 

    mongoose.connect(dbURI)
        .then((result) => console.log('Connected to DB'))
        .catch((err) => console.log(err));
    ```

4.  **Verify**:
    Run your server. You should see "Connected to DB" in the terminal.
