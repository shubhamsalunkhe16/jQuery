## Introduction to jQuery

- jQuery is a `fast, small, and feature-rich JavaScript library`.
- It simplifies tasks like HTML `document traversal` and `manipulation`, `event handling`, and `animation`, making it easier to develop web applications.

## Document Ready

- `Ensures that the DOM is fully loaded` before running scripts.

### Syntax:

```javascript
$(document).ready(function () {
  // Code here runs after the DOM is fully loaded
});
```

### Example:

```javascript
$(document).ready(function () {
  console.log("The DOM is ready!");
});
```

---

## Selectors

- used to `find or select HTML elements` based on their name, id, classes, types, attributes, etc.

```javascript
// Select by ID
$("#id");

// Select by class
$(".class");

// Select all paragraphs
$("p");

// Select elements by attribute
$("[name='value']");
```

---

## DOM Manipulation

- provides methods to `manipulate the DOM` easily.

### Methods:

1. `Getting and Setting Content:`

   ```javascript
   // Get text content
   let text = $("#myDiv").text();

   // Set text content
   $("#myDiv").text("Hello, World!");

   // Get HTML content
   let html = $("#myDiv").html();

   // Set HTML content
   $("#myDiv").html("<b>Hello, World!</b>");
   ```

2. `Adding/Removing Elements:`

   ```javascript
   // Append content
   $("#myDiv").append("<p>Appended Paragraph</p>");

   // Prepend content
   $("#myDiv").prepend("<p>Prepended Paragraph</p>");

   // Remove an element
   $("#myDiv").remove();
   ```

3. `Modifying Attributes:`

   ```javascript
   // Get an attribute
   let href = $("#myLink").attr("href");

   // Set an attribute
   $("#myLink").attr("href", "https://example.com");
   ```

4. `Modifying CSS:`

   ```javascript
   // Get a CSS property
   let color = $("#myDiv").css("color");

   // Set a CSS property
   $("#myDiv").css("color", "blue");
   ```

---

## Event Handling

- simplifies event handling and binding.

### Example:

```javascript
// Click event
$("#myButton").click(function () {
  alert("Button clicked!");
});

// Hover event
$("#myDiv").hover(function () {
  $(this).css("background-color", "yellow");
});

// Delegated event (useful for dynamically added elements)
$(document).on("click", ".dynamicButton", function () {
  alert("Dynamic button clicked!");
});
```

---

## Effects and Animations

Add dynamic effects to web elements.

### Methods:

1. `Show/Hide Elements:`

   ```javascript
   // Hide with animation
   $("#myDiv").hide(1000); // 1000ms duration

   // Show with animation
   $("#myDiv").show(1000);

   // hide/Show with animation
   $("#myDiv").toggle(1000);
   ```

2. `Fading Effects:`

   ```javascript
   // Fade in
   $("#myDiv").fadeIn(1000);

   // Fade out
   $("#myDiv").fadeOut(1000);

   // Fade in/out
   $("#myDiv").fadeToggle(1000);
   ```

3. `Sliding Effects:`

   ```javascript
   // Slide up
   $("#myDiv").slideUp(1000);

   // Slide down
   $("#myDiv").slideDown(1000);

   // Slide up/down
   $("#myDiv").slideToggle(1000);
   ```

4. `Custom Animation:`
   ```javascript
   // Animate CSS properties
   $("#myDiv").animate({ width: "300px", height: "300px" }, 1000);
   ```

---

## AJAX

Perform asynchronous HTTP requests.

### Example:

1. `GET Request:`

   ```javascript
   $.get("data.json", function (data) {
     console.log(data);
   });
   ```

2. `POST Request:`

   ```javascript
   $.post("submit.php", { name: "John" }, function (response) {
     console.log(response);
   });
   ```

3. `AJAX Method:`
   ```javascript
   $.ajax({
     url: "data.json",
     type: "GET",
     success: function (data) {
       console.log("Data:", data);
     },
     error: function (xhr, status, error) {
       console.error("Error:", error);
     },
   });
   ```

