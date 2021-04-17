# Kings County Housing Prices
### Using multilinear regression to predict the price of homes and recommend to homeowners the best ways to increase their home value. 

**Authors**: Ethan Kunin

The contents of this repository detail an analysis of the module one project. This analysis is detailed in hopes of making the work accessible and replicable.


### Business problem: 


King County home sales have been increasing as Seattle continues to grow. Top notch labor, and a favorable climate make King County a desirable place to live and work. Our real estate team has been tasked with advising clients on the best ways to increase their home value. This could mean renovation, expanding square footage, or other unique recommendations. We are also assisting them in determing a fair price for their home when they decide to put in on the market. 


### Data:
Data originates from Kaggle. 20,000+ rows and 20+ columns. CSV formatted. 


## Methods
- Scrubbed data to deal with duplicates and nulls
- Eliminated outliers using either IQR method or Z-scores
- Performed multiple multi-linear regression analyses to determine the most relevant features for determining a home's value. 



## Baseline Model



```python
model_base = model_summary(df, x_baseline, 'price')
sked_show(df, x_baseline, model_base)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.700</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.700</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2772.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:05</td>     <th>  Log-Likelihood:    </th> <td>-2.9152e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 21387</td>      <th>  AIC:               </th>  <td>5.831e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 21368</td>      <th>  BIC:               </th>  <td>5.832e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    18</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
        <td></td>           <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>     <td> 6.718e+06</td> <td> 2.96e+06</td> <td>    2.269</td> <td> 0.023</td> <td> 9.14e+05</td> <td> 1.25e+07</td>
</tr>
<tr>
  <th>bedrooms</th>      <td>-3.947e+04</td> <td> 1995.219</td> <td>  -19.782</td> <td> 0.000</td> <td>-4.34e+04</td> <td>-3.56e+04</td>
</tr>
<tr>
  <th>bathrooms</th>     <td> 4.386e+04</td> <td> 3311.837</td> <td>   13.242</td> <td> 0.000</td> <td> 3.74e+04</td> <td> 5.03e+04</td>
</tr>
<tr>
  <th>sqft_living</th>   <td>  154.0667</td> <td>    6.047</td> <td>   25.478</td> <td> 0.000</td> <td>  142.214</td> <td>  165.920</td>
</tr>
<tr>
  <th>sqft_lot</th>      <td>    0.1239</td> <td>    0.048</td> <td>    2.583</td> <td> 0.010</td> <td>    0.030</td> <td>    0.218</td>
</tr>
<tr>
  <th>floors</th>        <td> 6286.6806</td> <td> 3615.492</td> <td>    1.739</td> <td> 0.082</td> <td> -799.956</td> <td> 1.34e+04</td>
</tr>
<tr>
  <th>waterfront</th>    <td> 6.205e+05</td> <td> 1.82e+04</td> <td>   34.080</td> <td> 0.000</td> <td> 5.85e+05</td> <td> 6.56e+05</td>
</tr>
<tr>
  <th>view</th>          <td> 5.307e+04</td> <td> 2136.663</td> <td>   24.839</td> <td> 0.000</td> <td> 4.89e+04</td> <td> 5.73e+04</td>
</tr>
<tr>
  <th>condition</th>     <td> 2.632e+04</td> <td> 2366.782</td> <td>   11.121</td> <td> 0.000</td> <td> 2.17e+04</td> <td>  3.1e+04</td>
</tr>
<tr>
  <th>grade</th>         <td> 9.645e+04</td> <td> 2179.461</td> <td>   44.252</td> <td> 0.000</td> <td> 9.22e+04</td> <td> 1.01e+05</td>
</tr>
<tr>
  <th>sqft_above</th>    <td>   28.2441</td> <td>    6.608</td> <td>    4.274</td> <td> 0.000</td> <td>   15.292</td> <td>   41.196</td>
</tr>
<tr>
  <th>yr_built</th>      <td>-2657.3467</td> <td>   72.367</td> <td>  -36.721</td> <td> 0.000</td> <td>-2799.191</td> <td>-2515.502</td>
</tr>
<tr>
  <th>yr_renovated</th>  <td>   23.7180</td> <td>    3.995</td> <td>    5.936</td> <td> 0.000</td> <td>   15.887</td> <td>   31.549</td>
</tr>
<tr>
  <th>zipcode</th>       <td> -584.3960</td> <td>   33.219</td> <td>  -17.592</td> <td> 0.000</td> <td> -649.508</td> <td> -519.284</td>
</tr>
<tr>
  <th>lat</th>           <td> 6.002e+05</td> <td> 1.08e+04</td> <td>   55.637</td> <td> 0.000</td> <td> 5.79e+05</td> <td> 6.21e+05</td>
</tr>
<tr>
  <th>long</th>          <td>-2.177e+05</td> <td> 1.32e+04</td> <td>  -16.435</td> <td> 0.000</td> <td>-2.44e+05</td> <td>-1.92e+05</td>
</tr>
<tr>
  <th>sqft_living15</th> <td>   21.1994</td> <td>    3.464</td> <td>    6.119</td> <td> 0.000</td> <td>   14.409</td> <td>   27.990</td>
</tr>
<tr>
  <th>sqft_lot15</th>    <td>   -0.3950</td> <td>    0.073</td> <td>   -5.379</td> <td> 0.000</td> <td>   -0.539</td> <td>   -0.251</td>
</tr>
<tr>
  <th>basementyes</th>   <td>-2893.6903</td> <td> 5096.237</td> <td>   -0.568</td> <td> 0.570</td> <td>-1.29e+04</td> <td> 7095.317</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>18115.994</td> <th>  Durbin-Watson:     </th>  <td>   1.619</td>  
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>   <th>  Jarque-Bera (JB):  </th> <td>1802205.182</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 3.548</td>   <th>  Prob(JB):          </th>  <td>    0.00</td>  
</tr>
<tr>
  <th>Kurtosis:</th>       <td>47.408</td>   <th>  Cond. No.          </th>  <td>2.17e+08</td>  
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.17e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)



Insert images here
    
![png](output_37_2.png)
    

Insert images here

    
![png](output_37_3.png)
    


### Baseline Model Conclusion
- R^2 is 0.70
- QQ Plot deviates significantly around the 3rd quantile
- Floors and basement are not statistically significant
- Residuals trail off around $1.5 million, begins to become cone shaped
- Model not meet assumption of homoscedasticity

## EDA/New Feature Model

Explore adding new features to try and find significant relationships with price



 
EDA Results
- Price is right skewed
- Bedrooms increases up to 5/6 and then decreases
- Bathrooms increases with price
- Sqft living is right skewed and has a positive relationship with price
- Floors doesn't seem to have a relationship with price
- View doesn't seem to have a relationship with price
- Condition increases as price increases
- Grade increases as price increases
- Sqft above increases with price
- Year built doesn't have a relationship with price
- Year renovated looks equivalent
- Zipcode varies
- Sqft lot does not look linear


```python
# Total rooms
# Addition, multiplication would create too large of a SD. ie (2 beds 1 bath=3, 4 beds 1 bath=5)
df['total_rooms'] = df['bedrooms']+df['bathrooms']
```


```python
# Had erroniously stated 33 bedrooms and 1.5 bathrooms
# df=df.drop(15856)
df.sort_values(by='total_rooms', ascending=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>total_rooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8537</th>
      <td>424049043</td>
      <td>2014-08-11</td>
      <td>450000.00000</td>
      <td>9</td>
      <td>7.50000</td>
      <td>4050</td>
      <td>6504</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>7</td>
      <td>4050</td>
      <td>0.0</td>
      <td>1996</td>
      <td>0.00000</td>
      <td>98144</td>
      <td>47.59230</td>
      <td>-122.30100</td>
      <td>1448</td>
      <td>3866</td>
      <td>0</td>
      <td>16.50000</td>
    </tr>
    <tr>
      <th>13301</th>
      <td>627300145</td>
      <td>2014-08-14</td>
      <td>1150000.00000</td>
      <td>10</td>
      <td>5.25000</td>
      <td>4590</td>
      <td>10920</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>2.00000</td>
      <td>3</td>
      <td>9</td>
      <td>2500</td>
      <td>2090.0</td>
      <td>2008</td>
      <td>0.00000</td>
      <td>98004</td>
      <td>47.58610</td>
      <td>-122.11300</td>
      <td>2730</td>
      <td>10400</td>
      <td>1</td>
      <td>15.25000</td>
    </tr>
    <tr>
      <th>12764</th>
      <td>1225069038</td>
      <td>2014-05-05</td>
      <td>2280000.00000</td>
      <td>7</td>
      <td>8.00000</td>
      <td>13540</td>
      <td>307752</td>
      <td>3.00000</td>
      <td>0.00000</td>
      <td>4.00000</td>
      <td>3</td>
      <td>12</td>
      <td>9410</td>
      <td>4130.0</td>
      <td>1999</td>
      <td>0.00000</td>
      <td>98053</td>
      <td>47.66750</td>
      <td>-121.98600</td>
      <td>4850</td>
      <td>217800</td>
      <td>1</td>
      <td>15.00000</td>
    </tr>
    <tr>
      <th>8748</th>
      <td>1773100755</td>
      <td>2014-08-21</td>
      <td>520000.00000</td>
      <td>11</td>
      <td>3.00000</td>
      <td>3000</td>
      <td>4960</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>7</td>
      <td>2400</td>
      <td>600.0</td>
      <td>1918</td>
      <td>1999.00000</td>
      <td>98106</td>
      <td>47.55600</td>
      <td>-122.36300</td>
      <td>1420</td>
      <td>4960</td>
      <td>1</td>
      <td>14.00000</td>
    </tr>
    <tr>
      <th>7245</th>
      <td>6762700020</td>
      <td>2014-10-13</td>
      <td>7700000.00000</td>
      <td>6</td>
      <td>8.00000</td>
      <td>12050</td>
      <td>27600</td>
      <td>2.50000</td>
      <td>0.00000</td>
      <td>3.00000</td>
      <td>4</td>
      <td>13</td>
      <td>8570</td>
      <td>3480.0</td>
      <td>1910</td>
      <td>1987.00000</td>
      <td>98102</td>
      <td>47.62980</td>
      <td>-122.32300</td>
      <td>3940</td>
      <td>8800</td>
      <td>1</td>
      <td>14.00000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1973</th>
      <td>5101404170</td>
      <td>2014-11-13</td>
      <td>200000.00000</td>
      <td>1</td>
      <td>0.75000</td>
      <td>680</td>
      <td>9600</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>5</td>
      <td>680</td>
      <td>0.0</td>
      <td>1947</td>
      <td>0.00000</td>
      <td>98115</td>
      <td>47.69640</td>
      <td>-122.30600</td>
      <td>1580</td>
      <td>6624</td>
      <td>0</td>
      <td>1.75000</td>
    </tr>
    <tr>
      <th>9811</th>
      <td>3598600049</td>
      <td>2015-04-24</td>
      <td>224000.00000</td>
      <td>1</td>
      <td>0.75000</td>
      <td>840</td>
      <td>7203</td>
      <td>1.50000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>6</td>
      <td>840</td>
      <td>0.0</td>
      <td>1949</td>
      <td>0.00000</td>
      <td>98168</td>
      <td>47.47560</td>
      <td>-122.30100</td>
      <td>1560</td>
      <td>8603</td>
      <td>0</td>
      <td>1.75000</td>
    </tr>
    <tr>
      <th>8614</th>
      <td>6303400395</td>
      <td>2015-01-30</td>
      <td>325000.00000</td>
      <td>1</td>
      <td>0.75000</td>
      <td>410</td>
      <td>8636</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>2</td>
      <td>4</td>
      <td>410</td>
      <td>0.0</td>
      <td>1953</td>
      <td>0.00000</td>
      <td>98146</td>
      <td>47.50770</td>
      <td>-122.35700</td>
      <td>1190</td>
      <td>8636</td>
      <td>0</td>
      <td>1.75000</td>
    </tr>
    <tr>
      <th>10469</th>
      <td>7129304375</td>
      <td>2014-07-14</td>
      <td>202000.00000</td>
      <td>1</td>
      <td>0.75000</td>
      <td>590</td>
      <td>5650</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>6</td>
      <td>590</td>
      <td>0.0</td>
      <td>1944</td>
      <td>0.00000</td>
      <td>98118</td>
      <td>47.51810</td>
      <td>-122.26700</td>
      <td>980</td>
      <td>5650</td>
      <td>0</td>
      <td>1.75000</td>
    </tr>
    <tr>
      <th>11662</th>
      <td>7987400316</td>
      <td>2014-08-14</td>
      <td>255000.00000</td>
      <td>1</td>
      <td>0.50000</td>
      <td>880</td>
      <td>1642</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>6</td>
      <td>500</td>
      <td>380.0</td>
      <td>1910</td>
      <td>0.00000</td>
      <td>98126</td>
      <td>47.57320</td>
      <td>-122.37200</td>
      <td>1410</td>
      <td>2992</td>
      <td>1</td>
      <td>1.50000</td>
    </tr>
  </tbody>
</table>
<p>21387 rows × 23 columns</p>
</div>




```python
distr_(df, 'total_rooms')
```

    Total_rooms Summary
    Median: 5.5
    Mean: 5.49
    Max: 16.5
    Min: 1.5
    Std: 1.463



    
![png](output_45_1.png)
    



```python
# SQF vs. neighborhood average Living
df['living_vs_neighbor'] = df['sqft_living']/df['sqft_living15']
```


```python
distr_(df, 'living_vs_neighbor')
```

    Living_vs_neighbor Summary
    Median: 1.0
    Mean: 1.054
    Max: 6.0
    Min: 0.1872791519434629
    Std: 0.3203



    
![png](output_47_1.png)
    



```python
df['lot_vs_neighbor'] = df['sqft_lot']/df['sqft_lot15']
```


```python
distr_(df, 'lot_vs_neighbor')
```

    Lot_vs_neighbor Summary
    Median: 1.0
    Mean: 1.134
    Max: 87.52717948717948
    Min: 0.054971997700810314
    Std: 1.286



    
![png](output_49_1.png)
    



```python
# SQF vs. lot size
df['live_lot'] = df['sqft_living']/df['sqft_lot']
```


```python
distr_(df, 'live_lot')
```

    Live_lot Summary
    Median: 0.248
    Mean: 0.3244
    Max: 4.653846153846154
    Min: 0.0006095498431482305
    Std: 0.2692



    
![png](output_51_1.png)
    



```python
df['renovated_yes'] = (df['yr_renovated']!=0).map({True:1,
                                                   False: 0})
df['renovated_yes'].value_counts(1)
```




    0   0.96549
    1   0.03451
    Name: renovated_yes, dtype: float64




```python
# Homes that have been renovated have greater mean price

sns.barplot(data=df, x='renovated_yes', y='price', ci=68);
plt.show()
print(f"Has had renovation mean price: {round(df[df['renovated_yes']==1]['price'].mean(),2)}")
print(f"Has NOT had renovation mean price: {round(df[df['renovated_yes']==0]['price'].mean(),2)}")
```


    
![png](output_53_0.png)
    


    Has had renovation mean price: 770466.14
    Has NOT had renovation mean price: 532976.31



```python
X_feats = ['bedrooms', 'bathrooms', 'sqft_living',
           'sqft_lot', 'floors', 'waterfront', 'view',
           'condition', 'grade','sqft_above', 'yr_built',
           'sqft_living15', 'sqft_lot15', 'basementyes', 'zipcode',
           'lat', 'long', 'total_rooms', 'living_vs_neighbor',
           'lot_vs_neighbor','live_lot']

new_feat_model = model_summary(df, X_feats, 'price')
sked_show(df, X_feats, new_feat_model)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2614.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:30</td>     <th>  Log-Likelihood:    </th> <td>-2.9117e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 21387</td>      <th>  AIC:               </th>  <td>5.824e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 21366</td>      <th>  BIC:               </th>  <td>5.826e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    20</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 1.448e+07</td> <td> 2.95e+06</td> <td>    4.909</td> <td> 0.000</td> <td>  8.7e+06</td> <td> 2.03e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-3.551e+04</td> <td> 1866.090</td> <td>  -19.030</td> <td> 0.000</td> <td>-3.92e+04</td> <td>-3.19e+04</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 4.065e+04</td> <td> 2381.239</td> <td>   17.072</td> <td> 0.000</td> <td>  3.6e+04</td> <td> 4.53e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>  279.7819</td> <td>    7.979</td> <td>   35.066</td> <td> 0.000</td> <td>  264.143</td> <td>  295.421</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>    0.1747</td> <td>    0.061</td> <td>    2.884</td> <td> 0.004</td> <td>    0.056</td> <td>    0.293</td>
</tr>
<tr>
  <th>floors</th>             <td>-2.183e+04</td> <td> 4272.861</td> <td>   -5.109</td> <td> 0.000</td> <td>-3.02e+04</td> <td>-1.35e+04</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 6.235e+05</td> <td> 1.79e+04</td> <td>   34.785</td> <td> 0.000</td> <td> 5.88e+05</td> <td> 6.59e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 5.337e+04</td> <td> 2101.482</td> <td>   25.394</td> <td> 0.000</td> <td> 4.92e+04</td> <td> 5.75e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.584e+04</td> <td> 2301.904</td> <td>   11.224</td> <td> 0.000</td> <td> 2.13e+04</td> <td> 3.03e+04</td>
</tr>
<tr>
  <th>grade</th>              <td>  9.67e+04</td> <td> 2146.728</td> <td>   45.047</td> <td> 0.000</td> <td> 9.25e+04</td> <td> 1.01e+05</td>
</tr>
<tr>
  <th>sqft_above</th>         <td>   48.0559</td> <td>    6.555</td> <td>    7.332</td> <td> 0.000</td> <td>   35.208</td> <td>   60.903</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-2943.7297</td> <td>   69.090</td> <td>  -42.607</td> <td> 0.000</td> <td>-3079.151</td> <td>-2808.309</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td> -130.1541</td> <td>    7.326</td> <td>  -17.766</td> <td> 0.000</td> <td> -144.513</td> <td> -115.795</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>   -0.2132</td> <td>    0.084</td> <td>   -2.527</td> <td> 0.012</td> <td>   -0.379</td> <td>   -0.048</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-1581.4224</td> <td> 5109.472</td> <td>   -0.310</td> <td> 0.757</td> <td>-1.16e+04</td> <td> 8433.526</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -606.7536</td> <td>   32.743</td> <td>  -18.531</td> <td> 0.000</td> <td> -670.931</td> <td> -542.576</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.832e+05</td> <td> 1.07e+04</td> <td>   54.720</td> <td> 0.000</td> <td> 5.62e+05</td> <td> 6.04e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-1.857e+05</td> <td> 1.31e+04</td> <td>  -14.128</td> <td> 0.000</td> <td>-2.11e+05</td> <td> -1.6e+05</td>
</tr>
<tr>
  <th>total_rooms</th>        <td> 5139.3667</td> <td> 1157.167</td> <td>    4.441</td> <td> 0.000</td> <td> 2871.232</td> <td> 7407.501</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-2.953e+05</td> <td> 1.23e+04</td> <td>  -24.084</td> <td> 0.000</td> <td>-3.19e+05</td> <td>-2.71e+05</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> -739.6128</td> <td> 1374.112</td> <td>   -0.538</td> <td> 0.590</td> <td>-3432.976</td> <td> 1953.750</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 1.019e+05</td> <td> 7652.203</td> <td>   13.319</td> <td> 0.000</td> <td> 8.69e+04</td> <td> 1.17e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>16214.800</td> <th>  Durbin-Watson:     </th>  <td>   1.628</td>  
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>   <th>  Jarque-Bera (JB):  </th> <td>1099789.781</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 3.073</td>   <th>  Prob(JB):          </th>  <td>    0.00</td>  
</tr>
<tr>
  <th>Kurtosis:</th>       <td>37.589</td>   <th>  Cond. No.          </th>  <td>4.73e+17</td>  
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 9.7e-22. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_54_2.png)
    



    
![png](output_54_3.png)
    


### New Feature Model Conclusion
- R^2 imporved to 0.71
- Basementyes and lot_vs_neighbor are statistically insignificant
- Does not meet assumption of homoscedasticity
- Next step should be to remove outliers and run tests again

## Z-Score Outlier Removal
- Removing Z-Scores may address my issue of heteroskedacicity
- It will also reduce my right skew because values on the tails will be removed, especially on the right


```python
scaler = StandardScaler()
scaler
```




    StandardScaler()




```python
df_scaled = df.copy()
```


```python
# Don't need to scale locatation or binary variables

num_cols = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors','view', 'condition', 'grade',
       'sqft_above', 'yr_built','sqft_living15', 'sqft_lot15',
       'total_rooms', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot']
```


```python
df_scaled[num_cols] = scaler.fit_transform(df_scaled[num_cols])
df_scaled
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>total_rooms</th>
      <th>living_vs_neighbor</th>
      <th>lot_vs_neighbor</th>
      <th>live_lot</th>
      <th>renovated_yes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>2014-10-13</td>
      <td>221900.00000</td>
      <td>-0.41185</td>
      <td>-1.45459</td>
      <td>-0.98204</td>
      <td>-0.22816</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>-0.73673</td>
      <td>0.0</td>
      <td>-0.54875</td>
      <td>0.00000</td>
      <td>98178</td>
      <td>47.51120</td>
      <td>-122.25700</td>
      <td>-0.94499</td>
      <td>-0.26054</td>
      <td>0</td>
      <td>-1.01840</td>
      <td>-0.53992</td>
      <td>-0.10418</td>
      <td>-0.42942</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>2014-12-09</td>
      <td>538000.00000</td>
      <td>-0.41185</td>
      <td>0.17194</td>
      <td>0.53098</td>
      <td>-0.18985</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>0.45812</td>
      <td>400.0</td>
      <td>-0.68492</td>
      <td>1991.00000</td>
      <td>98125</td>
      <td>47.72100</td>
      <td>-122.31900</td>
      <td>-0.43431</td>
      <td>-0.18785</td>
      <td>1</td>
      <td>-0.16385</td>
      <td>1.45891</td>
      <td>-0.14459</td>
      <td>0.11312</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>2015-02-25</td>
      <td>180000.00000</td>
      <td>-1.51952</td>
      <td>-1.45459</td>
      <td>-1.42833</td>
      <td>-0.12349</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-1.41822</td>
      <td>-1.23157</td>
      <td>0.0</td>
      <td>-1.29771</td>
      <td>0.00000</td>
      <td>98028</td>
      <td>47.73790</td>
      <td>-122.23300</td>
      <td>1.06855</td>
      <td>-0.17239</td>
      <td>0</td>
      <td>-1.70204</td>
      <td>-2.40571</td>
      <td>0.08271</td>
      <td>-0.91929</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>2014-12-09</td>
      <td>604000.00000</td>
      <td>0.69582</td>
      <td>1.14785</td>
      <td>-0.13301</td>
      <td>-0.24380</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>2.44799</td>
      <td>-0.56451</td>
      <td>-0.89363</td>
      <td>910.0</td>
      <td>-0.20831</td>
      <td>0.00000</td>
      <td>98136</td>
      <td>47.52080</td>
      <td>-122.39300</td>
      <td>-0.91581</td>
      <td>-0.28429</td>
      <td>1</td>
      <td>1.03251</td>
      <td>1.21055</td>
      <td>-0.10418</td>
      <td>0.25105</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>2015-02-18</td>
      <td>510000.00000</td>
      <td>-0.41185</td>
      <td>-0.15337</td>
      <td>-0.43779</td>
      <td>-0.16969</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>0.28920</td>
      <td>-0.13327</td>
      <td>0.0</td>
      <td>0.54065</td>
      <td>0.00000</td>
      <td>98074</td>
      <td>47.61680</td>
      <td>-122.04500</td>
      <td>-0.27381</td>
      <td>-0.19282</td>
      <td>0</td>
      <td>-0.33476</td>
      <td>-0.37525</td>
      <td>-0.04439</td>
      <td>-0.43287</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21574</th>
      <td>7430200100</td>
      <td>2014-05-14</td>
      <td>1220000.00000</td>
      <td>0.69582</td>
      <td>1.79846</td>
      <td>3.07807</td>
      <td>-0.13687</td>
      <td>0.00814</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>2.85033</td>
      <td>1.59263</td>
      <td>1800.0</td>
      <td>1.22152</td>
      <td>0.00000</td>
      <td>98074</td>
      <td>47.65020</td>
      <td>-122.06600</td>
      <td>3.75328</td>
      <td>-0.06272</td>
      <td>1</td>
      <td>1.37433</td>
      <td>0.07260</td>
      <td>-0.21796</td>
      <td>0.72628</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21577</th>
      <td>8672200110</td>
      <td>2015-03-17</td>
      <td>1090000.00000</td>
      <td>1.80349</td>
      <td>2.12377</td>
      <td>2.27258</td>
      <td>-0.16819</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>2.31279</td>
      <td>-0.63136</td>
      <td>1.99662</td>
      <td>2.87197</td>
      <td>0.0</td>
      <td>1.18748</td>
      <td>0.00000</td>
      <td>98056</td>
      <td>47.53540</td>
      <td>-122.18100</td>
      <td>1.52087</td>
      <td>-0.17539</td>
      <td>0</td>
      <td>2.22888</td>
      <td>1.00777</td>
      <td>-0.08840</td>
      <td>0.69749</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21581</th>
      <td>191100405</td>
      <td>2015-04-21</td>
      <td>1580000.00000</td>
      <td>0.69582</td>
      <td>1.47316</td>
      <td>1.44532</td>
      <td>-0.12048</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>1.99662</td>
      <td>1.95471</td>
      <td>0.0</td>
      <td>1.22152</td>
      <td>0.00000</td>
      <td>98040</td>
      <td>47.56530</td>
      <td>-122.22300</td>
      <td>0.44114</td>
      <td>-0.09700</td>
      <td>0</td>
      <td>1.20342</td>
      <td>1.36015</td>
      <td>-0.10418</td>
      <td>0.04593</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21584</th>
      <td>249000205</td>
      <td>2014-10-15</td>
      <td>1540000.00000</td>
      <td>1.80349</td>
      <td>2.12377</td>
      <td>2.59913</td>
      <td>-0.16949</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>2.85033</td>
      <td>3.23404</td>
      <td>0.0</td>
      <td>1.25557</td>
      <td>0.00000</td>
      <td>98004</td>
      <td>47.63210</td>
      <td>-122.20000</td>
      <td>1.15610</td>
      <td>-0.13943</td>
      <td>0</td>
      <td>2.22888</td>
      <td>1.73121</td>
      <td>-0.18016</td>
      <td>0.84801</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21590</th>
      <td>7936000429</td>
      <td>2015-03-26</td>
      <td>1010000.00000</td>
      <td>0.69582</td>
      <td>1.79846</td>
      <td>1.55417</td>
      <td>-0.19086</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>1.14291</td>
      <td>0.97710</td>
      <td>910.0</td>
      <td>1.28961</td>
      <td>0.00000</td>
      <td>98136</td>
      <td>47.55370</td>
      <td>-122.39800</td>
      <td>0.09096</td>
      <td>-0.24044</td>
      <td>1</td>
      <td>1.37433</td>
      <td>2.05684</td>
      <td>0.02122</td>
      <td>0.60587</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>21387 rows × 27 columns</p>
</div>



Since everything is either continuous or binary, we don't need to one hot encode any variables at the moment


```python
# Run regression with standardized variables. See if there is any differernce
model_summary(df_scaled, X_feats, 'price')
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2614.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:31</td>     <th>  Log-Likelihood:    </th> <td>-2.9117e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 21387</td>      <th>  AIC:               </th>  <td>5.824e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 21366</td>      <th>  BIC:               </th>  <td>5.826e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    20</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 9.614e+06</td> <td>  2.9e+06</td> <td>    3.312</td> <td> 0.001</td> <td> 3.92e+06</td> <td> 1.53e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>  -2.8e+04</td> <td> 1554.158</td> <td>  -18.018</td> <td> 0.000</td> <td> -3.1e+04</td> <td> -2.5e+04</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 3.469e+04</td> <td> 2173.550</td> <td>   15.962</td> <td> 0.000</td> <td> 3.04e+04</td> <td>  3.9e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>  2.57e+05</td> <td> 7330.050</td> <td>   35.066</td> <td> 0.000</td> <td> 2.43e+05</td> <td> 2.71e+05</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td> 7259.1465</td> <td> 2516.721</td> <td>    2.884</td> <td> 0.004</td> <td> 2326.184</td> <td> 1.22e+04</td>
</tr>
<tr>
  <th>floors</th>             <td>-1.179e+04</td> <td> 2307.463</td> <td>   -5.109</td> <td> 0.000</td> <td>-1.63e+04</td> <td>-7265.691</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 6.235e+05</td> <td> 1.79e+04</td> <td>   34.785</td> <td> 0.000</td> <td> 5.88e+05</td> <td> 6.59e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 4.077e+04</td> <td> 1605.350</td> <td>   25.394</td> <td> 0.000</td> <td> 3.76e+04</td> <td> 4.39e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 1.678e+04</td> <td> 1495.057</td> <td>   11.224</td> <td> 0.000</td> <td> 1.39e+04</td> <td> 1.97e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 1.133e+05</td> <td> 2514.588</td> <td>   45.047</td> <td> 0.000</td> <td> 1.08e+05</td> <td> 1.18e+05</td>
</tr>
<tr>
  <th>sqft_above</th>         <td> 3.982e+04</td> <td> 5430.829</td> <td>    7.332</td> <td> 0.000</td> <td> 2.92e+04</td> <td> 5.05e+04</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-8.647e+04</td> <td> 2029.441</td> <td>  -42.607</td> <td> 0.000</td> <td>-9.04e+04</td> <td>-8.25e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td> -8.92e+04</td> <td> 5020.834</td> <td>  -17.766</td> <td> 0.000</td> <td> -9.9e+04</td> <td>-7.94e+04</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>-5834.7303</td> <td> 2309.407</td> <td>   -2.527</td> <td> 0.012</td> <td>-1.04e+04</td> <td>-1308.118</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-1581.4224</td> <td> 5109.472</td> <td>   -0.310</td> <td> 0.757</td> <td>-1.16e+04</td> <td> 8433.526</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -606.7536</td> <td>   32.743</td> <td>  -18.531</td> <td> 0.000</td> <td> -670.931</td> <td> -542.576</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.832e+05</td> <td> 1.07e+04</td> <td>   54.720</td> <td> 0.000</td> <td> 5.62e+05</td> <td> 6.04e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-1.857e+05</td> <td> 1.31e+04</td> <td>  -14.128</td> <td> 0.000</td> <td>-2.11e+05</td> <td> -1.6e+05</td>
</tr>
<tr>
  <th>total_rooms</th>        <td>  944.5443</td> <td>  934.600</td> <td>    1.011</td> <td> 0.312</td> <td> -887.342</td> <td> 2776.431</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-9.457e+04</td> <td> 3926.669</td> <td>  -24.084</td> <td> 0.000</td> <td>-1.02e+05</td> <td>-8.69e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> -951.3096</td> <td> 1767.420</td> <td>   -0.538</td> <td> 0.590</td> <td>-4415.585</td> <td> 2512.966</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 2.743e+04</td> <td> 2059.598</td> <td>   13.319</td> <td> 0.000</td> <td> 2.34e+04</td> <td> 3.15e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>16214.800</td> <th>  Durbin-Watson:     </th>  <td>   1.628</td>  
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>   <th>  Jarque-Bera (JB):  </th> <td>1099789.781</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 3.073</td>   <th>  Prob(JB):          </th>  <td>    0.00</td>  
</tr>
<tr>
  <th>Kurtosis:</th>       <td>37.589</td>   <th>  Cond. No.          </th>  <td>1.40e+18</td>  
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 1.05e-22. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    <statsmodels.regression.linear_model.RegressionResultsWrapper at 0x7fa2d10b5160>




    
![png](output_62_2.png)
    


Confirmed that standardized yields the same results as non-standardized


```python
# Scale Price and add onto outlier df
df_scaled2 = df_scaled.copy()
```


```python
df_scaled2['price'] = scaler.fit_transform(df_scaled2[['price']])
df_scaled2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>total_rooms</th>
      <th>living_vs_neighbor</th>
      <th>lot_vs_neighbor</th>
      <th>live_lot</th>
      <th>renovated_yes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>2014-10-13</td>
      <td>-0.86899</td>
      <td>-0.41185</td>
      <td>-1.45459</td>
      <td>-0.98204</td>
      <td>-0.22816</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>-0.73673</td>
      <td>0.0</td>
      <td>-0.54875</td>
      <td>0.00000</td>
      <td>98178</td>
      <td>47.51120</td>
      <td>-122.25700</td>
      <td>-0.94499</td>
      <td>-0.26054</td>
      <td>0</td>
      <td>-1.01840</td>
      <td>-0.53992</td>
      <td>-0.10418</td>
      <td>-0.42942</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>2014-12-09</td>
      <td>-0.00863</td>
      <td>-0.41185</td>
      <td>0.17194</td>
      <td>0.53098</td>
      <td>-0.18985</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>0.45812</td>
      <td>400.0</td>
      <td>-0.68492</td>
      <td>1991.00000</td>
      <td>98125</td>
      <td>47.72100</td>
      <td>-122.31900</td>
      <td>-0.43431</td>
      <td>-0.18785</td>
      <td>1</td>
      <td>-0.16385</td>
      <td>1.45891</td>
      <td>-0.14459</td>
      <td>0.11312</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>2015-02-25</td>
      <td>-0.98304</td>
      <td>-1.51952</td>
      <td>-1.45459</td>
      <td>-1.42833</td>
      <td>-0.12349</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-1.41822</td>
      <td>-1.23157</td>
      <td>0.0</td>
      <td>-1.29771</td>
      <td>0.00000</td>
      <td>98028</td>
      <td>47.73790</td>
      <td>-122.23300</td>
      <td>1.06855</td>
      <td>-0.17239</td>
      <td>0</td>
      <td>-1.70204</td>
      <td>-2.40571</td>
      <td>0.08271</td>
      <td>-0.91929</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>2014-12-09</td>
      <td>0.17101</td>
      <td>0.69582</td>
      <td>1.14785</td>
      <td>-0.13301</td>
      <td>-0.24380</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>2.44799</td>
      <td>-0.56451</td>
      <td>-0.89363</td>
      <td>910.0</td>
      <td>-0.20831</td>
      <td>0.00000</td>
      <td>98136</td>
      <td>47.52080</td>
      <td>-122.39300</td>
      <td>-0.91581</td>
      <td>-0.28429</td>
      <td>1</td>
      <td>1.03251</td>
      <td>1.21055</td>
      <td>-0.10418</td>
      <td>0.25105</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>2015-02-18</td>
      <td>-0.08484</td>
      <td>-0.41185</td>
      <td>-0.15337</td>
      <td>-0.43779</td>
      <td>-0.16969</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>0.28920</td>
      <td>-0.13327</td>
      <td>0.0</td>
      <td>0.54065</td>
      <td>0.00000</td>
      <td>98074</td>
      <td>47.61680</td>
      <td>-122.04500</td>
      <td>-0.27381</td>
      <td>-0.19282</td>
      <td>0</td>
      <td>-0.33476</td>
      <td>-0.37525</td>
      <td>-0.04439</td>
      <td>-0.43287</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21574</th>
      <td>7430200100</td>
      <td>2014-05-14</td>
      <td>1.84764</td>
      <td>0.69582</td>
      <td>1.79846</td>
      <td>3.07807</td>
      <td>-0.13687</td>
      <td>0.00814</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>2.85033</td>
      <td>1.59263</td>
      <td>1800.0</td>
      <td>1.22152</td>
      <td>0.00000</td>
      <td>98074</td>
      <td>47.65020</td>
      <td>-122.06600</td>
      <td>3.75328</td>
      <td>-0.06272</td>
      <td>1</td>
      <td>1.37433</td>
      <td>0.07260</td>
      <td>-0.21796</td>
      <td>0.72628</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21577</th>
      <td>8672200110</td>
      <td>2015-03-17</td>
      <td>1.49380</td>
      <td>1.80349</td>
      <td>2.12377</td>
      <td>2.27258</td>
      <td>-0.16819</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>2.31279</td>
      <td>-0.63136</td>
      <td>1.99662</td>
      <td>2.87197</td>
      <td>0.0</td>
      <td>1.18748</td>
      <td>0.00000</td>
      <td>98056</td>
      <td>47.53540</td>
      <td>-122.18100</td>
      <td>1.52087</td>
      <td>-0.17539</td>
      <td>0</td>
      <td>2.22888</td>
      <td>1.00777</td>
      <td>-0.08840</td>
      <td>0.69749</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21581</th>
      <td>191100405</td>
      <td>2015-04-21</td>
      <td>2.82749</td>
      <td>0.69582</td>
      <td>1.47316</td>
      <td>1.44532</td>
      <td>-0.12048</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>1.99662</td>
      <td>1.95471</td>
      <td>0.0</td>
      <td>1.22152</td>
      <td>0.00000</td>
      <td>98040</td>
      <td>47.56530</td>
      <td>-122.22300</td>
      <td>0.44114</td>
      <td>-0.09700</td>
      <td>0</td>
      <td>1.20342</td>
      <td>1.36015</td>
      <td>-0.10418</td>
      <td>0.04593</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21584</th>
      <td>249000205</td>
      <td>2014-10-15</td>
      <td>2.71862</td>
      <td>1.80349</td>
      <td>2.12377</td>
      <td>2.59913</td>
      <td>-0.16949</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>2.85033</td>
      <td>3.23404</td>
      <td>0.0</td>
      <td>1.25557</td>
      <td>0.00000</td>
      <td>98004</td>
      <td>47.63210</td>
      <td>-122.20000</td>
      <td>1.15610</td>
      <td>-0.13943</td>
      <td>0</td>
      <td>2.22888</td>
      <td>1.73121</td>
      <td>-0.18016</td>
      <td>0.84801</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21590</th>
      <td>7936000429</td>
      <td>2015-03-26</td>
      <td>1.27606</td>
      <td>0.69582</td>
      <td>1.79846</td>
      <td>1.55417</td>
      <td>-0.19086</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>1.14291</td>
      <td>0.97710</td>
      <td>910.0</td>
      <td>1.28961</td>
      <td>0.00000</td>
      <td>98136</td>
      <td>47.55370</td>
      <td>-122.39800</td>
      <td>0.09096</td>
      <td>-0.24044</td>
      <td>1</td>
      <td>1.37433</td>
      <td>2.05684</td>
      <td>0.02122</td>
      <td>0.60587</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>21387 rows × 27 columns</p>
</div>




```python
cols_to_check = ['price', 'bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'view', 'condition', 'grade',
       'sqft_above', 'yr_built', 'sqft_living15', 'sqft_lot15', 
       'total_rooms', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot']
```


```python
outliers_z = pd.DataFrame()

for col in cols_to_check:
    outliers_z[col] = df_scaled2[col].abs()>3

outliers_z['total'] = outliers_z.any(axis=1)
df_scaledz_orem = df_scaled[~outliers_z['total']].copy()
```


```python
df_scaledz_orem.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>total_rooms</th>
      <th>living_vs_neighbor</th>
      <th>lot_vs_neighbor</th>
      <th>live_lot</th>
      <th>renovated_yes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
      <td>18739.00000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4642413539.57815</td>
      <td>483952.00406</td>
      <td>-0.04684</td>
      <td>-0.11802</td>
      <td>-0.13537</td>
      <td>-0.12247</td>
      <td>-0.08184</td>
      <td>0.00027</td>
      <td>-0.17642</td>
      <td>0.02538</td>
      <td>-0.11964</td>
      <td>-0.11325</td>
      <td>-0.04140</td>
      <td>59.32921</td>
      <td>98077.57025</td>
      <td>47.55865</td>
      <td>-122.21411</td>
      <td>-0.09102</td>
      <td>-0.12234</td>
      <td>0.36501</td>
      <td>-0.09092</td>
      <td>-0.09671</td>
      <td>-0.05894</td>
      <td>-0.08101</td>
      <td>0.02972</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2864427156.31319</td>
      <td>234698.26149</td>
      <td>0.93754</td>
      <td>0.89297</td>
      <td>0.80788</td>
      <td>0.26986</td>
      <td>0.95007</td>
      <td>0.01633</td>
      <td>0.54277</td>
      <td>0.99882</td>
      <td>0.87434</td>
      <td>0.84950</td>
      <td>0.98689</td>
      <td>338.99128</td>
      <td>53.41876</td>
      <td>0.14070</td>
      <td>0.13789</td>
      <td>0.87702</td>
      <td>0.33910</td>
      <td>0.48145</td>
      <td>0.91097</td>
      <td>0.80957</td>
      <td>0.27328</td>
      <td>0.77142</td>
      <td>0.16983</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1000102.00000</td>
      <td>82500.00000</td>
      <td>-2.62718</td>
      <td>-2.10519</td>
      <td>-1.86373</td>
      <td>-0.34553</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-2.17104</td>
      <td>-2.27193</td>
      <td>-1.71434</td>
      <td>-2.42115</td>
      <td>0.00000</td>
      <td>98001.00000</td>
      <td>47.15590</td>
      <td>-122.51100</td>
      <td>-1.99554</td>
      <td>-0.44323</td>
      <td>0.00000</td>
      <td>-2.72750</td>
      <td>-2.43218</td>
      <td>-0.79723</td>
      <td>-1.17798</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2202500202.50000</td>
      <td>312000.00000</td>
      <td>-0.41185</td>
      <td>-0.80398</td>
      <td>-0.74257</td>
      <td>-0.24249</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>-0.74880</td>
      <td>-0.68492</td>
      <td>0.00000</td>
      <td>98033.00000</td>
      <td>47.46290</td>
      <td>-122.32600</td>
      <td>-0.74072</td>
      <td>-0.28064</td>
      <td>0.00000</td>
      <td>-0.67658</td>
      <td>-0.56570</td>
      <td>-0.14893</td>
      <td>-0.60972</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4019301386.00000</td>
      <td>434975.00000</td>
      <td>-0.41185</td>
      <td>-0.15337</td>
      <td>-0.25275</td>
      <td>-0.18364</td>
      <td>-0.91774</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>-0.63136</td>
      <td>-0.56451</td>
      <td>-0.33845</td>
      <td>0.02999</td>
      <td>0.00000</td>
      <td>98065.00000</td>
      <td>47.56950</td>
      <td>-122.22800</td>
      <td>-0.25922</td>
      <td>-0.19187</td>
      <td>0.00000</td>
      <td>0.00706</td>
      <td>-0.16707</td>
      <td>-0.10418</td>
      <td>-0.29794</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7348200155.00000</td>
      <td>600000.00000</td>
      <td>0.69582</td>
      <td>0.49724</td>
      <td>0.36770</td>
      <td>-0.12246</td>
      <td>0.93402</td>
      <td>0.00000</td>
      <td>-0.30530</td>
      <td>0.90831</td>
      <td>0.28920</td>
      <td>0.37364</td>
      <td>0.77895</td>
      <td>0.00000</td>
      <td>98117.00000</td>
      <td>47.68050</td>
      <td>-122.12800</td>
      <td>0.42655</td>
      <td>-0.11180</td>
      <td>1.00000</td>
      <td>0.69069</td>
      <td>0.25755</td>
      <td>-0.04133</td>
      <td>0.24014</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9900000190.00000</td>
      <td>1640000.00000</td>
      <td>2.91116</td>
      <td>2.77438</td>
      <td>2.94745</td>
      <td>2.87196</td>
      <td>2.78577</td>
      <td>1.00000</td>
      <td>2.31279</td>
      <td>2.44799</td>
      <td>2.85033</td>
      <td>2.99266</td>
      <td>1.49387</td>
      <td>2015.00000</td>
      <td>98199.00000</td>
      <td>47.77760</td>
      <td>-121.31500</td>
      <td>2.99455</td>
      <td>2.96184</td>
      <td>1.00000</td>
      <td>2.91252</td>
      <td>2.99458</td>
      <td>2.93377</td>
      <td>2.99903</td>
      <td>1.00000</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(f'Num observations before dropping with Z-score: {len(df_scaled2)}')
print('----Dropping all rows where an outlier occurrs accross columns----')
print(f'Num observations after dropping with Z-score: {len(df_scaledz_orem)}')
print(f'Num observations removed: {len(df_scaled2)-len(df_scaledz_orem)}')
print(f'Num observations removed as percent of original DF: {round(100*float(((len(df_scaled2)-len(df_scaledz_orem))/len(df_scaled2))),2)}%')
```

    Num observations before dropping with Z-score: 21387
    ----Dropping all rows where an outlier occurrs accross columns----
    Num observations after dropping with Z-score: 18739
    Num observations removed: 2648
    Num observations removed as percent of original DF: 12.38%



```python
print(f"Max price observation: {df_scaledz_orem['price'].max()}")
print(f"Min price observation: {df_scaledz_orem['price'].min()}")
```

    Max price observation: 1640000.0
    Min price observation: 82500.0



```python
df_scaledz_orem.drop('sqft_basement', axis=1, inplace=True)
```


```python
# Run regression to check QQ Plot

X_ztarg = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'sqft_above', 'yr_built', 'yr_renovated', 'zipcode', 'lat', 'long',
       'sqft_living15', 'sqft_lot15', 'basementyes', 'total_rooms',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot']
```


```python
model_scaled = model_summary(df_scaledz_orem, X_ztarg, 'price')
sked_show(df_scaledz_orem, X_ztarg, model_scaled)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.691</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.690</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1990.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:31</td>     <th>  Log-Likelihood:    </th> <td>-2.4732e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 18739</td>      <th>  AIC:               </th>  <td>4.947e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 18717</td>      <th>  BIC:               </th>  <td>4.949e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    21</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 4.016e+06</td> <td> 2.05e+06</td> <td>    1.957</td> <td> 0.050</td> <td>-6833.661</td> <td> 8.04e+06</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-1.132e+04</td> <td> 1157.201</td> <td>   -9.786</td> <td> 0.000</td> <td>-1.36e+04</td> <td>-9056.338</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.776e+04</td> <td> 1647.784</td> <td>   10.775</td> <td> 0.000</td> <td> 1.45e+04</td> <td>  2.1e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td> 6.617e+04</td> <td> 7532.499</td> <td>    8.785</td> <td> 0.000</td> <td> 5.14e+04</td> <td> 8.09e+04</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td> 1.221e+04</td> <td> 9876.679</td> <td>    1.236</td> <td> 0.216</td> <td>-7149.905</td> <td> 3.16e+04</td>
</tr>
<tr>
  <th>floors</th>             <td> -414.5743</td> <td> 1735.966</td> <td>   -0.239</td> <td> 0.811</td> <td>-3817.224</td> <td> 2988.076</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 2.804e+05</td> <td> 5.88e+04</td> <td>    4.771</td> <td> 0.000</td> <td> 1.65e+05</td> <td> 3.96e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 3.137e+04</td> <td> 1835.552</td> <td>   17.089</td> <td> 0.000</td> <td> 2.78e+04</td> <td>  3.5e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 1.861e+04</td> <td> 1073.157</td> <td>   17.338</td> <td> 0.000</td> <td> 1.65e+04</td> <td> 2.07e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 9.637e+04</td> <td> 1869.500</td> <td>   51.550</td> <td> 0.000</td> <td> 9.27e+04</td> <td>    1e+05</td>
</tr>
<tr>
  <th>sqft_above</th>         <td> 2.873e+04</td> <td> 4358.421</td> <td>    6.592</td> <td> 0.000</td> <td> 2.02e+04</td> <td> 3.73e+04</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-6.945e+04</td> <td> 1529.107</td> <td>  -45.419</td> <td> 0.000</td> <td>-7.24e+04</td> <td>-6.65e+04</td>
</tr>
<tr>
  <th>yr_renovated</th>       <td>   20.6159</td> <td>    2.954</td> <td>    6.980</td> <td> 0.000</td> <td>   14.826</td> <td>   26.406</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -379.2061</td> <td>   23.025</td> <td>  -16.469</td> <td> 0.000</td> <td> -424.337</td> <td> -334.075</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.459e+05</td> <td> 7417.778</td> <td>   73.599</td> <td> 0.000</td> <td> 5.31e+05</td> <td>  5.6e+05</td>
</tr>
<tr>
  <th>long</th>               <td> -6.32e+04</td> <td> 9439.522</td> <td>   -6.696</td> <td> 0.000</td> <td>-8.17e+04</td> <td>-4.47e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td> 3.048e+04</td> <td> 5306.531</td> <td>    5.745</td> <td> 0.000</td> <td> 2.01e+04</td> <td> 4.09e+04</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>-1556.0571</td> <td> 7627.760</td> <td>   -0.204</td> <td> 0.838</td> <td>-1.65e+04</td> <td> 1.34e+04</td>
</tr>
<tr>
  <th>basementyes</th>        <td> 1.284e+04</td> <td> 3834.671</td> <td>    3.347</td> <td> 0.001</td> <td> 5319.496</td> <td> 2.04e+04</td>
</tr>
<tr>
  <th>total_rooms</th>        <td> 2339.1522</td> <td>  716.156</td> <td>    3.266</td> <td> 0.001</td> <td>  935.422</td> <td> 3742.882</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-8634.9054</td> <td> 4391.496</td> <td>   -1.966</td> <td> 0.049</td> <td>-1.72e+04</td> <td>  -27.175</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 1.883e+04</td> <td> 5188.720</td> <td>    3.629</td> <td> 0.000</td> <td> 8661.320</td> <td>  2.9e+04</td>
</tr>
<tr>
  <th>live_lot</th>           <td>   3.7e+04</td> <td> 2068.873</td> <td>   17.885</td> <td> 0.000</td> <td> 3.29e+04</td> <td> 4.11e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>5315.173</td> <th>  Durbin-Watson:     </th> <td>   1.458</td> 
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>25047.224</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 1.305</td>  <th>  Prob(JB):          </th> <td>    0.00</td> 
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 8.026</td>  <th>  Cond. No.          </th> <td>7.04e+18</td> 
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 3.64e-24. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_73_2.png)
    



    
![png](output_73_3.png)
    


### Z-Score Outlier Removal Conclusion
- Our R^2 dropped to 0.691
- QQ plot is more normal
- Sqft_lot, floors, sqft_lot15 are insignificant
- Does not achieve homoscedasticity

## IQR Outlier Removal
- Checking if IQR outlier removal does a better job at normaling QQ plot and achieving homoscedasticity


```python
def find_outliers_IQR(data):
    """Detects outliers using the 1.5*IQR thresholds.
    Returns a boolean Series where True=outlier"""
    res = data.describe()
    q1 = res['25%']
    q3 = res['75%']
    thresh = 1.5*(q3-q1)
    idx_outliers =(data < (q1-thresh)) | (data > (q3+thresh))
    return idx_outliers
```


```python
df_iqr = df.copy()
```


```python
df_iqr.drop(['sqft_basement'], axis=1, inplace=True)
```


```python
# Only checking IQR outliers for columns that are continuous/ordinal

iqr_check = ['price', 'bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot','sqft_above', 'yr_built',
       'sqft_living15', 'sqft_lot15', 'total_rooms',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot']
```


```python
iqr_outliers = pd.DataFrame()
for col in iqr_check:
    iqr_outliers[col]=find_outliers_IQR(df_iqr[col])
iqr_outliers['total'] = iqr_outliers.any(axis=1)
df_iqr2 = df_iqr[~iqr_outliers['total']].copy()
```


```python
print(f'Num observations before dropping with IQR: {len(df_iqr)}')
print(f'Num observations after dropping with IQR: {len(df_iqr2)}')
print(f'Num observations removed: {len(df_iqr)-len(df_iqr2)}')
print(f'Num observations removed as percent of original DF: {(len(df_iqr)-len(df_iqr2))/len(df_iqr):.2}%')
```

    Num observations before dropping with IQR: 21387
    Num observations after dropping with IQR: 13389
    Num observations removed: 7998
    Num observations removed as percent of original DF: 0.37%



```python
print(f"Max price outliers removed: {df_iqr2['price'].max()}")
print(f"Min price outliers removed: {df_iqr2['price'].min()}")
```

    Max price outliers removed: 1120000.0
    Min price outliers removed: 81000.0



```python
df_iqr2.columns
iqr_pred = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'sqft_above', 'yr_built', 'yr_renovated', 'zipcode', 'lat', 'long',
       'sqft_living15', 'sqft_lot15', 'basementyes', 'total_rooms',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes']
```


```python
model_initiqr = model_summary(df_iqr2, iqr_pred, 'price')
sked_show(df_iqr2, iqr_pred, model_initiqr)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.711</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1494.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:32</td>     <th>  Log-Likelihood:    </th> <td>-1.7382e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 13389</td>      <th>  AIC:               </th>  <td>3.477e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 13366</td>      <th>  BIC:               </th>  <td>3.479e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    22</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 1.079e+07</td> <td> 2.01e+06</td> <td>    5.376</td> <td> 0.000</td> <td> 6.86e+06</td> <td> 1.47e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-1.074e+04</td> <td> 1417.675</td> <td>   -7.577</td> <td> 0.000</td> <td>-1.35e+04</td> <td>-7963.423</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.269e+04</td> <td> 1832.725</td> <td>    6.926</td> <td> 0.000</td> <td> 9100.199</td> <td> 1.63e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   33.1017</td> <td>   10.252</td> <td>    3.229</td> <td> 0.001</td> <td>   13.006</td> <td>   53.197</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>   -8.8020</td> <td>    2.871</td> <td>   -3.066</td> <td> 0.002</td> <td>  -14.429</td> <td>   -3.175</td>
</tr>
<tr>
  <th>floors</th>             <td> 8522.9111</td> <td> 3307.358</td> <td>    2.577</td> <td> 0.010</td> <td> 2040.021</td> <td>  1.5e+04</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.773e+05</td> <td> 3.26e+04</td> <td>    5.445</td> <td> 0.000</td> <td> 1.13e+05</td> <td> 2.41e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 3.315e+04</td> <td> 1771.516</td> <td>   18.714</td> <td> 0.000</td> <td> 2.97e+04</td> <td> 3.66e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 3.054e+04</td> <td> 1556.930</td> <td>   19.614</td> <td> 0.000</td> <td> 2.75e+04</td> <td> 3.36e+04</td>
</tr>
<tr>
  <th>grade</th>              <td>  6.86e+04</td> <td> 1636.795</td> <td>   41.911</td> <td> 0.000</td> <td> 6.54e+04</td> <td> 7.18e+04</td>
</tr>
<tr>
  <th>sqft_above</th>         <td>   26.1142</td> <td>    5.581</td> <td>    4.679</td> <td> 0.000</td> <td>   15.175</td> <td>   37.054</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-2228.5564</td> <td>   54.100</td> <td>  -41.193</td> <td> 0.000</td> <td>-2334.601</td> <td>-2122.512</td>
</tr>
<tr>
  <th>yr_renovated</th>       <td> 2585.2945</td> <td>  352.531</td> <td>    7.334</td> <td> 0.000</td> <td> 1894.285</td> <td> 3276.304</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -298.2342</td> <td>   21.562</td> <td>  -13.832</td> <td> 0.000</td> <td> -340.499</td> <td> -255.970</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.302e+05</td> <td> 6959.387</td> <td>   76.192</td> <td> 0.000</td> <td> 5.17e+05</td> <td> 5.44e+05</td>
</tr>
<tr>
  <th>long</th>               <td> 2.403e+04</td> <td> 9206.252</td> <td>    2.610</td> <td> 0.009</td> <td> 5982.584</td> <td> 4.21e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   80.5553</td> <td>    9.799</td> <td>    8.220</td> <td> 0.000</td> <td>   61.347</td> <td>   99.763</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    6.2593</td> <td>    3.000</td> <td>    2.087</td> <td> 0.037</td> <td>    0.380</td> <td>   12.139</td>
</tr>
<tr>
  <th>basementyes</th>        <td> 1.875e+04</td> <td> 3823.721</td> <td>    4.904</td> <td> 0.000</td> <td> 1.13e+04</td> <td> 2.62e+04</td>
</tr>
<tr>
  <th>total_rooms</th>        <td> 1950.3309</td> <td>  925.392</td> <td>    2.108</td> <td> 0.035</td> <td>  136.433</td> <td> 3764.229</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 1.667e+04</td> <td> 1.77e+04</td> <td>    0.939</td> <td> 0.348</td> <td>-1.81e+04</td> <td> 5.14e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 9.004e+04</td> <td> 2.41e+04</td> <td>    3.734</td> <td> 0.000</td> <td> 4.28e+04</td> <td> 1.37e+05</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 1.316e+05</td> <td> 1.65e+04</td> <td>    7.972</td> <td> 0.000</td> <td> 9.92e+04</td> <td> 1.64e+05</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td>-5.122e+06</td> <td> 7.04e+05</td> <td>   -7.276</td> <td> 0.000</td> <td> -6.5e+06</td> <td>-3.74e+06</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1308.382</td> <th>  Durbin-Watson:     </th> <td>   1.866</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>2687.128</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.634</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.791</td>  <th>  Cond. No.          </th> <td>3.92e+17</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 8.49e-22. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_84_2.png)
    



    
![png](output_84_3.png)
    


### IQR Outlier Removal Conclusion
- R^2 has increased to 0.71
- sqft_lot15 and living_vs_neighbor are insignificant
- QQ plot is significantly more normal. Small peak towards 2nd quantile
- homoscedasticity has improved because we have removed more outlier variables
- This model is working better but concerned that too much data has been removed (37%)

## Explore OHE Orindal Variables


```python
# Does not look like clear linear relationship between ordinal variables
# yr_built does not have a linear relationship
# lot_vs_neighbor does not have a linear relationship

def ordinal_check(df, col, val='price'):
    fig, axes = plt.subplots(ncols=2, figsize=(20,6))
    sns.stripplot(data=df, x=col, y=val, ax=axes[0])
    sns.barplot(data=df, x=col, y=val, ax=axes[1])

    fig.suptitle(f'Z-{col.upper()} vs. Price')
    plt.show()
    print('------------------------------------------------------------')
    print(df[col].value_counts(1))
```


```python
for col in ['floors', 'condition']:
    ordinal_check(df_iqr2, col)
```


    
![png](output_88_0.png)
    


    ------------------------------------------------------------
    1.00000   0.56853
    2.00000   0.34155
    1.50000   0.08447
    3.00000   0.00299
    2.50000   0.00246
    Name: floors, dtype: float64



    
![png](output_88_2.png)
    


    ------------------------------------------------------------
    3   0.62753
    4   0.28494
    5   0.07999
    2   0.00680
    1   0.00075
    Name: condition, dtype: float64



```python
# OHE: Floors/condition
from sklearn.preprocessing import OneHotEncoder
encoder = OneHotEncoder(sparse=False, drop='first')
encoder
```




    OneHotEncoder(drop='first', sparse=False)




```python
cat_cols=['floors', 'condition']
```


```python
encoder.fit(df_iqr2[cat_cols])

ohe_vars = encoder.transform(df_iqr2[cat_cols])
encoder.get_feature_names(cat_cols)
cat_vars = pd.DataFrame(ohe_vars,columns=encoder.get_feature_names(cat_cols))
```


```python
# Do this for formula OLS

name_dict = {}
for col in cat_vars.columns:
    name_dict[col]=col.replace('.','_')
name_dict
```




    {'floors_1.5': 'floors_1_5',
     'floors_2.0': 'floors_2_0',
     'floors_2.5': 'floors_2_5',
     'floors_3.0': 'floors_3_0',
     'condition_2': 'condition_2',
     'condition_3': 'condition_3',
     'condition_4': 'condition_4',
     'condition_5': 'condition_5'}




```python
cat_vars.rename(columns=name_dict, inplace=True)
cat_vars
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>floors_1_5</th>
      <th>floors_2_0</th>
      <th>floors_2_5</th>
      <th>floors_3_0</th>
      <th>condition_2</th>
      <th>condition_3</th>
      <th>condition_4</th>
      <th>condition_5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>13384</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>13385</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>13386</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>13387</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>13388</th>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
  </tbody>
</table>
<p>13389 rows × 8 columns</p>
</div>




```python
df_iqr2 = df_iqr2.reset_index()
```


```python
df_iqr2.drop('index', axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>total_rooms</th>
      <th>living_vs_neighbor</th>
      <th>lot_vs_neighbor</th>
      <th>live_lot</th>
      <th>renovated_yes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>2014-10-13</td>
      <td>221900.00000</td>
      <td>3</td>
      <td>1.00000</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>7</td>
      <td>1180</td>
      <td>1955</td>
      <td>0.00000</td>
      <td>98178</td>
      <td>47.51120</td>
      <td>-122.25700</td>
      <td>1340</td>
      <td>5650</td>
      <td>0</td>
      <td>4.00000</td>
      <td>0.88060</td>
      <td>1.00000</td>
      <td>0.20885</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>2014-12-09</td>
      <td>538000.00000</td>
      <td>3</td>
      <td>2.25000</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>7</td>
      <td>2170</td>
      <td>1951</td>
      <td>1991.00000</td>
      <td>98125</td>
      <td>47.72100</td>
      <td>-122.31900</td>
      <td>1690</td>
      <td>7639</td>
      <td>1</td>
      <td>5.25000</td>
      <td>1.52071</td>
      <td>0.94803</td>
      <td>0.35487</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2487200875</td>
      <td>2014-12-09</td>
      <td>604000.00000</td>
      <td>4</td>
      <td>3.00000</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>5</td>
      <td>7</td>
      <td>1050</td>
      <td>1965</td>
      <td>0.00000</td>
      <td>98136</td>
      <td>47.52080</td>
      <td>-122.39300</td>
      <td>1360</td>
      <td>5000</td>
      <td>1</td>
      <td>7.00000</td>
      <td>1.44118</td>
      <td>1.00000</td>
      <td>0.39200</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1954400510</td>
      <td>2015-02-18</td>
      <td>510000.00000</td>
      <td>3</td>
      <td>2.00000</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>8</td>
      <td>1680</td>
      <td>1987</td>
      <td>0.00000</td>
      <td>98074</td>
      <td>47.61680</td>
      <td>-122.04500</td>
      <td>1800</td>
      <td>7503</td>
      <td>0</td>
      <td>5.00000</td>
      <td>0.93333</td>
      <td>1.07690</td>
      <td>0.20792</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1321400060</td>
      <td>2014-06-27</td>
      <td>257500.00000</td>
      <td>3</td>
      <td>2.25000</td>
      <td>1715</td>
      <td>6819</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>7</td>
      <td>1715</td>
      <td>1995</td>
      <td>0.00000</td>
      <td>98003</td>
      <td>47.30970</td>
      <td>-122.32700</td>
      <td>2238</td>
      <td>6819</td>
      <td>0</td>
      <td>5.25000</td>
      <td>0.76631</td>
      <td>1.00000</td>
      <td>0.25150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>13384</th>
      <td>5556300109</td>
      <td>2014-11-21</td>
      <td>1080000.00000</td>
      <td>5</td>
      <td>3.50000</td>
      <td>3230</td>
      <td>7560</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>10</td>
      <td>3230</td>
      <td>2007</td>
      <td>0.00000</td>
      <td>98052</td>
      <td>47.64670</td>
      <td>-122.11800</td>
      <td>3230</td>
      <td>8580</td>
      <td>0</td>
      <td>8.50000</td>
      <td>1.00000</td>
      <td>0.88112</td>
      <td>0.42725</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13385</th>
      <td>1121000357</td>
      <td>2014-08-27</td>
      <td>1090000.00000</td>
      <td>4</td>
      <td>3.00000</td>
      <td>3410</td>
      <td>6541</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>2.00000</td>
      <td>3</td>
      <td>9</td>
      <td>2680</td>
      <td>2007</td>
      <td>0.00000</td>
      <td>98126</td>
      <td>47.54160</td>
      <td>-122.38000</td>
      <td>2300</td>
      <td>6345</td>
      <td>1</td>
      <td>7.00000</td>
      <td>1.48261</td>
      <td>1.03089</td>
      <td>0.52133</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13386</th>
      <td>2428100080</td>
      <td>2014-10-01</td>
      <td>1060000.00000</td>
      <td>4</td>
      <td>3.00000</td>
      <td>2990</td>
      <td>6695</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>10</td>
      <td>2990</td>
      <td>2014</td>
      <td>0.00000</td>
      <td>98075</td>
      <td>47.58170</td>
      <td>-122.04700</td>
      <td>2760</td>
      <td>6600</td>
      <td>0</td>
      <td>7.00000</td>
      <td>1.08333</td>
      <td>1.01439</td>
      <td>0.44660</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13387</th>
      <td>8924100308</td>
      <td>2015-02-03</td>
      <td>1050000.00000</td>
      <td>4</td>
      <td>2.50000</td>
      <td>3260</td>
      <td>5974</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>3</td>
      <td>9</td>
      <td>2820</td>
      <td>2007</td>
      <td>0.00000</td>
      <td>98115</td>
      <td>47.67720</td>
      <td>-122.26700</td>
      <td>2260</td>
      <td>6780</td>
      <td>1</td>
      <td>6.50000</td>
      <td>1.44248</td>
      <td>0.88112</td>
      <td>0.54570</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13388</th>
      <td>1070000180</td>
      <td>2014-10-15</td>
      <td>1110000.00000</td>
      <td>4</td>
      <td>3.50000</td>
      <td>3660</td>
      <td>4760</td>
      <td>2.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>3</td>
      <td>9</td>
      <td>2840</td>
      <td>2014</td>
      <td>0.00000</td>
      <td>98199</td>
      <td>47.64820</td>
      <td>-122.40900</td>
      <td>3210</td>
      <td>4640</td>
      <td>1</td>
      <td>7.50000</td>
      <td>1.14019</td>
      <td>1.02586</td>
      <td>0.76891</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>13389 rows × 26 columns</p>
</div>




```python
df_iqr3 = pd.concat([df_iqr2, cat_vars], axis=1)
```


```python
df_iqr3.drop('index', axis=1, inplace=True)
```


```python
df_iqr3.drop(['floors', 'condition'], axis=1, inplace=True)
```


```python
df_iqr3.columns
X_iqr_ohetargs = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'waterfront', 'view', 'grade', 'sqft_above', 'yr_built',
       'sqft_living15', 'sqft_lot15', 'basementyes', 'lat', 'long', 'zipcode',
       'total_rooms', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot',
       'renovated_yes', 'floors_1_5', 'floors_2_0', 'floors_2_5', 'floors_3_0',
       'condition_2', 'condition_3', 'condition_4', 'condition_5']
```


```python
model_iqr_ohe = model_summary(df_iqr3, X_iqr_ohetargs, 'price')
sked_show(df_iqr3, X_iqr_ohetargs, model_iqr_ohe)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.710</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1214.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:33</td>     <th>  Log-Likelihood:    </th> <td>-1.7383e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 13389</td>      <th>  AIC:               </th>  <td>3.477e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 13361</td>      <th>  BIC:               </th>  <td>3.479e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    27</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 1.099e+07</td> <td> 2.02e+06</td> <td>    5.436</td> <td> 0.000</td> <td> 7.03e+06</td> <td>  1.5e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>  -1.1e+04</td> <td> 1434.601</td> <td>   -7.669</td> <td> 0.000</td> <td>-1.38e+04</td> <td>-8190.320</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.355e+04</td> <td> 1846.498</td> <td>    7.338</td> <td> 0.000</td> <td> 9930.242</td> <td> 1.72e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   33.1515</td> <td>   10.297</td> <td>    3.219</td> <td> 0.001</td> <td>   12.967</td> <td>   53.336</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>   -8.3860</td> <td>    2.876</td> <td>   -2.916</td> <td> 0.004</td> <td>  -14.023</td> <td>   -2.749</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.668e+05</td> <td> 3.27e+04</td> <td>    5.098</td> <td> 0.000</td> <td> 1.03e+05</td> <td> 2.31e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 3.287e+04</td> <td> 1773.881</td> <td>   18.528</td> <td> 0.000</td> <td> 2.94e+04</td> <td> 3.63e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 6.896e+04</td> <td> 1639.266</td> <td>   42.066</td> <td> 0.000</td> <td> 6.57e+04</td> <td> 7.22e+04</td>
</tr>
<tr>
  <th>sqft_above</th>         <td>   27.3336</td> <td>    5.603</td> <td>    4.878</td> <td> 0.000</td> <td>   16.351</td> <td>   38.317</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-2227.4284</td> <td>   59.263</td> <td>  -37.585</td> <td> 0.000</td> <td>-2343.593</td> <td>-2111.264</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   80.7038</td> <td>    9.825</td> <td>    8.214</td> <td> 0.000</td> <td>   61.445</td> <td>   99.963</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    5.4835</td> <td>    3.009</td> <td>    1.823</td> <td> 0.068</td> <td>   -0.414</td> <td>   11.381</td>
</tr>
<tr>
  <th>basementyes</th>        <td>  1.86e+04</td> <td> 3829.436</td> <td>    4.856</td> <td> 0.000</td> <td> 1.11e+04</td> <td> 2.61e+04</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.284e+05</td> <td> 6979.865</td> <td>   75.705</td> <td> 0.000</td> <td> 5.15e+05</td> <td> 5.42e+05</td>
</tr>
<tr>
  <th>long</th>               <td> 2.767e+04</td> <td> 9251.223</td> <td>    2.991</td> <td> 0.003</td> <td> 9532.672</td> <td> 4.58e+04</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -293.9438</td> <td>   21.701</td> <td>  -13.545</td> <td> 0.000</td> <td> -336.480</td> <td> -251.408</td>
</tr>
<tr>
  <th>total_rooms</th>        <td> 2547.2981</td> <td>  928.401</td> <td>    2.744</td> <td> 0.006</td> <td>  727.500</td> <td> 4367.096</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 1.679e+04</td> <td> 1.78e+04</td> <td>    0.943</td> <td> 0.346</td> <td>-1.81e+04</td> <td> 5.17e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 8.398e+04</td> <td> 2.42e+04</td> <td>    3.473</td> <td> 0.001</td> <td> 3.66e+04</td> <td> 1.31e+05</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 1.249e+05</td> <td> 1.67e+04</td> <td>    7.497</td> <td> 0.000</td> <td> 9.23e+04</td> <td> 1.58e+05</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 4.054e+04</td> <td> 6152.271</td> <td>    6.590</td> <td> 0.000</td> <td> 2.85e+04</td> <td> 5.26e+04</td>
</tr>
<tr>
  <th>floors_1_5</th>         <td> 3584.6312</td> <td> 3947.122</td> <td>    0.908</td> <td> 0.364</td> <td>-4152.287</td> <td> 1.13e+04</td>
</tr>
<tr>
  <th>floors_2_0</th>         <td> 4048.4746</td> <td> 3456.091</td> <td>    1.171</td> <td> 0.241</td> <td>-2725.952</td> <td> 1.08e+04</td>
</tr>
<tr>
  <th>floors_2_5</th>         <td> 3.186e+04</td> <td> 1.87e+04</td> <td>    1.700</td> <td> 0.089</td> <td>-4875.663</td> <td> 6.86e+04</td>
</tr>
<tr>
  <th>floors_3_0</th>         <td> 9.493e+04</td> <td> 1.75e+04</td> <td>    5.434</td> <td> 0.000</td> <td> 6.07e+04</td> <td> 1.29e+05</td>
</tr>
<tr>
  <th>condition_2</th>        <td>-8029.1610</td> <td> 3.53e+04</td> <td>   -0.228</td> <td> 0.820</td> <td>-7.72e+04</td> <td> 6.11e+04</td>
</tr>
<tr>
  <th>condition_3</th>        <td> 1.355e+04</td> <td> 3.36e+04</td> <td>    0.404</td> <td> 0.686</td> <td>-5.23e+04</td> <td> 7.94e+04</td>
</tr>
<tr>
  <th>condition_4</th>        <td> 4.513e+04</td> <td> 3.36e+04</td> <td>    1.344</td> <td> 0.179</td> <td>-2.07e+04</td> <td> 1.11e+05</td>
</tr>
<tr>
  <th>condition_5</th>        <td> 7.294e+04</td> <td> 3.37e+04</td> <td>    2.165</td> <td> 0.030</td> <td> 6902.379</td> <td> 1.39e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1313.261</td> <th>  Durbin-Watson:     </th> <td>   1.865</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>2692.025</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.637</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.790</td>  <th>  Cond. No.          </th> <td>1.00e+16</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 1.3e-18. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_100_2.png)
    



    
![png](output_100_3.png)
    


### OHE Ordinal Conclusion
- R^2 of 0.71
- Majority of the OHE variables are not statistically significant so may drop them
- QQ plot looks normal
- Homoscedasticity looks passable

## Check assumptions of multicollinearity and correlation


```python
#https://nbviewer.jupyter.org/github/flatiron-school/Online-DS-FT-022221-Cohort-Notes/blob/master/Phase_2/topic_19_part1_multiple_regression/topic_19_Multiple_Regression_v2-SG.ipynb

df_iqr2.corr()['price'].round(2).sort_values(ascending=False)
```




    price                 1.00000
    grade                 0.58000
    sqft_living           0.57000
    sqft_living15         0.56000
    lat                   0.48000
    sqft_above            0.44000
    live_lot              0.40000
    bathrooms             0.38000
    total_rooms           0.37000
    bedrooms              0.27000
    floors                0.26000
    view                  0.24000
    basementyes           0.19000
    living_vs_neighbor    0.18000
    renovated_yes         0.09000
    yr_renovated          0.09000
    condition             0.07000
    waterfront            0.04000
    long                  0.04000
    index                 0.04000
    id                    0.03000
    zipcode               0.01000
    sqft_lot15           -0.01000
    lot_vs_neighbor      -0.01000
    yr_built             -0.02000
    sqft_lot             -0.02000
    Name: price, dtype: float64




```python
# https://heartbeat.fritz.ai/seaborn-heatmaps-13-ways-to-customize-correlation-matrix-visualizations-f1c49c816f07
corr2 = df_iqr2.corr()

fig, ax = plt.subplots(figsize=(15,15))
matrix = np.triu(corr2)
sns.heatmap(corr2,cmap="coolwarm", annot=True, fmt='.1g', mask=matrix)
```




    <AxesSubplot:>




    
![png](output_104_1.png)
    



```python
def corr_finder(df):
    df_corr = df.corr().abs().stack().reset_index().sort_values(0, ascending=False)
    df_corr['pairs'] = list(zip(df_corr.level_0, df_corr.level_1))
    df_corr.set_index(['pairs'], inplace = True)
    df_corr.drop(columns=['level_1', 'level_0'], inplace = True)

    # # cc for correlation coefficient
    df_corr.columns = ['cc']
    df_corr.drop_duplicates(inplace=True)

    return df_corr[(df_corr.cc>.75) & (df_corr.cc<1)]
```


```python
#https://github.com/learn-co-curriculum/dsc-multicollinearity-of-features-lab/tree/solution
corr_finder(df_iqr2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cc</th>
    </tr>
    <tr>
      <th>pairs</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(yr_renovated, renovated_yes)</th>
      <td>0.99997</td>
    </tr>
    <tr>
      <th>(sqft_lot15, sqft_lot)</th>
      <td>0.95056</td>
    </tr>
    <tr>
      <th>(total_rooms, bedrooms)</th>
      <td>0.89193</td>
    </tr>
    <tr>
      <th>(total_rooms, bathrooms)</th>
      <td>0.84303</td>
    </tr>
    <tr>
      <th>(sqft_living, sqft_above)</th>
      <td>0.82733</td>
    </tr>
    <tr>
      <th>(sqft_living15, sqft_living)</th>
      <td>0.82134</td>
    </tr>
    <tr>
      <th>(sqft_above, sqft_living15)</th>
      <td>0.76633</td>
    </tr>
    <tr>
      <th>(sqft_living, total_rooms)</th>
      <td>0.76241</td>
    </tr>
  </tbody>
</table>
</div>



Methodology will be to check each pair for correlation with price and drop the feature that 
has a lower correlation with price

- yr_renovated, renovated_yes: DROP - yr_renovated (should be dropped anyway)
- sqft_lot, sqft_lot15: DROP - sqft_lot15
- total_rooms, bedrooms: DROP - total rooms because it takes away from nuance of bath/bed
- bathrooms, total_rooms: DROP - total rooms because it takes away from nuance of bath/bed
- sqft_living, sqft_above: DROP - sqft_above
- sqft_living, sqft_living15: DROP - sqft_living_15
- sqft_above, sqft_living15: DROP - sqft_living_15
- sqft_living, total_rooms: DROP - total_rooms


```python
df_iqr_nocolin = df_iqr2.copy()
```


```python
cols_to_drop = ['index','yr_renovated', 'sqft_lot15', 'total_rooms', 'sqft_above', 'sqft_living15']
```


```python
df_iqr_nocolin.drop(columns=cols_to_drop, axis=1, inplace=True)
```


```python
df_iqr_nocolin.columns
X_nocolin_targs = ['bedrooms', 'bathrooms', 'sqft_living', 'zipcode', 'lat', 'long',
       'sqft_lot', 'waterfront', 'floors','view', 'condition', 'grade',
       'yr_built', 'basementyes', 'living_vs_neighbor', 'lot_vs_neighbor',
       'live_lot', 'renovated_yes']
```


```python
df_iqr_mult = model_summary(df_iqr_nocolin, X_nocolin_targs, 'price')
sked_show(df_iqr_nocolin, X_nocolin_targs, df_iqr_mult)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.708</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.707</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1797.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:34</td>     <th>  Log-Likelihood:    </th> <td>-1.7390e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 13389</td>      <th>  AIC:               </th>  <td>3.478e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 13370</td>      <th>  BIC:               </th>  <td>3.480e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    18</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 1.191e+07</td> <td> 2.02e+06</td> <td>    5.911</td> <td> 0.000</td> <td> 7.96e+06</td> <td> 1.59e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-7817.3073</td> <td> 1544.270</td> <td>   -5.062</td> <td> 0.000</td> <td>-1.08e+04</td> <td>-4790.320</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.595e+04</td> <td> 2529.363</td> <td>    6.308</td> <td> 0.000</td> <td>  1.1e+04</td> <td> 2.09e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>  128.6500</td> <td>    3.609</td> <td>   35.645</td> <td> 0.000</td> <td>  121.575</td> <td>  135.725</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -300.7249</td> <td>   21.672</td> <td>  -13.876</td> <td> 0.000</td> <td> -343.205</td> <td> -258.245</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.292e+05</td> <td> 6991.353</td> <td>   75.687</td> <td> 0.000</td> <td> 5.15e+05</td> <td> 5.43e+05</td>
</tr>
<tr>
  <th>long</th>               <td> 2.931e+04</td> <td> 9235.694</td> <td>    3.174</td> <td> 0.002</td> <td> 1.12e+04</td> <td> 4.74e+04</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>   -2.5561</td> <td>    0.687</td> <td>   -3.723</td> <td> 0.000</td> <td>   -3.902</td> <td>   -1.210</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.692e+05</td> <td> 3.27e+04</td> <td>    5.172</td> <td> 0.000</td> <td> 1.05e+05</td> <td> 2.33e+05</td>
</tr>
<tr>
  <th>floors</th>             <td> 1.365e+04</td> <td> 3129.711</td> <td>    4.361</td> <td> 0.000</td> <td> 7515.152</td> <td> 1.98e+04</td>
</tr>
<tr>
  <th>view</th>               <td> 3.275e+04</td> <td> 1766.349</td> <td>   18.543</td> <td> 0.000</td> <td> 2.93e+04</td> <td> 3.62e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.979e+04</td> <td> 1557.271</td> <td>   19.130</td> <td> 0.000</td> <td> 2.67e+04</td> <td> 3.28e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 7.188e+04</td> <td> 1617.272</td> <td>   44.444</td> <td> 0.000</td> <td> 6.87e+04</td> <td>  7.5e+04</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-2229.8463</td> <td>   54.306</td> <td>  -41.060</td> <td> 0.000</td> <td>-2336.295</td> <td>-2123.398</td>
</tr>
<tr>
  <th>basementyes</th>        <td> 6889.2197</td> <td> 2559.441</td> <td>    2.692</td> <td> 0.007</td> <td> 1872.353</td> <td> 1.19e+04</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-1.233e+05</td> <td> 5898.776</td> <td>  -20.903</td> <td> 0.000</td> <td>-1.35e+05</td> <td>-1.12e+05</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 4.218e+04</td> <td> 8755.287</td> <td>    4.817</td> <td> 0.000</td> <td>  2.5e+04</td> <td> 5.93e+04</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 1.282e+05</td> <td> 1.59e+04</td> <td>    8.056</td> <td> 0.000</td> <td>  9.7e+04</td> <td> 1.59e+05</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 3.964e+04</td> <td> 6145.803</td> <td>    6.450</td> <td> 0.000</td> <td> 2.76e+04</td> <td> 5.17e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1363.317</td> <th>  Durbin-Watson:     </th> <td>   1.870</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>2837.707</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.652</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.840</td>  <th>  Cond. No.          </th> <td>2.17e+08</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.17e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_113_2.png)
    



    
![png](output_113_3.png)
    


- R^2 of 0.708
- QQ plot looks normal
- No features with insignificant p-values
- homoscedasticity looks passable

Check Assumption of Linearity


```python
# Figure out how to delete empty axis

def lin_check(df, cols, ncols=4, figsize=(20,15)):
    fig, axes = plt.subplots(nrows=(len(cols)//ncols) +1, ncols=ncols, figsize=figsize)
    for ax, col in zip(axes.flatten(), cols):
        sns.regplot(data=df, x=col, y='price', ax=ax, line_kws={'color': 'red'})
        ax.set_title(f'{col} vs. price')
    fig.tight_layout()
```


```python
nocolin_cols = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'yr_built', 'basementyes', 'living_vs_neighbor', 'lot_vs_neighbor',
       'live_lot', 'renovated_yes']
## commenting out for speed

# lin_check(df_iqr_nocolin, nocolin_cols)
```

- sqft_lot does not have a linear relationship
- yr_built does not have a linear relationship
- lot_vs_neighbor does not have a linear relationship


```python
# comming out for speed
# X_iqr_nolin = ['bedrooms', 'bathrooms', 'sqft_living', 'lat', 'long',
#              'floors', 'waterfront', 'view', 'condition', 'grade', 'zipcode',
#              'basementyes', 'living_vs_neighbor',
#              'live_lot', 'renovated_yes']
# df_iqr_nocolin = model_summary(df_iqr_nocolin, X_iqr_nolin, 'price')
# sked_show(df_iqr_nocolin, X_iqr_nolin, df_iqr_nocolin)
```

### Linearity Conclusion
- R^2 has dropped to 0.67
- No insignificant p-values
- QQ plot looks normal
- Sked looks normal
- One of the features we dropped must have had a significant impact on our target variable

## Pivoting Back to Z-Score
- R^2 was reduced
- Testing if I can achieve similar results and drop less data


```python
df_z = df_scaledz_orem.copy()
df_z.drop('yr_renovated', axis=1, inplace=True)
```

## Check for multicolinearity

Not going to OHE the variables that were unsuccesful in IQR method



```python
# Check correlation
def initial_corr_check(df, col='price'):
    return df_z.corr()['price'].round(2).sort_values(ascending=False)
initial_corr_check(df_z)
```




    price                 1.00000
    grade                 0.63000
    sqft_living           0.62000
    sqft_living15         0.57000
    sqft_above            0.52000
    bathrooms             0.45000
    total_rooms           0.43000
    lat                   0.43000
    bedrooms              0.31000
    floors                0.28000
    living_vs_neighbor    0.24000
    live_lot              0.24000
    view                  0.20000
    basementyes           0.17000
    sqft_lot              0.10000
    renovated_yes         0.09000
    sqft_lot15            0.09000
    condition             0.05000
    long                  0.04000
    waterfront            0.03000
    yr_built              0.03000
    lot_vs_neighbor       0.03000
    id                    0.00000
    zipcode              -0.04000
    Name: price, dtype: float64




```python
def corr_triangle(df):
    corr2 = df.corr()

    fig, ax = plt.subplots(figsize=(15,15))
    matrix = np.triu(corr2)
    return sns.heatmap(corr2,cmap="coolwarm", annot=True, fmt='.1g', mask=matrix)
```


```python
corr_triangle(df_z)
```




    <AxesSubplot:>




    
![png](output_127_1.png)
    



```python
# To Drop based on mulitcolinearity:
# total_rooms, bedrooms -DROP total_rooms (nuance)
# sqft_lot, sqft_lot15 -DROP sqft_lot15
# sqft_living, sqft_above -DROP sqft_above
# bathrooms, total_rooms -DROP total_rooms(nuance)
# sqft_living, sqft_living15 -DROP sqft_living15
# total_rooms, sqft_living -DROP total_rooms

corr_finder(df_z)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cc</th>
    </tr>
    <tr>
      <th>pairs</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(total_rooms, bedrooms)</th>
      <td>0.89598</td>
    </tr>
    <tr>
      <th>(sqft_lot, sqft_lot15)</th>
      <td>0.85946</td>
    </tr>
    <tr>
      <th>(sqft_living, sqft_above)</th>
      <td>0.84780</td>
    </tr>
    <tr>
      <th>(total_rooms, bathrooms)</th>
      <td>0.83665</td>
    </tr>
    <tr>
      <th>(sqft_living, sqft_living15)</th>
      <td>0.77120</td>
    </tr>
    <tr>
      <th>(total_rooms, sqft_living)</th>
      <td>0.75943</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Confirm no more multicolinearity issues

corr_finder(df_z.drop(['total_rooms', 'sqft_lot15', 'sqft_above', 'sqft_living15'], axis=1))
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cc</th>
    </tr>
    <tr>
      <th>pairs</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
# It really doesn't look like there's a linear relationship between total rooms and price

sns.scatterplot(data=df_z, x='total_rooms', y='price', ci=68)
```




    <AxesSubplot:xlabel='total_rooms', ylabel='price'>




    
![png](output_130_1.png)
    



```python
df_z_multirem = df_z.copy()
```


```python
df_z_multirem.drop(['total_rooms', 'sqft_lot15', 'sqft_above', 'sqft_living15'], axis=1, inplace=True)
```


```python
df_z_multirem.columns
```




    Index(['id', 'date', 'price', 'bedrooms', 'bathrooms', 'sqft_living',
           'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
           'yr_built', 'zipcode', 'lat', 'long', 'basementyes',
           'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes'],
          dtype='object')




```python
X_multirem_targ = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'yr_built', 'zipcode', 'lat', 'long', 'basementyes',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes']
```


```python
model_z_multirem = model_summary(df_z_multirem, X_multirem_targ, 'price')
sked_show(df_z_multirem, X_multirem_targ, model_z_multirem)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.689</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.689</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2307.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:36</td>     <th>  Log-Likelihood:    </th> <td>-2.4737e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 18739</td>      <th>  AIC:               </th>  <td>4.948e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 18720</td>      <th>  BIC:               </th>  <td>4.949e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    18</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 4.959e+06</td> <td> 2.05e+06</td> <td>    2.416</td> <td> 0.016</td> <td> 9.35e+05</td> <td> 8.98e+06</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-9334.6716</td> <td> 1340.015</td> <td>   -6.966</td> <td> 0.000</td> <td> -1.2e+04</td> <td>-6708.121</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.906e+04</td> <td> 1899.762</td> <td>   10.035</td> <td> 0.000</td> <td> 1.53e+04</td> <td> 2.28e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td> 1.283e+05</td> <td> 2639.145</td> <td>   48.618</td> <td> 0.000</td> <td> 1.23e+05</td> <td> 1.33e+05</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td> 1.049e+04</td> <td> 4645.290</td> <td>    2.259</td> <td> 0.024</td> <td> 1387.974</td> <td> 1.96e+04</td>
</tr>
<tr>
  <th>floors</th>             <td> 3188.3390</td> <td> 1656.735</td> <td>    1.924</td> <td> 0.054</td> <td>  -59.012</td> <td> 6435.690</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 2.871e+05</td> <td> 5.88e+04</td> <td>    4.880</td> <td> 0.000</td> <td> 1.72e+05</td> <td> 4.02e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 3.077e+04</td> <td> 1832.840</td> <td>   16.789</td> <td> 0.000</td> <td> 2.72e+04</td> <td> 3.44e+04</td>
</tr>
<tr>
  <th>condition</th>          <td>   1.8e+04</td> <td> 1069.924</td> <td>   16.823</td> <td> 0.000</td> <td> 1.59e+04</td> <td> 2.01e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 9.956e+04</td> <td> 1841.327</td> <td>   54.071</td> <td> 0.000</td> <td>  9.6e+04</td> <td> 1.03e+05</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-6.969e+04</td> <td> 1531.649</td> <td>  -45.501</td> <td> 0.000</td> <td>-7.27e+04</td> <td>-6.67e+04</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -380.9131</td> <td>   23.048</td> <td>  -16.527</td> <td> 0.000</td> <td> -426.090</td> <td> -335.737</td>
</tr>
<tr>
  <th>lat</th>                <td>  5.45e+05</td> <td> 7428.578</td> <td>   73.367</td> <td> 0.000</td> <td>  5.3e+05</td> <td>  5.6e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-5.727e+04</td> <td> 9414.086</td> <td>   -6.084</td> <td> 0.000</td> <td>-7.57e+04</td> <td>-3.88e+04</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-5138.9456</td> <td> 2586.979</td> <td>   -1.986</td> <td> 0.047</td> <td>-1.02e+04</td> <td>  -68.231</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-3.315e+04</td> <td> 1610.973</td> <td>  -20.578</td> <td> 0.000</td> <td>-3.63e+04</td> <td>   -3e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 1.991e+04</td> <td> 3850.502</td> <td>    5.170</td> <td> 0.000</td> <td> 1.24e+04</td> <td> 2.75e+04</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 3.573e+04</td> <td> 1997.815</td> <td>   17.886</td> <td> 0.000</td> <td> 3.18e+04</td> <td> 3.96e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 4.104e+04</td> <td> 5905.364</td> <td>    6.949</td> <td> 0.000</td> <td> 2.95e+04</td> <td> 5.26e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>5305.167</td> <th>  Durbin-Watson:     </th> <td>   1.468</td> 
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>25198.882</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 1.300</td>  <th>  Prob(JB):          </th> <td>    0.00</td> 
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 8.051</td>  <th>  Cond. No.          </th> <td>2.11e+08</td> 
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.11e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_135_2.png)
    



    
![png](output_135_3.png)
    


### Multicolinearity Assumptions Conclusion
- R^2 is 68.8
- No statistically insignificant features but floors, basement, and sqft loss are close to threshold
- QQ plot seems passable
- Skedacity vears upward as price increases

## Check for Linearity and possible OHE


```python
df_z_multirem.columns
```




    Index(['id', 'date', 'price', 'bedrooms', 'bathrooms', 'sqft_living',
           'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
           'yr_built', 'zipcode', 'lat', 'long', 'basementyes',
           'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes'],
          dtype='object')




```python
## commenting out for speed
# z_multi_check = ['bedrooms', 'bathrooms', 'sqft_living',
#        'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
#        'yr_built', 'basementyes',
#        'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes']
# lin_check(df_z_multirem, z_multi_check)
```


```python
oridnal_cats = ['bedrooms', 'bathrooms', 'floors', 'condition', 'grade', 'basementyes', 'renovated_yes']
for col in oridnal_cats:
    print(ordinal_check(df_z_multirem, col))
    print('---------------------------------------------------------------------------------------')
```


    
![png](output_140_0.png)
    


    ------------------------------------------------------------
    -0.41185   0.46753
    0.69582    0.31901
    -1.51952   0.13064
    1.80349    0.06569
    2.91116    0.00881
    -2.62718   0.00832
    Name: bedrooms, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_2.png)
    


    ------------------------------------------------------------
    0.49724    0.25594
    -1.45459   0.19483
    -0.47867   0.14953
    0.17194    0.09600
    -0.15337   0.09387
    -0.80398   0.07108
    0.82255    0.05326
    1.14785    0.03004
    1.79846    0.02497
    1.47316    0.01953
    2.12377    0.00438
    -1.77989   0.00256
    2.44907    0.00245
    2.77438    0.00101
    -1.12928   0.00032
    -2.10519   0.00021
    Name: bathrooms, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_4.png)
    


    ------------------------------------------------------------
    -0.91774   0.52345
    0.93402    0.36539
    0.00814    0.08933
    2.78577    0.01724
    1.85990    0.00459
    Name: floors, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_6.png)
    


    ------------------------------------------------------------
    -0.63136   0.63915
    0.90831    0.27275
    2.44799    0.08063
    -2.17104   0.00747
    Name: condition, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_8.png)
    


    ------------------------------------------------------------
    -0.56451   0.44906
    0.28920    0.28246
    1.14291    0.11068
    -1.41822   0.10166
    1.99662    0.03869
    -2.27193   0.01115
    2.85033    0.00630
    Name: grade, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_10.png)
    


    ------------------------------------------------------------
    0   0.63499
    1   0.36501
    Name: basementyes, dtype: float64
    None
    ---------------------------------------------------------------------------------------



    
