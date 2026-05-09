# Node.js TypeScript Practice

A professional, lightweight Node.js API server built with TypeScript and native Node.js HTTP APIs. This project demonstrates custom routing, dynamic URL parameters, JSON request parsing, and file-based persistence in a clean, maintainable structure.

## Project Overview

This repository is a real-world practice project for building a scalable Node.js backend without Express or external routing libraries.

It includes:

- Custom route registration using a centralized route map
- Dynamic route matching for parameterized paths such as `/api/users/:id`
- JSON body parsing with native Node.js streams
- File-based datastore using `src/data/user.json`
- Modular helpers for request handling and response serialization
- Environment-based configuration via `.env`

## Project Structure

```text
src/
  server.ts
  config/
    index.ts
  data/
    user.json
  helpers/
    RouterHandler.ts
    dynamicRouterHandler.ts
    fileDb.ts
    parseBody.ts
    sendJson.ts
  routes/
    index.ts
```

## Architecture

- `src/server.ts`: starts the HTTP server, resolves requests, and dispatches handlers.
- `src/helpers/RouterHandler.ts`: stores routes per HTTP method and path.
- `src/helpers/dynamicRouterHandler.ts`: matches dynamic routes and extracts path parameters.
- `src/helpers/parseBody.ts`: parses incoming JSON request payloads.
- `src/helpers/sendJson.ts`: sends standardized JSON responses.
- `src/helpers/fileDb.ts`: reads and writes the user JSON datastore.
- `src/routes/index.ts`: defines API endpoints.

## Setup

### Prerequisites

- Node.js 18 or newer
- npm

### Install dependencies

```bash
npm install
```

### Configure environment

Create a `.env` file in the project root:

```env
PORT=5000
```

### Run the project

```bash
npx ts-node-dev --respawn --transpile-only src/server.ts
```

You should see:

```bash
server is running on port 5000
```

## API Endpoints

### GET `/`

Returns a welcome response.

Example:

```bash
curl http://localhost:5000/
```

Response:

```json
{
  "message": "Hello from node js with typescript...",
  "path": "/"
}
```

### GET `/api`

Returns server health status.

Example:

```bash
curl http://localhost:5000/api
```

Response:

```json
{
  "message": "Health status ok",
  "path": "/api"
}
```

### POST `/api/users`

Creates a new user in the JSON datastore.

Example:

```bash
curl -X POST http://localhost:5000/api/users \
  -H "Content-Type: application/json" \
  -d '{"id":3,"name":"New User"}'
```

Response:

```json
{
  "success": true,
  "data": {
    "id": 3,
    "name": "New User"
  }
}
```

### PUT `/api/users/:id`

Updates a user by ID.

Example:

```bash
curl -X PUT http://localhost:5000/api/users/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Updated Name"}'
```

Response:

```json
{
  "success": true,
  "message": "id 1 user updated",
  "data": {
    "id": 1,
    "name": "Updated Name"
  }
}
```

## Why this project is impressive

- Uses TypeScript with strong typing and modern idioms
- Implements custom routing without Express
- Demonstrates a clean separation between configuration, routing, helpers, and data
- Easily extendable for additional REST endpoints and middleware

## Notes

- `src/data/user.json` is a simple prototype datastore. For production, replace it with a real database.
- This repo is ideal for learning Node.js internals, TypeScript server design, and API structure.

### License

- This project is licensed under the terms of the **[MIT License](./LICENSE)**.
- You may replace or update the license as needed for client or proprietary projects.

---

### Contact and Maintainer

- **Name:** Md Abu Kayser
- **Project:** _nodejs-typescript-practice_
- **Maintainer:** [md-abu-kayser](https://github.com/md-abu-kayser)
- **Email:** [abu.kayser.official@gmail.com](mailto:abu.kayser.official@gmail.com)
- **GitHub:** [github.com/abu.kayser-official](https://github.com/md-abu-kayser)

If you’d like this README tailored for a specific purpose - such as **hiring managers**, **open-source contributors**, or **client deliverables** - feel free to request a custom tone or format.

---
