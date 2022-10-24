<template>
	<div class="container">
		<SiteNavigation />

		<header>
			<h1>{{ event[0].title.rendered  }}</h1>
		</header>
		<section class="eventInfoContainer">
			<article class="date">
				<h3>
					Date:
				</h3>
				<p>
					{{  event[0].acf.date  }}
				</p>
			</article>
			<article class="time">
				<h3> 
					Time:
				</h3>
				<p>
					{{  event[0].acf.time  }}
				</p>
			</article>
			<article class="year">
				<h3> 
					Year:
				</h3>
				<p>
					{{  event[0].acf.year  }}
				</p>
			</article>
		</section>
		<section>
			<article>
				<span class="descripton" v-html="event[0].content.rendered"></span>
			</article>
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
			<article class="formContainer">
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
			
			<section>
				<Social />
			</section>
		</section>
	</div>
</template>

<script>
// in this API call, we go get a specifci building, filtered by the ID in the URL
// we access what is in the URL by using the params object
export default {
	async asyncData({ params }) {
		const event = await fetch(
			// `http://cm.beneb.com/wp-json/wp/v2/buildings/143`
			// `https://cm.beneb.com/wp-json/wp/v2/buildings/?slug=high-court-of-australia`
			`http://cm.beneb.com/wp-json/wp/v2/events/?slug=${params.slug}`
		).then((res) => {
			if (res.ok) {
				return res.json()
			}
			throw new Error(res.status)
		})
		return { event }
	},
}
</script>

<style>
	.eventInfoContainer {
		display: flex;
		align-items: center;
		flex-direction: column;
		text-align:center;
		align-items: center;
		padding-bottom:2%;
		/* flex-grow:1;
		width:100%; */
		/* justify-content: space-between; */
	}
	.date {
		background-color: #eda384;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%
	}
	.time {
		background-color: #7087c2;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%
		
	}
	.year {
		background-color: #f27075;
		color:white;
		text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
		flex-grow:1;
		width:100%
	}

	.descripton :v-deep(p){
		font-size:100px;
	}

	.description ::v-deep(p){ font-size:3fr}

	.image {

	}

	@media only screen and (min-width: 800px) {
		.eventInfoContainer {
			flex-direction:row;
		}

  }
</style>