# Resources

## ZTH Resources

### Section 2, Video 6

Clip path maker: <https://bennettfeely.com/clippy/>

### Section 2, Video 8

Animation timing functions: <https://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp>

### Section 2, Video 9

Pseudo classes: <https://www.w3schools.com/css/css_pseudo_classes.asp>

### Section 2, Video 10

Animation fill mode <https://www.w3schools.com/cssref/css3_pr_animation-fill-mode.asp>

### Section 3, Video 12

For this section looks to the slides-students-C04.key presentation

#### 3 Pillars of good HTML a CSS

##### Responsive design

- Fluid layouts
- Media queries
- Correct units
- Desktop-first vs mobile-first

##### Maintainable and scalable code

- Clean
- Easy-to-understand
- Growth
- Reusable
- How to organize files
- How to name classes
- How to structure HTML

##### Web performance

- Less HTTP requests
- Less code
- Compress code
- Use a CSS preprocessor
- Less images
- Compress images

> Questions post into Q&A in Discord

### Section 3, Video 14

Look at the specificity what style wins. Winner is style what meets at most specificities in this
categories:

- Inline
- IDs
- Classes
- Elements

For example if I have class ```.button``` with **yellow** background color in my header and then will I
have ```main .button``` with **purple color**, all buttons will be with yellow background expect of
button in main section because this selector meets more conditions than usual ```.button``` class.

class ```.button``` doesn't has inline style, doesn't has IDs, has 1 class and no elements.
The second selector has no inline, no ID's, one class and one element (```main```). That the reason why
the second declaration wins in ```<main>``` section.

>Look at <https://codepen.io/littleTheRabbit/pen/QWjgVxR> how specificity works in practice.

#### Remember

Always avoid to !important declaration !!! Because then no one can override your style later! He must
parse your code and find your ```!important``` and delete it. But in this case can break your code at
whole!

>It's very recommend look at video 14 in section 3 *4:46* time where starts specificity (time can be
>different in video will be updated)

#### Good way how to start your final css

>At first, remember, source order is very important. Last loaded css wins and override properties in the
>same selector than in class which was loaded before

1. Variables
2. Declare just elements
3. Declare ID's
4. Declare classes
5. Declare pseudo classes

### Section 3, Vide 16

How CSS values are processed? This is important for many reasons. You're using units for measuring in CSS
like pixels (px), points (pt), em or rem, vh (viewport height) or vw (viewport width). But how it's
processed into real units on your display?

More on my codepen: <https://codepen.io/littleTheRabbit/pen/GRpvROq>

### Section 3, Video 18

Continue work on Natours project. Recalculating our absolute values to relative values. See the video
for more details

Recalculated properties from root font-size to relative units:

- padding
- margin
- top, left, bottom, right
- width, height
- font properties like (font-size, letter-spacing)
- transform
- box-shadow

#### Why is using px is a bad practice

Using pixels in any element (within root html element) it's a bad idea because your web be less
seo readable. Change px to something else like percentage (*hopefully you remember that absolute value for
most browser are 16px*).

### Section 3, Video 19

#### default box-sizing (content-box)

The real dimensions of box is:

- total width = right border + right padding + specified width + left padding + left border
- total height = top border + top padding + specified height + bottom padding + bottom border

Example: height = 0 + 20px + 100px + 20px + 0 = 140px

- With ```box-sizing: content-box``` is fill content area to padding.

#### most using box-sizing (border-box)

total width = specified width
total height = specified height

Example: height = 0 + 20px + 100px + 20px + 0 = 100px

This means that 20px for both paddings will be nulled

- With ```box-sizing: border-box``` is filled area including padding. All to the border

#### Box types

##### Block

- Elements are formatted visually as blocks
- 100% if parent width
- Vertically, one after another
- **Box-model applies as showed**

```css
display: block;
display: flex;
display: list-item;
display: table;
```

##### Inline

- Content is distributed in lines
- **Occupies only content's space**
- **No line-breaks**
- No heights and widths
- Paddings and margins only horizontal (left and right)

```css
display: inline;
```

##### Inline block

Combines **block** and **inline** box model

- A mix of block and inline
- Occupies only content's space (like **inline** box model)
- No line-breaks (like **inline** box model)
- Box-model applies as showed (like **block** box model)

```css
display: inline-block;
```

#### Positioning schemes

##### Normal flow

- Default positioning scheme;
- NOT floated;
- NOT absolutely positioned;
- Elements laid out according to their source order.

```css
position: relative;
```

##### Floats

- Element is removed from the normal flow
- Text and inline elements will wrap around the floated element;
- The container will not adjust its height to the element.

