<template>
	<div class="container">

		<body>
			<header>
				<SiteNavigation />
			</header>
			<section class="intro">
				<h1>Explore a world full of possibilities</h1>
				<h2>Explore and find what you're interested in</h2>
				<hr class="bar">
			</section>
			<section>
				<Search />
			</section>
			<footer>
				<Social />
			</footer>
		</body>
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
	font-size: 6vw;
	text-align: center;
}

h2 {
	font-size: 5vw;
}

h3 {
	font-size: 4vw;
}

h4 {
	font-size: 3.5vw;
}

p {
	font-size: 3vw;
}

/* Intro styling  */
.intro {
	padding-top: 20px;
	text-align: center;
}

.bar {
	border-top: 1px solid #539844;
}

@media only screen and (min-width: 800px) {

	/* DESKTOP TEXT STYLE */
	h1 {
		font-size: 3vw;
		text-align: center;
	}

	h2 {
		font-size: 2vw;
	}

	h3 {
		font-size: 1.5vw;
	}

	h4 {
		font-size: 1vw;
	}

	p {
		font-size: 1vw;
	}

	/* OTHER DESKTOP STYLE */
	body {
		min-height: 100vh;
		margin: 0;

		display: grid;
		grid-template-rows: auto 1fr auto;
	}

	header {
		min-height: 50px;
	}

	footer {
		min-height: 50px;
		background: PapayaWhip;
	}

}
</style>


