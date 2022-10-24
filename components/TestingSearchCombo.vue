<template>
	<div class="content">

		<div class="parent">
            <img class="image1" src="@/Images/Simple_world_map.png" />
            <span @click="setLocality('Germany')" class="dot image2"></span>
        </div>

        <input type="text" placeholder="Search" class="search-input" v-model="localityValue"/>
		{{ localityValue }}
		{{ categoryValue }}
        {{ searchURL }}
		<button @click="setCategory('First Peoples')">First Peoples</button>

        <button @click="getItems">Search</button>

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
            localityValue: '',
			categoryValue: '',
            searchURL: '',
            apiURL: 'https://collections.museumsvictoria.com.au/api/search?',
		}
	},
    methods: {
		async setLocality(locality) {
			let baseString = '&locality='
			this.localityValue = baseString.concat(locality)
		},
		async setCategory(category) {
			let baseString = '&category='
			this.categoryValue = baseString.concat(category)
		},
        async getItems () {
            // apiURL = 'https://collections.museumsvictoria.com.au/api/search?recordtype='
			// https://collections.museumsvictoria.com.au/api/search?category=First Peoples&perpage=100&page=20
			let query = this.localityValue.concat(this.categoryValue)
            this.searchURL = this.apiURL.concat(query)
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