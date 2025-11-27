# Deployment

Your app works locally. Now let's share it with the world. We will use a service like Render or Heroku.

## Steps

1.  **Prepare for Production**:
    *   Ensure your `package.json` has a `start` script: `"start": "node app.js"`.
    *   Ensure you are not hardcoding secrets (like DB URI) in your code. Use environment variables (`process.env.DB_URI`).
    *   Ensure your app listens on the port assigned by the host: `app.listen(process.env.PORT || 3000)`.

2.  **Push to GitHub**:
    *   Commit all your code.
    *   Push to a public or private repository.

3.  **Deploy (Example: Render)**:
    *   Create a new "Web Service" on Render.
    *   Connect your GitHub repo.
    *   Set the "Build Command" to `npm install`.
    *   Set the "Start Command" to `node app.js`.
    *   **Crucial**: Add your Environment Variables (e.g., `DB_URI`) in the dashboard settings.

4.  **Go Live**:
    *   Click deploy. Wait for the build to finish.
    *   Visit your live URL!
