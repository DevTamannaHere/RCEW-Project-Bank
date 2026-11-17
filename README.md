# RCEW Project Bank

A web platform for students of **Rajasthan College of Engineering for Women (RCEW)** to upload, browse and discover academic projects in one place, with a faculty validation workflow.

## Features

- **Student registration and login** with roll-number validation (format like `23ERWCS029`)
- **Upload projects** with title, description, department, year, category, level, tags, supervisor, collaborators, GitHub repo and deploy link
- **Browse and search** projects, filtered by year, department and category, sorted by recent, popular, rating or year
- **Project details page** with view counts and 1 to 5 star ratings
- **Faculty validation** status for each project (pending, approved or disapproved) with comments
- **Dashboard stats** by year, department and category
- **User profile** with photo, GitHub and Gmail links, and an edit-profile page
- **Light and dark theme**, responsive layout

## Tech Stack

| Layer      | Technology                                                    |
|------------|---------------------------------------------------------------|
| Frontend   | React 18, TypeScript, Vite, React Router, TanStack Query      |
| UI         | Tailwind CSS, Radix UI (shadcn/ui components), Framer Motion  |
| Backend    | Node.js, Express, Zod                                         |
| Testing    | Vitest                                                        |
| Deployment | Render (`render.yaml`) and Netlify (`netlify.toml`)           |

## Project Structure

```
RCEW-Project-Bank/
├── client/             # React app (pages, components, hooks)
│   ├── pages/          # Index, Browse, Upload, ProjectDetails, Login, Register, Profile...
│   ├── components/     # ProtectedRoute, ThemeToggle, UserProfile, ui/ (shadcn)
│   └── hooks/          # use-auth and other hooks
├── server/             # Express API
│   ├── routes/         # auth.ts, projects.ts
│   └── models/         # Data models (not used yet)
├── shared/             # TypeScript types shared by client and server
└── public/             # Static assets
```

## Getting Started

### Prerequisites

- Node.js 18 or higher
- npm

### Installation

```bash
git clone https://github.com/tamannayadav04/RCEW-Project-Bank.git
cd RCEW-Project-Bank
npm install
```

### Environment variables

Create a `.env` file in the project root. Do not commit real secrets.

```
PING_MESSAGE=ping
```

### Run in development

```bash
npm run dev
```

The app runs at `http://localhost:8080` (or the port Vite prints in the terminal).

### Build and run for production

```bash
npm run build
npm start
```

### Other scripts

| Command             | Purpose                  |
|---------------------|--------------------------|
| `npm test`          | Run Vitest tests         |
| `npm run typecheck` | TypeScript type check    |
| `npm run format.fix`| Format code with Prettier|

## API Endpoints

| Method | Endpoint                              | Description                     |
|--------|---------------------------------------|---------------------------------|
| POST   | `/api/auth/register`                  | Register a student              |
| POST   | `/api/auth/login`                     | Log in                          |
| GET    | `/api/auth/profile`                   | Get profile                     |
| POST   | `/api/auth/upload-photo`              | Upload profile photo            |
| GET    | `/api/projects`                       | List projects (search, filters) |
| GET    | `/api/projects/:id`                   | Get one project                 |
| POST   | `/api/projects`                       | Create a project                |
| PUT    | `/api/projects/:id`                   | Update a project                |
| POST   | `/api/projects/:id/view`              | Record a view                   |
| POST   | `/api/projects/:id/rate`              | Rate a project                  |
| POST   | `/api/projects/:id/faculty-validation`| Approve or disapprove a project |
| GET    | `/api/projects/stats`                 | Project statistics              |
| GET    | `/api/projects/years`                 | Available years                 |

## Current Status

This is a work in progress.

- The API currently stores users and projects **in memory**, so data resets when the server restarts.
- Authentication is a placeholder: passwords are not hashed and a real JWT is not issued yet.

## Roadmap

- [ ] Add persistent storage for users and projects
- [ ] Hash passwords with bcrypt and issue real JWTs
- [ ] File uploads for project documentation and source code
- [ ] Faculty and admin roles
- [ ] Add screenshots

## Author

**Tamanna Yadav**
B.Tech CSE, Rajasthan College of Engineering for Women
