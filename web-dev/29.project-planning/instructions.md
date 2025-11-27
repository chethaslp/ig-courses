# Project Planning: Blogging App

Before writing code, we need to plan our application. We are building a blog where users can view posts, and admins can create/delete them.

## Features
1.  **Home Page**: List all blog posts (title, snippet).
2.  **Post Details**: View the full content of a post.
3.  **Create Post**: A form to add a new blog post.
4.  **Delete Post**: Remove a post.
5.  **About Page**: Static page about the author.

## Database Schema (MongoDB)
We need a `Blog` model with:
*   `title`: String, required.
*   `snippet`: String, required (short summary).
*   `body`: String, required (main content).
*   `timestamps`: Created at / Updated at.

## Routes
| Method | Path | Description |
| :--- | :--- | :--- |
| GET | `/` | Redirect to `/blogs` |
| GET | `/blogs` | Show all blogs (Index) |
| POST | `/blogs` | Create a new blog |
| GET | `/blogs/create` | Show form to create blog |
| GET | `/blogs/:id` | Show single blog details |
| DELETE | `/blogs/:id` | Delete a blog |
