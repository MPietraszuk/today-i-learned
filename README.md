# Today I Learned (React + Supabase)

A small “Today I Learned” app built with **React** and **Supabase**.

This project originally started with **Create React App (CRA)**, but was refactored to **Vite** after running into tooling/version conflicts (details below).

---

##### Why I migrated from CRA → Vite

This project was initially scaffolded as a CRA app, but I hit multiple issues:

- `react-scripts` was missing / broken (installed as `react-scripts@0.0.0`)
- CRA (react-scripts v5) is not a great match for **React 19** and newer Node versions
- My environment was running a modern Node/NPM combo, and CRA tooling became the bottleneck

To keep React 19 and get a reliable dev server/build pipeline, I migrated to **Vite**, which is lighter, faster, and plays nicely with current React + Node.

---

##### Tech Stack

- **React** (React 19)
- **Vite** (dev server + bundler)
- **Supabase** (Postgres + API)

---

##### Running the App Locally

Follow these steps to download and run the project on your own machine.

##### Prerequisites

Make sure you have the following installed:

- **Node.js** (v18+ recommended)
- **npm** (comes with Node)
- A **Supabase account** (free tier is fine)

You can verify Node and npm with:

```
bash
node -v
npm -v
```

##### 1) Clone the repository

> git clone https://github.com/YOUR_USERNAME/today-i-learned.git
> cd today-i-learned

##### 2) Install dependencies

> bash
> npm install

##### 3) Configure Supabase environment variables

Create a `.env` file in the project root:

> bash
> VITE_SUPABASE_URL="https://YOUR_PROJECT_ID.supabase.co"
> VITE_SUPABASE_ANON_KEY="YOUR_PUBLIC_ANON_KEY"

⚠️ Important
Vite only exposes environment variables prefixed with VITE*.
Using `REACT_APP*\*` (CRA style) will not work.

You can find these values in the Supabase dashboard:

Settings → API → Project URL

Settings → API → anon public key

##### 4) Run the development server

> npm run dev

Vite will start the dev server and print a local URL, typically:

> http://localhost:5173

Open that URL in your browser.

##### 5) Build for production (optional)

> npm run build

To preview the production build locally:

> bash
> npm run preview

##### Using the App

Viewing Facts

- When the app loads, it fetches a list of “facts” from Supabase

- Facts are displayed immediately without needing to sign in

##### Adding a New Fact

- Enter the fact text

- Select a category (if applicable)

- Submit the form

- The new fact is saved to the Supabase database and appears in the list

**Note:** Inserts work because Row Level Security (RLS) policies allow public inserts.

##### Updating Facts

- Facts can be updated directly in the UI (depending on enabled features)

- Updates are permitted via Supabase RLS policies

This is intentionally permissive for learning/demo purposes.
In a production app, updates would typically be restricted to authenticated users or content owners.

##### Data Persistence

- All data is stored in a Supabase Postgres database

- Refreshing the page does not reset the data

- Changes are reflected immediately for all users

##### Notes on Security & Scope

This project is intentionally simple and educational:

- Public read/write access is enabled via Supabase RLS

- No authentication is required

- No admin role or moderation workflow is implemented

These tradeoffs were made to:

- Focus on React + Vite tooling

- Learn Supabase RLS concepts

- Avoid scope creep for an MVP

##### Possible Future Enhancements

- User authentication (Supabase Auth)

- Per-user fact ownership

- Voting or likes

- Moderation / approval flow

- Pagination and filtering

- Improved validation and error handling

##### Summary

This project demonstrates:

- Migrating from Create React App → Vite

- Running modern React (19) with a fast dev setup

- Using Supabase as a backend with Row Level Security

- Building a small but complete full-stack React app
