<template>
	<div class="container">

		<body>
			<header>
				<SiteNavigation />
				<hr class="bar">
			</header>
			
			<!-- Item details -->
			<section>
				<h2>{{ item.displayTitle }}</h2>
			</section>
			<section>
				<article class="itemDescriptionBox">
					<p class="itemDescription">Object Summary: {{ item.objectSummary }}</p>
				</article>
			</section>

			<section>
				<!-- Filter for related items -->
				<article>
					<p>Follow your interest</p>
					<button class="linkButton" @click="getItems('&category='.concat(item.category))">Category:
						{{ item.category }}</button>
					<button class="linkButton" @click="getItems('&locality='.concat(item.locality))">Locality:
						{{ item.locality }}</button>
				</article>
				
				<!-- Related items -->
				<article>
					<p v-if="$fetchState.pending">Loading items...<span class="loading"></span></p>
					<p v-else-if="$fetchState.error">Error while fetching items</p>
					<ul v-else class="list-group">
						<li v-for="item in items" :key="item.id" class="list-group-item">
							<p>
								<NuxtLink class="pagelink" :to="item.id">
									{{ item.displayTitle }}
								</NuxtLink>
							</p>
							<p class="truncate">{{ item.objectSummary }}</p>
						</li>
					</ul>
				</article>
				<hr class="bar">
			</section>

			<footer>
				<Social />
			</footer>
		</body>

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
	data() {
		return {
			items: [],
		}
	},
	methods: {
		async getItems(input) {
			// General API search URL
			let apiURL = 'https://collections.museumsvictoria.com.au/api/search?recordtype=item&perpage=10' // can use recordtype, perpage, and page

			// Add query data from page
			this.searchURL = apiURL.concat(input)

			//Fetch Data
			let apiData = await fetch(this.searchURL)
				.then((response) =>
					response.json()
				)
			let Arr = [];
			for (let i = 0; i < apiData.length; i++) {
				Arr.push(apiData[i]);
			}
			this.items = Arr;
		}
	},
	async fetch() {
		//make the api call and fill the empty events array
	},
}

</script>

<style>
header {
	padding-top: 20px;
	background-color: white;
}

/* Button styling */
.linkButton {
	background-color: #539844;
	padding: 7px 15px;
	border-radius: 5px;
	display: inline-block;
	text-align: center;
	color:white;
	margin: 0 auto
}

/* Description Styling */
.itemDescriptionBox {
	background-color: #f8eb47;
	width: 100%;
	border-radius: 5px;
	box-shadow: 10px 10px 8px -4px #e3e3e3;
}

.itemDescription {
	padding: 10px;
}

@media only screen and (min-width: 800px) {}
</style>