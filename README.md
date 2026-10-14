# School Management System (SLMS)

A school administration web app (2018) built with **Node.js / Express**, **MongoDB**
and **AngularJS 1.x**. It covers the "super admin" setup side of a school system:
branches, academic years, courses, staff, and role-based permissions.

## Features

- Log in / log out, with sessions stored in files (`express-session` + `session-file-store`)
- **School branches**: add and manage campuses
- **Academic years** and **periods**
- **Courses** and **qualifications**
- **Staff leave types**
- **Users**, plus **profiles** (roles) with per-action permissions through
  [`acl`](https://www.npmjs.com/package/acl) on a MongoDB backend

## Layout

```
app.js             Express server: login/session, permissions, mounts all routes (port 8000)
routes/            REST routes per resource (/branches, /years, /courses, /users, …)
controllers/       request handlers
models/            Mongoose schemas
utils/permissions.js   list of actions that can be granted to a profile
public/            AngularJS single-page front end (index.html, js/controllers, partials/)
```

## Running it

Needs Node.js and a MongoDB server on `localhost` (database `slms_db`).

```
npm install
node app.js
```

Open http://localhost:8000. On first start the app creates a demo admin login:
`admin@school.com` / `1234`.

**Known issue:** `app.js` requires `./routes/configRoutes.js`, which was never
committed, so the server won't start until you remove the `/config` route lines
or add that file.

## Status

Unmaintained student project, kept for reference. Not production-ready:
passwords are stored and compared in plain text, the session secret is
hard-coded, and the session cookie never expires.

## Credits

Built by Musab Hussain, Muhammad Abeer and Ali Raza Khan. It started at
`abeersaqib/SLMS-CC`.
