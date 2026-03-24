---
layout: post
title: TBR Picker
date: 2026-03-24
description: A guide about my TBR Picker 📖🎲 project
tags: reading
# categories: sample-posts
categories: Personal
featured: false
toc:
  sidebar: right
---

### 📖 Welcome to TBR Picker

<br>This little project is my personal tool to help me get back into my reading habit. Last year I collected so many books, and now I want to finally read them all and make the most of my upcomimg Kobo Clara Colour.

With TBR Picker 📖🎲, I can add books manually or (in the future) upload my Goodreads CSV to randomly pick my next read. The CSV upload isn’t ready yet because I don’t have my Goodreads data and I’m still figuring out the exact format of the CSV, but manual entry works perfectly for now.

It has a reroll button if I’m not feeling the first pick, and every book added appears in a list with a delete button — making it easy to manage my reading list.

This project was a fun way to combine web development, JavaScript, and a cute pastel aesthetic with something personal. It’s my little helper for finally tackling my unread books, and I’m excited to share it here on my blog! 🎲💖

---

### 📖 How to Use the TBR Picker

This guide will help in getting started with TBR Picker for an easy pick on a next read.

#### 1. Adding Books Manually
- Enter the **Title**, **Author**, and **Genre** in the input fields under “Or Add a Book Manually.”
- Click **Add Book ➕** to add it to your list.
- Your added books will appear below in a list, each with a **Delete ❌** button to remove them if needed.

#### 2. Uploading a Goodreads CSV (Future Feature)
- You can upload a CSV file using the **Choose CSV 📁** button.
- ⚠️ The CSV upload isn’t fully ready yet because I don’t have my Goodreads data yet and I don't know how Goodreads parse their users' data. Right now, I made the web app to get the TBR shelf. In my case, that's the `want-to-read` shelf. 

This is how the CSV file is structured right now, so do your CSV file exactly like this:

```text
title                           shelf               author           genre
The Silent Garden           want-to-read        Clara Whitmore	    mystery
Stars Over Maple Street	    read                Julian Hart         contemporary
The Forgotten Library	    want-to-read        Elena Brooks	    fantasy
Midnight Train to Nowhere   want-to-read        Daniel Cross	    thriller
The Last Summer Letter	    read                Mia Holloway	    romance
The Ocean Between Us	    want-to-read        Lucas Bennett	    contemporary
A Shadow in the Hall	    want-to-read        Nora Keats          mystery
The Clockmaker's Secret	    read                Henry Dalton	    historical fiction
Whispers of the Forest	    want-to-read        Sophia Lang         fantasy
The Girl Who Stayed         read                Amelia Rowe         drama
Rain Over Tokyo	            want-to-read        Oliver Chase	    contemporary
```

The TBR Picker📖🎲 will then display the books in the `want-to-read` shelf.

#### 3. Picking a Book
- Once you have books added manually (or from a future CSV upload), click Pick a Book 🎲 to randomly choose a book.
- If you’re not feeling the first pick, click Reroll 🔄 to shuffle and get another book.


> You can try the TBR Picker 📖🎲 [here]({% link _projects/TBR_Picker.md %})! 🐳