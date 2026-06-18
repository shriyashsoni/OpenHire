# OpenHire CLI 🚀

Build your startup's dedicated career page, complete with an ATS (Applicant Tracking System), an AI-assisted autofill application page, and a secure Admin Dashboard — in literally under 2 minutes.

OpenHire is a fully open-source recruitment platform heavily inspired by leading ATS workflows. It provides everything you need out of the box.

## 🌟 Features Included Out-of-the-Box
1. **Dynamic Public Career Page**: Showcase your company benefits and list all open roles. Matches your brand color and identity automatically.
2. **AI-Powered Job Application Page**: Built-in PDF parsing that magically reads a candidate's resume and auto-fills their application.
3. **Secure Admin Dashboard**: Create jobs, manage custom application questions (with logic branching), review applications, and track visits.
4. **Dynamic SEO & Social Sharing**: Every job has unique meta tags so when you share links on Twitter/LinkedIn, the preview cards look perfect.
5. **Serverless Backend via Convex**: Securely stores resumes, applications, and job schemas in a fast, real-time database.

---

## 🛠️ Installation Guide

Follow these steps to generate and deploy your own HR platform.

### Step 1: Run the CLI
In your terminal, navigate to the folder where you want to create your platform and run the CLI tool:
```bash
npx create-open-hire
```
*(If you have cloned this repo locally, run `node cli.js` instead).*

The interactive CLI will ask you for:
- **Project Name** (e.g., \`my-career-page\`)
- **Company Name** (e.g., \`TechStartup Inc\`)
- **Website URL** (e.g., \`https://techstartup.com\`)
- **Primary Brand Color Hex** (e.g., \`#1A73E8\`)
- **Support Email** (e.g., \`careers@techstartup.com\`)

The CLI will instantly scaffold your project and inject your brand identity (names, colors, URLs) across the entire platform, including your auto-generated Privacy Policy!

### Step 2: Install Dependencies
Navigate into your newly created folder and install the required npm packages:
```bash
cd my-career-page
npm install
```

### Step 3: Setup your Convex Database (Backend)
OpenHire runs entirely on [Convex](https://convex.dev/) as its serverless backend. Setting it up is free and instantaneous.

Run the following command:
```bash
npx convex dev
```
1. It will prompt you to log into Convex (via GitHub or email).
2. It will ask you to configure a project. Just hit **Enter** to accept the defaults.
3. Convex will automatically upload the backend schema (`convex/schema.ts`) and create your database tables!
4. Keep this terminal window open; it syncs your backend in real-time.

### Step 4: Run the Local Frontend Server
Open a **new** terminal window (keep the Convex one running), navigate to your project directory, and start the frontend:
```bash
npm run dev
```
You can now visit your brand new HR platform at \`http://localhost:5173\`!

---

## 🔐 Setting up the Admin Dashboard
By default, the platform includes a hidden Admin Dashboard located at `/admin.html` (e.g., `http://localhost:5173/admin.html`).

### Generating your first Admin User
Before you can log in, you need to seed the database with an admin account.
In your terminal, run:
```bash
npx convex run seed:createDefaultAdmin
```
This script will create a default admin using your company email as the username. 
*(If you want to customize the username and password, you can edit the \`convex/seed.ts\` file before running it).*

Once created, go to `/admin.html` on your site and log in to start creating jobs!

---

## 🌐 Deployment

Deploying your OpenHire platform is incredibly easy.

1. **Backend**: Run \`npx convex deploy\` to push your database schema to production. This will give you a production Convex URL.
2. **Frontend**: Create a `.env.local` file and add:
   \`\`\`
   VITE_CONVEX_URL=your_production_convex_url
   \`\`\`
3. Push your repository to GitHub.
4. Import your repository into **Vercel** or **Netlify**. Ensure you add the `VITE_CONVEX_URL` environment variable in their dashboard settings.
5. Hit deploy!

Your startup now has a world-class, professional career portal. Happy hiring! 🚀
