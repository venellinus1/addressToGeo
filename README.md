# addressToGeo
Convert csv/xls file containing addresses to Geozones (lat/lon), eg
101681 Billau GbR;101681;Billau GbR;Romerstr. 58 - 62;D;68623;Lampertheim - converted to  49.59282, 8.46978

Convertion of list containing multiple(xxxx's) addresses into geo coordinates appeared a bit challenging if the goal is to avoid any errors during this automatic conversion. The goal was achieved by using 3 different providers for converting addresses:
-wialon: string urlGetAUs = "http://search-maps.wialon.com/hst-api.wialon.com/gis_searchintelli?phrase=" + values[2]+","+values[3] + "&count=20&uid=" + uid + "&sid=" + sid;
-google: "http://maps.googleapis.com/maps/api/geocode/xml?address=" + txtAddress.Text + "&sensor=true"; 
-openstreetmap http://nominatim.openstreetmap.org/search.php?q=" + searchstr + "&polygon_geojson=1&viewbox="
Combining the results from the 3 searches, if 2 of them provide lat/lon coordinates which are within configurable distance (eg 100m or 200m or ..) then the median result from these 2 is taken as final result

