# The page building phase

A page is built from the response received from the server (usually HTML, CSS and JS code). It is done in 2 distinct steps:

## Steps and notes for page-building

1. Parsing the HTML and building the DOM
2. Executing JS code

- Browsers parse and build the HTML, one element at a time until a `<script>` tag is reached.
- HTML code is a blueprint the browser follows when building the initial DOM. The browser can fix problems that it finds in this blueprint.

- JS code found in `<script>` tags is executed by the browsers JS engine: V8 for Chrome, Spidermonkey for Firefox, etc.
- ECMAScript is an interface and browsers must implement features for their engines. JS is such an implementation of ECMAScript.
- The primary global object the browser exposes to the JS engine is the `window` object.
- The `window` and `document` objects are given to us by Web API's.
- Because the construction of the page is halted when it finds a `<script>` tag, HTML elements that have yet to be defined cannot be selected. This is why most code puts `<script>` tags at the end of their HTML.
- Once there are no more HTML elements to process, we move into the _event handling_ phase.

## The event handling phase

### Overview

> The browser execution environment is, at its core, based on the idea that only a single piece of code can be executed at once: the so-called single-threaded execution model.

- The **event_queue** keeps track of events that have occurred but have yet to be processed.
- All generated events (whether they be user or server generated) are placed on the same queue in the order that they are detected by the browser.

### Steps

1. Browser checks head of the event queue
2. No events, browser keeps checking
3. If there is an event, the browser takes it and executes the associated handler (if it exists). During this execution, the rest of the events wait in the event queue to be processed.

> It’s important to note that the browser mechanism that puts events onto the queue is external to the page-building and event-handling phases. The processing that’s necessary to determine when events have occurred and that pushes them onto the event queue doesn’t participate in the thread that’s handling the events.

### Event are asynchronous

- When events happen, they happen at unpredictable times and unpredictable orderings.
- The handling of events is **asynchronous**.

### Registering events

1. By assigning functions to special properties
2. By using the built-in `addEventListener` method.

> We should use the second (2) method as 1 only allows for us to register a single event handler for each event type.