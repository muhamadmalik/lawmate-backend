# Law Mate - Backend Server

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js CI](https://github.com/your-username/law-mate-backend/actions/workflows/node.js.yml/badge.svg)](https://github.com/your-username/law-mate-backend/actions/workflows/node.js.yml)

This repository contains the backend server for **Law Mate**, a platform designed to connect clients seeking legal assistance with qualified lawyers. It handles user authentication, profile management, appointment booking, payment processing, and all core business logic.

---

## Table of Contents

- [About The Project](#about-the-project)
- [Key Features](#key-features)
- [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Folder Structure](#folder-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## About The Project

Law Mate is a two-sided marketplace for legal services. This backend provides a robust and scalable foundation using Node.js, Express, and PostgreSQL. It exposes a RESTful API for client-side applications (web and mobile) to consume.

### Key Features

- **Dual Role System:** Separate logic and endpoints for `Clients` and `Lawyers`.
- **Secure Authentication:** JWT-based authentication with password hashing and OTP verification.
- **Comprehensive Lawyer Profiles:** Lawyers can manage their experience, education, specializations, services, pricing, and availability.
- **Advanced Search & Filtering:** Clients can find the perfect lawyer based on various criteria.
- **Appointment Lifecycle Management:** End-to-end booking, approval, and status tracking.
- **Integrated Wallet System:** Lawyers can track earnings and request payouts.
- **Content Management:** Lawyers can publish articles to showcase their expertise.

### Built With

*   [Node.js](https://nodejs.org/) - JavaScript runtime environment
*   [Express.js](https://expressjs.com/) - Web framework for Node.js
*   [PostgreSQL](https://www.postgresql.org/) - Advanced open-source relational database
*   [Sequelize](https://sequelize.org/) / [Prisma](https://www.prisma.io/) - ORM for Node.js
*   [JSON Web Token (JWT)](https://jwt.io/) - For secure authentication
*   [Bcrypt.js](https://www.npmjs.com/package/bcryptjs) - For password hashing
*   [Joi](https://joi.dev/) / [express-validator](https://express-validator.github.io/docs/) - For request validation

---

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Make sure you have the following software installed on your system:
*   **Node.js** (v16 or higher): [Download Node.js](https://nodejs.org/en/download/)
*   **npm** or **yarn**:
    ```sh
    npm install npm@latest -g
    ```
*   **PostgreSQL**: [Download PostgreSQL](https://www.postgresql.org/download/)
*   **Git**: [Download Git](https://git-scm.com/downloads)

### Installation

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/your-username/law-mate-backend.git
    cd law-mate-backend
    ```

2.  **Install NPM packages:**
    ```sh
    npm install
    ```

3.  **Set up environment variables:**
    Create a `.env` file in the root of the project by copying the example file.
    ```sh
    cp .env.example .env
    ```
    Now, open the `.env` file and fill in the required values, especially your database connection details.

    ```dotenv
    # Application Port
    PORT=5000

    # PostgreSQL Database Connection URL
    DATABASE_URL=postgres://YOUR_DB_USER:YOUR_DB_PASSWORD@localhost:5432/lawmate_db

    # JWT Configuration
    JWT_SECRET=your_super_secret_key_for_jwt
    JWT_EXPIRES_IN=7d

    # CORS Origin
    CORS_ORIGIN=http://localhost:3000

    # Payment & OTP Service Credentials (Optional, for specific features)
    PAYMENT_GATEWAY_KEY=
    PAYMENT_GATEWAY_SECRET=
    TWILIO_ACCOUNT_SID=
    TWILIO_AUTH_TOKEN=
    TWILIO_PHONE_NUMBER=
    ```

4.  **Database Setup:**
    *   Ensure your PostgreSQL server is running.
    *   Connect to PostgreSQL and create the database specified in your `.env` file.
        ```sql
        CREATE DATABASE lawmate_db;
        ```
    *   Run the database migrations to create all the tables. (This command assumes you are using an ORM like Sequelize or Prisma).
        ```sh
        # For Sequelize
        npx sequelize-cli db:migrate

        # For Prisma
        npx prisma migrate dev
        ```
    *   (Optional) Run the seeders to populate the database with initial data (like specializations).
        ```sh
        # For Sequelize
        npx sequelize-cli db:seed:all

        # For Prisma
        npx prisma db seed
        ```

---

## Usage

Once the installation and setup are complete, you can run the server.

*   **For development (with automatic reloading):**
    ```sh
    npm run dev
    ```
    The server will start on the port specified in your `.env` file (e.g., `http://localhost:5000`).

*   **For production:**
    ```sh
    npm start
    ```

---

## API Documentation

For a detailed overview of all available API endpoints, including request/response examples and authentication requirements, please refer to our full **[API Documentation](./DOCUMENTATION.md)**.

Alternatively, you can import the provided Postman collection (`LawMate.postman_collection.json`) to test the endpoints directly.

---

## Folder Structure

The project follows a modular structure to keep the codebase organized and maintainable.

```
law-mate-backend/
├── src/
│   ├── api/
│   │   ├── routes/          # Route definitions (e.g., auth.routes.js)
│   │   └── controllers/     # Request/response logic (e.g., auth.controller.js)
│   ├── config/              # Database connection, environment vars
│   ├── middleware/          # Custom middleware (e.g., auth.middleware.js)
│   ├── models/              # Sequelize/Prisma model definitions
│   ├── services/            # Business logic (e.g., payment.service.js)
│   ├── utils/               # Helper functions
│   └── app.js               # Express app setup
├── .env.example             # Example environment file
├── package.json
└── server.js                # Server entry point
```

---

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

---

## License

Distributed under the MIT License. See `LICENSE` for more information.

---
