This blog is targeted at javascript developers with experience using React, but many of the design-system concepts should be applicable across any ui-framework.

April 2018 I began my work at Oqton as a principal front-end engineer. Like many engineers working at startups, I came onboard with the understanding that my job would involve writing code (for the front-end), but the specifics would change as the company’s goals evolved. Before working at Oqton, my experience with css was very minimal. I generally felt okay modifying existing css, but I would hesitate if you were to ask me to implement any large feature to match a design specification. At some point during the first week, I noticed a bug in the UI that was only happening on Firefox. I did a bit of googling, wrote a few lines of css, and was very proud of myself when I was able to make a PR that addressed the issue. As the app evolved, our UI-Lead (who had been doing most of the css to this point) had assigned me a few more css-related tickets. I was frustrated by how long it took me to implement designs that I considered “so simple”.

FLEXBOX-ZOMBIES
While googling furiously to find the solution to a css-problem I was stuck on, I came upon the site Flexbox-Zombies. They didn’t have an immediate solution to my problem, but they did completely change the way that I approach css. This site offers an amazing (free) course that teaches you step-by-step how to use flexbox. I can’t say this enough: “Flexbox-Zombies has been one of the most useful learning resources in my career and I recommend it to anyone who uses css”. After completing the flexbox-zombies course, I became more confident in fixing css and even implementing new features.

Our UI-Lead had mentioned that we would be hiring another full-time ui engineer. He had mentioned that they would either be focusing on business-logic or design-system implementation. By this time I had cut my teeth on a few more css tickets. I wondered if I had the skills necessary to implement the styling for our app. I offered that I would be interested in taking ownership of our style implementation and beginning the work in making an official design system for our UI team.

Enough with the coming-of-age css-engineer-with-imposter-syndrome blog. Let’s talk about how our app is set up:

Tools we’ll use
  - Styled Components
  - Styled System
Design System Structure
Our code for the design-system is broken down into the following sections
Foundations
Components
Blocks
Layouts
Workflows

We utilize the StyledComponents library to write CSS-in-JS for our app’s components. In addition to StyledComponents, we use the (similarly-named) StyledSystem, which allows for smarter prop handling when declaring colors, spacing, flex-properties, or anything related to the theme.
Foundations - These are the basic definitions upon which our design-system’s theme are built.
Foundations include the following:
- Colors. Every color that will be used in the app is defined here. In most cases, the color is named based on its usage, rather than on the closest related hue. In some cases, it makes sense to group colors, for example we created a group for status colors.
- Typography. We have defined a map for font-sizes, font-weights, and letter-spacing. Every typography type that we use is defined here with a color, fontSize, fontWeight, letterSpacing, and line height. The fallback for our app (if no typography is uses) is bodyText. If a component’s typography will have its color change based on the state, we will leave that color-switching logic to the component, rather than creating two typography types i.e. if we have inputText, we will not create inputTextError, we will instead overwrite the color for the typography from inside that component. 
  typography,
  elevation,
  frames,
  spacing,
  space: spacing,
  radii,
  breakpoints


Storybook
The Theme
Styled-System
Responsive Layouts
