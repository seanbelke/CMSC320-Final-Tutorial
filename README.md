# CMSC320-Final-Tutorial

In which we analyze WCA data.  Some analysis ideas we have are:

- Predicting single based on average (and more importantly, how strong the relationship is)
    - later: predicting a person's best single based on their average in a particular round
- Predicting country of residence based on relative placings in events.  For this one we want to explore if there really is any relationship between the events that someone competes in the most, or does the best in, and where they live.  For example, it seemed like (at least at one point), Skewb was popular among Polish cubers, but we want to try to quantify that observation.
- Attempting to cluster competitors into the groups they competed in.  This one is based on the idea that each group will have some good scrambles and some bad scrambles, and so we might be able to cluster people into groups based on who had their best solve on the first scramble and their worst on the fourth, etc.

We're going to use the WCA databases found at https://www.worldcubeassociation.org/results/misc/export.html

### Predicting single based on average

What we wish to investigate here:
- Is there a linear relationship between one's best single in competition and their best average in competition?
- Graph a scatterplot with a line of best fit for a few different events to show this relationship. 
- Do any events look nonlinear?
- Plot the correlation coefficients for all (most, maybe not multiblind for example) WCA events based on this analysis.  Are there any outliers, or do all events have roughly the same strength of a linear relationship between single and average?  (does anything weird happen with BLD events?)

What kind of data do we need for this analysis?

We would need a table with columns for CompetitorID, EventID, PBAverage, and PBSingle.  Can probably just pull from the top 200 results for each event for this one.  The idea would be to take the people that are in the top 200 for each event's average.  Then find their best single, and add a row to our big table for that person (personID, eventID, average, single).  Note that the times are listed in hundreths-of-seconds in the table.  For example, the 2x2 single 0.49 seconds is listed as 49.  

Notes: 
- during EDA we realized that the relationship might not be fully linear.  When we look at the slope of the single vs. avg regression line for the fastest 200 competitors, it's less than the slope of the single vs. avg regression line for the top 100000 competitors.  This seems to suggest that there's an upward curve as we go higher, which isn't linear.  We can mention in our analysis that this is why we think it's not linear.

For Sean on Friday: 
- Clean up dataframe: 
    - drop unused columns
    - drop magic and master magic
- Begin with 3x3-centric analysis.  
    - random sample of entire dataset
    - note how it looks really linear!
    - could this be due to a large range of values relative to the residuals? 
    - try a smaller range (e.g., sample from ranks 0-200 (then maybe 10-200, citing yusheng du as a reason to ignore the very top results), 1000-2000), and show that they look less "tight".
    - run some regression hypothesis tests on the top solvers to see what kind of linear relationship we see there.  
    - run the same regression hypothesis tests on the overall dataset to see what kind of linear relationship we see there.  
    - talk about your hunch that it's not linear by comparing the slopes of the regression line for the top samples to the ones for the later samples.  
    - add a quadratic term (?) here I'm getting confused.
