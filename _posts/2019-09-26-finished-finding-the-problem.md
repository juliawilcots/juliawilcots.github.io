---
layout: post
title: "Finished finding the problem"
date: 2019-09-26
---

Yesterday I started digging into Ronov et al. 1980 ("Ronov") and Figure 3 of Husson and Peters 2017 (the oxygen one; "HP17"). My ultimate goal is to find the best way to scale up my record of dolomite abundance through time to a global scale. HP17 successfully used Ronov's data (+ Ronov 1982) to do this with Macrostrat, so I'm trying to figure out exactly what they did.

(Everything I will talk about in this post can be found in the Jupyter notebook ```ronov-musings.ipynb```)

In addition to working with Ronov's data (which is very complete for the Phanerozoic, but less so for the "Upper Proterozoic," and completely lacking anything older than 1600 Ma), I hope to find a way to use Marjorie Cantine's carbonate database ("MCDB") to scale the Precambrian part of Macrostrat records to global. This will be slightly more complicated, because Marjorie *only* compiled stratigraphic columns that contain carbonate to construct her database, so I will have to find some way around this. (Note: 9/27/19: I think Ronov 1982 may be helpful in this regard!)

## Back to HP17+Ronov 1980:  
I first noticed an issue when I tried to recreate Fig. 3a from HP17. I thought this would be a very straightforward task, but I soon ran into some hiccups:

### 1. "The total amount of sediment in Ronov's compilation is 639 million km^3" --HP17

I first (mistakenly) summed all of the volumes in Ronov's **three** "volume" columns in Table 1 ("platforms", "geosynclines" *and* "continents"), for a total of 1278.58 million km^3. This is exactly twice the total reported by HP17. Eventually I realized that "continents" = "platforms" + "geosynclines". I am not sure why Ronov chose this nomenclature. It's confusing. Anyway, the sum of all the volumes in the "continents" column is 639.29 million km^3. 

Reading the rest of Table 1 in Ronov et al. 1980, I saw Ronov broke the total volume into 11 distinct lithologies. Because I am interested in sedimentary rocks (as were HP17), I subtracted the volume of volcanics ("geosyncline submarine-volcanic", "terrestrial volcanic orogenic" and "platform terrestrial trap") from the total volume. **This, I believe, gives me the true total volume of *sediments* per time bin!** (535 million km^3)

This 535 figure is clearly less than HP17's 639, all because **I ignored volcanic rocks**. Upon closer reading of Ronov et al. 1980 I discovered these sentences (in the abstract, not too hard to find...): "The volume of geosynclinal *sediments* of the whole Phanerozoic is 457x10^6 km^3. The volume of platformal *sediments* is 182x10^6 km^3." Summing these figures gives ~639, the number reported by HP17. **I believe HP17 used the figure 639 (instead of 535) due to Ronov's poor word choice!** He called all of the Phanerozoic ***deposits*** *"sediments"*. I agree this is confusing. 

Anyway, I think my total volume of **535 million cubic kilometers** is the correct value to use, so I now take issue with the figure reported in HP17. (Should I tell Jon and Shanan?)

It took me a few hours to figure all of that out, then I ran into problem 2:

### 2. HP17 have 22 data points in Figure 3a; Ronov has 25 time bins in Table 1. 

I needed to figure out: (1) what happened to the missing 3 bins, and (2) why HP17 have a point at ~1600 Ma but Ronov only goes as far back as the "Lower Cambrian". Luckily, this wasn't too hard. HP17 condensed the Cambrian from 3 to 1 time bin, and did the same for the Carboniferous and the Permian.

(I figured out on 9/27/19 that the point at 1600 Ma is from Ronov 1982 -- I'll talk about this later.)

Finally, my volume fluxes (incl. volcanics so the total vol = 639 as in HP17) still weren't equal to HP17's.

### 3. Fixing volume fluxes = fixing time bins

Plotting the data with the geologic timescale (using my function ```add_timescale``` in ```macro_methods.py```), I realized the modern (GSA 2012) definitions of geologic periods and epochs were clearly different than those used by Ronov et al. 1980. (I tried to track down Ronov's reference, but it is an obscure Russian paper from 1975 and I gave up.) Anyway, I realized there were two ways of thinking about Ronov's data in terms of the modern timescale:

  1. Ronov's **names** are correct
  2. Ronov's **dates** are correct
  
HP17 assumed the former, and I believe this is the right thing to do. Basically, this means that Ronov's "Carboniferous" = the modern "Carboniferous." Once I shifted all of the data (based on the names of their periods) to the modern timescale, my volume fluxes matched HP17's exactly and I could recreate the red line in their Figure 3a. 


### SUMMARY
All of this investigation took me about 1 day of work. Ultimately, I think if Husson and Peters had included ~3 more sentences in their paper *or* shared their code / their digitization of Ronov et al. 1980, I would not have had to do any of this.

Also, I still think I am right about the "sediments" vs. "deposits" and the total volume of Phanerozoic *sedimentary* rocks is 535 million km^3, not 639. It remains to be seen whether or not this change will make a difference in my analyses. (I also might redo everything in HP17 to see what changes.)
