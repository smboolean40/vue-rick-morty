<template>
  <section class="characters container">
	<div class="row mb-5">
		<div class="col-12">
			<SearchBar @search="searchCharacters"/>
		</div>
	</div>
	<div class="row">
		<div class="col-6 col-md-4 col-lg-3 mb-3" v-for="(elm, index) in charactersFiltered" :key="index">
			<Character :info="elm"/>
		</div>
	</div>
  </section>
</template>

<script>
import axios from 'axios';
import Character from './Character.vue';
import SearchBar from './SearchBar.vue';

export default {
	name: "Characters",
	components: {
		Character,
		SearchBar
	},
	data() {
		return {
			characters: [],
			searchText: ""
		}
	},
	created() {
		axios
			.get("https://api.sampleapis.com/rickandmorty/characters")
			.then( (res) => {
				this.characters = res.data;
			});
	},
	methods: {
		searchCharacters(text) {
			this.searchText = text;
		}
	},
	computed: {
		charactersFiltered() {
			const arrFiltered = this.characters.filter(
				(elm) => {
					// console.log("dentro al filtro");
					return elm.name.toLowerCase().includes(this.searchText.toLowerCase()); // true o false
				}
			);

			return arrFiltered;
		}
	}
}
</script>

<style lang="scss" scoped>

</style>