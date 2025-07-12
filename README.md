Here is a `readme.md` for your project:

```markdown
# NLW Agents Server

This project is a backend API developed during the Rocketseat NLW Agents event. It provides endpoints for managing rooms and questions, supporting audio uploads, and integrates with a PostgreSQL database using Drizzle ORM.

## Available Routes

- `GET /health`  
  Health check endpoint.

- `GET /rooms`  
  List all rooms.

- `POST /rooms`  
  Create a new room.  
  **Body:**  
  ```json
  {
    "name": "Room name",
    "description": "Room description"
  }
  ```

- `GET /rooms/:roomId/questions`  
  List all questions for a specific room.

- `POST /rooms/:roomId/questions`  
  Create a question in a room.  
  **Body:**
  ```json
  {
    "question": "Your question"
  }
  ```

- `POST /upload-audio`  
  Upload an audio file (route details in code).

## Packages Used

- **fastify**: Web framework for building APIs.
- **@fastify/cors**: CORS support for Fastify.
- **@fastify/multipart**: File upload support.
- **fastify-type-provider-zod**: Type-safe validation using Zod.
- **zod**: Schema validation.
- **drizzle-orm**: TypeScript ORM for SQL databases.
- **drizzle-kit**: CLI for Drizzle ORM migrations and generation.
- **postgres**: PostgreSQL client.
- **@google/genai**: Google Generative AI integration.
- **@biomejs/biome**: Linting and formatting.
- **typescript**: TypeScript support.
- **ultracite**: Utility package (see docs).

## Scripts

- `dev`: Start the server in watch mode with TypeScript support.
- `start`: Start the server.
- `db:generate`: Generate Drizzle ORM artifacts.
- `db:migrate`: Run database migrations.
- `db:studio`: Open Drizzle Studio for DB management.
- `db:seed`: Seed the database.

## Environment Variables

Copy `.env.example` to `.env` and fill in the values:

```
PORT=3333
DATABASE_URL=postgres://docker:docker@localhost:5432/agents
GEMINI_API_KEY=your_google_genai_key
```

- `PORT`: Port for the server.
- `DATABASE_URL`: PostgreSQL connection string.
- `GEMINI_API_KEY`: Google Generative AI API key.

## Using `client.http`

The `client.http` file contains example HTTP requests for testing the API using IntelliJ HTTP Client.

- Set the `@baseUrl` variable to your server URL.
- Use the requests to test endpoints and chain responses (e.g., use `createRoom` response in subsequent requests).

## Docker Compose

The `docker-compose.yml` file sets up a PostgreSQL database with the `pgvector` extension:

- **Service:** `nlw-agents-pg`
- **Image:** `pgvector/pgvector:pg17`
- **Ports:** 5432:5432
- **Volumes:** Initializes the DB with `setup.sql`.

### Running with Docker

1. Start the database:
   ```
   docker compose up -d
   ```
2. Run migrations:
   ```
   npm run db:migrate
   ```
3. Start the server:
   ```
   npm run dev
   ```

---

Developed during the [Rocketseat NLW Agents](https://www.rocketseat.com.br/) event.

```
