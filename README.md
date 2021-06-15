# jsonstorage

Store and retrieve your JSON data for free using simple GET and POST requests [https://www.jsonstorage.net/](https://www.jsonstorage.net). Based on .NET Core and Azure Cosmos DB. Source code of the initial version is in the /legacy branch.

## Api

Public API does not require authentication (as long as the item was intially created using unauthenticated request).

*Get JSON*:
GET https://api.jsonstorage.net/v1/json/(id)

*Create JSON* (unauthenticated):
POST https://api.jsonstorage.net/v1/json

*Update JSON* (unauthenticated):
PUT https://api.jsonstorage.net/json/(id)

Entities created from the App always require API key (for editing).

## Sample

It uses jsonstorage as a data provider for storing to-dos

* Source Code [todomvc-jsonstorage](https://github.com/adoprog/todomvc-angular2-jsonstorage)
* Hosted Demo [https://todomvc-jsonstorage.azurewebsites.net/](https://todomvc-jsonstorage.azurewebsites.net/)

## App

The app [https://app.jsonstorage.net](https://app.jsonstorage.net) is a UI for managing JSON snippets. It provides a few extra features in addition to the public API

![App UI](/docs/images/app.png)

### Items

Item is a piece of content you want to serve. Each item created from the app is tied to your user profile and cannot be edited without the API key.

### Api Keys

Api Key allows editing the content from the API. There are two types of API keys: normal and read-only.

*Create JSON* (authenticated)
POST [https://api.jsonstorage.net/v1/json/%item_id%?apiKey=%api_key%](https://api.jsonstorage.net/v1/json/%item_id%?apiKey=%api_key%)

*Update JSON* (authenticated)
PUT [https://api.jsonstorage.net/v1/json/%item_id%?apiKey=%api_key%](https://api.jsonstorage.net/v1/json/%item_id%?apiKey=%api_key%)

### Intents

Intents allow to personalize served content based on one or many of the following:

* Query String
* Request Header
* IP Address
* (more to be added)

You create intents first, and then assign intents and desired outputs to one of the items. The rules are executed top to bottom, the last rule (if applicable) will override the previous one.

![App UI](/docs/images/virtual.png)

![JsonStorage](https://2.bp.blogspot.com/-iMkQcOCzFcs/WJI4rcHrLyI/AAAAAAAAEM4/Hcggu0JjauEY7NUpqioZIofZFyyuX1ffwCLcB/s1600/Plan.png)

### Personalization

You can serve personalized content for website built with React, NextJS, and other frameworks.

### Live Demo

[https://jsonstorage-demo-react.netlify.app/](https://jsonstorage-demo-react.netlify.app/)

Try with query string:

* ?persona=developer
* ?persona=marketer

[Source Code](https://github.com/adoprog/jsonstorage-demo-react)

### How it was built

This project was created by taking sample React website from [here](https://github.com/issaafalkattan/React-Landing-Page-Template), then:

```npm install @jsonstorage/personalize-react```

and updating the code to use personalized title and text:

![usage](/docs/images/usage.PNG)

### Back-end configuration

The data is stored here: [https://app.jsonstorage.net/](https://app.jsonstorage.net/)

![backend](/docs/images//backend.PNG)

## Related blog posts

* [Build your startup on Azure. Part 1: JsonStorage.net](http://devopssnippets.blogspot.com/2017/03/build-your-startup-on-azure-part-1.html)
* [Build your startup on Azure. Part 2: Creating and publishing the project](http://devopssnippets.blogspot.com/2017/04/build-your-startup-on-azure-part-2.html)