```css
float: left;
float: right;
```

##### Absolute positioning

- Element is removed from the normal flow
- No impact on surrounding content or elements;
- We use top, bottom, left and right to offset the element from its relatively positioned container.

Floats and absolute positioning haven't equal that **Element is removed from the normal flow**
Floats and absolute positioning haven't equal that
**Text and inline elements will wrap around the floated element** to
**No impact on surrounding content or elements**

```css
position: absolute;
position: fixed;
```

#### Stacking context

Stacking context is the solution for overflowing content of boxes

The css keyword for this is ```z-index```

We have 3 layers for example:

- Layer 1 (totally last and behind others)

```css
z-index: 1;
position: relative;
```

- Layer 2 (Between 1 and 3)

```css
z-index: 2;
position: absolute;
```

- Layer 3 (Highest layer - on the top)

```css
z-index: 3;
position: relative;
```

Look at the Video 19 in section 3 or slides

### Section 3, Video 20

Look CSS Architecture, Components and BEM in slides and video

- Think at first how layout should look before you start writing the code
- Build layout in HTML and CSS with a consistent structure for naming classes (e.g. BEM)
- Architect Create a logical architecture of your CSS with files and folders

#### Think

Component-Driven design

- Modular building blocks (like carousel or aside box with news)
- Held together by the layout of the page
- Re-usable across a project and between different projects (think about naming conventions e.g.)
- Independent, allowing us to use them anywhere on the page

##### Atomic design (for better memorize)

- Atoms
- Molecules
- Organisms (component)
- Templates
- Pages

>Read more about atomic design, it's super popular

#### Build

Using BEM

- Block Element Modifier
- BLOCK: standalone component that is meaningful on its own.
- ELEMENT: part of a block that has no standalone meaning.
- MODIFIER: a different version of a block or an element.

Low-specificity BEM selectors

```css
.block {}
.block__element {}
.block__element--modifier {}
```

