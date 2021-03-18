# Detailed Methods

1. Download the dataset “College Level Characteristics from the IPEDS Database and the College Scorecard” from [Opportunity Insights](https://opportunityinsights.org/data/?geographic_level=100&topic=105&paper_id=0#resource-listing). 
2. Copy and paste the data into a new sheet. Delete all columns that are not name, tier, exp_instr_pc_2013, sticker_price_2013, grad_rate_150_p_2013, avgfacsal_2013	scorecard_median_earnings_2011. These columns represent the name of the college, its tier, instructional expenditures per student in 2013, sticker price in 2013, graduation rate within 150% of normal time in 2013, average faculty salary in 2013, and median earnings post graduation in 2011. Title this sheet “Relevant Columns”.
3. Copy and paste the data in Relevant Columns into a new sheet called “Removed Missing Data.” 
4. Remove all rows that have data missing in any of the six columns. To do so, sort the data by tier, from low to high. All rows without tier information will fall to the bottom of the sheet. Delete these rows. 
5. Repeat step 4 for all remaining columns in the sheet until all rows have complete data.
6. Copy and paste this data into C17 of a new sheet called “Analysis”. 
7. Add six new columns for the z-scores of each of the six quantitative characteristics. 
8. Add a new column titled “number” in column B. Type “1” into B18. Type “=B18+1” into B19. Drag this equation down through the column. This numbers each institution from 1-2069.
9. Record the mean and standard deviation with Excel formulas =AVERAGE(range) and =STDEV(range) respectively for each of the six columns. 
10. Use the =STANDARDIZE(value, mean, stdev) equation to find the z-scores for each of the six characteristics for every school. 
11. In cell E4, type table heading “Anchor School.” From F4:L4, type “School #”, then “z_characteristic” for each of the six characteristics. 
12. In G3:L3, input 9-14, the column numbers for each of those z-scores.
13. In the “School #” column, type 10 arbitrary numbers from 1-2069 as initial guesses for the Solver problem.
14. In E5, type the equation =VLOOKUP($F5, $B$17:$O$2086, 2). Drag this equation through the column. This returns the school corresponding to the number.
15. In G5, type the equation =VLOOKUP($F5, $B$17:$O$2086, G$3). Drag this equation through the row, then through the columns. This returns the z-scores of the schools chosen.
16. In P17:Y17, add new headings “Distance^2 to 1,” “Distance^2 to 2,” etc. until “Distance ^2 to 10”. 
17. In Z17, add the new heading “Min Distance.” In AA17, add the new heading “Cluster.”
18. In P18, type the equation =SUMXMY2($J18:$O18, $G$5:$L$5). This returns the squared distance between that row’s z-scores and the first anchor school’s. 
19. Drag this equation horizontally through Distance^2 to 10. In Q18, change all the 5’s to 6’s; in R18, change all the 5’s to 7’s, and so on. 
20. Drag the Distance equations through their columns. 
21. In Z18, type the equation =MIN(P18:Y18). This returns the minimum distance. 
22. In AA18, type the equation =MATCH(Z18, P18:Y18, 0). This returns the cluster number that corresponds to the minimum distance.
23. In Z8, type the equation =SUM(Z18:Z2086). This returns the sum of the minimum distances. Label this value as such.
24. In the Data tab, click Solver. 
25. Set the objective to Z8 to Min.
26. In “By Changing Cells,” select the column of school numbers ($F$5:$F$14). 
27. Set the constraints so that the column values are greater than or equal to 1, less than equal to 2069, and are integers.
28. Select the Evolutionary Solving Method. Click Options, then the Evolutionary tab and set the Mutation rate to 0.5. Click OK.
29. Click Solve. When the solver is done, make sure “Keep Solver Equation” is selected, and click OK. The Anchor Schools should now reflect the Solver’s solution. 
30. Copy the Cluster column in column AD. Copy the name column into column AC. 
31. Sort by Cluster. Now, we can see the schools that belong to each cluster more clearly.
32. In AC3 and AC4, title a new table with headings “Cluster” and “Count.” Under “Cluster,” input 1-10. 
33. Select the ten cells under “Count” and type =FREQUENCY(AD18:AD2086, AC4:AC13). Hit Ctrl+Shift+Enter. This returns the number of schools in each cluster.
34. Copy and paste the table with the anchor school characteristics into a new sheet called “Visualization.”
35. Create a bar graph with the z-scores, with each category being a different series and the Horizontal Axis Labels being the Anchor School names.
36. Add a legend and title the axes and the bar graph.
