# Fetching Data from an API

## Objective
Learn how to fetch data from a public API using the `fetch` API.

## Instructions

### Step 1: Setup
Create an HTML file with a button and a `div` to display data.

### Step 2: Fetch Function
Write a JavaScript function to fetch data from a public API (e.g., JSONPlaceholder).
```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => response.json())
  .then(json => console.log(json));
```

### Step 3: Verify
Log the data to the console to verify it’s being fetched correctly.

**Resources:**
*   [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
*   [JSONPlaceholder](https://jsonplaceholder.typicode.com/)
