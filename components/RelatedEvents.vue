<!-- this component returns a list of all the buildings -->
<template>
	<div class="">
		<!-- these would show while the data loads or if an error -->
		<p v-if="$fetchState.pending">Loading events...</p>
		<p v-else-if="$fetchState.error">Error while fetching events</p>

		<ul v-else class="list-group">
			<!-- this is a for loop, it just loops through the list of buildings returned from the API -->
			<li v-for="event in events" :key="event.id" class="list-group-item">
				<!-- now make a link for each item -->
				<NuxtLink class="pagelink" :to="'/events/' + event.slug">
					<!-- return the rendered title -->
					{{  event.title.rendered  }}
				</NuxtLink>
			</li>
		</ul>

	</div>
</template>


<script>
export default {
	// layout: 'home',
	async fetch() {
		this.events = await fetch('http://cm.beneb.com/wp-json/wp/v2/events/?per_page=5').then((res) =>
			res.json()
		)
	},
	data() {
		return {
			events: [],
		}
	},
}
</script>

<style scoped>
	.htmlReturn ::v-deep(p){ font-size:1fr}
	 
</style>