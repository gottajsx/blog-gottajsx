+++
authors = ["Lone Coder"]
title = "Supabase Cheatsheet"
date = "2024-10-12"
description = "Essential Supabase Cheatsheet"
tags = [
    "Supabase",
]
+++

Supabase is an open-source backend-as-a-service platform that provides tools for building applications. It offers features like a PostgreSQL database, authentication, real-time data synchronization, storage for files, and auto-generated APIs. 

## Setup

```js
export const supabase = createClient(
  process.env.SUPABASE_URL,
  process.env.SUPABASE_KEY
);
```

The code initializes a Supabase client to connect your app to a Supabase project using environment variables for the project’s URL and API key. This allows secure interaction with your Supabase backend for tasks like database queries and authentication.

## Authentication

```js
// email signup
const { data, error } = await supabase.auth.signUp({ email, password });

// email login
const { error } = await supabase.auth.signInWithPassword({ email, password });

// magic link
const { error } = await supabase.auth.signInWithOtp({
  email,
  options: {
    emailRedirectTo: 'url to redirect to'
  }
});

// reset password
const { error } = await supabase.auth.resetPasswordForEmail(email);

// oAuth login
const { error } = await supabase.auth.signInWithOAuth({
  provider: 'oauth provider',
  options: {
    redirectTo: 'url to redirect to'
  }
});

// get user data
const user = (await this.sb.supabase.auth.getUser()).data.user;
```
* *Email signup*: Registers a new user with an email and password using Supabase authentication.
* *Email login*: Logs in a user with their email and password.
* *Magic link*: Sends a one-time login link to the user’s email, which logs them in when clicked.
* *Reset password*: Sends a password reset link to the user's email.
* *OAuth login*: Logs in a user using an external provider (e.g., Google, GitHub) with a redirect URL.
* *Get user data*: Retrieves the currently authenticated user's data.

## Write Operations#

```js
// add record
const { error } = await supabase.from('profiles').insert({ ...data });

// update record by filter
const { error } = await supabase.from('profiles').update({ username }).eq('id', id);

// upsert record (add or merge record)
const { error } = await this.sb.supabase.from('profiles').upsert({ ...data });

// delete record by filter
const { error } = await this.sb.supabase.from('profiles').delete().eq('id', id);
```
* *Add record*: Inserts a new record into the `profiles` table.
* *Update record by filter*: Updates the record in `profiles` where the `id` matches.
* *Upsert record*: Inserts a record or updates it if it already exists in `profiles`.
* *Delete record by filter*: Deletes the record from `profiles` where the `id` matches.

## Read Operations

The goal of a read operation in Supabase is to retrieve data from a specified table in the database. This allows you to fetch records based on various filters, conditions, or retrieve entire sets of data.

```jsx
// select all by filter
const { error, data } = await supabase.from('profiles').select('*').eq('username', username);

// select all with count
const { error, data, count } = await supabase.from('profiles').select('*', {count: 'exact')
  .eq('username', username);

// pagination
const getPagination = (page, size) => {
  const limit = size ? +size : 3
  const from = page ? page * limit : 0
  const to = page ? from + size - 1 : size - 1
  return { from, to }
};

const { from, to } = getPagination(page, 10);

const { error, data } = await supabase.from('profiles').select('*').range(from, to);

// order
const { error, data } = await supabase.from('profiles').select('*')
  .order('username', { ascending: true });

// inner joins (all joins use to_json() to convey child data with uniqueness)
const { error, data } = await supabase.from('posts').select('*, author!inner(*)');
```

## Storage

Supabase Storage is a service that allows you to store and manage files such as images, videos, documents, etc., directly within your Supabase project. It provides features similar to cloud storage services (like AWS S3) and integrates seamlessly with Supabase’s authentication and database services.

```jsx
// upload file
const { data, error } = await supabase.storage.from('photos').upload(path, file));

// delete file by url
const { error } = await supabase.storage.from('photos').remove([url]);

// get url
const { data } = this.sb.supabase.storage.from('photos').getPublicUrl(path);
```

