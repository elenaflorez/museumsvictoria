<template>
	<div class="container">

		<SiteNavigation />
		<header>
			<h1>{{  building[0].title.rendered  }}</h1>
			<h2>{{ building[0].acf.year }}</h2>
			<p>Risk Status: {{ building[0].acf.risk_status }}</p>
		</header>
		<section class="buildingInfoContainer">
			<article class="address">
				<h3>
					Address:
				</h3>
				<p>
					{{  building[0].acf.location  }}
				</p>
			</article>
			<article class="suburb">
				<h3> 
					Suburb:
				</h3>
				<p>
					{{  building[0].acf.suburb  }}
				</p>
			</article>
			<article class="architect">
				<h3> 
					Architect:
				</h3>
				<p>
					{{  building[0].acf.architect[0].name  }}
				</p>
			</article>
		</section>

		<section>
			<figure><img class="quoteImage" src="@/Images/Quote.png" alt="Banner" /></figure> 
		</section>

		<section class="related">
			<article>
				<h2>Related Events</h2>
				<RelatedEvents />
			</article>
			<article>
				<h2>Related Buildings</h2>
				<RelatedBuildings />
			</article>
		</section>

		<section class="diveIn">
			<h2>Want to Dive In?</h2>
			<p>Get involved with this historic landmark and others like it</p>

			<div class="form">
				<aside>
					<img class="" src="@/Images/CM Diving Board.png" alt="Banner" />
				</aside>
			<article class="">
            <form>
                <label for="fname"><p class="about_p">First name:</p></label>
                <input type="text" id="fname" name="fname"><br>
                <label for="lname"><p class="about_p">Last name:</p></label>
                <input type="text" id="lname" name="lname"><br><br>
                <label for="email"><p class="about_p">Email:</p></label>
                <input type="text" id="email" name="email"><br>
                <label for="phone"><p class="about_p">Phone:</p></label>
                <input type="text" id="phone" name="phone"><br>
                <label for="address"><p class="about_p">Address:</p></label>
                <input type="text" id="address" name="address"><br>
                <label for="mailList"><p class="about_p">Would you like to be on our contact list?</p></label>
                <input type="checkbox" id="mailList" name="mailList" value="Would you like to be on our contact list?">
                <label for="mailList">Yes</label><br>
                <label for="message"><p class="about_p">Message:</p></label>
                <input type="text" id="message" name="message"><br>
                <input type="submit" value="Dive In">
              </form>
          </article>
			</div>
		</section>
			
			<section>
				<Social />
			</section>
	</div>
</template>

<script>
// in this API call, we go get a specifci building, filtered by the ID in the URL
// we access what is in the URL by using the params object
export default {
	async asyncData({ params }) {
		const building = await fetch(
			// `http://cm.beneb.com/wp-json/wp/v2/buildings/142`
			//`https://cm.beneb.com/wp-json/wp/v2/buildings/?slug=high-court-of-australia`
			`http://cm.beneb.com/wp-json/wp/v2/buildings/?slug=${params.slug}`
		).then((res) => {
			if (res.ok) {
				return res.json()
			}
			throw new Error(res.status)
		})
		return { building }
	},
}
</script>

<style>
	.buildingInfoContainer {
		display: flex;
		align-items: center;
		flex-direction: column;
		text-align:center;
		align-items: center;
		padding-bottom:2%;
	}
	.address {
		background-color: #999594;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%;
	}
	.suburb {
		background-color: #7087c2;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%;
	}
	.architect {
		background-color: #f27075;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%;
	}
	.diveIn {
		padding-bottom:2%;
		width:100%;
	}
	.formContainer {
		display:grid;
		grid-template-columns: 1fr 2fr;
	}
	.related {
		display:flex;
		flex-direction:column;
		padding-bottom:2%
	}
	.quoteImage {
		width:100%;
	}
	header {
		text-align:center;
		padding-bottom: 2%;
	}
	.formContainer {
		padding-top:5%;
  		display: flex;
  		align-items: center;
  		flex-direction: column;
  		text-align:left;
	}
	.form {
		display:flex;
		flex-direction: column;
	}

	@media only screen and (min-width: 800px) {
		.form {
		display:grid;
		grid-template-columns: 1fr 1fr;
	}
	.related {
		display:grid;
		grid-template-columns: 1fr 1fr;
		padding-bottom:2%
	}
	.buildingInfoContainer {
		flex-direction:row;
	}

  }

</style>
