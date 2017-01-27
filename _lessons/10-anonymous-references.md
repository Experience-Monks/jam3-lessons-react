---
layout: lesson
title: Avoid anonymous references
slug: avoid-anonymous-references
references:
  - title: 'Improve control and performance for render functions in React'
    url: 'https://jeremenichelli.github.io/2016/10/better-control-and-speed-react-render/'
---

Not only returning React elements, other computational operations like loops can happen inside a render function.

This power in combination with some short hand allowed from JavaScript itself can become a double-edge sword.

```jsx
class Movies extends React.Component {
  render() {
    const movies = this.props.movies;

    return (
      <div className="movies">
        { (movies || []).map(mov => <MovieBox data={ mov }/>) }
      </div>
    );
  }
}
```

Remember this render function might get called several times. On every call we are defaulting to an empty array in case no movie prop was passed. Doing `[]` equals to new Array, as `{}` is the same as `Object.create(null)`.

Not only these are expensive operations, but they also generate anonymous references on memory making our application slower on each update. Quick solution, create a constant reference with a default value.

```jsx
const noMovies = [];

class Movies extends React.Component {
  render() {
    const movies = this.props.movies;

    return (
      <div className="movies">
        { (movies || noMovies).map(m => <MovieBox data={ m }/>) }
      </div>
    );
  }
}
```

The same occurs with the arrow function inside map. Though it looks great, it is better to move it outside to avoid new memory allocations on each render.

```jsx
const noMovies = [];

function renderMovie(movie) {
  return <MovieBox data={ movie }/>;
}

class Movies extends React.Component {
  render() {
    const movies = this.props.movies;

    return (
      <div className="movies">
        { (movies || noMovies).map(renderMovie) }
      </div>
    );
  }
}
```

For the same reason, you should avoid using `bind` inside render.
