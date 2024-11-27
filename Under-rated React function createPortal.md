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

### The solution 🟰

As you might have guessed already I refactored the code to use the createPortal function, removed all listeners and created two blog index bar, one for mobile and one for desktop and with createPortal I would search for the header and attach the blog index bar it, thus having no need to make any expensive calculations. The equivalent of doing this in plain JavaScript would be:

- Get the header from the DOM using the `getElementById` method.
- Append the blog index bar component as a child with `.appendChild`.

### Why use createPortal over appendChild? 🤔

The advantage of using the portals is that React will move the component in the real DOM to the header but in it's virtual DOM said component will be treated still as a child of it's original parent component. This behavior ensures that you can use portals without losing the benefits of React's tree management, even if the DOM structure changes for styling or practical reasons.

<!-- TODO continue! -->
