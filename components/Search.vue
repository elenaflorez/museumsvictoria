<template>
	<div class="content">

		<!-- Map used for setting locality -->
		<section>
			<h2>Are you interested in a part of the world?</h2>
			<p>(No need to select all of the below before searching!)</p>
			<div class="parent">
				<img class="map" src="@/Images/Simple_world_map.png" />
				<span @click="setLocality('Germany')" class="dot germany"></span>
				<span @click="setLocality('Australia')" class="dot australia"></span>
				<span @click="setLocality('Ghana')" class="dot ghana"></span>
				<span @click="setLocality('Mexico')" class="dot mexico"></span>
			</div>
			<hr class="bar">
		</section>

		<!-- Section for setting category -->
		<section>
			<h2>Are you interested in any of these categories?</h2>
			<article class="imageBox">
				<div class="imageContainer" @click="setCategory('First Peoples')">
					<img src="@/Images/Indigenous Australian.png" alt="First Peoples" class="image">
					<div class="middle">
						<div class="text">First Peoples</div>
					</div>
				</div>
				<div class="imageContainer" @click="setCategory('history+%26+technology')">
					<img src="@/Images/History and Tech.png" alt="History & Technology" class="image">
					<div class="middle">
						<div class="text">History & Technology</div>
					</div>
				</div>
			</article>
			<hr class="bar">
		</section>

		<section>
			<h2>What about these?</h2>
			<article class="imageBox">
				<div class="imageContainer" @click="setCollectionArea('sustainable futures')">
					<img src="@/Images/Science.png" alt="Science" class="image">
					<div class="middle">
						<div class="text">Sustainable Futures</div>
					</div>
				</div>
				<div class="imageContainer" @click="setCollectionArea('migration+%26+cultural+diversity')">
					<img src="@/Images/Diversity.png" alt="Diversity" class="image">
					<div class="middle">
						<div class="text">Migration & Cultural Diversity</div>
					</div>
				</div>
			</article>
			<hr class="bar">
		</section>

		<!-- Button for running API query -->
		<button class="go-button" @click="getItems">Go!</button>
		<hr class="bar">

		<!-- Allow user filter for specific title value -->
		<section class="filterSearchBox">
			<div>
				<h4>Searching for: {{ localityDisplay }} {{ categoryDisplay }} {{ collectionAreaDisplay }}</h4>
			</div>
			<div><input type="text" placeholder="Filter Results" class="search-input" v-model="userSearch" /></div>
			<div><button class="clear-button" @click="clear">Clear</button></div>
		</section>
		<hr class="bar">

		<p v-if="items == []">No results</p>

		<section>
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
		</section>
	</div>
</template>


<script>
import { throws } from 'assert';

