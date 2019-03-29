---
layout: post
title:  "react-redux-material-meteor-en"
subtitle:   "react-redux-material front-end x meteor back-end"
categories: doc
tags: dev boilerplate react meteor
---

react-redux-material front-end x meteor back-end

# Overview 

This project is two applications. One is a client app, including React, and the other is a backend app based on Meteor.

By separating the apps, you can work with one Meteor backend and a variety of other client apps(ReactNative, Angular, React... etc)

The communication between the backend and the client app is done with DDP (Distributed Data Protocol). The backend and client only talk to each other in the same language without knowing each other at all.



# Stack

create-react-app

react-redux

react-router

asteroid

react-s-alert

material-ui

meteor


# Functions

Routing and Login functions have been implemented.

# How does it work?
Clone the project and open the Meteor backend as shown below.

>$ cd {project_name}/rm-back
>
>$ npm install
>
>$ meteor -p 9000

Open the backend on port 9000, expand one terminal and open the client.

>$ cd {project_name}/rm-front
>
>$ npm install
>
>$ npm start

After that, you can test it by connecting to **localhost:3000** in your browser. The app is communication with the Meteor backend

The DDP connection is configured in the asteroid.js file. You can subscribe to backend data and set up listeners.

# Pros

This project is all-in-one architecture using Webpack, React and so on. It also has a Meteor real-time backend in a quick and simple configuration.

Many front-end apps and one Meteor backend app will be connected. We will be able to make something like our own Baas.
