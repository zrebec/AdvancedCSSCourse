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

For example if I have class `.button` with **yellow** background color in my header and then will I
have `main .button` with **purple color**, all buttons will be with yellow background expect of
button in main section because this selector meets more conditions than usual `.button` class.

class `.button` doesn't has inline style, doesn't has IDs, has 1 class and no elements.
The second selector has no inline, no ID's, one class and one element (`main`). That the reason why
the second declaration wins in `<main>` section.

> Look at <https://codepen.io/littleTheRabbit/pen/QWjgVxR> how specificity works in practice.

#### Remember

Always avoid to !important declaration !!! Because then no one can override your style later! He must
parse your code and find your `!important` and delete it. But in this case can break your code at
whole!

> It's very recommend look at video 14 in section 3 _4:46_ time where starts specificity (time can be
> different in video will be updated)

#### Good way how to start your final css

> At first, remember, source order is very important. Last loaded css wins and override properties in the
> same selector than in class which was loaded before

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
seo readable. Change px to something else like percentage (_hopefully you remember that absolute value for
most browser are 16px_).

### Section 3, Video 19

#### default box-sizing (content-box)

The real dimensions of box is:

- total width = right border + right padding + specified width + left padding + left border
- total height = top border + top padding + specified height + bottom padding + bottom border

Example: height = 0 + 20px + 100px + 20px + 0 = 140px

- With `box-sizing: content-box` is fill content area to padding.

#### most using box-sizing (border-box)

total width = specified width
total height = specified height

Example: height = 0 + 20px + 100px + 20px + 0 = 100px

This means that 20px for both paddings will be nulled

- With `box-sizing: border-box` is filled area including padding. All to the border

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

The css keyword for this is `z-index`

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

> Read more about atomic design, it's super popular

#### Build

Using BEM

- Block Element Modifier
- BLOCK: standalone component that is meaningful on its own.
- ELEMENT: part of a block that has no standalone meaning.
- MODIFIER: a different version of a block or an element.

Low-specificity BEM selectors

```css
.block {
}
.block__element {
}
.block__element--modifier {
}
```

