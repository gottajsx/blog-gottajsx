+++
authors = ["Lone Coder"]
title = "Firestore Cheatsheet"
date = "2024-10-10"
description = "Essential Firestore Cheatsheet"
tags = [
    "Firestore", "Firebase"
]
+++

Firestore sees data as collections of documents, and a collection can store sub-collections too. A collection in Firestore is a container for a group of documents. Each document in a collection is unique, and the collection itself does not store any data other than references to the documents it contains.

* Collections can be thought of like folders in a filesystem, while documents are like files within those folders.
* Collections contain documents (which are key-value pairs or structured objects) but cannot directly store data themselves.

Example:

```
/Users            <-- Collection
   /User1         <-- Document
      /Posts      <-- Subcollection (inside User1 document)
         /Post1   <-- Document in Posts subcollection
         /Post2   <-- Document in Posts subcollection
   /User2         <-- Document
      /Posts      <-- Subcollection (inside User2 document)
         /Post3   <-- Document in Posts subcollection
```

## CRUD Operations in Firestore

Before a CRUD operation can be performed, a collection to work with need to be selected.
```js
// to reduce a few keystokes to access the todos collection
const todos = db.collection("todos")
```

### Create Operation

The documents stored would be converted to JSON an object-like structure must be used.
```js
doc = {name:"clap this article"};
todos.add(doc);

// or
db.collection("todos").add({name:"clap this article"});
```

### Read Operation

#### To quickly get all the documents inside a collection.

```js
db.collection("todos").get().then(snapshot=>snapshot.docs.forEach(doc=>console.log(doc.data())))
```

1. It takes a screenshot of the current state of collection

2. From the screenshot, the docs stored in the collection are extracted

3. The `forEach` is a `for` loop that console logs data stored in every document.

### To get a specific document.

```js
const docid = "sfdagerfkajilf";
db.collection("todos").doc(docid);
```
when a document is added to a collection, firestore generates a random `id` and uses it as the name of a document.
To fetch a certain document, we need to specify the `id`

### Update a document

#### Reset the Whole document

```js
    db.collection("todos").doc("dagfshdjhkdfagsh").set({
      task1: "follow LucidMach on medium",
      task2: "share this article to everyone"
    });
```

#### Modify a Part of the Document

```js
    db.collection("todos").doc("afdghrujfkhotdf").update({
      task2: "follow LucidMach on twitter"
    });
```

On using `.update()`, only the specified part of the document changes, so the unspecified part doesn’t change,

### Delete Documents 

This operation is very similar to updating a document
```js
db.collection("todos").doc("afdghrujfkhotdf").delete()
```
