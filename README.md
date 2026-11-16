# RBAC User Management

Full-stack user management system with JWT authentication and role-based access control. Three roles (Admin, Manager and User) determine which dashboards and operations each person can access.

![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)
![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?logo=sequelize&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-14-000000?logo=nextdotjs&logoColor=white)

## Features

- JWT login with bcrypt password hashing
- Role-based authorization (Admin, Manager, User)
- User CRUD restricted to administrators
- Registration restricted to Admin and Manager
- Protected routes on the client (`AuthContext` + `ProtectedRoute`)
- Form validation with React Hook Form and Zod

## Architecture

```
├── backend/                 Express REST API (port 5000)
│   ├── app.js
│   ├── config/              Sequelize + SQLite connection
│   ├── middlewares/         JWT authentication
│   ├── models/              User model
│   └── routes/              /auth and /user
└── frontend/                Next.js 14 (App Router)
    └── app/
        ├── login/  register/  profile/  admin/
        └── components/  context/  utils/
```

## API

| Method | Route | Access | Description |
|---|---|---|---|
| POST | `/auth/login` | Public | Authenticate and return a token |
| POST | `/auth/register` | Admin, Manager | Create a user |
| GET | `/auth/user` | Authenticated | Current user |
| GET | `/user/users` | Admin | List users |
| PUT | `/user/users/:id` | Admin | Update a user |
| DELETE | `/user/users/:id` | Admin | Delete a user |
| GET | `/user/dashboard`, `/user/gestor`, `/user/admin` | By role | Dashboards |

## Getting started

**Backend**

```bash
cd backend
cp .env.example .env      # set JWT_SECRET_KEY
npm install
npm start                 # http://localhost:5000
```

**Frontend**

```bash
cd frontend
npm install
npm run dev               # http://localhost:3000
```

Set `API_BASE_URL` in `frontend/app/config/config.js` to `http://localhost:5000` when running locally.
