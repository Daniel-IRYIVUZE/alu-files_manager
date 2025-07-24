# alu-files_manager

A full-featured file management API built for Holberton School's Advanced Back-End Development module.  
This project provides secure user authentication, file uploads, access control, publishing, file listing, and image thumbnail generation using a microservices architecture.

## Tech Stack

- Node.js & Express – RESTful API backend
- MongoDB – File metadata and user data storage
- Redis – Session management and job queue
- Bull – Background processing (thumbnail generation)
- UUID – Unique file identifiers
- Multer – Handling file uploads

## Features

### User Authentication
- Register and log in via API
- Auth tokens stored in Redis
- Secure access to protected endpoints

### File Management
- Upload files of different types (folders, images, documents)
- Store metadata in MongoDB
- Save physical files in a local `/uploads` directory

### File Access Control
- Set files as public or private
- Only authenticated users can view or manage their files
- Retrieve files using their unique IDs

### Background Jobs
- Use Bull and Redis to generate image thumbnails asynchronously for image uploads

### File Listing and Retrieval
- Paginated listing of user files (with parent-child folder structure)
- Serve raw file content or preview via endpoint

## API Endpoints Overview

| Method | Endpoint                    | Description                      |
|--------|-----------------------------|----------------------------------|
| POST   | `/users`                    | Register new user                |
| GET    | `/connect`                  | Log in                           |
| GET    | `/disconnect`               | Log out                          |
| GET    | `/users/me`                 | Get user profile                 |
| POST   | `/files`                    | Upload a file or folder          |
| GET    | `/files/:id`                | Get file metadata by ID          |
| GET    | `/files`                    | List user files (paginated)      |
| PUT    | `/files/:id/publish`        | Publish a private file           |
| PUT    | `/files/:id/unpublish`      | Unpublish a public file          |
| GET    | `/files/:id/data`           | Retrieve file content            |

## Setup and Run

```bash
# Clone repository
git clone https://github.com/Daniel-IRYIVUZE/alu-files_manager.git
cd alu-files_manager

# Install dependencies
npm install

# Set environment variables
cp .env.example .env
# Edit .env file with MongoDB and Redis credentials

# Start Redis server
redis-server

# Start the server
npm start

# Start the background worker
npm run worker
````
## Testing

Unit and integration tests are located in the `tests/` folder.

```bash
npm test
```

## Authors

* Daniel Iryivuze

Built for Holberton School’s Advanced Back-End Development module.