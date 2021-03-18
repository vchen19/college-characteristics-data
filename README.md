# college-characteristics-data
This analysis serves to group colleges by characteristics that would be of interest to an applying high school senior.

## Background

High school seniors today face overwhelming pressure and uncertainty regarding college applications. According to a survey of 31,000 students, [92% of seniors](https://www.insidehighered.com/admissions/article/2020/11/09/nearly-half-high-school-seniors-havent-started-applying-college-survey) feel stress and fear regarding college applications, primarily due to concerns of cost. And yet, only [8.1% of students](https://www.insidehighered.com/admissions/article/2020/11/09/nearly-half-high-school-seniors-havent-started-applying-college-survey) say that college advertising feels personal to them. There is clearly a deficiency of information for students to find which colleges are best for their specific circumstances and needs. The consequence is that students are applying to [more colleges than ever](https://www.insidehighered.com/admissions/views/2017/12/04/high-school-students-are-applying-too-many-colleges-essay), in hopes that they have a higher chance of getting a good match. This can lead to increased stress and anxiety during a critical period in their lifetimes.

## Business question 

Can cluster analysis help high school seniors to narrow down which universities to apply to?

## Data sources

All data was sourced from the [Opportunity Insights College Data](https://opportunityinsights.org/data/?geographic_level=100&topic=105&paper_id=0#resource-listing). The original dataset can be found [here](https://github.com/vchen19/college-characteristics-data/blob/main/mrc_table10%20(1).csv).

## Methods

More detailed methods can be found here. 

A database called “College Level Characteristics from the IPEDS Database and the College Scorecard” was downloaded from Opportunity Insights College Data. Each row lists a college or university. The college’s tier, instruction expenditures per student in 2013, sticker price in 2013, percent of students graduating within 150% of normal time in 2013, average faculty salary in 2013, and median earnings post graduation in 2011 were considered relevant columns for our analysis, and all other columns were deleted. Next, the data was sorted by the first column from high to low. The rows with missing data in that column would fall to the bottom, making it easier to delete rows with missing data. This process was repeated for all columns. Each school was assigned a unique number from 1-2069.

Next, 10-cluster Excel Solver analysis began on this data. The mean and standard deviation was found for each of the six categories, which was used to find z-scores for each data point for each school. 10 anchor schools were arbitrarily chosen as a starting point for the optimization problem, and their respective z-scores were identified. Equations were set up to calculate the mean squared distance of each school’s z-scores to each anchor’s z-scores. The minimum distance of the 10 distances was identified for each school, then, the sum of these minimum distances was found. The Excel Solver tool was used to minimize this sum of minimum distances by changing the anchor schools. The individual schools in each cluster were found by matching the minimum distance of each school to a cluster. 

## Results

The z-scores of the anchor schools that the Solver found are shown below. These z-scores are representative of the characteristics of each of the ten clusters, also shown below.

![Cluster Characteristics Table](https://github.com/vchen19/college-characteristics-data/blob/main/Cluster%20Characteristics%20Table.png)
![Cluster Characteristics Bar Graph](https://github.com/vchen19/college-characteristics-data/blob/main/Cluster%20Characteristics%20Bar%20Graph.png)

The analysis resulted in 216 schools in the first cluster, 648 schools in the 2nd, 61 in the 3rd, 82 in the 4th, 261 in the 5th, 194 in the 6th, 189 in the 7th, 379 in the 8th, 29 in the 9th, and 10 in the 10th.

## Discussion

Analysis like this can be useful to students looking to narrow down the thousands of college options that exist in this country. By identifying which schools have relatively high quality of education (reflected in metrics like expenditure per student) for relatively low cost (reflected in metrics like sticker price), a student can alleviate some worries about the cost of college and identify which colleges are best suited to their specific needs. For example, a student looking for a school with a lower sticker price with an above-average graduation rate might look at clusters 6 and 9, for schools like the University of Missouri or the Colorado School for Mines.

There are limitations to this analysis. 10-cluster analysis cannot narrow down the number of schools to a reasonable amount for students to apply to. Additionally, other, more subjective factors should be taken into consideration for a student. However, this analysis can serve as a useful starting point to eliminate options that are not within a particular cluster of interest. A more precise analysis might find use a greater number of clusters. It would also be useful to find a way to not eliminate schools with missing data, perhaps by assigning an average value where there is data missing. This would ensure that any potential options are not excluded from the student’s decision-making process.

