## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

DESCRIPTION: 

This is a sample movie site that makes use of the movie API at http://www.omdbapi.com/. It is accessed through an API key and will retrieve data based on user input. The user will put in a search for a movie or franchise and matching results will be output in the body below. The user can then click on any of these results to view more info about the movie on a separate page. 

Vue-Router:
There is only two routes that are used for this sample site that being Home (or "/") and movie details "/movie/:id". The movie details route will create a path based on the id for the movie that the user selected. It will then use the id from the route in order to determine what to output on the page. For example, if a movie has an id of 435234 that will be shown on the route "/movies/435234". The JS function will then fetch all associated information associated with that id (movie Title, Year, Poster, and Plot) and put it into and object to be printed onto the page. 


