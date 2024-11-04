# #30DayMapChallenge 2024

[link to site](https://30daymapchallenge.com/)

![This years themes](30dmc_2024.png)


## 1 - Points
[notebook for day 1](day1/day1.ipynb)
>30DayMapChallenge classic: A map with points. Start the challenge with points. Show individual locations—anything from cities to trees or more abstract concepts. Simple, but a key part of the challenge. 📍

![](day1/day1_zurich.png)

from [the OpenStreetMap Wiki](https://wiki.openstreetmap.org/wiki/Tag:railway=switch?uselang=en-GB):
>a railway switch (or ... railway _point_) is a _point_ where trains can change from one track to another track

- queried OpenStreetMap with `osmnx` with the tag `railway=switch` to get the _points_, and `railway=rail` to get the rails.
- little bit of filtering to remove some tracks (there were *too many*), and the _points_ on those tracks
- plotted the _points_ on top of the their respective tracks.
- made sure to use SBB's [fonts](https://brand.sbb.ch/d/k7TF5BpX3B3F/markenelemente#/markenelemente/typographie-1) and [colours](https://brand.sbb.ch/d/k7TF5BpX3B3F/markenelemente#/markenelemente/farben-1).

## 2 - Lines
>30DayMapChallenge classic: A map with focus on lines. Roads, rivers, routes, or borders—this day is all about mapping connections and divisions. Another traditional way to keep things moving. 📏

![croissant distribution](day2/day2_lines.png)

- croissant distribution 🥐
    - or the probability of me eating 10 croissants next week, if on average i eat three croissants a week, and today's croissant is independent of the previous croissant.

- queried OpenStreetMap using `osmnx` and a polygon of france grabbed from Natural Earth
- tag for bakeries: `shop:bakery` and for farms: `landuse:farmland`
- took centroid of each feature (regardless of weather it was node/way/relation)
- and plotted these using seaborn's `jointplot()` with `kind=kde`
- each density, both on main axes and marginal axes is to a separate scale (`common_norm:False, common_grid:False`)
- font used: [Borel](https://github.com/RosaWagner/Borel)

$$ \frac{\lambda ^{k}e^{-\lambda }}{k!}$$


## 3 - Polygons
>30DayMapChallenge classic: A map with polygons. Regions, countries, lakes—this day is for defined shapes that fill space. 🛑

![day 3 - polygons](day3/day3.png)

regional capitals of italy
- taken from OpenStreetMap using `osmnx`.
- required slightly fiddly filtering, and as usual requires having OpenStreetMap, and the tag wiki open to work out what `admin_level` you want etc...
- buffered 300 m around each regional capital representative node, and grabbed:
    - all the buildings, `parks` and `gardens` (from `leisure`) and `square` from `place` (also used `highway`=`pedestrian` polygons for squares/piazza).
- plotted them with the _tricolore_.
- font used: [Scoglietto](https://www.fontspace.com/scoglietto-font-f1487)



## 4 - Hexagons
>Maps using hexagonal grids. Step away from square grids and try mapping with hexagons. A fun way to show density or spatial patterns. 🔷

![day4](day4/day4.png)

springs and pubs of Hungary.
- `osmnx` for getting country outline; springs (`natural:spring`); and pubs (`amenity:[pub, bar]`) from OpenStreetMap
- `h3` for making the hexagons
- spatial join to count number of occurrences of springs/pubs in each hexagon
- `pd.qcut()` for grouping counts into discrete number of bins
- and multiplying `rgb` values from `Oranges` and `Blues` to make the bivariate choropleth.

- heavily leaning on what i did [last year](../2023/day13_choropleth/day13.ipynb).

## 5 - A journey
>Map any journey. Personal or not. Trace a journey—this could be a daily commute, a long-distance trip, or something from history. The key is to map movement from one place to another. 🚶\u200d♂️✈️

![baltic states by bicycle](day5/day5.png)

- **manually** tidied up a `.kmz` file i made _years_ ago of my route (that i digitized from the paper map i was drawing on at the time)
- `python` for:
    - getting country outlines from Natural Earth; cities, rivers and lakes from OpenStreetMap via `osmnx`; hillshade from Copernicus Global DEM (90 m)
    - making the elevation profile along the lower edge made by sampling the DEM along the route in python (with quite a bit of trial and error to find an acceptable compromise between detail and clarity re: sampling frequency along route)
- qgis for everything else.
    - i don't often use QGIS (preferring to do things programmatically)
    - it is _very_ capable.
    - making this i got more comfortable with the expression builder, and label placements. although i still don't quite understand why  manually moving labels _isn't_ done in the layout view.
    - also learnt a bit more about `.svg`. and icons.
- i apologise for the perhaps overly gratuitous use of drop shadows.

## 6 - Raster
>A map using raster data. Rasters are everywhere, but today’s focus is purely on grids and pixels—satellite imagery, heatmaps, or any continuous surface data. 🟦🟧

- relative elevation model...

## 7 - Vintage style
>Map something modern in a vintage aesthetic. Create a map that captures the look and feel of historical cartography but focuses on a contemporary topic. Use muted colors, fonts, and classic elements. 🕰️🗺️

- somewhere with coastline, and canals and bathymetry


## 8 - Humanitarian Data Exchange (HDX)
>Use data from HDX to map humanitarian topics. Explore the datasets from the Humanitarian Data Exchange, covering disaster response, health, population, and development. Map for social good. 🌍🚑
 
## 9 - AI only
>This day is all about prompt engineering. Use AI tools like DALL-E, MidJourney, Stable Diffusion, or ChatGPT with geospatial capabilities to create a map based on AI-generated content. The challenge is to get the right prompt and critically assess the output—how well does AI capture or distort the map's intent?",

## 10 - Pen & paper
>Draw a map by hand. Go analog and draw a map using pen and paper. The result doesn’t have to be perfect—it’s about the creative process. ✏️🗺️

## 11 - Arctic
>Map the Arctic. Whether it’s ice coverage, wildlife habitats, or the effects of climate change, this day is all about mapping the cold extremes of the Arctic. ❄️🧊

- something from my thesis / paper
- dh/dt

## 12 - Time and space
>Map something where time matters. Visualize change over time—urban growth, migration, or environmental shifts. Show the relationship between time and geography. ⏳🌍

- terminus retreat

## 13 - A new tool
>Use a tool you’ve never tried before. The challenge has always been about trying new things. Use a tool, software, or drawing technique you’ve never worked with before. 🧪🔧

- overpass turbo
- lonboard
- blender
- grass!

## 14 - A world map
>Map the whole world. Whether it’s continents, ecosystems, or oceans, this is the day to map the entire planet. 🌍

- geology / crust age.
- when did it last rain...


## 15 - My data
>Map something personal. Map data from your own life—this could be places you’ve travelled, your daily routine, or any other personal touch. 🗒️

- my network

## 16 - Choropleth
>Classic choropleth map. Use color to show data variation across regions. This simple but effective technique is a staple for showing thematic differences. 🎨

## 17 - Collaborative map
>Collaborate with others on a single map. For today’s challenge, team up! Whether you work with one person or several, the idea is to combine your efforts on a single map. 🤝🗺️

## 18 - 3D
>Map with depth. Add a third dimension to your map. Whether it’s visualizing elevation, buildings, or something more abstract, today’s about thinking beyond flat surfaces. 🎢🏔️

## 19 - Typography
>Map focused on typography. Let text and words do the heavy lifting today. Whether you’re focusing on place names, labeling, or using text to create shapes and patterns. ✍️🅰️

## 20 - OpenStreetMap
>Use OpenStreetMap data to create something. OpenStreetMap offers rich, editable data from roads to buildings and beyond. The goal is to showcase the power of this community-driven dataset. 🗺️📍

## 21 - Conflict
>Map a conflict. Political, territorial, or social—there are conflicts all around us. Map boundaries, tension points, or the outcomes of conflicts. ⚔️🛑

- hadrians wall.
- edge of logging / deforestation

## 22 - 2 colours
>Create a map using only 2 colors. No gradients or shading—just two flat colors. This restriction encourages creativity in design and forces you to think about how to clearly convey your message with minimal color.

## 23 - Memory
>Map based on memory. Create a map of a place you remember—hometown, favorite destination, or somewhere meaningful. It doesn’t need to be perfectly accurate, just how you recall it. 💭🗺️

- house i grew up in

## 24 - Only circular shapes
>Map using only circles. Everything should be circular. Forget straight lines and sharp edges, and see how creative you can get by sticking to round shapes. 🔵⭕

![encircled iceland incircles](day24/Ísland_circles_wCapital.png)

- find successive largest inscribed circles
- pretty slow to find *lots*.


## 25 - Heat
>Map something related to heat. Focus on heat, whether it’s actual temperature or areas of intensity—like heatmaps of activity or metaphorical heat. 🔥


## 26 - Map projections
>Explore different map projections and how they distort the world. Whether it's focusing on the classic Mercator, the Peters projection, or a more obscure one like the Waterman Butterfly, today is about playing with how we represent the round Earth on flat surfaces.

- can i make my own?
- or use one from that book what that i have

## 27 - Micromapping
>Map something small and precise. Zoom in and map a small area in high detail. It could be a single building, a street corner, or a tiny plot of land. Focus on accuracy at a small scale. 🧐🔍

- my desk... but at a scale that is larger than 1:1.

## 28 - The blue planet
>Map oceans, rivers, and lakes. Focus on water today. Map the oceans, rivers, or lakes, diving deep into marine environments or water systems. 🌊🐋

## 29 - Overture
>Use data from the Overture Maps Foundation. Explore data from Overture Maps Foundation to create a map that highlights new geographic datasets. A great opportunity to dive into open geospatial data! 🌍📊

- this tutorial https://docs.overturemaps.org/examples/lonboard/

## 30 - The final map
>The final challenge—your choice! Revisit a technique from earlier in the month, refine an idea, or try something completely new. End the challenge on a high note with a map that showcases your creativity, growth, or just pure fun! 🎉🌐