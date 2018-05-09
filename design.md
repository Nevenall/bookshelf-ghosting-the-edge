# Design notes for Ghosting the Edge

- need to style lists and tables
- we need to specify callout-left and callout-right
- Also, right now asides are styled with headers like the rest of the text, which doesn't work well. 
  - either we should use raleway sized up for aside headers, or do the math to reduce the abel headers
- i wonder of light body font would be good for stat blocks, because then bold will have more contrast?
- can we have css automatically calculate some of the various sizes? can we use more dynamic stuff?
  - or is it better to do break point styling? 
- we should have separate sidebar and callout containers. sidebars go in margin, callouts have their own box. they might be articles not asides. they are still marginalia. well, some are. some are figures, like, the famous faces callout, vs a list of character creation stuff. 
  - sounds like we need several well defined containers. 