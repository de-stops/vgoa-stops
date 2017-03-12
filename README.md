# vgoa-stops

This is a simple script to download [VGOA](http://www.oberallgaeu.org/wirtschaft_verkehr/nahverkehr_schuelerbefoerderung/nahverkehr_schuelerbefoerderung/) stops as [GTFS-compatible CSV](https://developers.google.com/transit/gtfs/reference/stops-file).

The script uses the following endpoint:

```
http://www.bayern-fahrplan.de/XML_COORD_REQUEST?&jsonp=&boundingBox=&boundingBoxLU={minx}%3A{miny}%3AWGS84%5BDD.DDDDD%5D&boundingBoxRL={maxx}%3A{maxy}%3AWGS84%5BDD.DDDDD%5D&coordOutputFormat=WGS84%5BGGZHTXX%5D&type_1=STOP&outputFormat=json&inclFilter=1
```

It starts from bounding box `(9.9, 47.2, 10.6, 48)` and works down to smaller quadrants.

The script produces CSV output in the following format:

```
"stop_id","stop_name","stop_lon","stop_lat","stop_code"
"2509357","Werdenstein, Ort",10.2470891702,47.604513971,"de:9780:9357"
```

# Prerequisites

These scrips use PostGIS to filter stops belonging to administrative regions covered by the transport company.  
See [this project](https://github.com/highsource/postgis-verwaltungsgebiete) for a simple way to create a PostGIS database with administrative regions.

# Usage

## Windows

```
npm install
00-export-unfiltered-stops
01-filter-stops
```

# Disclaimer

Usage of this script may or may not be legal, use on your own risk.  
This repository provides only source code, no data.

# License

Source code is licensed under [BSD 2-clause license](LICENSE). No license and no guarantees implied on the produced data, produce and use on your own risk.