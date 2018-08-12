+++
chapter = "Routing"
title = "ANGULAR 2"
subtitle = "A PRACTICAL INTRODUCTION TO THE NEW WEB DEVELOPMENT PLATFORM"
author = "Sebastian Eschweiler"
chapter_number = 7
leanpub = "https://leanpub.com/angular2-book"
+++

#### Adding the Base Element
> The first thing which needs to be done is to add the <base> element to the application’s HTML code. We do that by adding the following element right after the <head> tag in index.html.  
>  
> `<base href="/">`  
>  
> The value which is assigned to the href is the base URL which is used to prefix relative URLs. By default the Angular 2 Component Router uses HTML 5 style for routing URL. That means that router URL can not be distinguished from server URL. By setting the base URL it becomes clear which part of the URL belongs to the server and which part belongs to the client router. If server assets (e.g. images) are requested by using a relative URL, the base URL is used to prefix the relative URL and makes sure that no client router specific URL parts are used to retrieve the static server resource.  
  
#### Routing Configuration  
> In addition the _pathMatch_ property is set to the string value _full_. This means that an exact patch match is needed to activate the redirect. To have an exact match the URL must not contain additional segments after the path specified. The other possible _pathMatch_ value is _prefix_. In this case a match is recognized when the URL begins with the redirect route’s prefix path.
In our case, of course, only a full match makes sense because otherwise every URL would match the empty path and all other routes (e.g. car/create) would never be accessible.
  
#### Routing URL Styles
##### HTML 5 Style and Hash Location Style  
Each time we navigate to an application route the browser’s location and history is update with the corresponding URL. In contrast to a server URL this URL is just part of the single page application and not sent to the server. In browsers supporting HTML 5 the Router is able to use history.pushState() to set history entries programmatically. In this case URLs of local application routes can look like normal server routes (HTML 5 Style). If history.pushState() is not supported in the browser the local part of the URLs must be separated from the server part of the URL. A common way the separation is done is using a hash (#) in the URL. The URL part which is behind the hash is the local part and is used for client side routing and not sent to the server. In Angular this URL style is called Hash Location Style.

##### Location Strategies  
In Angular 2 both forms of URL styling are supported. The HTML 5 Style is called _Path Location Strategy_ and activated by default. In the sample application of this chapter we made use of the _Path Location Strategy_ without the need of defining this explicitly. If you want to switch to the _Hash Location Strategy_ you need to override this setting by providing the _useHash:true_ in an object as the second argument of _RouterModule.forRoot()_ method:
```typescript
export const routing: ModuleWithProviders = RouterModule.forRoot(appRoutes, { useHash:true });
```