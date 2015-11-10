# Data-Representation-and-Querying

### Scott Coyne - G00316578

## Introduction
This project provides the design and documentation for the dataset "Playgrounds County Galway" which is Available at [https://data.gov.ie](https://data.gov.ie/dataset/playgrounds-county-galway/resource/019cf36c-7da9-4d0b-9bcd-7ac647a1b1c7)

The above dataset will be used to provide information about local playgrounds located in the County Galway area. Which could be implemented into an App or Website to provide the Location, Closing times, Amenities, Pictures of the playground etc. 

Given this information, this API would be able to show Real Time information about each playground. And would provide Parents/children and playground enthusiasts concrete information and pictures of the playgrounds, without having to drive to leave the house.

This API could also be implemented across several other counties, with a similar dataset.


## About The Data Provided

This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [*data.gov.ie/dataset*](https://data.gov.ie/dataset/playgrounds-county-galway/resource/019cf36c-7da9-4d0b-9bcd-7ac647a1b1c7)
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
| AGE_GROUP | The recommended age group for the park Eg: 2 to 10 years, All
| List_of_Eq | A list of equipment available at the park Eg: Spring Rocker,  Slide, Basket Swing
| Liosta_Tre | A list of equipment available at the park in Irish (As Gaeilge)
| List_of_00 | A list of other equipment available in the park Eg: Toddler Swing, Basket Swing
| PUBLIC_TOI | If there is public toilets available in the park Eg: Yes/No/9-6
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PARKING | If parking is available, Eg: Yes/No
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/2.jpg


## Design Ideas For An API'S URL

#### Playgrounds In My Area

You can get a list of Playgrounds near you or in a specific area, based on the location (Location_o) using a GET method at the following URL:
*http://playgrounds.ie/location/[Location_o]*

From the URL above, [Location_o] is where the user could enter in the location of where they want to be able to find a playground, Eg: Roundstone. The user would then be provided with a list of playgrounds with relevant data, in or close to that area. 

The data will be returned in JSON format, with the following properties for each Playground:

| Name      | Description |
| :-------------|:------------|
| Location_o | The Location of the playground, Eg: Bearna, Salthill, Knocknacarra|
| Playground | The Playground name Eg: Monivea, Castle Park, Portumna|
| AGE_GROUP | The recommended age group for the park Eg: 2 to 10 years, All
| List_of_Eq | A list of equipment available at the park Eg: Spring Rocker,  Slide, Basket Swing
| Liosta_Tre | A list of equipment available at the park in Irish (As Gaeilge)
| PUBLIC_TOI | If there is public toilets available in the park Eg: Yes/No/9-6
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PARKING | If parking is available, Eg: Yes/No
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/1.jpg


An example of a response from the URL: *http://playgrounds.ie/location/Roundstone* would be:
```json
{
    "Location_o": "Roundstone (Cloch na Ron)",
    "Playground": "Roundstone Village, Connemara",
    "AGE_GROUP": "0 to 16 Years",
    "List_of_Eq": "[Climber and Slide, Climber with Rope, Flat Swings, Cradle Swings, Crazy Goose, Springer]",
    "Liosta_Tre": "[Dreapadóir le Sleamhnán, Luascán Cothrom,  Luascán Cliabháin , Lingeadan, Maide Corrach]",
    "PUBLIC_TOI": "No",
    "OPENING_HO": "Daylight Hours",
    "PARKING": "YES",
    "PHOTO": "http://www.galway.ie/gis/playgrounds/1.jpg"
}
```



#### Playgrounds By Age Group

You can get a list of Playgrounds based on the recommended age group (AGE_GROUP) using a GET method at the following URL:
*http://playgrounds.ie/age/[AGE_GROUP]*


From the URL above, [AGE_GROUP] is where the user could enter in the age group for playgrounds that they are looking for Eg: 7. The user would then be provided with a list of playgrounds based on that age with relevant data. 

The data will be returned in JSON format, with the following properties for each Playground:

| Name      | Description |
| :-------------|:------------|
| AGE_GROUP | The recommended age group for the park Eg: 2 to 10 years, All
| Location_o | The Location of the playground, Eg: Bearna, Salthill, Knocknacarra|
| Playground | The Playground name Eg: Monivea, Castle Park, Portumna|
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/2.jpg


An example of a response from the URL: *http://playgrounds.ie/age/all* would be:
```json
{
    "AGE_GROUP": "ALL",
    "Location_o": "An Cloigeann",
    "Playground": "Cleggan",
    "OPENING_HO": "Available when Community  Centre is in use",
    "PHOTO": "http://www.galway.ie/gis/playgrounds/2.jpg"
}
```



#### Playgrounds With Specific Equipment

You can get a list of Playgrounds based on the Equipment the playground has (List_of_Eq) using a GET method at the following URL:*http://playgrounds.ie/equipment/[List_of_Eq]*

From the URL above, [List_of_Eq] is where the user could enter in the type of equipment they want the playground to contain Eg: swings, slide. The user would then be provided  with a list of playgrounds that have the equipment there looking for.

The data will be returned in JSON format, with the following properties for each Playground:

| Name      | Description |
| :-------------|:------------|
| List_of_Eq | A list of equipment available at the park Eg: Spring Rocker,  Slide, Basket Swing
| Liosta_Tre | A list of equipment available at the park in Irish (As Gaeilge)
| List_of_00 | A list of other equipment available in the park Eg: Toddler Swing, Basket Swing
| Location_o | The Location of the playground, Eg: Bearna, Salthill, Knocknacarra|
| Playground | The Playground name Eg: Monivea, Castle Park, Portumna|
| AGE_GROUP | The recommended age group for the park Eg: 2 to 10 years, All
| OPENING_HO | Opening hours to the park if applicable, Eg: Daylight Hours, Summer Hours
| PHOTO | Provides a link to a photograph of the park Eg: http://www.galway.ie/gis/playgrounds/8.jpg


An example of a response from the URL: *http://playgrounds.ie/equipment/slide* would be:

1.
```json
{
    "List_of_Eq": "['Roundabout', 'Rocker', 'Swing', 'SwingwithCradleSeat', 'SeeSawandSlide']",
    "Liosta_Tre": "['Timpeallán', 'Luascaire', 'Luascáin', 'MaideCorrach' , 'Sleamhnán']",
    "List_of_00": "None  Specified",
    "Location_o": "Ballinasloe (St. Michaels Place)",
    "Playground": "St. Michaels Place, Ballinasloe",
    "AGE_GROUP": "1-12 Years",
    "OPENING_HO": "DayLight Hours",
    "PHOTO": "http://www.galway.ie/gis/playgrounds/8.jpg"
}
```
2.
```json
{
    "List_of_Eq": "['Cable Runway', 'Basket Swing', 'Cradle Swings',  'Toddlers Multiplay and Slide']",
    "Liosta_Tre": "['Rúidchosán Cábla', 'Ciseán Luascadh', 'Luascáin', 'Aonad Ilspraoi Lapadáin le Sleamhnán']",
    "List_of_00": "Basket Nest Swing &  Cradle Swing",
    "Location_o": "Moylough (Maigh Locha)",
    "Playground": "Ballinasloe",
    "AGE_GROUP": "0-12 Years",
    "OPENING_HO": "DayLight Hours",
    "PHOTO": "http://www.galway.ie/gis/playgrounds/13.jpg"
}
```



