# CMSC320-Final-Tutorial

In which we analyze the World Cube Association (WCA) data.
The WCA oversees and organizes Rubik's Cube competitions around the world.
Read more about the WCA here: https://www.worldcubeassociation.org/.
Results from Rubik's Cube competitions are generally kept track of using
single solve times and average times over 5 or 3 solves. There are also
multiple events, more than the standard 3x3x3 cube, for example, 4x4x4,
3x3x3 one-handed, etc.

Some analysis ideas we have are:

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