![png](output_140_12.png)
    


    ------------------------------------------------------------
    0   0.97028
    1   0.02972
    Name: renovated_yes, dtype: float64
    None
    ---------------------------------------------------------------------------------------


Most of the data apppears ordinal, floor is in between


```python
df_z_loc = df_z_multirem.copy()
```


```python
from sklearn.preprocessing import OneHotEncoder
encoder = OneHotEncoder(sparse=False, drop='first')
encoder
loc_col=['zipcode']
encoder.fit(df_z_loc[loc_col])

ohe_vars2 = encoder.transform(df_z_loc[loc_col])
encoder.get_feature_names(loc_col)
cat_vars2 = pd.DataFrame(ohe_vars2,columns=encoder.get_feature_names(loc_col))
```


```python
df_z_loc = df_z_loc.reset_index()
```


```python
df_z_loc2 = pd.concat([df_z_loc, cat_vars2], axis=1)
```


```python
df_z_loc2.drop('zipcode', axis=1, inplace=True)
```


```python
X_z_zip = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'waterfront', 'view', 'condition', 'grade',
       'basementyes', 'living_vs_neighbor',
       'live_lot', 'renovated_yes', 'zipcode_98002',
       'zipcode_98003', 'zipcode_98004', 'zipcode_98005', 'zipcode_98006',
       'zipcode_98007', 'zipcode_98008', 'zipcode_98010', 'zipcode_98011',
       'zipcode_98014', 'zipcode_98019', 'zipcode_98022', 'zipcode_98023',
       'zipcode_98024', 'zipcode_98027', 'zipcode_98028', 'zipcode_98029',
       'zipcode_98030', 'zipcode_98031', 'zipcode_98032', 'zipcode_98033',
       'zipcode_98034', 'zipcode_98038', 'zipcode_98039', 'zipcode_98040',
       'zipcode_98042', 'zipcode_98045', 'zipcode_98052', 'zipcode_98053',
       'zipcode_98055', 'zipcode_98056', 'zipcode_98058', 'zipcode_98059',
       'zipcode_98065', 'zipcode_98070', 'zipcode_98072', 'zipcode_98074',
       'zipcode_98075', 'zipcode_98077', 'zipcode_98092', 'zipcode_98102',
       'zipcode_98103', 'zipcode_98105', 'zipcode_98106', 'zipcode_98107',
       'zipcode_98108', 'zipcode_98109', 'zipcode_98112', 'zipcode_98115',
       'zipcode_98116', 'zipcode_98117', 'zipcode_98118', 'zipcode_98119',
       'zipcode_98122', 'zipcode_98125', 'zipcode_98126', 'zipcode_98133',
       'zipcode_98136', 'zipcode_98144', 'zipcode_98146', 'zipcode_98148',
       'zipcode_98155', 'zipcode_98166', 'zipcode_98168', 'zipcode_98177',
       'zipcode_98178', 'zipcode_98188', 'zipcode_98198', 'zipcode_98199']
```


