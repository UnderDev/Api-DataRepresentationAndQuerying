# Data-Representation-and-Querying

### Scott Coyne - G00316578

## Introduction
This project provides the design and documentation for the dataset "Playgrounds County Galway" which is available at [https://data.gov.ie](https://data.gov.ie/data)

The above dataset will be used to provied information about the local playgrounds located in the County Galway area. Which could be implemented into an app or website to provied the Location, Closing times, Amenities, Pictures of the playgound etc. Given this information, users would be able to find playgrounds in their area to the specification they desire, without having to leave the house.
This Api could also be implemented accross serveral other counties, with a similar dataset.

## About the data Provided

This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [*data.gov.ie/dataset*](https://data.gov.ie/dataset/playgrounds-county-galway/resource/019cf36c-7da9-4d0b-9bcd-7ac647a1b1c7).
The CSV file contains 63 rows, the first being a header row with the names of each field.

There are sixteen values on each line, which are as follows:

| Name      | Description |
| :-------------|:------------|
| X     | The X Gps position on the map|
| Y     | The Y Gps position on the map|
| Fid |  The identifier number|
| ID | The identifier number|
| Location_o | The Location of the playground, Eg: Bearna, Salthill, Knocknacarra|
| Area_ | The Area of the playground, Eg: West Galway - Conamara, North Galway - Tuam|
| Managed_By | Who The playground is managed by Eg: Galway County Council, Ballinasloe Town Council|
| Playground | The Playground name Eg: Monivea, Castle Park, Portumna|
| AGE_GROUP | The recomended age group for the park Eg: 2 to 10 years, All
| List_of_Eq | A list of equipment availible at the park Eg: Spring Rocker,  Slide, Basket Swing
| Liosta_Tre | A list of equipment availible at the park in Irish (As Gaeilge)
| List_of_00 | A list of other equipment availible in the park Eg: Toddler Swing, Basket Swing
| PUBLIC_TOI | If ther is public toilets available in the park Eg: Yes/No/9-6
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PARKING | If parking is available, Eg: Yes/No
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/2.jpg


## Design Ideas For An Api URL

### Playgrounds In My Area

You could get a list of Playgrounds near you or in a specific area, based on the location (Location_o) using a GET method at he following URL:
*http://playgrounds.ie/location/[Location_o]*

From the url above, [Location_o] is where the user could enter in the location of where they want to be abe to find a playground, Eg Gort. The user would then be provieded with a list of playgrounds with relevent data, in or close to that area. The data will be returned in JSON format, with the following properties for each Playground:

| Name      | Description |
| :-------------|:------------|
| Location_o | The Location of the playground, Eg: Bearna, Salthill, Knocknacarra|
| Playground | The Playground name Eg: Monivea, Castle Park, Portumna|
| AGE_GROUP | The recomended age group for the park Eg: 2 to 10 years, All
| List_of_Eq | A list of equipment availible at the park Eg: Spring Rocker,  Slide, Basket Swing
| Liosta_Tre | A list of equipment availible at the park in Irish (As Gaeilge)
| PUBLIC_TOI | If ther is public toilets available in the park Eg: Yes/No/9-6
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PARKING | If parking is available, Eg: Yes/No
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/2.jpg


An example of a response would be:
```json
{
    "Location_o":"Roundstone (Cloch na Ron)",
    "Playground":"Roundstone Village, Connemara",
    "AGE_GROUP":"0 to 16 Years",
    "List_of_Eq":"Climber and Slide, Climber with Rope, Flat Swings, Cradle Swings, Crazy Goose, Springer",
    "Liosta_Tre":"Dreapadóir le Sleamhnán, Luascán Cothrom,  Luascán Cliabháin , Lingeadan, Maide Corrach",
    "PUBLIC_TOI":"No",
    "OPENING_HO":"Daylight Hours",
    "PARKING":"YES",
  }
```

