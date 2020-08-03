# Regression-Model-for-King-County-Housing-Market
An investigation into the variables that affect housing costs in King County, Washington.

## Objectives:

* Find what aspects of a house have a significant impact on its value
* Which is a better predictor of price: Condition or Grade?
* Find the areas that are more profitable to sell homes. 

I decided to used the OSEMN method as I approached this project.  This is because the method seemed, to me, to cut away a lot of the fluff from the CRISP-DM and KDD methods into a simple, somewhat free form, approach.

# Obtaining the data

After considering our stakeholder's needs, we determined that we needed (1) explore the relationship between a house's condition and the grade given by King County, (2) find a way to cross reference data to locate the best place to search for homes, and (3) also look for predictors that impact house prices the most.  This way we can help our stakeholders **find a deal** on a house, make **quick renovations** at minimal costs, and sell the home quickly for a profit.

# Scrubbing

We got rid of the placeholder values and NaN's, as well as did some **feature engineering** to split King County into 4 quadrants, change the **dates sold** into **seasons** and **days of the year** to explore whether seasonality has any effect on house prices, and made dummy variables a clean set to work with. 

# Exploring

I used joint plots to visualize the relationship of the features to our target variable of price.    
Right away we can see that there is **little to no relationship** between house prices to the day of the year.

