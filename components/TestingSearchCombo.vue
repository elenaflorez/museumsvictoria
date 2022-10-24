<template>
	<div class="content">

        <!-- Filtering List idea -->
        <input type="text" placeholder="Search" class="search-input" v-model="searchValue"/>
		{{ searchValue }}
        {{ searchURL }}

        <button @click="getEvents">Refresh</button>

		<p v-if="$fetchState.pending"> <span class="loading"></span></p>
		<p v-else-if="$fetchState.error">Error while fetching events</p>
            
		<ul v-else class="list-group">
			<li v-for="event in events" :key="event.id" class="list-group-item">
				{{ event }}
			</li>
		</ul>

	</div>
</template>


<script>
import { throws } from 'assert';

export default {
	//data will return an array
	data() {
		return {
			//empty array to be filled
			events: [],
            searchValue: '',
            searchURL: '',
            apiURL: 'https://collections.museumsvictoria.com.au/api/search?recordtype=',
		}
	},
    methods: {
        async getEvents () {
            // this.searchValue='HAHA YOU SPRUNG MY TRAP'
            // apiURL = 'https://collections.museumsvictoria.com.au/api/search?recordtype='
            this.searchURL = this.apiURL.concat(this.searchValue)
            let apiData = await fetch(this.searchURL)
		.then((response) =>
			response.json()
		)
		// // create empty araay
		let yearArr = [];
		//loop through events/events array
		for (let i = 0; i < apiData.length; i++) {
            yearArr.push(apiData[i]);
		} 
		//now set events to be the yearArray 
		this.events = yearArr;
        }
    },
	//now go get the data
	async fetch() {
		//make the api call and fill the empty events array
		
	},
	computed: {
        usersList() {
            if (this.searchValue.trim().length > 0) {
                return []
            }
            return this.users
        }
    }
	
}
</script>