# JQUERY

jQuery offers a simple way to achieve a variety of common JavaScript tasks quickly and consistently, across all major browsers and without any fallback code needed.
SELECT ELEMENTS
It is simpler to access elements using jQuery's CSS-style selectors than it is using DOM queries The selectors are also more powerful and flexible.
PERFORM TASKS
jQuery's methods let you update the DOM tree, animate elements into and out of view, and loop through a set of elements, all in one line of code.
HANDLE EVENTS
jQuery includes methods that allow you to attach event listeners to selected elements without having to write any fallback code to support older browsers.


jQuery is a JavaScript file that you include in your web pages.
It lets you find elements using CSS-style selectors and then do something with the elements using jQuery methods
1: FIND ELEMENTS USING CSS-STYLE SELECTORS
A function called JQuery () lets you find one or more elements in the page.
It creates an object called jQuery which holds references to those elements. $() is often used as a shorthand to save typing jQuery (), as shown here.
FUNCTION (CREATES JQUERY OBJECT)

$( ' 1i.hot 1 )
SELECTOR
The jQuery() function has one parameter: a CSS-style selector.
This selector finds all of the <1i> elements with a class of hot.


The jQuery object has many methods that you can use to work with the elements you select. The methods represent tasks that you commonly need to perform with elements.
2: DO SOMETHING WITH THE ELEMENTS USING JQUERY METHODS
Here a jQuery object is created by the j Query () function. The object and the elements it contains is referred to as a matched set or a jQuery selection.
You can then use the methods of the jQuery object to update the elements that it contains. Here, the method adds a new value to the class attribute.
JQUERY OBJECT METHOD
$( '1i.hot' ) .addClass('complete');



CONTENT FILTERS
Get or change content of elements, attributes, text nodes
GET/CHANGE CONTENT
.html()
•text()
.replaceWithQ
.remove()

ELEMENTS
.before()
.after()
.prepend()
.append()
.remove()
.clone()
.unwrap()
.detach()
. empty()
.add()




FINDING ELEMENTS
Find and select elements to work with & traverse the DOM
GENERAL
.find()
.closest()
.parent()
.parents()
.children()
.siblings()
.next()
.nextAll()
.prev()
.prevAll()


EFFECTS & ANIMATION
Add effects and animation to parts of the page
BASIC
.show()
.hide()
.toggle()

FADING
.fadeln()
.fadeOut()
.fadeTo()
.fadeToggle()

SLIDING
.siideOown()
.slideUpO
.slideToggle()


CUSTOM
.delay()
.stop()
.animate()

# CHECKING A PAGE IS READY TO WORK WITH
jQuery’s . ready () method checks that the page is ready for your code to work with.


BASIC EFFECTS
. show () Displays selected elements
.hide() Hides selected elements
. toggl e () Toggles between showing and hiding selected elements

FADING EFFECTS
.fadeln()
Fades in selected elements making them opaque
.fadeOut()
Fades out selected elements making them transparent
.fadeTo()
Changes opacity of selected elements
.fadeToggle()
Hides or shows selected elements by changing their opacity (the opposite of their current state)

SLIDING EFFECTS
.slideUp()
Shows selected elements with a sliding motion
.siideOown()
Hides selected elements with a sliding motion
.sl ideToggleQ
Hides or shows selected elements with a sliding motion (in the opposite direction to its current state)


CUSTOM EFFECTS

. delayO
Delays execution of subsequent items in queue
.stop()
Stops an animation if it is currently running
.animate()
Creates custom animations (see p334)


ANIMATING CSS PROPERTIES
The .animate() method allows you to create some of your own effects and animations by changing CSS properties


