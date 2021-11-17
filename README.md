# Work with dataset "Aerial Bombing Operations in World War II" #

## Introdution ##

To create a visualization in the Tableau about air warfare in 1942 year on South-East Pacific, and to answer few question:

- how important the participation of the RAAF was in 1942 year for Allied
- where was main air strike aera for USAAF and RAAF
- which aircrafts was "workshorse" in Allied air force

I decided to use the "Aerial Bombing Operations in World War II" [link](https://www.kaggle.com/usaf/world-war-ii) dataset from Kaggle called "operations.csv". 
It has an open CC0: Public Domain license and consists of digitized paper mission reports from WWII. It does not contain information about other types of missions, such as combat, reconnaissance, transport, etc.

## Dataset description ##
 
Dataset has 46 columns (14 string, 12 integer, 8 Uuid,12 other) and 178742 rows.

Here is columns list:

1.	Mission ID – Unique ID for every mission
2.	Mission Date – Air ride date
3.	Theater of Operations – Sub-area within a theater of war
4.	Country –Air force’s country of origin 
5.	Air Force – part of air force
6.	Unit ID – Identification code of the unit involved in the attack
7.	Aircraft Series – Model of aircraft
8.	Callsign – Empty column
9.	Mission Type – Numeric value describing mission type
10.	Takeoff Base – Base from which aircrafts launched
11.	Takeoff Location – Geographical area of the Takeoff Base
12.	Takeoff Latitude – Base latitude
13.	Takeoff Longitude – Base longitude
14.	Target ID – Unique ID for each target
15.	Target Country –  Geographic area of the Target
16.	Target City – Description of attack place 
17.	Target Type – Type of target
18.	Target Industry – Description of the target
19.	Target Priority – Description of the  target’s priority (numerical alphabetic values)
20.	Target Latitude - Target coordinate
21.	Target Longitude - Target coordinate
22.	Altitude (Hundreds of Feet) – Height from which the attack was carried out
23.	Airborne Aircraft	- Number of aircrafts launched 
24.	Attacking Aircraft – Number of aircrafts attacking the Target
25.	Bombing Aircraft	 - Number of aircrafts which dropped bombs
26.	Aircraft Returned – Number of aircrafts returned to the base
27.	Aircraft Failed – Number of aircrafts which failed the mission
28.	Aircraft Damaged – Number of  damaged aircrafts
29.	Aircraft Lost – Number of aircrafts lost
30.	High Explosives – Description of the different type of blasting explosives used
31.	High Explosives Type – Number of blasting explosives used
32.	High Explosives Weight (Pounds) – Weight of blasting explosives used (in Pounds)
33.	High Explosives Weight (Tons) – Weight of blasting explosives used (in Tons)
34.	Incendiary Devices – Description of the different type of incendiary bombs used
35.	Incendiary Devices Type – Number of incendiary bombs used
36.	Incendiary Devices Weight (Pounds) – Weight of incendiary bombs used (in Pounds)
37.	Incendiary Devices Weight (Tons) – Weight of incendiary bombs used (in Tons)
38.	Fragmentation Devices	– Description of the different type of fragmentation devices used
39.	Fragmentation Devices Type –Number of fragmentation devices used
40.	Fragmentation Devices Weight (Pounds) – Weight of fragmentation devices used (in Pounds)
41.	Fragmentation Devices Weight (Tons) – Weight of fragmentation devices used (in Tons)
42.	Total Weight (Pounds) – Weight of all types of devices used (in Pounds)
43.	Total Weight (Tons) – Weight of all types of devices used (in Pounds)
44.	Time Over Target – Amount of time spent by aircraft over target
45.	Bomb Damage Assessment – Description of results of the attack
46.	Source ID – Unique rapport ID


## Why Excel ##

When I checked in Kaggle what this dataset contained, I decided to use Excel to clean up that dataset for several reasons:
-	I will work only with a small part of this data.
-	Data was collected manually, so there are a lot of empty cells or improperly classified information (data in wrong cells).
-	Data needed to be checking and corrected manually.
-	Some cells had to filled in manually.
-	In my opinion, Excel is the tool for manual work on small data sets 


## How I worked with data in Excel ##

### Data import ###

I imported data to Excel from operations.csv. During importing, I changed the formatting of column “Mission Date” from text to date. Next, I used the sorting function to check the data. Data format was correct.
After that, I used a filter to extract a new set of data. I used the following filters: 
- Mission Date - 1942 year,
- Theater of Operations - PTO
- Target Country - Places which are close to Salomon Islands and New Guinea or blank.
- Target City – city and places which are in Salomon Islands and New Guinea area or blank.
  
As a result, I was left with 950 rows.
Finally, I created a new excel spreadsheet containing only the 950 rows selected. 


### Data cleaning ###

New dataset was much smaller than before, so I was easier to filter information.  I had to manually check every column. I made the following changes:

-	column Unit ID: there were 53 rows with incorrect Unit ID’s or blank (correct ID has to follow a specific patter: a number followed by a letter code (USAAF - FG, BS, BG for RAAF – SQ)).
    -	1 row contained name 405 B instead of 405 BS – corrected
    -	5 rows contained Target Latitude instead of Unit ID (data was incorrectly entered in the entire row)– I corrected data in all cells
    -	47 rows with incorrect data (base name instead of Unit ID) or blank – I filled these cells with “unknown”
-	column Aircraft Series: 
    -	13 rows contained different name variations of the same airplane (BEAU, BEAUF, BEAUFORT) – I corrected it to BEAUFORT
    -	1 row contained the name LIB. This row belonged to 32 SQ, which didn’t use Liberator aircraft in 1942. They used HUDSON instead -I changed the data accordingly
-	column Callsign: was empty – I deleted it.
-	column Mission Type: it contained numeric information from 1 to 12 and 5 blank cells – I didn’t need this information in my analysis, so I decided to delete this column after finishing the cleanup process. 
-	columns Takeoff Base, Takeoff Location, Takeoff Latitude, Takeoff Longitude, Target ID: I didn’t need the information – I deleted these cloumns.
-	column Target Country: I decided to changed name to Geographic Area and corrected the data to represent geographical location instead of political situation.
    -	3 rows contained "PAPUA NEW GUINEA, MANUS ISLAND" instead of “NEW GUINEA” – I changed them to “NEW GUINEA”
    -	6 rows contained “AUSTRALIA”. I checked the coordinates
        -	3 rows referred to Timor Sea outside that area that I was analyzing – I deleted these rows
        -	3 rows were referring to places within Australia – I included these rows
    -	139 cells contained “BISMARK ARCHIPELAGO” I checked coordinates
        - 3 rows should be “NEW GUINEA” instead of “BISMARK ARCHIPELAGO” – I changed them
    - 2 cells contained “CORAL SEA AREA” I checked coordinates, which pointed to  “BISMARK ARCHIPELAGO” – I changed these cells
    - 710 cells contained “NEW GUINEA” - I checked coordinates
        - 1 row coordinates pointed to Celebes – I deleted the row as it was outside of the scope of my analysis
        - 60 cells should be labeled as“SOLOMON ISLAND” or “BISMARK ARCHIPELAGO” instead of “NEW GUINEA” – I changed them
    -	56 cells contain “SOLOMON ISLAND”  - I checked coordinates
    -	49 rows with empty cells I checked coordinates and added the relevant description or deleted
        -	1 row was Moluki Island what is outside my geographic frame – I deleted it
        -	12 rows belonged to Timor Sea outside area of my analysis – I deleted them
        -	8 cells should contain “SOLOMON ISLAND” – I filled them
        -	19 cells should contain “NEW GUINEA” - I filled them
        -	1 cell should contain “BISMARK ARCHIPELAGO” - I filled it
        -	8 cells should contain “AUSTRALIA” - I filled them
-	Column Target City: this column contained target description – name of cities or villages, type of vessels, etc. – changed the cell’s name to “Target Description”
    -	2 blank rows – I filled them with “unknow”
-	Column Target Type: contained 39 types of detailed target description (historic information), sometimes similar to information in the respective  Target Description cells – I didn’t change it.
-	Columns Target Industry, Target Priority: both were empty – I removed them
-	Columns Target Latitude and Target Longitude:– All data was correct
-	Column Altitude (Hundreds of Feet): I didn’t need this information – I removed the collumn
-	Columns Aircraft Returned, Aircraft Failed, Aircraft Damaged, Aircraft Lost: the columns were empty - I removed them
-	Column Attacking Aircraft: contained 14 blank cells. As I knew the aircraft type, the unit code, the target location, High Explosive type and High Explosive Weight for each of the blank rows, I compared it with data from other missions with same parameters. For example, in order to find ‘Attacking Aircraft’ for B-26 from 19 BS for mission on 16-11-1942, in which the unit dropped 2 tons of 2000 LB GP (GP-M34/M66) High Explosive bombs on supply depot in Buna, I compared it with another mission (5 bombers from 22 BG that dropped similar type and number of bombs in Buna on the same day).
    -	4 rows with B17 airplane contained data about numbers of aircraft and High Explosive  in wrong cells – I corrected that
    -	9 empty cells –  I filled them in accordance with the method above
    -	1 row remained empty – there was not enough data to fill it.
-	Columns “Airborne Aircraft” and “Bombing Aircraft”: contained small amount of data and were less useful in future analysis – I removed them
-	Next 14 columns (High Explosives onwards): contained information about type of bombs used during missions. For my analysis, I only used  information about total amount of bombs dropped (Total Weight (Pounds)). 
Before I deleted the unnecessary information, I checked the column Total Weight (Pounds). There were 165 blank cells. To filled them I used rest of columns
    -	5 rows contained information about total weight but in wrong cells – I corrected it.
    - I used column Total Weight (Tons) to fill empty cells by using formula “=…*2000” – after this, I was left with 24 empty or 0 value cells.
    -	1 row – I filled it  with information from column High Explosives Weight (Pounds)
    -	23 rows - I didn’t have information which would allow me to fill empty cells. I filled them with 0
    - I removed the formula
-	columns Time Over Target, Bomb Damage Assessment, Source ID: didn’t contain useful information – I removed them


After this I had 934 rows and 15 columns.
	
-	I checked the integrity of data again. I use filters in columns: Country, Air Force, Unit ID and compered the dataset to information found on Wikipedia and website [here](https://www.ozatwar.com/5thaf.htm) to verify it
  -	1 row contained wrong data about 19 BG (wrong country and air force) – I corrected it
  -	22 rows I had to change unit ID from 89 S to 89 BS
  -	3 rows changed country to Australia and air force to RAAF
  -	1 row changed unit ID form 35 B FG to 35 FG
  -	1 row changed  Air Force from RAAF/NEI to RAAF
  -	I changed column name from Mission Type to Number of Missions and filled cells with value 1


I did not remove double rows – I could not verify whether there were more missions on the same day or the data contained mistakes.

## Analysis

The dataset was finally saved in Excel format [AB_PTO_1942_cleaned1 .xlsx](https://github.com/TomekKulesza/Documents-myWork-projects-Portfolio/files/7555354/AB_PTO_1942_cleaned1.xlsx) which is ease to read by Tablaeu.

To answer for question which was foundation of my analysis I created presentation contained three dashboards [here](https://public.tableau.com/views/Alliedaerialbombingin1942onNewGuineaBismarckSeaandSolomonIslands/SummaryforUSAAFRAAFraids?:language=en-US&:display_count=n&:origin=viz_share_link).

