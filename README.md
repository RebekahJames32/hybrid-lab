# 🧬 Hybrid Lab

A website where you pick an animal, pick a dinosaur, and watch the AI invent a brand-new hybrid creature with a unique name, description, and special abilities.

## 📁 What's in this folder

```
hybrid-lab/
├── index.html         ← the website (front page)
├── api/
│   └── hybrid.js      ← the tiny backend (talks to Claude AI safely)
├── package.json       ← project info
└── README.md          ← this file
```

## 🚀 How to publish it on the internet

We're going to use **Vercel** because it's free, fast, and built for exactly this kind of project. Total time: about 10 minutes.

### Step 1 — Get an Anthropic API key

1. Go to **https://console.anthropic.com**
2. Sign up or log in
3. Add a small amount of credit ($5 is plenty — each hybrid costs less than a tenth of a penny)
4. Go to **API Keys** in the menu and click **Create Key**
5. Copy the key (it starts with `sk-ant-...`) and save it somewhere safe — you'll only see it once

### Step 2 — Sign up for Vercel

1. Go to **https://vercel.com**
2. Click **Sign Up** (using GitHub is easiest, but email works too)
3. Free plan is fine — you don't need to upgrade

### Step 3 — Deploy the site

The easiest way (no Git or command line needed):

1. On Vercel, click **Add New → Project**
2. Look for the option to **upload a folder** (sometimes called "Import" or "Deploy")
3. Drag the entire `hybrid-lab` folder onto the page
4. Vercel will ask for a project name — type whatever you like (this becomes part of the URL)
5. **Before you click Deploy**, find the **Environment Variables** section and add:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** the key you copied in Step 1 (starts with `sk-ant-...`)
6. Click **Deploy** and wait about 30 seconds

That's it! Vercel will give you a URL like `https://hybrid-lab-caiden.vercel.app` and the site is live for anyone in the world to use.

> If you don't see a "drag and drop folder" option, the alternative is to push the folder to GitHub and connect that repo to Vercel — Vercel has a tutorial for this on their site.

### Step 4 — Test it!

Open the URL Vercel gave you, pick an animal and a dinosaur, and hit **Create Hybrid**. The AI should generate a fresh creature.

## 🛠️ Making changes later

If you want to add more animals, change colors, or update text:

1. Edit `index.html` on your computer
2. Go back to your Vercel project page
3. Click **Deployments → New Deployment** and re-upload the folder
4. (Or, if you set up GitHub, just push your changes and Vercel will redeploy automatically)

## 🔒 Why this setup is safe

The API key is stored on Vercel's servers as an "environment variable" — it never gets sent to anyone visiting the site. The website only talks to your own backend (`/api/hybrid`), and your backend is the only thing that knows the secret key. Even if someone views the page source code, they can't steal the key.

## 💸 How much does this cost?

- **Vercel hosting:** Free for personal projects (very generous limits)
- **Anthropic API:** Pay-as-you-go. Each hybrid creation costs roughly **$0.001** (a tenth of a penny). $5 of credit = about 5,000 hybrids.

If you ever want to limit usage so things can't get out of hand, you can set a monthly spending cap in your Anthropic dashboard.

## 🐛 Troubleshooting

**"The button works but I always get the offline fallback hybrid"**
→ The backend isn't reachable. Check that you uploaded the `api/` folder correctly and that `ANTHROPIC_API_KEY` is set in Vercel's environment variables.

**"500 Server Error"**
→ Open the Vercel dashboard, go to your project, click **Logs**, and look at the most recent error. Most often this means the API key is missing or wrong.

**"It works on Vercel but not when I open index.html locally"**
→ That's expected! When you open the file directly in your browser, there's no backend running, so it falls back to the offline generator. To test the AI part locally, you'd need to run `vercel dev` (Vercel's local development command), but it's easier to just deploy and test on the live URL.

## 🎨 Ideas for what to add next

- More animals and dinosaurs
- A "Save your favorites" feature
- An image of the hybrid (using an AI image model)
- Sound effects when the fusion happens
- Share button to send hybrids to friends
- A "Battle" mode where two hybrids fight

Have fun! 🦖⚡🐺
