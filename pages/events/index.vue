<template>
	<div class="container">
		<SiteNavigation />
		<h1>
			All Events
		</h1>
		<section>
			<figure><img class="presentsImage" src="@/Images/Canberra Modern Presents 1.png" alt="Banner" /></figure> 
		</section>
		<div class="building">
			<!-- The building list is over in the components folder -->
			<!-- the code below loads the component here so we can use it again -->
			<EventsList/>

			<!-- this is a really useful line of code that will just output what the API call returns -->
			<!-- <pre>{{ $data }}</pre> -->
		</div>
		<Social />
	</div>
</template>

<script>
</script>


<style>
	.presentsImage {
		width:40%;
		display:block;
		margin-left: auto;
		margin-right: auto;
	}
</style>