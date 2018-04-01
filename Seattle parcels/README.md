[Carto map showing neighborhood view](http://bit.ly/block-project-carto) 
[Tableau map showing block view](http://bit.ly/block-project-tableau) 


----------


1. [Retrieve King County Parcel Data](ftp://ftp.kingcounty.gov/gis-web/GISData/property_SHP.zip)
2. Retrieve Seattle alleys from Open Street Map using [Overpass API](http://overpass-turbo.eu/) 
```
[out:json][timeout:45];
(
  way["service"="alley"]({{bbox}});
);
out body;
>;
out skel qt;
```
3. Export Alley data as GEOJSON
4. Upload Parcel and Alley data to Carto.
5. Filter parcel data to include only parcels > 4,000 sqft and zoned as *R**
6. Draw buffer around Alleys
7. Intersect Alley buffers and Parcels (carto)
```sql
WITH alley_buffers AS (
  SELECT cartodb_id,
         ST_Transform(
           ST_Buffer(the_geom::geography,     30)::geometry
           ,3857
         ) AS the_geom_webmercator
FROM export_overpass
  )

SELECT a.*
FROM seattle_parcels a
inner join
alley_buffers b ON
ST_INTERSECTS(a.the_geom_webmercator, b.the_geom_webmercator)
where lotsqft >4000 and sitetype like '%R%'
```
8. Download resulting data.
