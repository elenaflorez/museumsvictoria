<!-- this component returns a list of all the buildings -->
<template>
	<div class="">
		<!-- these would show while the data loads or if an error -->
		<p v-if="$fetchState.pending">Loading buildings...</p>
		<p v-else-if="$fetchState.error">Error while fetching buildings</p>

		<ul v-else class="list-group">
			<!-- this is a for loop, it just loops through the list of buildings returned from the API -->
			<li v-for="building in buildings" :key="building.id" class="list-group-item">
				<!-- now make a link for each item -->
				<!-- <NuxtLink :to="building.slug"> -->
				<NuxtLink class="pagelink" :to="'/buildings/' + building.slug">
					<!-- return the rendered title -->
					{{  building.title.rendered  }}
				</NuxtLink>
			</li>
		</ul>

	</div>
</template>


<script>
export default {
	// layout: 'home',
	async fetch() {
		this.buildings = await fetch('http://cm.beneb.com/wp-json/wp/v2/buildings/?per_page=5').then((res) =>
			res.json()
		)
	},
	data() {
		return {
			buildings: [],
		}
	},
}
</script>

<style scoped>
	.htmlReturn ::v-deep(p){ font-size:50px}
	 
</style>