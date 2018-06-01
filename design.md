# Design notes for Ghosting the Edge

- style ordered lists
- lists have a top/bottom margin that doesn't work with columns. 

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

## Callout Borders

could try a gradient from secondary color to white and see how that looks
when the callout is inline and there is a sidebar in the margin the borders are wrong

also, what about inline callouts? 
