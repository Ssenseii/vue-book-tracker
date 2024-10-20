<script setup>
/// Vue
import { ref } from "vue";

/// Components
import Title from "./components/Title.vue";
import AddBook from "./components/AddBook.vue";
import BookList from "./components/BookList.vue";
import SearchBar from "./components/SearchBar.vue";

/// Constants

const books = ref([
	{
		id: 0,
		bookName: "Helsreach",
		bookRating: 5,
		bookProgress: "Finished",
	},
	{
		id: 1,
		bookName: "The Secret History",
		bookRating: 4,
		bookProgress: "Finished",
	},
	{
		id: 2,
		bookName: "Titanicus",
		bookRating: 4,
		bookProgress: "In Progress",
	},
	{
		id: 3,
		bookName: "Angel Exterminatus",
		bookRating: 0,
		bookProgress: "Not Started",
	},
]);

// Add Book
const handleBookAdded = (bookData) => {
  books.value.push(bookData);
  console.log("book added");
};

</script>

<template>
	<main class="flex flex-col items-center m-4 gap-2">
		<Title />
		<AddBook @book-added="handleBookAdded"/>
		<SearchBar />
		<BookList :books="books" />
	</main>
</template>
