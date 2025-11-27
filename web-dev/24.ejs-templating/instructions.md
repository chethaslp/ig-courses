# EJS Templating Setup

Server-Side Rendering (SSR) allows us to generate HTML on the server before sending it to the client. We will use EJS (Embedded JavaScript) as our template engine.

## Steps

1.  **Install EJS**:
    In your existing Express project (or a new one), install the package:
    ```bash
    npm install ejs
    ```

2.  **Configure Express**:
    Set EJS as the view engine in your `server.js` or `app.js`:
    ```javascript
    app.set('view engine', 'ejs');
    ```

3.  **Create a View**:
    *   Create a folder named `views`.
    *   Inside `views`, create a file named `index.ejs`.
    *   Add standard HTML to it:
        ```html
        <!DOCTYPE html>
        <html>
        <head>
            <title>My EJS App</title>
        </head>
        <body>
            <h1>Hello from EJS!</h1>
        </body>
        </html>
        ```

4.  **Render the View**:
    Update your root route to render the file instead of sending text:
    ```javascript
    app.get('/', (req, res) => {
        res.render('index'); // No need for .ejs extension
    });
    ```

5.  **Test**:
    Start your server and visit `http://localhost:3000`. You should see your HTML page.
