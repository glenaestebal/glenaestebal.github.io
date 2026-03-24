---
layout: page
title: TBR Picker 📖🎲
date: 2026-03-24
description: A TBR randomizer for figuring out my next read
img: assets/img/tbr_picker/background.jpg
importance: 1
category: Personal
related_publications: false
---

### Before Using the TBR Picker

<br>This is a simple web app to help randomly pick a next read. Here is a [guide]({% link _posts/2026-03-24-TBR-Picker.md %})!

Since the CSV upload isn’t ready yet (I don’t have my Goodreads data and I’m still figuring out the exact format), start by adding books manually. Once the books are added, a random book will be generated. A reroll chance is also given if you don't like the generated book.

<div class="mt-5 text-center">
    <h2>Pick My Next Read 🔮</h2>

<div class="mt-4 text-center">
    <!-- Upload Section -->
    <h5 style="font-size: 14px; color: #5a6fa8; font-weight: 500; text-transform: lowercase; letter-spacing: 1px;">
    ✧ upload goodreads csv ✧ 
    </h5>
    <!-- Custom File Upload Button -->
    <label for="fileInput"
    id="fileLabel"
    class="btn rounded-pill px-4 mt-2"
    style="background-color:#85A1F2; color:black; cursor:pointer;"
    >
    Choose CSV 📁
    </label>
    <input type="file" id="fileInput" style="display: none;" />
    <div id="uploadMessage" style="color:#5a6fa8; font-weight:500; margin-top:8px;"></div>
</div>

<div>
    <hr class="my-4">
    <!-- Manual Input Section -->
    <div class="mt-4">
    <h5>Or Add a Book Manually</h5>
    <input type="text" id="title" placeholder="Book Title" class="form-control mb-2" />
    <input type="text" id="author" placeholder="Author" class="form-control mb-2" />
    <input type="text" id="genre" placeholder="Genre" class="form-control mb-2" />
    <button onclick="addBook()" class="btn rounded-pill px-4 mt-2" style="background-color:#85A1F2; color:black;">
        Add Book ➕
    </button>
    <div id="manualMessage" style="color:#FF7276; font-weight:500; margin-top:8px;"></div>
</div>

<div>
    <h5 class="mt-4">📋 Added Books</h5>
    <ul id="bookList" class="list-group mt-2"></ul>
</div>

<div>
    <hr class="my-4">
    <!-- Picker and Reroll -->
    <button onclick="rerollBook()" class="btn rounded-pill px-4 mt-2" style="background-color:#91DDF2; color:black;">
    Reroll 🔄
    </button>
    <button onclick="pickBook()" class="btn rounded-pill px-4" style="background-color:#8BC6FC; color:black;">
        Pick a Book 🎲
    </button>
    <h3 id="result" class="mt-4"></h3>
</div>

{% raw %}
<script>
let books = [];

// Upload Goodreads CSV
document.getElementById('fileInput').addEventListener('change', function(event) {
  const file = event.target.files[0];
  const reader = new FileReader();

  reader.onload = function(e) {
    const text = e.target.result;
    const rows = text.split('\n');

    const parsedBooks = rows
        .map(row => {
        const separator = row.includes('\t') ? '\t' : ',';
        return row.split(separator).map(cell => cell.trim());
        })
      .filter(row => row[1] === "want-to-read")
      .map(row => ({
        title: row[0],
        author: row[2] || "Unknown",
        genre: row[3] || "Unknown"
      }));

    parsedBooks.forEach(book => displayBook(book));
    books = books.concat(parsedBooks);

    const message = document.getElementById('uploadMessage');
    message.innerText = parsedBooks.length + " books loaded from Goodreads! 🎉";

    // Optional: hide message after 5 seconds
    setTimeout(() => {
        message.innerText = "";
        }, 4000);
    };

  reader.readAsText(file);
});

// Manual add
function addBook() {
  const title = document.getElementById('title').value.trim();
  const author = document.getElementById('author').value.trim();
  const genre = document.getElementById('genre').value.trim();

  if (!title || !author) {
    const msg = document.getElementById('manualMessage');
    msg.innerText = "Please enter at least title and author!";
    setTimeout(() => { msg.innerText = ""; }, 4000);

    return;
  }

  const book = { title, author, genre };
  books.push(book);

  displayBook(book); // add to visible list

  // Clear inputs
  document.getElementById('title').value = "";
  document.getElementById('author').value = "";
  document.getElementById('genre').value = "";
}

// Display book in list with delete button
function displayBook(book) {
  const list = document.getElementById('bookList');

  const item = document.createElement('li');
  item.className = "list-group-item d-flex justify-content-between align-items-center";

  // book info
  item.innerHTML = `${book.title} by ${book.author} (${book.genre || "No genre"})`;

  // delete button
  const deleteBtn = document.createElement('button');
  deleteBtn.className = "btn btn-sm";
  deleteBtn.style.backgroundColor = "#FF7276";
  deleteBtn.style.color = "black";
  deleteBtn.style.marginLeft = "10px";
  deleteBtn.innerText = "Delete ❌";
  deleteBtn.onclick = function() {
    // remove from DOM
    list.removeChild(item);
    // remove from books array
    const index = books.indexOf(book);
    if (index > -1) books.splice(index, 1);
  };

  item.appendChild(deleteBtn);
  list.appendChild(item);
}

// Pick random book
function pickBook() {
  if (books.length === 0) {
    const msg = document.getElementById('manualMessage');
    msg.innerText = "Add or upload books first!";

    setTimeout(() => { msg.innerText = ""; }, 4000);

    return;
  }

  const randomIndex = Math.floor(Math.random() * books.length);
  const book = books[randomIndex];

  document.getElementById('result').innerText =
    `${book.title} by ${book.author} (Genre: ${book.genre})`;
}

// Reroll
function rerollBook() {
  if (books.length === 0) {
    const msg = document.getElementById('manualMessage');
    msg.innerText = "Add or upload books first!";
    setTimeout(() => { msg.innerText = ""; }, 4000);

    return;
  }

  if (!document.getElementById('result').innerText) {
    const msg = document.getElementById('manualMessage');
    msg.innerText = "Pick a book first before rerolling!";
    setTimeout(() => { msg.innerText = ""; }, 4000);

    return;
  }

  let newIndex;
  const currentBookTitle = document.getElementById('result').innerText.split(" by ")[0];

  do {
    newIndex = Math.floor(Math.random() * books.length);
  } while (books.length > 1 && books[newIndex].title === currentBookTitle);

  const book = books[newIndex];
  document.getElementById('result').innerText =
    `${book.title} by ${book.author} (Genre: ${book.genre})`;
}
</script>
{% endraw %}