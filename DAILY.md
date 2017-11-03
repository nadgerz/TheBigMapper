October 25th 2017
=================

ok, we're off!

I will list the resources I found useful when working with these
technology stacks and tools. (see README.md)


The aim of the project is to allow a user to view, add, edit and delete objects on a map.

Long term aim is for this to be usable from a smartphone too, hence React-Native.

At the start though, I will assume a desktop browser experience, just to learn best practices for React.

After a bit of noodling around, I have decided to use TypeScript with React, so I get all that type-safety goodness in JavaScript.

I also want the ability for an Admin login to enable various 'groups' of users, with a variety of access privileges.

For instance, maybe 'the public' defaults to 'read-only' but other groups are only allowed to edit certain attributes on objects and other groups are allowed to add/delete objects.

As the application should run in a web-browser, on an iPhone
and on Android phones, we'll start by trying to code all
the front-end using React and React Native, to try and share
as much code as possible across the three platforms.

Well, that's the plan!


**JavaScript**

BOOKS:

A great series of 'books' by Kyle Simpson (@YDKJS)

You Don't Know JS: https://github.com/getify/You-Dont-Know-JS

While you can get these for free, via github... please consider
buying them if they start to prove useful. They are not lengthy, but
they are comprehensive at the same time... at least in the areas
of JavaScript that matter.

Kyle also has some great classes on Pluralsight too:

http://www.pluralsight.com

This is more of an investment, for sure... but it is a superb collection
of teaching material coverings a LOT of subjects; not just JavaScript.

This site alone will carry you through your programming (and design)
career!


START
=====

ok, on my first day, I am going to work through the first of two tutorials that touches on some technology I want to use.

https://blog.patricktriest.com/game-of-thrones-map-node-postgres-redis/

It happens to use PostgreSQL/PostGIS, but I am more interesting in the Node/Express/GeoJSON aspects.


ok, I have postgres/postgis installed anyway, but there are a number of built binaries out there.

I don't think this tutorial needs anything super up-to-date, but v9 postgres and v2 postgis should be fine.



October 26th 2017
=================

Well, the link above was an eye-opener, with regards to Redis.

I will need to think about the design of data as it comes into a map, because the caching capabilities of Redis should really speed up requests for data on a pan/zoom.

The idea is that data will not actually change that much, and if it does, we can just flush the cache peridically.

Given we are bring back data geo-spatially, that is quite expensive, so we could bring it back and cache it, especially at a zoomed in level.

Anyway, some thought needed over time to load vs. memory, etc.

What I would love is for the map to render super-quick, with Node being used to query the database.

Today was just going over the last aspects of the link and a start to Part II

https://blog.patricktriest.com/game-of-thrones-leaflet-webpack/

As I am concerned about data volumes... I have downloaded the OSM (OpenStreetMap) data for Berlin, Germany
and have converted it to GEOjson using a tool called osmtogeojson.

This is on NPM

npm --install --global osmtogeojson

Then:

time /home/si/.nvm/versions/node/v8.8.1/bin/node --max_old_space_size=8192 `which osmtogeojson` berlin-latest.osm > berlin-latest.geojson

My aim is that if I can load THIS data on the fly, with caching, loading poles and cables and post boxes 
and whatever will be piss-easy

I suspect this set of data will be insane... but the aim of this map product is 'local', so Berlin sized level is more than enough.

Also 'too much' data will give me an opportunity to learn what I need.  

At this point (map pun!) I do not know enough about MongoDB and GeoJSON to have a sane view




Sunday: October 29th 2017
=========================

I bought this course on Udemy, for $25:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

after I had listened to this link: https://www.youtube.com/watch?v=AcPJtA41-5Q

The Youtube link was about loading GeoJSON data and that seemed to dovetail
nicely with the fact that I had converted the Berlin OSM data about into GeoJSON format.

The Udemy course is by the same guy and the Youtube videos were a precursor to him developing 
the Udemy course.

He has another course on Udemy that is the pre-req for the one I bought, but
I think that is likely only needed for someone with little to no programming experience.


Monday: October 30th 2017
=========================

I am now just working through the Udemy course:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

I figured this was not a bad direction as the application is map-related :)

It happens to also be covering things like jQuery, CSS and JavaScript anyway, so
there is practice there.

And I get to see how WebStorm (the editor I am using for all this) performs.

# chrome dev tools

I am displaying the map/app in Google Chrome, so I get to deal with Chrome Dev Tools,
which I suspect knowing well will be a huge productivity boost.

I have a subscription the Pluralsigth and John Sonmez (http://www.simpleprogrammer.com)
has a course on 'Using The Chrome Developer Tools'

https://app.pluralsight.com/library/courses/chrome-developer-tools/table-of-contents

It's a few years old now, so probably something on Youtube with Paul Irish, might be a better bet,
give Chrome Dev Tools are 'evergreen'.


# webpack

I also hope to set things up to be using webpack, babel, browserify and friends, so that
I can start using ES6 modules.  No browser supports them natively yet (as opposed to CommonJS), but
as ES6 (and ES7/8) is the way we are going... why not bite the bullet now?


# es6 and beyond

I have started reading:

https://leanpub.com/exploring-es6

by Axel Rauschmayer, to get a side-by-side comparison of ES5 to ES6

It is free online, at: http://exploringjs.com/es6.html

But please buy it :)


Tuesday: October 31st 2017
==========================

Still working through the Udemy course:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

Up to Lecture 17

Not going to go into details as the course will explain itself, if you get it.

Suffice to say though, that Leaflet.js seems very comprehensive and I think will
do all I want.  It probably will not be as comprehensive as a map application as
I have used before, but less complexity might be a bonus.

Certainly the code base should be more maintainable, especially if I use
ES6 modules.

One thing I have noticed, using Chrome Dev Tools is how much network traffic there is
pulling in map tiles.

Redis might be my thing for caching those.

And if many people were, say, using this application (that I have yet to write :) ),
we could even cache on an internal server, as people using the application add to the
'common' cache.

But I get ahead of myself :)

I have noticed that the Udemy course uses Bootstrap and his Version 3 seems to play more nicely 
than the Bootstrap version 4 I installed.

That might be because I know JS about Bootstrap though :)

Going to get through all the Native and Plugin Leaflet controls lectures (Section 2: The Leaflet Map Object) today.


Wed: Nov 1st 2017
=================

Still working through the Udemy course:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

Did not complete all the plugins yesterday, but have added quite a few... many of which
will prove super useful.

Thu: Nov 2nd 2017
=================

Still working through the Udemy course:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

Mainly learned about Basemap and leaflet basemap providers.

And ability to switch layers.

Need to learn about draworder.


Fri: Nov 3rd 2017
=================

Still working through the Udemy course:

https://www.udemy.com/display-and-analyze-gis-data-on-the-web/learn/v4/overview

Learning about Layer and Feature groups, to make different layers and features
act as a single entity.

Also realised we can change the basemap opacity.

This will be useful to display a 'Stamen Watercolor' background and have our own artifacts
show through or even have a simple Topo map blend with it.


