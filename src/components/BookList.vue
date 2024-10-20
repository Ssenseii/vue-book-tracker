<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["bookDeleted"]);

const props = defineProps({
	books: {
		type: Array,
		required: false,
	},
});

const editBook = (id) => {
	emit("bookEdited", id);
};

const deleteBook = (id) => {
	emit("bookDeleted", id);
    console.log("book deletion emited:", id);
};
</script>

<template>
	<table>
		<thead>
			<th>Book Name</th>
			<th>Book Rating</th>
			<th>Book Progress</th>
			<th>Actions</th>
		</thead>
		<tbody>
			<tr v-for="book in books" :key="book.id">
				<td>{{ book.bookName }}</td>
				<td>{{ book.bookRating }}</td>
				<td>{{ book.bookProgress }}</td>
				<td>
					<button @click="editBook(book.id)">Edit</button>
					<button @click="deleteBook(book.id)">Delete</button>
				</td>
			</tr>
		</tbody>
	</table>
</template>

<style scoped>
table {
	margin: 2rem;
	border-radius: 2rem;
}

thead {
	background-color: lightgray;
}

td,
th {
	border: 1px solid lightslategray;
	padding: 0.5rem 1rem;
}

button {
	background-color: lightslategray;
	color: white;

	padding-inline: 0.5rem;
	margin-inline: 0.25rem;

	border-radius: 0.5rem;
}
</style>
