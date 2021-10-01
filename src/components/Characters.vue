<template>
  <section class="characters container">
	<div class="row">
		<div class="col-6 col-md-4 col-lg-3 mb-3" v-for="(elm, index) in characters" :key="index">
			<Character :info="elm"/>
		</div>
	</div>
  </section>
</template>

<script>
import axios from 'axios';
import Character from './Character.vue';

export default {
	name: "Characters",
	components: {
		Character
	},
	data() {
		return {
			characters: []
		}
	},
	created() {
		axios
			.get("https://api.sampleapis.com/rickandmorty/characters")
			.then( (res) => {
				this.characters = res.data;
			});
	}
}
</script>

<style lang="scss" scoped>

</style>