

Date: 2025-11-15
Tags: {
#F 
[[%TS]],
[[%Computer Science]],
}

# As const ! Most underrated TS Feature


```ts
const routes = {
	home: "/",
	admin: "/admin",
	users: "/users"
};

//If we look at the types, we get:

routes.home // = String

//If we would want a function which takes one of
//routes as parameter we would have to write:

const goToRoute = (route: "/" | "/admin" | "users") => {};
```

This is repeated code, and we NEVER want repeated code. So what can we do? And if we would try something like this:


```ts
goToRoute(routes.admin);
```

We would get this Error: 

>Argument of type 'string' is not assignable to parameter of type '"/" | "/admin" | "users"'.ts(2345)
>(property) admin: string

And why is that? Its because we are able to change routes.admin so it doesn't apply to all of the cases anymore. It could be change so TS preserves is like a string.

What we can do is this: 

```ts
const routes = {
	home: "/",
	admin: "/admin",
	users: "/users"
} as const;
```

And if we hover over routes it goes from this:

```ts
const routes: {  
	home: string;  
	admin: string;  
	users: string;  
};
```

To this:

```ts
const routes: {  
	readonly home: "/";  
	readonly admin: "/admin";  
	readonly users: "/users";  
}
```

Now routes.admin will work, because it gets refers as "admin"

```ts
goToRoute(routes.admin);

(property) admin: "/admin"
```

**As const makes Objects *Read Only*.**

We could also use Object.freeze, but this only works on the top level. If we have a second layer we could modify it, but not the top layer.

```ts
const routes = Object.freeze({
	home: "/",
	admin: "/admin",
	users: "/users",
	deep: {
		whatever: "/whatever"
	}
});

//What we could do is this:

routes.deep.whatever = "/idk";

//This would resolve in an Error:

routes.home = "/home";
```

Our goToRoute is still bad, so lets modify it now:

```ts
// Currently it is:

goToRoute = (route: "/" | "/admin" | "users") => {};

//So we create a type for it:

type TypeOfRoutes = typeof routes; 

//Now we got acces to home, admin, and users. But 
//how do acctually extrect the values? 
//We are going to index into the Object.

type Route = (typeof routes)[keyof typeof routes];

//This route gives us these values:

type Route = "/" | "/home" | "/users"

//So we can upgrade our goToRoute function

goToRoute = (route: Routes) => {};

//Now all Values are getting "copied", and if we 
//add new Values to our routes Object, 
//we can directly use them in the function.
```

Okay but how does that work? We are indexing into the object

```ts
//Lets break it down

type RouteKeys = keyof typeof routes

//That gives us all properties
// type RouteKeys = "users" | "home" | "admin"

//If we for example just do this:

type Route = (typeof routes) // =>  "/" | "/home" | "/users"

//And if we do this:

type Route = (typeof routes)["home"] // => "/home"

//We can also pass unions, like:

type Route = (typeof routes)["home" | "/admin"] 
// => "/home" | "/admin"

//Or we can just pass all:

type Route = (typeof routes)[RouteKeys]

```
