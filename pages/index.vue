<template>
	<div class="container">
		<SiteNavigation />
		<section class="bannerContainer">
        	<img class="bannerImage" src="@/Images/BannerImage.png" alt="Banner" />
        	<div class="bannerText">
          		<h1 class="titleText">Canberra Modern</h1>
          		<h2 class="titleText">Conservation through participation </h2>
        	</div>
    	</section>

		<!-- START TESTING -->
		<!-- <EventbyYear /> THIS WORKS AND ITS GOOD -->

		<!-- <input type="text" placeholder="Search" class="search-input" v-model="searchValue"/>
		{{ searchValue }} -->
		
		<!-- <h4>TESTING FIELD</h4>
		<TestingSearch /> -->

		<h4>TESTING SEARCH</h4>
		<TestingSearchCombo />

		<!-- <TestingSpecies /> -->

		<!-- END TESTING -->
		<h2>Showcase Events</h2>
		<section class = "eventsContainer">
			<article>
				<NuxtLink class="pagelink" :to="'/events/gala-the-dressmaker-1950s-vintage-ball-at-the-nfsa'">
					<img class="eventImage" src="@/Images/Canberra Modern Presents 1.png" alt="Banner" />
					<p>Love to dress up? - The Dressmaker 1950s Vintage Ball at the NFSA</p>
				</NuxtLink>
			</article>
			

			<article>
				<NuxtLink class="pagelink" :to="'/events/cocktails-talk-martinis-at-manning-clark-house'">
					<img class="eventImage" src="@/Images/Canberra Modern Presents 2.png" alt="Banner" />
					<p>Love to go out? - Martinis at Manning Clark House</p>
				</NuxtLink>
			</article>

			<article>
				<NuxtLink class="pagelink" :to="'/events/talk-australians-and-the-marimekko-mystique-1954-75'">
					<img class="eventImage" src="@/Images/Canberra Modern Presents 3.png" alt="Banner" />
					<p>Love history and design? - Australians and the Marimekko Mystique</p>
				</NuxtLink>
			</article>
		</section>
		<h2>Upcoming Events</h2>
		<ShowcaseEvents />

		<Social />

	</div>
</template>

<script>
import TestingSearchCombo from '../components/TestingSearchCombo.vue';
export default {
    name: "IndexPage",
    data: () => ({
        searchValue: "",
    }),
    components: { TestingSearchCombo }
}
</script>

<style>
/* TESTING */
.search-input {
	width: 200px; 
	height:30px;
	border-radius: 2px;
}
/* END TESTING */
* {
	font-family: Futura;
}

h1 {
	font-weight:950;
	font-size:6vw;
	text-align:center;
}

h2 {
	font-weight:700;
	font-style:italic;
	font-size:5vw;
}

h3 {
	font-weight:500;
	font-size:4vw;
}

p {
	font-size:3vw;
}

.bannerContainer {
    position: relative;
    text-align: center;
}

.bannerImage {
  width:100%
}

.eventImage {
	width:30%;
	margin-left: auto;
	margin-right: auto;
	display:block;
}

.bannerText {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0,0,0,0.5);
  font-size:6vw;
}

.titleText {
	color:white;
}

.eventsContainer {
	display: flex;
    flex-direction:column; /*Reactive sizing for these columns */
    /* column-gap: 10% */
}

@media only screen and (min-width: 800px) {
    h1 {
	font-weight:950;
	font-size:4vw;
	text-align:center;
}

h2 {
	font-weight:700;
	font-style:italic;
	font-size:3vw;
}

h3 {
	font-weight:500;
	font-size:2.5vw;
}

p {
	font-size:2vw;
}
.eventsContainer {
	display: grid;
    grid-template-columns: 1fr 1fr 1fr; /*Reactive sizing for these columns */
    column-gap: 10%
}
.eventImage {
	width:100%
}

  }

</style>