- Block will be card with a user quick profile ```.card``` (it's organism)
- Elements will be user__photo, user__name, user__email (it's a molecules)
- Card will have a button view detailed profile and delete profile. It will be buttons, atoms independent
  on this card but, you can adjust design button from default to card (then you will have 2 classes at
  minimum). ```.btn btn--card```

Look at picture in slides

#### Architect

##### 7-1 Pattern

- 7 different folders for partial Sass files
- 1 main Sass file to import all other files
- 1 compiled stylesheet

###### 7-1 Pattern Folders

- base/ /*Basic definitions*/
- components/ /*1 file for each component (like carousel)*/
- layout/ /*layout of the project*/
- pages/ /*styles for specific pages of the project*/
- themes/ /*for implementation different visual themes*/
- abstracts/ /*like mixins, functions, etc... abstracts which are not generated in finally css*/
- vendors/ /*3rd party css files*/

## Section 4, Video 23

### Why Sass

- **Variables**: for reusable values such as colors, font-sizes, spacing, etc...
- **Nesting**: to nest selectors inside of one another, allowing us to write less code
- **Operators**: for mathematical operations right inside of CSS
- **Partial and imports**: to write CSS in different values and importing them all into one single file
- **Mixins**: to write reusable pieces of CSS code
- **Functions**: similar to mixins, with difference that they produce a value that can be used
- **Extends**: to make different selectors inherit declarations that are common to all of them
- **Control directives**: for writing complex code using conditionals and loops (not covered in this course)

## Section 4, Video 27

### Why Node.js

Allows developers to write and run JavaScript code on server. Developers started using node.js to also write too to help
with local development

In this course we will using node.js as helper with local development (like Sass)

### npm

npm is Node Package Manager. Simple command line interface that allows developers to install and manage packages on
their local computers. There are all kinds of open source tools, libraries and frameworks needed for modern development.
Modern web development could simply not exist without package manager.

### Installing Sass on local computer

- Download node.js from <https://nodejs.org/en/download> and install it
- Open terminal and check nodejs version via ```node -v``` to check all working
- Move to project folder and type ```npm init```
- Fill project info and check ```package.json``` file to check all is correct
- Install sass via command (still in project folder) ```npm install node-sass --save-dev```
  -- save-dev is used to save the package for development purpose. Example: unit tests, minification. (like JDK?)
  -- save is used to save the package required for the application to run.  (like just JRE?)
- Then you should to see dependencies in your package.json file
- Install also jquery but not with dev tools, just ```mpm install query --save```
- Check in node_modules for directories of modules

>You can re-create node_modules directory by your ```package.json``` file via command ```npm install```

In fact, we don't need jquery (that was a example with ```--save``` option). So uninstall it via command
```npm uninstall jquery --save```

## Section 4, Video 28

To run node-sass in project, edit your ```package.json``` file in script section:

```json
"scripts": {
    "compile:sass": "node-sass <input file> <output file> -w"
  },
```

- ```w``` means watch in this case. That means if I change input file, the script will be ran

then type ```npm run compile:sass``` to run your script

## Section 4, Video 29

Automatic re-render page if I change it (no need Go Live Server Anymore)

```bash
sudo npm install live-server -g
```

```g``` means to install globally because we want install it globally for all projects. ```sudo`` needs for authorize
to install global```node_modules```.

in command line write ```live-server``` to run it globally. And should open the window with your page and it will watch
it globally if you change anything in your page (like ```index.html``` e.g.)

## Section 5, Video 31

### Converting our css code to Sass: Variables and Nesting

in  Sass you can use hex color code as variable. But this
works only in Sass. In normal CSS you must give 3 separate colors and not
just hex code.

```sass
$color-black: #000;
box-shadow: 0 1rem 2rem rgba($color-black, 0.5);
```

Things like ```font-family``` or ```line-height``` you don't need it to have as
variables because you usually defines only once this things.

## Section 5, Video 32

### Implementing 7-1 architecture with Sass

For directory structure, look at Section 3: Video 20 -> Architect -> 7-1 pattern.

- abstracts (variables, mixins, functions)
- base (animations, typography, utilities)
- components (buttons)
- layout (header, footer)
- pages (home)
- main.scss (including above)

>In _base.scss we have typography property in html (font-size). But this defines
>the basic font-size and defines what 1rem is. That's the reason why is it better
>to keep it in base

## Section 5, Video 33

### Basic principles of responsive layout

1. Fluid Grids and Layouts
  To allow content easily adapt to the current viewport width used to browse the
  website. Uses % rather than px for all layout-related dimensions.
2. Flexible / Responsive images
 Images behave differently that text content, and so we need to ensure that
 they also adapt nicely to the current viewport
3. Media queries
  To change styles on certain viewport widths (breakpoints), allowing to
  create different version of our website (using just ```min-width``` and never
  ```max-width```. The basic principle is have done webpage for mobile and than
  adding content or changing layout on larger output devices)

#### Types of layouts in our projects

- Float layouts (Natours Project)
- Flexbox (Trillo Project)
- CSS Grid (Nexter Project)

## Section 5, Video 34

Fluid responsive layout with floats. This is probably longest video in course. Here
will be just small pieces of video. Look at your abbreviations and look vide again
if something is not clear. Many comments are in code too.

### What we learn

- How to architect and build a simple grid system
- How the attribute selectors works
- How the ```:not``` pseudo-class works
- How calc() works, and what's the difference between calc and simple sass
operations

Beware of using ```width``` and ```max-width```. Using rather ```max-width```
instead of first one because it's much responsive.

- ```:not``` pseudo class is negative of condition. For example
```:not(:last-child)``` means every child expect last one
- With ```calc()``` function in CSS you can make math operations and mix units
which is very useful.

```css
[class^="col-"] {
    float: left;

    &:not(:last-child) {
      margin-right: $gutter-horizontal;
    }
}

.col-1-of-2 {
  width: calc((100% - #{$gutter-horizontal}) / 2);
  background-color: orangered;
}
```

This divides 100% width of your window minus your spacing between columns and make
2 columns with exact width.

>Note in CSS functions you must using Sass variables as above with hashtag.

**Be very careful** when you're using and mixing units with ```float```
property. If float will not exact the row ```max-width``` (e.g if you forgot to
```margin```, next row will be aside until you're using ```clear``` property.

>Use clearfix mixin (look at code) to get your margin back. If you will not
>include in your row, your row will have 0 height (without margin)

The selector ```[class^="col-"]``` causes that all class with starts with name
col will including stuff inside the selector. If you remember with ```[]```
you can mark any attribute in element. This is DRY principle (Don't repeat yourself)

>Of course, the second way is add a ``coll`` class to your every column in your
>HTML and keep just specific properties for ```col-1-of-2```. Then your element
>attribute will look like ```class="col col-1-of-2"``` but this is a often better
>way to reach DRY principle.

Byt the you want select any class which just contain ```col``` instead of start
with ```col``` you can use asterisk (*) instead of (^) symbol which is start if
you know regular expressions.

For more info look at my [codepen](https://codepen.io/littleTheRabbit/pen/bGVaYWX)

## Other links (not for project)

Open Weather Map for Bratislava (current weather)
<api.openweathermap.org/data/2.5/weather?q=Bratislava&appid=ce13fc2d411a948e2b5c24786dfc7eb7>
