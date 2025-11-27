# Project: Task Manager

Combine everything you've learned to build a persistent Task Manager application.

## Requirements

1.  **Database**:
    *   Connect to MongoDB.
    *   Create a `Task` model with `title` (string) and `description` (string).

2.  **Routes & Views**:
    *   `GET /`: Display all tasks in a list (use `index.ejs`).
    *   `GET /create`: Show a form to add a new task.
    *   `POST /tasks`: Handle the form submission and save to the database.
    *   `GET /tasks/:id`: Show details of a single task.
    *   `DELETE /tasks/:id`: Delete a task (you might need `method-override` package or use AJAX).

3.  **Styling**:
    *   Use CSS to make the list and forms look presentable.

## Tips
*   Remember to use `app.use(express.urlencoded({ extended: true }))` to parse form data.
*   Use `Task.findById(req.params.id)` to get a specific task.
*   Use `Task.findByIdAndDelete(req.params.id)` for deletion.
