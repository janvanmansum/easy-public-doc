Geographic coordinates in EASY
==============================

In EASY, dataset metadata can contain information about the location on Earth that the dataset is about. This can
for example be use to indicate the location of an excavation site that is described in an archaeological report.


Coordinate systems and EPSG
---------------------------
The Earth has a [spherical shape](https://en.wikipedia.org/wiki/Figure_of_the_Earth) and two coordinates are used 
to specify a location on its surface: one along the equator with the West-East direction called the longitude 
or referred to as X and one perpendicular along the line from the poles South-North called latitude or referred 
to as Y. When just given two numbers we need to know the units of measure; meters or degrees for example and 
also the order; X, Y or Y, X. Without specifying this the coordinates (numbers) cannot be used in a mainingfull way. 
\There is actually much more to this, like modeling the precise shape of the Earth (flattened sphere) and things 
like continental drifts, but we won't go into those details. 

A widely used standard to specify how the coordinates should be interpreted is the EPSG code for the 
'coordinate reference system' or CRS. On the website [http://www.epsg-registry.org](http://www.epsg-registry.org) 
you can search for specific codes or names and find the information you need. 

In EASY two systems are used: 

- the WGS84 system for global locations, and 
- RD ('Rijksdriehoeks') for locations in The Netherlands. 

### WGS84 - EPSG 4326
A global system, much used for navigation (GPS and maps). 

More detailed information can be found on the [WGS Wikipedia page](https://en.wikipedia.org/wiki/World_Geodetic_System)
and [epsg.io](https://epsg.io/4326).

**EPSG Coordinate System information**: "Axes: latitude, longitude. Orientations: north, east. UoM: degree"

Note: latitude, longitude = (Y,X) in EASY metadata (EMD)

### RD - EPSG 28992

A Dutch national system, used by the government and other official organisations. 

More detailed information can be found on the [RD Wikipedia page](https://nl.wikipedia.org/wiki/Rijksdriehoekscoördinaten)
and [epsg.io](https://epsg.io/28992).

**EPSG Coordinate System information**: "Axes: easting, northing (X,Y). Orientations: east, north. UoM: m."

Deposit forms on the EASY website
---------------------------------
Coordinate 'schemes' that can be selected are:  

- `RD` - (Rijksdriehoek)
- `degrees` - (WGS84)
- `local` - is only used on some rare occasions where we have other types of coordinates.

The web interface (form input fields) accept any textual representation, but our archivists will correct it if needed.

* **WGS84**: In EASY we prefer the decimal representation and NOT the degrees minutes seconds 
(DMS, example 52°09'22.178"N 5°23'15.5"E)

* **RD**: Also a decimal representation, without any separators for thousands. 

RD coordinates are converted 'on the fly' to WGS84 when showing markers on the map and for some AOI-PMH output formats

### EMD

Coordinates are stored in EMD (EASY MetaData):
Examples:

       <eas:spatial>
             <eas:point eas:scheme="RD">
                 <eas:x>108756</eas:x>
                 <eas:y>446481</eas:y>
             </eas:point>
       </eas:spatial>

or
       
       <eas:spatial>
            <eas:point eas:scheme="degrees">
                <eas:x>51.788160</eas:x>
                <eas:y>5.898827</eas:y>
            </eas:point>
       </eas:spatial>


### OAI-PMH

OAI-PMH output example:

from [https://easy.dans.knaw.nl/oai/?verb=ListRecords&metadataPrefix=oai_dc](https://easy.dans.knaw.nl/oai/?verb=ListRecords&metadataPrefix=oai_dc)
 
    <dc:coverage>east=178100; north=424425; units=m; projection=Dutch National Grid;</dc:coverage>
    <dc:coverage>φλ=51.80797731 5.72215365; projection=http://www.opengis.net/def/crs/EPSG/0/4326; units=decimal; source=RD 178100 424425;</dc:coverage>

Note that 'φλ' is also used here to make clear that the order is latitude,longitude.

SWORD deposits
--------------
With SWORD the metadata must be provided in DDM (XML) and the coordinates are in [GML](https://en.wikipedia.org/wiki/Geography_Markup_Language). 
We only interpret Point and Envelope (for box region). Coordinate systems recognised are RD and WGS84, 
which must be specified by the snsName attribute. 

**srsName for WGS84**:

URL "http://www.opengis.net/def/crs/EPSG/0/4326" or 
URN "urn:ogc:def:crs:EPSG::4326"
    
**srsName for RD**:
URL "http://www.opengis.net/def/crs/EPSG/0/28992" or URN "urn:ogc:def:crs:EPSG::28992"
    
    
DDM example:

    <dcx-gml:spatial srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
      <Point xmlns="http://www.opengis.net/gml">
        <pos>52.2 5.4</pos>
      </Point>
    </dcx-gml:spatial>
    <dcx-gml:spatial>
      <boundedBy xmlns="http://www.opengis.net/gml">
        <Envelope srsName="http://www.opengis.net/def/crs/EPSG/0/28992">
          <lowerCorner>463100 155100</lowerCorner>
          <upperCorner>462900 154900</upperCorner>
        </Envelope>
      </boundedBy>
    </dcx-gml:spatial>
    
See the page *["Depositing in EASY with SWORD 2.0"]* for technical details for SWORD2.0 and *["SWORD Auto-Ingest Manual"]* 
for SWORD1.3.

["SWORD Auto-Ingest Manual"]: ./pdf/SWORD%20Auto-Ingest%20Manual.pdf
["Depositing in EASY with SWORD 2.0"]: ./sword2.html