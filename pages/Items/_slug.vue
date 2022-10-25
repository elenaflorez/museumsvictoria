<template>
	<div class="container">
        <SiteNavigation />

        <p>Display Title: {{item.displayTitle}}</p>
        <p>Object Summary: {{item.objectSummary}}</p>
        <p>Physical Description: {{item.physicalDescription}}</p>
        <p>Category: {{item.Category}}</p>
        <p>Keywords: {{item.keywords}}</p>
        <p>Classifications: {{item.classifications}}</p>
        <p>Collections: {{item.collectionNames}}</p>
        <p>Item: {{item.Category}}</p>
		
	</div>
</template>

<script>
export default {
	async asyncData({ params }) {
		const item = await fetch(
			`https://collections.museumsvictoria.com.au/api/items/${params.slug}`
		).then((res) => {
			if (res.ok) {
				return res.json()
			}
			throw new Error(res.status)
		})
		return { item }
	},
}
</script>

<style>

	.descripton :v-deep(p){
		font-size:100px;    
	}

	.description ::v-deep(p){ font-size:3fr}

	.image {

	}

	@media only screen and (min-width: 800px) {

  }
</style>