export default {
	data() {
		return {
			items: [],

			// Query fields - used as input into API
			localityValue: '',
			categoryValue: '',
			collectionAreaValue: '',

			// Display fields - to show what is being put in the query
			localityDisplay: '',
			categoryDisplay: '',
			collectionAreaDisplay: '',

			// Filter field - used to filter result from API
			userSearch: '',

			// Initialised full URL for debugging
			searchURL: '',
		}
	},
	methods: {
		// Used to set values for API query
		async setLocality(locality) {
			let baseString = '&locality='
			this.localityValue = baseString.concat(locality)
			this.localityDisplay = locality
		},
		async setCategory(category) {
			let baseString = '&category='
			this.categoryValue = baseString.concat(category)
			this.categoryDisplay = category
		},
		async setCollectionArea(collectionarea) {
			let baseString = '&collectingarea='
			this.collectionAreaValue = baseString.concat(collectionarea)
			this.collectionAreaDisplay = collectionarea
		},

		// Clears inputs 
		async clear() {
			this.localityValue = ''
			this.categoryValue = ''
			this.collectionAreaValue = ''
			this.userSearch = ''
			this.localityDisplay = ''
			this.categoryDisplay = ''
			this.collectionAreaDisplay = ''
		},

		// Runs API query and returns the results
		async getItems() {
			// General API search URL
			let apiURL = 'https://collections.museumsvictoria.com.au/api/search?recordtype=item' // can use recordtype, perpage, and page

			// Add query data from page
			let query = this.localityValue.concat(this.collectionAreaValue).concat(this.categoryValue)
			this.searchURL = apiURL.concat(query)

			//Fetch Data
			let apiData = await fetch(this.searchURL)
				.then((response) =>
					response.json()
				)

			// Filter return from API
			let Arr = [];
			for (let i = 0; i < apiData.length; i++) {
				// First check that there is a user inputted search
				if (this.userSearch == '') {
					Arr.push(apiData[i]);
				} else {
					// Check if search term is in the display title, if yes add to return
					if (apiData[i].displayTitle.includes(this.userSearch)) {
						Arr.push(apiData[i]);
					}
				}
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
/* Map Styling */
.dot {
	height: 25px;
	width: 25px;
	background-color: #539844;
	border-radius: 50%;
	display: inline-block;
	cursor: pointer;
	border: 1px solid red;
}

.dot:hover {
	background-color: red;
}

.parent {
	position: relative;
	top: 0;
	left: 0;
}

.map {
	display: block;
	margin-left: auto;
	margin-right: auto;
	border-radius: 5%;
	max-width: 100%
}

.germany {
	position: absolute;
	top: 21%;
	left: 49%;
}

.australia {
	position: absolute;
	top: 72%;
	left: 83%;
}

.ghana {
	position: absolute;
	top: 49%;
	left: 47%;
}

.mexico {
	position: absolute;
	top: 40%;
	left: 15%;
}

/* Images Styling */

.imageBox {
	display: flex;
	flex-direction: column;
}

.imageContainer {
	position: relative;
	width: 100%;
}

.image {
	opacity: 1;
	display: block;
	width: 100%;
	height: auto;
	transition: .5s ease;
	backface-visibility: hidden;
}

.middle {
	transition: .5s ease;
	opacity: 0;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	-ms-transform: translate(-50%, -50%);
	text-align: center;
}

.imageContainer.image {
	opacity: 0.3;
	cursor: pointer;
}

.imageContainer .middle {
	opacity: 1;
	cursor: pointer;
}

.text {
	background-color: #539844;
	color: white;
	font-size: 16px;
	padding: 16px 32px;
}

/* Go Button Styling */
.go-button {
	background-color: red;
	padding: 15px 32px;
	border-radius: 5px;
	display: block;
	text-align: center;
	color: white;
	margin: 0 auto
}

.go-button:hover {
	border: 2px solid red;
	background-color: white;
	color: red;
}

/* Filter and Search Set Styling */
.filterSearchBox {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}

/* Filter Styling */
.search-input {
	width: 200px;
	height: 30px;
	border-radius: 2px;
}

/* Clear Button Styling */
.clear-button {
	background-color: white;
	border-color: black;
	padding: 7px 15px;
	border-radius: 5px;
	display: block;
	text-align: center;
	color: black;
	margin: 0 auto
}

.clear-button:hover {
	border: 2px solid blue;
	background-color: white;
	color: blue;
}

/* Return Styling */
.list-group-item .pagelink {
	color: #539844;
}

.truncate {
	width: 300px;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}

@media only screen and (min-width: 800px) {
	.imageBox {
		flex-direction: row;
	}

	.imageContainer {
		width: 50%;
	}

	.imageContainer.image {
		opacity: 0;
		cursor: pointer;
	}

	.imageContainer .middle {
		opacity: 0;
		cursor: pointer;
	}

	.imageContainer:hover .image {
		opacity: 0.3;
		cursor: pointer;
	}

	.imageContainer:hover .middle {
		opacity: 1;
		cursor: pointer;
	}

	.truncate {
		width: 800px;
	}

	.filterSearchBox {
		flex-direction: row;
	}
}
</style>