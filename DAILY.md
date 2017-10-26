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

Anyway, some thought needed over time vs. memory.

What I would love is for the map to render super-quick, with Node being used to query the database.

Today was just going over the last aspects of the link and a start to Part II

https://blog.patricktriest.com/game-of-thrones-leaflet-webpack/



