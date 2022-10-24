<template>
	<div class="container">
		<h2>{{ $route.params.slug }}</h2>
		<h3>Filename: pages/_pages.vue</h3>

		<SiteNavigation />

		<div class="page">
			<!-- the buiding returns an array with one item in it, so need to reference it below -->

			<pre>{{ $data }}</pre>
			<h2>{{page[0].id}}</h2>
			<h4>{{page[0].content.rendered}}</h4>
			<div v-html="page[0].content.rendered"></div>
		</div>
	</div>
</template>

<script>
// in this API call, we load a page based off the URL paramter
// we access what is in the URL by using the params object
export default {
	async asyncData({ params }) {
		const page = await fetch(
			// `http://cm.beneb.com/wp-json/wp/v2/pages/?slug=${params.slug}`
			// `http://cm.beneb.com/wp-json/wp/v2/pages/157`
			`http://cm.beneb.com/wp-json/wp/v2/pages/?slug=${params.slug}`
		).then((res) => {
			if (res.ok) {
				return res.json()
			}
			throw new Error(res.status)
		})
		return { page }
	},
}
</script>
