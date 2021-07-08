---
layout: post
title:      "React - Redux"
date:       2021-07-08 21:40:59 +0000
permalink:  react_-_redux
---


This was absolutely the most excelled portion of this whole experience. Learning how utilize state with React and then using the store to help maintain state was pretty interesting.

React is great for creating apps cause it can change data without reloading the page. It also gives us the ability to use HTML syntax to render components. 

Redux allows us to manage state in a single place. This helps make changes and app behavior more predicatable. With redux we are able to utlize tools like ...
```
mapStateToProps
```

MapStateToProps helps make sure any changes in the store are merged into the props in the components. This will help trigger a re-render to update the component. 

I have to say learning all this was quite interesting. I experienced an issue where everything worked just fine when going through the app. But if you type in a URL to access a record directly it fails. I thought this might related to how my routes were setup, but after hours of adjust routes, I realized it wasn't routes. While doing that I noticed the props loaded twice when hitting the page. The first time it didn't have my data yet, but the second one did. 

That realization helped me to see that everything was working, but my component was trying to render before the app had a chance to make the fetch, and update state & props. I didn't have this problem on the main page, cause I had implemented code to handle that. 

It turned out to be a simple fix. I just need to add logic to account for the stage when props was emptyied and once the state and props were updated it would re-render the component. 

This is was kind of tricky cause it all happens so quick. You barely see the "loading" phase before it's updated, but even the millasecond was enough to cause the app to fail. 

All in all I found this exciting and pushing my limits. I love learning, and pushing my knowledge. 

