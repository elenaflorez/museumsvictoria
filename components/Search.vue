<template>
	<div class="content">
		
		<!-- Map used for setting locality -->
		<div class="parent">
            <img class="map" src="@/Images/Simple_world_map.png" />
            <span @click="setLocality('Germany')" class="dot germany"></span>
        </div>
		<!-- Field used to set locality manually for testing/debugging -->
		<input type="text" placeholder="Search" class="search-input" v-model="localityValue"/>

		<!-- Section for setting category -->
		<button @click="setCategory('First Peoples')">First Peoples</button>

		<!-- Allow user search for specific title value -->
		<input type="text" placeholder="UserSearch" class="search-input" v-model="userSearch"/>

		<!-- Button for running API query -->
        <button @click="getItems">Search</button>

		<!-- Outputs for debugging and testing -->
		{{ localityValue }}
		{{ categoryValue }}
        {{ searchURL }}

		<p v-if="$fetchState.pending"> <span class="loading"></span></p>
		<p v-else-if="$fetchState.error">Error while fetching items</p>
        
		<ul v-else class="list-group">
			<li v-for="item in items" :key="item.id" class="list-group-item">
				<p><NuxtLink class="pagelink" :to="item.id">
					{{ item.displayTitle }}
				</NuxtLink></p>
				<p>Category: {{ item.category }}, Discipline: {{ item.discipline }}, Classifications: {{ item.classifications }}</p>
			</li>
		</ul>

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
		},
		async setCategory(category) {
			let baseString = '&category='
			this.categoryValue = baseString.concat(category)
		},

		// Runs API query and returns the results
        async getItems () {
			// General API search URL
			let apiURL = 'https://collections.museumsvictoria.com.au/api/search?' // can use recordtype, perpage, and page
					
			// Add query data from page
			let query = this.localityValue.concat(this.categoryValue)
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
  background-color: blue;
  border-radius: 50%;
  display: inline-block;
}
.parent {
  position: relative;
  top: 0;
  left: 0;
}
.map {
  position: relative;
  top: 0;
  left: 0;
  border: 1px red solid;
  max-width:100%
}
.germany {
  position: absolute;
  top: 20%;
  left: 20%;
}

/* Search styling */
.search-input {
	width: 200px; 
	height:30px;
	border-radius: 2px;
}
</style>