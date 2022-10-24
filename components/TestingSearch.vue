
<template>
	<div class="">

		<h4>Button</h4>
        <button @click="search">Search</button>

        <h4>Result</h4>
        {{ searchString }}

        <h4>Encoded</h4>
        {{ encoded }}   
    
	</div>
</template>

<script>
export default {
    data() {
		return {
            searchString: 'searchString start',
            encoded: 'encoded start',
			events: [],
            searchValue: '',
		}
	},
    methods: {
        async search() {
        this.searchString = 'test';
        console.log('test')
        this.encoded = encodeURIComponent('test1234 2')

        apiURL = 'https://collections.museumsvictoria.com.au/api/search?recordtype='
        searchURL = apiURL.concat(this.searchValue)
    },
    }
    
	
}
</script>