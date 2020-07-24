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

![Imgur](https://i.imgur.com/kcyyvnk.png)

This greatly clarified the pricing situation and also gave us a clue on where to start looking for homes.  Around latitude 47.5, longitude -122.35, you'll see a cluster of homes that are reasonably priced and not too far from Seattle to boot.  

With these coordinates in mind, we examined the **grades** these homes received to see if they met our criteria.

![Imgur](https://i.imgur.com/tFBIeGg.png)

Remember: We're looking for a home with a grade of 6 or more. Drawing your eyes to the **cluster** of reasonably priced homes, it appears many of these homes have **grades ranging from 6 to 8**. 

So far the homes in this cluster have met 2 two of our conditions: they're reasonably priced and have a decent grade. Last, we plotted a map of the houses with a condition rating of 2 (fair).

![Imgur](https://i.imgur.com/dnuiVWw.png)

There we go! In that **cluster** we see plenty of homes with a **condition rating of 2**.  The homes in this area  have surprisingly **met all three of our conditions**.  They're generally **less expensive**, has have a **minimum grade of 6**, and are in **fair condition**.

So where is this place? Plug the coordinates into Google Maps and we get...

![Imgur](https://i.imgur.com/P23QDNe.png)

**White Center** and the **Highline Seattle** area!

#### Recommendation:
Search for homes south of Seattle in the **White Center/Highline** area.  Again, look for homes in **fair condition** and have a **minimum grade of 6**. 

