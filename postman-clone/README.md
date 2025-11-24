# PostMaster (Postman Clone)

A lightweight, browser-based API requester inspired by Postman — built with plain HTML, Bootstrap and vanilla JavaScript. Useful for quick testing of HTTP endpoints while learning how requests and responses work.

**Status:** Demo / learning project

---

## Features
- Build and send HTTP GET and POST requests from the browser
- Send request body as raw JSON or as custom key/value parameters
- Add and remove custom parameters dynamically
- View response text in the UI

## Tech stack
- HTML
- Bootstrap 4 (CDN)
- Vanilla JavaScript (ES6+)

## Getting started

No build step or Node.js required — this is a static app. Two simple ways to run it locally:

1) Open directly in the browser (quick):

 - Double-click `index.html` or open it in your browser. Some APIs may block requests due to CORS when loaded from the `file://` protocol.

2) Serve over a local HTTP server (recommended):

```bash
# Using Python 3 (served at http://0.0.0.0:8000)
python3 -m http.server 8000

# Or with Node.js 'serve' (if installed):
npx serve . -l 3000
```

Then open `http://localhost:8000` (or the port you chose).

## How to use
1. Enter the target URL in the **URL** field (e.g. `https://jsonplaceholder.typicode.com/posts`).
2. Choose the **Request Type**: `GET` or `POST`.
3. Choose **Content Type**:
   - `JSON` — paste raw JSON into the text area.
   - `Custom Parameters` — click **+** to add key/value pairs.
4. Click **Submit**. The response body (as text) will appear in the **Response** area.

Example POST using JSON (to test locally):

```
URL: https://jsonplaceholder.typicode.com/posts
Request Type: POST
Content Type: JSON
Request JSON:
{
  "title": "foo",
  "body": "bar",
  "userId": 1
}
```

Example using custom params: toggle **Custom Parameters**, add keys `title`, `body`, `userId` and submit as a POST — the app will stringify parameters into JSON for the request body.

## CORS / Common issues
- Many public APIs block cross-origin requests from browsers unless they explicitly allow your origin. If requests fail with CORS errors in the browser console, try:
  - Using a server-side proxy or a CORS proxy such as `https://cors-anywhere.herokuapp.com/` (for quick testing only).
  - Hitting public test APIs that allow cross-origin requests (e.g. `jsonplaceholder.typicode.com`).
  - Serving the app via a local server (not `file://`) — some browsers treat CORS differently for file protocol.

## File overview
- `index.html` — main UI and markup (includes Bootstrap via CDN)
- `index.js` — request builder logic, add/remove params, and fetch handling

## Extending the app (ideas)
- Add support for additional HTTP methods (PUT, PATCH, DELETE, HEAD)
- Add headers editor (custom request headers)
- Display response status code, headers, and pretty-printed JSON with syntax highlighting
- Save and load request collections to localStorage
- Add authentication helpers (Bearer token input, Basic auth)

## Troubleshooting
- Blank response / network error: check browser console (F12) for CORS or network errors.
- Responses appear as HTML or not as JSON: the app displays response text — if you want formatted JSON, add a pretty-print step or integrate Prism.js (commented out in the HTML).

## Contributing
PRs and suggestions are welcome — this is a small demo project. Open an issue first for larger changes.

## License
MIT