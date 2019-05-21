> This blog is targeted at javascript developers with experience using React, but many of the design-system concepts should be applicable across any User Interface (UI). 

The goal of this blog is to give a brief background about myself and then spend a lot of time talking about what helped get me up to speed and how we set up our design system. It's also a bit of a brain-dump for myself so that I don't forget anything 🧠.

April 2018 I began my work at Oqton as a principal front-end engineer. Like many engineers working at startups, I came onboard with the understanding that my job would involve writing code (for the front-end), but the specifics would change as the company’s goals evolved. Before working at Oqton, my experience with css was very minimal. I generally felt okay modifying existing css, but I would hesitate if you were to ask me to implement any large feature to match a design specification. At some point during the first week, I noticed a bug in the UI that was only happening on Firefox. I did a bit of googling, wrote a few lines of css, and was very proud of myself when I was able to make a PR that addressed the issue. As the app evolved, our UI-Lead (who had been doing most of the css to this point) had assigned me a few more css-related tickets. I was frustrated by how long it took me to implement designs that, on first-glance, I considered “so simple”.

# FLEXBOX-ZOMBIES
While googling furiously to find the solution to a css-problem I was stuck on, I came upon the site [Flexbox-Zombies](https://mastery.games/p/flexbox-zombies). They didn’t have an immediate solution to my problem, but they did completely change the way that I approach css. This site offers an amazing (free) course that teaches you step-by-step how to use flexbox. I can’t say this enough: 

**“Flexbox-Zombies has been one of the most useful learning resources in my career and I recommend it to anyone who uses css”.** 

After completing the flexbox-zombies course, I became more confident in fixing css and even implementing new features.

Our UI-Lead had mentioned that we were potentially looking to hire another UI engineer. He had mentioned that the candidate would either be focusing on business-logic or design-system implementation. By this time I had cut my teeth on a few more css-related tickets. I wondered if I had the skills necessary to implement the styling for our app. I offered that I would be interested in taking ownership of our style implementation and beginning the work in making an official design system for our UI team.

## Let’s talk about how we set up our app's design system:
# Tools we use(d)
  We had started out using Rebass (v2) for styling all of our React components. Rebass is a great library and I would highly recommend it as a starting point for any design system. Later in this blog I'll go over how we rolled our own alternative to Rebass to meet our needs.
# Tools we use
  ## Styled Components
We utilize the StyledComponents library to write CSS-in-JS for our app’s components.
  ## Styled System
This library is great for creating easy-to-use props for consuming your themed components.

# Design System Structure
We've broken our code for the design-system into the following sections:  
- Foundations
- Components
- Blocks
- Layouts
- Workflows

Foundations - These are the basic definitions upon which our design-system’s theme are built.
Foundations include the following:
- Colors: Every color that will be used in the app is defined here. In most cases, the color is given a name based on its usage, rather than on the closest related hue (i.e. primary, secondary, tertiary, accent). In some cases, it makes sense to group colors, for example we created a group for status colors, and it may make sense to also have a standard dictionary of rainbow-esque colors.
- Typography: We have defined a map for font-sizes, font-weights, and letter-spacing. Every typography type that we use is defined here with a color, fontSize, fontWeight, letterSpacing, and line height. If a component’s typography will have its color change based on the state, we will leave that color-switching logic to the component, rather than creating two typography types i.e. if we have inputText, we will not create inputTextError, we will instead overwrite the color for the typography from inside that component. 
- Elevation: To avoid any rogue z-index values, every declaration of z-index in the UI is based on an elevation level defined by our elevation object
- Frames: Frames are used for having a consistent set of styles whenever we want to add border-radius, box-shadow, and background color to a div
- Spacing: All of our definitions of margin and padding are based on the spacing object. As a rule of thumb, if you're writing a hard-coded pixel value that's less than 32px, you should probably be using a spacing property
- Radii: We don't use this very often, but ideally, you could define all of your border radius values here.
- Breakpoints: We try to target 4 device types in our app: "small", "medium", "large", and "extra-large", 0, 768, 1280, and 1780px (respectively)

Components - Any reusable react component falls into the category of `Components`. The idea is, the components should be greedy, as in they will try to take up as much width as they have been given.

Blocks - We created the `Blocks` category for any components that needed to behave differently at different breakpoints. Ideally, Blocks should not implement any new component, but rather utilize existing components and add on some responsive magic

Layouts - Layouts are Meta-Components that `Lay Out` how content on a particular type of page is arranged. The layouts should behave differently at different breakpoints.

Workflows - Workflows are where the rubber meets the road. This is where we implement the actual pages that will be used in our app. For example, we may have a Part List Workflow and a Material List Workflow, which both would consume the List Layout.

#Storybook
For implementing and documenting all of our foundations, components, blocks, and layouts we used Storybook. It's an amazing library that allows users to easily document 
Storybook
The Theme
Styled-System
Responsive Layouts
