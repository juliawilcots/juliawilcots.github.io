---
layout: post
title: "Combining three records in Jupyter Lab"
date: 2019-10-01
---

I started using Jupyter Lab yesterday for no real reason, but it's nice to have individual notebooks in tabs on one browser tab.

Content-wise, I finally plotted the Macrostrat data with the MCDB and Ronov data. **I need to double check that I did everything right,** but as it stands, it appears there is a *smaller* thickness of carbonate* rock in the MCDB than there is in Macrostrat. Before I get to the two explanations I believe we can invoke to explain this, it's important to note that I think we can only look at carbonate thicknesses and how they vary using this database. I believe it is true that Marjorie target carbonate-bearing sections only. Until I know this is not the case I will only look at carbonates. 

Ok, now the two explanations:
1. Marjorie missed some units.
2. The thicknesses in Macrostrat and the MCDB are based on different estimates.

Both are probably true! Marjorie is one person and there are probably some North American units in Macrostrat that are not in her database. This is understandable. It's also definitely true that Macrostrat and Marjorie used different methods to estimate thickness and carb/dol fraction. To explore these two options in more detail I need to:

---
"Ground truth" units between the MCDB and Macrostrat.
---

(I also must remember to write an algorithm that matches all instances of the same strat_id and propagates the max thickness through each instance of that unit.)
