+++
authors = ["Lone Coder"]
title = "Nextjs CRUD Operations with Firebase"
date = "2024-10-10"
description = "Mastering CRUS Operations in Nextjs using Firestore Database"
tags = [
    "git", "ssh"
]
+++

## Requirements

* Yarn (https://yarnpkg.com)
* Visual Studio Code (https://code.visualstudio.com/download)
* Firebase

## Project Setup

Run the following command in your terminal
```bash
yarn create next-app next-firebase-crud
```

* Would you like to use TypeScript? No
* Would you like to use ESLint? Yes
* Would you like to use Tailwind CSS? Yes
* Would you like to use `src/` directory? Yes
* Would you like to use App Router? (recommended)? No
* Would you like to customize the default import alias (@/*)? Yes

## Dependencies Installation

```bash
cd next-firebase-crud
yard add firebase
```
## Firebase Setup

Go to Console https://console.firebase.google.com/u/0/

Type your project name. 

![crud_1](/images/crud_101024_1.webp)

Disable google analytics, click create project

![crud_2](/images/crud_101024_2.webp)

Click continue

![crud_3](/images/crud_101024_3.webp)

Go to cloud firestore, and create database

![crud_4](/images/crud_101024_4.webp)

![crud_5](/images/crud_101024_5.webp)

![crud_6](/images/crud_101024_6.webp)

Go to project setting, then choose web app.

![crud_7](/images/crud_101024_7.webp)

![crud_8](/images/crud_101024_8.webp)

![crud_9](/images/crud_101024_9.webp)

## Configuring Environment Variable

Create `.env file`, and copy-paste this code below that define variable value based on firebase config.
```
NEXT_PUBLIC_FIREBASE_API_KEY=api-key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=auth-domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=project-id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=storage-bucket
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=sender-id
NEXT_PUBLIC_FIREBASE_APP_ID=app-id
```

## Firebase Config file

Create firebase configuration file `src/config/firebase.js`, and copy paste code below:
```javascript
// Import the functions you need from the SDKs you need
import { initializeApp, getApps } from "firebase/app";
import { getFirestore } from "firebase/firestore";


// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: process.env.NEXT_PUBLIC_FIREBASE_API_KEY,
  authDomain: process.env.NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.NEXT_PUBLIC_FIREBASE_PROJECT_ID,
  storageBucket: process.env.NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
  appId: process.env.NEXT_PUBLIC_FIREBASE_APP_ID,
};

// Initialize Firebase
let app = getApps().length === 0 ? initializeApp(firebaseConfig) : getApps()[0];

export const db = getFirestore(app);
```
## List All Tasks

Update page `src/pages/index.js` and copy paste code below.
```javascript
import { db } from "@/config/firebase";
import { collection, getDocs } from "firebase/firestore";
import Head from "next/head";
import Link from "next/link";
import { useEffect, useState } from "react";

export default function Home() {
  const [tasks, setTasks] = useState([]);

  const getTasks = async () => {
    const col = collection(db, "tasks");
    const snapshot = await getDocs(col);
    setTasks(snapshot.docs.map(doc => {
      return {
        id: doc.id,
        ...doc.data()
      }
    }));
  }

  useEffect(() => {
    getTasks()
  }, [])

  return (
    <>
      <div className="container mx-auto mt-8 max-w-[560px]">
        <div className="flex justify-between items-center pb-4 border-b border-dashed border-gray-900 mb-4">
          <h1 className="text-3xl font-semibold">Tasks</h1>
          <Link
            className="bg-green-600 hover:bg-opacity-80 text-white rounded-lg px-4 py-2 duration-200"
            href="/create"
          >
            Create New
          </Link>
        </div>
        <ul>
          {tasks.map((task) => (
            <li key={task.id} className="py-2 flex justify-between w-full">
              <span>
                <strong>{task.name}</strong> - {task.description}
              </span>
              <span className="flex gap-2">
                <Link className="text-blue-700 underline hover:no-underline" href={`/${task.id}/edit`}>Edit</Link>
                <Link className="text-red-500 underline hover:no-underline" href={`/${task.id}/delete`}>Delete</Link>
              </span>
            </li>
          ))}
          {tasks?.length < 1 && <div className="py-2">No data</div>}
        </ul>
      </div>
      <Head>
        <title>Task</title>
      </Head>
    </>
  );
}
```

## Create New Task

Create page `src/pages/create.jsx` and copy paste code below.
```jsx
import { db } from "@/config/firebase";
import { addDoc, collection, doc, setDoc } from "firebase/firestore";
import Head from "next/head";
import { useRouter } from "next/router";
import { useEffect, useState } from "react";

export default function Create() {
  const router = useRouter();
  const [task, setTask] = useState({
    name: "",
    description: "",
  });

  const onChange = (e) => {
    setTask({ ...task, [e.target.name]: e.target.value });
  };


  const handleCreate = async () => {
    const col = collection(db, "tasks");
    try {
      addDoc(col, {
        name: task.name,
        description: task.description,
      });
      router.push("/");
    } catch (error) {}
  };

  return (
    <>
      <>
        <div className="container mx-auto mt-8 max-w-[560px]">
          <div className="flex justify-between items-center pb-4 border-b border-dashed border-gray-900 mb-4">
            <h1 className="text-3xl font-semibold">Create Task</h1>
          </div>
          <form>
            <div className="mb-4">
              <label>Title</label>
              <input
                className="mt-1 px-4 py-2 border border-gray-300 rounded-md block w-full"
                type="text"
                name="name"
                value={task?.name}
                onChange={onChange}
              />
            </div>
            <div className="mb-4">
              <label>Description</label>
              <input
                className="mt-1 px-4 py-2 border border-gray-300 rounded-md block w-full"
                type="text"
                name="description"
                value={task?.description}
                onChange={onChange}
              />
            </div>
            <button
              className="bg-green-600 hover:bg-opacity-80 text-white rounded-lg px-4 py-2 duration-200 w-full"
              type="button"
              onClick={handleCreate}
            >
              Create Task
            </button>
          </form>
        </div>
        <Head>
          <title>Create Task</title>
        </Head>
      </>
    </>
  );
}
```

## Edit Tasks

Create page `src/pages/[id]/edit.jsx` and copy paste code below.
```jsx
import { db } from "@/config/firebase";
import { doc, getDoc, setDoc } from "firebase/firestore";
import Head from "next/head";
import { useRouter } from "next/router";
import { useEffect, useState } from "react";

const Edit = () => {
  const router = useRouter();
  const { id } = router.query;

  const [task, setTask] = useState({
    name: "",
    description: "",
  });

  const onChange = (e) => {
    setTask({ ...task, [e.target.name]: e.target.value });
  };

  useEffect(() => {
    const fetchTask = async () => {
      const ref = doc(db, "tasks", id);
      const snapshot = await getDoc(ref);
      setTask({ id: snapshot.id, ...snapshot.data() });
    };

    if (id) {
      fetchTask();
    }
  }, [id]);

  const handleUpdate = async () => {
    const ref = doc(db, "tasks", id);
    setDoc(ref, {
      name: task.name,
      description: task.description,
    })
      .then(() => {
        router.push("/");
      })
      .catch((error) => {
        console.log(error);
      });
  };

  return (
    <>
      <div className="container mx-auto mt-8 max-w-[560px]">
        <div className="flex justify-between items-center pb-4 border-b border-dashed border-gray-900 mb-4">
          <h1 className="text-3xl font-semibold">Edit Task</h1>
        </div>
        <form>
          <div className="mb-4">
            <label>Title</label>
            <input
              className="mt-1 px-4 py-2 border border-gray-300 rounded-md block w-full"
              type="text"
              name="name"
              value={task?.name}
              onChange={onChange}
            />
          </div>
          <div className="mb-4">
            <label>Description</label>
            <input
              className="mt-1 px-4 py-2 border border-gray-300 rounded-md block w-full"
              type="text"
              name="description"
              value={task?.description}
              onChange={onChange}
            />
          </div>
          <button
            className="bg-green-600 hover:bg-opacity-80 text-white rounded-lg px-4 py-2 duration-200 w-full"
            type="button"
            onClick={handleUpdate}
          >
            Edit Task
          </button>
        </form>
      </div>
      <Head>
        <title>Edit Task</title>
      </Head>
    </>
  );
};

export default Edit;
```

## Delete Tasks

Create page `src/pages/[id]/delete.jsx` and copy paste code below.
```jsx
import { db } from "@/config/firebase";
import { deleteDoc, doc, getDoc } from "firebase/firestore";
import Head from "next/head";
import Link from "next/link";
import { useRouter } from "next/router";
import { useEffect, useState } from "react";

const Delete = () => {
  const router = useRouter();
  const { id } = router.query;

  const [task, setTask] = useState({
    title: "",
    description: "",
  });

  useEffect(() => {
    const fetchTask = async () => {
      const ref = doc(db, "tasks", id);
      const snapshot = await getDoc(ref);
      setTask({ id: snapshot.id, ...snapshot.data() });
    };

    if (id) {
      fetchTask();
    }
  }, [id]);

  const handleDelete = async () => {
    const ref = doc(db, "tasks", id);
    deleteDoc(ref)
      .then(() => {
        router.push("/");
      })
      .catch((error) => {
        console.log(error);
      });
  };

  return (
    <>
      <div className="container mx-auto mt-8 max-w-[560px]">
        <div className="flex justify-between items-center pb-4 border-b border-dashed border-gray-900 mb-4">
          <h1 className="text-3xl font-semibold">Delete Task</h1>
        </div>
        <form>
          <div className="my-12">
            Are you sure to delete <strong>{task?.name}</strong>?
          </div>
          <div className="flex w-full gap-2">
            <Link
              href="/"
              className="text-center bg-gray-300 hover:bg-opacity-80 text-black rounded-lg px-4 py-2 duration-200 w-full"
            >
              Cancel
            </Link>
            <button
              className="bg-red-500 hover:bg-opacity-80 text-white rounded-lg px-4 py-2 duration-200 w-full"
              type="button"
              onClick={handleDelete}
            >
              Delete
            </button>
          </div>
        </form>
      </div>
      <Head>
        <title>Delete Task</title>
      </Head>
    </>
  );
};

export default Delete;
```

## Tailwind Config

Clear some css variable at `src/styles/globals.css`:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
## Run Project

Run the following command:
```bash
yarn dev
```