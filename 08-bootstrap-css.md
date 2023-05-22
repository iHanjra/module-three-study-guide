# Bootstrap in React

| Term | Definition |
| ---- | ---------- |
| __CSS Framework__ | A pre-written code library or framework that provides solutions to common CSS problems and helps maintain consistency, responsiveness, and modern styling in web projects. |
| __Bootstrap__ | A popular open-source CSS framework initially developed at Twitter, providing a wide range of pre-designed CSS styles, components, and utilities for building responsive web applications. |
| __CDN (Content Delivery Network)__ | A network of servers distributed geographically that delivers web content, including CSS files, to users more efficiently by serving them from the server closest to the user. |

---

## Adding Bootstrap CSS link in `public/index.html`

- Why do we add this link to the `public/index.html` file instead of the `index.js` or `App.js` files? Because it's the root.

```html
<head>
  ...
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
    integrity="..."
    crossorigin="anonymous"
  />
</head>
```

## Example usage of Bootstrap CSS classes in a React component

- What is a `container` as it relates to page layouts? Provides a grid format and responsive and fixed width and centers.
- What does the `btn-primary` class do? Adds a color theme.

```js
import React from 'react';

const MyComponent = () => {
  return (
    <div className="container">
      <h1 className="display-4">Hello, Bootstrap!</h1>
      <button className="btn btn-primary">Click Me</button>
    </div>
  );
};

export default MyComponent;

```

## Bootstrap Grid

- What display property is the Bootstrap grid built on? Display: flex
- What's the relationship between the `container`, `row`, and `col-md-4`? The container holds the entire grid layout, the row creates a new row within the container, and the col-md-4 defines individual columns within the row. 
- How would we break down the `col-md-4` class? This column will be 4 columns wide from medium size screens up
- How many columns is the Bootstrap grid based on? 12
- How would we nest grids in Bootstrap? Create another set of row and col elements within an existing column. This allows you to create more complex grid structures by dividing columns into smaller sections.

```js
import React from 'react';

const BootstrapGridExample = () => {
  return (
    <div className="container">
      <h1>Bootstrap CSS Grid Example</h1>
      <div className="row">
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 1</h5>
              <p className="card-text">Some text for Card 1.</p>
            </div>
          </div>
        </div>
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 2</h5>
              <p className="card-text">Some text for Card 2.</p>
            </div>
          </div>
        </div>
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 3</h5>
              <p className="card-text">Some text for Card 3.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default BootstrapGridExample;
```
