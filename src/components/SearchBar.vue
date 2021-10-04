<template>
  <form class="d-flex">
	<input class="form-control" type="text" placeholder="search character" v-model="inputText">
	<button type="submit" class="btn btn-primary mx-3" @click.prevent="$emit('search', inputText)">Search</button>
	<button class="btn btn-warning" @click.prevent="resetSearch">Reset</button>
  </form>
</template>

<script>
export default {
	name: 'SearchBar',
	data() {
		return {
			inputText: ""
		}
	},
	methods: {
		resetSearch() {
			this.inputText = "";
			this.$emit('search', this.inputText);
		}
	}
}
</script>