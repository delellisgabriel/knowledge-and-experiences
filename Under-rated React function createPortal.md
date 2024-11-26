# Under-rated React function createPortal

## What does it do? 💫

In React, `createPortal` is a function that allows you to render a component's children into a different part of the DOM tree, outside of its parent component's hierarchy. When is this useful? you might or might not ask, when you want to render elements, such as modals, tooltips, or dropdowns, that should visually or logically break out of the current DOM structure.

Here's an example from the React [documentation](https://react.dev/reference/react-dom/createPortal):

```
import { createPortal } from 'react-dom';

// ...

<div>

<p>This child is placed in the parent div.</p>

{createPortal(

<p>This child is placed in the document body.</p>,

document.body

)}

</div>
```

## Real use case example 😎

At my last job we had implemented a blog navigation bar. It's positioned in two ways depending on the device's screen size; if it's a mid sized and up device the navigation bar would be positioned fixed to the left of the blog post and would follow the user's scrolling. On mobile devices this navigation bar had to be on top of the blogpost under the main navigation bar of the website.

This navigation bar is fixed to the top of the website and has a promotion banner above the navigation that hides and shows depending on whether the user is scrolling up☝️ or down 👇

<!-- TODO continue! -->