```python
model_zip = model_summary(df_z_loc2, X_z_zip, 'price')
sked_show(df_z_loc2, X_z_zip, model_zip)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.834</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.833</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1155.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:33:24</td>     <th>  Log-Likelihood:    </th> <td>-2.4150e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 18739</td>      <th>  AIC:               </th>  <td>4.832e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 18657</td>      <th>  BIC:               </th>  <td>4.838e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    81</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 3.335e+05</td> <td> 5231.768</td> <td>   63.751</td> <td> 0.000</td> <td> 3.23e+05</td> <td> 3.44e+05</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-4799.7959</td> <td>  993.515</td> <td>   -4.831</td> <td> 0.000</td> <td>-6747.175</td> <td>-2852.417</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.159e+04</td> <td> 1298.460</td> <td>    8.926</td> <td> 0.000</td> <td> 9044.455</td> <td> 1.41e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td> 1.358e+05</td> <td> 1989.241</td> <td>   68.292</td> <td> 0.000</td> <td> 1.32e+05</td> <td>  1.4e+05</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td> 9088.8315</td> <td> 3433.998</td> <td>    2.647</td> <td> 0.008</td> <td> 2357.883</td> <td> 1.58e+04</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 3.122e+05</td> <td> 4.39e+04</td> <td>    7.118</td> <td> 0.000</td> <td> 2.26e+05</td> <td> 3.98e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 2.852e+04</td> <td> 1364.353</td> <td>   20.906</td> <td> 0.000</td> <td> 2.58e+04</td> <td> 3.12e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 1.737e+04</td> <td>  762.430</td> <td>   22.777</td> <td> 0.000</td> <td> 1.59e+04</td> <td> 1.89e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 5.778e+04</td> <td> 1367.940</td> <td>   42.239</td> <td> 0.000</td> <td> 5.51e+04</td> <td> 6.05e+04</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-1.958e+04</td> <td> 1668.359</td> <td>  -11.734</td> <td> 0.000</td> <td>-2.28e+04</td> <td>-1.63e+04</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-1.675e+04</td> <td> 1218.191</td> <td>  -13.748</td> <td> 0.000</td> <td>-1.91e+04</td> <td>-1.44e+04</td>
</tr>
<tr>
  <th>live_lot</th>           <td>-2.295e+04</td> <td> 1388.951</td> <td>  -16.521</td> <td> 0.000</td> <td>-2.57e+04</td> <td>-2.02e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 4.874e+04</td> <td> 4204.833</td> <td>   11.591</td> <td> 0.000</td> <td> 4.05e+04</td> <td>  5.7e+04</td>
</tr>
<tr>
  <th>zipcode_98002</th>      <td> 2.332e+04</td> <td> 8761.321</td> <td>    2.661</td> <td> 0.008</td> <td> 6144.628</td> <td> 4.05e+04</td>
</tr>
<tr>
  <th>zipcode_98003</th>      <td>-5676.1759</td> <td> 7829.908</td> <td>   -0.725</td> <td> 0.469</td> <td> -2.1e+04</td> <td> 9671.157</td>
</tr>
<tr>
  <th>zipcode_98004</th>      <td> 6.196e+05</td> <td> 8452.354</td> <td>   73.308</td> <td> 0.000</td> <td> 6.03e+05</td> <td> 6.36e+05</td>
</tr>
<tr>
  <th>zipcode_98005</th>      <td> 3.232e+05</td> <td> 9507.683</td> <td>   33.989</td> <td> 0.000</td> <td> 3.05e+05</td> <td> 3.42e+05</td>
</tr>
<tr>
  <th>zipcode_98006</th>      <td> 2.621e+05</td> <td> 7254.603</td> <td>   36.122</td> <td> 0.000</td> <td> 2.48e+05</td> <td> 2.76e+05</td>
</tr>
<tr>
  <th>zipcode_98007</th>      <td> 2.568e+05</td> <td> 9800.795</td> <td>   26.205</td> <td> 0.000</td> <td> 2.38e+05</td> <td> 2.76e+05</td>
</tr>
<tr>
  <th>zipcode_98008</th>      <td> 2.409e+05</td> <td> 7946.681</td> <td>   30.314</td> <td> 0.000</td> <td> 2.25e+05</td> <td> 2.56e+05</td>
</tr>
<tr>
  <th>zipcode_98010</th>      <td> 7.886e+04</td> <td> 1.21e+04</td> <td>    6.506</td> <td> 0.000</td> <td> 5.51e+04</td> <td> 1.03e+05</td>
</tr>
<tr>
  <th>zipcode_98011</th>      <td> 1.404e+05</td> <td> 8736.400</td> <td>   16.074</td> <td> 0.000</td> <td> 1.23e+05</td> <td> 1.58e+05</td>
</tr>
<tr>
  <th>zipcode_98014</th>      <td> 1.016e+05</td> <td>  1.2e+04</td> <td>    8.457</td> <td> 0.000</td> <td>  7.8e+04</td> <td> 1.25e+05</td>
</tr>
<tr>
  <th>zipcode_98019</th>      <td> 8.452e+04</td> <td> 9098.027</td> <td>    9.290</td> <td> 0.000</td> <td> 6.67e+04</td> <td> 1.02e+05</td>
</tr>
<tr>
  <th>zipcode_98022</th>      <td> 2065.8914</td> <td> 9039.029</td> <td>    0.229</td> <td> 0.819</td> <td>-1.57e+04</td> <td> 1.98e+04</td>
</tr>
<tr>
  <th>zipcode_98023</th>      <td>-2.377e+04</td> <td> 6800.636</td> <td>   -3.495</td> <td> 0.000</td> <td>-3.71e+04</td> <td>-1.04e+04</td>
</tr>
<tr>
  <th>zipcode_98024</th>      <td> 1.446e+05</td> <td> 1.53e+04</td> <td>    9.473</td> <td> 0.000</td> <td> 1.15e+05</td> <td> 1.75e+05</td>
</tr>
<tr>
  <th>zipcode_98027</th>      <td> 1.877e+05</td> <td> 7563.515</td> <td>   24.814</td> <td> 0.000</td> <td> 1.73e+05</td> <td> 2.03e+05</td>
</tr>
<tr>
  <th>zipcode_98028</th>      <td> 1.313e+05</td> <td> 7830.483</td> <td>   16.762</td> <td> 0.000</td> <td> 1.16e+05</td> <td> 1.47e+05</td>
</tr>
<tr>
  <th>zipcode_98029</th>      <td> 2.276e+05</td> <td> 7677.976</td> <td>   29.650</td> <td> 0.000</td> <td> 2.13e+05</td> <td> 2.43e+05</td>
</tr>
<tr>
  <th>zipcode_98030</th>      <td> 1463.5199</td> <td> 8040.642</td> <td>    0.182</td> <td> 0.856</td> <td>-1.43e+04</td> <td> 1.72e+04</td>
</tr>
<tr>
  <th>zipcode_98031</th>      <td> 7674.6113</td> <td> 7896.872</td> <td>    0.972</td> <td> 0.331</td> <td>-7803.978</td> <td> 2.32e+04</td>
</tr>
<tr>
  <th>zipcode_98032</th>      <td>  611.8492</td> <td> 1.02e+04</td> <td>    0.060</td> <td> 0.952</td> <td>-1.94e+04</td> <td> 2.06e+04</td>
</tr>
<tr>
  <th>zipcode_98033</th>      <td> 3.461e+05</td> <td> 7157.820</td> <td>   48.357</td> <td> 0.000</td> <td> 3.32e+05</td> <td>  3.6e+05</td>
</tr>
<tr>
  <th>zipcode_98034</th>      <td> 1.885e+05</td> <td> 6705.274</td> <td>   28.116</td> <td> 0.000</td> <td> 1.75e+05</td> <td> 2.02e+05</td>
</tr>
<tr>
  <th>zipcode_98038</th>      <td> 2.881e+04</td> <td> 6659.284</td> <td>    4.327</td> <td> 0.000</td> <td> 1.58e+04</td> <td> 4.19e+04</td>
</tr>
<tr>
  <th>zipcode_98039</th>      <td> 8.455e+05</td> <td> 2.53e+04</td> <td>   33.374</td> <td> 0.000</td> <td> 7.96e+05</td> <td> 8.95e+05</td>
</tr>
<tr>
  <th>zipcode_98040</th>      <td> 4.732e+05</td> <td> 8529.047</td> <td>   55.482</td> <td> 0.000</td> <td> 4.56e+05</td> <td>  4.9e+05</td>
</tr>
<tr>
  <th>zipcode_98042</th>      <td>  426.3775</td> <td> 6673.223</td> <td>    0.064</td> <td> 0.949</td> <td>-1.27e+04</td> <td> 1.35e+04</td>
</tr>
<tr>
  <th>zipcode_98045</th>      <td> 1.015e+05</td> <td> 8759.146</td> <td>   11.589</td> <td> 0.000</td> <td> 8.43e+04</td> <td> 1.19e+05</td>
</tr>
<tr>
  <th>zipcode_98052</th>      <td> 2.503e+05</td> <td> 6659.742</td> <td>   37.585</td> <td> 0.000</td> <td> 2.37e+05</td> <td> 2.63e+05</td>
</tr>
<tr>
  <th>zipcode_98053</th>      <td> 2.297e+05</td> <td> 7440.215</td> <td>   30.875</td> <td> 0.000</td> <td> 2.15e+05</td> <td> 2.44e+05</td>
</tr>
<tr>
  <th>zipcode_98055</th>      <td> 4.888e+04</td> <td> 8056.651</td> <td>    6.067</td> <td> 0.000</td> <td> 3.31e+04</td> <td> 6.47e+04</td>
</tr>
<tr>
  <th>zipcode_98056</th>      <td> 1.032e+05</td> <td> 7144.537</td> <td>   14.441</td> <td> 0.000</td> <td> 8.92e+04</td> <td> 1.17e+05</td>
</tr>
<tr>
  <th>zipcode_98058</th>      <td> 3.033e+04</td> <td> 6943.907</td> <td>    4.368</td> <td> 0.000</td> <td> 1.67e+04</td> <td> 4.39e+04</td>
</tr>
<tr>
  <th>zipcode_98059</th>      <td> 9.517e+04</td> <td> 7007.389</td> <td>   13.581</td> <td> 0.000</td> <td> 8.14e+04</td> <td> 1.09e+05</td>
</tr>
<tr>
  <th>zipcode_98065</th>      <td> 1.246e+05</td> <td> 7877.512</td> <td>   15.814</td> <td> 0.000</td> <td> 1.09e+05</td> <td>  1.4e+05</td>
</tr>
<tr>
  <th>zipcode_98070</th>      <td> 1.151e+05</td> <td>  1.5e+04</td> <td>    7.651</td> <td> 0.000</td> <td> 8.56e+04</td> <td> 1.45e+05</td>
</tr>
<tr>
  <th>zipcode_98072</th>      <td> 1.698e+05</td> <td> 8051.760</td> <td>   21.088</td> <td> 0.000</td> <td> 1.54e+05</td> <td> 1.86e+05</td>
</tr>
<tr>
  <th>zipcode_98074</th>      <td>  2.06e+05</td> <td> 7174.814</td> <td>   28.714</td> <td> 0.000</td> <td> 1.92e+05</td> <td>  2.2e+05</td>
</tr>
<tr>
  <th>zipcode_98075</th>      <td>  2.15e+05</td> <td> 7725.463</td> <td>   27.833</td> <td> 0.000</td> <td>    2e+05</td> <td>  2.3e+05</td>
</tr>
<tr>
  <th>zipcode_98077</th>      <td> 1.477e+05</td> <td> 9398.804</td> <td>   15.717</td> <td> 0.000</td> <td> 1.29e+05</td> <td> 1.66e+05</td>
</tr>
<tr>
  <th>zipcode_98092</th>      <td> -3.04e+04</td> <td> 7555.037</td> <td>   -4.023</td> <td> 0.000</td> <td>-4.52e+04</td> <td>-1.56e+04</td>
</tr>
<tr>
  <th>zipcode_98102</th>      <td> 4.908e+05</td> <td> 1.25e+04</td> <td>   39.143</td> <td> 0.000</td> <td> 4.66e+05</td> <td> 5.15e+05</td>
</tr>
<tr>
  <th>zipcode_98103</th>      <td> 3.694e+05</td> <td> 6937.483</td> <td>   53.247</td> <td> 0.000</td> <td> 3.56e+05</td> <td> 3.83e+05</td>
</tr>
<tr>
  <th>zipcode_98105</th>      <td> 4.598e+05</td> <td> 8847.856</td> <td>   51.962</td> <td> 0.000</td> <td> 4.42e+05</td> <td> 4.77e+05</td>
</tr>
<tr>
  <th>zipcode_98106</th>      <td> 1.457e+05</td> <td> 7739.809</td> <td>   18.828</td> <td> 0.000</td> <td> 1.31e+05</td> <td> 1.61e+05</td>
</tr>
<tr>
  <th>zipcode_98107</th>      <td> 3.532e+05</td> <td> 8467.745</td> <td>   41.707</td> <td> 0.000</td> <td> 3.37e+05</td> <td>  3.7e+05</td>
</tr>
<tr>
  <th>zipcode_98108</th>      <td> 1.409e+05</td> <td> 9013.777</td> <td>   15.631</td> <td> 0.000</td> <td> 1.23e+05</td> <td> 1.59e+05</td>
</tr>
<tr>
  <th>zipcode_98109</th>      <td>  5.19e+05</td> <td> 1.17e+04</td> <td>   44.290</td> <td> 0.000</td> <td> 4.96e+05</td> <td> 5.42e+05</td>
</tr>
<tr>
  <th>zipcode_98112</th>      <td> 5.653e+05</td> <td> 8799.840</td> <td>   64.245</td> <td> 0.000</td> <td> 5.48e+05</td> <td> 5.83e+05</td>
</tr>
<tr>
  <th>zipcode_98115</th>      <td> 3.512e+05</td> <td> 6752.068</td> <td>   52.011</td> <td> 0.000</td> <td> 3.38e+05</td> <td> 3.64e+05</td>
</tr>
<tr>
  <th>zipcode_98116</th>      <td> 3.195e+05</td> <td> 8004.311</td> <td>   39.916</td> <td> 0.000</td> <td> 3.04e+05</td> <td> 3.35e+05</td>
</tr>
<tr>
  <th>zipcode_98117</th>      <td> 3.439e+05</td> <td> 6859.349</td> <td>   50.129</td> <td> 0.000</td> <td>  3.3e+05</td> <td> 3.57e+05</td>
</tr>
<tr>
  <th>zipcode_98118</th>      <td> 1.875e+05</td> <td> 6943.057</td> <td>   27.006</td> <td> 0.000</td> <td> 1.74e+05</td> <td> 2.01e+05</td>
</tr>
<tr>
  <th>zipcode_98119</th>      <td> 4.764e+05</td> <td> 9902.550</td> <td>   48.110</td> <td> 0.000</td> <td> 4.57e+05</td> <td> 4.96e+05</td>
</tr>
<tr>
  <th>zipcode_98122</th>      <td> 3.617e+05</td> <td> 8292.137</td> <td>   43.626</td> <td> 0.000</td> <td> 3.45e+05</td> <td> 3.78e+05</td>
</tr>
<tr>
  <th>zipcode_98125</th>      <td>   2.1e+05</td> <td> 7284.774</td> <td>   28.820</td> <td> 0.000</td> <td> 1.96e+05</td> <td> 2.24e+05</td>
</tr>
<tr>
  <th>zipcode_98126</th>      <td> 2.175e+05</td> <td> 7599.293</td> <td>   28.619</td> <td> 0.000</td> <td> 2.03e+05</td> <td> 2.32e+05</td>
</tr>
<tr>
  <th>zipcode_98133</th>      <td> 1.658e+05</td> <td> 6925.288</td> <td>   23.947</td> <td> 0.000</td> <td> 1.52e+05</td> <td> 1.79e+05</td>
</tr>
<tr>
  <th>zipcode_98136</th>      <td> 2.733e+05</td> <td> 8445.837</td> <td>   32.356</td> <td> 0.000</td> <td> 2.57e+05</td> <td>  2.9e+05</td>
</tr>
<tr>
  <th>zipcode_98144</th>      <td> 2.802e+05</td> <td> 7988.888</td> <td>   35.068</td> <td> 0.000</td> <td> 2.64e+05</td> <td> 2.96e+05</td>
</tr>
<tr>
  <th>zipcode_98146</th>      <td> 1.193e+05</td> <td> 8038.957</td> <td>   14.841</td> <td> 0.000</td> <td> 1.04e+05</td> <td> 1.35e+05</td>
</tr>
<tr>
  <th>zipcode_98148</th>      <td>  6.05e+04</td> <td> 1.39e+04</td> <td>    4.342</td> <td> 0.000</td> <td> 3.32e+04</td> <td> 8.78e+04</td>
</tr>
<tr>
  <th>zipcode_98155</th>      <td> 1.449e+05</td> <td> 6997.346</td> <td>   20.712</td> <td> 0.000</td> <td> 1.31e+05</td> <td> 1.59e+05</td>
</tr>
<tr>
  <th>zipcode_98166</th>      <td> 1.006e+05</td> <td> 8346.890</td> <td>   12.055</td> <td> 0.000</td> <td> 8.43e+04</td> <td> 1.17e+05</td>
</tr>
<tr>
  <th>zipcode_98168</th>      <td> 6.865e+04</td> <td> 7965.620</td> <td>    8.618</td> <td> 0.000</td> <td>  5.3e+04</td> <td> 8.43e+04</td>
</tr>
<tr>
  <th>zipcode_98177</th>      <td>  2.16e+05</td> <td> 8435.961</td> <td>   25.608</td> <td> 0.000</td> <td> 1.99e+05</td> <td> 2.33e+05</td>
</tr>
<tr>
  <th>zipcode_98178</th>      <td> 6.366e+04</td> <td> 8209.060</td> <td>    7.755</td> <td> 0.000</td> <td> 4.76e+04</td> <td> 7.97e+04</td>
</tr>
<tr>
  <th>zipcode_98188</th>      <td> 3.965e+04</td> <td> 9994.455</td> <td>    3.967</td> <td> 0.000</td> <td> 2.01e+04</td> <td> 5.92e+04</td>
</tr>
<tr>
  <th>zipcode_98198</th>      <td> 2.996e+04</td> <td> 8123.184</td> <td>    3.688</td> <td> 0.000</td> <td>  1.4e+04</td> <td> 4.59e+04</td>
</tr>
<tr>
  <th>zipcode_98199</th>      <td> 3.966e+05</td> <td> 8042.012</td> <td>   49.319</td> <td> 0.000</td> <td> 3.81e+05</td> <td> 4.12e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>4523.949</td> <th>  Durbin-Watson:     </th> <td>   1.553</td> 
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>29016.624</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 1.005</td>  <th>  Prob(JB):          </th> <td>    0.00</td> 
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 8.755</td>  <th>  Cond. No.          </th> <td>    100.</td> 
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_148_2.png)
    



    
![png](output_148_3.png)
    


### Checking for Linearity Conclusion
- When adding zipcode, R^2 moves up to 0.834
- Floors are statistically insignificant
- Tried OHE and they came back as majority insignificant
- Dropped floors because no linear relationship
- Some zipcodes were statistically insignificant but enough to drop the variables
- QQ plot trails off 2 quantile
- Homoscedasticity breaks down around $1,000,000

## Invididually check for homoskedacicity per feature


```python
X_z_zip2 = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'basementyes', 'living_vs_neighbor',
       'live_lot', 'renovated_yes']
