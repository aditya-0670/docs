<a name="readme-top"></a>

# 📄 Docs: Real‑Time Collaborative Document Editor

Docs is a powerful, real‑time collaborative document editor built with Next.js 15, Convex, and modern frontend tooling. It supports:

* **Collaborative cursors** to show each user’s position in the document
* **Mentions**, **comments**, and **reactions** for rich collaboration
* **Instant synchronization** across all connected clients
* **Authentication** and role‑based access control

---

## 📑 Table of Contents

* [🚀 Features](#-features)
* [📂 Architecture & Folder Structure](#-architecture--folder-structure)
* [⚙️ Getting Started](#️-getting-started)

  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
  * [Configuration](#configuration)
  * [Development](#development)
  * [Production Build & Deployment](#production-build--deployment)
* [🛠 Tech Stack](#-tech-stack)
* [📸 Screenshots](#-screenshots)
* [📈 Performance](#-performance)
* [🤝 Contributing](#-contributing)
* [📄 License](#-license)
* [⬆️ Back to Top](#readme-top)

---

## 🚀 Features

* **Real‑Time Editing**: Leveraging Convex and WebSockets for sub‑100ms sync latency.
* **Collaborative Cursors**: See other users’ cursors and selections live.
* **Rich Text Editing**: Built on Tiptap—supports formatting, lists, tables, images, and more.
* **Mentions & Comments**: @mention colleagues, leave threaded comments, and resolve discussions.
* **Authentication & Access Control**: User sign‑in and permissions via Clerk.
* **Scalable Backend**: Convex functions and schema manage document state and authorization.
* **Production‑Ready**: Zero‑config deployment on Vercel with environment‑specific settings.

---

## 📂 Architecture & Folder Structure

```
docs/                      # root of the project
├─ convex/                 # Convex backend: schema, auth, API functions
│   ├─ _generated/         # auto‑generated Convex types
│   ├─ auth.config.ts      # Clerk‑Convex JWT integration
│   ├─ documents.ts        # CRUD & real‑time sync functions
│   └─ schema.ts           # Convex data model for documents
├─ public/                 # static assets (SVG icons, favicons)
├─ src/                    # Next.js 15 app source
│   ├─ app/                # file‑based routes, layouts, error pages
│   ├─ components/         # reusable UI components & dialogs
│   ├─ config/             # editor and application settings
│   ├─ constants/          # shared constants (e.g. user roles)
│   ├─ extensions/         # custom Tiptap editor extensions
│   ├─ hooks/              # custom React hooks (debounce, search‑param)
│   ├─ lib/                # utility functions
│   ├─ store/              # Zustand state management for editor
│   └─ middleware.ts       # Next.js middleware (auth redirects)
├─ .env.example            # example environment variables
├─ next.config.ts          # Next.js configuration
├─ package.json            # project dependencies & scripts
├─ tailwind.config.ts      # Tailwind CSS configuration
├─ tsconfig.json           # TypeScript configuration
└─ README.md               # this documentation
```

---

## ⚙️ Getting Started

### Prerequisites

* **Node.js** ≥ 18
* **Git**
* A **Convex** account (free tier available)
* A **Clerk** account for authentication
* A **Liveblocks** account (optional, for advanced presence features)

### Installation

1. **Clone the repo**

   ```bash
   git clone https://github.com/aditya-0670/docs.git
   cd docs
   ```
2. **Install dependencies**

   ```bash
   npm install --legacy-peer-deps
   # or
   yarn install --legacy-peer-deps
   ```

### Configuration

1. **Copy environment templates**

   ```bash
   cp .env.example .env.local
   cp convex/.env.example convex/.env.local
   ```
2. **Set environment variables** in both `./.env.local` and `./convex/.env.local`:

   ```env
   # Application
   NEXT_PUBLIC_APP_BASE_URL=http://localhost:3000

   # Convex
   CONVEX_DEPLOYMENT="dev:<deployment-id>"
   NEXT_PUBLIC_CONVEX_URL=https://<deployment-id>.convex.cloud

   # Clerk (Auth)
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
   CLERK_SECRET_KEY=sk_test_...
   CLERK_ISSUER_URL="https://<issuer>.clerk.accounts.dev"

   # Liveblocks (optional)
   NEXT_PUBLIC_LIVEBLOCKS_API_KEY=pk_live_...
   LIVEBLOCKS_SECRET_KEY=sk_live_...
   ```

### Development

```bash
npm run dev
# or
yarn dev
```

Open your browser at `http://localhost:3000` and sign in to start editing.

### Production Build & Deployment

```bash
npm run build
npm run start       # locally
# or deploy to Vercel, Netlify, etc.
```

---

## 🛠 Tech Stack

* **Next.js 15** • React framework with file‑based routing
* **Convex** • Serverless database & functions for real‑time data
* **Clerk** • User authentication & management
* **Tiptap** • Headless rich‑text editor
* **Liveblocks** • Presence & awareness (optional)
* **Tailwind CSS** • Utility‑first styling
* **Zustand** • Lightweight React state management

---

## 📸 Screenshots

App’s UI and key features:

   <p align="center">
     <img src="/UI-DOCS.png" alt="UI Overview" width="300" />
   </p>

5. **Commit & Push**

   ```bash
   git add public/images/ui-overview.png public/images/comments-panel.png README.md
   git commit -m "docs: add screenshots for UI overview and comments panel"
   git push
   ```

---

## 🤝 Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a branch: `git checkout -b feature/YourFeature`
3. Commit changes: `git commit -m "feat: add amazing feature"`
4. Push branch: `git push origin feature/YourFeature`
5. Open a Pull Request

Ensure code follows existing patterns and includes tests for new functionality.

---

<p align="right">⬆️ <a href="#readme-top">Back to Top</a></p>
