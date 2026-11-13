VerifAI web version - deploy guide

Files: index.html, style.css, app.js, manifest.webmanifest, icons. No build step.
Backend: https://verifai-backend-59h5.onrender.com (already deployed, route POST /assess).

IMPORTANT - CORS (do this first or the site will show "Something went wrong"):
In your backend (Node/Express) make sure CORS allows your website:
    const cors = require("cors");   // npm i cors
    app.use(cors());                // or cors({ origin: "https://YOUR-SITE-URL" })
Redeploy the backend on Render after changing it.

Deploy the site (pick one, ~5 minutes):
A) Render: New > Static Site > connect a GitHub repo with these files. Build command: empty. Publish directory: .
B) Netlify Drop: drag the folder to app.netlify.com/drop
C) GitHub Pages: push files, Settings > Pages.

Test: open the link on a phone, type a claim, press "Assess claim".
Add to home screen: Chrome menu > Add to Home screen (iPhone: Share > Add to Home Screen).
First request can take up to a minute on Render free tier (server sleeping).
