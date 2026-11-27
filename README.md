# Smart Patient Monitoring System (BT209)

IoT-based patient monitoring dashboard for a CSE course project (Project No. 407), mentored by Ms. Aina Mehta.
This phase is **frontend only**: vitals are simulated in the browser, so it runs with no hardware and no backend.

## Features
- Doctor sign in (Dr. Ayush Sahu)
- Live ward overview: heart rate, SpO₂, temperature, blood pressure, respiratory rate, updated every 2 seconds
- Automatic warning and critical alerts with acknowledge
- Admit patient form with validation, emergency contact, allergies, bed choice and first medication
- Patient page: live chart, medication checklist, clinical notes, profile, discharge
- Bed map across General Ward, Cardiac Care and ICU
- Data saved in the browser (localStorage); "Reset demo" restores the sample patients

## Demo login
- Username: `ayush.sahu`
- Password: `doctor123`

## Run locally
```bash
npm install
npm run dev        # http://localhost:5173
npm run build      # production build in dist/
```
Requires Node 18 or newer.

## Deploy on GitHub Pages
1. Create a new GitHub repository and push this folder to its `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Smart Patient Monitoring System"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. In the repository go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. The workflow in `.github/workflows/deploy.yml` builds and publishes on every push.
   Your site appears at `https://<your-username>.github.io/<repo-name>/`.

Routing uses `HashRouter` and Vite uses a relative base, so no repo-name configuration is needed.

## Stack
React 18, Vite, Tailwind CSS 3, React Router, Recharts, Axios, Socket.IO Client.

## Next phase (backend)
Node.js/Express, MongoDB, MQTT broker and Socket.IO. The integration point is `src/services/api.js`:
set `USE_MOCK = false`, point `VITE_API_URL` at the server, and emit `vitals` events shaped
`{ patientId, hr, spo2, temp, sys, dia, rr }`.

## Disclaimer
Academic project with simulated data. Not for clinical use.
