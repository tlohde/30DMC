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
