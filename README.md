# Frontend Mentor - FAQ accordion card solution

This is a solution to the [FAQ accordion card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/faq-accordion-card-XlyjD0Oam). Frontend Mentor challenges help to improve coding skills through realistic projects.

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
- [Acknowledgments](#acknowledgments)

## Overview

### The challenge

This is a frontend project which implements a FAQ Accordion Card. Users should be able to:

- View the optimal layout for the component depending on their device's screen size;
- See hover states for all interactive elements on the page;
- Hide/Show the answer to a question when the question is clicked.

### Screenshot

- [Desktop-Screenshot](./screenshots/Desktop-Screenshot.png)
- [Mobile-Portrait-Screenshot](./screenshots/Mobile-Portrait-Screenshot.png)
- [Mobile-Landscape-Screenshot](./screenshots/Mobile-Landscape-Screenshot.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### What I learned

While working on this project, I have gained plenty of valuable knowledge which have strengthened my understanding on important concepts.

Since I chose to complete this project without Javascript, it was comparatively difficult and lengthy to accomplish the task successfully. However, it was a good choice to step out the comfort zone. As I was confused about everything, I revised many basic concepts, researched new elements and methods, tried different combinations, made several mistakes and eventually, figured out the way to finish the challenge. I believe that the overall learning process has been very productive and motivating for me.

Below, I have highlighted some key areas that I have learnt while working on this challenge.

- Illustration section:

  - With different illustrations for both the desktop and mobile versions, I struggled to find the best way to position the images in order to closely reflect the design. Here, I learnt how to position images absolutely and relatively.

  - After a lot of trial and error, I also realised that it was a better approach to use some illustrations as `background-image` so that their url could be simply changed with CSS to complement the responsive styles.

- FAQ section:

  - This part of the project was particularly challenging because I had little idea of the elements I should use along with a clever combination of CSS to achieve the desired results without Javascript.

    - At first, I learnt that in order to track and utilize the click event of the drop-down arrow with only CSS, it is necessary to use specific pseudo classes.

    - I learnt that the correct approach is to use checkbox type input for the Faq questions and a corresponding `<label>` tag with the same unique `id`. Thus, the `:checked` property can be used with the `<input>` tag to target and style the respective labels, questions and answers.

    - As there are multiple Faq questions and answers and the goal is to display only one answer unless the mouse clicks somewhere else, I bumped upon an issue where more than one answer would open up simultaneously. That's when I learnt about the `tabindex` attribute which allows an HTML element to receive focus and the `:focus-within` property which enables us to apply styling on the focused element.

    - Since I applied styles to many child elements inside each Faq, I resorted to a more precise styling. To do so, I used the `:focus-within` class with the parent `.faq` element instead of just `:focus`.

    ```html
    <!-- Container for a FAQ - has question and answer -->
    <div class="faq arrangement" tabindex="1">
      <!-- Input to connect the label to, but this will remain hidden -->
      <input type="checkbox" id="uniqueID" unchecked />

      <!-- question -->
      <div class="question arrangement">
        Sample FAQ Question

        <!-- Drop down arrow symbol which shows or hides the answer on click -->
        <label for="uniqueID">
          <img class="arrow" src="./images/icon-arrow-down.svg" alt=""
        /></label>
      </div>

      <!-- answer -- This is expandible/ collapsible -->
      <div id="n_ans" class="arrangement answer">Sample answer.</div>
    </div>
    ```

    ```css
    /* Focus styles */

    .faq:focus-within > input[type="checkbox"]:checked + .question {
      color: var(--Very-dark-desaturated-blue);
      font-weight: 700;
    }

    .faq:focus-within
      > input[type="checkbox"]:checked
      + .question
      > label
      > img {
      transform: rotate(180deg);
    }

    .faq:focus-within > input[type="checkbox"]:checked ~ .answer {
      display: flex;
      height: 54px;
    }
    ```

- Media Queries:

  - I have created a separate stylesheet for the responsive styles. In that CSS file, I have used media queries to create separate styles for Portrait and Landscape modes and for different devices - Smartphone, Tablet, iPad, Laptop, Desktop.

  Here's a short example:

  ```css
  @media only screen and (min-width: 375px) and (max-width: 1440px) and (orientation: portrait) {
    #box-icon {
      content: none;
      display: none;
    }
  }

  @media only screen and (min-width: 375px) and (orientation: landscape) {
    #box-icon {
      content: url(./images/illustration-box-desktop.svg);
      position: absolute;
      z-index: 3;
    }
  }
  ```

### Continued development

I would like to learn more about pseudo classes, practice and incorporate them into future projects because I found them quite useful and I want to be able to use them comfortably. I also realised that working with such CSS techniques can sometimes allow us to avoid the use of Javascript and keep the build simple.

### Useful resources

- [Toggle Content without Javascript](https://enmascript.com/articles/2019/09/26/toggle-content-on-click-without-javascript) - This is a detailed article which helped me to understand the concept behind the `:target` selector when I had no prior knowledge. However, this resource has implemented the URL method or anchor tag, which I did not use in my project.

- [The “Checkbox Hack” (and things you can do with it)](https://css-tricks.com/the-checkbox-hack/) - This article has many examples of the label-input combination and their applications in real projects. Studying the detailed examples and explanations in this article really helped me to strengthen my knowledge.

- [Media Queries for common device breakpoints](https://ui.dev/rwd/develop/browser-feature-support/media-queries-for-common-device-breakpoints) - I learnt and used some device dimensions from this article to make my project as responsive as possible.

## Author

- Porfolio / Website - [Hajera Khatun Saba](https://hksaba-portfolio.netlify.app/)
- Frontend Mentor - [@HKSABA](https://www.frontendmentor.io/profile/HKSABA)