---

## Traversing and Filtering

Navigate through DOM elements.

### Methods:

1. `Finding Elements:`

   ```javascript
   // Find all paragraphs inside a div
   $("#myDiv").find("p").css("color", "blue");
   ```

2. `Parent and Children:`

   ```javascript
   // Get the parent
   $("#child").parent().css("border", "1px solid black");

   // Get children
   $("#parent").children().css("margin", "10px");
   ```

3. `Filtering:`

   ```javascript
   // Filter elements
   $("p").filter(".important").css("font-weight", "bold");

   // Exclude elements
   $("p").not(".important").css("color", "gray");
   ```

---

## `get`, `set`, and `check` classes

#### **a. `get` classes**

- Retrieve the class list of an element.
  ```javascript
  const classes = $("#element").attr("class"); // Get all classes as a string
  console.log(classes);
  ```

#### **b. `set` classes**

- Add or remove classes dynamically.
  ```javascript
  $("#element").addClass("new-class"); // Add a class
  $("#element").removeClass("old-class"); // Remove a class
  $("#element").toggleClass("active-class"); // toggle a class
  ```

#### **c. `check` classes**

- Check if an element contains a specific class.
  ```javascript
  if ($("#element").hasClass("target-class")) {
    console.log("Class exists");
  }
  ```

---

## `wrap` and `unwrap` elements

#### **a. `wrap` an element**

- Wrap an element with a new parent element.
  ```javascript
  $("#element").wrap('<div class="wrapper"></div>');
  ```

#### **b. `unwrap` an element**

- Remove the parent element while preserving the child element.
  ```javascript
  $("#element").unwrap();
  ```

---

## `scrollTop` and `scrollLeft`

#### **a. `scrollTop`**

- Gets or sets the number of pixels an element’s content is scrolled vertically.
  ```javascript
  const scrollPosition = $("#element").scrollTop(); // Get current vertical scroll position
  $("#element").scrollTop(100); // Set vertical scroll position to 100px
  ```

#### **b. `scrollLeft`**

- Gets or sets the number of pixels an element’s content is scrolled horizontally.
  ```javascript
  const scrollPosition = $("#element").scrollLeft(); // Get current horizontal scroll position
  $("#element").scrollLeft(100); // Set horizontal scroll position to 100px
  ```

---

## Utilities

Perform common tasks.

### Example:

```javascript
// Iterate over an array
$.each([1, 2, 3], function (index, value) {
  console.log("Index:", index, "Value:", value);
});

// Merge objects
let obj1 = { a: 1 };
let obj2 = { b: 2 };
let result = $.extend({}, obj1, obj2);
console.log(result); // { a: 1, b: 2 }

// Trim whitespace
let text = $.trim("   Hello   ");
console.log(text); // "Hello"
```

---

## Plugins

Extend jQuery functionality using plugins.

### Example: jQuery UI

```javascript
$("#datepicker").datepicker();
```

---

## Advanced AJAX Handling

### Example: Handling Multiple AJAX Calls with `$.when()`

```javascript
// Multiple AJAX requests
let request1 = $.get("data1.json");
let request2 = $.get("data2.json");

// Wait for all requests to complete
$.when(request1, request2).done(function (response1, response2) {
  console.log("Data 1:", response1[0]);
  console.log("Data 2:", response2[0]);
});
```

---

## Animation Queue Control

Manage custom animation queues to control the sequence of animations.

### Example:

```javascript
$("#myDiv")
  .slideUp(1000)
  .queue(function (next) {
    $(this).css("background-color", "yellow");
    next(); // Move to the next animation in the queue
  })
  .slideDown(1000);
```

---

## Extending jQuery

Extend jQuery’s core functionality using `$.extend()`.

### Example:

```javascript
// Add a custom utility method
$.extend({
  capitalize: function (str) {
    return str.charAt(0).toUpperCase() + str.slice(1);
  },
});

// Use the custom method
console.log($.capitalize("hello")); // Output: Hello
```

---
