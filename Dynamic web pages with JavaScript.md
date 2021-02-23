When creating a web page, you add tags
(known as markup) to the contents of the
page. These tags provide extra meaning
and allow browsers to show users the
appropriate structure for the page.

#  Headings
h1
h2
h3
h4
h5
h6
HTML has six "levels" of
headings:
h1 is used for main headings
h2 is used for subheadings
If there are further sections
under the subheadings then the
h3 element is used, and so
on...

# Paragraph
To create a paragraph, surround
the words that make up the
paragraph with an opening <p>
tag and closing </p> tag.
By default, a browser will show
each paragraph on a new line
with some space between it and
any subsequent paragraphs. 

# Bold & Italic
(b)
By enclosing words in the tags
<b> and (/b) we can make
characters appear bold.
The (لا) element also represents
a section of text that would be
presented in a visually different
way (for example key words in a
paragraph) although the use of
the (b) element does not imply
any additional meaning.
  
  (i)
By enclosing words in the tags
<i> and (/i) we can make
characters appear italic.
The (i) element also represents
a section of text that would be
said in a different way from
surrounding content — such as
technical terms, names of ships,
foreign words, thoughts, or other
terms that would usually be
italicized. 
  
  # Superscript & Subscript
  (sup)
The (sup) element is used
to contain characters that
should be superscript such
as the suffixes of dates or
mathematical concepts like
raising a number to a power such
as 22.

(sub)
The (sub) element is used to
contain characters that should
be subscript. It is commonly
used with foot notes or chemical
formulas such as H20.


# Line Breaks & Horizontal Rules
(br /)
As you have already seen, the
browser will automatically show
each new paragraph or heading
on a new line. But if you wanted
to add a line break inside the
middle of a paragraph you can
use the line break tag (br /).

(hr /)
To create a break between
themes — such as a change of
topic in a book or a new scene
in a play — you can add a
horizontal rule between sections
using the (hr /) tag.


# Visual Editors & Their Code views 
Content management systems and HTML editors such as Dreamweaver
usually have two views of the page you are creating: a visual editor and a
code view.
Visual editors often resemble
word processors. Although
each editor will differ slightly,
there are some features that
are common to most editors
that allow you to control the
presentation of text.
●● Headings are created by
highlighting text then using
a drop-down box to select a
heading.
●● Bold and italic text are
created by highlighting some
text and pressing a b or i
button.
●● New paragraphs are created
using the return or the enter
key.
●● Line breaks are created by
pressing the shift key and the
return key at the same time.
●● Horizontal rules are created
using a button with a straight
line on it.

**Code** views show you the code
created by the visual editor so
you can manually edit it, or so
you can just enter new code
yourself. It is often activated
using a button with an icon
that says HTML or has angled
brackets. White space may be
added to the code by the editor
to make the code easier to read.

# Semantic Markup
There are some text elements that are not intended to affect the
structure of your web pages, but they do add extra information to the
pages — they are known as semantic markup.

# Strong & Emphasis
(strong)
The use of the (strong)
element indicates that its
content has strong importance.
For example, the words
contained in this element might
be said with strong emphasis.
By default, browsers will show
the contents of a (strong)
element in bold.

(em)
The (em) element indicates
emphasis that subtly changes
the meaning of a sentence.
By default browsers will show
the contents of an (em) element
in italic.

# Quotations
There are two elements
commonly used for marking up
quotations:
(blockquote)
The (blockquote) element is
used for longer quotes that take
up an entire paragraph. Note
how the (p) element is still
used inside the <blockquote>
element.
Browsers tend to indent the
contents of the (blockquote)
element, however you should not
use this element just to indent a
piece of text — rather you should
achieve this effect using CSS.


(q)
The (q) element is used for
shorter quotes that sit within
a paragraph. Browsers are
supposed to put quotes around
the (q) element, however
Internet Explorer does not —
therefore many people avoid
using the (q) element.


# Abbreviations & Acronyms
(abbr) html HTML
If you use an abbreviation or
an acronym, then the <abbr>
element can be used. A title
attribute on the opening tag is
used to specify the full term.
  
  
  # Citations & Definitions
  (cite)
When you are referencing a
piece of work such as a book,
film or research paper, the
(cite) element can be used
to indicate where the citation is
from.
In HTML5, (cite) should not
really be used for a person's
name — but it was allowed in
HTML 4, so most people are
likely to continue to use it.

(dfn)
The first time you explain some
new terminology (perhaps an
academic concept or some
jargon) in a document, it is
known as the defining instance
of it.
The (dfn) element is used to
indicate the defining instance of
a new term.

# Author Details
(address)
The (address) element has
quite a specific use: to contain
contact details for the author of
the page.
It can contain a physical address,
but it does not have to. For
example, it may also contain a
phone number or email address.

# Changes to Content
(ins)
(del)
The (ins) element can be used
to show content that has been
inserted into a document, while
the (del) element can show text
that has been deleted from it.

# (s)
The (s) element indicates
something that is no longer
accurate or relevant (but that
should not be deleted).
Visually the content of an (s)
element will usually be displayed
with a line through the center.

# There are lots of occasions when we
need to use lists. HTML provides us with
three different types:

* Ordered lists are lists where each item in the list is
numbered. For example, the list might be a set of steps for
a recipe that must be performed in order, or a legal contract
where each point needs to be identified by a section
number.
* Unordered lists are lists that begin with a bullet point
(rather than characters that indicate order).
* Definition lists are made up of a set of terms along with the
definitions for each of those terms.


# (ol)
The ordered list is created with
the (ol) element.
(li)
Each item in the list is placed
between an opening (li) tag
and a closing (/li) tag. (The li
stands for list item.)

# (ul)
The unordered list is created
with the (ul) element.
(li)
Each item in the list is placed
between an opening <li> tag
and a closing (/li) tag. (The li
stands for list item.) 
  
  
  # Definition Lists
  (dl)
The definition list is created with
the (dl) element and usually
consists of a series of terms and
their definitions.
Inside the (dl) element you will
usually see pairs of <dt> and
(dd) elements.
(dt)
This is used to contain the term
being defined (the definition
term).
(dd)
This is used to contain the
definition.
  
  
  # Nested lists
You can put a second list inside
an <li> element to create a sublist
or nested list.
  
  
  
  
