# Design notes for Ghosting the Edge

I would like the rythmn of the sidebars to match better. 
something about the header margins. 

I tried the callouts as typical size font, but I think the thin font seems more like a mistake then an intention. 

## Default Typographic Details

I'm just about to where I can decide what should be general bookshelf styling and what is book specific. 


## Page Nav

A json array that specifies the full path of each page to include and it's

page order, navigation


PageOrder.json 
``` json
{
  title: "Title of Book",
  pages: [
    // by def first page is the front page. 
    { name: "name of page", path: "path of page" },
    { name: "name of page", path: "path of page" }
  ] 
}
```


## Widths & Margins

Breakpoint | em | Pixels (px) | content width | sidebar width | callout width
1          | 49 | 784
2          | 60 | 960
3          | 90 | 1440
4          | 120| 1920

### Breakpoint | 49em | 784px

sidebars are designed to intrude on the text by half their width
 
Content Width  | 35em
Sidebar Width  | 11.5em    margin: -7em
Sidebar margin | 1em
Callout Width  | 30em
Callout Margin | 1em

### Breakpoint | 60em | 960px
 
Content Width  | 35em
Sidebar Width  | 11.5em
Sidebar margin | 1em
Callout Width  | 30em
Callout Margin | 1em

### Breakpoint | 90em | 1440px
 
Content Width  | 35em
Sidebar Width  | 11em
Sidebar margin | 1em
Callout Width  | 30em
Callout Margin | 1em

### Breakpoint | 120em | 1920px
 
Content Width  | 35em
Sidebar Width  | 11em
Sidebar margin | 1em
Callout Width  | 30em
Callout Margin | 1em

# BookShelf Design Document

Vue 
Vue cli 
Webpack 4
Vuetify


## Touch enabled page turning

Vuetify supports touch events. 


## Niggling bits

The vuetify framework seems to be reflowing the text when the drawer is closed. Hopefully once we start filling out the css that will go away.


## Design Thoughts

### structure for styles

Should we separate the basic typography?
i.e. have a div for the page and colors and format
and another div specifically for typography?
also, can we create a stylus style block in App.vue specifically for setting the theme colors?

typography will vary by font, but we could specify size variables
and expose them for customization
that should work in many instances
but is it good practice to separate the layout from raw typography?
one could make an argument that it's all typography
could we take a generically written css from the pages directory and add the #page scope to it to get something localized? I wonder if sass can do that? 

Sass is great! 

Also, we can do various things to make the styles more readable with scss
We could parcel out the media breakpoints into their various element types. 
Or we could just nest them in reasonable ways. 

the font size and line heights are very dependent on the fonts
but the widths and placement are not so much. 
most of the rythmn is pretty generic. 
either each book overides the various font sizes and line heights in book.scss
or each book can just edit the typography values.


## Todo

- [x] Add basic styling to App.vue
- [x] Add basic typography to App.vue
- [x] add roboto and material design icon fonts as woff(2) files so they can be embedded in the package.
- [x] clean up the scss 
- [ ] need to be able to assign theme colors in css before we can merge
- [ ] make a reduced version of material-icons because we only need like two icons
