<!-- this component can hold site navigation -->
<!-- if we put it here we can avoid having to repeat the code -->
<template>
	<nav>
    <p><NuxtLink class="blue" to="/">
      Home
    </NuxtLink></p>
		<p><NuxtLink class="red" to="/buildings">
      Buildings
    </NuxtLink></p>
    <p><NuxtLink class="orange" to="/events">
      Events
    </NuxtLink></p>
	</nav>
</template>
<script>

</script>

<!--You can put whatever you want down here to affect the styling of the nav-->
<style>
   nav {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

  .blue {
		color: #007bff;
		text-shadow: -1px -1px 0 grey, 1px -1px 0 grey, -1px 1px 0 grey, 1px 1px 0 grey;
	}
  .yellow {
		color: #eda384;
		text-shadow: -1px -1px 0 grey, 1px -1px 0 grey, -1px 1px 0 grey, 1px 1px 0 grey;
	}
  .red {
		color: #fae382;
		text-shadow: -1px -1px 0 black, 1px -1px 0 black, -1px 1px 0 black, 1px 1px 0 black;
	}
  .orange {
		color: #f37175;
		text-shadow: -1px -1px 0 black, 1px -1px 0 black, -1px 1px 0 black, 1px 1px 0 black;
	}


</style>