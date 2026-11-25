# JobShield — Vercel deployment

This package is prepared for Vercel's native Flask/Python deployment.

## Deploy from GitHub

1. Upload the **contents** of this folder to the root of your GitHub repository
   (not the ZIP file and not an extra nested `JobShield/` folder).
2. In Vercel, choose **Add New → Project**, import the GitHub repository,
   and click **Deploy**. Vercel detects the Flask app from the root `app.py`.
3. No custom Build Command or Output Directory is required. Vercel installs
   dependencies from `requirements.txt`.

## Important limitations

- Scan history uses SQLite at `/tmp/jobshield.sqlite3`. Vercel function storage is
  temporary and instance-local; history may disappear or differ between instances.
  Use a managed database for persistent shared history.
- PDF reports are generated in memory for download.
- URL fetching may fail for sites that block automated requests, require JavaScript,
  login, or CAPTCHA, or take longer than the platform's function time limit.
- The risk score is heuristic, not proof of fraud or employer legitimacy.
- This is an academic prototype. Add rate limiting, monitoring, stronger abuse
  controls, and a security review before production use.

## Local run

Install requirements and run `python app.py`; open http://127.0.0.1:5000.
