# Frontend Development

Now we connect the backend to the user interface.

## Steps

1.  **Partials**:
    *   Create `views/partials/head.ejs`, `nav.ejs`, `footer.ejs`.
    *   Include them in your main views to avoid code duplication.

2.  **Views**:
    *   `index.ejs`: Loop through the blogs passed from the controller and display them.
    *   `details.ejs`: Show the full content of a single blog.
    *   `create.ejs`: A form with inputs for title, snippet, and body.
    *   `404.ejs`: A custom error page.

3.  **Static Files**:
    *   Create a `public` folder for CSS and images.
    *   Configure Express to serve it: `app.use(express.static('public'));`.
    *   Add styles to make your blog look professional.

4.  **Interactivity**:
    *   For the "Delete" button on the details page, you might need a small script to send a `DELETE` request using `fetch` API, as HTML forms only support GET and POST natively.
    ```javascript
    const trashcan = document.querySelector('a.delete');
    trashcan.addEventListener('click', (e) => {
        const endpoint = `/blogs/${trashcan.dataset.doc}`;
        fetch(endpoint, { method: 'DELETE' })
            .then(response => response.json())
            .then(data => window.location.href = data.redirect)
            .catch(err => console.log(err));
    });
    ```
