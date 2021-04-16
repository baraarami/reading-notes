## Responsive Web Design


The Internet took off quicker than anyone would have predicted, growing like crazy. Now, for the past few years, mobile growth has exploded onto the scene. The growth of mobile Internet usage is also far out pacing that of general Internet usage growth.
These days it is hard to find someone who doesn’t own a mobile device, or multiple, connected to the Internet. In the UK there are more mobile phones than people, and should trends continue mobile Internet usage will surpass that of desktop Internet usage within the year.

Responsive Overview
Responsive web design is the practice of building a website suitable to work on every device and every screen size, no matter how large or small, mobile or desktop. Responsive web design is focused around providing an intuitive and gratifying experience for everyone. Desktop computer and cell phone users alike all benefit from responsive websites.

Responsive vs. Adaptive vs. Mobile
For some the term responsive may not be new, and others might be even more acquainted with the terms adaptive or mobile. Which may leave you wondering what exactly is the difference between all of them.

Responsive and adaptive web design are closely related, and often transposed as one in the same. Responsive generally means to react quickly and positively to any change, while adaptive means to be easily modified for a new purpose or situation, such as change. With responsive design websites continually and fluidly change based on different factors, such as viewport width, while adaptive websites are built to a group of preset factors. A combination of the two is ideal, providing the perfect formula for functional websites. Which term is used specifically doesn’t make a huge difference.

Mobile, on the other hand, generally means to build a separate website commonly on a new domain solely for mobile users. While this does occasionally have its place, it normally isn’t a great idea. Mobile websites can be extremely light but they do come with the dependencies of a new code base and browser sniffing, all of which can become an obstacle for both developers and users.

Currently the most popular technique lies within responsive web design, favoring design that dynamically adapts to different browser and device viewports, changing layout and content along the way. This solution has the benefits of being all three, responsive, adaptive, and mobile.


Responsive web design is broken down into three main components, including flexible layouts, media queries, and flexible media. The first part, flexible layouts, is the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width. Flexible grids are built using relative length units, most commonly percentages or em units. These relative lengths are then used to declare common grid property values such as width, margin, or padding.

Flexible layouts do not advocate the use of fixed measurement units, such as pixels or inches. Reason being, the viewport height and width continually change from device to device. Website layouts need to adapt to this change and fixed values have too many constraints. Fortunately, Ethan pointed out an easy formula to help identify the proportions of a flexible layout using relative values.

The formula is based around taking the target width of an element and dividing it by the width of it’s parent element. The result is the relative width of the target element.


Flexible Grid
Let’s see how this formula works inside of a two column layout. Below we have a parent division with the class of container wrapping both the section and aside elements. The goal is to have have the section on the left and the aside on the right, with equal margins between the two. Normally the markup and styles for this layout would look a bit like the following.

