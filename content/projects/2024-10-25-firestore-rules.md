+++
authors = ["Lone Coder"]
title = "Firebase Rules for Instagram Clone Project"
date = "2024-10-25"
description = "Firestore and storage rules for Instagram clone project"
tags = [
    "Firestore", "Firebase"
]
+++

## Firestore Rules

This Firestore security rules code controls access to the data in your Firestore database, setting permissions for both reading and writing.

Let's go through the following and explain it:
```javascript
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

First: 
```javascript
rules_version = '2';
```
This specifies that the rules are written using version 2 of the Firestore security rules. Each version may have differences in available features and syntax.

```javascript
service cloud.firestore {
  match /databases/{database}/documents {
```
Here, we define the security rules for a Firestore database. The service `cloud.firestore` line indicates these rules apply to Firestore.

`match /databases/{database}/documents` tells Firestore to apply these rules to all databases (usually there is only one database per project) and to all documents within it.

### Defining Access Rules

The section inside `match /{document=**} { ... }` applies these rules to all documents at all levels within the Firestore database, thanks to the `{document=**}` syntax, which is a wildcard for all document paths.

```javascript
allow read: if true;
```
`allow read: if true;` allows read access (both viewing and fetching documents) for anyone, whether they are authenticated or not. if true always evaluates to true, so any user, authenticated or not, can read the data.

```javascript
allow write: if request.auth != null;
```
`allow write: if request.auth != null;` allows write access (creating, updating, or deleting documents) only if the user is authenticated. Here, `request.auth != null` checks if the request is made by a user who is logged in. If `request.auth` is null, that means the user is unauthenticated, and the write request will be denied.

## Firebase Storage Rules

This Firebase Storage security rules code controls access to files stored in specific folders within your Firebase Storage bucket, setting permissions for both reading and writing.

Let's go through the following and explain it:
```javascript
rules_version = '2';

service firebase.storage {
  match /b/{bucket}/o {
    match /posts/{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /profilePics/{document=**} {
      allow read: if true; 
      allow write: if request.auth != null; 
    }
  }
}
```

```javascript
rules_version = '2';
```
This specifies that the rules are written in version 2, which may offer additional features or improved syntax compared to earlier versions.

```javascript
service firebase.storage {
  match /b/{bucket}/o {
```
This line defines the service as firebase.storage, indicating that these rules apply to Firebase Storage, which is used to store files such as images, videos, or other media.
`match /b/{bucket}/o` applies these rules to all buckets within the Firebase Storage service. `{bucket}` is a placeholder for the bucket name, and `/o` represents "objects" or files within that bucket.

### Access Rules for Specific Folders

These rules provide different access levels for two folders within the storage: `posts` and `profilePics`.

### Rules for the posts Folder

```javascript
    match /posts/{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
```
`match /posts/{document=**}` applies these rules to all files within the posts folder and any subfolders (because `{document=**}` is a wildcard for any path under `posts`).
`allow read: if true;` allows anyone to read (view/download) files in this folder, whether or not they are authenticated.
`allow write: if request.auth != null;` restricts write access (uploading or modifying files) to authenticated users only. If a user is unauthenticated (`request.auth == null`), they cannot write to this folder.

#### Rules for the profilePics Folder

```javascript
    match /profilePics/{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
```
`match /profilePics/{document=**}` applies the same pattern of rules as in the `posts` folder, but now for all files within the `profilePics` folder and its subfolders.
`allow read: if true;` grants read access to anyone, authenticated or not.
`allow write: if request.auth != null;` allows only authenticated users to upload or modify files in this folder.

