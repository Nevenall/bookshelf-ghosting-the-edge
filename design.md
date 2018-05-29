# Design notes for Ghosting the Edge

- style ordered lists
- work with, especially right aligned, sidebar/callouts to make sure list indicators are comfortably spaced from the main text.
- bump up the main text width for larger screen sizes, between 35 and 38 em? 
- callout styling
  - make a box or some horizontal rules? some kind of decoration?
  - make sure the margins are correct for all size breakpoints.

I would like the rythmn of the sidebars to match better. 
something about the header margins. 

I tried the callouts as typical size font, but I think the thin font seems more like a mistake then an intention. 
Could be thin font. 



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