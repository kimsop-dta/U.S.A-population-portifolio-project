 
# Project Title

U.S.A States-Dashboard


## Problem Statement

Create a Dashboard of the USA states and the population changes from 1950 to 2020

### Steps followed 

- Step 1 : Loaded the US state and the US population file into Power Bi.The daset was csv files.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4:In the home tab under manage column,clicked choose column.In the US States dataset select the name,abbreviation,census region name and census division name
- Step 5:Rename the columns,name to state,census region name to census region and census division name to census division.
- Step 5:It was observed that the US States population dataset the table was pivot.Select the year column and right?left click,select unpivot other columns.Rename the attribute column to abbreviation and value column to state population.
- Step 6: It was observed that the States of Hawai and  had no population data before 1950.Filter the year column,select the filter icon on year,number filter,select greater or equal than,input 1950 in the box.
- Step 7:Create a table named Measures.In the home ribbon select enter data,renamed the table _Measure and renamed the column _.Good practice to store all your measure in one table to avoid confusion.
- Step 7:close the power query and apply the changes to move to the report view.
- Step 8:In the data pane select the _Measure table and create new measure named States to find total count of US States.

   States = COUNT(States[State])
 
- Step 9: Calculated column was created in which, the US population of 2015 was dertermined.

for creating new column the following DAX expression was written;
  
  2015 population = CALCULATE(
    SUM('states-population'[state population]),
    'states-population'[Year]=2015) 

Snap of new calculated column ,
![Image](https://github.com/user-attachments/assets/8e6f06e7-7c9e-4f37-9546-222dc2da8cac)

- Step 10: Table was inserted into the canvas.State,Abbreviation,census region and census division were added into the table.
- Step 10: A bar chart was also inserted to the report design area representing the census region & State. "census region" was also added to the Legends.

snap of the bar chart 
![Image](https://github.com/user-attachments/assets/b0f63125-b0e3-4325-b0ed-3c59ba67de03)
- Step 11 :Insert Shape map into the report canvas.Add state in the location area,census region in the legend area and states count in the saturation area.

Snap of the Shape area map
![Image](https://github.com/user-attachments/assets/430c12e1-6c2e-42c1-be78-76f15450da8f)
- Step 12 :Insert a ribbon chart in the canvas.Add year in the X axis,population in the Y axis and state in the legend.

Snap of the ribbon chart
![Image](https://github.com/user-attachments/assets/523b0cf4-1eca-434b-ae24-56bb4b1d2a51)

- Step 13 : Insert a Slicer in the Canvas.Right click on the census region in the States and create an hierachy.Add the census division to the created hierachy.In the slicer and the created hierachy.

snap of the slicer
![Image](https://github.com/user-attachments/assets/bea62fd2-0220-41c2-9a0c-cf82bb8987b2)

- Step 14 :Rename the page Overview and create a new page called pop.tooltip.
- Step 15 : On the canvas format pane,select the page information,Select tooltip as the pagetype.
- step 16: Insert a line chart in the canvas,add the year to the x axis and the population to the y axis.

snap of the line chart

![Image](https://github.com/user-attachments/assets/1c9437c5-f879-46af-a572-ae744ff0d395)

- Step 17: go to the overview page  and elect the state map.ON the property pane active the tooltip and set the  page to pop.tooltip.

- step created Dynamic Title measure for the pop.tooltip using the following DAX expression;

     Tooltip title = 
      SELECTEDVALUE(States[State]) & "-Years"
      & MIN('States-population'[Year]) & "-"
      & MAX('States-population'[Year])  