for col in X_z_zip2:
    print(f'{col}-----------------')
    sm.graphics.plot_regress_exog(model_zip, col,plt.figure(figsize=(12,8)))
    plt.show()
    print('----------------------')
```

    bedrooms-----------------



    
![png](output_151_1.png)
    


    ----------------------
    bathrooms-----------------



    
![png](output_151_3.png)
    


    ----------------------
    sqft_living-----------------



    
![png](output_151_5.png)
    


    ----------------------
    sqft_lot-----------------



    
![png](output_151_7.png)
    


    ----------------------
    floors-----------------



    
![png](output_151_9.png)
    


    ----------------------
    waterfront-----------------



    
![png](output_151_11.png)
    


    ----------------------
    view-----------------



    
![png](output_151_13.png)
    


    ----------------------
    condition-----------------



    
![png](output_151_15.png)
    


    ----------------------
    grade-----------------



    
![png](output_151_17.png)
    


    ----------------------
    basementyes-----------------



    
![png](output_151_19.png)
    


    ----------------------
    living_vs_neighbor-----------------



    
![png](output_151_21.png)
    


    ----------------------
    live_lot-----------------



    
![png](output_151_23.png)
    


    ----------------------
    renovated_yes-----------------



    
![png](output_151_25.png)
    


    ----------------------



```python
# Sqft Lot, # live_lot are heteroscedasticstic
```


```python
X_z_zip_ho = ['bedrooms', 'bathrooms', 'sqft_living',
       'floors', 'view', 'condition', 'grade',
       'yr_built', 'basementyes', 'living_vs_neighbor',
       'renovated_yes', 'zipcode_98002',
       'zipcode_98003', 'zipcode_98004', 'zipcode_98005', 'zipcode_98006',
       'zipcode_98007', 'zipcode_98008', 'zipcode_98010', 'zipcode_98011',
       'zipcode_98014', 'zipcode_98019', 'zipcode_98022', 'zipcode_98023',
       'zipcode_98024', 'zipcode_98027', 'zipcode_98028', 'zipcode_98029',
       'zipcode_98030', 'zipcode_98031', 'zipcode_98032', 'zipcode_98033',
       'zipcode_98034', 'zipcode_98038', 'zipcode_98039', 'zipcode_98040',
       'zipcode_98042', 'zipcode_98045', 'zipcode_98052', 'zipcode_98053',
       'zipcode_98055', 'zipcode_98056', 'zipcode_98058', 'zipcode_98059',
       'zipcode_98065', 'zipcode_98070', 'zipcode_98072', 'zipcode_98074',
       'zipcode_98075', 'zipcode_98077', 'zipcode_98092', 'zipcode_98102',
       'zipcode_98103', 'zipcode_98105', 'zipcode_98106', 'zipcode_98107',
       'zipcode_98108', 'zipcode_98109', 'zipcode_98112', 'zipcode_98115',
       'zipcode_98116', 'zipcode_98117', 'zipcode_98118', 'zipcode_98119',
       'zipcode_98122', 'zipcode_98125', 'zipcode_98126', 'zipcode_98133',
       'zipcode_98136', 'zipcode_98144', 'zipcode_98146', 'zipcode_98148',
       'zipcode_98155', 'zipcode_98166', 'zipcode_98168', 'zipcode_98177',
       'zipcode_98178', 'zipcode_98188', 'zipcode_98198', 'zipcode_98199']