- Block will be card with a user quick profile `.card` (it's organism)
- Elements will be user**photo, user**name, user\_\_email (it's a molecules)
- Card will have a button view detailed profile and delete profile. It will be buttons, atoms independent
  on this card but, you can adjust design button from default to card (then you will have 2 classes at
  minimum). `.btn btn--card`

Look at picture in slides

#### Architect

##### 7-1 Pattern

- 7 different folders for partial Sass files
- 1 main Sass file to import all other files
- 1 compiled stylesheet

###### 7-1 Pattern Folders

- base/ /_Basic definitions_/
- components/ /_1 file for each component (like carousel)_/
- layout/ /_layout of the project_/
- pages/ /_styles for specific pages of the project_/
- themes/ /_for implementation different visual themes_/
- abstracts/ /_like mixins, functions, etc... abstracts which are not generated in finally css_/
- vendors/ /_3rd party css files_/

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
- Open terminal and check nodejs version via `node -v` to check all working
- Move to project folder and type `npm init`
- Fill project info and check `package.json` file to check all is correct
- Install sass via command (still in project folder) `npm install node-sass --save-dev`
  -- save-dev is used to save the package for development purpose. Example: unit tests, minification. (like JDK?)
  -- save is used to save the package required for the application to run. (like just JRE?)
- Then you should to see dependencies in your package.json file
- Install also jquery but not with dev tools, just `mpm install query --save`
- Check in node_modules for directories of modules

> You can re-create node_modules directory by your `package.json` file via command `npm install`

In fact, we don't need jquery (that was a example with `--save` option). So uninstall it via command
`npm uninstall jquery --save`

## Section 4, Video 28

To run node-sass in project, edit your `package.json` file in script section:

```json
"scripts": {
    "compile:sass": "node-sass <input file> <output file> -w"
  },
```

- `w` means watch in this case. That means if I change input file, the script will be ran

then type `npm run compile:sass` to run your script

## Section 4, Video 29

Automatic re-render page if I change it (no need Go Live Server Anymore)

```bash
sudo npm install live-server -g
```

`g` means to install globally because we want install it globally for all projects. ` sudo`` needs for authorize to install global `node_modules```.

in command line write `live-server` to run it globally. And should open the window with your page and it will watch
it globally if you change anything in your page (like `index.html` e.g.)

## Section 5, Video 31

### Converting our css code to Sass: Variables and Nesting

in Sass you can use hex color code as variable. But this
works only in Sass. In normal CSS you must give 3 separate colors and not
just hex code.

```sass
$color-black: #000;
box-shadow: 0 1rem 2rem rgba($color-black, 0.5);
```

Things like `font-family` or `line-height` you don't need it to have as
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

> In \_base.scss we have typography property in html (font-size). But this defines
> the basic font-size and defines what 1rem is. That's the reason why is it better
> to keep it in base

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
   create different version of our website (using just `min-width` and never
   `max-width`. The basic principle is have done webpage for mobile and than
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
- How the `:not` pseudo-class works
- How calc() works, and what's the difference between calc and simple sass
  operations

Beware of using `width` and `max-width`. Using rather `max-width`
instead of first one because it's much responsive.

- `:not` pseudo class is negative of condition. For example
  `:not(:last-child)` means every child expect last one
- With `calc()` function in CSS you can make math operations and mix units
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

> Note in CSS functions you must using Sass variables as above with hashtag.

**Be very careful** when you're using and mixing units with `float`
property. If float will not exact the row `max-width` (e.g if you forgot to
`margin`, next row will be aside until you're using `clear` property.

> Use clearfix mixin (look at code) to get your margin back. If you will not
> include in your row, your row will have 0 height (without margin)

The selector `[class^="col-"]` causes that all class with starts with name
col will including stuff inside the selector. If you remember with `[]`
you can mark any attribute in element. This is DRY principle (Don't repeat yourself)

> Of course, the second way is add a `coll` class to your every column in your
> HTML and keep just specific properties for `col-1-of-2`. Then your element
> attribute will look like `class="col col-1-of-2"` but this is a often better
> way to reach DRY principle.

Byt the you want select any class which just contain `col` instead of start
with `col` you can use asterisk (\*) instead of (^) symbol which is start if
you know regular expressions.

For more info look at my [codepen](https://codepen.io/littleTheRabbit/pen/bGVaYWX)

## Section 5, Video 35

Using Emmet in VS Code or another editor allows write HTML code much faster.
Just remember few rules:

- `.class` crates `<div class="class"></div>`
- `element.class` creates element with class (e.g. `<p>` or
  `<section>`)
- ```.composition>(img.composition__photo.composition__photo--p1)*3```
make

```html
<div class="composition">
    <img src="" alt="" class="composition__photo composition__photo--p1">
    <img src="" alt="" class="composition__photo composition__photo--p1">
    <img src="" alt="" class="composition__photo composition__photo--p1">
</div>
```

If header we have 95% of vieport height with 75vh using in clip-path and then
we will use a next section if different color background, we must calculate
how much vh it's between header and start of section and use negative number
for margin-top. In our example it's. **95vh - 75vh = 20vh** which is our
top margin.

```css
.section-about {
  background-color: $color-grey-light-1;
  padding: 25rem 0;
  margin-top: -20vh;
}
```

If we want text using linear background color we should use
`-webkit-background-clip:` property and then `color: transparent`.
So, to our ```.section-about we add those lines:

```css
display: inline-block;
background-image: linear-gradient(
  to right,
  $color-primary-light,
  $color-primary-dark
);
-webkit-background-clip: text;
color: transparent;
```

This couses that our heading text will be transparent and so... Background
linear gradinet will be visible as our text.

Don't worry. It's has `-webkit` prefix but it works in **Firefox** or
**Opera** too. But not in **Safari** .e.g.

If you're using ```transform``` property e.g. in as hover effect, you can
adding more effects in one line like:

```css
transform: skewY(2deg) skewX(15deg) scale(1.1);
text-shadow: 0.5rem 1rem 2rem rgba($color-black, 0.2);
```

Of course, dont forget to `transition: all 0.2s;` in your heading
(not in hover).

## Section 5, Video 36

- ```&rarr;``` is speacial character for arrow **->**

All HTML special chars you see [here](https://css-tricks.com/snippets/html/glyphs/).

The very small sizes like 1px or 3px we don't need recaluclate to **rem**.
Becuase we want fix this small size if someone zoom their screen for example.

```css
box-shadow: 0 1rem 2rem rgba($color-black, 0.15);
```

We added this to the button as hover effect (code above). Hot it works?

- First number is x-axis shadow
- Second one is y-axis shadow
- Third one is blur
- Last is the color (you should always using **rgba** and using opacity for
shadows)

## Section 5, Video 37

For better understanding absolute and realtive position:

```css
.composition {
  position: relative;
  &__photo {
    position: absolute;
    width: 55%;
    box-shadow: 0 1.5rem 4rem rgba($color-black, 0.4);
    border-radius: 2px;
    z-index: 10;
    transition: all 0.2s;
    outline-offset: 2rem;

    &--p1 {
      left: 0;
      top: -2rem;
    }

    &--p2 {
      right: 0;
      top: 2rem;
    }

    &--p3 {
      left: 20%;
      top: 10rem;
    }

    &:hover {
      outline: 1.5rem solid $color-primary;
      transform: scale(1.05) translateY(-1.5rem);
      box-shadow: 0 2.5rem 4rem rgba($color-black, 0.5);
      z-index: 20;
    }
  }

  &:hover &__photo:not(:hover) {
    transform: scale(0.95);
  }
}
```

and html

```html
<div class="composition">
<img src="img/nat-1-large.jpg" alt="Photo 1"
  class="composition__photo composition__photo--p1">
<img src="img/nat-2-large.jpg" alt="Photo 2"
  class="composition__photo composition__photo--p2">
<img src="img/nat-3-large.jpg" alt="Photo 3"
  class="composition__photo composition__photo--p3">
</div>
```

Look at the code above. The main class has ```relative``` position. This is
very **important**. ```relative``` means like default ```static``` but it's
like ```static``` to the parent and not to the document flow. The modifiders
has ```absolute``` position (but related to ```relative``` parent) and as you
can see, than you play with left, top positioning with children.

It will look like this:

![Compostion](<https://imgur.com/a/iXvJaCP> "Photo composition")

Width of images in **percentages** is also very important. Your pictures
will change the size dynamically without need to **media query**.

```css
transform: scale(1.05) translateY(-1.5rem);
```

causes that hover image will be a bit larger and upper about 1.5rem

Look at to the outline and outline offset. If we hover image, it will be
up to others and they will have outline (like a border). But we cannot set
outline distance. We must set a property ```outline-offset``` in parent.

```&:hover &__photo:not(:hover)``` in parent causes that all
```composition__photo``` elements which is not hover acutally will be smaller
(scale transform proeprty).

## Section 5, Video 38

Link to the Linea Icon font: <https://linea.io/>

Like **awesome fonts** but smaller and more customizable becuase you can
use it also as svg and not icon font.

To the skew the background we can use ```transform``` css property like in
exmaple below (in the ```.section-features```)

```scss
.section-features {
  // ...
  transform: skewY(-7deg);
  margin-top: -10rem;

  & > * {
    transform: skewY(7deg);
  }
}
```

This skew our class ```.section-features``` to -7deg (up to 7 deg) and all
children in ```.section-features``` class will be dropped about 7 deg to down.

And margin top causes up top corners about 10rem(s).

## Section 5, Video 39

In this Video our goals are rotating card, use ```perspective``` in CSS,
use ```backface-visbility``` property in CSS, how use background blend models
and how to use ```box-decoration-break``` property.

## My notes

### Creating a placeholder

The DRY principle is make piece of code just once. So, I'm using on Natours
webpage more effects like text gradient for example. In
```heading-secondary``` or in ```feature-box__icon```. So, just create
placehoder

```scss
%linear-gradient-text {
  display: inline-block;
  background-image: linear-gradient(
    to right,
    $color-primary-light,
    $color-primary-dark
  );
  -webkit-background-clip: text;
  color: transparent;
}
```

and next just implement this

```scss
.feature-box {
  ...

  &__icon {
    @extend %linear-gradient-text;
    ...
  }
}
```

## Section 5: Video 39

Implementation of CSS rotate with pesrpective

```scss
.card {
  perspective: 150rem;
  -moz-perspective: 150rem; // This for firefox working too
  position: relative;
  height: 50rem;

  &__side {
    color: white;
    font-size: 2rem;
    height: 50rem;
    transition: all 0.8s ease; //The easy is important for animation will look smother
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    backface-visibility: hidden;

    &--front {
      background-color: orangered;
    }

    &--back {
      background-color: steelblue;
      transform: rotateY(180deg);
    }
  }

  &:hover &__side--front {
    transform: rotateY(180deg);
  }

  &:hover &__side--back {
    transform: rotateY(0);
  }
}

```

**150rem** is the middle gold way. It's not easy to understand how
perspective numbers works but you should rememember that lower number
means more dramatic effect. If you change that for **15rem** it will be so weird.

Remember, that backside of the card is already rotated of **180deg** in start. That's
the reason why we're adding ```rotateY(0)``` into ```hover``` effect to backside. Now
if you're mouse on backside (which is already rotated), your text oritentation will
be normally.

>Don't remember for ```easy``` value in ```transition``` property. Animamation will
>more smooth.

We have ```height``` property 2 times there. In side and in card. Why? So, card
element is collapsed. When some elemen floats (our positioning to absolute) is like
an floating element, and float elements has 0 dimensions.

And implementation in **HTML**

```html
<div class="card">
  <div class="card__side">
    Card text
  </div>  
</div>
```

## Section 5, Video 40

The problem in last example was that card turns wrong. If you give more time to
transition, you will see that front card will be rotated only to 90deg and then
backside of card will start to rotate. So how to fix it?

Try fix the front side of the card rotation from 180deg to **-180deg**

```scss
&:hover &__side--front {
  transform: rotateY(-180deg);
}
```

Otherwise card rotate will wrong and it could makes a strange animations effects,
in worse case a stroggling card rotate.

The new property in CSS is ```background-blend-mode``` which can combine more
background. This property doesn't work in IE

```scss
&__picture {
  background-size: cover;
  height: 23rem;
  // Next property doesn't work in IE. Only Safari, Firefox and Chrome of course
  background-blend-mode: screen;

  &--1 {
    background-image: linear-gradient(
        to right bottom,
        $color-secondary-light,
        $color-secondary-dark
      ),
      url(../img/nat-5.jpg);
  }
}
```

>This shows how CSS is still more and more powerful. In earlier age you are must to
>use photoshop or some graphics editor to blend mode effect.

The problem in example above is that our box are not rounded anymore because image
overlay a corners. You can fix it with add ```overflow: hidden``` property to your
card side.

```scss
.card {
  ...
  &__side {
    ...
    border-radius: 3px;
    overflow: hidden;
  }
}
```

If we want cut the corners of our background image, we can use a ```clip-path```
property

```css
clip-path: polygon(0 0, 100% 0, 100% 85%, 0 100%);
```

We have 4 inputs (4 dimensions) in example above which means:

1. Where poligon starts 0 on x axis and 0 on y axis (top side)
2. Where first line of polygon ends (100% on x axis and 0 on y axis)
3. Where second line (right side) ends (100% on x asis and 85% on y axis)
4. Where third line ends (0 on x axis and 100% on y axis)

The css property ```text-decoration-break``` with ```clone``` value copy the all
decorations around text in every line of text.

## Section 5, Video 42

### What we learn in this section

- How to make text flow around shapes with ```shape-outside``` and ```float```
- How to apply ```filter``` to images
- How to create background video covering an entire section
- How to use ```<video>``` HTML element
- How and when to use the ```object-fit``` property

### Making circle shape

We can get a circle and text around of radius with ```shape-outside``` property and
known ```clip-path``` property.

```scss
-webkit-shape-outside: circle(50% at 50% 50%);
    shape-outside: circle(50% at 50% 50%);
    -webkit-clip-path: circle(50% at 50% 50%);
    clip-path: circle(50% at 50% 50%);
```

Then you can put img in to the circle:

```html
<figure class="story__shape">
  <img src="img/nat-8.jpg" alt="Person only tour" class="story__img">
</figure>
```

If your image is wider than taller and cannot fill circle shape, you **must chagne
width: 100%;** to ```height: 100%```

Final story card

```scss
.story {
  width: 75%;
  margin: 0 auto;
  box-shadow: 0 3rem 6rem rgba($color: $color-black, $alpha: 0.1);
  background-color: $color-white;
  border-radius: 3px;
  padding: 6rem;
  padding-left: 9rem;
  font-size: $default-font-size;
  transform: skewX(-12deg);

  &__shape {
    width: 15rem;
    height: 15rem;
    float: left;
    -webkit-shape-outside: circle(50% at 50% 50%);
    shape-outside: circle(50% at 50% 50%);
    -webkit-clip-path: circle(50% at 50% 50%);
    clip-path: circle(50% at 50% 50%);
    transform: translateX(-3rem) skewX(12deg);
  }

  &__img {
    height: 100%;
  }
}
```

Rememeber, if you want *skew* the box but not elements inside, you remember, that
general principle is to use **child selector** like

```scss
* > {
  transform: skewX(12deg);
}
```

This will works for the text but not for circle shape beucase we have translate
property already.

The solution is add this just to ```story__text``` class and ```skewX``` value
into ```story__shape``` class.

```scss
&__shape {
  ...
  transform: translateX(-3rem) skewX(12deg);
}

&__text {
  transform: skewX(12deg);
}
```

So, it's a duplicity of our code... This is shame of css but this is how it works now. At once we will have ```skewX``` as a proeprty or ```translateX``` as a css property but this time is this only the one solution.

## Section 5, Video 43

Now we must zoom out the image and show the name of the person on picture.

The first thing we add ```figcaption``` element into our figure

```html
<figure class="story__shape">
  <img src="img/nat-8.jpg" alt="Person only tour" class="story__img">
  <figcaption class="story__caption">Mary Smith</figcaption>
</figure>
```

Now we must edit our figcation position:

```scss
&__caption {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  opacity: 0;
}
```

Remember, if you're adding ```position: absolute```, don't forget to add
```position: relative``` in parent container!

>```Opacity: 0``` is important because we don't want show the text right now

Now we can add ```hover``` action in our ```story_caption``` class inside the
```story``` class.

```scss
&:hover &__caption {
  opacity: 1;
  transform: translate(-50%, -50%);
}
```

don't forget to add animation effect duration:

```scss
&__caption {
  ...
  transition: all 0.5s;
}
```

If you will have a strange effect like a little shake the text at the end of
animation you can fix this with add ```backface-visibility: hidden``` in the
```story__caption``` class.

## Other links (not for project)

Open Weather Map for Bratislava (current weather)
<api.openweathermap.org/data/2.5/weather?q=Bratislava&appid=ce13fc2d411a948e2b5c24786dfc7eb7>
