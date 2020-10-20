<template lang="html">
	<main>
		<h1>Country Info</h1>
		<select name="country-dropdown" v-on:click="fetchCountry">
			<option v-for="country in countries">{{ country.name }}</option>
		</select>
	</main>
</template>

<script>
export default {
	name: 'App',
	data() {
		return {
			countries: []
		};
	},
	mounted() {
		this.fetchCountry();
	},
	methods: {
		fetchCountry: function() {
			fetch('https://restcountries.eu/rest/v2/all')
				.then((response) => response.json())
				.then((data) => (this.countries = data));
		}
	}
};
</script>

<style lang="css" scoped></style>