```


```python
model_ind = model_summary(df_z_loc2, X_z_zip_ho, 'price', True)
sked_show(df_z_loc2, X_z_zip_ho, model_ind)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.832</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.831</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1156.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:36:15</td>     <th>  Log-Likelihood:    </th> <td>-2.4159e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 18739</td>      <th>  AIC:               </th>  <td>4.833e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 18658</td>      <th>  BIC:               </th>  <td>4.840e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    80</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> 3.503e+05</td> <td> 5257.136</td> <td>   66.635</td> <td> 0.000</td> <td>  3.4e+05</td> <td> 3.61e+05</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-5196.7558</td> <td>  998.411</td> <td>   -5.205</td> <td> 0.000</td> <td>-7153.732</td> <td>-3239.779</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.395e+04</td> <td> 1403.035</td> <td>    9.941</td> <td> 0.000</td> <td> 1.12e+04</td> <td> 1.67e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td> 1.344e+05</td> <td> 2008.788</td> <td>   66.885</td> <td> 0.000</td> <td>  1.3e+05</td> <td> 1.38e+05</td>
</tr>
<tr>
  <th>floors</th>             <td>-4669.7553</td> <td> 1123.409</td> <td>   -4.157</td> <td> 0.000</td> <td>-6871.740</td> <td>-2467.771</td>
</tr>
<tr>
  <th>view</th>               <td> 2.886e+04</td> <td> 1369.811</td> <td>   21.071</td> <td> 0.000</td> <td> 2.62e+04</td> <td> 3.15e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 1.512e+04</td> <td>  807.272</td> <td>   18.735</td> <td> 0.000</td> <td> 1.35e+04</td> <td> 1.67e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 6.274e+04</td> <td> 1430.644</td> <td>   43.851</td> <td> 0.000</td> <td> 5.99e+04</td> <td> 6.55e+04</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-1.805e+04</td> <td> 1260.530</td> <td>  -14.322</td> <td> 0.000</td> <td>-2.05e+04</td> <td>-1.56e+04</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-2.448e+04</td> <td> 1880.028</td> <td>  -13.022</td> <td> 0.000</td> <td>-2.82e+04</td> <td>-2.08e+04</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>-1.866e+04</td> <td> 1215.759</td> <td>  -15.352</td> <td> 0.000</td> <td> -2.1e+04</td> <td>-1.63e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 3.701e+04</td> <td> 4368.618</td> <td>    8.472</td> <td> 0.000</td> <td> 2.84e+04</td> <td> 4.56e+04</td>
</tr>
<tr>
  <th>zipcode_98002</th>      <td> 1.462e+04</td> <td> 8794.017</td> <td>    1.663</td> <td> 0.096</td> <td>-2615.982</td> <td> 3.19e+04</td>
</tr>
<tr>
  <th>zipcode_98003</th>      <td>-1.027e+04</td> <td> 7867.654</td> <td>   -1.305</td> <td> 0.192</td> <td>-2.57e+04</td> <td> 5151.224</td>
</tr>
<tr>
  <th>zipcode_98004</th>      <td>  6.07e+05</td> <td> 8512.544</td> <td>   71.308</td> <td> 0.000</td> <td>  5.9e+05</td> <td> 6.24e+05</td>
</tr>
<tr>
  <th>zipcode_98005</th>      <td> 3.149e+05</td> <td> 9576.428</td> <td>   32.885</td> <td> 0.000</td> <td> 2.96e+05</td> <td> 3.34e+05</td>
</tr>
<tr>
  <th>zipcode_98006</th>      <td> 2.546e+05</td> <td> 7289.441</td> <td>   34.921</td> <td> 0.000</td> <td>  2.4e+05</td> <td> 2.69e+05</td>
</tr>
<tr>
  <th>zipcode_98007</th>      <td> 2.453e+05</td> <td> 9854.187</td> <td>   24.893</td> <td> 0.000</td> <td> 2.26e+05</td> <td> 2.65e+05</td>
</tr>
<tr>
  <th>zipcode_98008</th>      <td> 2.279e+05</td> <td> 7995.289</td> <td>   28.510</td> <td> 0.000</td> <td> 2.12e+05</td> <td> 2.44e+05</td>
</tr>
<tr>
  <th>zipcode_98010</th>      <td> 8.773e+04</td> <td> 1.22e+04</td> <td>    7.213</td> <td> 0.000</td> <td> 6.39e+04</td> <td> 1.12e+05</td>
</tr>
<tr>
  <th>zipcode_98011</th>      <td> 1.347e+05</td> <td> 8775.143</td> <td>   15.350</td> <td> 0.000</td> <td> 1.17e+05</td> <td> 1.52e+05</td>
</tr>
<tr>
  <th>zipcode_98014</th>      <td> 1.132e+05</td> <td>  1.2e+04</td> <td>    9.416</td> <td> 0.000</td> <td> 8.97e+04</td> <td> 1.37e+05</td>
</tr>
<tr>
  <th>zipcode_98019</th>      <td> 8.823e+04</td> <td> 9145.626</td> <td>    9.648</td> <td> 0.000</td> <td> 7.03e+04</td> <td> 1.06e+05</td>
</tr>
<tr>
  <th>zipcode_98022</th>      <td> 1640.1187</td> <td> 9079.715</td> <td>    0.181</td> <td> 0.857</td> <td>-1.62e+04</td> <td> 1.94e+04</td>
</tr>
<tr>
  <th>zipcode_98023</th>      <td>-2.776e+04</td> <td> 6828.606</td> <td>   -4.065</td> <td> 0.000</td> <td>-4.11e+04</td> <td>-1.44e+04</td>
</tr>
<tr>
  <th>zipcode_98024</th>      <td> 1.469e+05</td> <td> 1.53e+04</td> <td>    9.607</td> <td> 0.000</td> <td> 1.17e+05</td> <td> 1.77e+05</td>
</tr>
<tr>
  <th>zipcode_98027</th>      <td> 1.833e+05</td> <td> 7573.440</td> <td>   24.197</td> <td> 0.000</td> <td> 1.68e+05</td> <td> 1.98e+05</td>
</tr>
<tr>
  <th>zipcode_98028</th>      <td> 1.248e+05</td> <td> 7868.770</td> <td>   15.861</td> <td> 0.000</td> <td> 1.09e+05</td> <td>  1.4e+05</td>
</tr>
<tr>
  <th>zipcode_98029</th>      <td> 2.121e+05</td> <td> 7684.957</td> <td>   27.594</td> <td> 0.000</td> <td> 1.97e+05</td> <td> 2.27e+05</td>
</tr>
<tr>
  <th>zipcode_98030</th>      <td> -690.6374</td> <td> 8072.780</td> <td>   -0.086</td> <td> 0.932</td> <td>-1.65e+04</td> <td> 1.51e+04</td>
</tr>
<tr>
  <th>zipcode_98031</th>      <td> 5279.7407</td> <td> 7929.509</td> <td>    0.666</td> <td> 0.506</td> <td>-1.03e+04</td> <td> 2.08e+04</td>
</tr>
<tr>
  <th>zipcode_98032</th>      <td>-6237.9923</td> <td> 1.02e+04</td> <td>   -0.609</td> <td> 0.542</td> <td>-2.63e+04</td> <td> 1.38e+04</td>
</tr>
<tr>
  <th>zipcode_98033</th>      <td> 3.377e+05</td> <td> 7189.735</td> <td>   46.968</td> <td> 0.000</td> <td> 3.24e+05</td> <td> 3.52e+05</td>
</tr>
<tr>
  <th>zipcode_98034</th>      <td> 1.811e+05</td> <td> 6735.104</td> <td>   26.889</td> <td> 0.000</td> <td> 1.68e+05</td> <td> 1.94e+05</td>
</tr>
<tr>
  <th>zipcode_98038</th>      <td> 2.835e+04</td> <td> 6691.924</td> <td>    4.237</td> <td> 0.000</td> <td> 1.52e+04</td> <td> 4.15e+04</td>
</tr>
<tr>
  <th>zipcode_98039</th>      <td> 8.336e+05</td> <td> 2.55e+04</td> <td>   32.735</td> <td> 0.000</td> <td> 7.84e+05</td> <td> 8.83e+05</td>
</tr>
<tr>
  <th>zipcode_98040</th>      <td> 4.621e+05</td> <td> 8584.960</td> <td>   53.822</td> <td> 0.000</td> <td> 4.45e+05</td> <td> 4.79e+05</td>
</tr>
<tr>
  <th>zipcode_98042</th>      <td> 1158.2153</td> <td> 6706.919</td> <td>    0.173</td> <td> 0.863</td> <td> -1.2e+04</td> <td> 1.43e+04</td>
</tr>
<tr>
  <th>zipcode_98045</th>      <td> 1.085e+05</td> <td> 8786.574</td> <td>   12.351</td> <td> 0.000</td> <td> 9.13e+04</td> <td> 1.26e+05</td>
</tr>
<tr>
  <th>zipcode_98052</th>      <td> 2.438e+05</td> <td> 6688.076</td> <td>   36.453</td> <td> 0.000</td> <td> 2.31e+05</td> <td> 2.57e+05</td>
</tr>
<tr>
  <th>zipcode_98053</th>      <td> 2.315e+05</td> <td> 7475.923</td> <td>   30.967</td> <td> 0.000</td> <td> 2.17e+05</td> <td> 2.46e+05</td>
</tr>
<tr>
  <th>zipcode_98055</th>      <td> 3.539e+04</td> <td> 8093.904</td> <td>    4.373</td> <td> 0.000</td> <td> 1.95e+04</td> <td> 5.13e+04</td>
</tr>
<tr>
  <th>zipcode_98056</th>      <td> 9.586e+04</td> <td> 7165.547</td> <td>   13.378</td> <td> 0.000</td> <td> 8.18e+04</td> <td>  1.1e+05</td>
</tr>
<tr>
  <th>zipcode_98058</th>      <td> 2.639e+04</td> <td> 6976.985</td> <td>    3.783</td> <td> 0.000</td> <td> 1.27e+04</td> <td> 4.01e+04</td>
</tr>
<tr>
  <th>zipcode_98059</th>      <td> 9.215e+04</td> <td> 7035.599</td> <td>   13.097</td> <td> 0.000</td> <td> 7.84e+04</td> <td> 1.06e+05</td>
</tr>
<tr>
  <th>zipcode_98065</th>      <td> 1.179e+05</td> <td> 7900.042</td> <td>   14.924</td> <td> 0.000</td> <td> 1.02e+05</td> <td> 1.33e+05</td>
</tr>
<tr>
  <th>zipcode_98070</th>      <td> 1.447e+05</td> <td> 1.48e+04</td> <td>    9.802</td> <td> 0.000</td> <td> 1.16e+05</td> <td> 1.74e+05</td>
</tr>
<tr>
  <th>zipcode_98072</th>      <td> 1.734e+05</td> <td> 8045.276</td> <td>   21.552</td> <td> 0.000</td> <td> 1.58e+05</td> <td> 1.89e+05</td>
</tr>
<tr>
  <th>zipcode_98074</th>      <td> 2.018e+05</td> <td> 7209.996</td> <td>   27.990</td> <td> 0.000</td> <td> 1.88e+05</td> <td> 2.16e+05</td>
</tr>
<tr>
  <th>zipcode_98075</th>      <td> 2.119e+05</td> <td> 7763.732</td> <td>   27.289</td> <td> 0.000</td> <td> 1.97e+05</td> <td> 2.27e+05</td>
</tr>
<tr>
  <th>zipcode_98077</th>      <td> 1.606e+05</td> <td> 9328.612</td> <td>   17.217</td> <td> 0.000</td> <td> 1.42e+05</td> <td> 1.79e+05</td>
</tr>
<tr>
  <th>zipcode_98092</th>      <td>-3.054e+04</td> <td> 7590.955</td> <td>   -4.023</td> <td> 0.000</td> <td>-4.54e+04</td> <td>-1.57e+04</td>
</tr>
<tr>
  <th>zipcode_98102</th>      <td> 4.328e+05</td> <td> 1.27e+04</td> <td>   34.172</td> <td> 0.000</td> <td> 4.08e+05</td> <td> 4.58e+05</td>
</tr>
<tr>
  <th>zipcode_98103</th>      <td> 3.225e+05</td> <td> 7035.046</td> <td>   45.849</td> <td> 0.000</td> <td> 3.09e+05</td> <td> 3.36e+05</td>
</tr>
<tr>
  <th>zipcode_98105</th>      <td> 4.134e+05</td> <td> 9038.160</td> <td>   45.739</td> <td> 0.000</td> <td> 3.96e+05</td> <td> 4.31e+05</td>
</tr>
<tr>
  <th>zipcode_98106</th>      <td> 1.243e+05</td> <td> 7775.795</td> <td>   15.982</td> <td> 0.000</td> <td> 1.09e+05</td> <td>  1.4e+05</td>
</tr>
<tr>
  <th>zipcode_98107</th>      <td>  3.07e+05</td> <td> 8525.163</td> <td>   36.006</td> <td> 0.000</td> <td>  2.9e+05</td> <td> 3.24e+05</td>
</tr>
<tr>
  <th>zipcode_98108</th>      <td> 1.129e+05</td> <td> 9078.018</td> <td>   12.431</td> <td> 0.000</td> <td> 9.51e+04</td> <td> 1.31e+05</td>
</tr>
<tr>
  <th>zipcode_98109</th>      <td> 4.602e+05</td> <td> 1.19e+04</td> <td>   38.821</td> <td> 0.000</td> <td> 4.37e+05</td> <td> 4.83e+05</td>
</tr>
<tr>
  <th>zipcode_98112</th>      <td> 5.136e+05</td> <td> 8997.896</td> <td>   57.078</td> <td> 0.000</td> <td> 4.96e+05</td> <td> 5.31e+05</td>
</tr>
<tr>
  <th>zipcode_98115</th>      <td> 3.173e+05</td> <td> 6861.837</td> <td>   46.236</td> <td> 0.000</td> <td> 3.04e+05</td> <td> 3.31e+05</td>
</tr>
<tr>
  <th>zipcode_98116</th>      <td>  2.84e+05</td> <td> 8093.814</td> <td>   35.086</td> <td> 0.000</td> <td> 2.68e+05</td> <td>    3e+05</td>
</tr>
<tr>
  <th>zipcode_98117</th>      <td> 3.069e+05</td> <td> 6967.841</td> <td>   44.043</td> <td> 0.000</td> <td> 2.93e+05</td> <td> 3.21e+05</td>
</tr>
<tr>
  <th>zipcode_98118</th>      <td> 1.587e+05</td> <td> 7026.508</td> <td>   22.592</td> <td> 0.000</td> <td> 1.45e+05</td> <td> 1.73e+05</td>
</tr>
<tr>
  <th>zipcode_98119</th>      <td> 4.208e+05</td> <td>    1e+04</td> <td>   41.970</td> <td> 0.000</td> <td> 4.01e+05</td> <td>  4.4e+05</td>
</tr>
<tr>
  <th>zipcode_98122</th>      <td> 3.107e+05</td> <td> 8432.271</td> <td>   36.851</td> <td> 0.000</td> <td> 2.94e+05</td> <td> 3.27e+05</td>
</tr>
<tr>
  <th>zipcode_98125</th>      <td> 1.912e+05</td> <td> 7347.198</td> <td>   26.018</td> <td> 0.000</td> <td> 1.77e+05</td> <td> 2.06e+05</td>
</tr>
<tr>
  <th>zipcode_98126</th>      <td>  1.89e+05</td> <td> 7665.277</td> <td>   24.651</td> <td> 0.000</td> <td> 1.74e+05</td> <td> 2.04e+05</td>
</tr>
<tr>
  <th>zipcode_98133</th>      <td> 1.491e+05</td> <td> 6968.355</td> <td>   21.394</td> <td> 0.000</td> <td> 1.35e+05</td> <td> 1.63e+05</td>
</tr>
<tr>
  <th>zipcode_98136</th>      <td> 2.428e+05</td> <td> 8514.135</td> <td>   28.520</td> <td> 0.000</td> <td> 2.26e+05</td> <td>  2.6e+05</td>
</tr>
<tr>
  <th>zipcode_98144</th>      <td> 2.377e+05</td> <td> 8011.153</td> <td>   29.671</td> <td> 0.000</td> <td> 2.22e+05</td> <td> 2.53e+05</td>
</tr>
<tr>
  <th>zipcode_98146</th>      <td> 1.054e+05</td> <td> 8095.742</td> <td>   13.019</td> <td> 0.000</td> <td> 8.95e+04</td> <td> 1.21e+05</td>
</tr>
<tr>
  <th>zipcode_98148</th>      <td> 4.985e+04</td> <td>  1.4e+04</td> <td>    3.558</td> <td> 0.000</td> <td> 2.24e+04</td> <td> 7.73e+04</td>
</tr>
<tr>
  <th>zipcode_98155</th>      <td> 1.345e+05</td> <td> 7048.459</td> <td>   19.084</td> <td> 0.000</td> <td> 1.21e+05</td> <td> 1.48e+05</td>
</tr>
<tr>
  <th>zipcode_98166</th>      <td> 9.077e+04</td> <td> 8403.240</td> <td>   10.801</td> <td> 0.000</td> <td> 7.43e+04</td> <td> 1.07e+05</td>
</tr>
<tr>
  <th>zipcode_98168</th>      <td> 5.804e+04</td> <td> 8032.807</td> <td>    7.226</td> <td> 0.000</td> <td> 4.23e+04</td> <td> 7.38e+04</td>
</tr>
<tr>
  <th>zipcode_98177</th>      <td> 1.985e+05</td> <td> 8499.493</td> <td>   23.352</td> <td> 0.000</td> <td> 1.82e+05</td> <td> 2.15e+05</td>
</tr>
<tr>
  <th>zipcode_98178</th>      <td> 4.692e+04</td> <td> 8267.418</td> <td>    5.675</td> <td> 0.000</td> <td> 3.07e+04</td> <td> 6.31e+04</td>
</tr>
<tr>
  <th>zipcode_98188</th>      <td> 3.198e+04</td> <td>    1e+04</td> <td>    3.182</td> <td> 0.001</td> <td> 1.23e+04</td> <td> 5.17e+04</td>
</tr>
<tr>
  <th>zipcode_98198</th>      <td> 2.199e+04</td> <td> 8162.409</td> <td>    2.694</td> <td> 0.007</td> <td> 5993.316</td> <td>  3.8e+04</td>
</tr>
<tr>
  <th>zipcode_98199</th>      <td> 3.619e+05</td> <td> 8108.288</td> <td>   44.634</td> <td> 0.000</td> <td> 3.46e+05</td> <td> 3.78e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>4554.552</td> <th>  Durbin-Watson:     </th> <td>   1.554</td> 
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>28504.162</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 1.021</td>  <th>  Prob(JB):          </th> <td>    0.00</td> 
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 8.687</td>  <th>  Cond. No.          </th> <td>    111.</td> 
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_154_2.png)
    



    
![png](output_154_3.png)
    


### Skedacicity Individual Conclusion:
- It has not changed much, concern is that too many high outlier values are left in the dataset

## Going back to IQR because of heteroscedasticity


```python
# IQR method is more strict on removing outliers

df_iqr4 = df_iqr.copy()
```


```python
df_iqr4.drop('yr_renovated', axis=1, inplace=True)
```


```python
# Lower bound is negative

res=df_iqr4['price'].describe()
thresh = res['75%'] -res['25%']
u_bound=res['75%']+1.5*thresh
u_bound

```




    1125564.75




```python
df_iqr4['outlier'] = (df_iqr4['price']>u_bound).map({True:True,
                                False:False})
```


```python
df_iqror=df_iqr4.loc[df_iqr4['outlier']==False]
```


```python
# Add number of removed values
print(f'Num observations before removal: {len(df)}')
print(f'Num observations after removal:  {len(df_iqror)}')
print(f'Num observations removed:  {len(df) - len(df_iqror)}')
print(f'Percent observations removed:  {round(100*((len(df) - len(df_iqror))/len(df)),2)}%')
print('--------------------------------------------')
fig, axes = plt.subplots(nrows=2, figsize=(6,10))
sns.boxplot(data=df_iqror, x='price', ax=axes[0])
axes[0].set_title('Outliers Removed')
sns.boxplot(data=df_iqr4, x='price', ax=axes[1])
axes[1].set_title('Outliers Not Removed')
plt.show();
print('--------------------------------------------')
print(f"Max Home Price: {df_iqror['price'].max()}")
print(f"Min Home Price: {df_iqror['price'].min()}")
```

    Num observations before removal: 21387
    Num observations after removal:  20235
    Num observations removed:  1152
    Percent observations removed:  5.39%
    --------------------------------------------



    
![png](output_162_1.png)
    


    --------------------------------------------
    Max Home Price: 1120000.0
    Min Home Price: 78000.0


## Baseline Model Price Removal


```python
X_targs3= ['bedrooms', 'bathrooms', 'sqft_living', 'lat', 'long', 'zipcode',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'sqft_above', 'yr_built', 'sqft_living15',
       'sqft_lot15', 'basementyes', 'total_rooms', 'living_vs_neighbor',
       'lot_vs_neighbor', 'live_lot', 'renovated_yes']
```


```python
model_iqr_price = model_summary(df_iqror, X_targs3, 'price', True)
sked_show(df_iqror, X_targs3,model_iqr_price)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.705</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.705</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2298.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:58</td>     <th>  Log-Likelihood:    </th> <td>-2.6401e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 20235</td>      <th>  AIC:               </th>  <td>5.281e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 20213</td>      <th>  BIC:               </th>  <td>5.282e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    21</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td>-3.625e+05</td> <td> 1.72e+06</td> <td>   -0.210</td> <td> 0.833</td> <td>-3.74e+06</td> <td> 3.01e+06</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-1.252e+04</td> <td> 1116.849</td> <td>  -11.211</td> <td> 0.000</td> <td>-1.47e+04</td> <td>-1.03e+04</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.544e+04</td> <td> 1435.653</td> <td>   10.758</td> <td> 0.000</td> <td> 1.26e+04</td> <td> 1.83e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   18.0607</td> <td>    5.600</td> <td>    3.225</td> <td> 0.001</td> <td>    7.083</td> <td>   29.038</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.298e+05</td> <td> 6129.117</td> <td>   86.440</td> <td> 0.000</td> <td> 5.18e+05</td> <td> 5.42e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-2.338e+04</td> <td> 7616.982</td> <td>   -3.069</td> <td> 0.002</td> <td>-3.83e+04</td> <td>-8447.803</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -248.9450</td> <td>   19.145</td> <td>  -13.003</td> <td> 0.000</td> <td> -286.470</td> <td> -211.420</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>    0.2416</td> <td>    0.036</td> <td>    6.679</td> <td> 0.000</td> <td>    0.171</td> <td>    0.312</td>
</tr>
<tr>
  <th>floors</th>             <td> 4281.4259</td> <td> 2540.816</td> <td>    1.685</td> <td> 0.092</td> <td> -698.781</td> <td> 9261.633</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.427e+05</td> <td> 1.66e+04</td> <td>    8.590</td> <td> 0.000</td> <td>  1.1e+05</td> <td> 1.75e+05</td>
</tr>
<tr>
  <th>view</th>               <td>  3.09e+04</td> <td> 1365.983</td> <td>   22.624</td> <td> 0.000</td> <td> 2.82e+04</td> <td> 3.36e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.673e+04</td> <td> 1363.265</td> <td>   19.604</td> <td> 0.000</td> <td> 2.41e+04</td> <td> 2.94e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 6.898e+04</td> <td> 1292.737</td> <td>   53.357</td> <td> 0.000</td> <td> 6.64e+04</td> <td> 7.15e+04</td>
</tr>
<tr>
  <th>sqft_above</th>         <td>   38.2290</td> <td>    4.179</td> <td>    9.147</td> <td> 0.000</td> <td>   30.037</td> <td>   46.421</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-1916.8886</td> <td>   43.253</td> <td>  -44.318</td> <td> 0.000</td> <td>-2001.667</td> <td>-1832.110</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   81.4389</td> <td>    5.075</td> <td>   16.047</td> <td> 0.000</td> <td>   71.492</td> <td>   91.386</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    0.0025</td> <td>    0.050</td> <td>    0.049</td> <td> 0.961</td> <td>   -0.095</td> <td>    0.100</td>
</tr>
<tr>
  <th>basementyes</th>        <td> 1.814e+04</td> <td> 3088.694</td> <td>    5.872</td> <td> 0.000</td> <td> 1.21e+04</td> <td> 2.42e+04</td>
</tr>
<tr>
  <th>total_rooms</th>        <td> 2923.1709</td> <td>  696.399</td> <td>    4.198</td> <td> 0.000</td> <td> 1558.173</td> <td> 4288.169</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 5.155e+04</td> <td> 8223.717</td> <td>    6.269</td> <td> 0.000</td> <td> 3.54e+04</td> <td> 6.77e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 1236.0066</td> <td>  830.539</td> <td>    1.488</td> <td> 0.137</td> <td> -391.918</td> <td> 2863.931</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 9.056e+04</td> <td> 4502.041</td> <td>   20.116</td> <td> 0.000</td> <td> 8.17e+04</td> <td> 9.94e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 2.998e+04</td> <td> 4827.868</td> <td>    6.209</td> <td> 0.000</td> <td> 2.05e+04</td> <td> 3.94e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1694.168</td> <th>  Durbin-Watson:     </th> <td>   1.827</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>3157.837</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.587</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.539</td>  <th>  Cond. No.          </th> <td>8.81e+17</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The smallest eigenvalue is 2.63e-22. This might indicate that there are<br/>strong multicollinearity problems or that the design matrix is singular.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_165_2.png)
    



    
![png](output_165_3.png)
    


### Baseline IQR Model Conclusion
- While R^2 0.71
- We have homoskedacicity
- QQ model shows very few values tailing off, only past 2.5 quantiles
- Assumptions are better met

## Check for Multicolinearity


```python
df_iqror.corr()['price'].round(2).sort_values(ascending=False)
```




    price                 1.00000
    grade                 0.63000
    sqft_living           0.62000
    sqft_living15         0.56000
    sqft_above            0.53000
    bathrooms             0.45000
    lat                   0.43000
    total_rooms           0.42000
    bedrooms              0.30000
    floors                0.27000
    living_vs_neighbor    0.24000
    view                  0.23000
    live_lot              0.17000
    basementyes           0.16000
    sqft_lot              0.09000
    renovated_yes         0.08000
    sqft_lot15            0.08000
    long                  0.07000
    yr_built              0.06000
    waterfront            0.05000
    lot_vs_neighbor       0.04000
    condition             0.03000
    id                    0.01000
    zipcode              -0.02000
    outlier                   nan
    Name: price, dtype: float64




```python
corr2 = df_iqror.corr()

