+++
authors = ["Lone Coder"]
title = "Supabase Setup for a NextJS Project"
date = "2025-02-10"
description = "How to setup supabase for a NextJS Project"
tags = [
    "Supabase"
]
+++

## Initializing our Next.js Application

In your terminal, enter this command to initialize a new Next.js application:
```bash
npx create-next-app@latest todo-app --typescript --tailwind --eslint
```

You will be prompted for more configurations. For this project, choose these configurations:

1. `src/` directory: No
2. App Router: Yes
3. Customize default import alias: No

We are also going to install some dependencies. Run these commands in your terminal:
```bash
cd todo-app

npm install @supabase/supabase-js @supabase/ssr react-icons
```

 ## Setting up Supabase

Login to Supabase with your GitHub account or with any method you prefer. After logging in, create a new project and store your database password safely.

![supabase_project_creation](/images/supabase_setup-100225_1.webp)

Take note of your `Project URL` and `API Key` as we will store it as environment variables in our Next.js project.

![supabase_env_variables](/images/supabase_setup-100225_2.webp)

In your Next.js project’s top-level directory, create a `.env.local` file and add the following environment variables:

```bash
NEXT_PUBLIC_SUPABASE_URL=https://your-supabase-project-url.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=this-should-be-your-api-key
```