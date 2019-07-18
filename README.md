# The-Wyndor-Glass-Co-Optimal-Advertising-Solutions
## summary
“The Wyndor Glass Co.”  is a famous example that we handle resource utilization questions in order to increase the production of two types of glass doors produced by three plants(1, 2 and 3).

When making decisions about the mix of products, production capacities and potential future sales should be considered together. Here, sales information is an uncertainty factor that depends on the marketing strategy.

In this problem, we assume that there will be N(200) total advertising time slots with two different media(TV and radio). 
In our model, we assume sales predictions will be based on the number of TV and radio advertising time slots. 

## outliers
We built a linear model based on training set data to retrieve the error items. We made a Q-Q plot for error items and found 9 outliers.
### QQ Plot
The Q-Q plot, or quantile-quantile plot, is a graphical tool to help us assess if a set of data plausibly came from some theoretical distribution such as a Normal or exponential.

For example, if we run a statistical analysis that assumes our dependent variable is Normally distributed, we can use a Normal Q-Q plot to check that assumption. It’s just a visual check, not an air-tight proof, so it is somewhat subjective. 

## LEO

fter removing outliers, we built the linear regression model once again, and we created two models based on this.
The first one is a deterministic forecast (DF) model, which we simply used the linear regression model for:𝑚(1(𝑋) = 𝛽-0 + 𝛽-1𝑥1 + 𝛽-2𝑥2.

The second one is the empirical additive error model (EAE), where 𝑚(2(𝑋, 𝜉 ) = 𝛽-0 + 𝛽-1𝑥1 + 𝛽-2𝑥2 + 𝜉0is used, as well as 𝜉0 = 𝑊 − 𝑚(1(𝑋, 𝜉 ), which is named as empirical additive errors.

The next step is putting what we received from the prediction into the optimization program. This part is called Learning Enabled Optimization (LEO), which is an approach combining statistical learning and stochastic optimization. The model is shown below:

![Image of LEO](https://github.com/xinyueniu/The-Wyndor-Glass-Co-Optimal-Advertising-Solutions-/blob/master/change.png)

𝑖 ≡ 𝑖𝑛𝑑𝑒𝑥𝑜𝑓𝑝𝑟𝑜𝑑𝑢𝑐𝑡,𝑖 ∈ {𝐴,𝐵}.

𝑦" ≡ 𝑛𝑢𝑚𝑏𝑒𝑟 𝑜𝑓 𝑏𝑎𝑡𝑐h𝑒𝑠 𝑜𝑓 𝑝𝑟𝑜𝑑𝑢𝑐𝑡 𝑖 𝑝𝑟𝑜𝑑𝑢𝑐𝑒𝑑

𝐿1,𝐿2 = 𝑡h𝑒 𝑚𝑖𝑛 𝑣𝑎𝑙𝑢𝑒 𝑜𝑓 𝑥1𝑖𝑛 𝑡h𝑒 𝑤h𝑜𝑙𝑒 𝑑𝑎𝑡𝑎 𝑠𝑒𝑡, 𝑡h𝑒 𝑚𝑖𝑛 𝑣𝑎𝑙𝑢𝑒 𝑜𝑓 𝑥2𝑖𝑛 𝑡h𝑒 𝑤h𝑜𝑙𝑒 𝑑𝑎𝑡𝑎 𝑠𝑒𝑡

𝑈1,𝑈2 = 𝑡h𝑒 𝑚𝑎𝑥 𝑣𝑎𝑙𝑢𝑒 𝑜𝑓 𝑥1𝑖𝑛 𝑡h𝑒 𝑤h𝑜𝑙𝑒 𝑑𝑎𝑡𝑎 𝑠𝑒𝑡, 𝑡h𝑒 𝑚𝑎𝑥 𝑣𝑎𝑙𝑢𝑒 𝑜𝑓 𝑥2𝑖𝑛 𝑡h𝑒 𝑤h𝑜𝑙𝑒 𝑑𝑎𝑡𝑎 𝑠𝑒𝑡

![Image of result](https://github.com/xinyueniu/The-Wyndor-Glass-Co-Optimal-Advertising-Solutions-/blob/master/result.png)

## Validation
### DF Model
For the training set for the deterministic forecasts, we received a set of determined values x1d and x2d, we plug them into optimization model.

![Image of de](https://github.com/xinyueniu/The-Wyndor-Glass-Co-Optimal-Advertising-Solutions-/blob/master/de.png)

Since the validation data set also has 100 samples, we have 100 objective values after calculation. Then, we found the 95% Confidence Interval of the objective values based on the dataset (of 100 values), which was calculated to be (46.180, 46.981). Since the 𝑜𝑏𝑗_𝑑𝑓 = 48.5077 do not exist inside of the CI. We cannot accept the solution that came from the deterministic forecasts.

### EAE Model
![Image of val](https://github.com/xinyueniu/The-Wyndor-Glass-Co-Optimal-Advertising-Solutions-/blob/master/val.png)

The training and validation datasets both have 100 𝜉 , we found 100 objective values after calculating for each set. We used the Chi-Square Test to verify whether there is a significant difference between these two group objective values. The null hypothesis is as follows: 𝐻n = 𝑡𝑤𝑜 𝑠𝑎𝑚𝑝𝑙𝑒𝑠 h𝑎𝑣𝑒 𝑠𝑎𝑚𝑒 𝑑𝑖𝑠𝑡𝑟𝑖𝑏𝑢𝑡𝑖𝑜𝑛. After performing the Chi-Square Test, we found our P- value to be 1, which means we cannot reject that these two samples have the same distribution.

## conclusion
Considering the consistency of training data set and validation data set, the DF model’s result is not qualified, and we agree that the outcome of EAE model is more accurate.
