# VerifAI — Deployment Guide

VerifAI consists of two parts:

- **Frontend:** A static web application built with HTML, CSS, and JavaScript.
- **Backend:** A Node.js and Express API deployed separately on Render.

## 1. Frontend Deployment

The frontend does not require a build step.

For a static hosting provider:

- Connect the frontend repository.
- Select Static Site as the deployment type.
- Leave the build command empty.
- Set the publish directory to the repository root.
- Deploy the application.

Main frontend files:

- `index.html`
- `style.css`
- `app.js`

## 2. Backend Deployment

The backend runs separately as a Node.js and Express service on Render.
The backend source is maintained in a separate private repository.

The API exposes:

`POST /assess`

Use the backend repository's deployment configuration and environment
variables when deploying the service.

## 3. CORS Configuration

The backend must allow requests from the deployed frontend origin.

Configure CORS to allow the frontend domain and the required HTTP methods
and headers. Avoid allowing unrestricted origins in a production deployment.

Example (Express):

```js
const cors = require("cors");

app.use(cors({
  origin: "https://YOUR-FRONTEND-URL",
  methods: ["POST"]
}));
```

Redeploy the backend after changing the CORS settings.

## 4. Testing the Deployment

After deployment:

1. Open the frontend.
2. Submit a sample health claim.
3. Check that the frontend can communicate with the backend.
4. Verify that assessment results and scientific source links are displayed.
5. Test the interface in both English and Arabic.

## 5. Free Hosting Considerations

On Render's free hosting tier, the backend may become inactive after a
period without requests.

The first request can take up to a minute while the service wakes up.

---

## Important Note

VerifAI is an educational screening prototype. Its results are not medical
advice, diagnosis, or treatment recommendations.
