
# Workspace Backend

This is a simple Node.js backend for the Workspace app, using PostgreSQL for data storage.

## Setup

1.  **Install Dependencies**:
    ```bash
    cd backend
    npm install
    ```

2.  **Database Configuration**:
    *   You need a running PostgreSQL database.
    *   Create a `.env` file in the `backend` folder based on the example:
        ```
        DATABASE_URL=postgres://user:password@localhost:5432/workspace_db
        JWT_SECRET=your_secret_key
        PORT=3000
        ```
    *   Replace `user`, `password`, `localhost`, and `workspace_db` with your actual PostgreSQL credentials.
    *   The server will automatically create the necessary tables (`users`, `user_data`) on startup.

3.  **Run Server**:
    ```bash
    npm start
    ```

## Deploying to Russian Clouds (Amvera, Timeweb, Yandex)

Since you requested a solution "convenient for RF", this backend is standard Node.js and can be deployed easily on Russian PaaS providers.

### Amvera Cloud (Example)
1.  Create a project in Amvera.
2.  Push this code to the Amvera git repository.
3.  Add a PostgreSQL database in the Amvera dashboard.
4.  Set the `DATABASE_URL` environment variable in Amvera settings to point to your internal Amvera Postgres DB.

### Timeweb Cloud / Yandex Cloud
1.  Create a VM or App Service.
2.  Install Node.js and PostgreSQL (or use Managed PostgreSQL).
3.  Clone the repo, install deps, and run `npm start`.

## API Endpoints

*   `POST /api/register`: Register a new user `{ username, password }`.
*   `POST /api/login`: Login `{ username, password }`. Returns `{ token }`.
*   `GET /api/data`: Get user data (requires Auth header).
*   `POST /api/data`: Save user data (requires Auth header).
