# Regression-Model-for-King-County-Housing-Market
An investigation into the variables that affect housing costs in King County, Washington.

## Objectives:

* Find what aspects of a house have a significant impact on its value
* Which is a better predictor of price: Condition or Grade?
* Find the areas that are more profitable to sell homes. 

## The Questions!

### What single aspect of a house has the greatest impact on its value?

According to the model, **grades** have the the **greatest impact** on a home's price, especially if they have a **grade of 10 or higher** (binned as grade A in notebook). Even grades 8 and 9 are highly impactful.  

![Imgur](https://i.imgur.com/M1ZiyfZ.png)

As we can see from this plot, there is a clear **linear relationship** between grades and price.  As the home's **grade increases**, the **average price increases**, as well.  The caveat to this is that, according to King County, a **house's potential grade has limits**.  For instance, their website explicitly states that for a home  **grade of 13** (the highest) it must be "**Mansion level**". This means that small, single-level, 1,500 square-foot homes will **never** be able to obtain a grade of 13, **no matter how much work is put into it**.

#### Recommendation:
When flipping homes, **focus** most on **increasing** the home's grade.  Try to **find a home** that is **at least has a grade of 6 or 7**.  These homes will be up to code and may reduce time and overall costs.

### Which is a better predictor of price: Condition or Grade?

![Imgur](https://i.imgur.com/npW51s9.png)

Again, this one goes to the home's grade.  We didn't know this going into the project, but if **grade** is the highest predictor, then it will obviously **out perform** the condition of the home, as well.

This does not mean that we didn't find anything useful during our analysis.

![Imgur](https://i.imgur.com/kYOPcHf.png)

A simple change from a **fair** condition to an **average** condition brings about the **greatest change** in price.  Add this to what we have seen with grade and you can see the quality of home you should purchase and about how much work to put into it.

#### Recommendation:

Purchase a home in a **fair condition** and has a **minimum grade of 6**. Put in enough work to **raise the condition to average** and the **grade one increment higher** and you'll see a **significant increase** in the home's price.

### Where should we look for a home?

We cross referenced four separate plots using the coordinates of the homes in our dataset.

![Imgur](https://i.imgur.com/Q7bLsSu.png)

Here, we see that prices of homes increase as you get into the Bellevue, Kirkland, and Redmond Area.  House prices **drop** as you head **south**.  It was a bit suspicious to see so many home's that the map's legend claimed had a price of "0". To ease our suspicions, we made another plot which filtered out every value above 140,000.    

Next, we looked at a map of the grade of homes.

![Imgur](https://i.imgur.com/XkJNK0o.png)

Remember: We're looking for a home with a grade of 6 or more.  According to this map, there is no shortage of grade 8 homes in the area.  If you draw your eyes to latitude 47.5, longitude -122.3 ~ -122.35, you'll see a cluster of homes that are in the greater Seattle area that have **grades from 6 to 8**. 

Last, we plotted a map of the houses with a condition of 2 (fair).  A lower house condition will help offset the price of a higher grade.

![Imgur](https://i.imgur.com/yVHiuHI.png)

There we go! In that cluster we were looking at in the previous map, we see plenty of homes with a **condition of 2**.  This is the best place to look for a home to flip as the area is **less expensive**, has homes with a **minimum grade of 6**, and are in **fair condition**.

So where is this place? Plug in the coordinates to Google Maps and we get...

![Imgur](https://i.imgur.com/P23QDNe.png)

White Center, Washington and the Highline, Seattle area!

#### Recommendation:
Search for homes south of Seattle in the **White Center/Highline** area.  Again, look for homes in **fair condition** and has a **minimum grade** of 6. 

