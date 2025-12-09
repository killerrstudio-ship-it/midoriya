
MIDORIYA IMPERIAL — Full AAA website package
===========================================

What's included:
- static site pages (index.html, navigation.html, rules.html, commands.html, applications.html, support.html, partners.html, news.html, founders.html)
- assets/ (banners, logos)
- api/ (serverless endpoints for Vercel: apply.js, support.js) - these forward form submissions to Discord webhooks if environment variables are set
- package.json (for local dev)
- README (this file)

How to deploy to Vercel (recommended):
1. Install Vercel CLI (optional): npm i -g vercel
2. Create a Vercel account and login: vercel login
3. From this folder, run: vercel
   - Choose scope and confirm. Vercel will detect the static site and serverless functions under /api.
4. Set environment variables in Vercel dashboard for the project:
   - DISCORD_WEBHOOK_APPLICATIONS  (Discord webhook URL for application submissions)
   - DISCORD_WEBHOOK_SUPPORT       (Discord webhook URL for support tickets)
   - OPTIONAL: ADMIN_EMAIL for admin notifications
5. After deploy, your site will be live at https://your-project.vercel.app

Local testing (Node):
- You can run a local test server for static files using any static server (e.g., serve or live-server).
- API endpoints are serverless; for local testing, use 'vercel dev' to emulate the serverless functions.

Editing the site:
- Open files in the project root with any editor (VSCode recommended).
- CSS is in css/style.css, JS in js/script.js.
- To change founders, edit the anchors in founders.html.
- To change branding images, replace files in assets/ (banner1.png, banner2.png, eye_logo.png).

How forms work:
- Applications form posts JSON to /api/apply
- Support form posts JSON to /api/support
- The serverless functions will read env vars DISCORD_WEBHOOK_APPLICATIONS and DISCORD_WEBHOOK_SUPPORT and forward payloads to those URLs
- If webhooks are not set, submissions will be stored in /data/*.json (for local testing).

Security notes:
- Never commit real Discord webhook URLs into version control. Use Vercel environment variables.
