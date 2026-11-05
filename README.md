# TripNest — Project Review 2 Starter

A React + Vite travel booking demo with separate Admin and User modules, Local Storage persistence, and Vercel SPA routing.

## 1. Requirements

- Node.js 20.19+ or 22.12+
- VS Code (recommended)
- Internet connection for Google Fonts and the sample travel photos

## 2. Run the project

Open this folder in VS Code. Open Terminal → New Terminal and run:

```bash
npm install
npm run dev
```

Open the local URL printed in the terminal (normally `http://localhost:5173`).

Before deployment, check that this succeeds:

```bash
npm run build
```

## 3. Demo accounts

| Module | Email | Password |
|---|---|---|
| Admin | `admin@tripnest.demo` | `admin123` |
| User | `user@tripnest.demo` | `user123` |

New signups are always assigned the `user` role. Admin users are pre-seeded for the project demonstration.

## 4. Review demonstration flow

1. Open the home page and point out the public travel catalogue.
2. Log in as the demo user. Open User Dashboard.
3. Book a tour, enter a travel date in `YYYY-MM-DD` format, and choose 1–10 travellers.
4. Show the new booking under **My bookings** with `Pending` status.
5. Log out and log in as the demo admin.
6. Open Admin Panel. Add or edit a tour package.
7. Find the user booking and change its status to `Confirmed` or `Cancelled`.
8. Log back in as the user to show the booking status update.
9. Show the deployed Vercel URL and refresh a nested route such as `/user` or `/admin`.

## 5. Local Storage used

- `tripnest_users_v1`: demo user records
- `tripnest_session_v1`: current signed-in user (does not include the password)
- `tripnest_tours_v1`: tour catalogue
- `tripnest_bookings_v1`: booking requests and statuses

To reset the demo data, open browser DevTools → Application → Local Storage → your localhost/Vercel origin and delete the four `tripnest_*` keys, then refresh.

## 6. Important security note

This is a classroom demonstration of Local Storage authentication because the assignment explicitly asks for it. It is **not production authentication**: browser Local Storage can be inspected and modified, and demo passwords are stored in plain text. A real travel booking service needs a backend, a database, server-side authorization, and properly hashed passwords. Do not use real customer data or real passwords in this demo.

## 7. Bring your existing website design into this project

1. Copy your existing images into `public/images/` and reference them as `/images/your-file.jpg`.
2. Transfer reusable CSS into `src/styles.css` (or create separate CSS files and import them from the related component).
3. Convert each old page into a React component under `src/pages/`.
4. In JSX, change `class` to `className`, `for` to `htmlFor`, close all tags, and use `onClick` instead of `onclick`.
5. Replace direct DOM manipulation (`document.querySelector`, `innerHTML`, etc.) with React state (`useState`) and event handlers.
6. Keep the authentication, booking and role-protection logic from this starter, then merge your existing visual sections into `Home.jsx`.

## 8. Deploy to Vercel

1. Create a new GitHub repository and push this project folder.
2. Sign in to Vercel and choose **Add New → Project**.
3. Import the GitHub repository.
4. Confirm the settings:
   - Framework Preset: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Install Command: `npm install`
5. Click **Deploy**.
6. Open the deployed URL. Test signup, login, role restrictions, booking, admin status changes, and refresh `/user` and `/admin` directly.

The included `vercel.json` sends application routes back to `index.html`, so React Router routes can load on direct navigation and refresh.

## 9. Project structure

```text
travel-agency-review/
├── public/
├── src/
│   ├── components/
│   │   ├── ProtectedRoute.jsx
│   │   └── SiteLayout.jsx
│   ├── context/
│   │   └── AuthContext.jsx
│   ├── lib/
│   │   └── storage.js
│   ├── pages/
│   │   ├── AdminDashboard.jsx
│   │   ├── Home.jsx
│   │   ├── Login.jsx
│   │   ├── Signup.jsx
│   │   └── UserDashboard.jsx
│   ├── App.jsx
│   ├── main.jsx
│   └── styles.css
├── index.html
├── package.json
├── vercel.json
└── vite.config.js
```
