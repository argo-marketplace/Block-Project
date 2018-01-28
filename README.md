# Block-Project
[Block Project website](http://www.the-block-project.com/home/)
![](https://github.com/argo-marketplace/Block-Project/blob/master/block-seattle.png)

## What is this?
This is a spatial analysis of Seattle Parcel Data for the Block Project. 

## Why is this needed?
Based on preliminary analysis of King County Parcel Data, the city of Seattle has 120,000 residential parcels with a lot size of >4,000 sqft (the minimum area required to participate in Block Project)

This analysis is aimed towards building a list of residential clusters in Seattle that exhibit amenable characteristics to participating in the Block Project.
		
## How is this being done?
 1. We retrieved King County Parcel Data from the [King County Parcel Viewer](gismaps.kingcounty.gov/parcelviewer2/)
 2. We used [American Fact Finder](https://factfinder.census.gov/faces/nav/jsf/pages/searchresults.xhtml?refresh=t) to retrieve King County Census Tracts as well as Demographic data.
 3. We isolate the following Census variables from the American Community Survey (2011-2016) 5-year estimates.
    - Age
    - Median Household Income
    - Educational Attainment
    - % Own vs Rent
    - Tenure
4. A score is calculated based on these variables. The Census Tracts with the highest scores exhibit those areas in Seattle where the Block Project can focus their outreach efforts and build critical mass.

## What's next?
Upon refining the spatial analysis,  we plan to use [lob.com](http://www.lob.com) to programmatically send mailers to households in areas that exhibit strong characteristics towards participating in the Block Project.
