## README PLZ

Intro to ionic:
-- quick to get started
-- plays pretty well with angular
-- build native mobile apps with web languages

Why use angular:
-- two way data binding, especially sexy with mobile reactivity
-- modularity and compartmentalization
-- very easy to share information across views

What's the point?
Ionic comes with nice built-in styles.
Like twitter's bootstrap, looks very basic
Need to structure the app in an angular-friendly way that enhances compartmentalization
Need to style these things accordingly
Need to be able to quickly override basic components to prototype quickly
Need to be able to use CSS pre-processors like SASS (this only really supports Sass but easy to rewrite to support LESS)

## File Structure

Ionic bootstraps the app with all the nitty gritty in the `/www` directory
By default, the override styles belong in the scss folder, *outside* the `/www` directory
But, if you want to use just CSS, that folder is *inside* the `/www` directory--pretty silly

Let's store all app-related files in `/www`
Let's keep the app-wide styles in one place--`/www/assets`
Let's ditch `/www/js`, since we are in Angular and we will have JS everywhere, having a long JS folder that holds our global app file is silly indeed
Let's then create a file structure that keeps our components(reuseable across the app) and modules (specific feature views) compartmentalized

#### Filters, Services, and Factories

These are closely related to components, resusable code throughout an app. Why not group them there?

1. **Readability**
Say you need to change a specific filter called in a template inside a directive. Would you look in that directive's controller? In the module's controller that calls the directive? By abstracting our file structure, we make our app easier to navigate, read, and contribute to.

2. **Data manipulation vs Interaction manipulation**
Following the MVC mindset, reusable filters, serives, and factories are data manipulators that give you control over the M (Model Data). Whereas components, also reusable, manipulate the V (View). Storing them separately keeps a clean distinction of what thing is good for what purpose.

#### Compartmentalized Styles

To practice what we preach, we should store our component and module styles with their respective templates and controllers. This may seem arbitrary but it helps keep the code base maintainable and readable to people before and after you.

## Style Overrides

`/www/assets/scss` will act as our base styles location. We start out with `base.scss`. Here, we can override Ionic's default style assignments. In `base.scss`, there is a collection of the most commonly changes variables to get us started.

**Best Practice** Don't change files in `/lib`. Even though it works, it will make upgrading version of Ionic and sharing code a nightmare.

In this directory, we can use SASS's `@include` functionality to compartmentalize our custom changes. For example, if you want to style all of Ionic's list styles differently, create a file `_list.scss` and include it in your base.scss files:

```
@import 'list'
...
```

This should get you started!