fig, ax = plt.subplots(figsize=(15,15))
matrix = np.triu(corr2)
sns.heatmap(corr2,cmap="coolwarm", annot=True, fmt='.1g', mask=matrix)
```




    <AxesSubplot:>




    
![png](output_169_1.png)
    



```python
# Remove total_rooms, sqft_above

corr_finder(df_iqror)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cc</th>
    </tr>
    <tr>
      <th>pairs</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>(bedrooms, total_rooms)</th>
      <td>0.89690</td>
    </tr>
    <tr>
      <th>(sqft_living, sqft_above)</th>
      <td>0.85335</td>
    </tr>
    <tr>
      <th>(bathrooms, total_rooms)</th>
      <td>0.83498</td>
    </tr>
    <tr>
      <th>(sqft_living, total_rooms)</th>
      <td>0.75134</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Confirm we don't have multicolinearity

corr_finder(df_iqror.drop(['total_rooms', 'sqft_above'], axis=1))
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cc</th>
    </tr>
    <tr>
      <th>pairs</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
df_iqror_mc = df_iqror.drop(['total_rooms', 'sqft_above'], axis=1)
```

### Multicolinearity Conclusion
- Had to drop total_rooms and sqft_above because they did not meet assumption of no multicolinearity


```python
df_iqror_mc.columns
x_targs = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'yr_built', 'zipcode', 'lat', 'long', 'sqft_living15', 'sqft_lot15',
       'basementyes', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot',
       'renovated_yes']
```


```python
model_iqr_co = model_summary(df_iqror_mc, x_targs, 'price', True)
sked_show(df_iqror_mc, x_targs, model_iqr_co)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.704</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.703</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2399.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:24:59</td>     <th>  Log-Likelihood:    </th> <td>-2.6405e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 20235</td>      <th>  AIC:               </th>  <td>5.281e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 20214</td>      <th>  BIC:               </th>  <td>5.283e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    20</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td>-1.995e+05</td> <td> 1.73e+06</td> <td>   -0.116</td> <td> 0.908</td> <td>-3.58e+06</td> <td> 3.18e+06</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-9957.8892</td> <td> 1186.480</td> <td>   -8.393</td> <td> 0.000</td> <td>-1.23e+04</td> <td>-7632.293</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 1.798e+04</td> <td> 1964.365</td> <td>    9.154</td> <td> 0.000</td> <td> 1.41e+04</td> <td> 2.18e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   44.4572</td> <td>    4.809</td> <td>    9.244</td> <td> 0.000</td> <td>   35.030</td> <td>   53.884</td>
</tr>
<tr>
  <th>sqft_lot</th>           <td>    0.2449</td> <td>    0.036</td> <td>    6.759</td> <td> 0.000</td> <td>    0.174</td> <td>    0.316</td>
</tr>
<tr>
  <th>floors</th>             <td> 1.088e+04</td> <td> 2441.073</td> <td>    4.459</td> <td> 0.000</td> <td> 6100.082</td> <td> 1.57e+04</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.461e+05</td> <td> 1.66e+04</td> <td>    8.781</td> <td> 0.000</td> <td> 1.14e+05</td> <td> 1.79e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 2.944e+04</td> <td> 1359.317</td> <td>   21.657</td> <td> 0.000</td> <td> 2.68e+04</td> <td> 3.21e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.561e+04</td> <td> 1360.596</td> <td>   18.825</td> <td> 0.000</td> <td> 2.29e+04</td> <td> 2.83e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 7.073e+04</td> <td> 1281.028</td> <td>   55.215</td> <td> 0.000</td> <td> 6.82e+04</td> <td> 7.32e+04</td>
</tr>
<tr>
  <th>yr_built</th>           <td>-1916.5543</td> <td>   43.341</td> <td>  -44.220</td> <td> 0.000</td> <td>-2001.506</td> <td>-1831.602</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -244.7912</td> <td>   19.178</td> <td>  -12.764</td> <td> 0.000</td> <td> -282.382</td> <td> -207.200</td>
</tr>
<tr>
  <th>lat</th>                <td> 5.273e+05</td> <td> 6135.306</td> <td>   85.938</td> <td> 0.000</td> <td> 5.15e+05</td> <td> 5.39e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-1.962e+04</td> <td> 7621.439</td> <td>   -2.575</td> <td> 0.010</td> <td>-3.46e+04</td> <td>-4682.804</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   86.3697</td> <td>    5.057</td> <td>   17.081</td> <td> 0.000</td> <td>   76.458</td> <td>   96.281</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>   -0.0040</td> <td>    0.050</td> <td>   -0.079</td> <td> 0.937</td> <td>   -0.102</td> <td>    0.094</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-2640.5755</td> <td> 2097.124</td> <td>   -1.259</td> <td> 0.208</td> <td>-6751.110</td> <td> 1469.959</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 5.615e+04</td> <td> 8225.127</td> <td>    6.826</td> <td> 0.000</td> <td>    4e+04</td> <td> 7.23e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 1263.0751</td> <td>  832.230</td> <td>    1.518</td> <td> 0.129</td> <td> -368.164</td> <td> 2894.314</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 8.682e+04</td> <td> 4492.592</td> <td>   19.326</td> <td> 0.000</td> <td>  7.8e+04</td> <td> 9.56e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 2.936e+04</td> <td> 4837.259</td> <td>    6.070</td> <td> 0.000</td> <td> 1.99e+04</td> <td> 3.88e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1658.619</td> <th>  Durbin-Watson:     </th> <td>   1.827</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>3086.697</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.577</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.526</td>  <th>  Cond. No.          </th> <td>2.19e+08</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.19e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_175_2.png)
    



    
![png](output_175_3.png)
    


## Check for assumptions of Linearity


```python
df_iqror_mc.columns
```




    Index(['id', 'date', 'price', 'bedrooms', 'bathrooms', 'sqft_living',
           'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
           'yr_built', 'zipcode', 'lat', 'long', 'sqft_living15', 'sqft_lot15',
           'basementyes', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot',
           'renovated_yes', 'outlier'],
          dtype='object')




```python
# yr_built, sqft_lot do not have linear relationships

# lin_check(df_iqror_mc, x_targs)
```


    
![png](output_178_0.png)
    



```python
df_iqr_nocl = df_iqror_mc.drop(['yr_built', 'sqft_lot'], axis=1)
```


```python
df_iqr_nocl.columns
x_targs = ['bedrooms', 'bathrooms', 'sqft_living', 'floors',
       'waterfront', 'view', 'condition', 'grade', 'zipcode', 'lat', 'long',
       'sqft_living15', 'sqft_lot15', 'basementyes', 'living_vs_neighbor',
       'lot_vs_neighbor', 'live_lot', 'renovated_yes']
```


```python
model_iqr5 = model_summary(df_iqr_nocl, x_targs, 'price', True)
sked_show(df_iqr_nocl, x_targs, model_iqr5)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.674</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.674</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   2324.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:25:00</td>     <th>  Log-Likelihood:    </th> <td>-2.6501e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 20235</td>      <th>  AIC:               </th>  <td>5.301e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 20216</td>      <th>  BIC:               </th>  <td>5.302e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    18</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td>-2.687e+07</td> <td> 1.69e+06</td> <td>  -15.865</td> <td> 0.000</td> <td>-3.02e+07</td> <td>-2.36e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-6904.0274</td> <td> 1241.560</td> <td>   -5.561</td> <td> 0.000</td> <td>-9337.586</td> <td>-4470.469</td>
</tr>
<tr>
  <th>bathrooms</th>          <td>-9896.4359</td> <td> 1950.067</td> <td>   -5.075</td> <td> 0.000</td> <td>-1.37e+04</td> <td>-6074.145</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   52.3699</td> <td>    5.037</td> <td>   10.397</td> <td> 0.000</td> <td>   42.497</td> <td>   62.243</td>
</tr>
<tr>
  <th>floors</th>             <td>  854.5008</td> <td> 2547.664</td> <td>    0.335</td> <td> 0.737</td> <td>-4139.128</td> <td> 5848.130</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.276e+05</td> <td> 1.74e+04</td> <td>    7.319</td> <td> 0.000</td> <td> 9.35e+04</td> <td> 1.62e+05</td>
</tr>
<tr>
  <th>view</th>               <td>  3.49e+04</td> <td> 1418.732</td> <td>   24.602</td> <td> 0.000</td> <td> 3.21e+04</td> <td> 3.77e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 4.349e+04</td> <td> 1362.706</td> <td>   31.916</td> <td> 0.000</td> <td> 4.08e+04</td> <td> 4.62e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 5.821e+04</td> <td> 1308.353</td> <td>   44.492</td> <td> 0.000</td> <td> 5.56e+04</td> <td> 6.08e+04</td>
</tr>
<tr>
  <th>zipcode</th>            <td> -137.2615</td> <td>   19.945</td> <td>   -6.882</td> <td> 0.000</td> <td> -176.355</td> <td>  -98.168</td>
</tr>
<tr>
  <th>lat</th>                <td>  5.81e+05</td> <td> 6298.903</td> <td>   92.241</td> <td> 0.000</td> <td> 5.69e+05</td> <td> 5.93e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-1.003e+05</td> <td> 7743.983</td> <td>  -12.951</td> <td> 0.000</td> <td>-1.15e+05</td> <td>-8.51e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   88.9844</td> <td>    5.296</td> <td>   16.801</td> <td> 0.000</td> <td>   78.603</td> <td>   99.366</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    0.2332</td> <td>    0.034</td> <td>    6.833</td> <td> 0.000</td> <td>    0.166</td> <td>    0.300</td>
</tr>
<tr>
  <th>basementyes</th>        <td> 3091.8040</td> <td> 2194.270</td> <td>    1.409</td> <td> 0.159</td> <td>-1209.143</td> <td> 7392.751</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 6.329e+04</td> <td> 8615.709</td> <td>    7.345</td> <td> 0.000</td> <td> 4.64e+04</td> <td> 8.02e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 6060.9267</td> <td>  678.005</td> <td>    8.939</td> <td> 0.000</td> <td> 4731.981</td> <td> 7389.873</td>
</tr>
<tr>
  <th>live_lot</th>           <td> 5.512e+04</td> <td> 4649.196</td> <td>   11.856</td> <td> 0.000</td> <td>  4.6e+04</td> <td> 6.42e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 8.855e+04</td> <td> 4874.646</td> <td>   18.166</td> <td> 0.000</td> <td>  7.9e+04</td> <td> 9.81e+04</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1712.086</td> <th>  Durbin-Watson:     </th> <td>   1.831</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>2834.941</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.630</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 4.332</td>  <th>  Cond. No.          </th> <td>2.02e+08</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.02e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_181_2.png)
    



    
![png](output_181_3.png)
    


### Checking for assumptions conclusion
- R^2 dropped to 0.674
- All Assumptions have been met

## Final Model


```python

from sklearn.preprocessing import OneHotEncoder
encoder = OneHotEncoder(sparse=False, drop='first')
encoder

cat_cols=['zipcode']

encoder.fit(df_iqr_nocl[cat_cols])

ohe_vars = encoder.transform(df_iqr_nocl[cat_cols])
encoder.get_feature_names(cat_cols)
cat_vars = pd.DataFrame(ohe_vars,columns=encoder.get_feature_names(cat_cols))
```


```python
df_iqr_nocl = df_iqr_nocl.reset_index()
```


```python
df_iqr_zip = pd.concat([df_iqr_nocl,cat_vars], axis=1)
```


```python
df_iqr_zip.columns
x_targs =['bedrooms', 'bathrooms', 'sqft_living',
        'waterfront', 'view', 'condition', 'grade','lat',
       'long', 'sqft_living15', 'sqft_lot15', 'basementyes',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes',
       'zipcode_98002', 'zipcode_98003', 'zipcode_98004',
       'zipcode_98005', 'zipcode_98006', 'zipcode_98007', 'zipcode_98008',
       'zipcode_98010', 'zipcode_98011', 'zipcode_98014', 'zipcode_98019',
       'zipcode_98022', 'zipcode_98023', 'zipcode_98024', 'zipcode_98027',
       'zipcode_98028', 'zipcode_98029', 'zipcode_98030', 'zipcode_98031',
       'zipcode_98032', 'zipcode_98033', 'zipcode_98034', 'zipcode_98038',
       'zipcode_98039', 'zipcode_98040', 'zipcode_98042', 'zipcode_98045',
       'zipcode_98052', 'zipcode_98053', 'zipcode_98055', 'zipcode_98056',
       'zipcode_98058', 'zipcode_98059', 'zipcode_98065', 'zipcode_98070',
       'zipcode_98072', 'zipcode_98074', 'zipcode_98075', 'zipcode_98077',
       'zipcode_98092', 'zipcode_98102', 'zipcode_98103', 'zipcode_98105',
       'zipcode_98106', 'zipcode_98107', 'zipcode_98108', 'zipcode_98109',
       'zipcode_98112', 'zipcode_98115', 'zipcode_98116', 'zipcode_98117',
       'zipcode_98118', 'zipcode_98119', 'zipcode_98122', 'zipcode_98125',
       'zipcode_98126', 'zipcode_98133', 'zipcode_98136', 'zipcode_98144',
       'zipcode_98146', 'zipcode_98148', 'zipcode_98155', 'zipcode_98166',
       'zipcode_98168', 'zipcode_98177', 'zipcode_98178', 'zipcode_98188',
       'zipcode_98198', 'zipcode_98199']
```


```python
model_iqr6 = model_summary(df_iqr_zip, x_targs, 'price')
sked_show(df_iqr_zip, x_targs, model_iqr6)
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.832</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.831</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1174.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:27:30</td>     <th>  Log-Likelihood:    </th> <td>-2.5831e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 20235</td>      <th>  AIC:               </th>  <td>5.168e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 20149</td>      <th>  BIC:               </th>  <td>5.175e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    85</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td>-1.847e+07</td> <td> 3.33e+06</td> <td>   -5.548</td> <td> 0.000</td> <td> -2.5e+07</td> <td>-1.19e+07</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-5169.3252</td> <td>  905.283</td> <td>   -5.710</td> <td> 0.000</td> <td>-6943.754</td> <td>-3394.897</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 9690.2367</td> <td> 1381.972</td> <td>    7.012</td> <td> 0.000</td> <td> 6981.459</td> <td> 1.24e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   77.5541</td> <td>    3.642</td> <td>   21.296</td> <td> 0.000</td> <td>   70.416</td> <td>   84.692</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.642e+05</td> <td> 1.29e+04</td> <td>   12.725</td> <td> 0.000</td> <td> 1.39e+05</td> <td> 1.89e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 2.968e+04</td> <td> 1047.450</td> <td>   28.339</td> <td> 0.000</td> <td> 2.76e+04</td> <td> 3.17e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.524e+04</td> <td> 1003.160</td> <td>   25.158</td> <td> 0.000</td> <td> 2.33e+04</td> <td> 2.72e+04</td>
</tr>
<tr>
  <th>grade</th>              <td>  4.25e+04</td> <td>  967.328</td> <td>   43.938</td> <td> 0.000</td> <td> 4.06e+04</td> <td> 4.44e+04</td>
</tr>
<tr>
  <th>lat</th>                <td> 1.655e+05</td> <td> 3.45e+04</td> <td>    4.800</td> <td> 0.000</td> <td> 9.79e+04</td> <td> 2.33e+05</td>
</tr>
<tr>
  <th>long</th>               <td>-8.362e+04</td> <td> 2.46e+04</td> <td>   -3.396</td> <td> 0.001</td> <td>-1.32e+05</td> <td>-3.54e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   62.1707</td> <td>    3.865</td> <td>   16.087</td> <td> 0.000</td> <td>   54.596</td> <td>   69.746</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    0.2088</td> <td>    0.026</td> <td>    7.928</td> <td> 0.000</td> <td>    0.157</td> <td>    0.260</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-1.632e+04</td> <td> 1406.011</td> <td>  -11.607</td> <td> 0.000</td> <td>-1.91e+04</td> <td>-1.36e+04</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td> 4.545e+04</td> <td> 6227.497</td> <td>    7.299</td> <td> 0.000</td> <td> 3.32e+04</td> <td> 5.77e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 4741.1058</td> <td>  489.795</td> <td>    9.680</td> <td> 0.000</td> <td> 3781.068</td> <td> 5701.143</td>
</tr>
<tr>
  <th>live_lot</th>           <td>-6.139e+04</td> <td> 3080.434</td> <td>  -19.928</td> <td> 0.000</td> <td>-6.74e+04</td> <td>-5.53e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 4.491e+04</td> <td> 3534.157</td> <td>   12.707</td> <td> 0.000</td> <td>  3.8e+04</td> <td> 5.18e+04</td>
</tr>
<tr>
  <th>zipcode_98002</th>      <td> 1.816e+04</td> <td> 7690.853</td> <td>    2.361</td> <td> 0.018</td> <td> 3082.507</td> <td> 3.32e+04</td>
</tr>
<tr>
  <th>zipcode_98003</th>      <td>-7583.6840</td> <td> 6874.156</td> <td>   -1.103</td> <td> 0.270</td> <td>-2.11e+04</td> <td> 5890.223</td>
</tr>
<tr>
  <th>zipcode_98004</th>      <td> 4.657e+05</td> <td> 1.35e+04</td> <td>   34.401</td> <td> 0.000</td> <td> 4.39e+05</td> <td> 4.92e+05</td>
</tr>
<tr>
  <th>zipcode_98005</th>      <td> 2.846e+05</td> <td> 1.36e+04</td> <td>   20.880</td> <td> 0.000</td> <td> 2.58e+05</td> <td> 3.11e+05</td>
</tr>
<tr>
  <th>zipcode_98006</th>      <td> 2.374e+05</td> <td> 1.12e+04</td> <td>   21.168</td> <td> 0.000</td> <td> 2.15e+05</td> <td> 2.59e+05</td>
</tr>
<tr>
  <th>zipcode_98007</th>      <td> 2.218e+05</td> <td>  1.4e+04</td> <td>   15.836</td> <td> 0.000</td> <td> 1.94e+05</td> <td> 2.49e+05</td>
</tr>
<tr>
  <th>zipcode_98008</th>      <td> 2.086e+05</td> <td> 1.33e+04</td> <td>   15.635</td> <td> 0.000</td> <td> 1.82e+05</td> <td> 2.35e+05</td>
</tr>
<tr>
  <th>zipcode_98010</th>      <td> 1.008e+05</td> <td> 1.18e+04</td> <td>    8.560</td> <td> 0.000</td> <td> 7.77e+04</td> <td> 1.24e+05</td>
</tr>
<tr>
  <th>zipcode_98011</th>      <td> 7.764e+04</td> <td> 1.73e+04</td> <td>    4.483</td> <td> 0.000</td> <td> 4.37e+04</td> <td> 1.12e+05</td>
</tr>
<tr>
  <th>zipcode_98014</th>      <td> 8.121e+04</td> <td> 1.91e+04</td> <td>    4.261</td> <td> 0.000</td> <td> 4.39e+04</td> <td> 1.19e+05</td>
</tr>
<tr>
  <th>zipcode_98019</th>      <td> 5.264e+04</td> <td> 1.87e+04</td> <td>    2.811</td> <td> 0.005</td> <td> 1.59e+04</td> <td> 8.93e+04</td>
</tr>
<tr>
  <th>zipcode_98022</th>      <td> 4.322e+04</td> <td> 1.03e+04</td> <td>    4.206</td> <td> 0.000</td> <td> 2.31e+04</td> <td> 6.34e+04</td>
</tr>
<tr>
  <th>zipcode_98023</th>      <td>-2.904e+04</td> <td> 6341.463</td> <td>   -4.579</td> <td> 0.000</td> <td>-4.15e+04</td> <td>-1.66e+04</td>
</tr>
<tr>
  <th>zipcode_98024</th>      <td> 1.434e+05</td> <td> 1.69e+04</td> <td>    8.489</td> <td> 0.000</td> <td>  1.1e+05</td> <td> 1.76e+05</td>
</tr>
<tr>
  <th>zipcode_98027</th>      <td>   1.8e+05</td> <td> 1.14e+04</td> <td>   15.844</td> <td> 0.000</td> <td> 1.58e+05</td> <td> 2.02e+05</td>
</tr>
<tr>
  <th>zipcode_98028</th>      <td> 6.285e+04</td> <td> 1.68e+04</td> <td>    3.731</td> <td> 0.000</td> <td> 2.98e+04</td> <td> 9.59e+04</td>
</tr>
<tr>
  <th>zipcode_98029</th>      <td> 2.171e+05</td> <td>  1.3e+04</td> <td>   16.703</td> <td> 0.000</td> <td> 1.92e+05</td> <td> 2.43e+05</td>
</tr>
<tr>
  <th>zipcode_98030</th>      <td> 2044.3475</td> <td> 7574.059</td> <td>    0.270</td> <td> 0.787</td> <td>-1.28e+04</td> <td> 1.69e+04</td>
</tr>
<tr>
  <th>zipcode_98031</th>      <td> 1246.2076</td> <td> 7897.203</td> <td>    0.158</td> <td> 0.875</td> <td>-1.42e+04</td> <td> 1.67e+04</td>
</tr>
<tr>
  <th>zipcode_98032</th>      <td>-1.343e+04</td> <td> 9156.535</td> <td>   -1.467</td> <td> 0.142</td> <td>-3.14e+04</td> <td> 4512.678</td>
</tr>
<tr>
  <th>zipcode_98033</th>      <td> 2.687e+05</td> <td> 1.46e+04</td> <td>   18.443</td> <td> 0.000</td> <td>  2.4e+05</td> <td> 2.97e+05</td>
</tr>
<tr>
  <th>zipcode_98034</th>      <td> 1.271e+05</td> <td> 1.55e+04</td> <td>    8.186</td> <td> 0.000</td> <td> 9.67e+04</td> <td> 1.58e+05</td>
</tr>
<tr>
  <th>zipcode_98038</th>      <td> 4.819e+04</td> <td> 8559.523</td> <td>    5.630</td> <td> 0.000</td> <td> 3.14e+04</td> <td>  6.5e+04</td>
</tr>
<tr>
  <th>zipcode_98039</th>      <td> 5.827e+05</td> <td> 4.41e+04</td> <td>   13.205</td> <td> 0.000</td> <td> 4.96e+05</td> <td> 6.69e+05</td>
</tr>
<tr>
  <th>zipcode_98040</th>      <td> 3.749e+05</td> <td>  1.2e+04</td> <td>   31.292</td> <td> 0.000</td> <td> 3.51e+05</td> <td> 3.98e+05</td>
</tr>
<tr>
  <th>zipcode_98042</th>      <td> 1.081e+04</td> <td> 7265.296</td> <td>    1.487</td> <td> 0.137</td> <td>-3434.619</td> <td>  2.5e+04</td>
</tr>
<tr>
  <th>zipcode_98045</th>      <td> 1.213e+05</td> <td> 1.59e+04</td> <td>    7.633</td> <td> 0.000</td> <td> 9.01e+04</td> <td> 1.52e+05</td>
</tr>
<tr>
  <th>zipcode_98052</th>      <td> 2.081e+05</td> <td> 1.48e+04</td> <td>   14.106</td> <td> 0.000</td> <td> 1.79e+05</td> <td> 2.37e+05</td>
</tr>
<tr>
  <th>zipcode_98053</th>      <td> 1.982e+05</td> <td> 1.58e+04</td> <td>   12.508</td> <td> 0.000</td> <td> 1.67e+05</td> <td> 2.29e+05</td>
</tr>
<tr>
  <th>zipcode_98055</th>      <td> 3.041e+04</td> <td> 8852.569</td> <td>    3.435</td> <td> 0.001</td> <td> 1.31e+04</td> <td> 4.78e+04</td>
</tr>
<tr>
  <th>zipcode_98056</th>      <td> 7.976e+04</td> <td> 9638.778</td> <td>    8.275</td> <td> 0.000</td> <td> 6.09e+04</td> <td> 9.87e+04</td>
</tr>
<tr>
  <th>zipcode_98058</th>      <td> 2.675e+04</td> <td> 8354.950</td> <td>    3.202</td> <td> 0.001</td> <td> 1.04e+04</td> <td> 4.31e+04</td>
</tr>
<tr>
  <th>zipcode_98059</th>      <td> 8.592e+04</td> <td> 9449.193</td> <td>    9.093</td> <td> 0.000</td> <td> 6.74e+04</td> <td> 1.04e+05</td>
</tr>
<tr>
  <th>zipcode_98065</th>      <td> 1.276e+05</td> <td> 1.47e+04</td> <td>    8.693</td> <td> 0.000</td> <td> 9.88e+04</td> <td> 1.56e+05</td>
</tr>
<tr>
  <th>zipcode_98070</th>      <td> 7.276e+04</td> <td> 1.13e+04</td> <td>    6.458</td> <td> 0.000</td> <td> 5.07e+04</td> <td> 9.48e+04</td>
</tr>
<tr>
  <th>zipcode_98072</th>      <td> 1.125e+05</td> <td> 1.73e+04</td> <td>    6.517</td> <td> 0.000</td> <td> 7.87e+04</td> <td> 1.46e+05</td>
</tr>
<tr>
  <th>zipcode_98074</th>      <td> 1.883e+05</td> <td>  1.4e+04</td> <td>   13.492</td> <td> 0.000</td> <td> 1.61e+05</td> <td> 2.16e+05</td>
</tr>
<tr>
  <th>zipcode_98075</th>      <td> 2.076e+05</td> <td> 1.35e+04</td> <td>   15.427</td> <td> 0.000</td> <td> 1.81e+05</td> <td> 2.34e+05</td>
</tr>
<tr>
  <th>zipcode_98077</th>      <td> 1.163e+05</td> <td>  1.8e+04</td> <td>    6.461</td> <td> 0.000</td> <td>  8.1e+04</td> <td> 1.52e+05</td>
</tr>
<tr>
  <th>zipcode_98092</th>      <td>-7103.7523</td> <td> 6871.133</td> <td>   -1.034</td> <td> 0.301</td> <td>-2.06e+04</td> <td> 6364.231</td>
</tr>
<tr>
  <th>zipcode_98102</th>      <td> 3.838e+05</td> <td> 1.52e+04</td> <td>   25.301</td> <td> 0.000</td> <td> 3.54e+05</td> <td> 4.14e+05</td>
</tr>
<tr>
  <th>zipcode_98103</th>      <td> 2.767e+05</td> <td> 1.39e+04</td> <td>   19.850</td> <td> 0.000</td> <td> 2.49e+05</td> <td> 3.04e+05</td>
</tr>
<tr>
  <th>zipcode_98105</th>      <td> 3.403e+05</td> <td> 1.46e+04</td> <td>   23.352</td> <td> 0.000</td> <td> 3.12e+05</td> <td> 3.69e+05</td>
