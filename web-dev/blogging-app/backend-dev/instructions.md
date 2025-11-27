# Backend Development

Let's build the core of our application.

## Steps

1.  **Setup**:
    *   Initialize `npm`, install `express`, `ejs`, `mongoose`.
    *   Create `app.js` and set up the server.

2.  **Database**:
    *   Connect to MongoDB Atlas.
    *   Create `models/blog.js` with the schema defined in the planning phase.

3.  **Routes**:
    *   Implement the routes defined in the planning phase.
    *   For now, just return text or JSON to verify they work (e.g., `res.send('All blogs')`).

4.  **MVC Structure (Optional but Recommended)**:
    *   Create a `controllers` folder.
    *   Move logic from routes to controller functions (e.g., `blogController.blog_index`).
    *   Keep your route files clean.
