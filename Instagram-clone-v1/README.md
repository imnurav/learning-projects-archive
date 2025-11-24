# Instagram Clone (v1)

A lightweight Instagram-like clone built with Next.js, Tailwind CSS, Firebase, and NextAuth for authentication. This project is intended as a learning/demo project showcasing core features like user authentication (Google), uploading posts, stories, basic feeds, and responsive UI.

**Status:** Prototype / Learning project — not production hardened.

**Live demo:** Local only (no public demo provided). You can run it locally following the instructions below.

**Screenshots:** Add screenshots to `public/` and reference them here for a better README.

**Table of contents**
- **Features**
- **Tech Stack**
- **Prerequisites**
- **Environment Variables**
- **Installation & Setup**
- **Firebase setup**
- **NextAuth (Google) setup**
- **Running the app**
- **Project structure**
- **Scripts**
- **Troubleshooting**
- **Contributing**
- **License**

**Features**
- Google sign-in (NextAuth)
- Firebase Firestore for posts and user data
- Firebase Storage for images
- Responsive feed, posts, stories, suggestions, profile preview
- Upload modal for creating posts

**Tech Stack**
- Frontend: `Next.js` (React) + `Tailwind CSS`
- Authentication: `next-auth` (Google provider)
- Backend / Database: `Firebase` (Firestore + Storage)

**Prerequisites**
- Node.js (v16 or later recommended)
- npm or yarn
- Firebase account
- Google Cloud project for OAuth credentials (for NextAuth Google provider)

**Environment Variables**
Create a `.env.local` file in the project root (or set the variables in your hosting environment). Do NOT commit secrets to git.

Example `.env.local` (replace values with yours):

```env
GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=your-google-client-secret
NEXT_PUBLIC_FIREBASE_API_KEY=your-firebase-api-key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your-firebase-auth-domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your-firebase-project-id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your-firebase-storage-bucket
NEXT_PUBLIC_FIREBASE_MESSAGE_SENDER_ID=your-firebase-messaging-sender-id
NEXT_PUBLIC_FIREBASE_APP_ID=your-firebase-app-id
SECRET=some-random-secret-for-nextauth
```

- Use `NEXT_PUBLIC_*` for values required in the browser.
- For production deployments (e.g., Vercel) configure these in the hosting UI rather than committing.

I found these env variable names in the project; keep the same keys above when creating your `.env.local`.

**Installation & Setup**
1. Clone the repo and change into the folder:

```bash
git clone <repo-url>
cd Instagram-clone-v1
```

2. Install dependencies:

```bash
npm install
# or
yarn install
```

3. Create `.env.local` using the variables shown above.

4. Configure Firebase and Google OAuth as described below.

**Firebase Setup**
1. Go to the Firebase Console and create a new project (or use an existing one).
2. In Project settings -> General -> Add app -> Web, register a web app and copy the Firebase config.
3. Put the values into your `.env.local` as `NEXT_PUBLIC_FIREBASE_*` variables.
4. Enable Authentication -> Sign-in method -> Google and configure an OAuth client ID (see NextAuth setup below).
5. Create a Firestore database (start in test mode for development) and a Storage bucket.

Recommended minimal security rules (for dev only):
- Use test rules while developing. Lock down before production.

**NextAuth (Google) setup**
1. In Google Cloud Console, create OAuth 2.0 credentials (OAuth client ID) for a Web application.
2. Configure authorized redirect URIs:
   - Local dev: `http://localhost:3000/api/auth/callback/google`
   - Production: `https://<your-domain>/api/auth/callback/google`
3. Add the `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` to your `.env.local`.
4. Set `SECRET` in `.env.local` to a random long string (used by NextAuth).

**Running the app**
- Development:

```bash
npm run dev
# or
yarn dev
```

Open `http://localhost:3000`.

- Build for production:

```bash
npm run build
npm run start
```

**Project structure (important files)**
- `firebase.js` : Firebase initialization and helpers.
- `pages/_app.js` : Next.js app wrapper.
- `pages/api/auth/[...nextauth].js` : NextAuth configuration.
- `pages/index.js` : Main feed / home page.
- `pages/auth/signin.js` : Custom sign-in page.
- `pages/api/*` : API routes used by the app.
- `components/` : UI components (`Feed.js`, `Header.js`, `Post.js`, `UploadModal.js`, etc.).
- `styles/globals.css` : Tailwind and global CSS.

**Scripts**
- `dev` : Run development server (`next dev`).
- `build` : Build the app for production (`next build`).
- `start` : Start the production server (`next start`).

Check `package.json` for exact script names.

**Troubleshooting**
- Google sign-in fails: ensure OAuth credentials are correct and the Authorized redirect URI matches.
- Missing Firebase data: verify your `NEXT_PUBLIC_FIREBASE_*` values and that Firestore/Storage rules allow reads/writes in dev.
- Images not uploading: confirm Firebase Storage bucket name and permissions.
- App shows white screen: check the browser console and server logs for runtime errors (often missing env vars).

**Deployment**
- Vercel is recommended for Next.js projects. Add the same env variables in Vercel Project Settings.
- Set `NEXT_PUBLIC_*` values and `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, `SECRET` in Vercel.

**Contributing**
- This is a personal/learning project. Feel free to open issues or PRs if you'd like to contribute additions or fixes.

**License**
- MIT — see LICENSE file if included in the repository.

---

If you want, I can also:
- create a `.env.example` file with placeholders,
- add a short `screenshots/` folder and update README with images,
- or set up a simple `firebase.rules` sample for Firestore/Storage.

If you'd like any of those, tell me which and I'll add them.
This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
