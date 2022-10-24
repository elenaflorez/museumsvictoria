<template>
	<div class="container">

		<SiteNavigation />
		<header>
			<h1>All Buildings</h1>
		</header>

		<section>
			<figure><img class="quoteImage" src="@/Images/quote2.png" alt="Banner" /></figure> 
		</section>


		<div class="building">
			<!-- The building list is over in the components folder -->
			<!-- the code below loads the component here so we can use it again -->
			<BuildingsList />

			<!-- this is a really useful line of code that will just output what the API call returns -->
			<!-- <pre>{{ $data }}</pre> -->
		</div>
		<Social />
	</div>
</template>

<script>
// in this API call, we go get a specifci building, filtered by the ID in the URL
// we access what is in the URL by using the params object
/* export default {
	async asyncData({ params }) {
		const building = await fetch(
			`http://cm.beneb.com/wp-json/wp/v2/buildings/`
		).then((res) => {
			if (res.ok) {
				return res.json()
			}
			throw new Error(res.status)
		})
		return { building }
	},
} */
</script>


<style>
</style>