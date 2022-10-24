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
				<p><NuxtLink class="pagelink" :to="'/buildings/' + building.slug">
					<!-- return the rendered title -->
					{{  building.title.rendered  }}
				</NuxtLink>
				<!-- now show me the building year -->
				: {{ building.acf.year }}</p>
			</li>
		</ul>
	</div>
</template>


<script>
export default {
	// layout: 'home',
	async fetch() {
		this.buildings = await fetch('http://cm.beneb.com/wp-json/wp/v2/buildings/?per_page=20').then((res) =>
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

<style>
	.list-group-item {
		background-color: #fae382;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		
	}
	.pagelink {
		color: white;
		text-shadow: -1px -1px 0 #007bff, 1px -1px 0 #007bff, -1px 1px 0 #007bff, 1px 1px 0 #007bff;
	}
</style>