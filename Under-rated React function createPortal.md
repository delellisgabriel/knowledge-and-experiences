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

At my last job, we implemented a blog index bar with responsive positioning based on screen size:

- On medium-sized screens and larger, the blog index bar was fixed to the left of the blog post and followed the user's scrolling.
- On mobile devices, the blog index bar was positioned just below the website's main navigation bar.

The main navigation bar was fixed to the top of the page and included a promotional banner above it. This banner would appear or hide depending on whether the user was scrolling up or down.

With the first implementation of this blog index bar we would get the total height of the navbar + the current banner height which meant we had to listen to events make the calculation and the blog index bar would kind of move with it but it was buggy and we were not happy with it.

## The solution

As you might have guessed already I refactored the code to use the createPortal function, removed all listeners and created two blog index bar, one for mobile and one for desktop and with createPortal I would attach it to the header thus having no need to make any expensive calculations, also this is the equivalent of using document.getElementById get the header and then append the component as a child with .appendChild method.

The advantage of using the createPortal function is that React will move the component in the DOM to the header but in it's virtual DOM it will remain as a child of the component.

<!-- TODO continue! -->
