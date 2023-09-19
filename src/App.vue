<script setup>
import { ref, reactive } from "vue";
import Books from "./components/Books.vue";
import BookProgress from "./components/BookProgress.vue";
import AddBook from "./components/AddBook.vue";

let books = reactive([
  {
    id: 1,
    title: "History of Europe",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-6-540x861.jpg",
    isRead: true,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
  {
    id: 2,
    title: "Penguin Classics",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-2-540x861.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo, Jon Snow",
  },
  {
    id: 3,
    title: "Becoming",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-7-540x861.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
  {
    id: 4,
    title: "Sonnets",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-5-540x861.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
]);

let showAddBook = ref(false);

function addBook(newBook) {
  books.push(newBook);
  showAddBook.value = false;
};

function toggleIsRead(idBook) {
  books.forEach((book) => {
    if (book.id === idBook) book.isRead = !book.isRead;
  });
}
</script>

<template>
  <div v-if="!showAddBook" class="container">
    <h1>📖 My Books</h1>
    <div class="header-btns">
      <button class="btn" @click="showAddBook = true">Add Book +</button>
    </div>

    <div class="books-container">
      <Books :books="books" @toggleIsRead="toggleIsRead" />]
      <BookProgress :books="books" />
    </div>
  </div>
  <div v-else>
    <AddBook @addBook="addBook" @closeAddBook="showAddBook = false" />
  </div>
</template>

<style scoped></style>
