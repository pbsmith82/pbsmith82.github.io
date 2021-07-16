---
layout: post
title:      "Let's Talk Redux"
date:       2021-07-16 16:22:48 +0000
permalink:  lets_talk_redux
---


Redux is often used with React and is a predictable state container that was released in 2015 and was created by Dan Abramov and Andrew Clark. It is meant to help JavaScript apps behave consistently across client, server, and native environments. It is also easy to test. 

While it’s mostly used as a state management tool with React, you can use it with any other JavaScript framework or library. Redux allows the state of your application to be kept in a store. Than each component can access any state that it needs.

Anyone who researches Redux can see there are a series of benefits and limitations. Some people would redux has been a hot topic for discussion. Below is a list of some it's benefits and Limitations. 

* **State transfer:** State is stored in the ‘store.’ It can be difficult to identify the source of the state variables as your application grows.  The store allows you to call state data from any component.

* **Predictability:** Redux is a predictable state container, Since reducers are pure functions, you can always expect the same results. 

* **Maintainability:** Since Redux has a strict structure for how the state should be managed, it makes the code easy to replicate and scale.

* **Ease of testing and debugging:** With the help of Redux tools like Redux DevTools it easy to test and debug your code.

While I would suggest every developer to consider Redux, it may not be necessary. When you are working with a smaller application, setting up Redux can be a difficult and seemingly unnecessary overhead unless you’re scaling a large application.


# Action Creators, Reducers, and Stores. 

**Action:** When you update your state with Redux, you always start with an action. Actions are Javascript objects that contain a type and an optional payload.

**Action creators:** They are functions that return action objects, which is sent to various reducers.

**Reducer:** Reducers are pure functions that enter changes to state and returns a new state. It can take in the previous state and action as parameters and then return the new state.

**Redux store:** The store is where state objects are stored. When store is updated, it updates the components that are subscribed to it. It is responsible for storing, reading, and updating state.


If you choose to use Redux, you will it makes the ability to access and update state from any component much easier, and much more dependable. I personally found it very useful, and often found myself having to remember what it is like to use React without Redux. 
