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

const filteredBooks = ref([...books.value]);

// Add Book
const handleBookAdded = (bookData) => {
	books.value.push(bookData);
	console.log("book added");
};

// Delete Book
const handleBookDeleted = (id) => {
	books.value = books.value.filter((book) => {
		return book.id !== id;
	});
	console.log("Book Deleted Succesfully!");
};

// Search For Book
const handleBookSearch = (searchterm) => {
	if (searchterm.trim() !== "") {
		filteredBooks.value = filteredBooks.value.filter((book) =>
			book.bookName.toLowerCase().includes(searchterm.toLowerCase())
		);
	} else {
		filteredBooks.value = books.value;
	}
};
</script>

<template>
	<main class="flex flex-col items-center m-4 gap-2">
		<Title />
		<AddBook @book-added="handleBookAdded" />
		<SearchBar @book-searched="handleBookSearch" />
		<BookList @book-deleted="handleBookDeleted" :books="filteredBooks" />
	</main>
</template>
