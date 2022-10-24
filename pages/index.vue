<template>
	<div class="container">

		<h4>TESTING SEARCH</h4>
		<Search />

	</div>
</template>

<script>
import Search from '../components/Search.vue';
export default {
    name: "IndexPage",
    data: () => ({
        searchValue: "",
    }),
    components: { Search }
}
</script>

<style>
/* NEW STYLE */
.search-input {
	width: 200px; 
	height:30px;
	border-radius: 2px;
}
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
.image1 {
  position: relative;
  top: 0;
  left: 0;
  border: 1px red solid;
  max-width:100%
}
.image2 {
  position: absolute;
  top: 20%;
  left: 20%;
  border: 1px green solid;
}
/* END NEW STYLE */
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


