# DOM Manipulation With JS

* Select elements from the DOM
```javascript
const element = document.getElementById("id");
```
```javascript
const element = document.querySelector("css-selector");
```
```javascript
const element = document.querySelectorAll("css-selector-1, css-selector-2");
```
```javascript
const element = document.getElementsByClassName("class-name");
```

* Creating an element and then appending it to a container
```javascript
const newElement = document.createElement("div"); // Or some other type such as <a> or <span>
newElement.innerText = "Hello World";

/*
Note - You could also use newElement.textContent, the result will be the same, the difference is highlighted in a following section.
*/

const container = document.getElementById("container-id");
if(container) container.append(newElement);

/*
Note - You could also use container.appendChild, the result will be the same, the difference is highlighted in a following section.
*/
```

* Difference between innerText and textContent
Consider the following code:
```html
<div id="container">
  <span>Hello</span>
  <span style="display: none;">World</span>
</div>
```
```javascript
const container = document.getElementById("container");
if(container){
  const text1 = container.innerText;
  const text2 = container.textContent;
  console.log(text1);
  /*
   Output:
   Hello
   Note - World is not shown
  */
  console.log(text2);
  /*
  Output:
    Hello
    World
  Note - Indentations, spaces and all will also be printed
  */
}
```

* Difference between append and appendChild
```javascript
container.append("Hello World", "John Doe"); // Possible with both strings and nodes
container.appendChild("Hello World", "John Doe") // Error - Multiple arguments are not supported and only nodes can be passed
```

* Inserting HTML via JS
```javascript
container.innerHTML = "<strong>Hello World</strong>" // Will render the text as bold

/*
Note - Using container.innerText here will treat strong tag as part of the string and will not render it as HTML.
Using innerHTML is the only way to insert HTML into a container via JS. Also, if you show a user generated input using this, it could be a risk as malicious code could be entered.

If you have to display text from user input, it is better to create an element, such as a strong tag, assign its innerText and then append that element to a container.
*/
```

* Removing elements
```javascript
const elementToRemove = document.getElementById("to-remove");
const container = document.getElementById("container");

elementToRemove.remove(); // Will delete from the DOM
container.append(elementToRemove); // Will add it again

container.removeChild(elementToRemove); // Will also remove from DOM, same thing
```

* Modifying attributes
```html
<span title="hello world" id="span-1">I am a span</span>
```
```javascript
const element = document.getElementById("span-1");

console.log(element.getAttribute("title")); // hello world
element.setAttribute("title", "good job"); // Will set to good job
console.log(element.title); // good job, does the same thing
element.title = "hello world"; // Will set title back to hello world
element.removeAttribute("title"); // Will remove title attribute from element
```
