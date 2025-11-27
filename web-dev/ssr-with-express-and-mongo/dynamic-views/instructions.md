# Dynamic Views with EJS

The power of EJS comes from injecting data and using JavaScript logic directly in your HTML.

## Steps

1.  **Pass Data**:
    Modify your route to pass an object to the view:
    ```javascript
    app.get('/', (req, res) => {
        const user = { name: "Alice", isAdmin: true };
        res.render('index', { user: user });
    });
    ```

2.  **Display Data**:
    In `views/index.ejs`, use the `<%= %>` syntax to output values:
    ```html
    <h1>Welcome, <%= user.name %>!</h1>
    ```

3.  **Use Conditionals**:
    Use `<% %>` (without the `=`) for control flow:
    ```html
    <% if (user.isAdmin) { %>
        <button>Admin Dashboard</button>
    <% } else { %>
        <p>Welcome, guest.</p>
    <% } %>
    ```

4.  **Use Loops**:
    Pass an array of items and loop through them:
    ```javascript
    // In route
    const items = ['Apple', 'Banana', 'Cherry'];
    res.render('index', { items });
    ```

    ```html
    <!-- In view -->
    <ul>
        <% items.forEach(function(item) { %>
            <li><%= item %></li>
        <% }); %>
    </ul>
    ```
