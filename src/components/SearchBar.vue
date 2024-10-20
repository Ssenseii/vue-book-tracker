<script setup>
import { defineEmits, ref } from "vue";

const searchterm = ref("");
const emit = defineEmits(["bookSearched"]);

const searchForBook = () => {
	emit("bookSearched", searchterm.value);
};
</script>

<template>
	<input
		v-model="searchterm"
		v-on:input="searchForBook"
		id="searchbar"
		type="text"
		placeholder="search here..."
	/>
</template>

<style scoped>
input {
	border: 1px solid gray;
	border-radius: 8px;
	height: 36px;
	width: 256px;

	padding-inline: 1rem;
}
</style>
