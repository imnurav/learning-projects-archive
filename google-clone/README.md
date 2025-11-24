# Google Clone

>A small Google Search UI clone built with Next.js. This project demonstrates a simple search interface, server-side fetching of Google Custom Search results, and rendering of web and image results.

**Status:** Learning / demo project.

**Live demo:** Local only.

**Table of contents**
- Features
- Tech stack
- Prerequisites
- Environment variables
- Installation & running
- Google Custom Search setup
- Project structure
- Scripts
- Troubleshooting
- Contributing
- License

## Features
- Search input and results page
- Web and Image results (switch using `searchType=image`)
- Server-side fetching of search results via Google Custom Search API
- Simple, responsive UI built with Tailwind CSS and Heroicons

## Tech stack
- Next.js
- React
- Tailwind CSS
- NextAuth (present in dependencies — optional for authentication)
- Google Custom Search API

## Prerequisites
- Node.js (v16+ recommended)
- Yarn or npm
- A Google account to set up a Custom Search Engine and API key

## Environment variables
Create a `.env.local` file at the project root (do NOT commit secrets). This project reads the following variables in `pages/search.js`:

```env
API_KEY=your-google-api-key
CONTEXT_KEY=your-custom-search-engine-id
```

- `API_KEY` — Google API key with Custom Search API enabled.
- `CONTEXT_KEY` — the Custom Search Engine ID (cx) for your search engine.

If you plan to add authentication (NextAuth) later, you'll also need provider-specific env vars and a `SECRET`.

## Installation & running
1. Clone the repository and enter the folder:

```bash
git clone <repo-url>
cd GoogleClone
```

2. Install dependencies:

```bash
yarn
# or
npm install
```

3. Create `.env.local` with the `API_KEY` and `CONTEXT_KEY` values.

4. Run the development server:

```bash
yarn dev
# or
npm run dev
```

Open `http://localhost:3000` and perform a search.

## Google Custom Search setup
1. Go to Google Cloud Console and enable the **Custom Search API** for your project.
2. Create an API key under Credentials.
3. Create a Custom Search Engine (CSE) at https://cse.google.com/cse/ and configure it to search the entire web (or specific sites). Copy the Search Engine ID (cx) from the CSE control panel — this is your `CONTEXT_KEY`.
4. Place the API key and cx value into `.env.local`.

Notes:
- The free Google Custom Search has usage limits; for heavy usage consider a paid plan or other search providers.

## Project structure (important files)
- `pages/search.js` — Search results page; server-side fetch happens in `getServerSideProps` and expects `API_KEY` & `CONTEXT_KEY`.
- `pages/index.js` — Home/search input (start from here to perform searches).
- `pages/api/*` — API routes (if present).
- `pages/components/` — UI components used by the search page (results, header, images, etc.).
- `Response.js` — (optional) contains a sample/mock response used for testing.
- `styles/` — Tailwind globals and custom styles.

## Scripts
- `dev` — run development server (`next dev`)
- `build` — build for production (`next build`)
- `start` — start production server (`next start`)
- `lint` — run linter (`next lint`)

Check `package.json` for the complete list.

## Troubleshooting
- If results are empty or you see API errors, verify `API_KEY` and `CONTEXT_KEY` are correct and that the Custom Search API is enabled on your Google Cloud project.
- If you see quota errors, check your API usage in Google Cloud Console and consider increasing quota or using the mock response for development.
- Typos in file imports (components) can cause runtime errors — check console and server logs for stack traces and file paths.

## Contributing
PRs welcome — this is a learning project. For larger changes, open an issue first to discuss.

## License
MIT

---
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
