# Mongoose CRUD Operations

Mongoose uses "Schemas" to define the structure of your data and "Models" to interact with the database.

## Steps

1.  **Define a Schema**:
    Create a folder `models` and a file `Task.js`:
    ```javascript
    const mongoose = require('mongoose');
    const Schema = mongoose.Schema;

    const taskSchema = new Schema({
        title: { type: String, required: true },
        completed: { type: Boolean, default: false }
    }, { timestamps: true });

    const Task = mongoose.model('Task', taskSchema);
    module.exports = Task;
    ```

2.  **Create (Save Data)**:
    In your route:
    ```javascript
    const Task = require('./models/Task');

    app.get('/add-task', (req, res) => {
        const task = new Task({
            title: 'Learn Mongoose'
        });

        task.save()
            .then((result) => res.send(result))
            .catch((err) => console.log(err));
    });
    ```

3.  **Read (Find Data)**:
    ```javascript
    app.get('/all-tasks', (req, res) => {
        Task.find()
            .then((tasks) => res.send(tasks))
            .catch((err) => console.log(err));
    });
    ```

4.  **Test**:
    Visit `/add-task` to create a document, then `/all-tasks` to see it.
