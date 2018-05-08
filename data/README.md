## Philly

Download GIS and data from NHGIS
Census tracts
Median household Income ACS 5 year
Total Population 2010 Census

Before join extracted state with:
ogr2ogr -f "ESRI Shapefile" -where "STATEFP10 = '42'" PA.shp US_tract_2010.shp

Joined in Qgis
copied fields from string to numeric and renamed
simplified geometry from over 30k nodes to about 2.8k nodes


## philly_homicides.csv
From 
http://www.opendataphilly.org/opendata/resource/215/philadelphia-police-part-one-crime-incidents/

This dataset was up to date as of Saturday 02/07/15 at 08:15 AM EST

Exctracted Homicides only (~ 3k points) from csv (~750k points)
Removed rows without lat/lon
Removed a few colums that were not needed
Added field OBJ_ID with value 1.

## PhiladelphiaEduAttain.csv

ACS 5 year estimates on educational attainment

`library(tidycensus)`
`library(dplyr)`
`library(tidyr)`

`v15 <- load_variables(2016, "acs5", cache = TRUE)`

`edu_vars <- c("......")`

`get_acs(geography = "tract", `
        `variables = edu_vars,` 
        `state = "PA", county = "Philadelphia County") %>%`
  `select(-moe) %>%  # we'll just take the estimates here for demo`
  `spread(variable, estimate) %>%` 
  `write.csv("data/PhiladelphiaEduAttain.csv", row.names=F)`

## HARV_RGB_Ortho.tif

Imagery collected using the [NEON Airborne Observation Platform](http://www.neonscience.org/science-design/collection-methods/airborne-remote-sensing) high resolution camera over the [NEON Harvard Forest field site](http://www.neonscience.org/science-design/field-sites/harvard-forest). Each RGB image is a 3-band raster.

Source: datacarpentry.org.




