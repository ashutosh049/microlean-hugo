---
title: A post by Alex Xu on Google Map
bookCollapseSection: false
weight: 2
bookToc: true
bookComments: true
---

# A post by Alex Xu on Google Map

<br>
<br>

Read the full article [here](https://www.linkedin.com/posts/alex-xu-a8131b11_systemdesign-coding-interviewtips-activity-6889974038777724928-G3u2)

Google started project G𝐨𝐨𝐠𝐥𝐞 M𝐚𝐩𝐬 in 2005. As of March 2021, Google Maps had one billion daily active users, 99% coverage of the world.

Although Google Maps is a very complex system, we can break it down into 3 high-level components. In this post, let’s take a look at how to design a simplified Google Maps.


### Location Service
The location service is responsible for recording a user’s location update. The Google Map clients send location updates every few seconds. The user location data is used in many cases:

- detect new and recently closed roads.
- improve the accuracy of the map over time.
- used as an input for live traffic data.

### Map Rendering

The world’s map is projected into a huge 2D map image. It is broken down into small image blocks called “tiles” (see below). The tiles are static. They don’t change very often. An efficient way to serve static tile files is with a CDN backed by cloud storage like S3. The users can load the necessary tiles to compose a map from nearby CDN.

What if a user is zooming and panning the map viewpoint on the client to explore their surroundings?

An efficient way is to pre-calculate the map blocks with different zoom levels and load the images when needed.


### Navigation Service
This component is responsible for finding a reasonably fast route from point A to point B. It calls two services to help with the path calculation:

1. Geocoding Service: resolve the given address to a latitude/longitude pair. 
2. Route Planner Service: this service does three things in sequence:

    - Calculate top-K shortest paths between A and B
    - Calculate the estimation of time for each path based on current traffic and historical data
    - Rank the paths by time predictions and user filtering. For example, the user doesn’t want to avoid tolls.

![Goole Map](https://media-exp1.licdn.com/dms/image/C5622AQEGdukkslxq_A/feedshare-shrink_800/0/1642697819441?e=2147483647&v=beta&t=6VsadWi_6NkAQDEw3aCxDK_xP6R7isdr5uMU6M0vwMc)
[Image source](https://media-exp1.licdn.com/dms/image/C5622AQEGdukkslxq_A/feedshare-shrink_800/0/1642697819441?e=2147483647&v=beta&t=6VsadWi_6NkAQDEw3aCxDK_xP6R7isdr5uMU6M0vwMc)

### More articles and references
- [Prototyping a Smoother Map](https://medium.com/google-design/google-maps-cb0326d165f5)
- [Traffic prediction with advanced Graph Neural Networks](https://deepmind.com/blog/article/traffic-prediction-with-advanced-graph-neural-networks)
- [Route Optimization And Planning With Google Maps](https://blog.routific.com/route-optimization-google-maps-313a45e13d27)


### Questions and follow-ups
- > Hi Alex, Thanks for sharing. Can you go a little deeper into how to find `K-Shortest path`? How would that work? `DFS`? `BFS`? Those solutions may be pretty slow given that it could be exponential to the number of intersections there is in a typical metropolitan area. Precompute routes based on given tiles? That may work for most cases, but if there is a road closure, traffic accident, how would that be handled? 
  - > Great question. Since the graph of the whole world is huge, we can run the shortest path on super segments instead, and then within each super segment, we can find how to navigate to the next super segment. Here is a good read: https://blog.routific.com/route-optimization-google-maps-313a45e13d27
- > How would the Navigation server get live traffic data? Does the User Location DB store that data?
- > Alex Xu how does the map work offline?
  - > My guess is that the nearby roads, building structures, etc are cached when we first install the app or click the navigate button. The mobile device can figure out the routes without talking to the server. It couldn't take traffic conditions into consideration though.

---

Original Article/Credit : [Alex Xu](https://www.linkedin.com/posts/alex-xu-a8131b11_systemdesign-coding-interviewtips-activity-6889974038777724928-G3u2/)

