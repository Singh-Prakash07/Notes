## hierarchy
- Window
  - DOM
  - BOM
  - jS Core
+ the window object is the ultimate parent of both the BOM and the DOM.
+ To put it simply, the document object (which is the entry point to the DOM) is a property of the window object.

## The Global Container: window
+ The window is the most important object in the browser. It represents the browser's open window or tab and is the global object for all JavaScript code in the browser. This means that any variable or function you declare globally is a property of the window object.
+ Think of the window as the entire car. It contains everything: the engine, the frame, the seats, and the dashboard.
+ Key purpose: It provides a context for all the objects and APIs available to your script.
+ Examples: window.innerWidth (the width of the browser viewport) or window.location (the URL of the current page).

## The Browser Object Model (BOM)
+ The BOM (Browser Object Model) is a collection of objects that allow JavaScript to interact with the browser itself. The window object is the central part of the BOM, and all other BOM objects are properties of the window. The BOM is not a standard, so different browsers may have slightly different implementations, though most have converged on the same core objects.

+ The BOM lets you control things outside of the web page content. Using the car analogy, the BOM would be the entire car, including the engine, the navigation system, and the climate controls.
+ Key purpose: To manipulate the browser environment.
+ Examples of BOM objects:
+ location: For getting and setting the current URL.
+ history: For navigating backward and forward through the browser's history.
+ navigator: For getting information about the user's browser (e.g., name, version).
+ screen: For getting information about the user's screen.
+ setTimeout(): A method to execute a function after a delay.
## DOM
+ The DOM (Document Object Model), is an application programming interface (API) for HTML and XML documents. It represents the page as a tree of objects, where each object is a node. This tree structure is how web browsers interpret and display a web page.

+ Tree of Objects: Every element in an HTML document, like <html>, <head>, <body>, and <p>, is represented as an object in this tree.
+ API: JavaScript uses the DOM to access, manipulate, and modify the content, structure, and style of a web page. For example, document.getElementById('my-id') is a way for JavaScript to find a specific element in the DOM tree.
+ Key purpose: To manipulate the content of the web page.
+ Examples of DOM methods:
+ document.getElementById(): Finds an element by its ID.
+ document.createElement(): Creates a new HTML element.
+ element.innerHTML: Gets or sets the HTML content of an element.

## The Hierarchy: A House Analogy
+ Imagine your browser tab is a house.
+ The window object is the house itself. It's the physical structure that contains everything—the walls, the roof, and all the rooms. It's the ultimate container.

+ The BOM (Browser Object Model) is the set of house features. This includes the thermostat (navigator), the address plaque (location), the door to the garden (history), and the clock on the wall (setTimeout). These features help you interact with and manage the house itself, but they are not part of the living room furniture.

The DOM (Document Object Model) is the furniture and contents within a specific room (the web page content). This is represented by the document object. The document object is a property of the window object, just like the furniture is inside the house. The DOM lets you move the couch (getElementById), change the color of a painting (element.style), or add a new chair (createElement).
## The Critical Relationship
+ This is where it all comes together:
+ The window object is the global object and top-level container.
+ The BOM is a collection of objects that are properties of the window object, allowing control over the browser.
+ The document object, which is the entry point to the DOM, is also a property of the window object. This gives JavaScript access to the web page content.
+ This means that window contains everything. The BOM is the window and its related objects. The DOM is represented by the document object, which is itself a part of the window object.

## How is BOM different from window?
+ The BOM is not "different" from the window object. it's a concept or a collection of APIs that are centered on the window object. The window object is the core of the BOM. So, when people talk about the BOM, they are referring to the set of APIs like location, history, and navigator, all of which are properties of the window object.
## Common Dialogs: alert(), prompt(), and confirm()
+ These are all methods of the window object. They are often called without the window prefix because window is the global object, and its properties are available everywhere.

+ alert('Hello!'): Displays a non-interactive dialog box with a message and an "OK" button. It returns undefined.

+ prompt('Enter your name:'): Displays a dialog box with a message, a text input field, and "OK" and "Cancel" buttons. It returns the string entered by the user or null if they click "Cancel".

+ confirm('Are you sure?'): Displays a dialog box with a message and "OK" and "Cancel" buttons. It returns true if the user clicks "OK" and false if they click "Cancel".
+ Key Limitation
+ The major limitation of these methods is that they are blocking. This means that they halt all JavaScript execution and prevent the user from interacting with the web page until they are dismissed. This can be a very poor user experience, which is why they are rarely used in modern web development. Instead, developers build custom, non-blocking modal dialogs using HTML and CSS.

| Concept |	What It Is	| Primary Use	| Contained By |
|---------|-------------|-------------|--------------|
| window |	The global object; represents the browser tab. | The central container for all browser functionality. | The browser environment |
|BOM | A collection of objects for browser interaction. |	Changing the URL, getting browser info, setting timers. |	window |
| DOM	| A tree structure of the web page's HTML. | Manipulating page content, style, and structure.	| document object (which is in window) |
