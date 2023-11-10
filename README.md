# #30DayMapChallenge 2023

[link to site](https://30daymapchallenge.com/)

![This year's themes](30dmc-2023.png)

## day 1 - points
Triangulation pillars of the Great Britain coloured by elevation

<img src="day1_points/day1.png" width=300>

- data from Ordnance Survey

## day 2 - lines
Geological fault lines and railways of Scotland

<img src="day2_lines/day2.png" width=300>

- data from OSM and BGS

## day 3 - polygons
Finnish lakes

<img src="day3_polygons/day3.png" width=300>

- data from Finnish Environment Institute (Syke) and Natural Earth

## day 4 - a bad map
Best restaurants in Tokyo
- endeavoured to include many incongruities

<img src="day4_badmap/day4.png" width=300>

- data from OSM and Natural Earth

## day 5 - analog
Route Sheet

<img src="day5_analog/day5.png" width=300>

- route sheet courtesy of Audax Club Hackney

## day 6 - asia
The Pole of Inaccessibility

<img src="day6_asia/day6.png" width=300>

- the point most distant from the coast
- Garcia-Castellanos & Lombardo (2007) identified two points: 44.29°N 82.19°E (2,510±10 km) and 45.28°N 88.14°E (2,514±7 km)
- Instead of simply using their points, I endeavoured to find them / see how close I could get myself...
- used a clumsy, inefficient and basic search routine, involving generating lots of buffers in different Azimuthal Equidistant Projections.
- I learnt a lot...and my code gets to within 100 km of the recognised values.
- Coastline/country data from Natural Earth

## day 7 - navigation
Polar Wander

<img src ="day7_navigation/day7.png" width=300>

- data from Natural Earth and [National Centers for Environmental Information (NOAA)](https://www.ncei.noaa.gov/products/wandering-geomagnetic-poles)
- data presented is from the International Geomagnetic Reference Field ([IGRF](https://geomag.bgs.ac.uk/research/modelling/IGRF.html))
- projections: North/South Polar Stereographic.

## day 8 - africa
Mount Kiliman-SAR-o

<img src ="day8_africa/day8.png" width=300>

- Following [this](https://planetarycomputer.microsoft.com/dataset/sentinel-1-grd#Example-Notebook) notebook in Microsoft Planetary Computer
- Data from Copernicus Sentinel 1B
- False colour composite (VV,VH,VV/VH)

## day 9 - hexagons
Hexagons tile the (great) plain(s)

<img src ="day9_hexagons/day9.png" width=300>

- hexagons generated using h3-py
- hexagons shaded by elevation
    - using elevation data from ASTER (NASA/METI) and the [open topo api](https://api.opentopodata.org/v1/aster30m)
- outline of the *Great Plains* from [here](https://cartographyvectors.com/map/1288-us-great-plains)
- coastline/country data from Natural Earth

## day 10 - north america
Impact Craters in North America

<img src = "day10_northamerica/day10.png" width=300>

- parsing html in `pandas` is easy
- formatting columns that contain lots of different characters around the numbers is fiddly
- also fiddly: sorting out the legend. three cheers for [this](https://stackoverflow.com/a/73354795) stack overflow answer
- data from the [Earth Impact Databse](http://www.passc.net/EarthImpactDatabase/New%20website_05-2018/NorthAmerica.html) and Natural Earth

## day 11 - retro
Hardangerjøkulen

<img src = "day11_retro/day11_retro.png" width=300>

- Hardangerjøkulen is an ice cap in Norway. This map features the north eastern portion of the ice cap (stippled) along with a few of the ice marginal lakes (diagonal hatched). The lake NE of the summit marked Ramnabergnuten is Ramnabergvatnet.


- elevation data taken from Copernicus Global Digital Elevation Model (ESA 2021) and accessed via [Planetary Computer](https://planetarycomputer.microsoft.com/dataset/cop-dem-glo-30)
    - contours generated using matplotlib
- mountain peaks, glacier and lake outlines grabbed from Open Street Map using #osmnx
- to fulfill the **retro** criteria:
    - axes background set to sepia
    - figure exported as `.png`
    - exported figure read back in as array
    - applied gaussian blur (`scipy.ndimage`) added some gaussian noise (`np.random.normal`) and then rotated it by 1 degree (`scipy.ndimage.rotate`) to give it that photocopied badly look.
- this was very much inspired by figures in Journal of Glaciology, e.g. [this](day11_retro/thorarinsson_1953.png) by [Sigurudur Thorarinsson](10.3189/S0022143000025454) and [this](day11_retro/sugden_1985.png) by [David Sugden et al.,](doi:10.3189/S0022143000006729)