</tr>
<tr>
  <th>zipcode_98106</th>      <td> 9.215e+04</td> <td> 1.03e+04</td> <td>    8.937</td> <td> 0.000</td> <td> 7.19e+04</td> <td> 1.12e+05</td>
</tr>
<tr>
  <th>zipcode_98107</th>      <td> 2.771e+05</td> <td> 1.44e+04</td> <td>   19.288</td> <td> 0.000</td> <td> 2.49e+05</td> <td> 3.05e+05</td>
</tr>
<tr>
  <th>zipcode_98108</th>      <td> 8.917e+04</td> <td> 1.13e+04</td> <td>    7.875</td> <td> 0.000</td> <td>  6.7e+04</td> <td> 1.11e+05</td>
</tr>
<tr>
  <th>zipcode_98109</th>      <td> 3.806e+05</td> <td> 1.53e+04</td> <td>   24.895</td> <td> 0.000</td> <td> 3.51e+05</td> <td> 4.11e+05</td>
</tr>
<tr>
  <th>zipcode_98112</th>      <td> 3.964e+05</td> <td> 1.37e+04</td> <td>   29.032</td> <td> 0.000</td> <td>  3.7e+05</td> <td> 4.23e+05</td>
</tr>
<tr>
  <th>zipcode_98115</th>      <td> 2.738e+05</td> <td> 1.42e+04</td> <td>   19.284</td> <td> 0.000</td> <td> 2.46e+05</td> <td> 3.02e+05</td>
</tr>
<tr>
  <th>zipcode_98116</th>      <td> 2.615e+05</td> <td> 1.15e+04</td> <td>   22.694</td> <td> 0.000</td> <td> 2.39e+05</td> <td> 2.84e+05</td>
</tr>
<tr>
  <th>zipcode_98117</th>      <td> 2.635e+05</td> <td> 1.44e+04</td> <td>   18.350</td> <td> 0.000</td> <td> 2.35e+05</td> <td> 2.92e+05</td>
</tr>
<tr>
  <th>zipcode_98118</th>      <td>  1.43e+05</td> <td>    1e+04</td> <td>   14.259</td> <td> 0.000</td> <td> 1.23e+05</td> <td> 1.63e+05</td>
</tr>
<tr>
  <th>zipcode_98119</th>      <td> 3.693e+05</td> <td> 1.42e+04</td> <td>   25.984</td> <td> 0.000</td> <td> 3.41e+05</td> <td> 3.97e+05</td>
</tr>
<tr>
  <th>zipcode_98122</th>      <td> 2.848e+05</td> <td> 1.25e+04</td> <td>   22.844</td> <td> 0.000</td> <td>  2.6e+05</td> <td> 3.09e+05</td>
</tr>
<tr>
  <th>zipcode_98125</th>      <td> 1.338e+05</td> <td> 1.53e+04</td> <td>    8.720</td> <td> 0.000</td> <td> 1.04e+05</td> <td> 1.64e+05</td>
</tr>
<tr>
  <th>zipcode_98126</th>      <td> 1.624e+05</td> <td> 1.05e+04</td> <td>   15.404</td> <td> 0.000</td> <td> 1.42e+05</td> <td> 1.83e+05</td>
</tr>
<tr>
  <th>zipcode_98133</th>      <td> 8.623e+04</td> <td> 1.58e+04</td> <td>    5.441</td> <td> 0.000</td> <td> 5.52e+04</td> <td> 1.17e+05</td>
</tr>
<tr>
  <th>zipcode_98136</th>      <td> 2.265e+05</td> <td> 1.08e+04</td> <td>   20.944</td> <td> 0.000</td> <td> 2.05e+05</td> <td> 2.48e+05</td>
</tr>
<tr>
  <th>zipcode_98144</th>      <td> 2.197e+05</td> <td> 1.16e+04</td> <td>   18.876</td> <td> 0.000</td> <td> 1.97e+05</td> <td> 2.43e+05</td>
</tr>
<tr>
  <th>zipcode_98146</th>      <td> 8.412e+04</td> <td> 9681.738</td> <td>    8.688</td> <td> 0.000</td> <td> 6.51e+04</td> <td> 1.03e+05</td>
</tr>
<tr>
  <th>zipcode_98148</th>      <td>  3.94e+04</td> <td>  1.3e+04</td> <td>    3.026</td> <td> 0.002</td> <td> 1.39e+04</td> <td> 6.49e+04</td>
</tr>
<tr>
  <th>zipcode_98155</th>      <td> 6.831e+04</td> <td> 1.65e+04</td> <td>    4.140</td> <td> 0.000</td> <td>  3.6e+04</td> <td> 1.01e+05</td>
</tr>
<tr>
  <th>zipcode_98166</th>      <td> 7.861e+04</td> <td> 8854.123</td> <td>    8.878</td> <td> 0.000</td> <td> 6.13e+04</td> <td>  9.6e+04</td>
</tr>
<tr>
  <th>zipcode_98168</th>      <td> 2.352e+04</td> <td> 9310.281</td> <td>    2.526</td> <td> 0.012</td> <td> 5272.091</td> <td> 4.18e+04</td>
</tr>
<tr>
  <th>zipcode_98177</th>      <td> 1.422e+05</td> <td> 1.66e+04</td> <td>    8.546</td> <td> 0.000</td> <td>  1.1e+05</td> <td> 1.75e+05</td>
</tr>
<tr>
  <th>zipcode_98178</th>      <td> 3.116e+04</td> <td> 9626.514</td> <td>    3.237</td> <td> 0.001</td> <td> 1.23e+04</td> <td>    5e+04</td>
</tr>
<tr>
  <th>zipcode_98188</th>      <td> 1.347e+04</td> <td> 9808.419</td> <td>    1.373</td> <td> 0.170</td> <td>-5756.737</td> <td> 3.27e+04</td>
</tr>
<tr>
  <th>zipcode_98198</th>      <td> 9933.1791</td> <td> 7460.514</td> <td>    1.331</td> <td> 0.183</td> <td>-4690.038</td> <td> 2.46e+04</td>
</tr>
<tr>
  <th>zipcode_98199</th>      <td> 3.118e+05</td> <td> 1.38e+04</td> <td>   22.669</td> <td> 0.000</td> <td> 2.85e+05</td> <td> 3.39e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1930.868</td> <th>  Durbin-Watson:     </th> <td>   1.806</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>6899.678</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.455</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 5.712</td>  <th>  Cond. No.          </th> <td>1.64e+08</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 1.64e+08. This might indicate that there are<br/>strong multicollinearity or other numerical problems.





    (<Figure size 360x360 with 1 Axes>,
     <AxesSubplot:xlabel='Price', ylabel='Residual'>)




    
![png](output_188_2.png)
    



    
![png](output_188_3.png)
    



```python
exog_check =['bedrooms', 'bathrooms', 'sqft_living',
        'waterfront', 'view', 'condition', 'grade','lat',
       'long', 'sqft_living15', 'sqft_lot15', 'basementyes',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes']

for col in exog_check:
    print(f'{col}-----------------')
    sm.graphics.plot_regress_exog(model_iqr6, col,plt.figure(figsize=(12,8)))
    plt.show()
    print('----------------------')
```

    bedrooms-----------------



    
![png](output_189_1.png)
    


    ----------------------
    bathrooms-----------------



    
![png](output_189_3.png)
    


    ----------------------
    sqft_living-----------------



    
![png](output_189_5.png)
    


    ----------------------
    waterfront-----------------



    
![png](output_189_7.png)
    


    ----------------------
    view-----------------



    
![png](output_189_9.png)
    


    ----------------------
    condition-----------------



    
![png](output_189_11.png)
    


    ----------------------
    grade-----------------



    
![png](output_189_13.png)
    


    ----------------------
    lat-----------------



    
![png](output_189_15.png)
    


    ----------------------
    long-----------------



    
![png](output_189_17.png)
    


    ----------------------
    sqft_living15-----------------



    
![png](output_189_19.png)
    


    ----------------------
    sqft_lot15-----------------



    
![png](output_189_21.png)
    


    ----------------------
    basementyes-----------------



    
![png](output_189_23.png)
    


    ----------------------
    living_vs_neighbor-----------------



    
![png](output_189_25.png)
    


    ----------------------
    lot_vs_neighbor-----------------



    
![png](output_189_27.png)
    


    ----------------------
    live_lot-----------------



    
![png](output_189_29.png)
    


    ----------------------
    renovated_yes-----------------



    
![png](output_189_31.png)
    


    ----------------------


### Final Model Conclusion
- R^2 0.832
- All assumptions have been met
- Using 20,235 observations

## Final Visuals


```python
df_iqr_zip2 = df_iqr_zip.copy()
cols_to_scale = ['bedrooms', 'bathrooms', 'sqft_living',
       'floors', 'waterfront', 'view', 'condition', 'grade', 'zipcode', 'lat',
       'long', 'sqft_living15', 'sqft_lot15', 'basementyes',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes']
```


```python
df_iqr_zip2[cols_to_scale] = scaler.fit_transform(df_iqr_zip2[cols_to_scale])

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>basementyes</th>
      <th>living_vs_neighbor</th>
      <th>lot_vs_neighbor</th>
      <th>live_lot</th>
      <th>renovated_yes</th>
      <th>outlier</th>
      <th>zipcode_98002</th>
      <th>zipcode_98003</th>
      <th>zipcode_98004</th>
      <th>zipcode_98005</th>
      <th>zipcode_98006</th>
      <th>zipcode_98007</th>
      <th>zipcode_98008</th>
      <th>zipcode_98010</th>
      <th>zipcode_98011</th>
      <th>zipcode_98014</th>
      <th>zipcode_98019</th>
      <th>zipcode_98022</th>
      <th>zipcode_98023</th>
      <th>zipcode_98024</th>
      <th>zipcode_98027</th>
      <th>zipcode_98028</th>
      <th>zipcode_98029</th>
      <th>zipcode_98030</th>
      <th>zipcode_98031</th>
      <th>zipcode_98032</th>
      <th>zipcode_98033</th>
      <th>zipcode_98034</th>
      <th>zipcode_98038</th>
      <th>zipcode_98039</th>
      <th>zipcode_98040</th>
      <th>zipcode_98042</th>
      <th>zipcode_98045</th>
      <th>zipcode_98052</th>
      <th>zipcode_98053</th>
      <th>zipcode_98055</th>
      <th>zipcode_98056</th>
      <th>zipcode_98058</th>
      <th>zipcode_98059</th>
      <th>zipcode_98065</th>
      <th>zipcode_98070</th>
      <th>zipcode_98072</th>
      <th>zipcode_98074</th>
      <th>zipcode_98075</th>
      <th>zipcode_98077</th>
      <th>zipcode_98092</th>
      <th>zipcode_98102</th>
      <th>zipcode_98103</th>
      <th>zipcode_98105</th>
      <th>zipcode_98106</th>
      <th>zipcode_98107</th>
      <th>zipcode_98108</th>
      <th>zipcode_98109</th>
      <th>zipcode_98112</th>
      <th>zipcode_98115</th>
      <th>zipcode_98116</th>
      <th>zipcode_98117</th>
      <th>zipcode_98118</th>
      <th>zipcode_98119</th>
      <th>zipcode_98122</th>
      <th>zipcode_98125</th>
      <th>zipcode_98126</th>
      <th>zipcode_98133</th>
      <th>zipcode_98136</th>
      <th>zipcode_98144</th>
      <th>zipcode_98146</th>
      <th>zipcode_98148</th>
      <th>zipcode_98155</th>
      <th>zipcode_98166</th>
      <th>zipcode_98168</th>
      <th>zipcode_98177</th>
      <th>zipcode_98178</th>
      <th>zipcode_98188</th>
      <th>zipcode_98198</th>
      <th>zipcode_98199</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>7129300520</td>
      <td>2014-10-13</td>
      <td>221900.00000</td>
      <td>-0.37292</td>
      <td>-1.48549</td>
      <td>-1.02942</td>
      <td>-0.88820</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>-0.51621</td>
      <td>1.86660</td>
      <td>-0.32337</td>
      <td>-0.30865</td>
      <td>-0.94823</td>
      <td>-0.25604</td>
      <td>-0.76904</td>
      <td>-0.52120</td>
      <td>-0.10071</td>
      <td>-0.41816</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>6414100192</td>
      <td>2014-12-09</td>
      <td>538000.00000</td>
      <td>-0.37292</td>
      <td>0.27683</td>
      <td>0.76661</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>-0.51621</td>
      <td>0.87250</td>
      <td>1.16303</td>
      <td>-0.74392</td>
      <td>-0.37888</td>
      <td>-0.18115</td>
      <td>1.30032</td>
      <td>1.59295</td>
      <td>-0.14249</td>
      <td>0.12412</td>
      <td>5.62937</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>5631500400</td>
      <td>2015-02-25</td>
      <td>180000.00000</td>
      <td>-1.50596</td>
      <td>-1.48549</td>
      <td>-1.55919</td>
      <td>-0.88820</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>-1.48339</td>
      <td>-0.94689</td>
      <td>1.28276</td>
      <td>-0.14016</td>
      <td>1.29662</td>
      <td>-0.16522</td>
      <td>-0.76904</td>
      <td>-2.49464</td>
      <td>0.09252</td>
      <td>-0.90780</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2487200875</td>
      <td>2014-12-09</td>
      <td>604000.00000</td>
      <td>0.76012</td>
      <td>1.33422</td>
      <td>-0.02158</td>
      <td>-0.88820</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>2.46600</td>
      <td>-0.51621</td>
      <td>1.07882</td>
      <td>-0.25535</td>
      <td>-1.26343</td>
      <td>-0.91569</td>
      <td>-0.28051</td>
      <td>1.30032</td>
      <td>1.33027</td>
      <td>-0.10071</td>
      <td>0.26199</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>1954400510</td>
      <td>2015-02-18</td>
      <td>510000.00000</td>
      <td>-0.37292</td>
      <td>-0.07563</td>
      <td>-0.38337</td>
      <td>-0.88820</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>0.45097</td>
      <td>-0.08409</td>
      <td>0.42479</td>
      <td>1.17968</td>
      <td>-0.19995</td>
      <td>-0.18627</td>
      <td>-0.76904</td>
      <td>-0.34702</td>
      <td>-0.03889</td>
      <td>-0.42161</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>20230</th>
      <td>21453</td>
      <td>1245002281</td>
      <td>2014-05-12</td>
      <td>1050000.00000</td>
      <td>0.76012</td>
      <td>2.39162</td>
      <td>1.68401</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>2.38532</td>
      <td>-0.85311</td>
      <td>0.91152</td>
      <td>0.08449</td>
      <td>0.77608</td>
      <td>-0.15434</td>
      <td>1.30032</td>
      <td>1.08418</td>
      <td>0.15427</td>
      <td>-0.08642</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>20231</th>
      <td>21461</td>
      <td>7010700308</td>
      <td>2014-11-12</td>
      <td>1010000.00000</td>
      <td>0.76012</td>
      <td>1.68669</td>
      <td>2.11041</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>1.41814</td>
      <td>2.26049</td>
      <td>0.71668</td>
      <td>-1.28450</td>
      <td>0.09286</td>
      <td>-0.31817</td>
      <td>1.30032</td>
      <td>2.59211</td>
      <td>-0.10071</td>
      <td>2.15779</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>20232</th>
      <td>21532</td>
      <td>8835770330</td>
      <td>2014-08-19</td>
      <td>1060000.00000</td>
      <td>-1.50596</td>
      <td>-0.78056</td>
      <td>0.50819</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>3.35250</td>
      <td>-0.62803</td>
      <td>-0.72649</td>
      <td>3.05413</td>
      <td>3.15106</td>
      <td>5.21972</td>
      <td>-0.76904</td>
      <td>-1.40174</td>
      <td>0.07567</td>
      <td>-1.14597</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>20233</th>
      <td>21577</td>
      <td>8672200110</td>
      <td>2015-03-17</td>
      <td>1090000.00000</td>
      <td>1.89316</td>
      <td>2.39162</td>
      <td>2.83399</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>2.86432</td>
      <td>-0.63008</td>
      <td>2.38532</td>
      <td>-0.42171</td>
      <td>-0.15191</td>
      <td>0.22490</td>
      <td>1.80090</td>
      <td>-0.16831</td>
      <td>-0.76904</td>
      <td>1.11579</td>
      <td>-0.08439</td>
      <td>0.70821</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
    <tr>
      <th>20234</th>
      <td>21590</td>
      <td>7936000429</td>
      <td>2015-03-26</td>
      <td>1010000.00000</td>
      <td>0.76012</td>
      <td>2.03915</td>
      <td>1.98120</td>
      <td>0.97397</td>
      <td>-0.04977</td>
      <td>-0.26888</td>
      <td>-0.63008</td>
      <td>1.41814</td>
      <td>1.07882</td>
      <td>-0.02226</td>
      <td>-1.29854</td>
      <td>0.20673</td>
      <td>-0.23533</td>
      <td>1.30032</td>
      <td>2.22538</td>
      <td>0.02894</td>
      <td>0.61664</td>
      <td>-0.17764</td>
      <td>False</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>1.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
      <td>0.00000</td>
    </tr>
  </tbody>
</table>
<p>20235 rows × 92 columns</p>
</div>




```python
x_targs2 = ['bedrooms', 'bathrooms', 'sqft_living',
       'waterfront', 'view', 'condition', 'grade',
       'sqft_living15', 'sqft_lot15', 'basementyes',
       'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot', 'renovated_yes',
        'zipcode_98002', 'zipcode_98003', 'zipcode_98004',
       'zipcode_98005', 'zipcode_98006', 'zipcode_98007', 'zipcode_98008',
       'zipcode_98010', 'zipcode_98011', 'zipcode_98014', 'zipcode_98019',
       'zipcode_98022', 'zipcode_98023', 'zipcode_98024', 'zipcode_98027',
       'zipcode_98028', 'zipcode_98029', 'zipcode_98030', 'zipcode_98031',
       'zipcode_98032', 'zipcode_98033', 'zipcode_98034', 'zipcode_98038',
       'zipcode_98039', 'zipcode_98040', 'zipcode_98042', 'zipcode_98045',
       'zipcode_98052', 'zipcode_98053', 'zipcode_98055', 'zipcode_98056',
       'zipcode_98058', 'zipcode_98059', 'zipcode_98065', 'zipcode_98070',
       'zipcode_98072', 'zipcode_98074', 'zipcode_98075', 'zipcode_98077',
       'zipcode_98092', 'zipcode_98102', 'zipcode_98103', 'zipcode_98105',
       'zipcode_98106', 'zipcode_98107', 'zipcode_98108', 'zipcode_98109',
       'zipcode_98112', 'zipcode_98115', 'zipcode_98116', 'zipcode_98117',
       'zipcode_98118', 'zipcode_98119', 'zipcode_98122', 'zipcode_98125',
       'zipcode_98126', 'zipcode_98133', 'zipcode_98136', 'zipcode_98144',
       'zipcode_98146', 'zipcode_98148', 'zipcode_98155', 'zipcode_98166',
       'zipcode_98168', 'zipcode_98177', 'zipcode_98178', 'zipcode_98188',
       'zipcode_98198', 'zipcode_98199']