![Imgur](https://i.imgur.com/TK85Hr8.png)

Consequently, the same can be said for all of the season variables we created.  The caveat here is that this **doesn't** mean that the prices of individual homes don't change, but you can expect to find houses at any price no matter the day or season of the year.  In other words, there is **no pattern** in the market in which a large number of houses are sold at lower prices because of less demand in specific seasons.

## The Questions!

### What single aspect of a house has the greatest impact on its value?

According to the model, **grades** have the the **greatest impact** on a home's price, especially if they have a **grade of 10 or higher** (binned as grade A in notebook). Even grades 8 and 9 are highly impactful.  

![Imgur](https://i.imgur.com/QKvBnyX.png)

As we can see from this plot, there is a clear **linear relationship** between grades and price.  As the home's **grade increases**, the **average price increases**, as well.  The caveat to this is that, according to King County, a **house's potential grade has limits**.  For instance, their website explicitly states that for a home  **grade of 13** (the highest) it must be "**Mansion level**". This means that small, single-level, 1,500 square-foot homes will **never** be able to obtain a grade of 13, **no matter how much work is put into it**.

### Recommendation:
When flipping homes, **focus** most on **increasing** the home's grade.  Try to **find a home** that is **at least has a grade of 6 or 7**.  These homes will be up to code and may reduce time and overall costs.

### Which is a better predictor of price: Condition or Grade?

![Imgur](https://i.imgur.com/LiB4YlF.png)

Again, this one goes to the home's grade.  We didn't know this going into the project, but if **grade** is the highest predictor, then it will obviously **out perform** the condition of the home, as well.

This does not mean that we didn't find anything useful during our analysis.

![Imgur](https://i.imgur.com/T8kAZBi.png)

A simple change from a **fair** condition to an **average** condition brings about the **greatest change** in price.  Add this to what we have seen with grade and you can see the quality of home you should purchase and about how much work to put into it.

### Recommendation:

Purchase a home in a **fair condition** and has a **minimum grade of 6**. Put in enough work to **raise the condition to average** and the **grade one increment higher** and you'll see a **significant increase** in the home's price.

### Where should we look for a home?

We cross referenced four separate plots using the coordinates of the homes in our dataset.

![Imgur](https://i.imgur.com/dHVQ16W.png)

Here, we see that prices of homes increase as you get into the Bellevue, Kirkland, and Redmond Area.  House prices **drop** as you head **south**.  It was a bit suspicious to see so many home's that the map's legend claimed had a price of "0". To ease our suspicions, we made another plot which filtered out every value above 140,000.    

![Imgur](https://i.imgur.com/B8pwnMK.png)

This greatly clarified the pricing situation and also gave us a clue on where to start looking for homes.  Around latitude 47.5, longitude -122.35, you'll see a cluster of homes that are reasonably priced and not too far from Seattle to boot.  

With these coordinates in mind, we examined the **grades** these homes received to see if they met our criteria.

![Imgur](https://i.imgur.com/yoKYaTn.png)

Remember: We're looking for a home with a grade of 6 or more. Drawing your eyes to the **cluster** of reasonably priced homes, it appears many of these homes have **grades ranging from 6 to 8**. 

So far the homes in this cluster have met 2 two of our conditions: they're reasonably priced and have a decent grade. Last, we plotted a map of the houses with a condition rating of 2 (fair).

![Imgur](https://i.imgur.com/v55jM0f.png)

There we go! In that **cluster** we see plenty of homes with a **condition rating of 2**.  The homes in this area  have surprisingly **met all three of our conditions**.  They're generally **less expensive**, has have a **minimum grade of 6**, and are in **fair condition**.

So where is this place? Plug the coordinates into Google Maps and we get...

![Imgur](https://i.imgur.com/i92oEgP.png)

**White Center** and the **Highline Seattle** area!

### Recommendation:
Search for homes south of Seattle in the **White Center/Highline** area.  Again, look for homes in **fair condition** and have a **minimum grade of 6**. 

# Modeling 

The baseline model was quite rough. 

![Imgur](https://i.imgur.com/VLm3sLH.png)

We see here that the Adjusted R-squared value is 0.722, meaning that the model can only explain 72.2% of the residual errors. 

![Imgur](https://i.imgur.com/IpnpVWv.png)

The skew of the errors weren't too bad, but the kurtosis denoted that the distribution of the residuals was very "peaky".

![Imgur](https://i.imgur.com/9KzngyU.png)

Lastly, the RMSE was pretty bad.  I then took to removing outliers from our conituous variables and re-ran the model to see that the R-squared value dropped to 0.704, the kurtosis did improve substantially, though.  

We then went through several types interations of models in order to improve the R-squared.  First  we looked for statistically insignificant features. Then, we checked for **multicollinearity** and removed the ones that were highly collinear. This resulted in a simpler model, but no change in R-squared.  Through trial and error, it was determined that adding or removing any other features would result in a lower R-squared.  

We tried performing **log transformations**, but that **dropped the R-squared** value to 0.656 and **increased** the **standard errors** of the features. Ultimately, it was decided to revert to before the log transformation since an R-squared value of 0.704 is a good compromise. 

Finally, we tried **Step-wise selection** on an earlier model that had the most variables available to find the optimum combination of features based on their p-values.  This actually raised some questions.  For one, even though the R-squared increased to  0.722, the **RMSE was identical** to the model whose R-squared was 0.704.  Additionally, the algorithm determinded that several variables had a p-value of **zero**.

![Imgur](https://i.imgur.com/13qYiR3.png)

Reluctant to believe that whether or not a home was viewed was a perfect predictor of a home's price (as that is how I interpreted this), we went back to the model that with an R-squared value of **0.704**.  As a final "Hail Mary", we **added interactions** to the model and saw an **increase in R-squared** and a **decrease in skew, kurtosis, and RMSE**!

![Imgur](https://i.imgur.com/QMsrtee.png)

![Imgur](https://i.imgur.com/2dvxQPl.png)

![Imgur](https://i.imgur.com/CzMwLTz.png)

![Imgur](https://i.imgur.com/C6rOqEH.png)

# Interpretation 
The model produced some interesting findings.  The features with the highest impact on price were whether the home received a **grade of 10 or higher** from the county, **on the waterfront**, and if it was **located in Quadrant 1** (the northwest part of King County).  

I'm pretty confident in these findings as they reflect the relationships we found during EDA.  

![Imgur](https://i.imgur.com/VlxgXi4.png)
Having a grade of 10 or higher (binned as grd_A in the model)

![Imgur](https://i.imgur.com/HbjedMM.png)
House on the waterfront

![Imgur](https://i.imgur.com/dHVQ16W.png)
Homes in Quadrant 1

In each of the above examples, you can see that the presence of these features will cause a **drastic increase in price**.  

As we can see from the QQ-plot, the **residual errors** are still **non-normal**.  The **RMSE**, while drastically improved, is still **over 150,000**.  This could be a result of not cutting out enough outliers, or misinterpretting continuous variables ad categorical or visa versa. It could also be a result of doing things things out of order, or not capitalizing on more feature engineering.  

There is some **good news**, however. The model is, for all of its flaws, **consistent**, as we can see from the cross-validation tests. When we contextualize the RMSE with the fact that our of houses prices range from $78,000 to over $3 million, being off by $150,000 isn't too bad on the high end of the market.  

# Conclusion

The model needs improvement.  In the future, I'd like to experiment more with feature engineering, being harsher on outliers, re-examine my interpretation of the continuous and categorical variables, and trying out other transformations.


