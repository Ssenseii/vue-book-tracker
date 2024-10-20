<script setup>
import { ref, defineEmits } from "vue";

const bookName = ref("");
const bookRating = ref(0);
const bookProgress = ref("");

const emit = defineEmits(["bookAdded"]);

const onSubmit = () => {
	if (bookName.value === "" || bookProgress.value === "") {
		window.alert("All Inputs Must be Filled");
		return 0;
	}

	if (bookRating.value < 0 || bookRating.value > 5) {
		window.alert("Rating must be between 0 and 5");
		return 0;
	}

	const bookData = {
		id: crypto.randomUUID(),
		bookName: bookName.value,
		bookRating: bookRating.value,
		bookProgress: bookProgress.value,
	};

	emit("bookAdded", bookData);
};
</script>

<template>
	<form id="form" @submit.prevent="onSubmit">
		<div>
			<label for="bookName">Book Name:</label>
			<input id="bookName" v-model="bookName" name="bookname" type="text" />
		</div>
		<div>
			<label for="bookRating">Book Rating: </label>
			<input
				v-model="bookRating"
				name="bookRating"
				id="bookRating"
				type="number"
				min="0"
				max="5"
				step="1"
			/>
		</div>
		<div>
			<label for="bookProgress">Book Progress: </label>
			<select name="bookProgress" v-model="bookProgress" id="bookProgress">
				<option value="Not Started">Not Started</option>
				<option value="In Progress">In Progress</option>
				<option value="Finished">Finished</option>
			</select>
		</div>
		<button type="submit">Add Book</button>
	</form>
</template>

<style scoped>
form {
	margin: 2rem;
	display: flex;
	flex-direction: column;
	gap: 1rem;
}

input,
select {
	border: 1px solid gray;
	border-radius: 4px;
	width: 100%;
	padding-inline: 0.5rem;
}

button {
	background-color: black;
	color: white;
	border-radius: 8px;
	height: 32px;
}
</style>