![Capture2](https://user-images.githubusercontent.com/79080942/115077321-8a123000-9f06-11eb-9398-75f86dab0cab.PNG)
![result](https://user-images.githubusercontent.com/79080942/115077333-8c748a00-9f06-11eb-80d9-7884081da96a.PNG)



Each media query may include a media type followed by one or more expressions. Common media types include all, screen, print, tv, and braille. The HTML5 specification includes new media types, even including 3d-glasses. Should a media type not be specified the media query will default the media type to screen.

The media query expression that follows the media type may include different media features and values, which then allocate to be true or false. When a media feature and value allocate to true, the styles are applied. If the media feature and value allocate to false the styles are ignored.

Logical Operators in Media Queries
Logical operators in media queries help build powerful expressions. There are three different logical operators available for use within media queries, including and, not, and only.

Using the and logical operator within a media query allows an extra condition to be added, making sure that a browser or devices does both a, b, c, and so forth. Multiple individual media queries can be comma separated, acting as an unspoken or operator. The example below selects all media types between 800 and 1024 pixels wide.

@media all and (min-width: 800px) and (max-width: 1024px) {...}

              
The not logical operator negates the query, specifying any query but the one identified. In the example below the expression applies to any device that does not have a color screen. Black and white or monochrome screens would apply here for example.


@media not screen and (color) {...}

              
The only logical operator is a new operator and is not recognized by user agents using the HTML4 algorithm, thus hiding the styles from devices or browsers that don’t support media queries. Below, the expression selects only screens in a portrait orientation that have a user agent capable of rending media queries.

@media only screen and (orientation: portrait) {...}

Aspect Ratio Media Features
The aspect-ratio and device-aspect-ratio features specifies the width/height pixel ratio of the targeted rendering area or output device. The min and max prefixes are available to use with the different aspect ratio features, identifying a ratio above or below that of which is stated.

The value for the aspect ratio feature consist of two positive integers separated by a forward slash. The first integer identifies the width in pixels while the second integer identifies the height in pixels.

Resolution Media Feature
The resolution media feature specifies the resolution of the output device in pixel density, also known as dots per inch or DPI. The resolution media feature does accept the min and max prefixes. Additionally, the resolution media feature will accept dots per pixel (1.3dppx), dots per centimeter (118dpcm), and other length based resolution values.

@media print and (min-resolution: 300dpi) {...}


Flexible Media
The final, equally important aspect to responsive web design involves flexible media. As viewports begin to change size media doesn’t always follow suit. Images, videos, and other media types need to be scalable, changing their size as the size of the viewport changes.

One quick way to make media scalable is by using the max-width property with a value of 100%. Doing so ensures that as the viewport gets smaller any media will scale down according to its containers width.

![Capture3](https://user-images.githubusercontent.com/79080942/115077671-1cb2cf00-9f07-11eb-88f9-7631c27f8f26.PNG)
![result2](https://user-images.githubusercontent.com/79080942/115077672-1de3fc00-9f07-11eb-8548-f6e488a6c379.PNG)

## What is “Float”?
Float is a CSS positioning property. To understand its purpose and origin, we can look to print design. In a print layout, images may be set into the page such that text wraps around them as needed. This is commonly and appropriately called “text wrap”. Here is an example of that.


In page layout programs, the boxes that hold the text can be told to honor the text wrap, or to ignore it. Ignoring the text wrap will allow the words to flow right over the image like it wasn’t even there. This is the difference between that image being part of the flow of the page (or not). Web design is very similar.


In web design, page elements with the CSS float property applied to them are just like the images in the print layout where the text flows around them. Floated elements remain a part of the flow of the web page. This is distinctly different than page elements that use absolute positioning. Absolutely positioned page elements are removed from the flow of the webpage, like when the text box in the print layout was told to ignore the page wrap. Absolutely positioned page elements will not affect the position of other elements and other elements will not affect them, whether they touch each other or not.  

#### What are floats used for?
Aside from the simple example of wrapping text around images, floats can be used to create entire web layouts.

![Capture4](https://user-images.githubusercontent.com/79080942/115078120-ce520000-9f07-11eb-8437-5b65e08c8a0d.PNG)



Clearing the Float
Float’s sister property is clear. An element that has the clear property set on it will not move up adjacent to the float like the float desires, but will move itself down past the float. Again an illustration probably does more good than words do.

Techniques for Clearing Floats
If you are in a situation where you always know what the succeeding element is going to be, you can apply the clear: both; value to that element and go about your business. This is ideal as it requires no fancy hacks and no additional elements making it perfectly semantic. Of course things don’t typically work out that way and we need to have more float-clearing tools in our toolbox.

The Empty Div Method is, quite literally, an empty div. <div style="clear: both;"></div> Sometimes you’ll see a <br> element or some other random element used, but div is the most common because it has no browser default styling, doesn’t have any special function, and is unlikely to be generically styled with CSS. This method is scorned by semantic purists since its presence has no contextual meaning at all to the page and is there purely for presentation. Of course in the strictest sense, they are right, but it gets the job done right and doesn’t hurt anybody.
The Overflow Method relies on setting the overflow CSS property on a parent element. If this property is set to auto or hidden on the parent element, the parent will expand to contain the floats, effectively clearing it for succeeding elements. This method can be beautifully semantic as it may not require additional elements. However if you find yourself adding a new div just to apply this, it is equally as non-semantic as the empty div method and less adaptable. Also bear in mind that the overflow property isn’t specifically for clearing floats. Be careful not to hide content or trigger unwanted scrollbars.
The Easy Clearing Method uses a clever CSS pseudo selector (:after) to clear floats. Rather than setting the overflow on the parent, you apply an additional class like “clearfix” to it. 

Problems with Floats
Floats often get beat on for being fragile. The majority of this fragility comes from IE 6 and the slew of float-related bugs it has. As more and more designers are dropping support for IE 6, you may not care, but for the folks that do care here is a quick rundown.

Pushdown is a symptom of an element inside a floated item being wider than the float itself (typically an image). Most browsers will render the image outside the float, but not have the part sticking out affect other layout. IE will expand the float to contain the image, often drastically affecting layout. A common example is an image sticking out of the main content push the sidebar down below.


Alternatives
If you need text wrapping around images, there really aren’t any alternatives for float. Speaking of which, check out this rather clever technique for wrapping text around irregular shapes. But for page layout, there definitely are choices. Eric Sol right here on A List Apart has an article on Faux Absolute Positioning, which is a very interesting technique that in many ways combines the flexibility of floats with the strength of absolute positioning. CSS3 has the Template Layout Module that, when widely adopted, will prove to be the page layout technique of choice.

Video
I did a screencast a while back explaining many of these float concepts.





The vast majority of websites out there use a grid. They may not explicitly have a grid system in place, but if they have a “main content area” floated to the left a “sidebar” floated to the right, it’s a simple grid.

If a more complex layout presents itself, people often reach for a grid framework. They assume grids are these super difficult things best left to super CSS nerds. That idea is perpetuated by the fact that a lot of the grid systems they reach for are very complicated.

Context
A block level element is as wide as the parent it’s inside (width: auto;). We can think of it as 100% wide. The wrapper for a grid probably don’t have much to do with semantics, it’s just a generic wrapper, so a div is fine.

![GIDE](https://user-images.githubusercontent.com/79080942/115078390-3b659580-9f08-11eb-8194-4447d2df401f.PNG)



If you have ever jumped on an escalator, then you can quickly understand floats.
Your <div> is almost perfect. You decide to introduce some floats to fix the relationship between a few elements.

The next thing you know, your newly floated elements jump out of your carefully chosen order, and stick to the side of your div like a magnet. The phrase “unintended behavior” comes to mind.

I’ve personally spent hours trying to fully understand floats. I’d read an article and say, “Oh, this makes sense!” Then I’d return to my code, try it out and… fail. Back to the drawing board.

I’m going to do my best to spare you this fate.

Floats create alternate flows. This is the hardest part to understand. And once you introduce them, you then need to write your code so that it accounts for up to three flows: normal, left and right. This is a whole new set of rules, as opposed to manipulating the width of elements or their positioning.

Actually, floats are pretty similar to the dynamics of riding an escalator, and I am going to show how they can be used alongside the clear property to create crystal-clear relationships within divs. This way, the next time you try to use floats in your code, you won’t encounter any surprises.

Gotta respect the pass lane

The default flow of elements is kind of like the picture above. Some guy is standing in the middle with his hand on the railing. He’s hogging the entire escalator. Nobody can pass him. Pretty poor escalator etiquette, really.

He is standing behind a bunch of other people that are doing the same thing, so nobody can pass them either. There is no concept of lanes or basic human decency.

This is the scenario when you are not using floats at all.


loats: Left and Right
Using floats can introduce up to two new flows: left and right.


And this allows the normal flow of elements, those without a float value, to fill in the spaces around these elements.


Floats allow you to create these new relationships between flows.

If you had one line of people standing in the middle of the elevator, you would have limited options for new structures. But when you have a left and right column, suddenly you can specify that certain people stand on the right, other ones stay left, and another group can fill in the gaps.

This allows you to create more readable and understandable code, because the float property also gives an indication of an element’s relationship to surrounding elements.

The Clear Property
There is one more wrinkle that we have not discussed yet: the clear property. “Clear” allows elements to specify where they should align in comparison to the floated elements.

In the first picture of the “Floats” section, the two escalator riders were courteously standing on each side of the escalator. This allows others to pass them and move freely as they wish.

Let’s say that instead of having one floated left element and one floated right element, we instead had 3 floated left elements and 1 on the right. The three floated left elements would stack up in a line on the left if we also give them the “clear: left” property. But if they horizontally aligned with the floated right element, it could make it very difficult or even impossible for the normal flow of elements to pass:


“Clear: left” tells each person floating left that they should align themselves behind the first element that is floated left. Depending on the size of the bottom two people, it could be challenging for any normal elements to squeeze through and occupy the space on the top right. So even good escalator practices can still lead to blockages.

One of the most frequent uses of the clear property is “clear:both”. This allows you to reset the flow of elements, as opposed to continuing to maintain a right, left and normal flow. It’s kind of like that guy on the escalator who takes up the whole space because he brought his suitcase.


With “clear:both”, it doesn’t matter where that one guy is standing in orientation to his suitcase. It doesn’t matter who is standing left or right above him. He’s still blocking the entire escalator. People who get on after him will need to start a new flow of elements, which could include any of the three flows: left, right, or normal.

He has escaped the three-flow system and reset the rules. Bad for people that want to run up the escalator? Sure. But it’s good if you want to stop anyone from passing.

Notice how this is different from the one gentleman at the beginning who stood in the middle of the escalator, behind a line of people who were doing the same. That was a one-flow system. “Clear: both” acknowledges that there may be up to three flows, and blocks the passage of any element that follows.

If you enjoyed this post, you may also enjoy my other explanations of challenging CSS and JavaScript topics, such as positioning, Model-View-Controller, and callbacks.

And if you think this might help other people in the same position as you, give it a “heart”!

This post originally appeared on the CodeAnalogies blog.




“SMACSS is becoming one of the most useful contributions to front-end discussions in years” *
I’ve been analyzing my process (and the process of those around me) and figuring out how best to structure code for projects on a larger scale. What I've found is a process that works equally well for sites small and large.

Learn how to structure your CSS to allow for flexibility and maintainability as your project and your team grows.



What is it?
SMACSS (pronounced “smacks”) is more style guide than rigid framework. There is no library within here for you to download or install. There is no git repository for you to clone. SMACSS is a way to examine your design process and as a way to fit those rigid frameworks into a flexible thought process. It is an attempt to document a consistent approach to site development when using CSS. And really, who isn’t building a site with CSS these days?!








