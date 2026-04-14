# Cedar Clinical Review Studio

Cedar Oaks Wellness Center — Admissions Clinical Decision Support Tool

Built on Cedar Oaks Training Guide 2025 criteria.

---

## Deploy to Vercel (Step-by-Step)

### Step 1 — Get your Anthropic API key
1. Go to https://console.anthropic.com
2. Click **API Keys** in the left sidebar
3. Click **Create Key**, name it "Cedar Clinical Review"
4. Copy the key — you'll need it in Step 4

### Step 2 — Push this folder to GitHub
1. Go to github.com and create a new repository called `cedar-clinical-review`
2. Make it **Private**
3. On your computer, open Terminal in this folder and run:
   ```
   git init
   git add .
   git commit -m "Initial Cedar Clinical Review Studio"
   git remote add origin https://github.com/YOUR_USERNAME/cedar-clinical-review.git
   git push -u origin main
   ```

### Step 3 — Connect to Vercel
1. Go to https://vercel.com and log in
2. Click **Add New Project**
3. Import your `cedar-clinical-review` repository
4. Leave all settings as default — Vercel will auto-detect Next.js
5. **Before clicking Deploy**, go to Step 4

### Step 4 — Add your API key to Vercel
1. On the deployment config screen, click **Environment Variables**
2. Add:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** (paste your key from Step 1)
3. Now click **Deploy**

### Step 5 — Share with your team
Once deployed, Vercel gives you a URL like `cedar-clinical-review.vercel.app`
Share that URL with your admissions team — everyone can use it with no login needed.

---

## Local Development

```bash
npm install
cp .env.example .env.local
# Edit .env.local and add your ANTHROPIC_API_KEY
npm run dev
```

Open http://localhost:3000

---

## How it works

- The frontend (pages/index.jsx) handles file uploads, form fields, and the UI
- When you click Analyze Case, it sends the documents to **/api/analyze** (your own server)
- The server (pages/api/analyze.js) calls the Anthropic API using your private API key
- The API key never touches the browser — it stays on the server

This means the tool works independently of your Claude.ai account and usage limits.

---

## Billing

You're billed directly through your Anthropic account at console.anthropic.com
Each case analysis uses approximately 2,000–6,000 tokens depending on document size.
At current Sonnet pricing this is roughly $0.02–$0.08 per analysis.
