# Frontend Mentor - Clipboard landing page solution

This is a solution to the [Clipboard landing page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/clipboard-landing-page-5cc9bccd6c4c91111378ecb9). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size
- See hover states for all interactive elements on the page

### Screenshot

#### Desktop Design
![](./screenshot-desktop.png)

#### Mobile Design
![](./screenshot-mobile.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow

### What I learned

In this project I learned to give fill property to SVG and faced difficulty, We can change the color of a SVG path or element with the fill property. However theres many ways to get it wrong.

So, CSS SVG fill not working is not working then 

1. Make sure to use inline SVGs instead of external
One issue with using fill in CSS that comes up is when using SVG as an external. Lets say we have an external SVG file named apple.svg. Now we want to include that in our

HTML like so (using the <img> tag):
```HTML
  <body>
    <img id="mySVG" src="apple.svg" alt="My Happy SVG" />
  </body>

```
```CSS
  /*  Now when we try to apply the fill CSS style, it will NOT work. */

  
#mySVG {
  fill:red;
}
```
2. If you are using url() method - make sure to encode values such as # in hex colors

```CSS
div {
 background: url("
   <svg xmlns='http://www.w3.org/2000/svg'>
      <path fill='#FF0000'  /* ❌ THIS WILL NOT WORK !  */
         d='M 0,10 H 20 L 10,0 Z' />
  </svg>");
}

```

The problem with the above is that our fill attribute is using a HEX value #FF0000. For url() to work, we need to encode the string. In this case # becomes %23

So the fix will be changing to fill='%23FF0000'

  
```CSS
div {
 background: url("data:image/svg+xml;utf8,
   <svg xmlns='http://www.w3.org/2000/svg'>
      <path fill='%23FF0000' /* ✔️ FIXED ! */
         d='M 0,10 H 20 L 10,0 Z' />
  </svg>");
}
```

3. Check if there is a fill attribute in the SVG itself.
## This was the issue the I faced

Be careful of style conflicts when using the fill attribute. Styles will be applied by the following order:

    inline CSS styles
    fill HTML attribute on the SVG element
    embeded fill styling inside the <defs> tag
    external CSS

So if you already have set a fill value on the SVG element, then remove it from there and add/declare in external CSS

### Useful resources

- [CSS SVG fill not working](https://weekendprojects.dev/posts/fixing-css-svg-fill-not-working/) - We can change the color of a SVG path or element with the fill property. However theres many ways to get it wrong. This post goes over the fixes.

## Author

- Website - [Shashikant](https://www.your-site.com)
- Frontend Mentor - [@shashikantdev3](https://www.frontendmentor.io/profile/shashikantdev3)
- Twitter - [@shashikantdev3](https://www.twitter.com/shashikantdev3)
