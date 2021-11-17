# The page building phase

A page is built from the response received from the server (usually HTML, CSS and JS code). It is done in 2 distinct steps:

1. Parsing the HTML and building the DOM
2. Executing JS code

- Browsers parse and build the HTML, one element at a time until a `<script>` tag is reached.
- HTML code is a blueprint the browser follows when building the initial DOM. The browser can fix problems that it finds in this blueprint.

- JS code found in `<script>` tags is executed by the browsers JS engine: V8 for Chrome, Spidermonkey for Firefox, etc.
- ECMAScript is an interface and browsers must implement features for their engines. JS is such an implementation of ECMAScript.
- The primary global object the browser exposes to the JS engine is the `window` object.