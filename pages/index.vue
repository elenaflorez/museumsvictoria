<template>
	<div class="container">
		<h1>H1</h1>
		<h2>H2</h2>
		<h3>H3</h3>
		<h4>H4</h4>
		<SiteNavigation />
		<h4>SEARCH</h4>
		<Search />
	</div>
</template>

<script>
import Search from '../components/Search.vue';
export default {
	name: "IndexPage",
	data: () => ({
		searchValue: "",
	}),
	components: { Search }
}
</script>

<style>
/* ALL TEXT STYLE */
* {
	font-family: Arial;
}

/* MOBILE TEXT STYLE  */
h1 {
	font-weight: 950;
	font-size: 6vw;
	text-align: center;
	font-family: Palatino;
}

h2 {
	font-weight: 700;
	font-style: italic;
	font-size: 5vw;
}

h3 {
	font-weight: 500;
	font-size: 4vw;
}

p {
	font-size: 3vw;
}

@media only screen and (min-width: 800px) {
	/* DESKTOP TEXT STYLE */
	h1 {
		font-weight: 950;
		font-size: 4vw;
		text-align: center;
	}

	h2 {
		font-weight: 700;
		font-style: italic;
		font-size: 3vw;
	}

	h3 {
		font-weight: 500;
		font-size: 2.5vw;
	}

	p {
		font-size: 2vw;
	}

}
</style>