```


```python
model_iqr7 = model_summary(df_iqr_zip, x_targs2, 'price')
```


<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.832</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.831</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   1199.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Fri, 16 Apr 2021</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>15:25:23</td>     <th>  Log-Likelihood:    </th> <td>-2.5833e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 20235</td>      <th>  AIC:               </th>  <td>5.168e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 20151</td>      <th>  BIC:               </th>  <td>5.175e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    83</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td>-4.178e+05</td> <td> 1.04e+04</td> <td>  -40.365</td> <td> 0.000</td> <td>-4.38e+05</td> <td>-3.98e+05</td>
</tr>
<tr>
  <th>bedrooms</th>           <td>-5161.2975</td> <td>  905.928</td> <td>   -5.697</td> <td> 0.000</td> <td>-6936.991</td> <td>-3385.604</td>
</tr>
<tr>
  <th>bathrooms</th>          <td> 9536.8698</td> <td> 1382.927</td> <td>    6.896</td> <td> 0.000</td> <td> 6826.220</td> <td> 1.22e+04</td>
</tr>
<tr>
  <th>sqft_living</th>        <td>   77.4319</td> <td>    3.645</td> <td>   21.245</td> <td> 0.000</td> <td>   70.288</td> <td>   84.576</td>
</tr>
<tr>
  <th>waterfront</th>         <td> 1.638e+05</td> <td> 1.29e+04</td> <td>   12.688</td> <td> 0.000</td> <td> 1.38e+05</td> <td> 1.89e+05</td>
</tr>
<tr>
  <th>view</th>               <td> 2.969e+04</td> <td> 1048.149</td> <td>   28.324</td> <td> 0.000</td> <td> 2.76e+04</td> <td> 3.17e+04</td>
</tr>
<tr>
  <th>condition</th>          <td> 2.515e+04</td> <td> 1003.636</td> <td>   25.056</td> <td> 0.000</td> <td> 2.32e+04</td> <td> 2.71e+04</td>
</tr>
<tr>
  <th>grade</th>              <td> 4.261e+04</td> <td>  967.985</td> <td>   44.021</td> <td> 0.000</td> <td> 4.07e+04</td> <td> 4.45e+04</td>
</tr>
<tr>
  <th>sqft_living15</th>      <td>   62.3358</td> <td>    3.868</td> <td>   16.117</td> <td> 0.000</td> <td>   54.755</td> <td>   69.917</td>
</tr>
<tr>
  <th>sqft_lot15</th>         <td>    0.2003</td> <td>    0.026</td> <td>    7.621</td> <td> 0.000</td> <td>    0.149</td> <td>    0.252</td>
</tr>
<tr>
  <th>basementyes</th>        <td>-1.607e+04</td> <td> 1406.623</td> <td>  -11.428</td> <td> 0.000</td> <td>-1.88e+04</td> <td>-1.33e+04</td>
</tr>
<tr>
  <th>living_vs_neighbor</th> <td>  4.53e+04</td> <td> 6232.820</td> <td>    7.268</td> <td> 0.000</td> <td> 3.31e+04</td> <td> 5.75e+04</td>
</tr>
<tr>
  <th>lot_vs_neighbor</th>    <td> 4740.5673</td> <td>  490.214</td> <td>    9.670</td> <td> 0.000</td> <td> 3779.708</td> <td> 5701.427</td>
</tr>
<tr>
  <th>live_lot</th>           <td>-6.085e+04</td> <td> 3080.042</td> <td>  -19.755</td> <td> 0.000</td> <td>-6.69e+04</td> <td>-5.48e+04</td>
</tr>
<tr>
  <th>renovated_yes</th>      <td> 4.506e+04</td> <td> 3537.057</td> <td>   12.738</td> <td> 0.000</td> <td> 3.81e+04</td> <td>  5.2e+04</td>
</tr>
<tr>
  <th>zipcode_98002</th>      <td> 1.339e+04</td> <td> 7565.333</td> <td>    1.770</td> <td> 0.077</td> <td>-1437.174</td> <td> 2.82e+04</td>
</tr>
<tr>
  <th>zipcode_98003</th>      <td>-3274.6114</td> <td> 6811.016</td> <td>   -0.481</td> <td> 0.631</td> <td>-1.66e+04</td> <td> 1.01e+04</td>
</tr>
<tr>
  <th>zipcode_98004</th>      <td> 5.097e+05</td> <td> 8337.762</td> <td>   61.127</td> <td> 0.000</td> <td> 4.93e+05</td> <td> 5.26e+05</td>
</tr>
<tr>
  <th>zipcode_98005</th>      <td> 3.255e+05</td> <td> 8325.123</td> <td>   39.101</td> <td> 0.000</td> <td> 3.09e+05</td> <td> 3.42e+05</td>
</tr>
<tr>
  <th>zipcode_98006</th>      <td> 2.684e+05</td> <td> 6277.359</td> <td>   42.759</td> <td> 0.000</td> <td> 2.56e+05</td> <td> 2.81e+05</td>
</tr>
<tr>
  <th>zipcode_98007</th>      <td> 2.608e+05</td> <td> 8606.802</td> <td>   30.297</td> <td> 0.000</td> <td> 2.44e+05</td> <td> 2.78e+05</td>
</tr>
<tr>
  <th>zipcode_98008</th>      <td> 2.461e+05</td> <td> 6901.242</td> <td>   35.666</td> <td> 0.000</td> <td> 2.33e+05</td> <td>  2.6e+05</td>
</tr>
<tr>
  <th>zipcode_98010</th>      <td> 8.242e+04</td> <td> 9696.224</td> <td>    8.500</td> <td> 0.000</td> <td> 6.34e+04</td> <td> 1.01e+05</td>
</tr>
<tr>
  <th>zipcode_98011</th>      <td> 1.455e+05</td> <td> 7593.212</td> <td>   19.164</td> <td> 0.000</td> <td> 1.31e+05</td> <td>  1.6e+05</td>
</tr>
<tr>
  <th>zipcode_98014</th>      <td> 1.065e+05</td> <td> 9104.655</td> <td>   11.698</td> <td> 0.000</td> <td> 8.87e+04</td> <td> 1.24e+05</td>
</tr>
<tr>
  <th>zipcode_98019</th>      <td> 9.728e+04</td> <td> 7666.476</td> <td>   12.689</td> <td> 0.000</td> <td> 8.23e+04</td> <td> 1.12e+05</td>
</tr>
<tr>
  <th>zipcode_98022</th>      <td> 4449.2990</td> <td> 7258.397</td> <td>    0.613</td> <td> 0.540</td> <td>-9777.752</td> <td> 1.87e+04</td>
</tr>
<tr>
  <th>zipcode_98023</th>      <td>-2.138e+04</td> <td> 5916.673</td> <td>   -3.613</td> <td> 0.000</td> <td> -3.3e+04</td> <td>-9778.715</td>
</tr>
<tr>
  <th>zipcode_98024</th>      <td> 1.542e+05</td> <td> 1.11e+04</td> <td>   13.913</td> <td> 0.000</td> <td> 1.32e+05</td> <td> 1.76e+05</td>
</tr>
<tr>
  <th>zipcode_98027</th>      <td> 1.959e+05</td> <td> 6281.542</td> <td>   31.194</td> <td> 0.000</td> <td> 1.84e+05</td> <td> 2.08e+05</td>
</tr>
<tr>
  <th>zipcode_98028</th>      <td> 1.345e+05</td> <td> 6786.217</td> <td>   19.821</td> <td> 0.000</td> <td> 1.21e+05</td> <td> 1.48e+05</td>
</tr>
<tr>
  <th>zipcode_98029</th>      <td> 2.361e+05</td> <td> 6648.370</td> <td>   35.513</td> <td> 0.000</td> <td> 2.23e+05</td> <td> 2.49e+05</td>
</tr>
<tr>
  <th>zipcode_98030</th>      <td> 5178.4013</td> <td> 6979.656</td> <td>    0.742</td> <td> 0.458</td> <td>-8502.295</td> <td> 1.89e+04</td>
</tr>
<tr>
  <th>zipcode_98031</th>      <td> 1.009e+04</td> <td> 6846.474</td> <td>    1.473</td> <td> 0.141</td> <td>-3334.552</td> <td> 2.35e+04</td>
</tr>
<tr>
  <th>zipcode_98032</th>      <td>-2113.7100</td> <td> 8891.841</td> <td>   -0.238</td> <td> 0.812</td> <td>-1.95e+04</td> <td> 1.53e+04</td>
</tr>
<tr>
  <th>zipcode_98033</th>      <td> 3.231e+05</td> <td> 6338.465</td> <td>   50.968</td> <td> 0.000</td> <td> 3.11e+05</td> <td> 3.35e+05</td>
</tr>
<tr>
  <th>zipcode_98034</th>      <td> 1.899e+05</td> <td> 5832.840</td> <td>   32.550</td> <td> 0.000</td> <td> 1.78e+05</td> <td> 2.01e+05</td>
</tr>
<tr>
  <th>zipcode_98038</th>      <td>  3.84e+04</td> <td> 5732.358</td> <td>    6.699</td> <td> 0.000</td> <td> 2.72e+04</td> <td> 4.96e+04</td>
</tr>
<tr>
  <th>zipcode_98039</th>      <td> 6.324e+05</td> <td> 4.27e+04</td> <td>   14.802</td> <td> 0.000</td> <td> 5.49e+05</td> <td> 7.16e+05</td>
</tr>
<tr>
  <th>zipcode_98040</th>      <td> 4.126e+05</td> <td> 8110.533</td> <td>   50.876</td> <td> 0.000</td> <td> 3.97e+05</td> <td> 4.29e+05</td>
</tr>
<tr>
  <th>zipcode_98042</th>      <td> 7228.6196</td> <td> 5786.201</td> <td>    1.249</td> <td> 0.212</td> <td>-4112.807</td> <td> 1.86e+04</td>
</tr>
<tr>
  <th>zipcode_98045</th>      <td> 1.059e+05</td> <td> 7347.501</td> <td>   14.410</td> <td> 0.000</td> <td> 9.15e+04</td> <td>  1.2e+05</td>
</tr>
<tr>
  <th>zipcode_98052</th>      <td> 2.569e+05</td> <td> 5795.624</td> <td>   44.318</td> <td> 0.000</td> <td> 2.45e+05</td> <td> 2.68e+05</td>
</tr>
<tr>
  <th>zipcode_98053</th>      <td>  2.39e+05</td> <td> 6340.531</td> <td>   37.698</td> <td> 0.000</td> <td> 2.27e+05</td> <td> 2.51e+05</td>
</tr>
<tr>
  <th>zipcode_98055</th>      <td> 4.933e+04</td> <td> 6926.829</td> <td>    7.122</td> <td> 0.000</td> <td> 3.58e+04</td> <td> 6.29e+04</td>
</tr>
<tr>
  <th>zipcode_98056</th>      <td> 1.055e+05</td> <td> 6193.430</td> <td>   17.042</td> <td> 0.000</td> <td> 9.34e+04</td> <td> 1.18e+05</td>
</tr>
<tr>
  <th>zipcode_98058</th>      <td> 3.899e+04</td> <td> 6027.017</td> <td>    6.469</td> <td> 0.000</td> <td> 2.72e+04</td> <td> 5.08e+04</td>
</tr>
<tr>
  <th>zipcode_98059</th>      <td> 1.051e+05</td> <td> 6051.123</td> <td>   17.366</td> <td> 0.000</td> <td> 9.32e+04</td> <td> 1.17e+05</td>
</tr>
<tr>
  <th>zipcode_98065</th>      <td> 1.302e+05</td> <td> 6728.480</td> <td>   19.346</td> <td> 0.000</td> <td> 1.17e+05</td> <td> 1.43e+05</td>
</tr>
<tr>
  <th>zipcode_98070</th>      <td> 1.077e+05</td> <td> 9544.288</td> <td>   11.281</td> <td> 0.000</td> <td>  8.9e+04</td> <td> 1.26e+05</td>
</tr>
<tr>
  <th>zipcode_98072</th>      <td> 1.741e+05</td> <td> 6937.978</td> <td>   25.093</td> <td> 0.000</td> <td>  1.6e+05</td> <td> 1.88e+05</td>
</tr>
<tr>
  <th>zipcode_98074</th>      <td> 2.214e+05</td> <td> 6204.011</td> <td>   35.688</td> <td> 0.000</td> <td> 2.09e+05</td> <td> 2.34e+05</td>
</tr>
<tr>
  <th>zipcode_98075</th>      <td> 2.327e+05</td> <td> 6642.941</td> <td>   35.025</td> <td> 0.000</td> <td>  2.2e+05</td> <td> 2.46e+05</td>
</tr>
<tr>
  <th>zipcode_98077</th>      <td> 1.714e+05</td> <td> 7811.598</td> <td>   21.948</td> <td> 0.000</td> <td> 1.56e+05</td> <td> 1.87e+05</td>
</tr>
<tr>
  <th>zipcode_98092</th>      <td>-1.677e+04</td> <td> 6410.629</td> <td>   -2.616</td> <td> 0.009</td> <td>-2.93e+04</td> <td>-4203.738</td>
</tr>
<tr>
  <th>zipcode_98102</th>      <td> 4.415e+05</td> <td> 1.03e+04</td> <td>   43.039</td> <td> 0.000</td> <td> 4.21e+05</td> <td> 4.62e+05</td>
</tr>
<tr>
  <th>zipcode_98103</th>      <td> 3.433e+05</td> <td> 5867.614</td> <td>   58.515</td> <td> 0.000</td> <td> 3.32e+05</td> <td> 3.55e+05</td>
</tr>
<tr>
  <th>zipcode_98105</th>      <td> 4.016e+05</td> <td> 7885.909</td> <td>   50.921</td> <td> 0.000</td> <td> 3.86e+05</td> <td> 4.17e+05</td>
</tr>
<tr>
  <th>zipcode_98106</th>      <td> 1.368e+05</td> <td> 6550.564</td> <td>   20.881</td> <td> 0.000</td> <td> 1.24e+05</td> <td>  1.5e+05</td>
</tr>
<tr>
  <th>zipcode_98107</th>      <td> 3.452e+05</td> <td> 7065.722</td> <td>   48.852</td> <td> 0.000</td> <td> 3.31e+05</td> <td> 3.59e+05</td>
</tr>
<tr>
  <th>zipcode_98108</th>      <td> 1.319e+05</td> <td> 7729.096</td> <td>   17.060</td> <td> 0.000</td> <td> 1.17e+05</td> <td> 1.47e+05</td>
</tr>
<tr>
  <th>zipcode_98109</th>      <td> 4.408e+05</td> <td> 1.04e+04</td> <td>   42.555</td> <td> 0.000</td> <td> 4.21e+05</td> <td> 4.61e+05</td>
</tr>
<tr>
  <th>zipcode_98112</th>      <td> 4.512e+05</td> <td> 8144.999</td> <td>   55.396</td> <td> 0.000</td> <td> 4.35e+05</td> <td> 4.67e+05</td>
</tr>
<tr>
  <th>zipcode_98115</th>      <td> 3.385e+05</td> <td> 5839.704</td> <td>   57.965</td> <td> 0.000</td> <td> 3.27e+05</td> <td>  3.5e+05</td>
</tr>
<tr>
  <th>zipcode_98116</th>      <td> 3.152e+05</td> <td> 6690.429</td> <td>   47.112</td> <td> 0.000</td> <td> 3.02e+05</td> <td> 3.28e+05</td>
</tr>
<tr>
  <th>zipcode_98117</th>      <td> 3.348e+05</td> <td> 5879.461</td> <td>   56.940</td> <td> 0.000</td> <td> 3.23e+05</td> <td> 3.46e+05</td>
</tr>
<tr>
  <th>zipcode_98118</th>      <td> 1.821e+05</td> <td> 5950.319</td> <td>   30.602</td> <td> 0.000</td> <td>  1.7e+05</td> <td> 1.94e+05</td>
</tr>
<tr>
  <th>zipcode_98119</th>      <td> 4.318e+05</td> <td> 8373.001</td> <td>   51.573</td> <td> 0.000</td> <td> 4.15e+05</td> <td> 4.48e+05</td>
</tr>
<tr>
  <th>zipcode_98122</th>      <td> 3.367e+05</td> <td> 7000.568</td> <td>   48.101</td> <td> 0.000</td> <td> 3.23e+05</td> <td>  3.5e+05</td>
</tr>
<tr>
  <th>zipcode_98125</th>      <td> 2.038e+05</td> <td> 6230.096</td> <td>   32.714</td> <td> 0.000</td> <td> 1.92e+05</td> <td> 2.16e+05</td>
</tr>
<tr>
  <th>zipcode_98126</th>      <td>   2.1e+05</td> <td> 6455.887</td> <td>   32.528</td> <td> 0.000</td> <td> 1.97e+05</td> <td> 2.23e+05</td>
</tr>
<tr>
  <th>zipcode_98133</th>      <td> 1.628e+05</td> <td> 5956.966</td> <td>   27.325</td> <td> 0.000</td> <td> 1.51e+05</td> <td> 1.74e+05</td>
</tr>
<tr>
  <th>zipcode_98136</th>      <td>  2.74e+05</td> <td> 7035.424</td> <td>   38.948</td> <td> 0.000</td> <td>  2.6e+05</td> <td> 2.88e+05</td>
</tr>
<tr>
  <th>zipcode_98144</th>      <td> 2.676e+05</td> <td> 6696.256</td> <td>   39.966</td> <td> 0.000</td> <td> 2.54e+05</td> <td> 2.81e+05</td>
</tr>
<tr>
  <th>zipcode_98146</th>      <td> 1.234e+05</td> <td> 6834.495</td> <td>   18.051</td> <td> 0.000</td> <td>  1.1e+05</td> <td> 1.37e+05</td>
</tr>
<tr>
  <th>zipcode_98148</th>      <td> 6.546e+04</td> <td> 1.22e+04</td> <td>    5.361</td> <td> 0.000</td> <td> 4.15e+04</td> <td> 8.94e+04</td>
</tr>
<tr>
  <th>zipcode_98155</th>      <td> 1.449e+05</td> <td> 6069.676</td> <td>   23.866</td> <td> 0.000</td> <td> 1.33e+05</td> <td> 1.57e+05</td>
</tr>
<tr>
  <th>zipcode_98166</th>      <td> 1.095e+05</td> <td> 7098.709</td> <td>   15.424</td> <td> 0.000</td> <td> 9.56e+04</td> <td> 1.23e+05</td>
</tr>
<tr>
  <th>zipcode_98168</th>      <td>  5.65e+04</td> <td> 6924.626</td> <td>    8.159</td> <td> 0.000</td> <td> 4.29e+04</td> <td> 7.01e+04</td>
</tr>
<tr>
  <th>zipcode_98177</th>      <td> 2.221e+05</td> <td> 7238.622</td> <td>   30.677</td> <td> 0.000</td> <td> 2.08e+05</td> <td> 2.36e+05</td>
</tr>
<tr>
  <th>zipcode_98178</th>      <td> 6.058e+04</td> <td> 6988.124</td> <td>    8.669</td> <td> 0.000</td> <td> 4.69e+04</td> <td> 7.43e+04</td>
</tr>
<tr>
  <th>zipcode_98188</th>      <td>  3.72e+04</td> <td> 8585.549</td> <td>    4.333</td> <td> 0.000</td> <td> 2.04e+04</td> <td>  5.4e+04</td>
</tr>
<tr>
  <th>zipcode_98198</th>      <td> 2.718e+04</td> <td> 6855.112</td> <td>    3.964</td> <td> 0.000</td> <td> 1.37e+04</td> <td> 4.06e+04</td>
</tr>
<tr>
  <th>zipcode_98199</th>      <td> 3.782e+05</td> <td> 6937.974</td> <td>   54.506</td> <td> 0.000</td> <td> 3.65e+05</td> <td> 3.92e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1931.779</td> <th>  Durbin-Watson:     </th> <td>   1.806</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>6935.425</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.454</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 5.721</td>  <th>  Cond. No.          </th> <td>2.14e+06</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.14e+06. This might indicate that there are<br/>strong multicollinearity or other numerical problems.



    
![png](output_195_1.png)
    



```python
df_coeff=pd.DataFrame({'coeff': model_iqr7.params, 'abs_coeff': abs(model_iqr7.params)})
```


```python
df_coeff.drop('Intercept', axis=0).sort_values(by='abs_coeff').tail(15).plot(kind='barh', y='coeff', figsize=(8,8))
```




    <AxesSubplot:>




    
![png](output_197_1.png)
    



```python
df_coeff2 = df_coeff.copy()
```


```python
df_coeff2.index
indices = ['Intercept', 'bedrooms', 'bathrooms', 'sqft_living', 'waterfront',
       'view', 'condition', 'grade', 'sqft_living15', 'sqft_lot15',
       'basementyes', 'living_vs_neighbor', 'lot_vs_neighbor', 'live_lot',
       'renovated_yes', 'zipcode_98002', 'zipcode_98003', 'zipcode_98004',
       'zipcode_98005', 'zipcode_98006', 'zipcode_98007', 'zipcode_98008',
       'zipcode_98010', 'zipcode_98011', 'zipcode_98014', 'zipcode_98019',
       'zipcode_98022', 'zipcode_98023', 'zipcode_98024', 'zipcode_98027',
       'zipcode_98028', 'zipcode_98029', 'zipcode_98030', 'zipcode_98031',
       'zipcode_98032', 'zipcode_98033', 'zipcode_98034', 'zipcode_98038',
       'zipcode_98039', 'zipcode_98040', 'zipcode_98042', 'zipcode_98045',
       'zipcode_98052', 'zipcode_98053', 'zipcode_98055', 'zipcode_98056',
       'zipcode_98058', 'zipcode_98059', 'zipcode_98065', 'zipcode_98070',
       'zipcode_98072', 'zipcode_98074', 'zipcode_98075', 'zipcode_98077',
       'zipcode_98092', 'zipcode_98102', 'zipcode_98103', 'zipcode_98105',
       'zipcode_98106', 'zipcode_98107', 'zipcode_98108', 'zipcode_98109',
       'zipcode_98112', 'zipcode_98115', 'zipcode_98116', 'zipcode_98117',
       'zipcode_98118', 'zipcode_98119', 'zipcode_98122', 'zipcode_98125',
       'zipcode_98126', 'zipcode_98133', 'zipcode_98136', 'zipcode_98144',
       'zipcode_98146', 'zipcode_98148', 'zipcode_98155', 'zipcode_98166',
       'zipcode_98168', 'zipcode_98177', 'zipcode_98178', 'zipcode_98188',
       'zipcode_98198', 'zipcode_98199']
```


```python
non_zip = []
for ind in indices:
    if ind.startswith('zip') or ind.startswith('Int'):
        pass
    else:
        non_zip.append(ind)
```


```python
df_coeff2.drop('Intercept', axis=0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>coeff</th>
      <th>abs_coeff</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bedrooms</th>
      <td>-5161.29749</td>
      <td>5161.29749</td>
    </tr>
    <tr>
      <th>bathrooms</th>
      <td>9536.86983</td>
      <td>9536.86983</td>
    </tr>
    <tr>
      <th>sqft_living</th>
      <td>77.43192</td>
      <td>77.43192</td>
    </tr>
    <tr>
      <th>waterfront</th>
      <td>163793.16672</td>
      <td>163793.16672</td>
    </tr>
    <tr>
      <th>view</th>
      <td>29687.68670</td>
      <td>29687.68670</td>
    </tr>
    <tr>
      <th>condition</th>
      <td>25147.42513</td>
      <td>25147.42513</td>
    </tr>
    <tr>
      <th>grade</th>
      <td>42612.05019</td>
      <td>42612.05019</td>
    </tr>
    <tr>
      <th>sqft_living15</th>
      <td>62.33575</td>
      <td>62.33575</td>
    </tr>
    <tr>
      <th>sqft_lot15</th>
      <td>0.20032</td>
      <td>0.20032</td>
    </tr>
    <tr>
      <th>basementyes</th>
      <td>-16074.24717</td>
      <td>16074.24717</td>
    </tr>
    <tr>
      <th>living_vs_neighbor</th>
      <td>45297.52906</td>
      <td>45297.52906</td>
    </tr>
    <tr>
      <th>lot_vs_neighbor</th>
      <td>4740.56730</td>
      <td>4740.56730</td>
    </tr>
    <tr>
      <th>live_lot</th>
      <td>-60847.34489</td>
      <td>60847.34489</td>
    </tr>
    <tr>
      <th>renovated_yes</th>
      <td>45056.66921</td>
      <td>45056.66921</td>
    </tr>
    <tr>
      <th>zipcode_98002</th>
      <td>13391.49638</td>
      <td>13391.49638</td>
    </tr>
    <tr>
      <th>zipcode_98003</th>
      <td>-3274.61140</td>
      <td>3274.61140</td>
    </tr>
    <tr>
      <th>zipcode_98004</th>
      <td>509660.44384</td>
      <td>509660.44384</td>
    </tr>
    <tr>
      <th>zipcode_98005</th>
      <td>325517.94583</td>
      <td>325517.94583</td>
    </tr>
    <tr>
      <th>zipcode_98006</th>
      <td>268415.47201</td>
      <td>268415.47201</td>
    </tr>
    <tr>
      <th>zipcode_98007</th>
      <td>260758.75232</td>
      <td>260758.75232</td>
    </tr>
    <tr>
      <th>zipcode_98008</th>
      <td>246142.95301</td>
      <td>246142.95301</td>
    </tr>
    <tr>
      <th>zipcode_98010</th>
      <td>82421.02307</td>
      <td>82421.02307</td>
    </tr>
    <tr>
      <th>zipcode_98011</th>
      <td>145513.27777</td>
      <td>145513.27777</td>
    </tr>
    <tr>
      <th>zipcode_98014</th>
      <td>106505.99028</td>
      <td>106505.99028</td>
    </tr>
    <tr>
      <th>zipcode_98019</th>
      <td>97278.06907</td>
      <td>97278.06907</td>
    </tr>
    <tr>
      <th>zipcode_98022</th>
      <td>4449.29897</td>
      <td>4449.29897</td>
    </tr>
    <tr>
      <th>zipcode_98023</th>
      <td>-21375.87779</td>
      <td>21375.87779</td>
    </tr>
    <tr>
      <th>zipcode_98024</th>
      <td>154185.19745</td>
      <td>154185.19745</td>
    </tr>
    <tr>
      <th>zipcode_98027</th>
      <td>195949.43814</td>
      <td>195949.43814</td>
    </tr>
    <tr>
      <th>zipcode_98028</th>
      <td>134508.52254</td>
      <td>134508.52254</td>
    </tr>
    <tr>
      <th>zipcode_98029</th>
      <td>236106.61928</td>
      <td>236106.61928</td>
    </tr>
    <tr>
      <th>zipcode_98030</th>
      <td>5178.40134</td>
      <td>5178.40134</td>
    </tr>
    <tr>
      <th>zipcode_98031</th>
      <td>10085.09748</td>
      <td>10085.09748</td>
    </tr>
    <tr>
      <th>zipcode_98032</th>
      <td>-2113.70998</td>
      <td>2113.70998</td>
    </tr>
    <tr>
      <th>zipcode_98033</th>
      <td>323060.06537</td>
      <td>323060.06537</td>
    </tr>
    <tr>
      <th>zipcode_98034</th>
      <td>189856.60977</td>
      <td>189856.60977</td>
    </tr>
    <tr>
      <th>zipcode_98038</th>
      <td>38403.13402</td>
      <td>38403.13402</td>
    </tr>
    <tr>
      <th>zipcode_98039</th>
      <td>632420.46815</td>
      <td>632420.46815</td>
    </tr>
    <tr>
      <th>zipcode_98040</th>
      <td>412631.59688</td>
      <td>412631.59688</td>
    </tr>
    <tr>
      <th>zipcode_98042</th>
      <td>7228.61956</td>
      <td>7228.61956</td>
    </tr>
    <tr>
      <th>zipcode_98045</th>
      <td>105879.51968</td>
      <td>105879.51968</td>
    </tr>
    <tr>
      <th>zipcode_98052</th>
      <td>256851.57623</td>
      <td>256851.57623</td>
    </tr>
    <tr>
      <th>zipcode_98053</th>
      <td>239028.15153</td>
      <td>239028.15153</td>
    </tr>
    <tr>
      <th>zipcode_98055</th>
      <td>49334.61469</td>
      <td>49334.61469</td>
    </tr>
    <tr>
      <th>zipcode_98056</th>
      <td>105547.34724</td>
      <td>105547.34724</td>
    </tr>
    <tr>
      <th>zipcode_98058</th>
      <td>38986.31578</td>
      <td>38986.31578</td>
    </tr>
    <tr>
      <th>zipcode_98059</th>
      <td>105082.71471</td>
      <td>105082.71471</td>
    </tr>
    <tr>
      <th>zipcode_98065</th>
      <td>130167.05785</td>
      <td>130167.05785</td>
    </tr>
    <tr>
      <th>zipcode_98070</th>
      <td>107672.26474</td>
      <td>107672.26474</td>
    </tr>
    <tr>
      <th>zipcode_98072</th>
      <td>174097.80981</td>
      <td>174097.80981</td>
    </tr>
    <tr>
      <th>zipcode_98074</th>
      <td>221408.51107</td>
      <td>221408.51107</td>
    </tr>
    <tr>
      <th>zipcode_98075</th>
      <td>232667.83746</td>
      <td>232667.83746</td>
    </tr>
    <tr>
      <th>zipcode_98077</th>
      <td>171449.30182</td>
      <td>171449.30182</td>
    </tr>
    <tr>
      <th>zipcode_98092</th>
      <td>-16769.09437</td>
      <td>16769.09437</td>
    </tr>
    <tr>
      <th>zipcode_98102</th>
      <td>441545.35223</td>
      <td>441545.35223</td>
    </tr>
    <tr>
      <th>zipcode_98103</th>
      <td>343341.39033</td>
      <td>343341.39033</td>
    </tr>
    <tr>
      <th>zipcode_98105</th>
      <td>401556.63727</td>
      <td>401556.63727</td>
    </tr>
    <tr>
      <th>zipcode_98106</th>
      <td>136783.10979</td>
      <td>136783.10979</td>
    </tr>
    <tr>
      <th>zipcode_98107</th>
      <td>345171.59372</td>
      <td>345171.59372</td>
    </tr>
    <tr>
      <th>zipcode_98108</th>
      <td>131859.60516</td>
      <td>131859.60516</td>
    </tr>
    <tr>
      <th>zipcode_98109</th>
      <td>440810.60144</td>
      <td>440810.60144</td>
    </tr>
    <tr>
      <th>zipcode_98112</th>
      <td>451202.47952</td>
      <td>451202.47952</td>
    </tr>
    <tr>
      <th>zipcode_98115</th>
      <td>338496.96515</td>
      <td>338496.96515</td>
    </tr>
    <tr>
      <th>zipcode_98116</th>
      <td>315201.46765</td>
      <td>315201.46765</td>
    </tr>
    <tr>
      <th>zipcode_98117</th>
      <td>334776.00539</td>
      <td>334776.00539</td>
    </tr>
    <tr>
      <th>zipcode_98118</th>
      <td>182092.45645</td>
      <td>182092.45645</td>
    </tr>
    <tr>
      <th>zipcode_98119</th>
      <td>431820.43551</td>
      <td>431820.43551</td>
    </tr>
    <tr>
      <th>zipcode_98122</th>
      <td>336734.74127</td>
      <td>336734.74127</td>
    </tr>
    <tr>
      <th>zipcode_98125</th>
      <td>203810.81539</td>
      <td>203810.81539</td>
    </tr>
    <tr>
      <th>zipcode_98126</th>
      <td>209998.71003</td>
      <td>209998.71003</td>
    </tr>
    <tr>
      <th>zipcode_98133</th>
      <td>162773.14716</td>
      <td>162773.14716</td>
    </tr>
    <tr>
      <th>zipcode_98136</th>
      <td>274012.76214</td>
      <td>274012.76214</td>
    </tr>
    <tr>
      <th>zipcode_98144</th>
      <td>267624.56206</td>
      <td>267624.56206</td>
    </tr>
    <tr>
      <th>zipcode_98146</th>
      <td>123372.16774</td>
      <td>123372.16774</td>
    </tr>
    <tr>
      <th>zipcode_98148</th>
      <td>65463.75880</td>
      <td>65463.75880</td>
    </tr>
    <tr>
      <th>zipcode_98155</th>
      <td>144861.04462</td>
      <td>144861.04462</td>
    </tr>
    <tr>
      <th>zipcode_98166</th>
      <td>109487.35262</td>
      <td>109487.35262</td>
    </tr>
    <tr>
      <th>zipcode_98168</th>
      <td>56495.66450</td>
      <td>56495.66450</td>
    </tr>
    <tr>
      <th>zipcode_98177</th>
      <td>222057.21343</td>
      <td>222057.21343</td>
    </tr>
    <tr>
      <th>zipcode_98178</th>
      <td>60579.28819</td>
      <td>60579.28819</td>
    </tr>
    <tr>
      <th>zipcode_98188</th>
      <td>37199.74745</td>
      <td>37199.74745</td>
    </tr>
    <tr>
      <th>zipcode_98198</th>
      <td>27176.89978</td>
      <td>27176.89978</td>
    </tr>
    <tr>
      <th>zipcode_98199</th>
      <td>378160.98415</td>
      <td>378160.98415</td>
    </tr>
  </tbody>
</table>
</div>




```python
zips = []
for ind in indices:
    if ind.startswith('zip'):
        zips.append(ind)
    else:
        pass
zips
```




    ['zipcode_98002',
     'zipcode_98003',
     'zipcode_98004',
     'zipcode_98005',
     'zipcode_98006',
     'zipcode_98007',
     'zipcode_98008',
     'zipcode_98010',
     'zipcode_98011',
     'zipcode_98014',
     'zipcode_98019',
     'zipcode_98022',
     'zipcode_98023',
     'zipcode_98024',
     'zipcode_98027',
     'zipcode_98028',
     'zipcode_98029',
     'zipcode_98030',
     'zipcode_98031',
     'zipcode_98032',
     'zipcode_98033',
     'zipcode_98034',
     'zipcode_98038',
     'zipcode_98039',
     'zipcode_98040',
     'zipcode_98042',
     'zipcode_98045',
     'zipcode_98052',
     'zipcode_98053',
     'zipcode_98055',
     'zipcode_98056',
     'zipcode_98058',
     'zipcode_98059',
     'zipcode_98065',
     'zipcode_98070',
     'zipcode_98072',
     'zipcode_98074',
     'zipcode_98075',
     'zipcode_98077',
     'zipcode_98092',
     'zipcode_98102',
     'zipcode_98103',
     'zipcode_98105',
     'zipcode_98106',
     'zipcode_98107',
     'zipcode_98108',
     'zipcode_98109',
     'zipcode_98112',
     'zipcode_98115',
     'zipcode_98116',
     'zipcode_98117',
     'zipcode_98118',
     'zipcode_98119',
     'zipcode_98122',
     'zipcode_98125',
     'zipcode_98126',
     'zipcode_98133',
     'zipcode_98136',
     'zipcode_98144',
     'zipcode_98146',
     'zipcode_98148',
     'zipcode_98155',
     'zipcode_98166',
     'zipcode_98168',
     'zipcode_98177',
     'zipcode_98178',
     'zipcode_98188',
     'zipcode_98198',
     'zipcode_98199']




```python
df_coeff3 = df_coeff2.drop((zips), axis=0)
```


```python
df_coeff3.drop('Intercept', axis=0, inplace=True)
```


```python
df_coeff3.sort_values(by='abs_coeff').tail(30).plot(kind='barh', y='coeff', figsize=(8,6))
plt.axvline(0, c='red')
plt.title('Coefficients of Features')
plt.grid()
```


    
![png](output_205_0.png)
    



```python
# Variables in the owners control

from matplotlib.ticker import FuncFormatter

def millions(x, pos):
    return '%1.1fM' % (x * 1e-6)

with plt.style.context('bmh'):

    fig, axs=plt.subplots(nrows=2, ncols=2, figsize=(18,13))

    sns.stripplot(data=df_iqr_zip, x='waterfront', y='price', ax=axs[0,0], palette="Set2")
    sns.stripplot(data=df_iqr_zip, x='condition', y='price', ax=axs[0,1])
    sns.stripplot(data=df_iqr_zip, x='renovated_yes', y='price', ax=axs[1,0], palette="Set2")
    sns.stripplot(data=df_iqr_zip, x='grade', y='price',ax=axs[1,1], palette="Set2")
    
    tf_labs = ['False', 'True']
    
    axs[0,0].set_title('Waterfront vs. Price', fontsize=14, fontweight='bold')
    axs[0,0].set_xlabel('Waterfront')
    axs[0,0].set_ylabel('Price')
    axs[0,0].set_xticklabels(tf_labs)
    
    axs[0,1].set_title('Condition vs. Price',fontsize=14, fontweight='bold')
    axs[0,1].set_xlabel('Condition')
    axs[0,1].set_ylabel('Price')
    
    axs[1,0].set_title('Has the home been renovated vs. Price', fontsize=14, fontweight='bold')
    axs[1,0].set_xlabel('Has the home been renovated?')
    axs[1,0].set_ylabel('Price')
    axs[1,0].set_xticklabels(tf_labs)
    
    axs[1,1].set_title('Grade vs. Price', fontsize=14, fontweight='bold')
    axs[1,1].set_xlabel('Grade')
    axs[1,1].set_ylabel('Price')
    
    
    
    formatter = FuncFormatter(millions)
    axs[0,0].yaxis.set_major_formatter(formatter)
    axs[0,1].yaxis.set_major_formatter(formatter)
    axs[1,0].yaxis.set_major_formatter(formatter)
    axs[1,1].yaxis.set_major_formatter(formatter)


```


    
![png](output_206_0.png)
    


## Additional Visualizations for Presentation


```python
# Plot Home prices over time
df_price = df_iqr_zip2.copy()
df_price = df_price.set_index('date')
df_price = df_price.reset_index()

```


```python
# Not using title because this is only going in PPT

with plt.style.context('bmh'):
    fig, ax = plt.subplots(figsize=(10,5))
    sns.lineplot(data=df_price, x='date', y='price')

    formatter = FuncFormatter(millions)
    ax.yaxis.set_major_formatter(formatter)
    ax.set_ylabel('Price ($)')
    ax.set_xlabel('Date')

```


    
![png](output_209_0.png)
    



```python

```


```python
# Tableau county data
```
