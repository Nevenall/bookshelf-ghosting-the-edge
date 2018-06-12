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

