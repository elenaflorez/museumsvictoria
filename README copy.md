# Design

The aim of the design was to create a more engaging and interesting website, to invite participation and have multiple points of engagement and interest for users. The website needs to be inviting and fun to create interest to attend events. 

<img src="Images/Initial Design.jpg"
     alt="Initial Design"
     style="display:block; margin-right: 10px; width:60%" />
The initial design was focused on having more images and showcased events, as further described below. 

## Brighter Design

The brief described that the design needed to draw on images and colours, as the period was a time of experimentation and pushing the boundaries. They also noted that they try to be accessible, digestible, and fun. The current website is not like this, largely bland and empty. 

I attempted to take the website in the opposite direction, taking the brand colours, fonts, and images, and creating a colorful and engaging website. I acknowledge its gaudy at times, and I probably would pare it back a bit in the final version, but it clearly makes a different personality statement for the brand. 

## Call to action

The brief noted that the motto is ‘Conservation through participation’, but the current website doesn’t have any attempt to incite interest or action. The copy was also a bit bland, very matter of fact and non conversational.I made the copy more inviting and inciting action, as shown in the showcased events on the main page, the ‘Dive in’ on each page. I also saw that the socials needed to be on each page and have a better call to action, rather than just the icons. 

## Connecting the website and showing buildings

Another criticism of the current website is that it is highly segregated and separate, buildings aren’t linked together by period or style, architects aren’t linked to their other buildings’ and events aren’t connected to similar events or buildings/architects. To fix this I had relevant events and buildings and events on each page, and added much more information to the main page so people could find what caught their interest and be taken through to other relevant events. 


# Development Process

## Initial steps
The development process for this website was challenging, figuring out how to use Vue’s components and links was a high initial learning curve. I found Ben’s repo instructive, and that gave me the basis to work with the basic components to build the website. 

## Finding feet and challenges
Once I had the basics, I was able to make my own components and embed them in the pages. I created and updated the EventsList and the event pages, as well as the BuildingList and building pages. I also created some smaller components in RelevantEvents, RelevantBuildings, and the socials. With these I was able to create some functioning pages that fit with my desired design. 

The major challenge was how to parse and interact with HTML returns from the API, as the other items were singular like ‘year’ the HTML was a set of different items that couldn’t be extracted individually. This limited my capability to style the event page for example, and to grab information from the other api’s like the about and partnerships page.

The other challenge was filtering page returns for lists like buildings and events, like filtering for buildings from the same architect, or similar events based on location. 

Finally I styled the site to respond to different screen sizes. I found that tablet and desktop could use the same structure given the text and image sizing was done by percentage and view width. But for mobile and smaller tablets I needed to change the website structure and grids to suit.  

## Future improvements

Given the above challenges, there are a few improvements I didn’t get to make that I would have. 

First is an ‘About’ page that consolidated the about, partnerships, and history sections of the API. I noticed that the current website has too many pages to navigate through, and it would have been better served by a single consolidated about page with all that extra contextual information about the organisation. Given the challenges with parsing HTML returns I wasn’t able to implement this page. 

Second is making the relevant events and buildings targeted to the current page, at the moment it doesn’t filter for similar events or relevant buildings, due to the filtering issue described above. 

Finally would be the having the showcase events change based on the month, as at the moment they are pointing to a particular page rather than an API return. 
