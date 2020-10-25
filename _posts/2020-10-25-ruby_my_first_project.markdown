---
layout: post
title:      "Ruby: My first project..."
date:       2020-10-25 23:30:30 +0000
permalink:  ruby_my_first_project
---


I chose to use Github Jobs API for my first project. It was a pretty simple API, with the exception of needing to page through the calls to get all the details. I know the goal of this project was to hit the API and create objects. Then to use those objects to return key details. All the while trying to demonstrate good OO principles. In the future though, I think I would rather gather user input prior to hitting API, allowing my API query to be more percise and I wouldn't have to page through the API as much. As these were a small amount of records, if there were many more records, paging through the API in the begining could be a very heavy call. 

Although I was able to quickly begin with my methods, and determine how I wanted the data to be returned, I soon came to realize I had no exit. I think that was the most difficult part of the program. In todays applications, you can simply exit at any point. I wanted to provide the similar experience. Allowing the user to chose at anypoint to close the program would provide the easiest use for the user, and not force them to complete certain routes to end. 

The other part I found I wanted to acount for was errors. If the user enters a certain number of errors they should be prompted with option to exit the program. To accomplish this I added an error counter. Once they hit 3 errors they are asked if they wish to continue. If not or a cat has been running across the keyboard, they simply hit any other key besides "y".

The final part of the project that I had a little fun researching was `STDIN.getch`. This helped me again create a comfortable user experience, allowing them to hit a single keystroke to progress forward, without the need to type something out and hit enter. I didn't want to use this in every user input situation, but anywhere it made sense I was able to utilize it. 

All in all, I have to say I enjoyed the project. I sure there is a lot of code refactoring that can be done, and maybe different things I wasn't aware of, but it allowed me to use what I had learned, as well as challeged me to explore more. 

The video of my walkthrough is available at: [Youtube: Github Jobs Walkthrough](https://youtu.be/d4iw3l3rBE8)
