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
- Predicting country of residence based on relative placings in events.  For this one we want to explore if there really is any relationship between the events that someone competes in the most, or does the best in, and where they live.  For example, it seemed like (at least at one point), Skewb was popular among Polish cubers, but we want to try to quantify that observation.
- Attempting to cluster competitors into the groups they competed in.  This one is based on the idea that each group will have some good scrambles and some bad scrambles, and so we might be able to cluster people into groups based on who had their best solve on the first scramble and their worst on the fourth, etc.

We're going to use the WCA databases found at https://www.worldcubeassociation.org/results/misc/export.html
