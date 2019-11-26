---
layout: post
title: "Validating Results"
date: 2019-11-25
---
I went into today with the goal of answering two questions that I think are essential to figure out before AGU:  
1. Are the lithological fractions in Macrostrat correct?
2. Does the North American dolomite record reflect global dolomite/carbonate ratios?

## Lithological fractions
My first thought was to use Marjorie's "Microstrat" database (MCDB) to validate Macrostrat. It did not work. (See macro-micro-fdol-comp.txt) There are only a handful of overlapping units and the databases were compiled using very different methods.

**Next steps:** Take a handful of Macrostrat references and calculate the dolomite fraction in each. Also, look at Jon and Shanan's methods paper to see if they addressed the lithological descriptions at all.

## Global signal?
I remembered from one Husson&Peters paper that they used global map data to compare the signals in the North American record. (This may be the methods paper, too.) I thought I'd found the global data set in Macrostrat:

http://macrostrat.org/api/defs/strat_names?all&response=long&format=csv

but I was wrong (I think). I decided to use a simple proxy for dolomite abundance and looked for stratigraphic names that contained the word *Dolomite*. I think this idea has merit, but the dataset was wrong (I think?) There are some international units in it, but I definitely need to check.

**Next steps:** Find the actual global record from the H/P paper (which one?). Figure out a better way of plotting the 'Dolomite' units in the North American dataset.
