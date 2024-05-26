# Introduction

jQuery is a fast, small, and feature-rich JavaScript library. It simplifies things like HTML document traversal and manipulation, event handling, and animation for rapid web development.

# Basic Setup - Include jQuery:

- Via CDN:
```
<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
```

- Via npm:
```
npm install jquery
```

- Include in your project:
```
<script src="node_modules/jquery/dist/jquery.min.js"></script>
```

# Basic Syntax
```
$(document).ready(function() {
    // jQuery code goes here
});
```

# Selecting Elements
```
By ID: $("#id")
By Class: $(".class")
By Tag: $("tag")
By Attribute: $("[attribute='value']")
```
```
$("#myId").hide();
$(".myClass").css("color", "red");
$("p").text("Hello, World!");
$("[data-toggle='tooltip']").tooltip();
```

# DOM Manipulation

- Get/Set HTML Content: html()
```
$("#myId").html(); // Get HTML content
$("#myId").html("<p>New content</p>"); // Set HTML content
```

- Get/Set Text Content: text()
```
$(".myClass").text(); // Get text content
$(".myClass").text("New text content"); // Set text content
```

- Get/Set Value: val()
```
$("input").val(); // Get value
$("input").val("New value"); // Set value
```

- Add Class: addClass()
```
$("p").addClass("highlight");
```

- Remove Class: removeClass()
```
$("p").removeClass("highlight");
```

- Toggle Class: toggleClass()
```
$("p").toggleClass("highlight");
```

# Event Handling

- Click Event: click()
```
$("#myButton").click(function() {
    alert("Button clicked!");
});
```

- Hover Event: hover()
```
$("#myElement").hover(
    function() {
        // Mouse enter
        $(this).css("background-color", "yellow");
    },
    function() {
        // Mouse leave
        $(this).css("background-color", "");
    }
);
```

- Other Events: focus(), blur(), change(), submit()
```
$("input").focus(function() {
    $(this).css("background-color", "lightblue");
});
```

# AJAX

- Load Data: load()
```
$("#result").load("ajax/test.html");
```

- AJAX GET Request: $.get()
```
$.get("ajax/test.html", function(data) {
    $("#result").html(data);
});
```

- AJAX POST Request: $.post()
```
$.post("ajax/test.html", { name: "John", time: "2pm" }, function(data) {
    $("#result").html(data);
});
```

- AJAX Full: $.ajax()
```
$.ajax({
    url: "ajax/test.html",
    type: "GET",
    dataType: "html",
    success: function(data) {
        $("#result").html(data);
    },
    error: function(xhr, status, error) {
        console.error(xhr, status, error);
    }
});
```

# Effects and Animations

- Hide/Show: hide(), show()
```
$("#myElement").hide();
$("#myElement").show();
```

- Toggle: toggle()
```
$("#myElement").toggle();
```

- Fade: fadeIn(), fadeOut(), fadeToggle()
```
$("#myElement").fadeIn();
$("#myElement").fadeOut();
$("#myElement").fadeToggle();
```

- Slide: slideDown(), slideUp(), slideToggle()
```
$("#myElement").slideDown();
$("#myElement").slideUp();
$("#myElement").slideToggle();
```

- Custom Animations: animate()
```
$("#myElement").animate({ left: '250px', opacity: '0.5' });
```

# Traversing the DOM

- Parent: parent()
```
$("#myElement").parent().css("border", "2px solid red");
```

- Children: children()
```
$("#myElement").children().css("border", "2px solid blue");
```

- Find: find()
```
$("#myElement").find("span").css("color", "green");
```

- Siblings: siblings()
```
$("#myElement").siblings().css("color", "purple");
```

- Next/Prev: next(), prev()
```
$("#myElement").next().css("color", "orange");
$("#myElement").prev().css("color", "pink");
```

# Utilities

- each(): Iterate over a jQuery object.
```
$("p").each(function(index, element) {
    $(element).css("color", "blue");
});
```

- map(): Translate a set of elements.
```
var items = $("li").map(function(index, element) {
    return $(element).text().toUpperCase();
}).get();
console.log(items);
```

- extend(): Merge the contents of two or more objects.
```
var defaults = { name: "John", age: 25 };
var options = { age: 30, city: "New York" };
var settings = $.extend({}, defaults, options);
console.log(settings);
```

# Chaining

jQuery methods can be chained together.
```
$("#myElement").css("color", "red").slideUp(2000).slideDown(2000);
```

# Plugin Creation

- Basic Plugin:
```
(function($) {
    $.fn.myPlugin = function() {
        return this.each(function() {
            $(this).css("color", "blue");
        });
    };
}(jQuery));

// Usage
$("p").myPlugin();
```

# Resources
[jQuery Documentation](https://api.jquery.com/)

