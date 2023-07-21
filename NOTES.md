# NOTES

React routing, a method of navigating through website pages based on url links.

## First steps: After installation

- We need too import browser router

``` JS
import { BrowserRouter } from "react-router-dom" 
```

- We need to wrap our root component in a browser router component that allows us to use the benefits of it

``` JS
ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>,
)

```

- In our App.jsx we need to import some components from react router

``` JS
import { Link, Route, Routes } from "react-router-dom"
```

- These will help us set up navigation through pages

- Firstly we need to set up a Routes component which will contain all our routes

- And in Routes we use route to create our routes by hardcoding a path and giving the component to render

``` Js
    <Routes>
        <Route path="/" element={<Dashboard />} />
        <Route path="/categories" element={<Categories />} />
        <Route path="/productsPage" element={<ProductsPage />} />
    </Routes>
```

- here we have multiple routes starting with the first which has the path="/" this is our home page. /categories and /productPage are routes the components that match the path. These components will be rendered without re-rendering the page when accessed from the path.

- Now to access these paths we have another route element named link

``` JS
<nav>
    <ul>
        <li>
        <Link to="/">Home</Link>
        </li>
        <li>
        <Link to="/categories">Categories</Link>
        </li>
        <li>
        <Link to="/productsPage/">Products</Link>
        </li>
    </ul>
</nav>
```
- In react router the Link component replaces our good old anchor tag and renders for us the component with the specified path


- Coming back to route we also have 3 other methods

``` JS
<Route path="/productsPage/:id" element={<Product />} />
<Route path="/productsPage/new" element={<NewProduct />} />
<Route path="*" element={<NotFound />} />

```

- Product page :id is a way to dynamically generate paths, inside ProductPage component we have a couple of Link components. Now when we access a link inside the ProductPage component because they have a number after the usual path for product page the route with id will be selected.


- The Product component is going to render but we don t know which product we have selected so to render that we can import a react router hook names useParams to get parameters from the path

```JS

import { useParams } from "react-router-dom"

const Product = () => {
   const {id} = useParams()
  return (
    <div>Product {id}</div>
  )
}
export default Product

```

- Continuing on the subject of paths here we have hardcoded a new path with product page, this is done just to show that react router 6 now knows how interpret paths and to distinguish paths that actually have an id or not and the fact that the route under the one with id is hardcoded 


``` JS
<Route path="/productsPage/:id" element={<Product />} />
<Route path="/productsPage/new" element={<NewProduct />} />
<Route path="*" element={<NotFound />} />

```

- Our last Route component is for rendering errors the path="*" and the star works kind of like regex validation, if any path introduced does not match the ones in the router the one with star will match and send us to the error path

