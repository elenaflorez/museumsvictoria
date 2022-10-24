<template>
	<div class="content">

		<!-- Map addition -->
		<div class="parent">
            <img class="image1" src="@/Images/Simple_world_map.png" />
            <span @click="setValue" class="dot image2"></span>
        </div>

        <input type="text" placeholder="Search" class="search-input" v-model="searchValue"/>
		{{ searchValue }}
        {{ searchURL }}

        <button @click="getEvents">Search</button>

		<p v-if="$fetchState.pending"> <span class="loading"></span></p>
		<p v-else-if="$fetchState.error">Error while fetching events</p>
            
		<ul v-else class="list-group">
			<li v-for="event in events" :key="event.id" class="list-group-item">
				<p><NuxtLink class="pagelink" :to="event.id">
					{{ event.displayTitle }}
				</NuxtLink></p>
				<p>Category: {{ event.category }}, Discipline: {{ event.discipline }}, Classifications: {{ event.classifications }}</p>
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
            apiURL: 'https://collections.museumsvictoria.com.au/api/search?locality=',
		}
	},
    methods: {
		async setValue() {
			this.searchValue = 'Germany'
		},
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