```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```


```python
df = pd.read_csv('kc_house_data.csv')
```


```python
df.head()
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
      <th>...</th>
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>10/13/2014</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>12/9/2014</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>2/25/2015</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>12/9/2014</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>2/18/2015</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
df.describe()
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
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.159700e+04</td>
      <td>2.159700e+04</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>2.159700e+04</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
      <td>21597.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.580474e+09</td>
      <td>5.402966e+05</td>
      <td>3.373200</td>
      <td>2.115826</td>
      <td>2080.321850</td>
      <td>1.509941e+04</td>
      <td>1.494096</td>
      <td>0.007547</td>
      <td>0.234292</td>
      <td>3.409825</td>
      <td>7.657915</td>
      <td>1788.596842</td>
      <td>291.725008</td>
      <td>1970.999676</td>
      <td>84.464787</td>
      <td>98077.951845</td>
      <td>47.560093</td>
      <td>-122.213982</td>
      <td>1986.620318</td>
      <td>12758.283512</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.876736e+09</td>
      <td>3.673681e+05</td>
      <td>0.926299</td>
      <td>0.768984</td>
      <td>918.106125</td>
      <td>4.141264e+04</td>
      <td>0.539683</td>
      <td>0.086549</td>
      <td>0.766390</td>
      <td>0.650546</td>
      <td>1.173200</td>
      <td>827.759761</td>
      <td>442.667800</td>
      <td>29.375234</td>
      <td>401.821438</td>
      <td>53.513072</td>
      <td>0.138552</td>
      <td>0.140724</td>
      <td>685.230472</td>
      <td>27274.441950</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000102e+06</td>
      <td>7.800000e+04</td>
      <td>1.000000</td>
      <td>0.500000</td>
      <td>370.000000</td>
      <td>5.200000e+02</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>370.000000</td>
      <td>0.000000</td>
      <td>1900.000000</td>
      <td>0.000000</td>
      <td>98001.000000</td>
      <td>47.155900</td>
      <td>-122.519000</td>
      <td>399.000000</td>
      <td>651.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.123049e+09</td>
      <td>3.220000e+05</td>
      <td>3.000000</td>
      <td>1.750000</td>
      <td>1430.000000</td>
      <td>5.040000e+03</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>7.000000</td>
      <td>1190.000000</td>
      <td>0.000000</td>
      <td>1951.000000</td>
      <td>0.000000</td>
      <td>98033.000000</td>
      <td>47.471100</td>
      <td>-122.328000</td>
      <td>1490.000000</td>
      <td>5100.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.904930e+09</td>
      <td>4.500000e+05</td>
      <td>3.000000</td>
      <td>2.250000</td>
      <td>1910.000000</td>
      <td>7.618000e+03</td>
      <td>1.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>7.000000</td>
      <td>1560.000000</td>
      <td>0.000000</td>
      <td>1975.000000</td>
      <td>0.000000</td>
      <td>98065.000000</td>
      <td>47.571800</td>
      <td>-122.231000</td>
      <td>1840.000000</td>
      <td>7620.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7.308900e+09</td>
      <td>6.450000e+05</td>
      <td>4.000000</td>
      <td>2.500000</td>
      <td>2550.000000</td>
      <td>1.068500e+04</td>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>4.000000</td>
      <td>8.000000</td>
      <td>2210.000000</td>
      <td>560.000000</td>
      <td>1997.000000</td>
      <td>0.000000</td>
      <td>98118.000000</td>
      <td>47.678000</td>
      <td>-122.125000</td>
      <td>2360.000000</td>
      <td>10083.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9.900000e+09</td>
      <td>7.700000e+06</td>
      <td>33.000000</td>
      <td>8.000000</td>
      <td>13540.000000</td>
      <td>1.651359e+06</td>
      <td>3.500000</td>
      <td>1.000000</td>
      <td>4.000000</td>
      <td>5.000000</td>
      <td>13.000000</td>
      <td>9410.000000</td>
      <td>4820.000000</td>
      <td>2015.000000</td>
      <td>2015.000000</td>
      <td>98199.000000</td>
      <td>47.777600</td>
      <td>-121.315000</td>
      <td>6210.000000</td>
      <td>871200.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(12,6))
sns.displot(data=df, x ='price' , kde=True)
# right skewed plot
```




    <seaborn.axisgrid.FacetGrid at 0x2884573a2e0>




    <Figure size 864x432 with 0 Axes>



    
![png](output_4_2.png)
    



```python
sns.countplot(data=df, x='bedrooms')
```




    <AxesSubplot:xlabel='bedrooms', ylabel='count'>




    
![png](output_5_1.png)
    



```python
df.corr()['price'].sort_values()[:-1]
```




    zipcode         -0.053402
    id              -0.016772
    long             0.022036
    condition        0.036056
    yr_built         0.053953
    sqft_lot15       0.082845
    sqft_lot         0.089876
    yr_renovated     0.126424
    floors           0.256804
    waterfront       0.266398
    lat              0.306692
    bedrooms         0.308787
    sqft_basement    0.323799
    view             0.397370
    bathrooms        0.525906
    sqft_living15    0.585241
    sqft_above       0.605368
    grade            0.667951
    sqft_living      0.701917
    Name: price, dtype: float64




```python
sns.scatterplot(data=df,x='sqft_living',y='price')
```




    <AxesSubplot:xlabel='sqft_living', ylabel='price'>




    
![png](output_7_1.png)
    



```python
sns.boxplot(data=df,x='bedrooms',y='price')
```




    <AxesSubplot:xlabel='bedrooms', ylabel='price'>




    
![png](output_8_1.png)
    



```python
plt.figure(figsize=(12,6))
sns.scatterplot(data=df,x='long',y='lat' , palette='plasma' , hue='price',alpha=0.2,edgecolor='black')
# price pattern doesn't look so clear because of the presence of outliers
```




    <AxesSubplot:xlabel='long', ylabel='lat'>




    
![png](output_9_1.png)
    



```python
df.sort_values('price',ascending=False)
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
      <th>...</th>
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7245</th>
      <td>6762700020</td>
      <td>10/13/2014</td>
      <td>7700000.0</td>
      <td>6</td>
      <td>8.00</td>
      <td>12050</td>
      <td>27600</td>
      <td>2.5</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>13</td>
      <td>8570</td>
      <td>3480</td>
      <td>1910</td>
      <td>1987</td>
      <td>98102</td>
      <td>47.6298</td>
      <td>-122.323</td>
      <td>3940</td>
      <td>8800</td>
    </tr>
    <tr>
      <th>3910</th>
      <td>9808700762</td>
      <td>6/11/2014</td>
      <td>7060000.0</td>
      <td>5</td>
      <td>4.50</td>
      <td>10040</td>
      <td>37325</td>
      <td>2.0</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>11</td>
      <td>7680</td>
      <td>2360</td>
      <td>1940</td>
      <td>2001</td>
      <td>98004</td>
      <td>47.6500</td>
      <td>-122.214</td>
      <td>3930</td>
      <td>25449</td>
    </tr>
    <tr>
      <th>9245</th>
      <td>9208900037</td>
      <td>9/19/2014</td>
      <td>6890000.0</td>
      <td>6</td>
      <td>7.75</td>
      <td>9890</td>
      <td>31374</td>
      <td>2.0</td>
      <td>0</td>
      <td>4</td>
      <td>...</td>
      <td>13</td>
      <td>8860</td>
      <td>1030</td>
      <td>2001</td>
      <td>0</td>
      <td>98039</td>
      <td>47.6305</td>
      <td>-122.240</td>
      <td>4540</td>
      <td>42730</td>
    </tr>
    <tr>
      <th>4407</th>
      <td>2470100110</td>
      <td>8/4/2014</td>
      <td>5570000.0</td>
      <td>5</td>
      <td>5.75</td>
      <td>9200</td>
      <td>35069</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>13</td>
      <td>6200</td>
      <td>3000</td>
      <td>2001</td>
      <td>0</td>
      <td>98039</td>
      <td>47.6289</td>
      <td>-122.233</td>
      <td>3560</td>
      <td>24345</td>
    </tr>
    <tr>
      <th>1446</th>
      <td>8907500070</td>
      <td>4/13/2015</td>
      <td>5350000.0</td>
      <td>5</td>
      <td>5.00</td>
      <td>8000</td>
      <td>23985</td>
      <td>2.0</td>
      <td>0</td>
      <td>4</td>
      <td>...</td>
      <td>12</td>
      <td>6720</td>
      <td>1280</td>
      <td>2009</td>
      <td>0</td>
      <td>98004</td>
      <td>47.6232</td>
      <td>-122.220</td>
      <td>4600</td>
      <td>21750</td>
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
    </tr>
    <tr>
      <th>2139</th>
      <td>1623049041</td>
      <td>5/8/2014</td>
      <td>82500.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>520</td>
      <td>22334</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>5</td>
      <td>520</td>
      <td>0</td>
      <td>1951</td>
      <td>0</td>
      <td>98168</td>
      <td>47.4799</td>
      <td>-122.296</td>
      <td>1572</td>
      <td>10570</td>
    </tr>
    <tr>
      <th>8267</th>
      <td>3883800011</td>
      <td>11/5/2014</td>
      <td>82000.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>860</td>
      <td>10426</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>860</td>
      <td>0</td>
      <td>1954</td>
      <td>0</td>
      <td>98146</td>
      <td>47.4987</td>
      <td>-122.341</td>
      <td>1140</td>
      <td>11250</td>
    </tr>
    <tr>
      <th>16184</th>
      <td>3028200080</td>
      <td>3/24/2015</td>
      <td>81000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>730</td>
      <td>9975</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>5</td>
      <td>730</td>
      <td>0</td>
      <td>1943</td>
      <td>0</td>
      <td>98168</td>
      <td>47.4808</td>
      <td>-122.315</td>
      <td>860</td>
      <td>9000</td>
    </tr>
    <tr>
      <th>465</th>
      <td>8658300340</td>
      <td>5/23/2014</td>
      <td>80000.0</td>
      <td>1</td>
      <td>0.75</td>
      <td>430</td>
      <td>5050</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>4</td>
      <td>430</td>
      <td>0</td>
      <td>1912</td>
      <td>0</td>
      <td>98014</td>
      <td>47.6499</td>
      <td>-121.909</td>
      <td>1200</td>
      <td>7500</td>
    </tr>
    <tr>
      <th>15279</th>
      <td>40000362</td>
      <td>5/6/2014</td>
      <td>78000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>780</td>
      <td>16344</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>5</td>
      <td>780</td>
      <td>0</td>
      <td>1942</td>
      <td>0</td>
      <td>98168</td>
      <td>47.4739</td>
      <td>-122.280</td>
      <td>1700</td>
      <td>10387</td>
    </tr>
  </tbody>
</table>
<p>21597 rows × 21 columns</p>
</div>




```python
len(df)*0.01
```




    215.97




```python
non_top_1_percent = df.sort_values('price',ascending=False).iloc[216: , :]
```


```python
plt.figure(figsize=(12,6))
sns.scatterplot(data=non_top_1_percent,x='long',y='lat' , palette='coolwarm' , hue='price',alpha=0.2,edgecolor='black')
# now we can see the price pattern more clearly
```




    <AxesSubplot:xlabel='long', ylabel='lat'>




    
![png](output_13_1.png)
    



```python
sns.boxplot(data=df,x='waterfront',y='price')
```




    <AxesSubplot:xlabel='waterfront', ylabel='price'>




    
![png](output_14_1.png)
    



```python
df.head()
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
      <th>...</th>
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>10/13/2014</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>12/9/2014</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>2/25/2015</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>12/9/2014</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>2/18/2015</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
df.drop('id',axis=1,inplace=True)
```


```python
df['date'] = pd.to_datetime(df['date'])
```


```python
df['year'] = df['date'].apply(lambda x : x.year)
df['month'] = df['date'].apply(lambda x : x.month)
```


```python
df.head()
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
      <th>...</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>year</th>
      <th>month</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014-10-13</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
      <td>2014</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2014-12-09</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
      <td>2014</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-02-25</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
      <td>2015</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2014-12-09</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>...</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
      <td>2014</td>
      <td>12</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-02-18</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
      <td>2015</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
plt.figure(figsize=(12,6))
sns.boxplot(data=df,x='month',y='price')
# no significant difference
```




    <AxesSubplot:xlabel='month', ylabel='price'>




    
![png](output_20_1.png)
    



```python
plt.figure(figsize=(12,6))
sns.boxplot(data=df,x='year',y='price')
```




    <AxesSubplot:xlabel='year', ylabel='price'>




    
![png](output_21_1.png)
    



```python
df.groupby('month').median()['price']
```




    month
    1     438500.0
    2     426500.0
    3     450000.0
    4     477000.0
    5     462000.0
    6     465000.0
    7     465000.0
    8     442200.0
    9     450000.0
    10    447000.0
    11    435000.0
    12    432500.0
    Name: price, dtype: float64




```python
df.groupby('year').median()['price']
```




    year
    2014    450000.0
    2015    451000.0
    Name: price, dtype: float64




```python
df.groupby('bedrooms').median()['price']
```




    bedrooms
    1     299000.0
    2     374000.0
    3     413000.0
    4     549997.5
    5     620000.0
    6     650000.0
    7     728580.0
    8     700000.0
    9     817000.0
    10    660000.0
    11    520000.0
    33    640000.0
    Name: price, dtype: float64




```python
df.drop('date',axis=1,inplace=True)
```


```python
df['zipcode'].nunique()
```




    70




```python
df.groupby('zipcode').median()['price'].sort_values() # isn't much fruitful, will drop it
```




    zipcode
    98002     235000.0
    98168     235000.0
    98032     249000.0
    98001     260000.0
    98188     264000.0
               ...    
    98005     765475.0
    98112     915000.0
    98040     993750.0
    98004    1150000.0
    98039    1895000.0
    Name: price, Length: 70, dtype: float64




```python
df.drop('zipcode',axis=1,inplace=True)
```


```python
X = df.drop('price',axis=1).values
y = df['price'].values
```


```python
from sklearn.model_selection import train_test_split
```


```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=101)
```


```python
from sklearn.preprocessing import MinMaxScaler
```


```python
sc = MinMaxScaler()
```


```python
X_train = sc.fit_transform(X_train)
```


```python
X_test = sc.transform(X_test)
```


```python
X_train.shape
```




    (15117, 19)




```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
```


```python
model = Sequential()

model.add(Dense(19,activation='relu')) # input layer

model.add(Dense(19,activation='relu'))
model.add(Dense(19,activation='relu'))
model.add(Dense(19,activation='relu'))

model.add(Dense(1)) # output layer

model.compile(optimizer='adam',loss='mse')
```


```python
model.fit(x=X_train,y=y_train,validation_data=(X_test,y_test),epochs=600,verbose=1)
```

    Epoch 1/600
    473/473 [==============================] - 1s 1ms/step - loss: 411069546496.0000 - val_loss: 299965775872.0000
    Epoch 2/600
    473/473 [==============================] - 1s 1ms/step - loss: 139940659200.0000 - val_loss: 95019376640.0000
    Epoch 3/600
    473/473 [==============================] - 1s 1ms/step - loss: 95816736768.0000 - val_loss: 90007609344.0000
    Epoch 4/600
    473/473 [==============================] - 1s 1ms/step - loss: 90106044416.0000 - val_loss: 83726172160.0000
    Epoch 5/600
    473/473 [==============================] - 1s 1ms/step - loss: 83179397120.0000 - val_loss: 76711895040.0000
    Epoch 6/600
    473/473 [==============================] - 1s 1ms/step - loss: 75462975488.0000 - val_loss: 68919640064.0000
    Epoch 7/600
    473/473 [==============================] - 1s 1ms/step - loss: 67372167168.0000 - val_loss: 61210255360.0000
    Epoch 8/600
    473/473 [==============================] - 1s 1ms/step - loss: 59972648960.0000 - val_loss: 55008632832.0000
    Epoch 9/600
    473/473 [==============================] - 1s 1ms/step - loss: 54557241344.0000 - val_loss: 51166203904.0000
    Epoch 10/600
    473/473 [==============================] - 1s 1ms/step - loss: 51469971456.0000 - val_loss: 48979619840.0000
    Epoch 11/600
    473/473 [==============================] - 1s 1ms/step - loss: 49717891072.0000 - val_loss: 47615303680.0000
    Epoch 12/600
    473/473 [==============================] - 1s 1ms/step - loss: 48481665024.0000 - val_loss: 46544203776.0000
    Epoch 13/600
    473/473 [==============================] - 1s 1ms/step - loss: 47495606272.0000 - val_loss: 45681532928.0000
    Epoch 14/600
    473/473 [==============================] - 1s 1ms/step - loss: 46602080256.0000 - val_loss: 44883423232.0000
    Epoch 15/600
    473/473 [==============================] - 1s 2ms/step - loss: 45837717504.0000 - val_loss: 44154302464.0000
    Epoch 16/600
    473/473 [==============================] - 1s 1ms/step - loss: 45022740480.0000 - val_loss: 43473747968.0000
    Epoch 17/600
    473/473 [==============================] - 1s 1ms/step - loss: 44217380864.0000 - val_loss: 42932424704.0000
    Epoch 18/600
    473/473 [==============================] - 1s 1ms/step - loss: 43546800128.0000 - val_loss: 41954062336.0000
    Epoch 19/600
    473/473 [==============================] - 1s 1ms/step - loss: 42722938880.0000 - val_loss: 41111797760.0000
    Epoch 20/600
    473/473 [==============================] - 1s 1ms/step - loss: 41856061440.0000 - val_loss: 40449703936.0000
    Epoch 21/600
    473/473 [==============================] - 1s 1ms/step - loss: 41096572928.0000 - val_loss: 39385755648.0000
    Epoch 22/600
    473/473 [==============================] - 1s 1ms/step - loss: 40294547456.0000 - val_loss: 38622871552.0000
    Epoch 23/600
    473/473 [==============================] - 1s 1ms/step - loss: 39513456640.0000 - val_loss: 37922066432.0000
    Epoch 24/600
    473/473 [==============================] - 1s 1ms/step - loss: 38934204416.0000 - val_loss: 37424324608.0000
    Epoch 25/600
    473/473 [==============================] - 1s 1ms/step - loss: 38403514368.0000 - val_loss: 36912713728.0000
    Epoch 26/600
    473/473 [==============================] - 1s 2ms/step - loss: 37985374208.0000 - val_loss: 36449120256.0000
    Epoch 27/600
    473/473 [==============================] - 1s 1ms/step - loss: 37616599040.0000 - val_loss: 36489723904.0000
    Epoch 28/600
    473/473 [==============================] - 1s 1ms/step - loss: 37279141888.0000 - val_loss: 36150919168.0000
    Epoch 29/600
    473/473 [==============================] - 1s 1ms/step - loss: 37019475968.0000 - val_loss: 35811475456.0000
    Epoch 30/600
    473/473 [==============================] - 1s 1ms/step - loss: 36847144960.0000 - val_loss: 35494461440.0000
    Epoch 31/600
    473/473 [==============================] - 1s 1ms/step - loss: 36539719680.0000 - val_loss: 35186274304.0000
    Epoch 32/600
    473/473 [==============================] - 1s 1ms/step - loss: 36311793664.0000 - val_loss: 35204517888.0000
    Epoch 33/600
    473/473 [==============================] - 1s 1ms/step - loss: 36176465920.0000 - val_loss: 34825048064.0000
    Epoch 34/600
    473/473 [==============================] - 1s 1ms/step - loss: 36020584448.0000 - val_loss: 34672308224.0000
    Epoch 35/600
    473/473 [==============================] - 1s 1ms/step - loss: 35851845632.0000 - val_loss: 34651549696.0000
    Epoch 36/600
    473/473 [==============================] - 1s 1ms/step - loss: 35702484992.0000 - val_loss: 34568425472.0000
    Epoch 37/600
    473/473 [==============================] - 1s 1ms/step - loss: 35552002048.0000 - val_loss: 34279843840.0000
    Epoch 38/600
    473/473 [==============================] - 1s 1ms/step - loss: 35360411648.0000 - val_loss: 34159388672.0000
    Epoch 39/600
    473/473 [==============================] - 1s 1ms/step - loss: 35272675328.0000 - val_loss: 33921619968.0000
    Epoch 40/600
    473/473 [==============================] - 1s 1ms/step - loss: 35124867072.0000 - val_loss: 33773705216.0000
    Epoch 41/600
    473/473 [==============================] - 1s 1ms/step - loss: 34931273728.0000 - val_loss: 34098855936.0000
    Epoch 42/600
    473/473 [==============================] - 1s 1ms/step - loss: 34831179776.0000 - val_loss: 33634023424.0000
    Epoch 43/600
    473/473 [==============================] - 1s 1ms/step - loss: 34690924544.0000 - val_loss: 33361133568.0000
    Epoch 44/600
    473/473 [==============================] - 1s 1ms/step - loss: 34535669760.0000 - val_loss: 33202579456.0000
    Epoch 45/600
    473/473 [==============================] - 1s 1ms/step - loss: 34413080576.0000 - val_loss: 33098907648.0000
    Epoch 46/600
    473/473 [==============================] - 1s 1ms/step - loss: 34367967232.0000 - val_loss: 32940509184.0000
    Epoch 47/600
    473/473 [==============================] - 1s 1ms/step - loss: 34261508096.0000 - val_loss: 32847521792.0000
    Epoch 48/600
    473/473 [==============================] - 1s 1ms/step - loss: 34072295424.0000 - val_loss: 32786577408.0000
    Epoch 49/600
    473/473 [==============================] - 1s 1ms/step - loss: 33956126720.0000 - val_loss: 32580988928.0000
    Epoch 50/600
    473/473 [==============================] - 1s 1ms/step - loss: 33879103488.0000 - val_loss: 32471961600.0000
    Epoch 51/600
    473/473 [==============================] - 1s 2ms/step - loss: 33791485952.0000 - val_loss: 32485097472.0000
    Epoch 52/600
    473/473 [==============================] - 1s 2ms/step - loss: 33678725120.0000 - val_loss: 32262291456.0000
    Epoch 53/600
    473/473 [==============================] - 1s 2ms/step - loss: 33577619456.0000 - val_loss: 32112881664.0000
    Epoch 54/600
    473/473 [==============================] - 1s 2ms/step - loss: 33421971456.0000 - val_loss: 32071376896.0000
    Epoch 55/600
    473/473 [==============================] - 1s 1ms/step - loss: 33409882112.0000 - val_loss: 31925538816.0000
    Epoch 56/600
    473/473 [==============================] - ETA: 0s - loss: 33150425088.000 - 1s 1ms/step - loss: 33288189952.0000 - val_loss: 31835969536.0000
    Epoch 57/600
    473/473 [==============================] - 1s 1ms/step - loss: 33237424128.0000 - val_loss: 31716558848.0000
    Epoch 58/600
    473/473 [==============================] - 1s 1ms/step - loss: 33101338624.0000 - val_loss: 31653120000.0000
    Epoch 59/600
    473/473 [==============================] - 1s 1ms/step - loss: 33089931264.0000 - val_loss: 31737690112.0000
    Epoch 60/600
    473/473 [==============================] - 1s 1ms/step - loss: 32944738304.0000 - val_loss: 31422724096.0000
    Epoch 61/600
    473/473 [==============================] - 1s 1ms/step - loss: 32902756352.0000 - val_loss: 31307546624.0000
    Epoch 62/600
    473/473 [==============================] - 1s 1ms/step - loss: 32846802944.0000 - val_loss: 31246733312.0000
    Epoch 63/600
    473/473 [==============================] - 1s 2ms/step - loss: 32743847936.0000 - val_loss: 31236429824.0000
    Epoch 64/600
    473/473 [==============================] - 1s 2ms/step - loss: 32724787200.0000 - val_loss: 31194990592.0000
    Epoch 65/600
    473/473 [==============================] - 1s 1ms/step - loss: 32635971584.0000 - val_loss: 31002374144.0000
    Epoch 66/600
    473/473 [==============================] - 1s 1ms/step - loss: 32629895168.0000 - val_loss: 30890362880.0000
    Epoch 67/600
    473/473 [==============================] - 1s 1ms/step - loss: 32550711296.0000 - val_loss: 30847535104.0000
    Epoch 68/600
    473/473 [==============================] - 1s 1ms/step - loss: 32517040128.0000 - val_loss: 30739789824.0000
    Epoch 69/600
    473/473 [==============================] - 1s 1ms/step - loss: 32457359360.0000 - val_loss: 30710829056.0000
    Epoch 70/600
    473/473 [==============================] - 1s 1ms/step - loss: 32351375360.0000 - val_loss: 30606401536.0000
    Epoch 71/600
    473/473 [==============================] - 1s 1ms/step - loss: 32253267968.0000 - val_loss: 30642087936.0000
    Epoch 72/600
    473/473 [==============================] - 1s 2ms/step - loss: 32280248320.0000 - val_loss: 30614554624.0000
    Epoch 73/600
    473/473 [==============================] - 1s 1ms/step - loss: 32260798464.0000 - val_loss: 30454198272.0000
    Epoch 74/600
    473/473 [==============================] - 1s 2ms/step - loss: 32211955712.0000 - val_loss: 30586781696.0000
    Epoch 75/600
    473/473 [==============================] - 1s 2ms/step - loss: 32083750912.0000 - val_loss: 30374057984.0000
    Epoch 76/600
    473/473 [==============================] - 1s 1ms/step - loss: 32133621760.0000 - val_loss: 30347653120.0000
    Epoch 77/600
    473/473 [==============================] - 1s 1ms/step - loss: 32050788352.0000 - val_loss: 30189549568.0000
    Epoch 78/600
    473/473 [==============================] - 1s 1ms/step - loss: 32001337344.0000 - val_loss: 30304632832.0000
    Epoch 79/600
    473/473 [==============================] - 1s 2ms/step - loss: 31938015232.0000 - val_loss: 30181074944.0000
    Epoch 80/600
    473/473 [==============================] - 1s 2ms/step - loss: 31985334272.0000 - val_loss: 30100043776.0000
    Epoch 81/600
    473/473 [==============================] - 1s 1ms/step - loss: 31910223872.0000 - val_loss: 30093791232.0000
    Epoch 82/600
    473/473 [==============================] - 1s 1ms/step - loss: 31846469632.0000 - val_loss: 29997723648.0000
    Epoch 83/600
    473/473 [==============================] - 1s 1ms/step - loss: 31776374784.0000 - val_loss: 30087389184.0000
    Epoch 84/600
    473/473 [==============================] - 1s 2ms/step - loss: 31794946048.0000 - val_loss: 29987852288.0000
    Epoch 85/600
    473/473 [==============================] - 1s 1ms/step - loss: 31671298048.0000 - val_loss: 30021218304.0000
    Epoch 86/600
    473/473 [==============================] - 1s 1ms/step - loss: 31633958912.0000 - val_loss: 29747712000.0000
    Epoch 87/600
    473/473 [==============================] - 1s 1ms/step - loss: 31703482368.0000 - val_loss: 29669666816.0000
    Epoch 88/600
    473/473 [==============================] - 1s 1ms/step - loss: 31682623488.0000 - val_loss: 29704247296.0000
    Epoch 89/600
    473/473 [==============================] - 1s 2ms/step - loss: 31596707840.0000 - val_loss: 29642596352.0000
    Epoch 90/600
    473/473 [==============================] - 1s 1ms/step - loss: 31565504512.0000 - val_loss: 29584257024.0000
    Epoch 91/600
    473/473 [==============================] - 1s 1ms/step - loss: 31512956928.0000 - val_loss: 29520517120.0000
    Epoch 92/600
    473/473 [==============================] - 1s 1ms/step - loss: 31479943168.0000 - val_loss: 29704099840.0000
    Epoch 93/600
    473/473 [==============================] - 1s 1ms/step - loss: 31508584448.0000 - val_loss: 29481545728.0000
    Epoch 94/600
    473/473 [==============================] - 1s 1ms/step - loss: 31486191616.0000 - val_loss: 29566773248.0000
    Epoch 95/600
    473/473 [==============================] - 1s 1ms/step - loss: 31394766848.0000 - val_loss: 29648123904.0000
    Epoch 96/600
    473/473 [==============================] - 1s 2ms/step - loss: 31315668992.0000 - val_loss: 29583237120.0000
    Epoch 97/600
    473/473 [==============================] - 1s 2ms/step - loss: 31241422848.0000 - val_loss: 29292662784.0000
    Epoch 98/600
    473/473 [==============================] - 1s 2ms/step - loss: 31378391040.0000 - val_loss: 29369214976.0000
    Epoch 99/600
    473/473 [==============================] - 1s 1ms/step - loss: 31221567488.0000 - val_loss: 29470926848.0000
    Epoch 100/600
    473/473 [==============================] - 1s 1ms/step - loss: 31326158848.0000 - val_loss: 29201633280.0000
    Epoch 101/600
    473/473 [==============================] - 1s 1ms/step - loss: 31203532800.0000 - val_loss: 29235296256.0000
    Epoch 102/600
    473/473 [==============================] - 1s 1ms/step - loss: 31147696128.0000 - val_loss: 29810350080.0000
    Epoch 103/600
    473/473 [==============================] - 1s 1ms/step - loss: 31235864576.0000 - val_loss: 29118554112.0000
    Epoch 104/600
    473/473 [==============================] - 1s 1ms/step - loss: 31159422976.0000 - val_loss: 29049733120.0000
    Epoch 105/600
    473/473 [==============================] - 1s 2ms/step - loss: 31119132672.0000 - val_loss: 29208303616.0000
    Epoch 106/600
    473/473 [==============================] - 1s 1ms/step - loss: 31096399872.0000 - val_loss: 29184106496.0000
    Epoch 107/600
    473/473 [==============================] - 1s 1ms/step - loss: 31037689856.0000 - val_loss: 28952469504.0000
    Epoch 108/600
    473/473 [==============================] - 1s 1ms/step - loss: 31071567872.0000 - val_loss: 29022015488.0000
    Epoch 109/600
    473/473 [==============================] - 1s 1ms/step - loss: 31005014016.0000 - val_loss: 29321684992.0000
    Epoch 110/600
    473/473 [==============================] - 1s 1ms/step - loss: 31008522240.0000 - val_loss: 28859578368.0000
    Epoch 111/600
    473/473 [==============================] - 1s 1ms/step - loss: 31023020032.0000 - val_loss: 28852164608.0000
    Epoch 112/600
    473/473 [==============================] - 1s 1ms/step - loss: 30968891392.0000 - val_loss: 28849743872.0000
    Epoch 113/600
    473/473 [==============================] - 1s 2ms/step - loss: 30972092416.0000 - val_loss: 28911583232.0000
    Epoch 114/600
    473/473 [==============================] - 1s 2ms/step - loss: 30858299392.0000 - val_loss: 28781010944.0000
    Epoch 115/600
    473/473 [==============================] - 1s 1ms/step - loss: 30902292480.0000 - val_loss: 28766414848.0000
    Epoch 116/600
    473/473 [==============================] - 1s 1ms/step - loss: 30879569920.0000 - val_loss: 28798289920.0000
    Epoch 117/600
    473/473 [==============================] - 1s 1ms/step - loss: 30831665152.0000 - val_loss: 29068281856.0000
    Epoch 118/600
    473/473 [==============================] - 1s 2ms/step - loss: 30843963392.0000 - val_loss: 28748265472.0000
    Epoch 119/600
    473/473 [==============================] - 1s 2ms/step - loss: 30720837632.0000 - val_loss: 28873168896.0000
    Epoch 120/600
    473/473 [==============================] - 1s 2ms/step - loss: 30881503232.0000 - val_loss: 28961382400.0000
    Epoch 121/600
    473/473 [==============================] - 1s 2ms/step - loss: 30736013312.0000 - val_loss: 28594130944.0000
    Epoch 122/600
    473/473 [==============================] - 1s 2ms/step - loss: 30751688704.0000 - val_loss: 28882708480.0000
    Epoch 123/600
    473/473 [==============================] - 1s 2ms/step - loss: 30753857536.0000 - val_loss: 28599179264.0000
    Epoch 124/600
    473/473 [==============================] - 1s 2ms/step - loss: 30706305024.0000 - val_loss: 28515393536.0000
    Epoch 125/600
    473/473 [==============================] - 1s 2ms/step - loss: 30680541184.0000 - val_loss: 28490518528.0000
    Epoch 126/600
    473/473 [==============================] - 1s 2ms/step - loss: 30682007552.0000 - val_loss: 28439420928.0000
    Epoch 127/600
    473/473 [==============================] - 1s 2ms/step - loss: 30599421952.0000 - val_loss: 28764510208.0000
    Epoch 128/600
    473/473 [==============================] - 1s 2ms/step - loss: 30659606528.0000 - val_loss: 28497754112.0000
    Epoch 129/600
    473/473 [==============================] - 1s 2ms/step - loss: 30571163648.0000 - val_loss: 28590874624.0000
    Epoch 130/600
    473/473 [==============================] - 1s 2ms/step - loss: 30540668928.0000 - val_loss: 28425619456.0000
    Epoch 131/600
    473/473 [==============================] - 1s 2ms/step - loss: 30638589952.0000 - val_loss: 28397965312.0000
    Epoch 132/600
    473/473 [==============================] - 1s 2ms/step - loss: 30531239936.0000 - val_loss: 28622280704.0000
    Epoch 133/600
    473/473 [==============================] - 1s 1ms/step - loss: 30532231168.0000 - val_loss: 28363753472.0000
    Epoch 134/600
    473/473 [==============================] - 1s 2ms/step - loss: 30486056960.0000 - val_loss: 28289089536.0000
    Epoch 135/600
    473/473 [==============================] - 1s 2ms/step - loss: 30513838080.0000 - val_loss: 28369147904.0000
    Epoch 136/600
    473/473 [==============================] - 1s 2ms/step - loss: 30452111360.0000 - val_loss: 28290451456.0000
    Epoch 137/600
    473/473 [==============================] - 1s 2ms/step - loss: 30470055936.0000 - val_loss: 28307232768.0000
    Epoch 138/600
    473/473 [==============================] - 1s 2ms/step - loss: 30507606016.0000 - val_loss: 28299401216.0000
    Epoch 139/600
    473/473 [==============================] - 1s 2ms/step - loss: 30443673600.0000 - val_loss: 28535869440.0000
    Epoch 140/600
    473/473 [==============================] - 1s 1ms/step - loss: 30412998656.0000 - val_loss: 28178434048.0000
    Epoch 141/600
    473/473 [==============================] - 1s 1ms/step - loss: 30392367104.0000 - val_loss: 28218392576.0000
    Epoch 142/600
    473/473 [==============================] - 1s 1ms/step - loss: 30435272704.0000 - val_loss: 28163313664.0000
    Epoch 143/600
    473/473 [==============================] - 1s 1ms/step - loss: 30410952704.0000 - val_loss: 28206350336.0000
    Epoch 144/600
    473/473 [==============================] - 1s 2ms/step - loss: 30417104896.0000 - val_loss: 28122609664.0000
    Epoch 145/600
    473/473 [==============================] - 1s 2ms/step - loss: 30281388032.0000 - val_loss: 28364713984.0000
    Epoch 146/600
    473/473 [==============================] - 1s 2ms/step - loss: 30374291456.0000 - val_loss: 28100122624.0000
    Epoch 147/600
    473/473 [==============================] - 1s 1ms/step - loss: 30377472000.0000 - val_loss: 28094091264.0000
    Epoch 148/600
    473/473 [==============================] - 1s 1ms/step - loss: 30340696064.0000 - val_loss: 28048635904.0000
    Epoch 149/600
    473/473 [==============================] - 1s 1ms/step - loss: 30338715648.0000 - val_loss: 28052269056.0000
    Epoch 150/600
    473/473 [==============================] - 1s 1ms/step - loss: 30319020032.0000 - val_loss: 28039694336.0000
    Epoch 151/600
    473/473 [==============================] - 1s 1ms/step - loss: 30297501696.0000 - val_loss: 27974602752.0000
    Epoch 152/600
    473/473 [==============================] - 1s 2ms/step - loss: 30290900992.0000 - val_loss: 28067221504.0000
    Epoch 153/600
    473/473 [==============================] - 1s 2ms/step - loss: 30314924032.0000 - val_loss: 27990718464.0000
    Epoch 154/600
    473/473 [==============================] - 1s 2ms/step - loss: 30256986112.0000 - val_loss: 28026347520.0000
    Epoch 155/600
    473/473 [==============================] - 1s 1ms/step - loss: 30275350528.0000 - val_loss: 28019079168.0000
    Epoch 156/600
    473/473 [==============================] - 1s 2ms/step - loss: 30221320192.0000 - val_loss: 27951196160.0000
    Epoch 157/600
    473/473 [==============================] - 1s 2ms/step - loss: 30230515712.0000 - val_loss: 27903893504.0000
    Epoch 158/600
    473/473 [==============================] - 1s 2ms/step - loss: 30198142976.0000 - val_loss: 27915644928.0000
    Epoch 159/600
    473/473 [==============================] - 1s 2ms/step - loss: 30091696128.0000 - val_loss: 28474011648.0000
    Epoch 160/600
    473/473 [==============================] - 1s 2ms/step - loss: 30150600704.0000 - val_loss: 27849922560.0000
    Epoch 161/600
    473/473 [==============================] - 1s 2ms/step - loss: 30126184448.0000 - val_loss: 27959635968.0000
    Epoch 162/600
    473/473 [==============================] - 1s 2ms/step - loss: 30089783296.0000 - val_loss: 27776737280.0000
    Epoch 163/600
    473/473 [==============================] - 1s 1ms/step - loss: 29996613632.0000 - val_loss: 28588761088.0000
    Epoch 164/600
    473/473 [==============================] - 1s 1ms/step - loss: 30144262144.0000 - val_loss: 27717427200.0000
    Epoch 165/600
    473/473 [==============================] - 1s 1ms/step - loss: 30051385344.0000 - val_loss: 27714791424.0000
    Epoch 166/600
    473/473 [==============================] - 1s 1ms/step - loss: 30033571840.0000 - val_loss: 27669970944.0000
    Epoch 167/600
    473/473 [==============================] - 1s 1ms/step - loss: 30062743552.0000 - val_loss: 27662835712.0000
    Epoch 168/600
    473/473 [==============================] - 1s 1ms/step - loss: 29947115520.0000 - val_loss: 27592153088.0000
    Epoch 169/600
    473/473 [==============================] - 1s 1ms/step - loss: 29969301504.0000 - val_loss: 27644950528.0000
    Epoch 170/600
    473/473 [==============================] - 1s 1ms/step - loss: 30001803264.0000 - val_loss: 27690274816.0000
    Epoch 171/600
    473/473 [==============================] - 1s 1ms/step - loss: 29988319232.0000 - val_loss: 27656972288.0000
    Epoch 172/600
    473/473 [==============================] - 1s 2ms/step - loss: 29900304384.0000 - val_loss: 27559260160.0000
    Epoch 173/600
    473/473 [==============================] - 1s 2ms/step - loss: 29885622272.0000 - val_loss: 27497740288.0000
    Epoch 174/600
    473/473 [==============================] - 1s 2ms/step - loss: 29920968704.0000 - val_loss: 27483199488.0000
    Epoch 175/600
    473/473 [==============================] - 1s 2ms/step - loss: 29856286720.0000 - val_loss: 27460659200.0000
    Epoch 176/600
    473/473 [==============================] - 1s 2ms/step - loss: 29805279232.0000 - val_loss: 27443951616.0000
    Epoch 177/600
    473/473 [==============================] - 1s 2ms/step - loss: 29804656640.0000 - val_loss: 27678617600.0000
    Epoch 178/600
    473/473 [==============================] - 1s 2ms/step - loss: 29814177792.0000 - val_loss: 27364532224.0000
    Epoch 179/600
    473/473 [==============================] - 1s 2ms/step - loss: 29790859264.0000 - val_loss: 27375822848.0000
    Epoch 180/600
    473/473 [==============================] - 1s 2ms/step - loss: 29719269376.0000 - val_loss: 27876753408.0000
    Epoch 181/600
    473/473 [==============================] - 1s 2ms/step - loss: 29710880768.0000 - val_loss: 27600300032.0000
    Epoch 182/600
    473/473 [==============================] - 1s 2ms/step - loss: 29750802432.0000 - val_loss: 27448582144.0000
    Epoch 183/600
    473/473 [==============================] - 1s 2ms/step - loss: 29636159488.0000 - val_loss: 27354798080.0000
    Epoch 184/600
    473/473 [==============================] - 1s 2ms/step - loss: 29607968768.0000 - val_loss: 27289217024.0000
    Epoch 185/600
    473/473 [==============================] - 1s 2ms/step - loss: 29640108032.0000 - val_loss: 27125807104.0000
    Epoch 186/600
    473/473 [==============================] - 1s 2ms/step - loss: 29535606784.0000 - val_loss: 27110004736.0000
    Epoch 187/600
    473/473 [==============================] - 1s 2ms/step - loss: 29492383744.0000 - val_loss: 27091441664.0000
    Epoch 188/600
    473/473 [==============================] - 1s 2ms/step - loss: 29478633472.0000 - val_loss: 27212681216.0000
    Epoch 189/600
    473/473 [==============================] - 1s 2ms/step - loss: 29363906560.0000 - val_loss: 26922809344.0000
    Epoch 190/600
    473/473 [==============================] - 1s 2ms/step - loss: 29330309120.0000 - val_loss: 26844874752.0000
    Epoch 191/600
    473/473 [==============================] - 1s 2ms/step - loss: 29175164928.0000 - val_loss: 27082250240.0000
    Epoch 192/600
    473/473 [==============================] - 1s 2ms/step - loss: 29176885248.0000 - val_loss: 26699397120.0000
    Epoch 193/600
    473/473 [==============================] - 1s 2ms/step - loss: 29085399040.0000 - val_loss: 26658627584.0000
    Epoch 194/600
    473/473 [==============================] - 1s 2ms/step - loss: 28960735232.0000 - val_loss: 26429591552.0000
    Epoch 195/600
    473/473 [==============================] - 1s 2ms/step - loss: 28845193216.0000 - val_loss: 26363066368.0000
    Epoch 196/600
    473/473 [==============================] - 1s 2ms/step - loss: 28741900288.0000 - val_loss: 26248278016.0000
    Epoch 197/600
    473/473 [==============================] - 1s 2ms/step - loss: 28584331264.0000 - val_loss: 26099597312.0000
    Epoch 198/600
    473/473 [==============================] - 1s 2ms/step - loss: 28523296768.0000 - val_loss: 26080380928.0000
    Epoch 199/600
    473/473 [==============================] - 1s 2ms/step - loss: 28476561408.0000 - val_loss: 25924003840.0000
    Epoch 200/600
    473/473 [==============================] - 1s 2ms/step - loss: 28307666944.0000 - val_loss: 25824899072.0000
    Epoch 201/600
    473/473 [==============================] - 1s 2ms/step - loss: 28187977728.0000 - val_loss: 25858910208.0000
    Epoch 202/600
    473/473 [==============================] - 1s 2ms/step - loss: 28077568000.0000 - val_loss: 25700444160.0000
    Epoch 203/600
    473/473 [==============================] - 1s 2ms/step - loss: 28097290240.0000 - val_loss: 25510010880.0000
    Epoch 204/600
    473/473 [==============================] - 1s 2ms/step - loss: 27908986880.0000 - val_loss: 25541861376.0000
    Epoch 205/600
    473/473 [==============================] - 1s 2ms/step - loss: 27812894720.0000 - val_loss: 25326553088.0000
    Epoch 206/600
    473/473 [==============================] - 1s 2ms/step - loss: 27672147968.0000 - val_loss: 25390954496.0000
    Epoch 207/600
    473/473 [==============================] - 1s 2ms/step - loss: 27671918592.0000 - val_loss: 25457680384.0000
    Epoch 208/600
    473/473 [==============================] - 1s 2ms/step - loss: 27453265920.0000 - val_loss: 25194010624.0000
    Epoch 209/600
    473/473 [==============================] - 1s 2ms/step - loss: 27479558144.0000 - val_loss: 24936071168.0000
    Epoch 210/600
    473/473 [==============================] - 1s 2ms/step - loss: 27318339584.0000 - val_loss: 24855879680.0000
    Epoch 211/600
    473/473 [==============================] - 1s 2ms/step - loss: 27258060800.0000 - val_loss: 24826787840.0000
    Epoch 212/600
    473/473 [==============================] - 1s 1ms/step - loss: 27162918912.0000 - val_loss: 24706000896.0000
    Epoch 213/600
    473/473 [==============================] - 1s 1ms/step - loss: 27054354432.0000 - val_loss: 24594118656.0000
    Epoch 214/600
    473/473 [==============================] - 1s 1ms/step - loss: 26957068288.0000 - val_loss: 24628711424.0000
    Epoch 215/600
    473/473 [==============================] - 1s 1ms/step - loss: 26837921792.0000 - val_loss: 24639832064.0000
    Epoch 216/600
    473/473 [==============================] - 1s 1ms/step - loss: 26799962112.0000 - val_loss: 24529469440.0000
    Epoch 217/600
    473/473 [==============================] - 1s 1ms/step - loss: 26734692352.0000 - val_loss: 24294819840.0000
    Epoch 218/600
    473/473 [==============================] - 1s 1ms/step - loss: 26501953536.0000 - val_loss: 24589076480.0000
    Epoch 219/600
    473/473 [==============================] - 1s 2ms/step - loss: 26493208576.0000 - val_loss: 24083255296.0000
    Epoch 220/600
    473/473 [==============================] - 1s 2ms/step - loss: 26418911232.0000 - val_loss: 24068599808.0000
    Epoch 221/600
    473/473 [==============================] - 1s 1ms/step - loss: 26323384320.0000 - val_loss: 24024686592.0000
    Epoch 222/600
    473/473 [==============================] - 1s 1ms/step - loss: 26309103616.0000 - val_loss: 23973998592.0000
    Epoch 223/600
    473/473 [==============================] - 1s 1ms/step - loss: 26148567040.0000 - val_loss: 23763963904.0000
    Epoch 224/600
    473/473 [==============================] - 1s 1ms/step - loss: 26082342912.0000 - val_loss: 23752724480.0000
    Epoch 225/600
    473/473 [==============================] - 1s 1ms/step - loss: 26003503104.0000 - val_loss: 23657764864.0000
    Epoch 226/600
    473/473 [==============================] - 1s 1ms/step - loss: 25963864064.0000 - val_loss: 23560486912.0000
    Epoch 227/600
    473/473 [==============================] - 1s 1ms/step - loss: 25869219840.0000 - val_loss: 23438551040.0000
    Epoch 228/600
    473/473 [==============================] - 1s 1ms/step - loss: 25736568832.0000 - val_loss: 23360002048.0000
    Epoch 229/600
    473/473 [==============================] - 1s 1ms/step - loss: 25553991680.0000 - val_loss: 23494789120.0000
    Epoch 230/600
    473/473 [==============================] - 1s 1ms/step - loss: 25544355840.0000 - val_loss: 23313326080.0000
    Epoch 231/600
    473/473 [==============================] - 1s 1ms/step - loss: 25402116096.0000 - val_loss: 23224320000.0000
    Epoch 232/600
    473/473 [==============================] - 1s 1ms/step - loss: 25296662528.0000 - val_loss: 23052931072.0000
    Epoch 233/600
    473/473 [==============================] - 1s 1ms/step - loss: 25279850496.0000 - val_loss: 22922940416.0000
    Epoch 234/600
    473/473 [==============================] - 1s 1ms/step - loss: 25157734400.0000 - val_loss: 22818142208.0000
    Epoch 235/600
    473/473 [==============================] - 1s 1ms/step - loss: 25044852736.0000 - val_loss: 22977583104.0000
    Epoch 236/600
    473/473 [==============================] - 1s 2ms/step - loss: 24900026368.0000 - val_loss: 22695979008.0000
    Epoch 237/600
    473/473 [==============================] - 1s 1ms/step - loss: 24820049920.0000 - val_loss: 22638135296.0000
    Epoch 238/600
    473/473 [==============================] - 1s 1ms/step - loss: 24734572544.0000 - val_loss: 22480869376.0000
    Epoch 239/600
    473/473 [==============================] - 1s 1ms/step - loss: 24625195008.0000 - val_loss: 22447071232.0000
    Epoch 240/600
    473/473 [==============================] - 1s 1ms/step - loss: 24549310464.0000 - val_loss: 22295377920.0000
    Epoch 241/600
    473/473 [==============================] - 1s 1ms/step - loss: 24359940096.0000 - val_loss: 22700738560.0000
    Epoch 242/600
    473/473 [==============================] - 1s 2ms/step - loss: 24341364736.0000 - val_loss: 22136832000.0000
    Epoch 243/600
    473/473 [==============================] - 1s 2ms/step - loss: 24151478272.0000 - val_loss: 22072086528.0000
    Epoch 244/600
    473/473 [==============================] - 1s 1ms/step - loss: 24073924608.0000 - val_loss: 21869383680.0000
    Epoch 245/600
    473/473 [==============================] - 1s 1ms/step - loss: 23916171264.0000 - val_loss: 22045005824.0000
    Epoch 246/600
    473/473 [==============================] - 1s 2ms/step - loss: 23888392192.0000 - val_loss: 21703843840.0000
    Epoch 247/600
    473/473 [==============================] - 1s 2ms/step - loss: 23746140160.0000 - val_loss: 21589839872.0000
    Epoch 248/600
    473/473 [==============================] - 1s 1ms/step - loss: 23614408704.0000 - val_loss: 21541126144.0000
    Epoch 249/600
    473/473 [==============================] - 1s 2ms/step - loss: 23548637184.0000 - val_loss: 21413949440.0000
    Epoch 250/600
    473/473 [==============================] - 1s 2ms/step - loss: 23449800704.0000 - val_loss: 21390493696.0000
    Epoch 251/600
    473/473 [==============================] - 1s 1ms/step - loss: 23384449024.0000 - val_loss: 21347031040.0000
    Epoch 252/600
    473/473 [==============================] - 1s 2ms/step - loss: 23254663168.0000 - val_loss: 21205399552.0000
    Epoch 253/600
    473/473 [==============================] - 1s 2ms/step - loss: 23137779712.0000 - val_loss: 21063876608.0000
    Epoch 254/600
    473/473 [==============================] - 1s 2ms/step - loss: 22982543360.0000 - val_loss: 21015590912.0000
    Epoch 255/600
    473/473 [==============================] - 1s 2ms/step - loss: 22905669632.0000 - val_loss: 20945129472.0000
    Epoch 256/600
    473/473 [==============================] - 1s 2ms/step - loss: 22845175808.0000 - val_loss: 20872638464.0000
    Epoch 257/600
    473/473 [==============================] - 1s 2ms/step - loss: 22740654080.0000 - val_loss: 21103618048.0000
    Epoch 258/600
    473/473 [==============================] - 1s 2ms/step - loss: 22640787456.0000 - val_loss: 20696928256.0000
    Epoch 259/600
    473/473 [==============================] - 1s 2ms/step - loss: 22575405056.0000 - val_loss: 20676292608.0000
    Epoch 260/600
    473/473 [==============================] - 1s 2ms/step - loss: 22514784256.0000 - val_loss: 20687065088.0000
    Epoch 261/600
    473/473 [==============================] - 1s 2ms/step - loss: 22350161920.0000 - val_loss: 20640745472.0000
    Epoch 262/600
    473/473 [==============================] - 1s 2ms/step - loss: 22281916416.0000 - val_loss: 20556402688.0000
    Epoch 263/600
    473/473 [==============================] - 1s 2ms/step - loss: 22198181888.0000 - val_loss: 20421832704.0000
    Epoch 264/600
    473/473 [==============================] - 1s 2ms/step - loss: 22132955136.0000 - val_loss: 20570781696.0000
    Epoch 265/600
    473/473 [==============================] - 1s 2ms/step - loss: 22102173696.0000 - val_loss: 20421996544.0000
    Epoch 266/600
    473/473 [==============================] - 1s 2ms/step - loss: 22042478592.0000 - val_loss: 20166002688.0000
    Epoch 267/600
    473/473 [==============================] - 1s 2ms/step - loss: 21953019904.0000 - val_loss: 20279064576.0000
    Epoch 268/600
    473/473 [==============================] - 1s 2ms/step - loss: 21913882624.0000 - val_loss: 20055189504.0000
    Epoch 269/600
    473/473 [==============================] - 1s 2ms/step - loss: 21777784832.0000 - val_loss: 20255834112.0000
    Epoch 270/600
    473/473 [==============================] - 1s 2ms/step - loss: 21653217280.0000 - val_loss: 20075499520.0000
    Epoch 271/600
    473/473 [==============================] - 1s 1ms/step - loss: 21671264256.0000 - val_loss: 19903881216.0000
    Epoch 272/600
    473/473 [==============================] - 1s 1ms/step - loss: 21610328064.0000 - val_loss: 19849189376.0000
    Epoch 273/600
    473/473 [==============================] - 1s 1ms/step - loss: 21489598464.0000 - val_loss: 19816620032.0000
    Epoch 274/600
    473/473 [==============================] - 1s 1ms/step - loss: 21440141312.0000 - val_loss: 19791579136.0000
    Epoch 275/600
    473/473 [==============================] - 1s 2ms/step - loss: 21362255872.0000 - val_loss: 19755649024.0000
    Epoch 276/600
    473/473 [==============================] - 1s 1ms/step - loss: 21342791680.0000 - val_loss: 19722252288.0000
    Epoch 277/600
    473/473 [==============================] - 1s 1ms/step - loss: 21271998464.0000 - val_loss: 19703914496.0000
    Epoch 278/600
    473/473 [==============================] - 1s 1ms/step - loss: 21184227328.0000 - val_loss: 19727523840.0000
    Epoch 279/600
    473/473 [==============================] - 1s 1ms/step - loss: 21169803264.0000 - val_loss: 19618217984.0000
    Epoch 280/600
    473/473 [==============================] - 1s 2ms/step - loss: 21124405248.0000 - val_loss: 19746486272.0000
    Epoch 281/600
    473/473 [==============================] - 1s 1ms/step - loss: 20973197312.0000 - val_loss: 19669706752.0000
    Epoch 282/600
    473/473 [==============================] - 1s 2ms/step - loss: 21005240320.0000 - val_loss: 19613337600.0000
    Epoch 283/600
    473/473 [==============================] - 1s 2ms/step - loss: 20946069504.0000 - val_loss: 19487096832.0000
    Epoch 284/600
    473/473 [==============================] - 1s 2ms/step - loss: 20919232512.0000 - val_loss: 19457415168.0000
    Epoch 285/600
    473/473 [==============================] - 1s 2ms/step - loss: 20862234624.0000 - val_loss: 19366328320.0000
    Epoch 286/600
    473/473 [==============================] - 1s 1ms/step - loss: 20795029504.0000 - val_loss: 19464177664.0000
    Epoch 287/600
    473/473 [==============================] - 1s 2ms/step - loss: 20810702848.0000 - val_loss: 19242887168.0000
    Epoch 288/600
    473/473 [==============================] - 1s 2ms/step - loss: 20710483968.0000 - val_loss: 19320887296.0000
    Epoch 289/600
    473/473 [==============================] - 1s 2ms/step - loss: 20625278976.0000 - val_loss: 19242110976.0000
    Epoch 290/600
    473/473 [==============================] - 1s 2ms/step - loss: 20646877184.0000 - val_loss: 19108165632.0000
    Epoch 291/600
    473/473 [==============================] - 1s 2ms/step - loss: 20483987456.0000 - val_loss: 19272794112.0000
    Epoch 292/600
    473/473 [==============================] - 1s 2ms/step - loss: 20538992640.0000 - val_loss: 19168231424.0000
    Epoch 293/600
    473/473 [==============================] - 1s 2ms/step - loss: 20543725568.0000 - val_loss: 18947067904.0000
    Epoch 294/600
    473/473 [==============================] - 1s 2ms/step - loss: 20421556224.0000 - val_loss: 19263973376.0000
    Epoch 295/600
    473/473 [==============================] - 1s 2ms/step - loss: 20405225472.0000 - val_loss: 18914899968.0000
    Epoch 296/600
    473/473 [==============================] - 1s 2ms/step - loss: 20316565504.0000 - val_loss: 18956099584.0000
    Epoch 297/600
    473/473 [==============================] - 1s 2ms/step - loss: 20391477248.0000 - val_loss: 18852761600.0000
    Epoch 298/600
    473/473 [==============================] - 1s 2ms/step - loss: 20319627264.0000 - val_loss: 18842841088.0000
    Epoch 299/600
    473/473 [==============================] - 1s 1ms/step - loss: 20175398912.0000 - val_loss: 18899232768.0000
    Epoch 300/600
    473/473 [==============================] - 1s 2ms/step - loss: 20237991936.0000 - val_loss: 18794055680.0000
    Epoch 301/600
    473/473 [==============================] - 1s 2ms/step - loss: 20208826368.0000 - val_loss: 18676953088.0000
    Epoch 302/600
    473/473 [==============================] - 1s 2ms/step - loss: 20170948608.0000 - val_loss: 18801395712.0000
    Epoch 303/600
    473/473 [==============================] - 1s 2ms/step - loss: 20153839616.0000 - val_loss: 18655750144.0000
    Epoch 304/600
    473/473 [==============================] - 1s 2ms/step - loss: 20147439616.0000 - val_loss: 18881171456.0000
    Epoch 305/600
    473/473 [==============================] - 1s 2ms/step - loss: 20095424512.0000 - val_loss: 18656301056.0000
    Epoch 306/600
    473/473 [==============================] - 1s 1ms/step - loss: 20016662528.0000 - val_loss: 18689017856.0000
    Epoch 307/600
    473/473 [==============================] - 1s 1ms/step - loss: 20031485952.0000 - val_loss: 18601883648.0000
    Epoch 308/600
    473/473 [==============================] - 1s 1ms/step - loss: 20029286400.0000 - val_loss: 19000616960.0000
    Epoch 309/600
    473/473 [==============================] - 1s 1ms/step - loss: 19877746688.0000 - val_loss: 18513076224.0000
    Epoch 310/600
    473/473 [==============================] - 1s 1ms/step - loss: 19946287104.0000 - val_loss: 18536669184.0000
    Epoch 311/600
    473/473 [==============================] - 1s 2ms/step - loss: 19920564224.0000 - val_loss: 18519648256.0000
    Epoch 312/600
    473/473 [==============================] - 1s 1ms/step - loss: 19823712256.0000 - val_loss: 18617327616.0000
    Epoch 313/600
    473/473 [==============================] - 1s 2ms/step - loss: 19916460032.0000 - val_loss: 18449453056.0000
    Epoch 314/600
    473/473 [==============================] - 1s 2ms/step - loss: 19813292032.0000 - val_loss: 18427480064.0000
    Epoch 315/600
    473/473 [==============================] - 1s 2ms/step - loss: 19797358592.0000 - val_loss: 18401036288.0000
    Epoch 316/600
    473/473 [==============================] - 1s 2ms/step - loss: 19791351808.0000 - val_loss: 18397616128.0000
    Epoch 317/600
    473/473 [==============================] - 1s 2ms/step - loss: 19807604736.0000 - val_loss: 18487490560.0000
    Epoch 318/600
    473/473 [==============================] - 1s 2ms/step - loss: 19671525376.0000 - val_loss: 18866821120.0000
    Epoch 319/600
    473/473 [==============================] - 1s 2ms/step - loss: 19681046528.0000 - val_loss: 18403391488.0000
    Epoch 320/600
    473/473 [==============================] - 1s 2ms/step - loss: 19723100160.0000 - val_loss: 18404976640.0000
    Epoch 321/600
    473/473 [==============================] - 1s 2ms/step - loss: 19716980736.0000 - val_loss: 18240188416.0000
    Epoch 322/600
    473/473 [==============================] - 1s 2ms/step - loss: 19652390912.0000 - val_loss: 18298773504.0000
    Epoch 323/600
    473/473 [==============================] - 1s 2ms/step - loss: 19673139200.0000 - val_loss: 18337882112.0000
    Epoch 324/600
    473/473 [==============================] - 1s 2ms/step - loss: 19599884288.0000 - val_loss: 18728110080.0000
    Epoch 325/600
    473/473 [==============================] - 1s 1ms/step - loss: 19571056640.0000 - val_loss: 18264479744.0000
    Epoch 326/600
    473/473 [==============================] - 1s 2ms/step - loss: 19537463296.0000 - val_loss: 18333145088.0000
    Epoch 327/600
    473/473 [==============================] - 1s 2ms/step - loss: 19535491072.0000 - val_loss: 18292592640.0000
    Epoch 328/600
    473/473 [==============================] - 1s 1ms/step - loss: 19581239296.0000 - val_loss: 18151729152.0000
    Epoch 329/600
    473/473 [==============================] - 1s 2ms/step - loss: 19513413632.0000 - val_loss: 18218532864.0000
    Epoch 330/600
    473/473 [==============================] - 1s 2ms/step - loss: 19491020800.0000 - val_loss: 18222059520.0000
    Epoch 331/600
    473/473 [==============================] - 1s 2ms/step - loss: 19426603008.0000 - val_loss: 18180939776.0000
    Epoch 332/600
    473/473 [==============================] - 1s 1ms/step - loss: 19441784832.0000 - val_loss: 18186723328.0000
    Epoch 333/600
    473/473 [==============================] - 1s 1ms/step - loss: 19391342592.0000 - val_loss: 18211213312.0000
    Epoch 334/600
    473/473 [==============================] - 1s 2ms/step - loss: 19343536128.0000 - val_loss: 18122418176.0000
    Epoch 335/600
    473/473 [==============================] - 1s 2ms/step - loss: 19491379200.0000 - val_loss: 18079653888.0000
    Epoch 336/600
    473/473 [==============================] - 1s 1ms/step - loss: 19502999552.0000 - val_loss: 18050924544.0000
    Epoch 337/600
    473/473 [==============================] - 1s 2ms/step - loss: 19355766784.0000 - val_loss: 18138734592.0000
    Epoch 338/600
    473/473 [==============================] - 1s 2ms/step - loss: 19306090496.0000 - val_loss: 18052775936.0000
    Epoch 339/600
    473/473 [==============================] - 1s 2ms/step - loss: 19292585984.0000 - val_loss: 17978615808.0000
    Epoch 340/600
    473/473 [==============================] - 1s 2ms/step - loss: 19290783744.0000 - val_loss: 18010521600.0000
    Epoch 341/600
    473/473 [==============================] - 1s 2ms/step - loss: 19323547648.0000 - val_loss: 18227941376.0000
    Epoch 342/600
    473/473 [==============================] - 1s 2ms/step - loss: 19279656960.0000 - val_loss: 18061924352.0000
    Epoch 343/600
    473/473 [==============================] - 1s 2ms/step - loss: 19217008640.0000 - val_loss: 17982482432.0000
    Epoch 344/600
    473/473 [==============================] - 1s 1ms/step - loss: 19210117120.0000 - val_loss: 18004699136.0000
    Epoch 345/600
    473/473 [==============================] - 1s 2ms/step - loss: 19228989440.0000 - val_loss: 17884428288.0000
    Epoch 346/600
    473/473 [==============================] - 1s 1ms/step - loss: 19192813568.0000 - val_loss: 18045212672.0000
    Epoch 347/600
    473/473 [==============================] - 1s 2ms/step - loss: 19224832000.0000 - val_loss: 17992083456.0000
    Epoch 348/600
    473/473 [==============================] - 1s 2ms/step - loss: 19165165568.0000 - val_loss: 18336790528.0000
    Epoch 349/600
    473/473 [==============================] - 1s 1ms/step - loss: 19106590720.0000 - val_loss: 17869969408.0000
    Epoch 350/600
    473/473 [==============================] - 1s 1ms/step - loss: 19110416384.0000 - val_loss: 17881892864.0000
    Epoch 351/600
    473/473 [==============================] - 1s 1ms/step - loss: 18997319680.0000 - val_loss: 18528755712.0000
    Epoch 352/600
    473/473 [==============================] - 1s 1ms/step - loss: 19040643072.0000 - val_loss: 17968205824.0000
    Epoch 353/600
    473/473 [==============================] - 1s 1ms/step - loss: 19018301440.0000 - val_loss: 18022451200.0000
    Epoch 354/600
    473/473 [==============================] - 1s 1ms/step - loss: 19032696832.0000 - val_loss: 17838735360.0000
    Epoch 355/600
    473/473 [==============================] - 1s 1ms/step - loss: 19025340416.0000 - val_loss: 17893619712.0000
    Epoch 356/600
    473/473 [==============================] - 1s 1ms/step - loss: 19016839168.0000 - val_loss: 17910267904.0000
    Epoch 357/600
    473/473 [==============================] - 1s 1ms/step - loss: 19032217600.0000 - val_loss: 17758691328.0000
    Epoch 358/600
    473/473 [==============================] - 1s 1ms/step - loss: 18993975296.0000 - val_loss: 17970472960.0000
    Epoch 359/600
    473/473 [==============================] - 1s 1ms/step - loss: 18980395008.0000 - val_loss: 18247841792.0000
    Epoch 360/600
    473/473 [==============================] - 1s 1ms/step - loss: 18964901888.0000 - val_loss: 18020089856.0000
    Epoch 361/600
    473/473 [==============================] - 1s 1ms/step - loss: 18964776960.0000 - val_loss: 17830551552.0000
    Epoch 362/600
    473/473 [==============================] - 1s 1ms/step - loss: 18894727168.0000 - val_loss: 17882939392.0000
    Epoch 363/600
    473/473 [==============================] - 1s 1ms/step - loss: 18888093696.0000 - val_loss: 18051758080.0000
    Epoch 364/600
    473/473 [==============================] - 1s 1ms/step - loss: 18990661632.0000 - val_loss: 18062501888.0000
    Epoch 365/600
    473/473 [==============================] - 1s 1ms/step - loss: 18878939136.0000 - val_loss: 17746679808.0000
    Epoch 366/600
    473/473 [==============================] - 1s 1ms/step - loss: 18838558720.0000 - val_loss: 17799651328.0000
    Epoch 367/600
    473/473 [==============================] - 1s 1ms/step - loss: 18833141760.0000 - val_loss: 17790287872.0000
    Epoch 368/600
    473/473 [==============================] - 1s 1ms/step - loss: 18870812672.0000 - val_loss: 17691527168.0000
    Epoch 369/600
    473/473 [==============================] - 1s 1ms/step - loss: 18813362176.0000 - val_loss: 18113679360.0000
    Epoch 370/600
    473/473 [==============================] - 1s 1ms/step - loss: 18839406592.0000 - val_loss: 18026821632.0000
    Epoch 371/600
    473/473 [==============================] - 1s 1ms/step - loss: 18837907456.0000 - val_loss: 17778188288.0000
    Epoch 372/600
    473/473 [==============================] - 1s 2ms/step - loss: 18943014912.0000 - val_loss: 17654593536.0000
    Epoch 373/600
    473/473 [==============================] - 1s 2ms/step - loss: 18802911232.0000 - val_loss: 17644619776.0000
    Epoch 374/600
    473/473 [==============================] - 1s 1ms/step - loss: 18821208064.0000 - val_loss: 17631838208.0000
    Epoch 375/600
    473/473 [==============================] - 1s 1ms/step - loss: 18823542784.0000 - val_loss: 17630795776.0000
    Epoch 376/600
    473/473 [==============================] - 1s 1ms/step - loss: 18737485824.0000 - val_loss: 17689071616.0000
    Epoch 377/600
    473/473 [==============================] - 1s 1ms/step - loss: 18723479552.0000 - val_loss: 17985196032.0000
    Epoch 378/600
    473/473 [==============================] - 1s 1ms/step - loss: 18707234816.0000 - val_loss: 17644355584.0000
    Epoch 379/600
    473/473 [==============================] - 1s 1ms/step - loss: 18754732032.0000 - val_loss: 17664229376.0000
    Epoch 380/600
    473/473 [==============================] - 1s 1ms/step - loss: 18714769408.0000 - val_loss: 17770264576.0000
    Epoch 381/600
    473/473 [==============================] - 1s 1ms/step - loss: 18710429696.0000 - val_loss: 17638901760.0000
    Epoch 382/600
    473/473 [==============================] - 1s 1ms/step - loss: 18681323520.0000 - val_loss: 17656029184.0000
    Epoch 383/600
    473/473 [==============================] - 1s 1ms/step - loss: 18623275008.0000 - val_loss: 17685542912.0000
    Epoch 384/600
    473/473 [==============================] - 1s 1ms/step - loss: 18682880000.0000 - val_loss: 17622808576.0000
    Epoch 385/600
    473/473 [==============================] - 1s 1ms/step - loss: 18649407488.0000 - val_loss: 17700861952.0000
    Epoch 386/600
    473/473 [==============================] - 1s 1ms/step - loss: 18809057280.0000 - val_loss: 17538838528.0000
    Epoch 387/600
    473/473 [==============================] - 1s 1ms/step - loss: 18591889408.0000 - val_loss: 17757687808.0000
    Epoch 388/600
    473/473 [==============================] - 1s 1ms/step - loss: 18599133184.0000 - val_loss: 17593608192.0000
    Epoch 389/600
    473/473 [==============================] - 1s 1ms/step - loss: 18619621376.0000 - val_loss: 17527836672.0000
    Epoch 390/600
    473/473 [==============================] - 1s 1ms/step - loss: 18588301312.0000 - val_loss: 17560705024.0000
    Epoch 391/600
    473/473 [==============================] - 1s 1ms/step - loss: 18553210880.0000 - val_loss: 17507028992.0000
    Epoch 392/600
    473/473 [==============================] - 1s 1ms/step - loss: 18557501440.0000 - val_loss: 17603403776.0000
    Epoch 393/600
    473/473 [==============================] - 1s 1ms/step - loss: 18541049856.0000 - val_loss: 17578786816.0000
    Epoch 394/600
    473/473 [==============================] - 1s 1ms/step - loss: 18579128320.0000 - val_loss: 17501571072.0000
    Epoch 395/600
    473/473 [==============================] - 1s 1ms/step - loss: 18526490624.0000 - val_loss: 17969106944.0000
    Epoch 396/600
    473/473 [==============================] - 1s 1ms/step - loss: 18516903936.0000 - val_loss: 17481367552.0000
    Epoch 397/600
    473/473 [==============================] - 1s 1ms/step - loss: 18580699136.0000 - val_loss: 17576458240.0000
    Epoch 398/600
    473/473 [==============================] - 1s 2ms/step - loss: 18534488064.0000 - val_loss: 17466906624.0000
    Epoch 399/600
    473/473 [==============================] - 1s 2ms/step - loss: 18451939328.0000 - val_loss: 17915310080.0000
    Epoch 400/600
    473/473 [==============================] - 1s 1ms/step - loss: 18499031040.0000 - val_loss: 17438113792.0000
    Epoch 401/600
    473/473 [==============================] - 1s 1ms/step - loss: 18488735744.0000 - val_loss: 17850093568.0000
    Epoch 402/600
    473/473 [==============================] - 1s 1ms/step - loss: 18474928128.0000 - val_loss: 17620205568.0000
    Epoch 403/600
    473/473 [==============================] - 1s 1ms/step - loss: 18470092800.0000 - val_loss: 17626368000.0000
    Epoch 404/600
    473/473 [==============================] - 1s 1ms/step - loss: 18416117760.0000 - val_loss: 17570617344.0000
    Epoch 405/600
    473/473 [==============================] - 1s 1ms/step - loss: 18378555392.0000 - val_loss: 17476126720.0000
    Epoch 406/600
    473/473 [==============================] - 1s 1ms/step - loss: 18393858048.0000 - val_loss: 17691398144.0000
    Epoch 407/600
    473/473 [==============================] - 1s 1ms/step - loss: 18394390528.0000 - val_loss: 17950654464.0000
    Epoch 408/600
    473/473 [==============================] - 1s 1ms/step - loss: 18322989056.0000 - val_loss: 17428695040.0000
    Epoch 409/600
    473/473 [==============================] - 1s 1ms/step - loss: 18425579520.0000 - val_loss: 17341360128.0000
    Epoch 410/600
    473/473 [==============================] - 1s 1ms/step - loss: 18322399232.0000 - val_loss: 17506250752.0000
    Epoch 411/600
    473/473 [==============================] - 1s 1ms/step - loss: 18310373376.0000 - val_loss: 17523437568.0000
    Epoch 412/600
    473/473 [==============================] - 1s 1ms/step - loss: 18381557760.0000 - val_loss: 17321398272.0000
    Epoch 413/600
    473/473 [==============================] - 1s 1ms/step - loss: 18340489216.0000 - val_loss: 17449562112.0000
    Epoch 414/600
    473/473 [==============================] - 1s 1ms/step - loss: 18343964672.0000 - val_loss: 17436860416.0000
    Epoch 415/600
    473/473 [==============================] - 1s 1ms/step - loss: 18288943104.0000 - val_loss: 17538873344.0000
    Epoch 416/600
    473/473 [==============================] - 1s 1ms/step - loss: 18294360064.0000 - val_loss: 17347235840.0000
    Epoch 417/600
    473/473 [==============================] - 1s 1ms/step - loss: 18359437312.0000 - val_loss: 17449193472.0000
    Epoch 418/600
    473/473 [==============================] - 1s 1ms/step - loss: 18205757440.0000 - val_loss: 17397307392.0000
    Epoch 419/600
    473/473 [==============================] - 1s 1ms/step - loss: 18302670848.0000 - val_loss: 17377890304.0000
    Epoch 420/600
    473/473 [==============================] - 1s 1ms/step - loss: 18294020096.0000 - val_loss: 17388718080.0000
    Epoch 421/600
    473/473 [==============================] - 1s 1ms/step - loss: 18223216640.0000 - val_loss: 17380808704.0000
    Epoch 422/600
    473/473 [==============================] - 1s 1ms/step - loss: 18238715904.0000 - val_loss: 17760366592.0000
    Epoch 423/600
    473/473 [==============================] - 1s 2ms/step - loss: 18220853248.0000 - val_loss: 17355239424.0000
    Epoch 424/600
    473/473 [==============================] - 1s 2ms/step - loss: 18252570624.0000 - val_loss: 17422014464.0000
    Epoch 425/600
    473/473 [==============================] - 1s 1ms/step - loss: 18218139648.0000 - val_loss: 17294450688.0000
    Epoch 426/600
    473/473 [==============================] - 1s 1ms/step - loss: 18244765696.0000 - val_loss: 17416495104.0000
    Epoch 427/600
    473/473 [==============================] - 1s 1ms/step - loss: 18205442048.0000 - val_loss: 17602385920.0000
    Epoch 428/600
    473/473 [==============================] - 1s 1ms/step - loss: 18196033536.0000 - val_loss: 17351749632.0000
    Epoch 429/600
    473/473 [==============================] - 1s 1ms/step - loss: 18173798400.0000 - val_loss: 17372803072.0000
    Epoch 430/600
    473/473 [==============================] - 1s 1ms/step - loss: 18197231616.0000 - val_loss: 17405116416.0000
    Epoch 431/600
    473/473 [==============================] - 1s 1ms/step - loss: 18198943744.0000 - val_loss: 17280016384.0000
    Epoch 432/600
    473/473 [==============================] - 1s 1ms/step - loss: 18144942080.0000 - val_loss: 17327583232.0000
    Epoch 433/600
    473/473 [==============================] - 1s 1ms/step - loss: 18104705024.0000 - val_loss: 17326000128.0000
    Epoch 434/600
    473/473 [==============================] - 1s 1ms/step - loss: 18103824384.0000 - val_loss: 17429106688.0000
    Epoch 435/600
    473/473 [==============================] - 1s 1ms/step - loss: 18095536128.0000 - val_loss: 17245773824.0000
    Epoch 436/600
    473/473 [==============================] - 1s 1ms/step - loss: 18098528256.0000 - val_loss: 17259995136.0000
    Epoch 437/600
    473/473 [==============================] - 1s 1ms/step - loss: 18084825088.0000 - val_loss: 17517205504.0000
    Epoch 438/600
    473/473 [==============================] - 1s 1ms/step - loss: 18075932672.0000 - val_loss: 17465911296.0000
    Epoch 439/600
    473/473 [==============================] - 1s 1ms/step - loss: 18075916288.0000 - val_loss: 17209536512.0000
    Epoch 440/600
    473/473 [==============================] - 1s 1ms/step - loss: 18012090368.0000 - val_loss: 17873369088.0000
    Epoch 441/600
    473/473 [==============================] - 1s 1ms/step - loss: 18143148032.0000 - val_loss: 17191303168.0000
    Epoch 442/600
    473/473 [==============================] - 1s 1ms/step - loss: 18085171200.0000 - val_loss: 17168362496.0000
    Epoch 443/600
    473/473 [==============================] - 1s 1ms/step - loss: 18060204032.0000 - val_loss: 17257377792.0000
    Epoch 444/600
    473/473 [==============================] - 1s 1ms/step - loss: 17957117952.0000 - val_loss: 17383702528.0000
    Epoch 445/600
    473/473 [==============================] - 1s 1ms/step - loss: 18085681152.0000 - val_loss: 17376514048.0000
    Epoch 446/600
    473/473 [==============================] - 1s 1ms/step - loss: 17986887680.0000 - val_loss: 17364385792.0000
    Epoch 447/600
    473/473 [==============================] - 1s 1ms/step - loss: 18071627776.0000 - val_loss: 17414070272.0000
    Epoch 448/600
    473/473 [==============================] - 1s 1ms/step - loss: 18041096192.0000 - val_loss: 17320699904.0000
    Epoch 449/600
    473/473 [==============================] - 1s 2ms/step - loss: 17906735104.0000 - val_loss: 17188409344.0000
    Epoch 450/600
    473/473 [==============================] - 1s 1ms/step - loss: 17904328704.0000 - val_loss: 17216104448.0000
    Epoch 451/600
    473/473 [==============================] - 1s 1ms/step - loss: 17999233024.0000 - val_loss: 17224151040.0000
    Epoch 452/600
    473/473 [==============================] - 1s 1ms/step - loss: 17913661440.0000 - val_loss: 17149563904.0000
    Epoch 453/600
    473/473 [==============================] - 1s 1ms/step - loss: 17885898752.0000 - val_loss: 17244923904.0000
    Epoch 454/600
    473/473 [==============================] - 1s 1ms/step - loss: 17927872512.0000 - val_loss: 17704316928.0000
    Epoch 455/600
    473/473 [==============================] - 1s 1ms/step - loss: 18020169728.0000 - val_loss: 17281669120.0000
    Epoch 456/600
    473/473 [==============================] - 1s 1ms/step - loss: 17904230400.0000 - val_loss: 17299388416.0000
    Epoch 457/600
    473/473 [==============================] - 1s 1ms/step - loss: 17946742784.0000 - val_loss: 17155721216.0000
    Epoch 458/600
    473/473 [==============================] - 1s 1ms/step - loss: 17902841856.0000 - val_loss: 17166797824.0000
    Epoch 459/600
    473/473 [==============================] - 1s 1ms/step - loss: 17936246784.0000 - val_loss: 17379399680.0000
    Epoch 460/600
    473/473 [==============================] - 1s 1ms/step - loss: 17925380096.0000 - val_loss: 17196593152.0000
    Epoch 461/600
    473/473 [==============================] - 1s 1ms/step - loss: 17896468480.0000 - val_loss: 17116503040.0000
    Epoch 462/600
    473/473 [==============================] - 1s 1ms/step - loss: 17859614720.0000 - val_loss: 17122073600.0000
    Epoch 463/600
    473/473 [==============================] - 1s 1ms/step - loss: 17959639040.0000 - val_loss: 17136352256.0000
    Epoch 464/600
    473/473 [==============================] - 1s 1ms/step - loss: 17850298368.0000 - val_loss: 17255776256.0000
    Epoch 465/600
    473/473 [==============================] - 1s 1ms/step - loss: 17810624512.0000 - val_loss: 17160594432.0000
    Epoch 466/600
    473/473 [==============================] - 1s 1ms/step - loss: 17871405056.0000 - val_loss: 17548687360.0000
    Epoch 467/600
    473/473 [==============================] - 1s 1ms/step - loss: 17871730688.0000 - val_loss: 17470132224.0000
    Epoch 468/600
    473/473 [==============================] - 1s 1ms/step - loss: 17798203392.0000 - val_loss: 17366677504.0000
    Epoch 469/600
    473/473 [==============================] - 1s 1ms/step - loss: 17805598720.0000 - val_loss: 17134791680.0000
    Epoch 470/600
    473/473 [==============================] - 1s 1ms/step - loss: 17799675904.0000 - val_loss: 17151632384.0000
    Epoch 471/600
    473/473 [==============================] - 1s 1ms/step - loss: 17791178752.0000 - val_loss: 17127333888.0000
    Epoch 472/600
    473/473 [==============================] - 1s 1ms/step - loss: 17833986048.0000 - val_loss: 17094616064.0000
    Epoch 473/600
    473/473 [==============================] - 1s 1ms/step - loss: 17829089280.0000 - val_loss: 17092102144.0000
    Epoch 474/600
    473/473 [==============================] - 1s 2ms/step - loss: 17749399552.0000 - val_loss: 17106300928.0000
    Epoch 475/600
    473/473 [==============================] - 1s 2ms/step - loss: 17746710528.0000 - val_loss: 17093426176.0000
    Epoch 476/600
    473/473 [==============================] - 1s 1ms/step - loss: 17678282752.0000 - val_loss: 17366095872.0000
    Epoch 477/600
    473/473 [==============================] - 1s 1ms/step - loss: 17775861760.0000 - val_loss: 17090862080.0000
    Epoch 478/600
    473/473 [==============================] - 1s 1ms/step - loss: 17819359232.0000 - val_loss: 17044538368.0000
    Epoch 479/600
    473/473 [==============================] - 1s 1ms/step - loss: 17707528192.0000 - val_loss: 17340502016.0000
    Epoch 480/600
    473/473 [==============================] - 1s 1ms/step - loss: 17746149376.0000 - val_loss: 17058469888.0000
    Epoch 481/600
    473/473 [==============================] - 1s 1ms/step - loss: 17737068544.0000 - val_loss: 17069565952.0000
    Epoch 482/600
    473/473 [==============================] - 1s 1ms/step - loss: 17730414592.0000 - val_loss: 17175115776.0000
    Epoch 483/600
    473/473 [==============================] - 1s 1ms/step - loss: 17768204288.0000 - val_loss: 17194547200.0000
    Epoch 484/600
    473/473 [==============================] - 1s 1ms/step - loss: 17693988864.0000 - val_loss: 17132826624.0000
    Epoch 485/600
    473/473 [==============================] - 1s 1ms/step - loss: 17681315840.0000 - val_loss: 17372717056.0000
    Epoch 486/600
    473/473 [==============================] - 1s 1ms/step - loss: 17707943936.0000 - val_loss: 17299476480.0000
    Epoch 487/600
    473/473 [==============================] - 1s 1ms/step - loss: 17674092544.0000 - val_loss: 17075566592.0000
    Epoch 488/600
    473/473 [==============================] - 1s 1ms/step - loss: 17823997952.0000 - val_loss: 17117336576.0000
    Epoch 489/600
    473/473 [==============================] - 1s 1ms/step - loss: 17684342784.0000 - val_loss: 17137377280.0000
    Epoch 490/600
    473/473 [==============================] - 1s 1ms/step - loss: 17705701376.0000 - val_loss: 17213237248.0000
    Epoch 491/600
    473/473 [==============================] - 1s 1ms/step - loss: 17687574528.0000 - val_loss: 17092782080.0000
    Epoch 492/600
    473/473 [==============================] - 1s 1ms/step - loss: 17694222336.0000 - val_loss: 17122529280.0000
    Epoch 493/600
    473/473 [==============================] - 1s 1ms/step - loss: 17613074432.0000 - val_loss: 17166010368.0000
    Epoch 494/600
    473/473 [==============================] - 1s 1ms/step - loss: 17609416704.0000 - val_loss: 17105862656.0000
    Epoch 495/600
    473/473 [==============================] - 1s 1ms/step - loss: 17665769472.0000 - val_loss: 17143525376.0000
    Epoch 496/600
    473/473 [==============================] - 1s 1ms/step - loss: 17634183168.0000 - val_loss: 17179615232.0000
    Epoch 497/600
    473/473 [==============================] - 1s 1ms/step - loss: 17647771648.0000 - val_loss: 17080997888.0000
    Epoch 498/600
    473/473 [==============================] - 1s 1ms/step - loss: 17643001856.0000 - val_loss: 16981613568.0000
    Epoch 499/600
    473/473 [==============================] - 1s 1ms/step - loss: 17590839296.0000 - val_loss: 17047828480.0000
    Epoch 500/600
    473/473 [==============================] - 1s 2ms/step - loss: 17611876352.0000 - val_loss: 16985080832.0000
    Epoch 501/600
    473/473 [==============================] - 1s 1ms/step - loss: 17618726912.0000 - val_loss: 17112437760.0000
    Epoch 502/600
    473/473 [==============================] - 1s 1ms/step - loss: 17596721152.0000 - val_loss: 16969800704.0000
    Epoch 503/600
    473/473 [==============================] - 1s 1ms/step - loss: 17625208832.0000 - val_loss: 17023882240.0000
    Epoch 504/600
    473/473 [==============================] - 1s 1ms/step - loss: 17599569920.0000 - val_loss: 17028604928.0000
    Epoch 505/600
    473/473 [==============================] - 1s 1ms/step - loss: 17571622912.0000 - val_loss: 17611659264.0000
    Epoch 506/600
    473/473 [==============================] - 1s 1ms/step - loss: 17709543424.0000 - val_loss: 17075666944.0000
    Epoch 507/600
    473/473 [==============================] - 1s 1ms/step - loss: 17607297024.0000 - val_loss: 16921198592.0000
    Epoch 508/600
    473/473 [==============================] - 1s 1ms/step - loss: 17590515712.0000 - val_loss: 17116786688.0000
    Epoch 509/600
    473/473 [==============================] - 1s 1ms/step - loss: 17541568512.0000 - val_loss: 17096473600.0000
    Epoch 510/600
    473/473 [==============================] - 1s 1ms/step - loss: 17560678400.0000 - val_loss: 17023244288.0000
    Epoch 511/600
    473/473 [==============================] - 1s 1ms/step - loss: 17556850688.0000 - val_loss: 16941773824.0000
    Epoch 512/600
    473/473 [==============================] - 1s 1ms/step - loss: 17473458176.0000 - val_loss: 17291599872.0000
    Epoch 513/600
    473/473 [==============================] - 1s 1ms/step - loss: 17550424064.0000 - val_loss: 16989191168.0000
    Epoch 514/600
    473/473 [==============================] - 1s 1ms/step - loss: 17581203456.0000 - val_loss: 16963018752.0000
    Epoch 515/600
    473/473 [==============================] - 1s 1ms/step - loss: 17486444544.0000 - val_loss: 16979864576.0000
    Epoch 516/600
    473/473 [==============================] - 1s 1ms/step - loss: 17441865728.0000 - val_loss: 17129488384.0000
    Epoch 517/600
    473/473 [==============================] - 1s 1ms/step - loss: 17620860928.0000 - val_loss: 16986841088.0000
    Epoch 518/600
    473/473 [==============================] - 1s 1ms/step - loss: 17581676544.0000 - val_loss: 16951170048.0000
    Epoch 519/600
    473/473 [==============================] - 1s 1ms/step - loss: 17510649856.0000 - val_loss: 16956873728.0000
    Epoch 520/600
    473/473 [==============================] - 1s 1ms/step - loss: 17504145408.0000 - val_loss: 16996211712.0000
    Epoch 521/600
    473/473 [==============================] - 1s 1ms/step - loss: 17522776064.0000 - val_loss: 17256769536.0000
    Epoch 522/600
    473/473 [==============================] - 1s 1ms/step - loss: 17464897536.0000 - val_loss: 16952413184.0000
    Epoch 523/600
    473/473 [==============================] - 1s 1ms/step - loss: 17508679680.0000 - val_loss: 16895735808.0000
    Epoch 524/600
    473/473 [==============================] - 1s 1ms/step - loss: 17459556352.0000 - val_loss: 16911131648.0000
    Epoch 525/600
    473/473 [==============================] - 1s 1ms/step - loss: 17430720512.0000 - val_loss: 17050735616.0000
    Epoch 526/600
    473/473 [==============================] - 1s 2ms/step - loss: 17504677888.0000 - val_loss: 16859044864.0000
    Epoch 527/600
    473/473 [==============================] - 1s 1ms/step - loss: 17433540608.0000 - val_loss: 17243711488.0000
    Epoch 528/600
    473/473 [==============================] - 1s 1ms/step - loss: 17578121216.0000 - val_loss: 16904546304.0000
    Epoch 529/600
    473/473 [==============================] - 1s 1ms/step - loss: 17440028672.0000 - val_loss: 17352622080.0000
    Epoch 530/600
    473/473 [==============================] - 1s 1ms/step - loss: 17387616256.0000 - val_loss: 16837360640.0000
    Epoch 531/600
    473/473 [==============================] - 1s 1ms/step - loss: 17424109568.0000 - val_loss: 16903471104.0000
    Epoch 532/600
    473/473 [==============================] - 1s 1ms/step - loss: 17428013056.0000 - val_loss: 17044509696.0000
    Epoch 533/600
    473/473 [==============================] - 1s 1ms/step - loss: 17506926592.0000 - val_loss: 16911598592.0000
    Epoch 534/600
    473/473 [==============================] - 1s 1ms/step - loss: 17349877760.0000 - val_loss: 16847442944.0000
    Epoch 535/600
    473/473 [==============================] - 1s 1ms/step - loss: 17462859776.0000 - val_loss: 16960095232.0000
    Epoch 536/600
    473/473 [==============================] - 1s 1ms/step - loss: 17456762880.0000 - val_loss: 16920781824.0000
    Epoch 537/600
    473/473 [==============================] - 1s 1ms/step - loss: 17413384192.0000 - val_loss: 16843290624.0000
    Epoch 538/600
    473/473 [==============================] - 1s 1ms/step - loss: 17451384832.0000 - val_loss: 16922301440.0000
    Epoch 539/600
    473/473 [==============================] - 1s 1ms/step - loss: 17448591360.0000 - val_loss: 17838651392.0000
    Epoch 540/600
    473/473 [==============================] - 1s 1ms/step - loss: 17391026176.0000 - val_loss: 17110682624.0000
    Epoch 541/600
    473/473 [==============================] - 1s 1ms/step - loss: 17349730304.0000 - val_loss: 17340135424.0000
    Epoch 542/600
    473/473 [==============================] - 1s 1ms/step - loss: 17399525376.0000 - val_loss: 16785908736.0000
    Epoch 543/600
    473/473 [==============================] - 1s 1ms/step - loss: 17361887232.0000 - val_loss: 16818991104.0000
    Epoch 544/600
    473/473 [==============================] - 1s 1ms/step - loss: 17382201344.0000 - val_loss: 16910757888.0000
    Epoch 545/600
    473/473 [==============================] - 1s 1ms/step - loss: 17384681472.0000 - val_loss: 16815897600.0000
    Epoch 546/600
    473/473 [==============================] - 1s 1ms/step - loss: 17365938176.0000 - val_loss: 16917916672.0000
    Epoch 547/600
    473/473 [==============================] - 1s 1ms/step - loss: 17338167296.0000 - val_loss: 16802512896.0000
    Epoch 548/600
    473/473 [==============================] - 1s 1ms/step - loss: 17397225472.0000 - val_loss: 16869421056.0000
    Epoch 549/600
    473/473 [==============================] - 1s 1ms/step - loss: 17359169536.0000 - val_loss: 16824785920.0000
    Epoch 550/600
    473/473 [==============================] - 1s 1ms/step - loss: 17350033408.0000 - val_loss: 16851249152.0000
    Epoch 551/600
    473/473 [==============================] - 1s 2ms/step - loss: 17280577536.0000 - val_loss: 17378557952.0000
    Epoch 552/600
    473/473 [==============================] - ETA: 0s - loss: 17412243456.000 - 1s 1ms/step - loss: 17344638976.0000 - val_loss: 16975721472.0000
    Epoch 553/600
    473/473 [==============================] - 1s 1ms/step - loss: 17338621952.0000 - val_loss: 16800025600.0000
    Epoch 554/600
    473/473 [==============================] - 1s 1ms/step - loss: 17316055040.0000 - val_loss: 16862316544.0000
    Epoch 555/600
    473/473 [==============================] - 1s 1ms/step - loss: 17375266816.0000 - val_loss: 16915309568.0000
    Epoch 556/600
    473/473 [==============================] - 1s 1ms/step - loss: 17359138816.0000 - val_loss: 16800276480.0000
    Epoch 557/600
    473/473 [==============================] - 1s 1ms/step - loss: 17318199296.0000 - val_loss: 17024293888.0000
    Epoch 558/600
    473/473 [==============================] - 1s 1ms/step - loss: 17352030208.0000 - val_loss: 16792160256.0000
    Epoch 559/600
    473/473 [==============================] - 1s 1ms/step - loss: 17261432832.0000 - val_loss: 16845987840.0000
    Epoch 560/600
    473/473 [==============================] - 1s 1ms/step - loss: 17349748736.0000 - val_loss: 16852600832.0000
    Epoch 561/600
    473/473 [==============================] - 1s 1ms/step - loss: 17335138304.0000 - val_loss: 16817105920.0000
    Epoch 562/600
    473/473 [==============================] - 1s 1ms/step - loss: 17310754816.0000 - val_loss: 16706452480.0000
    Epoch 563/600
    473/473 [==============================] - 1s 1ms/step - loss: 17309636608.0000 - val_loss: 16773080064.0000
    Epoch 564/600
    473/473 [==============================] - 1s 1ms/step - loss: 17233534976.0000 - val_loss: 16868401152.0000
    Epoch 565/600
    473/473 [==============================] - 1s 1ms/step - loss: 17327622144.0000 - val_loss: 16726552576.0000
    Epoch 566/600
    473/473 [==============================] - 1s 1ms/step - loss: 17243774976.0000 - val_loss: 17355145216.0000
    Epoch 567/600
    473/473 [==============================] - 1s 1ms/step - loss: 17244905472.0000 - val_loss: 16844094464.0000
    Epoch 568/600
    473/473 [==============================] - 1s 1ms/step - loss: 17247678464.0000 - val_loss: 16700102656.0000
    Epoch 569/600
    473/473 [==============================] - 1s 1ms/step - loss: 17329719296.0000 - val_loss: 16870217728.0000
    Epoch 570/600
    473/473 [==============================] - 1s 1ms/step - loss: 17246330880.0000 - val_loss: 16812294144.0000
    Epoch 571/600
    473/473 [==============================] - 1s 1ms/step - loss: 17253181440.0000 - val_loss: 16759370752.0000
    Epoch 572/600
    473/473 [==============================] - 1s 1ms/step - loss: 17247365120.0000 - val_loss: 16862174208.0000
    Epoch 573/600
    473/473 [==============================] - 1s 1ms/step - loss: 17229746176.0000 - val_loss: 17101646848.0000
    Epoch 574/600
    473/473 [==============================] - 1s 1ms/step - loss: 17321803776.0000 - val_loss: 16800883712.0000
    Epoch 575/600
    473/473 [==============================] - 1s 1ms/step - loss: 17187717120.0000 - val_loss: 16796655616.0000
    Epoch 576/600
    473/473 [==============================] - 1s 1ms/step - loss: 17233430528.0000 - val_loss: 16980755456.0000
    Epoch 577/600
    473/473 [==============================] - 1s 2ms/step - loss: 17202589696.0000 - val_loss: 16744699904.0000
    Epoch 578/600
    473/473 [==============================] - 1s 1ms/step - loss: 17244815360.0000 - val_loss: 16851810304.0000
    Epoch 579/600
    473/473 [==============================] - 1s 1ms/step - loss: 17227044864.0000 - val_loss: 16968036352.0000
    Epoch 580/600
    473/473 [==============================] - 1s 1ms/step - loss: 17232910336.0000 - val_loss: 17069802496.0000
    Epoch 581/600
    473/473 [==============================] - 1s 1ms/step - loss: 17206228992.0000 - val_loss: 16742193152.0000
    Epoch 582/600
    473/473 [==============================] - 1s 1ms/step - loss: 17273309184.0000 - val_loss: 16703675392.0000
    Epoch 583/600
    473/473 [==============================] - 1s 1ms/step - loss: 17196652544.0000 - val_loss: 16698246144.0000
    Epoch 584/600
    473/473 [==============================] - 1s 1ms/step - loss: 17147912192.0000 - val_loss: 17299116032.0000
    Epoch 585/600
    473/473 [==============================] - 1s 1ms/step - loss: 17177084928.0000 - val_loss: 16849084416.0000
    Epoch 586/600
    473/473 [==============================] - 1s 1ms/step - loss: 17275084800.0000 - val_loss: 16982516736.0000
    Epoch 587/600
    473/473 [==============================] - 1s 1ms/step - loss: 17124235264.0000 - val_loss: 16713549824.0000
    Epoch 588/600
    473/473 [==============================] - 1s 1ms/step - loss: 17203030016.0000 - val_loss: 16883893248.0000
    Epoch 589/600
    473/473 [==============================] - 1s 1ms/step - loss: 17091122176.0000 - val_loss: 16836400128.0000
    Epoch 590/600
    473/473 [==============================] - 1s 1ms/step - loss: 17193918464.0000 - val_loss: 17002910720.0000
    Epoch 591/600
    473/473 [==============================] - 1s 1ms/step - loss: 17098727424.0000 - val_loss: 17140400128.0000
    Epoch 592/600
    473/473 [==============================] - 1s 1ms/step - loss: 17197176832.0000 - val_loss: 16717284352.0000
    Epoch 593/600
    473/473 [==============================] - 1s 1ms/step - loss: 17125906432.0000 - val_loss: 16994859008.0000
    Epoch 594/600
    473/473 [==============================] - 1s 1ms/step - loss: 17103512576.0000 - val_loss: 16705495040.0000
    Epoch 595/600
    473/473 [==============================] - 1s 1ms/step - loss: 17039226880.0000 - val_loss: 16678105088.0000
    Epoch 596/600
    473/473 [==============================] - 1s 1ms/step - loss: 17154993152.0000 - val_loss: 16768863232.0000
    Epoch 597/600
    473/473 [==============================] - 1s 1ms/step - loss: 17118851072.0000 - val_loss: 16999837696.0000
    Epoch 598/600
    473/473 [==============================] - 1s 1ms/step - loss: 17170586624.0000 - val_loss: 16748457984.0000
    Epoch 599/600
    473/473 [==============================] - 1s 1ms/step - loss: 17130048512.0000 - val_loss: 17116685312.0000
    Epoch 600/600
    473/473 [==============================] - 1s 1ms/step - loss: 17128094720.0000 - val_loss: 16697310208.0000
    




    <tensorflow.python.keras.callbacks.History at 0x288595b5040>




```python
loss_df = pd.DataFrame(model.history.history)
```


```python
loss_df.head()
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
      <th>loss</th>
      <th>val_loss</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4.110695e+11</td>
      <td>2.999658e+11</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.399407e+11</td>
      <td>9.501938e+10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9.581674e+10</td>
      <td>9.000761e+10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.010604e+10</td>
      <td>8.372617e+10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8.317940e+10</td>
      <td>7.671190e+10</td>
    </tr>
  </tbody>
</table>
</div>




```python
loss_df.plot()
```




    <AxesSubplot:>




    
![png](output_42_1.png)
    



```python
pred = model.predict(X_test)
```


```python
from sklearn.metrics import mean_squared_error,mean_absolute_error,explained_variance_score, r2_score
```


```python
np.sqrt(mean_squared_error(y_test,pred))
```




    129218.07969087426




```python
df['price'].median()
```




    450000.0




```python
mean_absolute_error(y_test,pred)
```




    77320.7680314429




```python
explained_variance_score(y_test,pred)
```




    0.8741550060779331




```python
plt.figure(figsize=(12,6))
plt.scatter(y_test,pred)
plt.plot(y_test,y_test,'r')
```




    [<matplotlib.lines.Line2D at 0x2885b8a7070>]




    
![png](output_49_1.png)
    



```python
new_val = df.drop('price',axis=1).iloc[0].values
new_val = sc.transform(new_val.reshape(-1,19))
```


```python
model.predict(new_val)
```




    array([[230305.47]], dtype=float32)




```python
df['price'][0]
```




    221900.0



# pretty close

# comparing the ann model with catboost


```python
from catboost import CatBoostRegressor
```


```python
cb = CatBoostRegressor(random_state=123,iterations=10000)
```


```python
cb.fit(X_train,y_train,eval_set=(X_test,y_test), early_stopping_rounds=200)
```

    Learning rate set to 0.01834
    0:	learn: 364256.5842444	test: 360131.3789137	best: 360131.3789137 (0)	total: 6.05ms	remaining: 1m
    1:	learn: 360093.8121386	test: 356308.8019763	best: 356308.8019763 (1)	total: 11.4ms	remaining: 56.9s
    2:	learn: 355878.2558128	test: 352424.5678476	best: 352424.5678476 (2)	total: 16.5ms	remaining: 55.1s
    3:	learn: 351689.6059159	test: 348477.9227824	best: 348477.9227824 (3)	total: 21.6ms	remaining: 54.1s
    4:	learn: 347819.1028876	test: 344900.2988357	best: 344900.2988357 (4)	total: 26.9ms	remaining: 53.9s
    5:	learn: 343757.1839576	test: 341178.2676424	best: 341178.2676424 (5)	total: 32ms	remaining: 53.3s
    6:	learn: 339958.1065311	test: 337673.1757783	best: 337673.1757783 (6)	total: 37.4ms	remaining: 53.4s
    7:	learn: 336129.4223871	test: 334151.9526282	best: 334151.9526282 (7)	total: 42.7ms	remaining: 53.4s
    8:	learn: 332271.8239567	test: 330505.7673754	best: 330505.7673754 (8)	total: 48ms	remaining: 53.2s
    9:	learn: 328775.0501716	test: 327225.3741556	best: 327225.3741556 (9)	total: 52.9ms	remaining: 52.8s
    10:	learn: 325157.2046322	test: 323912.0131777	best: 323912.0131777 (10)	total: 58.4ms	remaining: 53s
    11:	learn: 321790.9710752	test: 320868.5008464	best: 320868.5008464 (11)	total: 63.6ms	remaining: 52.9s
    12:	learn: 318371.2444516	test: 317674.5228326	best: 317674.5228326 (12)	total: 68.5ms	remaining: 52.6s
    13:	learn: 315057.8134828	test: 314594.0274643	best: 314594.0274643 (13)	total: 73.5ms	remaining: 52.5s
    14:	learn: 311737.2831208	test: 311440.9286068	best: 311440.9286068 (14)	total: 78.6ms	remaining: 52.3s
    15:	learn: 308568.1332342	test: 308565.2799923	best: 308565.2799923 (15)	total: 84.1ms	remaining: 52.5s
    16:	learn: 305391.6417332	test: 305614.1681717	best: 305614.1681717 (16)	total: 89.9ms	remaining: 52.8s
    17:	learn: 302350.2741349	test: 302783.1234307	best: 302783.1234307 (17)	total: 95.9ms	remaining: 53.2s
    18:	learn: 299320.1429248	test: 299940.0639500	best: 299940.0639500 (18)	total: 102ms	remaining: 53.4s
    19:	learn: 296311.9499442	test: 297028.3676029	best: 297028.3676029 (19)	total: 107ms	remaining: 53.3s
    20:	learn: 293326.6045845	test: 294175.5321244	best: 294175.5321244 (20)	total: 112ms	remaining: 53.3s
    21:	learn: 290335.5207216	test: 291461.0821811	best: 291461.0821811 (21)	total: 117ms	remaining: 53s
    22:	learn: 287522.1981765	test: 288877.5969172	best: 288877.5969172 (22)	total: 122ms	remaining: 52.8s
    23:	learn: 284663.4399909	test: 286369.7668350	best: 286369.7668350 (23)	total: 127ms	remaining: 52.7s
    24:	learn: 281823.3824972	test: 283833.5676200	best: 283833.5676200 (24)	total: 132ms	remaining: 52.8s
    25:	learn: 279091.3827078	test: 281314.1367402	best: 281314.1367402 (25)	total: 137ms	remaining: 52.7s
    26:	learn: 276561.9982465	test: 278949.4292467	best: 278949.4292467 (26)	total: 143ms	remaining: 52.7s
    27:	learn: 273902.7488669	test: 276423.0625131	best: 276423.0625131 (27)	total: 149ms	remaining: 52.9s
    28:	learn: 271369.5406263	test: 274126.5185087	best: 274126.5185087 (28)	total: 154ms	remaining: 53.1s
    29:	learn: 268943.3117211	test: 271974.6918253	best: 271974.6918253 (29)	total: 160ms	remaining: 53.2s
    30:	learn: 266372.7595741	test: 269466.0955742	best: 269466.0955742 (30)	total: 166ms	remaining: 53.4s
    31:	learn: 263967.2778124	test: 267309.9009169	best: 267309.9009169 (31)	total: 172ms	remaining: 53.6s
    32:	learn: 261717.9451754	test: 265120.6154106	best: 265120.6154106 (32)	total: 178ms	remaining: 53.8s
    33:	learn: 259412.9341731	test: 262997.9678572	best: 262997.9678572 (33)	total: 185ms	remaining: 54.1s
    34:	learn: 257165.9395282	test: 260854.3521778	best: 260854.3521778 (34)	total: 191ms	remaining: 54.3s
    35:	learn: 254958.5780935	test: 258859.3017718	best: 258859.3017718 (35)	total: 196ms	remaining: 54.3s
    36:	learn: 252841.6306161	test: 256880.1589872	best: 256880.1589872 (36)	total: 202ms	remaining: 54.4s
    37:	learn: 250650.3160367	test: 254957.5954446	best: 254957.5954446 (37)	total: 207ms	remaining: 54.3s
    38:	learn: 248485.1676307	test: 252969.1261454	best: 252969.1261454 (38)	total: 212ms	remaining: 54.2s
    39:	learn: 246578.1490827	test: 251211.0290418	best: 251211.0290418 (39)	total: 217ms	remaining: 54.1s
    40:	learn: 244615.0090662	test: 249400.3275983	best: 249400.3275983 (40)	total: 222ms	remaining: 54s
    41:	learn: 242718.5257820	test: 247633.9177603	best: 247633.9177603 (41)	total: 228ms	remaining: 54s
    42:	learn: 240789.2374178	test: 245829.5070755	best: 245829.5070755 (42)	total: 234ms	remaining: 54.1s
    43:	learn: 238747.2515662	test: 243969.5887635	best: 243969.5887635 (43)	total: 240ms	remaining: 54.3s
    44:	learn: 236854.4535535	test: 242256.0205494	best: 242256.0205494 (44)	total: 246ms	remaining: 54.4s
    45:	learn: 235078.2528252	test: 240477.9334760	best: 240477.9334760 (45)	total: 252ms	remaining: 54.6s
    46:	learn: 233220.3830786	test: 238694.9750524	best: 238694.9750524 (46)	total: 259ms	remaining: 54.8s
    47:	learn: 231527.8419944	test: 237046.8669315	best: 237046.8669315 (47)	total: 265ms	remaining: 55s
    48:	learn: 229751.8227403	test: 235453.8684227	best: 235453.8684227 (48)	total: 271ms	remaining: 55.1s
    49:	learn: 228068.0877261	test: 233921.4842261	best: 233921.4842261 (49)	total: 277ms	remaining: 55.2s
    50:	learn: 226362.3434256	test: 232293.8138951	best: 232293.8138951 (50)	total: 283ms	remaining: 55.1s
    51:	learn: 224782.9964986	test: 230894.0905504	best: 230894.0905504 (51)	total: 288ms	remaining: 55.1s
    52:	learn: 223043.6381383	test: 229253.8529537	best: 229253.8529537 (52)	total: 294ms	remaining: 55.2s
    53:	learn: 221343.5692117	test: 227673.7051081	best: 227673.7051081 (53)	total: 300ms	remaining: 55.2s
    54:	learn: 219907.0653007	test: 226334.5119380	best: 226334.5119380 (54)	total: 305ms	remaining: 55.2s
    55:	learn: 218340.2194249	test: 224834.1184814	best: 224834.1184814 (55)	total: 311ms	remaining: 55.2s
    56:	learn: 216968.0940686	test: 223622.3539075	best: 223622.3539075 (56)	total: 316ms	remaining: 55.1s
    57:	learn: 215394.3169067	test: 222115.6663152	best: 222115.6663152 (57)	total: 321ms	remaining: 55s
    58:	learn: 213910.2832056	test: 220878.1911047	best: 220878.1911047 (58)	total: 326ms	remaining: 54.9s
    59:	learn: 212426.6755659	test: 219561.4373983	best: 219561.4373983 (59)	total: 331ms	remaining: 54.8s
    60:	learn: 210894.7026326	test: 218284.7396981	best: 218284.7396981 (60)	total: 336ms	remaining: 54.7s
    61:	learn: 209436.9309646	test: 216990.1246248	best: 216990.1246248 (61)	total: 341ms	remaining: 54.7s
    62:	learn: 208064.6764734	test: 215668.3688748	best: 215668.3688748 (62)	total: 347ms	remaining: 54.7s
    63:	learn: 206834.0093416	test: 214468.3807189	best: 214468.3807189 (63)	total: 353ms	remaining: 54.8s
    64:	learn: 205578.1921415	test: 213405.9557289	best: 213405.9557289 (64)	total: 360ms	remaining: 55.1s
    65:	learn: 204248.9512308	test: 212198.6130475	best: 212198.6130475 (65)	total: 367ms	remaining: 55.2s
    66:	learn: 202815.5063282	test: 210929.6288462	best: 210929.6288462 (66)	total: 373ms	remaining: 55.3s
    67:	learn: 201423.9955184	test: 209547.7509040	best: 209547.7509040 (67)	total: 379ms	remaining: 55.4s
    68:	learn: 200205.6240046	test: 208511.5028761	best: 208511.5028761 (68)	total: 385ms	remaining: 55.5s
    69:	learn: 199017.9791946	test: 207506.9526378	best: 207506.9526378 (69)	total: 391ms	remaining: 55.5s
    70:	learn: 197882.6573525	test: 206439.4511604	best: 206439.4511604 (70)	total: 397ms	remaining: 55.6s
    71:	learn: 196750.5523455	test: 205369.3752288	best: 205369.3752288 (71)	total: 403ms	remaining: 55.5s
    72:	learn: 195610.7014432	test: 204291.9967694	best: 204291.9967694 (72)	total: 408ms	remaining: 55.5s
    73:	learn: 194549.0072472	test: 203343.8833012	best: 203343.8833012 (73)	total: 414ms	remaining: 55.6s
    74:	learn: 193496.2988065	test: 202367.1697229	best: 202367.1697229 (74)	total: 421ms	remaining: 55.7s
    75:	learn: 192510.3692765	test: 201466.5911566	best: 201466.5911566 (75)	total: 427ms	remaining: 55.8s
    76:	learn: 191481.0587877	test: 200495.9877970	best: 200495.9877970 (76)	total: 433ms	remaining: 55.8s
    77:	learn: 190315.3903514	test: 199406.7571688	best: 199406.7571688 (77)	total: 438ms	remaining: 55.7s
    78:	learn: 189401.2967877	test: 198616.9859899	best: 198616.9859899 (78)	total: 443ms	remaining: 55.6s
    79:	learn: 188259.8129025	test: 197513.3481673	best: 197513.3481673 (79)	total: 448ms	remaining: 55.6s
    80:	learn: 187313.0189830	test: 196667.3495981	best: 196667.3495981 (80)	total: 453ms	remaining: 55.5s
    81:	learn: 186229.1412510	test: 195664.8539251	best: 195664.8539251 (81)	total: 458ms	remaining: 55.4s
    82:	learn: 185308.0785396	test: 194757.8769622	best: 194757.8769622 (82)	total: 463ms	remaining: 55.4s
    83:	learn: 184299.9259957	test: 193767.7631753	best: 193767.7631753 (83)	total: 468ms	remaining: 55.3s
    84:	learn: 183403.3104756	test: 192939.7746327	best: 192939.7746327 (84)	total: 473ms	remaining: 55.2s
    85:	learn: 182442.3748732	test: 192050.4855036	best: 192050.4855036 (85)	total: 479ms	remaining: 55.2s
    86:	learn: 181596.2881873	test: 191217.5083430	best: 191217.5083430 (86)	total: 484ms	remaining: 55.2s
    87:	learn: 180599.4579009	test: 190283.3034754	best: 190283.3034754 (87)	total: 489ms	remaining: 55.1s
    88:	learn: 179693.2235232	test: 189474.6427244	best: 189474.6427244 (88)	total: 494ms	remaining: 55s
    89:	learn: 178816.5932008	test: 188753.5110538	best: 188753.5110538 (89)	total: 499ms	remaining: 55s
    90:	learn: 177925.8827903	test: 187964.6162677	best: 187964.6162677 (90)	total: 504ms	remaining: 54.9s
    91:	learn: 177094.3990545	test: 187266.7881466	best: 187266.7881466 (91)	total: 510ms	remaining: 54.9s
    92:	learn: 176290.6427532	test: 186529.8895467	best: 186529.8895467 (92)	total: 515ms	remaining: 54.9s
    93:	learn: 175606.1086561	test: 185944.1434675	best: 185944.1434675 (93)	total: 521ms	remaining: 54.9s
    94:	learn: 174856.9875395	test: 185284.3553053	best: 185284.3553053 (94)	total: 527ms	remaining: 55s
    95:	learn: 173904.2278361	test: 184385.2671657	best: 184385.2671657 (95)	total: 534ms	remaining: 55.1s
    96:	learn: 173229.2826609	test: 183777.1042651	best: 183777.1042651 (96)	total: 541ms	remaining: 55.2s
    97:	learn: 172560.2675108	test: 183166.1515644	best: 183166.1515644 (97)	total: 547ms	remaining: 55.3s
    98:	learn: 171799.4183790	test: 182466.7167887	best: 182466.7167887 (98)	total: 553ms	remaining: 55.3s
    99:	learn: 171008.8674598	test: 181747.2563673	best: 181747.2563673 (99)	total: 559ms	remaining: 55.3s
    100:	learn: 170272.4167394	test: 181126.4080481	best: 181126.4080481 (100)	total: 565ms	remaining: 55.3s
    101:	learn: 169573.9629548	test: 180492.1122165	best: 180492.1122165 (101)	total: 571ms	remaining: 55.4s
    102:	learn: 168799.1153387	test: 179779.1543653	best: 179779.1543653 (102)	total: 577ms	remaining: 55.4s
    103:	learn: 167989.3326019	test: 178989.3136095	best: 178989.3136095 (103)	total: 582ms	remaining: 55.4s
    104:	learn: 167388.7274113	test: 178373.4865286	best: 178373.4865286 (104)	total: 588ms	remaining: 55.4s
    105:	learn: 166601.8704607	test: 177685.4366986	best: 177685.4366986 (105)	total: 593ms	remaining: 55.4s
    106:	learn: 165956.8694182	test: 177106.5430785	best: 177106.5430785 (106)	total: 599ms	remaining: 55.4s
    107:	learn: 165096.3892798	test: 176272.2481216	best: 176272.2481216 (107)	total: 605ms	remaining: 55.5s
    108:	learn: 164419.8037020	test: 175628.6179379	best: 175628.6179379 (108)	total: 611ms	remaining: 55.4s
    109:	learn: 163886.1338201	test: 175176.2484641	best: 175176.2484641 (109)	total: 616ms	remaining: 55.4s
    110:	learn: 163175.4840874	test: 174538.0986711	best: 174538.0986711 (110)	total: 621ms	remaining: 55.3s
    111:	learn: 162656.6601862	test: 174170.0254563	best: 174170.0254563 (111)	total: 626ms	remaining: 55.2s
    112:	learn: 162056.8885544	test: 173570.1714902	best: 173570.1714902 (112)	total: 631ms	remaining: 55.2s
    113:	learn: 161476.6323216	test: 173048.6010362	best: 173048.6010362 (113)	total: 636ms	remaining: 55.1s
    114:	learn: 160891.7995770	test: 172541.8996213	best: 172541.8996213 (114)	total: 641ms	remaining: 55.1s
    115:	learn: 160389.7610386	test: 172079.5831862	best: 172079.5831862 (115)	total: 646ms	remaining: 55s
    116:	learn: 159893.1108361	test: 171578.1552295	best: 171578.1552295 (116)	total: 651ms	remaining: 55s
    117:	learn: 159360.7640229	test: 171053.2117459	best: 171053.2117459 (117)	total: 656ms	remaining: 55s
    118:	learn: 158831.8822310	test: 170590.0703361	best: 170590.0703361 (118)	total: 661ms	remaining: 54.9s
    119:	learn: 158137.8509211	test: 169992.0227112	best: 169992.0227112 (119)	total: 666ms	remaining: 54.8s
    120:	learn: 157514.9866399	test: 169433.3810834	best: 169433.3810834 (120)	total: 671ms	remaining: 54.8s
    121:	learn: 156966.3169904	test: 168929.6799585	best: 168929.6799585 (121)	total: 676ms	remaining: 54.7s
    122:	learn: 156479.5502646	test: 168423.6996983	best: 168423.6996983 (122)	total: 681ms	remaining: 54.7s
    123:	learn: 155834.8013109	test: 167797.4242632	best: 167797.4242632 (123)	total: 687ms	remaining: 54.7s
    124:	learn: 155321.5464657	test: 167339.6686961	best: 167339.6686961 (124)	total: 692ms	remaining: 54.7s
    125:	learn: 154726.3445353	test: 166787.6726009	best: 166787.6726009 (125)	total: 698ms	remaining: 54.7s
    126:	learn: 154347.4628232	test: 166464.5265018	best: 166464.5265018 (126)	total: 705ms	remaining: 54.8s
    127:	learn: 153866.8983772	test: 165944.2799942	best: 165944.2799942 (127)	total: 712ms	remaining: 54.9s
    128:	learn: 153366.8469448	test: 165424.8935141	best: 165424.8935141 (128)	total: 718ms	remaining: 55s
    129:	learn: 152969.6731599	test: 165025.0490327	best: 165025.0490327 (129)	total: 724ms	remaining: 55s
    130:	learn: 152596.3812837	test: 164731.3573580	best: 164731.3573580 (130)	total: 730ms	remaining: 55s
    131:	learn: 152172.0025542	test: 164313.2719668	best: 164313.2719668 (131)	total: 736ms	remaining: 55s
    132:	learn: 151799.9190165	test: 163943.3547155	best: 163943.3547155 (132)	total: 741ms	remaining: 55s
    133:	learn: 151371.5625376	test: 163531.8877014	best: 163531.8877014 (133)	total: 746ms	remaining: 54.9s
    134:	learn: 150980.2951459	test: 163181.5339182	best: 163181.5339182 (134)	total: 751ms	remaining: 54.9s
    135:	learn: 150609.1879027	test: 162741.9119877	best: 162741.9119877 (135)	total: 756ms	remaining: 54.8s
    136:	learn: 150249.8690672	test: 162397.2579941	best: 162397.2579941 (136)	total: 761ms	remaining: 54.8s
    137:	learn: 149821.4870651	test: 161980.3713157	best: 161980.3713157 (137)	total: 766ms	remaining: 54.8s
    138:	learn: 149411.3973808	test: 161597.7365451	best: 161597.7365451 (138)	total: 771ms	remaining: 54.7s
    139:	learn: 148934.8038483	test: 161173.4388433	best: 161173.4388433 (139)	total: 776ms	remaining: 54.7s
    140:	learn: 148402.7969715	test: 160657.5654262	best: 160657.5654262 (140)	total: 781ms	remaining: 54.6s
    141:	learn: 148113.2637386	test: 160376.9718356	best: 160376.9718356 (141)	total: 786ms	remaining: 54.6s
    142:	learn: 147778.6421252	test: 160038.7177208	best: 160038.7177208 (142)	total: 791ms	remaining: 54.5s
    143:	learn: 147436.3701848	test: 159740.1239900	best: 159740.1239900 (143)	total: 796ms	remaining: 54.5s
    144:	learn: 147018.9802914	test: 159352.7453768	best: 159352.7453768 (144)	total: 801ms	remaining: 54.5s
    145:	learn: 146695.5435272	test: 159069.8698294	best: 159069.8698294 (145)	total: 806ms	remaining: 54.4s
    146:	learn: 146419.4088846	test: 158829.8644203	best: 158829.8644203 (146)	total: 811ms	remaining: 54.3s
    147:	learn: 146081.0046700	test: 158537.0129341	best: 158537.0129341 (147)	total: 816ms	remaining: 54.3s
    148:	learn: 145786.7147603	test: 158255.6067843	best: 158255.6067843 (148)	total: 821ms	remaining: 54.3s
    149:	learn: 145443.5255921	test: 157959.8434673	best: 157959.8434673 (149)	total: 826ms	remaining: 54.2s
    150:	learn: 145025.1916256	test: 157575.8709940	best: 157575.8709940 (150)	total: 831ms	remaining: 54.2s
    151:	learn: 144598.9149349	test: 157192.0927923	best: 157192.0927923 (151)	total: 835ms	remaining: 54.1s
    152:	learn: 144153.6035834	test: 156825.8301794	best: 156825.8301794 (152)	total: 840ms	remaining: 54.1s
    153:	learn: 143873.4066403	test: 156569.7091036	best: 156569.7091036 (153)	total: 845ms	remaining: 54s
    154:	learn: 143369.2812264	test: 156149.0235831	best: 156149.0235831 (154)	total: 850ms	remaining: 54s
    155:	learn: 143070.7550112	test: 155898.6400147	best: 155898.6400147 (155)	total: 855ms	remaining: 53.9s
    156:	learn: 142624.9663877	test: 155441.3367796	best: 155441.3367796 (156)	total: 860ms	remaining: 53.9s
    157:	learn: 142338.1713204	test: 155168.5017415	best: 155168.5017415 (157)	total: 867ms	remaining: 54s
    158:	learn: 142022.6179839	test: 154886.2018768	best: 154886.2018768 (158)	total: 873ms	remaining: 54s
    159:	learn: 141786.0016553	test: 154685.2255809	best: 154685.2255809 (159)	total: 879ms	remaining: 54.1s
    160:	learn: 141432.8416707	test: 154343.6204905	best: 154343.6204905 (160)	total: 884ms	remaining: 54s
    161:	learn: 141155.5446081	test: 154117.5476836	best: 154117.5476836 (161)	total: 889ms	remaining: 54s
    162:	learn: 140831.9673611	test: 153831.8801223	best: 153831.8801223 (162)	total: 895ms	remaining: 54s
    163:	learn: 140619.3999696	test: 153676.7866786	best: 153676.7866786 (163)	total: 900ms	remaining: 53.9s
    164:	learn: 140357.2036084	test: 153485.7525211	best: 153485.7525211 (164)	total: 905ms	remaining: 54s
    165:	learn: 140118.2865083	test: 153338.5835450	best: 153338.5835450 (165)	total: 912ms	remaining: 54s
    166:	learn: 139885.6390045	test: 153206.2933623	best: 153206.2933623 (166)	total: 918ms	remaining: 54s
    167:	learn: 139658.7347303	test: 153032.0021116	best: 153032.0021116 (167)	total: 924ms	remaining: 54s
    168:	learn: 139225.4231277	test: 152635.2475100	best: 152635.2475100 (168)	total: 930ms	remaining: 54.1s
    169:	learn: 138989.2748522	test: 152412.8929967	best: 152412.8929967 (169)	total: 936ms	remaining: 54.1s
    170:	learn: 138785.4120674	test: 152258.0373190	best: 152258.0373190 (170)	total: 942ms	remaining: 54.1s
    171:	learn: 138573.7791769	test: 152091.3611617	best: 152091.3611617 (171)	total: 948ms	remaining: 54.1s
    172:	learn: 138354.2053601	test: 151875.0361097	best: 151875.0361097 (172)	total: 953ms	remaining: 54.2s
    173:	learn: 138146.4983085	test: 151599.2863777	best: 151599.2863777 (173)	total: 959ms	remaining: 54.2s
    174:	learn: 137894.1781317	test: 151451.1824575	best: 151451.1824575 (174)	total: 965ms	remaining: 54.2s
    175:	learn: 137610.0567174	test: 151212.4858874	best: 151212.4858874 (175)	total: 972ms	remaining: 54.3s
    176:	learn: 137246.7070884	test: 150889.0195193	best: 150889.0195193 (176)	total: 978ms	remaining: 54.3s
    177:	learn: 137041.8053199	test: 150755.5878721	best: 150755.5878721 (177)	total: 983ms	remaining: 54.3s
    178:	learn: 136830.9070685	test: 150532.8409479	best: 150532.8409479 (178)	total: 989ms	remaining: 54.3s
    179:	learn: 136632.5822008	test: 150296.2980830	best: 150296.2980830 (179)	total: 995ms	remaining: 54.3s
    180:	learn: 136212.1422567	test: 149874.3683149	best: 149874.3683149 (180)	total: 1s	remaining: 54.3s
    181:	learn: 135880.3971942	test: 149583.6671402	best: 149583.6671402 (181)	total: 1.01s	remaining: 54.3s
    182:	learn: 135484.8215959	test: 149267.3418969	best: 149267.3418969 (182)	total: 1.01s	remaining: 54.3s
    183:	learn: 135296.8793038	test: 149127.7802793	best: 149127.7802793 (183)	total: 1.02s	remaining: 54.2s
    184:	learn: 135133.8131525	test: 149033.5720112	best: 149033.5720112 (184)	total: 1.02s	remaining: 54.2s
    185:	learn: 134831.8469708	test: 148702.3414619	best: 148702.3414619 (185)	total: 1.03s	remaining: 54.2s
    186:	learn: 134661.5638355	test: 148570.0171723	best: 148570.0171723 (186)	total: 1.03s	remaining: 54.2s
    187:	learn: 134436.7436989	test: 148438.8256224	best: 148438.8256224 (187)	total: 1.04s	remaining: 54.2s
    188:	learn: 134190.4608563	test: 148218.0631606	best: 148218.0631606 (188)	total: 1.04s	remaining: 54.3s
    189:	learn: 133880.9571911	test: 147952.2997887	best: 147952.2997887 (189)	total: 1.05s	remaining: 54.3s
    190:	learn: 133595.6329973	test: 147696.9617675	best: 147696.9617675 (190)	total: 1.06s	remaining: 54.3s
    191:	learn: 133436.5178851	test: 147607.3022196	best: 147607.3022196 (191)	total: 1.06s	remaining: 54.2s
    192:	learn: 133246.5857620	test: 147416.4653032	best: 147416.4653032 (192)	total: 1.07s	remaining: 54.2s
    193:	learn: 133060.4788497	test: 147271.4566393	best: 147271.4566393 (193)	total: 1.07s	remaining: 54.2s
    194:	learn: 132897.8392577	test: 147107.3591454	best: 147107.3591454 (194)	total: 1.08s	remaining: 54.2s
    195:	learn: 132711.5105408	test: 146975.6141338	best: 146975.6141338 (195)	total: 1.08s	remaining: 54.2s
    196:	learn: 132550.4401034	test: 146860.8219923	best: 146860.8219923 (196)	total: 1.09s	remaining: 54.2s
    197:	learn: 132370.7459339	test: 146689.1960475	best: 146689.1960475 (197)	total: 1.09s	remaining: 54.2s
    198:	learn: 132222.0404658	test: 146542.8603053	best: 146542.8603053 (198)	total: 1.1s	remaining: 54.2s
    199:	learn: 132079.4925526	test: 146438.5085701	best: 146438.5085701 (199)	total: 1.11s	remaining: 54.2s
    200:	learn: 131829.6627493	test: 146219.9732849	best: 146219.9732849 (200)	total: 1.11s	remaining: 54.2s
    201:	learn: 131647.6648042	test: 146068.1877803	best: 146068.1877803 (201)	total: 1.12s	remaining: 54.2s
    202:	learn: 131493.8617432	test: 145905.1192202	best: 145905.1192202 (202)	total: 1.12s	remaining: 54.2s
    203:	learn: 131361.1571988	test: 145731.7302366	best: 145731.7302366 (203)	total: 1.13s	remaining: 54.2s
    204:	learn: 131216.1787577	test: 145572.9300938	best: 145572.9300938 (204)	total: 1.13s	remaining: 54.2s
    205:	learn: 131041.4414450	test: 145400.9094326	best: 145400.9094326 (205)	total: 1.14s	remaining: 54.2s
    206:	learn: 130910.7630675	test: 145323.1306288	best: 145323.1306288 (206)	total: 1.15s	remaining: 54.2s
    207:	learn: 130737.9288526	test: 145183.6907457	best: 145183.6907457 (207)	total: 1.15s	remaining: 54.2s
    208:	learn: 130605.6060224	test: 145088.6638857	best: 145088.6638857 (208)	total: 1.16s	remaining: 54.2s
    209:	learn: 130377.1285758	test: 144916.4566636	best: 144916.4566636 (209)	total: 1.16s	remaining: 54.2s
    210:	learn: 130270.9292117	test: 144798.8745058	best: 144798.8745058 (210)	total: 1.17s	remaining: 54.2s
    211:	learn: 130142.5121093	test: 144732.8225142	best: 144732.8225142 (211)	total: 1.17s	remaining: 54.1s
    212:	learn: 130028.6461125	test: 144647.0555660	best: 144647.0555660 (212)	total: 1.18s	remaining: 54.1s
    213:	learn: 129873.5928215	test: 144570.6777518	best: 144570.6777518 (213)	total: 1.18s	remaining: 54.1s
    214:	learn: 129755.0976255	test: 144472.2875826	best: 144472.2875826 (214)	total: 1.19s	remaining: 54s
    215:	learn: 129624.9742563	test: 144400.1859349	best: 144400.1859349 (215)	total: 1.19s	remaining: 54s
    216:	learn: 129497.7445396	test: 144278.4628966	best: 144278.4628966 (216)	total: 1.2s	remaining: 54s
    217:	learn: 129307.1002276	test: 144138.0313823	best: 144138.0313823 (217)	total: 1.2s	remaining: 54.1s
    218:	learn: 129023.8250414	test: 143913.1404004	best: 143913.1404004 (218)	total: 1.21s	remaining: 54.1s
    219:	learn: 128905.8529527	test: 143835.6136904	best: 143835.6136904 (219)	total: 1.22s	remaining: 54.2s
    220:	learn: 128804.1658221	test: 143820.6470974	best: 143820.6470974 (220)	total: 1.22s	remaining: 54.2s
    221:	learn: 128678.0962572	test: 143680.1898185	best: 143680.1898185 (221)	total: 1.23s	remaining: 54.2s
    222:	learn: 128566.6458654	test: 143629.0940731	best: 143629.0940731 (222)	total: 1.24s	remaining: 54.2s
    223:	learn: 128474.6038523	test: 143562.7839249	best: 143562.7839249 (223)	total: 1.24s	remaining: 54.2s
    224:	learn: 128339.8563561	test: 143448.0487440	best: 143448.0487440 (224)	total: 1.25s	remaining: 54.2s
    225:	learn: 128105.0092818	test: 143238.0736467	best: 143238.0736467 (225)	total: 1.25s	remaining: 54.3s
    226:	learn: 127980.1626441	test: 143135.8972404	best: 143135.8972404 (226)	total: 1.26s	remaining: 54.3s
    227:	learn: 127873.2552611	test: 143065.2549273	best: 143065.2549273 (227)	total: 1.27s	remaining: 54.3s
    228:	learn: 127763.0711477	test: 142964.7513080	best: 142964.7513080 (228)	total: 1.27s	remaining: 54.3s
    229:	learn: 127679.6072733	test: 142872.4666081	best: 142872.4666081 (229)	total: 1.28s	remaining: 54.2s
    230:	learn: 127573.9033018	test: 142805.5981264	best: 142805.5981264 (230)	total: 1.28s	remaining: 54.2s
    231:	learn: 127462.4758158	test: 142680.9893029	best: 142680.9893029 (231)	total: 1.29s	remaining: 54.2s
    232:	learn: 127352.8878909	test: 142579.7902826	best: 142579.7902826 (232)	total: 1.29s	remaining: 54.2s
    233:	learn: 127252.9336100	test: 142504.4611895	best: 142504.4611895 (233)	total: 1.3s	remaining: 54.2s
    234:	learn: 127153.9100590	test: 142442.8453663	best: 142442.8453663 (234)	total: 1.3s	remaining: 54.2s
    235:	learn: 127058.7200268	test: 142338.7738560	best: 142338.7738560 (235)	total: 1.31s	remaining: 54.2s
    236:	learn: 126940.7664798	test: 142219.9661220	best: 142219.9661220 (236)	total: 1.31s	remaining: 54.2s
    237:	learn: 126850.9878384	test: 142086.0672251	best: 142086.0672251 (237)	total: 1.32s	remaining: 54.1s
    238:	learn: 126686.1703712	test: 141934.4682196	best: 141934.4682196 (238)	total: 1.32s	remaining: 54.1s
    239:	learn: 126600.4755076	test: 141880.1387914	best: 141880.1387914 (239)	total: 1.33s	remaining: 54.2s
    240:	learn: 126434.1627039	test: 141708.1508339	best: 141708.1508339 (240)	total: 1.34s	remaining: 54.2s
    241:	learn: 126318.6706200	test: 141589.7059189	best: 141589.7059189 (241)	total: 1.34s	remaining: 54.2s
    242:	learn: 126214.6035834	test: 141464.1998812	best: 141464.1998812 (242)	total: 1.35s	remaining: 54.2s
    243:	learn: 126112.4363879	test: 141354.4942535	best: 141354.4942535 (243)	total: 1.35s	remaining: 54.2s
    244:	learn: 125875.5138186	test: 141164.6531702	best: 141164.6531702 (244)	total: 1.36s	remaining: 54.2s
    245:	learn: 125789.3030549	test: 141080.1343886	best: 141080.1343886 (245)	total: 1.37s	remaining: 54.2s
    246:	learn: 125701.7165914	test: 140980.7352730	best: 140980.7352730 (246)	total: 1.37s	remaining: 54.2s
    247:	learn: 125603.9457545	test: 140881.2824047	best: 140881.2824047 (247)	total: 1.38s	remaining: 54.2s
    248:	learn: 125484.5873911	test: 140758.2980735	best: 140758.2980735 (248)	total: 1.39s	remaining: 54.3s
    249:	learn: 125308.9913813	test: 140615.4269529	best: 140615.4269529 (249)	total: 1.39s	remaining: 54.3s
    250:	learn: 125186.9752086	test: 140507.0209980	best: 140507.0209980 (250)	total: 1.4s	remaining: 54.3s
    251:	learn: 125076.4826362	test: 140423.2139553	best: 140423.2139553 (251)	total: 1.4s	remaining: 54.2s
    252:	learn: 124979.7707806	test: 140327.6171112	best: 140327.6171112 (252)	total: 1.41s	remaining: 54.2s
    253:	learn: 124865.6125064	test: 140193.8687815	best: 140193.8687815 (253)	total: 1.41s	remaining: 54.2s
    254:	learn: 124769.0626015	test: 140091.5826863	best: 140091.5826863 (254)	total: 1.42s	remaining: 54.2s
    255:	learn: 124670.6849159	test: 139997.6076494	best: 139997.6076494 (255)	total: 1.42s	remaining: 54.1s
    256:	learn: 124599.6812099	test: 139970.8179840	best: 139970.8179840 (256)	total: 1.43s	remaining: 54.1s
    257:	learn: 124475.2388571	test: 139847.3633319	best: 139847.3633319 (257)	total: 1.43s	remaining: 54.1s
    258:	learn: 124382.7456257	test: 139773.6687365	best: 139773.6687365 (258)	total: 1.44s	remaining: 54s
    259:	learn: 124301.6279885	test: 139680.3110640	best: 139680.3110640 (259)	total: 1.44s	remaining: 54s
    260:	learn: 124200.3014227	test: 139559.2909500	best: 139559.2909500 (260)	total: 1.45s	remaining: 54s
    261:	learn: 124101.1895442	test: 139487.2753926	best: 139487.2753926 (261)	total: 1.45s	remaining: 53.9s
    262:	learn: 124000.0151477	test: 139465.8795651	best: 139465.8795651 (262)	total: 1.46s	remaining: 53.9s
    263:	learn: 123917.1187492	test: 139378.0864934	best: 139378.0864934 (263)	total: 1.46s	remaining: 53.9s
    264:	learn: 123833.8356720	test: 139317.2988485	best: 139317.2988485 (264)	total: 1.47s	remaining: 53.9s
    265:	learn: 123752.8277240	test: 139224.8563323	best: 139224.8563323 (265)	total: 1.47s	remaining: 53.9s
    266:	learn: 123652.8044821	test: 139195.8207378	best: 139195.8207378 (266)	total: 1.48s	remaining: 53.8s
    267:	learn: 123583.8802641	test: 139161.8672666	best: 139161.8672666 (267)	total: 1.48s	remaining: 53.8s
    268:	learn: 123480.0114526	test: 139107.8090792	best: 139107.8090792 (268)	total: 1.49s	remaining: 53.8s
    269:	learn: 123400.5879419	test: 139035.3977308	best: 139035.3977308 (269)	total: 1.49s	remaining: 53.8s
    270:	learn: 123250.5347060	test: 138917.7256106	best: 138917.7256106 (270)	total: 1.5s	remaining: 53.8s
    271:	learn: 123170.9536689	test: 138891.4376360	best: 138891.4376360 (271)	total: 1.5s	remaining: 53.7s
    272:	learn: 123077.2147487	test: 138847.8262480	best: 138847.8262480 (272)	total: 1.51s	remaining: 53.7s
    273:	learn: 122945.9114193	test: 138715.8261398	best: 138715.8261398 (273)	total: 1.51s	remaining: 53.7s
    274:	learn: 122868.8544617	test: 138686.5736042	best: 138686.5736042 (274)	total: 1.52s	remaining: 53.7s
    275:	learn: 122764.4432007	test: 138584.1506064	best: 138584.1506064 (275)	total: 1.52s	remaining: 53.7s
    276:	learn: 122650.3369090	test: 138514.0961487	best: 138514.0961487 (276)	total: 1.53s	remaining: 53.7s
    277:	learn: 122588.5702167	test: 138452.6863664	best: 138452.6863664 (277)	total: 1.53s	remaining: 53.7s
    278:	learn: 122522.9900252	test: 138432.5099262	best: 138432.5099262 (278)	total: 1.54s	remaining: 53.7s
    279:	learn: 122413.9789229	test: 138345.7461724	best: 138345.7461724 (279)	total: 1.54s	remaining: 53.6s
    280:	learn: 122337.1033958	test: 138273.1649804	best: 138273.1649804 (280)	total: 1.55s	remaining: 53.6s
    281:	learn: 122141.3502427	test: 138109.5448142	best: 138109.5448142 (281)	total: 1.56s	remaining: 53.7s
    282:	learn: 122034.9726596	test: 138017.7506010	best: 138017.7506010 (282)	total: 1.56s	remaining: 53.7s
    283:	learn: 121977.7311622	test: 138006.1911632	best: 138006.1911632 (283)	total: 1.57s	remaining: 53.7s
    284:	learn: 121923.6083089	test: 137924.9622765	best: 137924.9622765 (284)	total: 1.57s	remaining: 53.7s
    285:	learn: 121847.8818963	test: 137867.2295467	best: 137867.2295467 (285)	total: 1.58s	remaining: 53.7s
    286:	learn: 121732.7193343	test: 137757.1767334	best: 137757.1767334 (286)	total: 1.58s	remaining: 53.7s
    287:	learn: 121644.7557121	test: 137641.3923791	best: 137641.3923791 (287)	total: 1.59s	remaining: 53.6s
    288:	learn: 121514.2570768	test: 137491.2274579	best: 137491.2274579 (288)	total: 1.59s	remaining: 53.6s
    289:	learn: 121441.3496721	test: 137463.1843960	best: 137463.1843960 (289)	total: 1.6s	remaining: 53.6s
    290:	learn: 121377.6378159	test: 137413.7882809	best: 137413.7882809 (290)	total: 1.6s	remaining: 53.6s
    291:	learn: 121315.3328356	test: 137337.0336013	best: 137337.0336013 (291)	total: 1.61s	remaining: 53.6s
    292:	learn: 121203.5153844	test: 137256.7837929	best: 137256.7837929 (292)	total: 1.61s	remaining: 53.5s
    293:	learn: 121122.0886487	test: 137220.9553494	best: 137220.9553494 (293)	total: 1.62s	remaining: 53.5s
    294:	learn: 121062.8770682	test: 137173.2533240	best: 137173.2533240 (294)	total: 1.63s	remaining: 53.5s
    295:	learn: 120990.8163664	test: 137103.1575795	best: 137103.1575795 (295)	total: 1.63s	remaining: 53.5s
    296:	learn: 120863.3182621	test: 136993.8844684	best: 136993.8844684 (296)	total: 1.64s	remaining: 53.5s
    297:	learn: 120796.6311104	test: 136917.8501153	best: 136917.8501153 (297)	total: 1.64s	remaining: 53.4s
    298:	learn: 120714.8887441	test: 136869.7446886	best: 136869.7446886 (298)	total: 1.65s	remaining: 53.4s
    299:	learn: 120634.4995549	test: 136819.4942229	best: 136819.4942229 (299)	total: 1.65s	remaining: 53.4s
    300:	learn: 120459.8900374	test: 136666.1029291	best: 136666.1029291 (300)	total: 1.66s	remaining: 53.5s
    301:	learn: 120384.0945626	test: 136591.6541081	best: 136591.6541081 (301)	total: 1.66s	remaining: 53.5s
    302:	learn: 120348.2937498	test: 136575.0163241	best: 136575.0163241 (302)	total: 1.67s	remaining: 53.5s
    303:	learn: 120292.3246015	test: 136508.6081933	best: 136508.6081933 (303)	total: 1.68s	remaining: 53.5s
    304:	learn: 120220.1875360	test: 136445.0190929	best: 136445.0190929 (304)	total: 1.68s	remaining: 53.5s
    305:	learn: 120161.2103076	test: 136399.0394424	best: 136399.0394424 (305)	total: 1.69s	remaining: 53.5s
    306:	learn: 120062.7292050	test: 136358.4184913	best: 136358.4184913 (306)	total: 1.69s	remaining: 53.5s
    307:	learn: 119983.6081824	test: 136250.0361180	best: 136250.0361180 (307)	total: 1.7s	remaining: 53.5s
    308:	learn: 119898.6920237	test: 136188.9881860	best: 136188.9881860 (308)	total: 1.7s	remaining: 53.5s
    309:	learn: 119766.7553135	test: 136069.8114114	best: 136069.8114114 (309)	total: 1.71s	remaining: 53.5s
    310:	learn: 119708.0296263	test: 135987.1578289	best: 135987.1578289 (310)	total: 1.72s	remaining: 53.4s
    311:	learn: 119665.3917229	test: 135959.1644309	best: 135959.1644309 (311)	total: 1.72s	remaining: 53.4s
    312:	learn: 119573.0004404	test: 135888.3518010	best: 135888.3518010 (312)	total: 1.73s	remaining: 53.4s
    313:	learn: 119388.8969094	test: 135709.4136503	best: 135709.4136503 (313)	total: 1.73s	remaining: 53.5s
    314:	learn: 119322.6668332	test: 135669.7964554	best: 135669.7964554 (314)	total: 1.74s	remaining: 53.5s
    315:	learn: 119251.5081177	test: 135591.7709763	best: 135591.7709763 (315)	total: 1.74s	remaining: 53.4s
    316:	learn: 119144.6166920	test: 135502.6346986	best: 135502.6346986 (316)	total: 1.75s	remaining: 53.4s
    317:	learn: 118994.6746922	test: 135399.8971055	best: 135399.8971055 (317)	total: 1.75s	remaining: 53.4s
    318:	learn: 118916.4405745	test: 135361.1130490	best: 135361.1130490 (318)	total: 1.76s	remaining: 53.4s
    319:	learn: 118851.3853458	test: 135299.7694038	best: 135299.7694038 (319)	total: 1.76s	remaining: 53.4s
    320:	learn: 118789.4579728	test: 135226.0866525	best: 135226.0866525 (320)	total: 1.77s	remaining: 53.4s
    321:	learn: 118720.0294731	test: 135172.5085152	best: 135172.5085152 (321)	total: 1.77s	remaining: 53.4s
    322:	learn: 118655.2727739	test: 135156.1046547	best: 135156.1046547 (322)	total: 1.78s	remaining: 53.3s
    323:	learn: 118588.4242638	test: 135102.1664347	best: 135102.1664347 (323)	total: 1.78s	remaining: 53.3s
    324:	learn: 118488.7306404	test: 135026.2229026	best: 135026.2229026 (324)	total: 1.79s	remaining: 53.3s
    325:	learn: 118412.3672970	test: 134940.3567959	best: 134940.3567959 (325)	total: 1.79s	remaining: 53.3s
    326:	learn: 118319.4823147	test: 134901.7901508	best: 134901.7901508 (326)	total: 1.8s	remaining: 53.3s
    327:	learn: 118262.6787779	test: 134850.8561448	best: 134850.8561448 (327)	total: 1.81s	remaining: 53.3s
    328:	learn: 118174.1236760	test: 134781.8605564	best: 134781.8605564 (328)	total: 1.81s	remaining: 53.2s
    329:	learn: 118135.8583523	test: 134733.0770023	best: 134733.0770023 (329)	total: 1.82s	remaining: 53.2s
    330:	learn: 117999.4197306	test: 134606.2001172	best: 134606.2001172 (330)	total: 1.82s	remaining: 53.2s
    331:	learn: 117945.9703640	test: 134557.9330719	best: 134557.9330719 (331)	total: 1.83s	remaining: 53.2s
    332:	learn: 117877.0483169	test: 134530.4543787	best: 134530.4543787 (332)	total: 1.83s	remaining: 53.2s
    333:	learn: 117829.4591068	test: 134480.0082843	best: 134480.0082843 (333)	total: 1.84s	remaining: 53.1s
    334:	learn: 117790.2202027	test: 134459.1160498	best: 134459.1160498 (334)	total: 1.84s	remaining: 53.1s
    335:	learn: 117750.9545178	test: 134390.6444851	best: 134390.6444851 (335)	total: 1.85s	remaining: 53.1s
    336:	learn: 117698.4548979	test: 134366.8579386	best: 134366.8579386 (336)	total: 1.85s	remaining: 53.1s
    337:	learn: 117577.5343744	test: 134276.3809267	best: 134276.3809267 (337)	total: 1.86s	remaining: 53.1s
    338:	learn: 117524.2591867	test: 134214.1040903	best: 134214.1040903 (338)	total: 1.86s	remaining: 53.1s
    339:	learn: 117436.0272420	test: 134146.4070470	best: 134146.4070470 (339)	total: 1.87s	remaining: 53.1s
    340:	learn: 117371.0983611	test: 134129.5437838	best: 134129.5437838 (340)	total: 1.87s	remaining: 53.1s
    341:	learn: 117310.2410871	test: 134073.7495030	best: 134073.7495030 (341)	total: 1.88s	remaining: 53s
    342:	learn: 117260.2781380	test: 134016.5841310	best: 134016.5841310 (342)	total: 1.88s	remaining: 53s
    343:	learn: 117203.4076903	test: 133936.6193659	best: 133936.6193659 (343)	total: 1.89s	remaining: 53s
    344:	learn: 117157.7939586	test: 133893.8398165	best: 133893.8398165 (344)	total: 1.89s	remaining: 53s
    345:	learn: 117106.7620004	test: 133862.4184263	best: 133862.4184263 (345)	total: 1.9s	remaining: 53s
    346:	learn: 117000.7699724	test: 133777.3495334	best: 133777.3495334 (346)	total: 1.91s	remaining: 53s
    347:	learn: 116920.5376160	test: 133725.9020983	best: 133725.9020983 (347)	total: 1.91s	remaining: 53s
    348:	learn: 116820.0362774	test: 133652.9910623	best: 133652.9910623 (348)	total: 1.92s	remaining: 53s
    349:	learn: 116725.7299752	test: 133568.7446044	best: 133568.7446044 (349)	total: 1.92s	remaining: 53s
    350:	learn: 116676.6942781	test: 133497.9658269	best: 133497.9658269 (350)	total: 1.93s	remaining: 53s
    351:	learn: 116602.8806712	test: 133456.5091370	best: 133456.5091370 (351)	total: 1.93s	remaining: 53s
    352:	learn: 116539.1756584	test: 133392.1194702	best: 133392.1194702 (352)	total: 1.94s	remaining: 52.9s
    353:	learn: 116492.0746155	test: 133345.6997306	best: 133345.6997306 (353)	total: 1.94s	remaining: 52.9s
    354:	learn: 116432.1093020	test: 133310.7151423	best: 133310.7151423 (354)	total: 1.95s	remaining: 52.9s
    355:	learn: 116375.2820916	test: 133207.2862093	best: 133207.2862093 (355)	total: 1.95s	remaining: 52.9s
    356:	learn: 116316.1266913	test: 133155.4172317	best: 133155.4172317 (356)	total: 1.96s	remaining: 52.9s
    357:	learn: 116273.6709157	test: 133143.3840590	best: 133143.3840590 (357)	total: 1.96s	remaining: 52.8s
    358:	learn: 116198.5824762	test: 133075.8689298	best: 133075.8689298 (358)	total: 1.97s	remaining: 52.8s
    359:	learn: 116154.9514721	test: 133037.0345773	best: 133037.0345773 (359)	total: 1.97s	remaining: 52.8s
    360:	learn: 116093.9540382	test: 133000.3528494	best: 133000.3528494 (360)	total: 1.98s	remaining: 52.8s
    361:	learn: 116042.5154143	test: 132981.9433852	best: 132981.9433852 (361)	total: 1.98s	remaining: 52.8s
    362:	learn: 115982.3777106	test: 132925.6549271	best: 132925.6549271 (362)	total: 1.99s	remaining: 52.8s
    363:	learn: 115937.3359713	test: 132902.0947070	best: 132902.0947070 (363)	total: 2s	remaining: 52.8s
    364:	learn: 115900.4128023	test: 132874.3177986	best: 132874.3177986 (364)	total: 2s	remaining: 52.9s
    365:	learn: 115851.3878653	test: 132859.0954804	best: 132859.0954804 (365)	total: 2.01s	remaining: 52.9s
    366:	learn: 115797.5375249	test: 132773.6347223	best: 132773.6347223 (366)	total: 2.01s	remaining: 52.9s
    367:	learn: 115758.7812403	test: 132743.8528651	best: 132743.8528651 (367)	total: 2.02s	remaining: 52.9s
    368:	learn: 115682.3679376	test: 132682.1129759	best: 132682.1129759 (368)	total: 2.02s	remaining: 52.8s
    369:	learn: 115630.0691194	test: 132601.4788617	best: 132601.4788617 (369)	total: 2.03s	remaining: 52.8s
    370:	learn: 115478.4667807	test: 132492.0262507	best: 132492.0262507 (370)	total: 2.04s	remaining: 52.9s
    371:	learn: 115366.2501404	test: 132391.7109941	best: 132391.7109941 (371)	total: 2.04s	remaining: 52.9s
    372:	learn: 115324.4541522	test: 132355.3093775	best: 132355.3093775 (372)	total: 2.05s	remaining: 52.9s
    373:	learn: 115272.8714325	test: 132292.2208586	best: 132292.2208586 (373)	total: 2.06s	remaining: 52.9s
    374:	learn: 115237.3309327	test: 132221.3115577	best: 132221.3115577 (374)	total: 2.06s	remaining: 52.9s
    375:	learn: 115203.3207842	test: 132196.8327644	best: 132196.8327644 (375)	total: 2.07s	remaining: 52.9s
    376:	learn: 115119.5283342	test: 132119.6889337	best: 132119.6889337 (376)	total: 2.07s	remaining: 52.9s
    377:	learn: 115039.8729400	test: 132108.9070109	best: 132108.9070109 (377)	total: 2.08s	remaining: 53s
    378:	learn: 114957.3708062	test: 132066.9280323	best: 132066.9280323 (378)	total: 2.09s	remaining: 53s
    379:	learn: 114916.6125012	test: 132055.7698317	best: 132055.7698317 (379)	total: 2.1s	remaining: 53.1s
    380:	learn: 114870.4897329	test: 132004.3214928	best: 132004.3214928 (380)	total: 2.1s	remaining: 53.1s
    381:	learn: 114822.3989990	test: 131953.0911570	best: 131953.0911570 (381)	total: 2.11s	remaining: 53.1s
    382:	learn: 114769.7185772	test: 131913.1147349	best: 131913.1147349 (382)	total: 2.11s	remaining: 53.1s
    383:	learn: 114706.0366959	test: 131878.3077832	best: 131878.3077832 (383)	total: 2.12s	remaining: 53.1s
    384:	learn: 114644.6984136	test: 131850.4028645	best: 131850.4028645 (384)	total: 2.12s	remaining: 53.1s
    385:	learn: 114587.2764452	test: 131813.0324702	best: 131813.0324702 (385)	total: 2.13s	remaining: 53s
    386:	learn: 114547.8030337	test: 131769.9661696	best: 131769.9661696 (386)	total: 2.13s	remaining: 53s
    387:	learn: 114491.6431668	test: 131764.4238181	best: 131764.4238181 (387)	total: 2.14s	remaining: 53s
    388:	learn: 114429.1447859	test: 131732.0625217	best: 131732.0625217 (388)	total: 2.15s	remaining: 53s
    389:	learn: 114392.3913053	test: 131719.2221320	best: 131719.2221320 (389)	total: 2.15s	remaining: 53s
    390:	learn: 114354.3853855	test: 131669.8563496	best: 131669.8563496 (390)	total: 2.16s	remaining: 53s
    391:	learn: 114300.7426782	test: 131620.8154605	best: 131620.8154605 (391)	total: 2.16s	remaining: 53s
    392:	learn: 114250.0683189	test: 131591.9188614	best: 131591.9188614 (392)	total: 2.17s	remaining: 53s
    393:	learn: 114199.7140966	test: 131541.2735013	best: 131541.2735013 (393)	total: 2.17s	remaining: 53s
    394:	learn: 114132.8621465	test: 131490.8758094	best: 131490.8758094 (394)	total: 2.18s	remaining: 53s
    395:	learn: 114097.3325808	test: 131455.7686442	best: 131455.7686442 (395)	total: 2.19s	remaining: 53s
    396:	learn: 113985.5291775	test: 131371.1282445	best: 131371.1282445 (396)	total: 2.19s	remaining: 53s
    397:	learn: 113944.3197553	test: 131347.6450956	best: 131347.6450956 (397)	total: 2.2s	remaining: 53s
    398:	learn: 113892.6638076	test: 131319.1810245	best: 131319.1810245 (398)	total: 2.2s	remaining: 53s
    399:	learn: 113850.0598658	test: 131296.5275443	best: 131296.5275443 (399)	total: 2.21s	remaining: 53s
    400:	learn: 113812.3703243	test: 131272.6289564	best: 131272.6289564 (400)	total: 2.21s	remaining: 53s
    401:	learn: 113721.1473159	test: 131195.7745475	best: 131195.7745475 (401)	total: 2.22s	remaining: 53s
    402:	learn: 113668.7103761	test: 131178.9691769	best: 131178.9691769 (402)	total: 2.22s	remaining: 53s
    403:	learn: 113614.2186839	test: 131143.6647908	best: 131143.6647908 (403)	total: 2.23s	remaining: 53s
    404:	learn: 113561.7084488	test: 131102.6790508	best: 131102.6790508 (404)	total: 2.23s	remaining: 52.9s
    405:	learn: 113509.8030565	test: 131066.3065218	best: 131066.3065218 (405)	total: 2.24s	remaining: 52.9s
    406:	learn: 113463.7879114	test: 131057.9255725	best: 131057.9255725 (406)	total: 2.25s	remaining: 53s
    407:	learn: 113415.3538713	test: 131035.4546189	best: 131035.4546189 (407)	total: 2.25s	remaining: 53s
    408:	learn: 113366.6698630	test: 131000.6862923	best: 131000.6862923 (408)	total: 2.26s	remaining: 53s
    409:	learn: 113321.4286277	test: 130990.5839592	best: 130990.5839592 (409)	total: 2.27s	remaining: 53s
    410:	learn: 113280.4464190	test: 130968.1038978	best: 130968.1038978 (410)	total: 2.27s	remaining: 53s
    411:	learn: 113219.0311409	test: 130927.5899106	best: 130927.5899106 (411)	total: 2.28s	remaining: 53s
    412:	learn: 113160.0005943	test: 130916.7057982	best: 130916.7057982 (412)	total: 2.28s	remaining: 53s
    413:	learn: 113031.7335029	test: 130802.4735225	best: 130802.4735225 (413)	total: 2.29s	remaining: 53s
    414:	learn: 112995.5762004	test: 130759.9882872	best: 130759.9882872 (414)	total: 2.29s	remaining: 53s
    415:	learn: 112933.8927540	test: 130729.9895480	best: 130729.9895480 (415)	total: 2.3s	remaining: 53s
    416:	learn: 112869.5475335	test: 130691.0606784	best: 130691.0606784 (416)	total: 2.31s	remaining: 53s
    417:	learn: 112838.3716331	test: 130675.7250495	best: 130675.7250495 (417)	total: 2.31s	remaining: 53s
    418:	learn: 112785.0407051	test: 130633.7731233	best: 130633.7731233 (418)	total: 2.32s	remaining: 53s
    419:	learn: 112740.3583640	test: 130614.8082720	best: 130614.8082720 (419)	total: 2.32s	remaining: 53s
    420:	learn: 112692.6009001	test: 130581.0330457	best: 130581.0330457 (420)	total: 2.33s	remaining: 53s
    421:	learn: 112647.1788558	test: 130566.7137788	best: 130566.7137788 (421)	total: 2.33s	remaining: 53s
    422:	learn: 112583.3597712	test: 130528.2372714	best: 130528.2372714 (422)	total: 2.34s	remaining: 53s
    423:	learn: 112541.0996574	test: 130499.8989411	best: 130499.8989411 (423)	total: 2.35s	remaining: 53s
    424:	learn: 112499.5180422	test: 130471.8168314	best: 130471.8168314 (424)	total: 2.35s	remaining: 53s
    425:	learn: 112449.2790269	test: 130463.0434990	best: 130463.0434990 (425)	total: 2.36s	remaining: 53s
    426:	learn: 112396.1191632	test: 130446.7829173	best: 130446.7829173 (426)	total: 2.36s	remaining: 52.9s
    427:	learn: 112292.8123396	test: 130373.8290174	best: 130373.8290174 (427)	total: 2.37s	remaining: 52.9s
    428:	learn: 112260.3407113	test: 130346.8683384	best: 130346.8683384 (428)	total: 2.37s	remaining: 52.9s
    429:	learn: 112215.8856925	test: 130339.9236257	best: 130339.9236257 (429)	total: 2.38s	remaining: 52.9s
    430:	learn: 112156.3912455	test: 130303.1153442	best: 130303.1153442 (430)	total: 2.38s	remaining: 52.9s
    431:	learn: 112110.4889221	test: 130278.9531591	best: 130278.9531591 (431)	total: 2.39s	remaining: 52.9s
    432:	learn: 112068.0451143	test: 130264.7401287	best: 130264.7401287 (432)	total: 2.39s	remaining: 52.8s
    433:	learn: 112035.0294626	test: 130217.1244010	best: 130217.1244010 (433)	total: 2.4s	remaining: 52.8s
    434:	learn: 111986.1439536	test: 130208.4699855	best: 130208.4699855 (434)	total: 2.4s	remaining: 52.8s
    435:	learn: 111933.6005226	test: 130202.1510122	best: 130202.1510122 (435)	total: 2.41s	remaining: 52.8s
    436:	learn: 111899.5935065	test: 130188.4190106	best: 130188.4190106 (436)	total: 2.41s	remaining: 52.8s
    437:	learn: 111872.3276826	test: 130175.8559792	best: 130175.8559792 (437)	total: 2.42s	remaining: 52.8s
    438:	learn: 111835.7804571	test: 130167.4975009	best: 130167.4975009 (438)	total: 2.42s	remaining: 52.8s
    439:	learn: 111808.1116281	test: 130151.3528654	best: 130151.3528654 (439)	total: 2.43s	remaining: 52.8s
    440:	learn: 111757.7984461	test: 130123.7746855	best: 130123.7746855 (440)	total: 2.43s	remaining: 52.8s
    441:	learn: 111704.9123135	test: 130134.4997578	best: 130123.7746855 (440)	total: 2.44s	remaining: 52.8s
    442:	learn: 111676.3082495	test: 130120.0907686	best: 130120.0907686 (442)	total: 2.44s	remaining: 52.8s
    443:	learn: 111642.4534240	test: 130054.2748868	best: 130054.2748868 (443)	total: 2.45s	remaining: 52.8s
    444:	learn: 111609.2880861	test: 130004.3645757	best: 130004.3645757 (444)	total: 2.46s	remaining: 52.7s
    445:	learn: 111575.2681795	test: 129972.6433615	best: 129972.6433615 (445)	total: 2.46s	remaining: 52.7s
    446:	learn: 111534.0402077	test: 129943.9629832	best: 129943.9629832 (446)	total: 2.47s	remaining: 52.7s
    447:	learn: 111478.4741338	test: 129875.0207724	best: 129875.0207724 (447)	total: 2.47s	remaining: 52.7s
    448:	learn: 111448.7850660	test: 129873.3718956	best: 129873.3718956 (448)	total: 2.48s	remaining: 52.7s
    449:	learn: 111422.0843941	test: 129856.8505251	best: 129856.8505251 (449)	total: 2.48s	remaining: 52.7s
    450:	learn: 111395.6516178	test: 129866.8923067	best: 129856.8505251 (449)	total: 2.49s	remaining: 52.6s
    451:	learn: 111375.5036515	test: 129840.6792145	best: 129840.6792145 (451)	total: 2.49s	remaining: 52.6s
    452:	learn: 111329.4278101	test: 129774.1669515	best: 129774.1669515 (452)	total: 2.5s	remaining: 52.6s
    453:	learn: 111251.2012846	test: 129708.5380226	best: 129708.5380226 (453)	total: 2.5s	remaining: 52.6s
    454:	learn: 111200.8013680	test: 129621.5627993	best: 129621.5627993 (454)	total: 2.51s	remaining: 52.6s
    455:	learn: 111070.9679988	test: 129512.9992765	best: 129512.9992765 (455)	total: 2.51s	remaining: 52.6s
    456:	learn: 111028.9488995	test: 129498.8512151	best: 129498.8512151 (456)	total: 2.52s	remaining: 52.5s
    457:	learn: 110997.5567338	test: 129444.9506406	best: 129444.9506406 (457)	total: 2.52s	remaining: 52.5s
    458:	learn: 110960.0686028	test: 129419.5373258	best: 129419.5373258 (458)	total: 2.53s	remaining: 52.5s
    459:	learn: 110924.6920276	test: 129409.0584327	best: 129409.0584327 (459)	total: 2.53s	remaining: 52.5s
    460:	learn: 110886.5852188	test: 129389.6930532	best: 129389.6930532 (460)	total: 2.54s	remaining: 52.5s
    461:	learn: 110846.5132136	test: 129377.9127912	best: 129377.9127912 (461)	total: 2.54s	remaining: 52.5s
    462:	learn: 110783.2789503	test: 129344.8058126	best: 129344.8058126 (462)	total: 2.55s	remaining: 52.4s
    463:	learn: 110729.6372710	test: 129355.0951721	best: 129344.8058126 (462)	total: 2.55s	remaining: 52.4s
    464:	learn: 110692.8260332	test: 129333.0145136	best: 129333.0145136 (464)	total: 2.56s	remaining: 52.4s
    465:	learn: 110660.7831980	test: 129301.8506505	best: 129301.8506505 (465)	total: 2.56s	remaining: 52.4s
    466:	learn: 110555.3011663	test: 129218.2667285	best: 129218.2667285 (466)	total: 2.57s	remaining: 52.4s
    467:	learn: 110503.1764866	test: 129202.9846047	best: 129202.9846047 (467)	total: 2.57s	remaining: 52.4s
    468:	learn: 110464.4221754	test: 129206.9228917	best: 129202.9846047 (467)	total: 2.58s	remaining: 52.3s
    469:	learn: 110403.8269801	test: 129167.7891047	best: 129167.7891047 (469)	total: 2.58s	remaining: 52.3s
    470:	learn: 110373.1082577	test: 129147.2874084	best: 129147.2874084 (470)	total: 2.59s	remaining: 52.3s
    471:	learn: 110347.1874426	test: 129151.4050218	best: 129147.2874084 (470)	total: 2.59s	remaining: 52.3s
    472:	learn: 110307.4343605	test: 129147.2184855	best: 129147.2184855 (472)	total: 2.6s	remaining: 52.3s
    473:	learn: 110273.8633765	test: 129128.6000303	best: 129128.6000303 (473)	total: 2.6s	remaining: 52.3s
    474:	learn: 110142.2672455	test: 129020.8831876	best: 129020.8831876 (474)	total: 2.61s	remaining: 52.3s
    475:	learn: 110084.7162335	test: 128997.6265609	best: 128997.6265609 (475)	total: 2.61s	remaining: 52.3s
    476:	learn: 110023.9195253	test: 128955.5571769	best: 128955.5571769 (476)	total: 2.62s	remaining: 52.3s
    477:	learn: 109975.6869521	test: 128926.9592240	best: 128926.9592240 (477)	total: 2.63s	remaining: 52.3s
    478:	learn: 109905.5033627	test: 128868.4808175	best: 128868.4808175 (478)	total: 2.63s	remaining: 52.3s
    479:	learn: 109877.2664430	test: 128856.9048191	best: 128856.9048191 (479)	total: 2.64s	remaining: 52.3s
    480:	learn: 109844.5715051	test: 128819.8645438	best: 128819.8645438 (480)	total: 2.64s	remaining: 52.3s
    481:	learn: 109809.7086406	test: 128804.7077180	best: 128804.7077180 (481)	total: 2.65s	remaining: 52.3s
    482:	learn: 109770.3599102	test: 128787.8215122	best: 128787.8215122 (482)	total: 2.65s	remaining: 52.3s
    483:	learn: 109738.9977815	test: 128766.6675853	best: 128766.6675853 (483)	total: 2.66s	remaining: 52.3s
    484:	learn: 109691.5686447	test: 128769.6226076	best: 128766.6675853 (483)	total: 2.66s	remaining: 52.2s
    485:	learn: 109653.6875306	test: 128767.2997752	best: 128766.6675853 (483)	total: 2.67s	remaining: 52.2s
    486:	learn: 109616.2646212	test: 128770.6578024	best: 128766.6675853 (483)	total: 2.67s	remaining: 52.2s
    487:	learn: 109565.1388444	test: 128752.0350215	best: 128752.0350215 (487)	total: 2.68s	remaining: 52.2s
    488:	learn: 109455.5260351	test: 128665.7270135	best: 128665.7270135 (488)	total: 2.68s	remaining: 52.2s
    489:	learn: 109402.7999574	test: 128623.7703832	best: 128623.7703832 (489)	total: 2.69s	remaining: 52.2s
    490:	learn: 109361.5679927	test: 128603.7505521	best: 128603.7505521 (490)	total: 2.69s	remaining: 52.2s
    491:	learn: 109328.7774187	test: 128554.8482031	best: 128554.8482031 (491)	total: 2.7s	remaining: 52.2s
    492:	learn: 109291.2452212	test: 128543.0663692	best: 128543.0663692 (492)	total: 2.71s	remaining: 52.2s
    493:	learn: 109257.7591019	test: 128525.5824281	best: 128525.5824281 (493)	total: 2.71s	remaining: 52.2s
    494:	learn: 109210.2323937	test: 128506.9706671	best: 128506.9706671 (494)	total: 2.71s	remaining: 52.1s
    495:	learn: 109131.3643873	test: 128443.0794091	best: 128443.0794091 (495)	total: 2.72s	remaining: 52.1s
    496:	learn: 109082.7922880	test: 128405.6689185	best: 128405.6689185 (496)	total: 2.73s	remaining: 52.1s
    497:	learn: 109056.1403914	test: 128393.3747161	best: 128393.3747161 (497)	total: 2.73s	remaining: 52.1s
    498:	learn: 109019.6701983	test: 128402.9789089	best: 128393.3747161 (497)	total: 2.73s	remaining: 52.1s
    499:	learn: 108968.0964187	test: 128396.7350089	best: 128393.3747161 (497)	total: 2.74s	remaining: 52.1s
    500:	learn: 108915.0158231	test: 128372.9115724	best: 128372.9115724 (500)	total: 2.75s	remaining: 52s
    501:	learn: 108872.9571601	test: 128351.9035806	best: 128351.9035806 (501)	total: 2.75s	remaining: 52s
    502:	learn: 108781.6796044	test: 128260.8801892	best: 128260.8801892 (502)	total: 2.75s	remaining: 52s
    503:	learn: 108763.2546218	test: 128256.1875339	best: 128256.1875339 (503)	total: 2.76s	remaining: 52s
    504:	learn: 108731.4481250	test: 128195.8987172	best: 128195.8987172 (504)	total: 2.77s	remaining: 52s
    505:	learn: 108615.7371620	test: 128090.5324297	best: 128090.5324297 (505)	total: 2.77s	remaining: 52.1s
    506:	learn: 108575.8447026	test: 128089.4433085	best: 128089.4433085 (506)	total: 2.78s	remaining: 52s
    507:	learn: 108520.6995262	test: 128065.8280973	best: 128065.8280973 (507)	total: 2.78s	remaining: 52s
    508:	learn: 108463.5080176	test: 128042.8508317	best: 128042.8508317 (508)	total: 2.79s	remaining: 52s
    509:	learn: 108435.1784664	test: 128031.8999493	best: 128031.8999493 (509)	total: 2.79s	remaining: 52s
    510:	learn: 108399.0743676	test: 128004.4993261	best: 128004.4993261 (510)	total: 2.8s	remaining: 52s
    511:	learn: 108361.5340245	test: 127978.2716782	best: 127978.2716782 (511)	total: 2.81s	remaining: 52s
    512:	learn: 108327.9935243	test: 127956.0366127	best: 127956.0366127 (512)	total: 2.81s	remaining: 52s
    513:	learn: 108288.8395909	test: 127927.0247754	best: 127927.0247754 (513)	total: 2.81s	remaining: 52s
    514:	learn: 108249.1430563	test: 127943.3106151	best: 127927.0247754 (513)	total: 2.82s	remaining: 51.9s
    515:	learn: 108223.4372579	test: 127927.2761668	best: 127927.0247754 (513)	total: 2.83s	remaining: 51.9s
    516:	learn: 108186.1616412	test: 127904.9765577	best: 127904.9765577 (516)	total: 2.83s	remaining: 51.9s
    517:	learn: 108131.6809173	test: 127899.5832343	best: 127899.5832343 (517)	total: 2.84s	remaining: 51.9s
    518:	learn: 108090.9918310	test: 127881.5892401	best: 127881.5892401 (518)	total: 2.84s	remaining: 51.9s
    519:	learn: 108048.9230053	test: 127873.5001908	best: 127873.5001908 (519)	total: 2.85s	remaining: 51.9s
    520:	learn: 108013.5615575	test: 127866.5927707	best: 127866.5927707 (520)	total: 2.85s	remaining: 51.9s
    521:	learn: 107939.2859226	test: 127803.6981567	best: 127803.6981567 (521)	total: 2.86s	remaining: 51.9s
    522:	learn: 107895.6761671	test: 127776.2655853	best: 127776.2655853 (522)	total: 2.86s	remaining: 51.8s
    523:	learn: 107809.3994399	test: 127702.8818675	best: 127702.8818675 (523)	total: 2.87s	remaining: 51.8s
    524:	learn: 107763.1974878	test: 127666.3106999	best: 127666.3106999 (524)	total: 2.87s	remaining: 51.8s
    525:	learn: 107737.2533522	test: 127632.3525190	best: 127632.3525190 (525)	total: 2.88s	remaining: 51.8s
    526:	learn: 107661.4986225	test: 127588.3059631	best: 127588.3059631 (526)	total: 2.88s	remaining: 51.8s
    527:	learn: 107622.5040698	test: 127569.7400881	best: 127569.7400881 (527)	total: 2.89s	remaining: 51.8s
    528:	learn: 107579.2450265	test: 127552.6083127	best: 127552.6083127 (528)	total: 2.89s	remaining: 51.8s
    529:	learn: 107543.6270465	test: 127524.4269247	best: 127524.4269247 (529)	total: 2.9s	remaining: 51.8s
    530:	learn: 107458.4535700	test: 127450.0219721	best: 127450.0219721 (530)	total: 2.9s	remaining: 51.8s
    531:	learn: 107403.5422314	test: 127415.8194229	best: 127415.8194229 (531)	total: 2.91s	remaining: 51.8s
    532:	learn: 107368.4621014	test: 127414.8311360	best: 127414.8311360 (532)	total: 2.91s	remaining: 51.7s
    533:	learn: 107340.8303036	test: 127404.9181095	best: 127404.9181095 (533)	total: 2.92s	remaining: 51.7s
    534:	learn: 107317.1598631	test: 127386.3120678	best: 127386.3120678 (534)	total: 2.92s	remaining: 51.7s
    535:	learn: 107279.7773400	test: 127346.9504414	best: 127346.9504414 (535)	total: 2.93s	remaining: 51.7s
    536:	learn: 107251.8280301	test: 127332.1483383	best: 127332.1483383 (536)	total: 2.94s	remaining: 51.7s
    537:	learn: 107216.7360188	test: 127335.6953991	best: 127332.1483383 (536)	total: 2.94s	remaining: 51.7s
    538:	learn: 107171.6608230	test: 127299.3861021	best: 127299.3861021 (538)	total: 2.95s	remaining: 51.8s
    539:	learn: 107137.6066755	test: 127290.5320339	best: 127290.5320339 (539)	total: 2.96s	remaining: 51.8s
    540:	learn: 107101.7626825	test: 127282.9563387	best: 127282.9563387 (540)	total: 2.96s	remaining: 51.8s
    541:	learn: 107060.5338415	test: 127288.6608368	best: 127282.9563387 (540)	total: 2.96s	remaining: 51.8s
    542:	learn: 107020.8758390	test: 127263.1442112	best: 127263.1442112 (542)	total: 2.97s	remaining: 51.7s
    543:	learn: 106983.4136464	test: 127251.0574510	best: 127251.0574510 (543)	total: 2.98s	remaining: 51.7s
    544:	learn: 106956.0298610	test: 127235.6435016	best: 127235.6435016 (544)	total: 2.98s	remaining: 51.7s
    545:	learn: 106917.3334126	test: 127215.9090738	best: 127215.9090738 (545)	total: 2.99s	remaining: 51.7s
    546:	learn: 106886.2523383	test: 127202.6902201	best: 127202.6902201 (546)	total: 2.99s	remaining: 51.7s
    547:	learn: 106856.4971284	test: 127195.7297022	best: 127195.7297022 (547)	total: 3s	remaining: 51.7s
    548:	learn: 106817.3886882	test: 127180.8030836	best: 127180.8030836 (548)	total: 3s	remaining: 51.7s
    549:	learn: 106735.8361727	test: 127110.8929668	best: 127110.8929668 (549)	total: 3.01s	remaining: 51.7s
    550:	learn: 106699.9740286	test: 127101.3765585	best: 127101.3765585 (550)	total: 3.02s	remaining: 51.7s
    551:	learn: 106654.0896967	test: 127075.0796195	best: 127075.0796195 (551)	total: 3.02s	remaining: 51.7s
    552:	learn: 106602.2736198	test: 127070.7272007	best: 127070.7272007 (552)	total: 3.02s	remaining: 51.7s
    553:	learn: 106551.3810277	test: 127040.1495090	best: 127040.1495090 (553)	total: 3.03s	remaining: 51.7s
    554:	learn: 106450.0537626	test: 126947.8037183	best: 126947.8037183 (554)	total: 3.04s	remaining: 51.7s
    555:	learn: 106414.0893063	test: 126925.4951421	best: 126925.4951421 (555)	total: 3.04s	remaining: 51.7s
    556:	learn: 106378.1907698	test: 126885.0434744	best: 126885.0434744 (556)	total: 3.05s	remaining: 51.7s
    557:	learn: 106329.6709300	test: 126853.1349626	best: 126853.1349626 (557)	total: 3.05s	remaining: 51.7s
    558:	learn: 106295.6935131	test: 126828.0793732	best: 126828.0793732 (558)	total: 3.06s	remaining: 51.6s
    559:	learn: 106261.0508447	test: 126773.0772568	best: 126773.0772568 (559)	total: 3.06s	remaining: 51.6s
    560:	learn: 106244.2811828	test: 126759.1549335	best: 126759.1549335 (560)	total: 3.07s	remaining: 51.6s
    561:	learn: 106182.3262629	test: 126707.9924242	best: 126707.9924242 (561)	total: 3.07s	remaining: 51.6s
    562:	learn: 106155.0271536	test: 126712.0595567	best: 126707.9924242 (561)	total: 3.08s	remaining: 51.6s
    563:	learn: 106117.8454255	test: 126686.2371125	best: 126686.2371125 (563)	total: 3.08s	remaining: 51.6s
    564:	learn: 106061.4553517	test: 126656.5251505	best: 126656.5251505 (564)	total: 3.09s	remaining: 51.6s
    565:	learn: 106023.6119706	test: 126614.4741613	best: 126614.4741613 (565)	total: 3.09s	remaining: 51.6s
    566:	learn: 105993.1977229	test: 126597.8128464	best: 126597.8128464 (566)	total: 3.1s	remaining: 51.6s
    567:	learn: 105962.4305649	test: 126573.8018903	best: 126573.8018903 (567)	total: 3.11s	remaining: 51.6s
    568:	learn: 105886.5584921	test: 126514.5119768	best: 126514.5119768 (568)	total: 3.11s	remaining: 51.6s
    569:	learn: 105856.7065755	test: 126512.7996411	best: 126512.7996411 (569)	total: 3.12s	remaining: 51.6s
    570:	learn: 105826.1914404	test: 126497.4487348	best: 126497.4487348 (570)	total: 3.13s	remaining: 51.6s
    571:	learn: 105791.6366163	test: 126482.0063200	best: 126482.0063200 (571)	total: 3.13s	remaining: 51.6s
    572:	learn: 105734.5250879	test: 126440.0115780	best: 126440.0115780 (572)	total: 3.14s	remaining: 51.6s
    573:	learn: 105674.5820005	test: 126400.5976055	best: 126400.5976055 (573)	total: 3.14s	remaining: 51.6s
    574:	learn: 105630.8896722	test: 126377.8078659	best: 126377.8078659 (574)	total: 3.15s	remaining: 51.6s
    575:	learn: 105605.3045405	test: 126371.8609851	best: 126371.8609851 (575)	total: 3.16s	remaining: 51.6s
    576:	learn: 105569.5780638	test: 126355.1045920	best: 126355.1045920 (576)	total: 3.16s	remaining: 51.6s
    577:	learn: 105511.1905643	test: 126306.2244686	best: 126306.2244686 (577)	total: 3.17s	remaining: 51.6s
    578:	learn: 105472.5716836	test: 126298.3768461	best: 126298.3768461 (578)	total: 3.17s	remaining: 51.6s
    579:	learn: 105387.1177627	test: 126231.2033383	best: 126231.2033383 (579)	total: 3.18s	remaining: 51.6s
    580:	learn: 105324.1591623	test: 126189.1946803	best: 126189.1946803 (580)	total: 3.18s	remaining: 51.6s
    581:	learn: 105288.6918589	test: 126177.8688561	best: 126177.8688561 (581)	total: 3.19s	remaining: 51.6s
    582:	learn: 105253.6656201	test: 126169.2005362	best: 126169.2005362 (582)	total: 3.19s	remaining: 51.6s
    583:	learn: 105209.0744091	test: 126133.8898113	best: 126133.8898113 (583)	total: 3.2s	remaining: 51.6s
    584:	learn: 105169.5877330	test: 126114.0373781	best: 126114.0373781 (584)	total: 3.21s	remaining: 51.6s
    585:	learn: 105108.0099174	test: 126098.6706251	best: 126098.6706251 (585)	total: 3.21s	remaining: 51.6s
    586:	learn: 105056.5618798	test: 126079.8292600	best: 126079.8292600 (586)	total: 3.22s	remaining: 51.6s
    587:	learn: 105003.5757607	test: 126055.5406233	best: 126055.5406233 (587)	total: 3.22s	remaining: 51.6s
    588:	learn: 104964.3093315	test: 126042.0206827	best: 126042.0206827 (588)	total: 3.23s	remaining: 51.6s
    589:	learn: 104905.6127233	test: 125993.0288953	best: 125993.0288953 (589)	total: 3.24s	remaining: 51.6s
    590:	learn: 104867.3415179	test: 125983.0068904	best: 125983.0068904 (590)	total: 3.24s	remaining: 51.6s
    591:	learn: 104834.5293054	test: 125958.9901249	best: 125958.9901249 (591)	total: 3.25s	remaining: 51.6s
    592:	learn: 104752.5701646	test: 125928.6274611	best: 125928.6274611 (592)	total: 3.25s	remaining: 51.6s
    593:	learn: 104713.8581913	test: 125910.8463808	best: 125910.8463808 (593)	total: 3.26s	remaining: 51.6s
    594:	learn: 104691.2051187	test: 125898.7553181	best: 125898.7553181 (594)	total: 3.26s	remaining: 51.6s
    595:	learn: 104651.6807745	test: 125883.8505452	best: 125883.8505452 (595)	total: 3.27s	remaining: 51.6s
    596:	learn: 104593.3457710	test: 125835.0734885	best: 125835.0734885 (596)	total: 3.28s	remaining: 51.6s
    597:	learn: 104544.6491057	test: 125803.1445702	best: 125803.1445702 (597)	total: 3.28s	remaining: 51.6s
    598:	learn: 104515.9994609	test: 125786.7557495	best: 125786.7557495 (598)	total: 3.29s	remaining: 51.6s
    599:	learn: 104467.6422434	test: 125770.5805762	best: 125770.5805762 (599)	total: 3.29s	remaining: 51.6s
    600:	learn: 104427.4464853	test: 125750.0078195	best: 125750.0078195 (600)	total: 3.3s	remaining: 51.6s
    601:	learn: 104388.4704915	test: 125722.1746680	best: 125722.1746680 (601)	total: 3.31s	remaining: 51.6s
    602:	learn: 104339.5942045	test: 125685.7157353	best: 125685.7157353 (602)	total: 3.31s	remaining: 51.6s
    603:	learn: 104295.2596471	test: 125652.9888182	best: 125652.9888182 (603)	total: 3.32s	remaining: 51.6s
    604:	learn: 104246.0543106	test: 125614.8348354	best: 125614.8348354 (604)	total: 3.33s	remaining: 51.6s
    605:	learn: 104208.9672487	test: 125610.9490340	best: 125610.9490340 (605)	total: 3.33s	remaining: 51.6s
    606:	learn: 104163.2679246	test: 125573.4063413	best: 125573.4063413 (606)	total: 3.34s	remaining: 51.6s
    607:	learn: 104121.0143035	test: 125566.4425923	best: 125566.4425923 (607)	total: 3.34s	remaining: 51.6s
    608:	learn: 104091.2875247	test: 125551.8846559	best: 125551.8846559 (608)	total: 3.35s	remaining: 51.6s
    609:	learn: 104056.6487138	test: 125540.3407402	best: 125540.3407402 (609)	total: 3.35s	remaining: 51.6s
    610:	learn: 104019.7384899	test: 125517.5824938	best: 125517.5824938 (610)	total: 3.36s	remaining: 51.6s
    611:	learn: 103987.2367661	test: 125502.3764841	best: 125502.3764841 (611)	total: 3.36s	remaining: 51.6s
    612:	learn: 103937.8619948	test: 125464.4970692	best: 125464.4970692 (612)	total: 3.37s	remaining: 51.6s
    613:	learn: 103903.2722965	test: 125450.1623987	best: 125450.1623987 (613)	total: 3.38s	remaining: 51.6s
    614:	learn: 103849.8131929	test: 125423.7472528	best: 125423.7472528 (614)	total: 3.38s	remaining: 51.6s
    615:	learn: 103814.9150660	test: 125396.2519833	best: 125396.2519833 (615)	total: 3.39s	remaining: 51.6s
    616:	learn: 103780.4817104	test: 125372.7589047	best: 125372.7589047 (616)	total: 3.39s	remaining: 51.6s
    617:	learn: 103761.5655271	test: 125365.5703981	best: 125365.5703981 (617)	total: 3.4s	remaining: 51.6s
    618:	learn: 103729.1102176	test: 125353.8363265	best: 125353.8363265 (618)	total: 3.4s	remaining: 51.6s
    619:	learn: 103699.7217541	test: 125345.0933084	best: 125345.0933084 (619)	total: 3.41s	remaining: 51.6s
    620:	learn: 103668.7035967	test: 125335.5782964	best: 125335.5782964 (620)	total: 3.41s	remaining: 51.6s
    621:	learn: 103613.8857475	test: 125297.3558811	best: 125297.3558811 (621)	total: 3.42s	remaining: 51.6s
    622:	learn: 103563.9888102	test: 125264.2646813	best: 125264.2646813 (622)	total: 3.42s	remaining: 51.6s
    623:	learn: 103512.3530363	test: 125223.8812333	best: 125223.8812333 (623)	total: 3.43s	remaining: 51.6s
    624:	learn: 103486.8722986	test: 125224.5152697	best: 125223.8812333 (623)	total: 3.44s	remaining: 51.5s
    625:	learn: 103452.6611968	test: 125208.8194688	best: 125208.8194688 (625)	total: 3.44s	remaining: 51.5s
    626:	learn: 103420.8920255	test: 125207.7254408	best: 125207.7254408 (626)	total: 3.45s	remaining: 51.5s
    627:	learn: 103396.9198371	test: 125190.1390273	best: 125190.1390273 (627)	total: 3.45s	remaining: 51.5s
    628:	learn: 103350.3339071	test: 125154.5175435	best: 125154.5175435 (628)	total: 3.46s	remaining: 51.5s
    629:	learn: 103319.8769457	test: 125128.3405622	best: 125128.3405622 (629)	total: 3.46s	remaining: 51.5s
    630:	learn: 103281.9800907	test: 125114.5166011	best: 125114.5166011 (630)	total: 3.47s	remaining: 51.5s
    631:	learn: 103206.6464336	test: 125079.7845888	best: 125079.7845888 (631)	total: 3.48s	remaining: 51.5s
    632:	learn: 103185.4449057	test: 125072.1943929	best: 125072.1943929 (632)	total: 3.48s	remaining: 51.5s
    633:	learn: 103140.4052537	test: 125053.8178761	best: 125053.8178761 (633)	total: 3.49s	remaining: 51.5s
    634:	learn: 103106.2686537	test: 125029.6329979	best: 125029.6329979 (634)	total: 3.49s	remaining: 51.5s
    635:	learn: 103077.1625922	test: 124996.7243718	best: 124996.7243718 (635)	total: 3.5s	remaining: 51.5s
    636:	learn: 103026.7432456	test: 124957.2079710	best: 124957.2079710 (636)	total: 3.5s	remaining: 51.5s
    637:	learn: 102996.6886586	test: 124941.6256408	best: 124941.6256408 (637)	total: 3.51s	remaining: 51.5s
    638:	learn: 102952.7995977	test: 124924.5063544	best: 124924.5063544 (638)	total: 3.51s	remaining: 51.5s
    639:	learn: 102907.9450969	test: 124909.1291874	best: 124909.1291874 (639)	total: 3.52s	remaining: 51.5s
    640:	learn: 102880.7992074	test: 124899.4736594	best: 124899.4736594 (640)	total: 3.52s	remaining: 51.4s
    641:	learn: 102840.9738714	test: 124875.0047552	best: 124875.0047552 (641)	total: 3.53s	remaining: 51.4s
    642:	learn: 102820.0219918	test: 124877.0946285	best: 124875.0047552 (641)	total: 3.53s	remaining: 51.4s
    643:	learn: 102778.3942406	test: 124884.0946656	best: 124875.0047552 (641)	total: 3.54s	remaining: 51.4s
    644:	learn: 102741.2220960	test: 124860.2363979	best: 124860.2363979 (644)	total: 3.54s	remaining: 51.4s
    645:	learn: 102709.6842656	test: 124834.6403386	best: 124834.6403386 (645)	total: 3.55s	remaining: 51.4s
    646:	learn: 102686.2383489	test: 124803.1899817	best: 124803.1899817 (646)	total: 3.55s	remaining: 51.4s
    647:	learn: 102646.7238260	test: 124797.1991307	best: 124797.1991307 (647)	total: 3.56s	remaining: 51.4s
    648:	learn: 102590.4857097	test: 124792.2948963	best: 124792.2948963 (648)	total: 3.56s	remaining: 51.4s
    649:	learn: 102567.5405531	test: 124789.0831840	best: 124789.0831840 (649)	total: 3.57s	remaining: 51.4s
    650:	learn: 102539.0460089	test: 124779.3722897	best: 124779.3722897 (650)	total: 3.58s	remaining: 51.3s
    651:	learn: 102505.1069530	test: 124756.5450520	best: 124756.5450520 (651)	total: 3.58s	remaining: 51.3s
    652:	learn: 102454.1059459	test: 124721.3464242	best: 124721.3464242 (652)	total: 3.59s	remaining: 51.3s
    653:	learn: 102405.0683483	test: 124687.9508158	best: 124687.9508158 (653)	total: 3.59s	remaining: 51.3s
    654:	learn: 102373.8959259	test: 124674.6940464	best: 124674.6940464 (654)	total: 3.6s	remaining: 51.3s
    655:	learn: 102346.5801037	test: 124658.6645821	best: 124658.6645821 (655)	total: 3.6s	remaining: 51.3s
    656:	learn: 102295.7304466	test: 124655.0662287	best: 124655.0662287 (656)	total: 3.61s	remaining: 51.3s
    657:	learn: 102260.0419911	test: 124637.2998966	best: 124637.2998966 (657)	total: 3.61s	remaining: 51.3s
    658:	learn: 102243.7376505	test: 124630.5415321	best: 124630.5415321 (658)	total: 3.62s	remaining: 51.3s
    659:	learn: 102213.7606429	test: 124620.6546035	best: 124620.6546035 (659)	total: 3.63s	remaining: 51.3s
    660:	learn: 102166.1896983	test: 124588.6251182	best: 124588.6251182 (660)	total: 3.63s	remaining: 51.3s
    661:	learn: 102142.6734664	test: 124570.3271060	best: 124570.3271060 (661)	total: 3.64s	remaining: 51.3s
    662:	learn: 102105.3340951	test: 124547.3014744	best: 124547.3014744 (662)	total: 3.64s	remaining: 51.3s
    663:	learn: 102073.4897393	test: 124545.9400184	best: 124545.9400184 (663)	total: 3.65s	remaining: 51.3s
    664:	learn: 102049.9053833	test: 124533.2308541	best: 124533.2308541 (664)	total: 3.65s	remaining: 51.3s
    665:	learn: 102024.2043104	test: 124520.4733902	best: 124520.4733902 (665)	total: 3.66s	remaining: 51.3s
    666:	learn: 101988.7889004	test: 124506.9059340	best: 124506.9059340 (666)	total: 3.67s	remaining: 51.3s
    667:	learn: 101946.3288944	test: 124474.1417776	best: 124474.1417776 (667)	total: 3.67s	remaining: 51.3s
    668:	learn: 101914.9970946	test: 124444.0905824	best: 124444.0905824 (668)	total: 3.68s	remaining: 51.3s
    669:	learn: 101889.6817979	test: 124441.8237499	best: 124441.8237499 (669)	total: 3.68s	remaining: 51.3s
    670:	learn: 101860.3760982	test: 124438.5854619	best: 124438.5854619 (670)	total: 3.69s	remaining: 51.3s
    671:	learn: 101830.7830808	test: 124432.2449368	best: 124432.2449368 (671)	total: 3.69s	remaining: 51.3s
    672:	learn: 101783.3871446	test: 124399.0332985	best: 124399.0332985 (672)	total: 3.7s	remaining: 51.3s
    673:	learn: 101734.2817393	test: 124359.6047370	best: 124359.6047370 (673)	total: 3.71s	remaining: 51.3s
    674:	learn: 101707.6335887	test: 124362.5910788	best: 124359.6047370 (673)	total: 3.71s	remaining: 51.3s
    675:	learn: 101680.8799759	test: 124350.9964235	best: 124350.9964235 (675)	total: 3.72s	remaining: 51.3s
    676:	learn: 101657.3756972	test: 124345.6709073	best: 124345.6709073 (676)	total: 3.72s	remaining: 51.3s
    677:	learn: 101624.6344131	test: 124334.0507045	best: 124334.0507045 (677)	total: 3.73s	remaining: 51.3s
    678:	learn: 101592.1061906	test: 124313.5610010	best: 124313.5610010 (678)	total: 3.73s	remaining: 51.3s
    679:	learn: 101532.4699942	test: 124260.7593634	best: 124260.7593634 (679)	total: 3.74s	remaining: 51.3s
    680:	learn: 101501.0618158	test: 124254.2839898	best: 124254.2839898 (680)	total: 3.75s	remaining: 51.3s
    681:	learn: 101466.3122307	test: 124232.2083430	best: 124232.2083430 (681)	total: 3.75s	remaining: 51.2s
    682:	learn: 101439.4976547	test: 124212.8400259	best: 124212.8400259 (682)	total: 3.76s	remaining: 51.2s
    683:	learn: 101406.2651821	test: 124202.0979434	best: 124202.0979434 (683)	total: 3.76s	remaining: 51.2s
    684:	learn: 101372.5439219	test: 124207.7998635	best: 124202.0979434 (683)	total: 3.77s	remaining: 51.2s
    685:	learn: 101323.5462937	test: 124166.1540919	best: 124166.1540919 (685)	total: 3.77s	remaining: 51.2s
    686:	learn: 101289.7964024	test: 124144.7830265	best: 124144.7830265 (686)	total: 3.78s	remaining: 51.2s
    687:	learn: 101238.5333957	test: 124114.4208146	best: 124114.4208146 (687)	total: 3.78s	remaining: 51.2s
    688:	learn: 101175.0367931	test: 124068.6896375	best: 124068.6896375 (688)	total: 3.79s	remaining: 51.2s
    689:	learn: 101152.6354821	test: 124068.5481895	best: 124068.5481895 (689)	total: 3.8s	remaining: 51.2s
    690:	learn: 101107.8589243	test: 124064.5141193	best: 124064.5141193 (690)	total: 3.8s	remaining: 51.2s
    691:	learn: 101081.4210561	test: 124038.6116828	best: 124038.6116828 (691)	total: 3.81s	remaining: 51.2s
    692:	learn: 101061.6969872	test: 124031.5081817	best: 124031.5081817 (692)	total: 3.81s	remaining: 51.2s
    693:	learn: 101048.2722946	test: 124036.4463294	best: 124031.5081817 (692)	total: 3.82s	remaining: 51.2s
    694:	learn: 101013.5052655	test: 124025.1780679	best: 124025.1780679 (694)	total: 3.83s	remaining: 51.2s
    695:	learn: 100982.6201274	test: 124012.6058816	best: 124012.6058816 (695)	total: 3.83s	remaining: 51.2s
    696:	learn: 100950.8507433	test: 124009.4203258	best: 124009.4203258 (696)	total: 3.84s	remaining: 51.2s
    697:	learn: 100925.4189853	test: 123997.6482819	best: 123997.6482819 (697)	total: 3.84s	remaining: 51.2s
    698:	learn: 100878.4541857	test: 123975.5227079	best: 123975.5227079 (698)	total: 3.85s	remaining: 51.2s
    699:	learn: 100847.7555224	test: 123970.6109930	best: 123970.6109930 (699)	total: 3.85s	remaining: 51.2s
    700:	learn: 100822.7540742	test: 123952.2913146	best: 123952.2913146 (700)	total: 3.86s	remaining: 51.2s
    701:	learn: 100799.4067228	test: 123943.2828275	best: 123943.2828275 (701)	total: 3.87s	remaining: 51.2s
    702:	learn: 100763.3607975	test: 123916.2751249	best: 123916.2751249 (702)	total: 3.87s	remaining: 51.2s
    703:	learn: 100735.3981307	test: 123889.6939969	best: 123889.6939969 (703)	total: 3.88s	remaining: 51.2s
    704:	learn: 100710.3268400	test: 123889.9237615	best: 123889.6939969 (703)	total: 3.88s	remaining: 51.2s
    705:	learn: 100682.8698913	test: 123873.6800689	best: 123873.6800689 (705)	total: 3.89s	remaining: 51.2s
    706:	learn: 100647.7300855	test: 123845.8515921	best: 123845.8515921 (706)	total: 3.9s	remaining: 51.2s
    707:	learn: 100618.4726755	test: 123828.8005595	best: 123828.8005595 (707)	total: 3.9s	remaining: 51.2s
    708:	learn: 100577.2872693	test: 123811.2971183	best: 123811.2971183 (708)	total: 3.91s	remaining: 51.2s
    709:	learn: 100555.3083136	test: 123823.1020344	best: 123811.2971183 (708)	total: 3.91s	remaining: 51.2s
    710:	learn: 100525.8813543	test: 123822.7497228	best: 123811.2971183 (708)	total: 3.92s	remaining: 51.2s
    711:	learn: 100491.2641472	test: 123789.5912602	best: 123789.5912602 (711)	total: 3.92s	remaining: 51.2s
    712:	learn: 100458.5162358	test: 123783.6922181	best: 123783.6922181 (712)	total: 3.93s	remaining: 51.2s
    713:	learn: 100411.7645128	test: 123744.8523057	best: 123744.8523057 (713)	total: 3.94s	remaining: 51.2s
    714:	learn: 100367.2551421	test: 123720.6389086	best: 123720.6389086 (714)	total: 3.94s	remaining: 51.2s
    715:	learn: 100338.0948380	test: 123694.2367826	best: 123694.2367826 (715)	total: 3.95s	remaining: 51.2s
    716:	learn: 100303.4344522	test: 123678.0751109	best: 123678.0751109 (716)	total: 3.96s	remaining: 51.2s
    717:	learn: 100280.3703601	test: 123670.0904363	best: 123670.0904363 (717)	total: 3.96s	remaining: 51.2s
    718:	learn: 100246.7360137	test: 123654.6484033	best: 123654.6484033 (718)	total: 3.96s	remaining: 51.2s
    719:	learn: 100210.8762658	test: 123646.8708826	best: 123646.8708826 (719)	total: 3.97s	remaining: 51.2s
    720:	learn: 100184.0541656	test: 123636.7385921	best: 123636.7385921 (720)	total: 3.98s	remaining: 51.2s
    721:	learn: 100157.3687930	test: 123633.8504257	best: 123633.8504257 (721)	total: 3.98s	remaining: 51.2s
    722:	learn: 100128.8198439	test: 123629.3924579	best: 123629.3924579 (722)	total: 3.99s	remaining: 51.2s
    723:	learn: 100097.6025986	test: 123590.1191221	best: 123590.1191221 (723)	total: 4s	remaining: 51.2s
    724:	learn: 100074.8778810	test: 123588.8289403	best: 123588.8289403 (724)	total: 4s	remaining: 51.2s
    725:	learn: 100041.3054028	test: 123585.7316117	best: 123585.7316117 (725)	total: 4.01s	remaining: 51.2s
    726:	learn: 100013.8409869	test: 123581.7790936	best: 123581.7790936 (726)	total: 4.01s	remaining: 51.2s
    727:	learn: 99987.1844735	test: 123562.3728648	best: 123562.3728648 (727)	total: 4.02s	remaining: 51.2s
    728:	learn: 99963.5017106	test: 123562.8014707	best: 123562.3728648 (727)	total: 4.03s	remaining: 51.2s
    729:	learn: 99932.2691736	test: 123557.3358883	best: 123557.3358883 (729)	total: 4.03s	remaining: 51.2s
    730:	learn: 99908.8338454	test: 123557.3614908	best: 123557.3358883 (729)	total: 4.04s	remaining: 51.2s
    731:	learn: 99882.6425995	test: 123535.1270891	best: 123535.1270891 (731)	total: 4.04s	remaining: 51.2s
    732:	learn: 99848.8202026	test: 123509.4012954	best: 123509.4012954 (732)	total: 4.05s	remaining: 51.2s
    733:	learn: 99824.3443615	test: 123499.2209281	best: 123499.2209281 (733)	total: 4.05s	remaining: 51.2s
    734:	learn: 99793.9411494	test: 123474.1864312	best: 123474.1864312 (734)	total: 4.06s	remaining: 51.2s
    735:	learn: 99760.2304569	test: 123452.6587531	best: 123452.6587531 (735)	total: 4.07s	remaining: 51.2s
    736:	learn: 99728.9881496	test: 123445.1487611	best: 123445.1487611 (736)	total: 4.07s	remaining: 51.2s
    737:	learn: 99706.5582359	test: 123445.9749422	best: 123445.1487611 (736)	total: 4.08s	remaining: 51.2s
    738:	learn: 99675.4505054	test: 123434.3158232	best: 123434.3158232 (738)	total: 4.08s	remaining: 51.2s
    739:	learn: 99647.3703021	test: 123429.0661618	best: 123429.0661618 (739)	total: 4.09s	remaining: 51.2s
    740:	learn: 99622.7461987	test: 123411.8823047	best: 123411.8823047 (740)	total: 4.09s	remaining: 51.2s
    741:	learn: 99601.6202929	test: 123400.8217593	best: 123400.8217593 (741)	total: 4.1s	remaining: 51.2s
    742:	learn: 99584.1572596	test: 123389.3929951	best: 123389.3929951 (742)	total: 4.11s	remaining: 51.2s
    743:	learn: 99560.1452427	test: 123373.2061822	best: 123373.2061822 (743)	total: 4.11s	remaining: 51.2s
    744:	learn: 99534.2341418	test: 123370.1868566	best: 123370.1868566 (744)	total: 4.12s	remaining: 51.2s
    745:	learn: 99510.8224938	test: 123360.1811395	best: 123360.1811395 (745)	total: 4.12s	remaining: 51.2s
    746:	learn: 99479.9828270	test: 123343.8386277	best: 123343.8386277 (746)	total: 4.13s	remaining: 51.1s
    747:	learn: 99435.1036208	test: 123310.3378999	best: 123310.3378999 (747)	total: 4.13s	remaining: 51.1s
    748:	learn: 99400.8004076	test: 123294.1043298	best: 123294.1043298 (748)	total: 4.14s	remaining: 51.1s
    749:	learn: 99378.7549725	test: 123280.4974639	best: 123280.4974639 (749)	total: 4.14s	remaining: 51.1s
    750:	learn: 99345.0258805	test: 123256.1610402	best: 123256.1610402 (750)	total: 4.15s	remaining: 51.1s
    751:	learn: 99313.3117794	test: 123229.4738620	best: 123229.4738620 (751)	total: 4.16s	remaining: 51.2s
    752:	learn: 99282.3735480	test: 123199.6310033	best: 123199.6310033 (752)	total: 4.17s	remaining: 51.2s
    753:	learn: 99251.8018400	test: 123176.4509994	best: 123176.4509994 (753)	total: 4.17s	remaining: 51.2s
    754:	learn: 99223.2236646	test: 123157.6767199	best: 123157.6767199 (754)	total: 4.18s	remaining: 51.2s
    755:	learn: 99194.6663236	test: 123134.7909246	best: 123134.7909246 (755)	total: 4.18s	remaining: 51.2s
    756:	learn: 99172.9322239	test: 123135.2560743	best: 123134.7909246 (755)	total: 4.19s	remaining: 51.2s
    757:	learn: 99152.0596950	test: 123127.4539349	best: 123127.4539349 (757)	total: 4.2s	remaining: 51.2s
    758:	learn: 99125.0171863	test: 123122.7330851	best: 123122.7330851 (758)	total: 4.2s	remaining: 51.2s
    759:	learn: 99092.4491948	test: 123107.5572040	best: 123107.5572040 (759)	total: 4.21s	remaining: 51.2s
    760:	learn: 99034.2951785	test: 123068.3579405	best: 123068.3579405 (760)	total: 4.21s	remaining: 51.1s
    761:	learn: 99007.9877612	test: 123069.8194193	best: 123068.3579405 (760)	total: 4.22s	remaining: 51.1s
    762:	learn: 98977.2796270	test: 123050.4716916	best: 123050.4716916 (762)	total: 4.22s	remaining: 51.1s
    763:	learn: 98955.1644522	test: 123033.2028921	best: 123033.2028921 (763)	total: 4.23s	remaining: 51.1s
    764:	learn: 98912.9722817	test: 123000.4118488	best: 123000.4118488 (764)	total: 4.24s	remaining: 51.2s
    765:	learn: 98881.8264908	test: 122987.5435975	best: 122987.5435975 (765)	total: 4.24s	remaining: 51.1s
    766:	learn: 98853.5662251	test: 122983.6881631	best: 122983.6881631 (766)	total: 4.25s	remaining: 51.1s
    767:	learn: 98826.9647610	test: 122986.6115934	best: 122983.6881631 (766)	total: 4.25s	remaining: 51.1s
    768:	learn: 98785.0125613	test: 122955.5939991	best: 122955.5939991 (768)	total: 4.26s	remaining: 51.1s
    769:	learn: 98743.7418346	test: 122921.8857875	best: 122921.8857875 (769)	total: 4.26s	remaining: 51.1s
    770:	learn: 98718.7580895	test: 122913.8680623	best: 122913.8680623 (770)	total: 4.27s	remaining: 51.1s
    771:	learn: 98689.3294310	test: 122917.7603004	best: 122913.8680623 (770)	total: 4.27s	remaining: 51.1s
    772:	learn: 98643.7078583	test: 122893.6859079	best: 122893.6859079 (772)	total: 4.28s	remaining: 51.1s
    773:	learn: 98599.5924882	test: 122870.1089507	best: 122870.1089507 (773)	total: 4.29s	remaining: 51.1s
    774:	learn: 98577.5406276	test: 122859.5822662	best: 122859.5822662 (774)	total: 4.29s	remaining: 51.1s
    775:	learn: 98561.4528738	test: 122864.9753876	best: 122859.5822662 (774)	total: 4.3s	remaining: 51.1s
    776:	learn: 98525.4234012	test: 122864.4449332	best: 122859.5822662 (774)	total: 4.3s	remaining: 51.1s
    777:	learn: 98495.1695061	test: 122857.9632122	best: 122857.9632122 (777)	total: 4.31s	remaining: 51.1s
    778:	learn: 98468.2300635	test: 122855.0169071	best: 122855.0169071 (778)	total: 4.31s	remaining: 51.1s
    779:	learn: 98439.9470782	test: 122850.5426575	best: 122850.5426575 (779)	total: 4.32s	remaining: 51.1s
    780:	learn: 98412.7024721	test: 122840.5349836	best: 122840.5349836 (780)	total: 4.33s	remaining: 51.1s
    781:	learn: 98384.8831060	test: 122815.0390768	best: 122815.0390768 (781)	total: 4.33s	remaining: 51.1s
    782:	learn: 98355.6180331	test: 122812.7975619	best: 122812.7975619 (782)	total: 4.34s	remaining: 51.1s
    783:	learn: 98329.4760356	test: 122792.5900104	best: 122792.5900104 (783)	total: 4.34s	remaining: 51.1s
    784:	learn: 98308.0301787	test: 122782.9184086	best: 122782.9184086 (784)	total: 4.35s	remaining: 51.1s
    785:	learn: 98285.7423827	test: 122775.6311437	best: 122775.6311437 (785)	total: 4.35s	remaining: 51s
    786:	learn: 98258.6239497	test: 122769.7369824	best: 122769.7369824 (786)	total: 4.36s	remaining: 51s
    787:	learn: 98236.7034036	test: 122768.7913331	best: 122768.7913331 (787)	total: 4.37s	remaining: 51s
    788:	learn: 98214.3180844	test: 122764.9046350	best: 122764.9046350 (788)	total: 4.37s	remaining: 51s
    789:	learn: 98198.2567724	test: 122757.6558231	best: 122757.6558231 (789)	total: 4.38s	remaining: 51s
    790:	learn: 98176.1214716	test: 122742.8302036	best: 122742.8302036 (790)	total: 4.38s	remaining: 51s
    791:	learn: 98142.1859012	test: 122719.1481215	best: 122719.1481215 (791)	total: 4.39s	remaining: 51s
    792:	learn: 98115.5748982	test: 122704.5156907	best: 122704.5156907 (792)	total: 4.39s	remaining: 51s
    793:	learn: 98059.7859519	test: 122664.1493871	best: 122664.1493871 (793)	total: 4.4s	remaining: 51s
    794:	learn: 98041.1781746	test: 122634.7752076	best: 122634.7752076 (794)	total: 4.4s	remaining: 51s
    795:	learn: 98015.6699157	test: 122638.4109640	best: 122634.7752076 (794)	total: 4.41s	remaining: 51s
    796:	learn: 97990.5008947	test: 122615.3694192	best: 122615.3694192 (796)	total: 4.42s	remaining: 51s
    797:	learn: 97942.9993164	test: 122581.5069484	best: 122581.5069484 (797)	total: 4.42s	remaining: 51s
    798:	learn: 97922.5537239	test: 122582.3658539	best: 122581.5069484 (797)	total: 4.42s	remaining: 51s
    799:	learn: 97902.0942942	test: 122583.6452878	best: 122581.5069484 (797)	total: 4.43s	remaining: 51s
    800:	learn: 97880.5539060	test: 122578.7095599	best: 122578.7095599 (800)	total: 4.44s	remaining: 51s
    801:	learn: 97856.4086008	test: 122566.6161444	best: 122566.6161444 (801)	total: 4.44s	remaining: 50.9s
    802:	learn: 97840.5389396	test: 122535.8541496	best: 122535.8541496 (802)	total: 4.45s	remaining: 50.9s
    803:	learn: 97801.8249026	test: 122505.9572581	best: 122505.9572581 (803)	total: 4.45s	remaining: 50.9s
    804:	learn: 97781.9271081	test: 122506.9899853	best: 122505.9572581 (803)	total: 4.46s	remaining: 50.9s
    805:	learn: 97756.1387809	test: 122490.7467446	best: 122490.7467446 (805)	total: 4.46s	remaining: 50.9s
    806:	learn: 97735.9627208	test: 122474.8676576	best: 122474.8676576 (806)	total: 4.47s	remaining: 50.9s
    807:	learn: 97717.3233258	test: 122464.0588520	best: 122464.0588520 (807)	total: 4.47s	remaining: 50.9s
    808:	learn: 97690.2653838	test: 122459.1998169	best: 122459.1998169 (808)	total: 4.48s	remaining: 50.9s
    809:	learn: 97666.7828573	test: 122446.6966500	best: 122446.6966500 (809)	total: 4.48s	remaining: 50.9s
    810:	learn: 97633.2781441	test: 122423.8270845	best: 122423.8270845 (810)	total: 4.49s	remaining: 50.9s
    811:	learn: 97611.3169919	test: 122420.0696576	best: 122420.0696576 (811)	total: 4.5s	remaining: 50.9s
    812:	learn: 97589.5929556	test: 122413.1459720	best: 122413.1459720 (812)	total: 4.5s	remaining: 50.9s
    813:	learn: 97567.7463425	test: 122414.8956426	best: 122413.1459720 (812)	total: 4.51s	remaining: 50.9s
    814:	learn: 97538.3698255	test: 122402.5662443	best: 122402.5662443 (814)	total: 4.51s	remaining: 50.9s
    815:	learn: 97520.3500382	test: 122393.6318822	best: 122393.6318822 (815)	total: 4.52s	remaining: 50.9s
    816:	learn: 97490.3222231	test: 122386.0958382	best: 122386.0958382 (816)	total: 4.53s	remaining: 50.9s
    817:	learn: 97452.9369438	test: 122359.1426136	best: 122359.1426136 (817)	total: 4.53s	remaining: 50.9s
    818:	learn: 97430.2597375	test: 122348.6366820	best: 122348.6366820 (818)	total: 4.54s	remaining: 50.9s
    819:	learn: 97399.8595803	test: 122352.2278435	best: 122348.6366820 (818)	total: 4.54s	remaining: 50.9s
    820:	learn: 97379.9876647	test: 122335.7175954	best: 122335.7175954 (820)	total: 4.55s	remaining: 50.9s
    821:	learn: 97346.6923339	test: 122342.4902872	best: 122335.7175954 (820)	total: 4.55s	remaining: 50.9s
    822:	learn: 97319.6711244	test: 122334.7203555	best: 122334.7203555 (822)	total: 4.56s	remaining: 50.9s
    823:	learn: 97296.9694792	test: 122331.4605803	best: 122331.4605803 (823)	total: 4.57s	remaining: 50.9s
    824:	learn: 97268.9606493	test: 122309.5440578	best: 122309.5440578 (824)	total: 4.57s	remaining: 50.9s
    825:	learn: 97250.8359121	test: 122305.5414283	best: 122305.5414283 (825)	total: 4.58s	remaining: 50.9s
    826:	learn: 97235.5928620	test: 122305.0456638	best: 122305.0456638 (826)	total: 4.58s	remaining: 50.9s
    827:	learn: 97207.1139365	test: 122291.2179796	best: 122291.2179796 (827)	total: 4.59s	remaining: 50.9s
    828:	learn: 97186.6437973	test: 122282.6105216	best: 122282.6105216 (828)	total: 4.6s	remaining: 50.9s
    829:	learn: 97168.8207213	test: 122281.2435756	best: 122281.2435756 (829)	total: 4.6s	remaining: 50.9s
    830:	learn: 97139.6688854	test: 122285.1794847	best: 122281.2435756 (829)	total: 4.61s	remaining: 50.8s
    831:	learn: 97115.1761335	test: 122279.2960233	best: 122279.2960233 (831)	total: 4.61s	remaining: 50.8s
    832:	learn: 97098.2328258	test: 122271.7490197	best: 122271.7490197 (832)	total: 4.62s	remaining: 50.8s
    833:	learn: 97074.4692405	test: 122266.2204899	best: 122266.2204899 (833)	total: 4.62s	remaining: 50.8s
    834:	learn: 97053.9268632	test: 122252.7513563	best: 122252.7513563 (834)	total: 4.63s	remaining: 50.8s
    835:	learn: 97032.9890380	test: 122251.4218802	best: 122251.4218802 (835)	total: 4.63s	remaining: 50.8s
    836:	learn: 97016.8625862	test: 122242.1457205	best: 122242.1457205 (836)	total: 4.64s	remaining: 50.8s
    837:	learn: 96990.8459520	test: 122228.5848314	best: 122228.5848314 (837)	total: 4.65s	remaining: 50.8s
    838:	learn: 96966.2858936	test: 122220.7008397	best: 122220.7008397 (838)	total: 4.65s	remaining: 50.8s
    839:	learn: 96921.0500682	test: 122183.2607143	best: 122183.2607143 (839)	total: 4.66s	remaining: 50.8s
    840:	learn: 96884.9660201	test: 122162.0516017	best: 122162.0516017 (840)	total: 4.66s	remaining: 50.8s
    841:	learn: 96858.0821037	test: 122158.7981998	best: 122158.7981998 (841)	total: 4.67s	remaining: 50.8s
    842:	learn: 96833.1738896	test: 122171.1827045	best: 122158.7981998 (841)	total: 4.67s	remaining: 50.8s
    843:	learn: 96818.9188775	test: 122161.5621437	best: 122158.7981998 (841)	total: 4.68s	remaining: 50.8s
    844:	learn: 96787.6740282	test: 122140.3390371	best: 122140.3390371 (844)	total: 4.69s	remaining: 50.8s
    845:	learn: 96767.6042156	test: 122127.1355641	best: 122127.1355641 (845)	total: 4.69s	remaining: 50.8s
    846:	learn: 96744.9419282	test: 122110.9677689	best: 122110.9677689 (846)	total: 4.7s	remaining: 50.8s
    847:	learn: 96723.7670582	test: 122111.3556034	best: 122110.9677689 (846)	total: 4.7s	remaining: 50.8s
    848:	learn: 96688.3051491	test: 122084.1921006	best: 122084.1921006 (848)	total: 4.71s	remaining: 50.8s
    849:	learn: 96663.0981219	test: 122072.6989833	best: 122072.6989833 (849)	total: 4.71s	remaining: 50.8s
    850:	learn: 96632.5636343	test: 122055.5928923	best: 122055.5928923 (850)	total: 4.72s	remaining: 50.8s
    851:	learn: 96615.8881135	test: 122052.2177970	best: 122052.2177970 (851)	total: 4.73s	remaining: 50.8s
    852:	learn: 96596.7265271	test: 122043.5811377	best: 122043.5811377 (852)	total: 4.73s	remaining: 50.7s
    853:	learn: 96547.2321898	test: 122008.3246916	best: 122008.3246916 (853)	total: 4.74s	remaining: 50.7s
    854:	learn: 96529.6000809	test: 122002.3728978	best: 122002.3728978 (854)	total: 4.74s	remaining: 50.7s
    855:	learn: 96509.7481981	test: 121994.0237018	best: 121994.0237018 (855)	total: 4.75s	remaining: 50.7s
    856:	learn: 96482.4715413	test: 121983.4062415	best: 121983.4062415 (856)	total: 4.76s	remaining: 50.7s
    857:	learn: 96456.3038428	test: 121962.2518957	best: 121962.2518957 (857)	total: 4.76s	remaining: 50.7s
    858:	learn: 96435.7657483	test: 121947.3915820	best: 121947.3915820 (858)	total: 4.77s	remaining: 50.7s
    859:	learn: 96398.1305773	test: 121911.1904239	best: 121911.1904239 (859)	total: 4.77s	remaining: 50.7s
    860:	learn: 96373.8960025	test: 121888.0647317	best: 121888.0647317 (860)	total: 4.78s	remaining: 50.7s
    861:	learn: 96348.6692557	test: 121874.2900252	best: 121874.2900252 (861)	total: 4.8s	remaining: 50.9s
    862:	learn: 96315.0480345	test: 121854.2347369	best: 121854.2347369 (862)	total: 4.8s	remaining: 50.8s
    863:	learn: 96285.8822013	test: 121832.9458880	best: 121832.9458880 (863)	total: 4.81s	remaining: 50.8s
    864:	learn: 96248.8781519	test: 121815.4892199	best: 121815.4892199 (864)	total: 4.81s	remaining: 50.8s
    865:	learn: 96229.1941299	test: 121810.6266288	best: 121810.6266288 (865)	total: 4.82s	remaining: 50.8s
    866:	learn: 96202.4809294	test: 121799.9007295	best: 121799.9007295 (866)	total: 4.82s	remaining: 50.8s
    867:	learn: 96183.8596767	test: 121778.8534559	best: 121778.8534559 (867)	total: 4.83s	remaining: 50.8s
    868:	learn: 96158.8140686	test: 121780.2713239	best: 121778.8534559 (867)	total: 4.83s	remaining: 50.8s
    869:	learn: 96150.1219178	test: 121782.5927603	best: 121778.8534559 (867)	total: 4.84s	remaining: 50.8s
    870:	learn: 96117.0896119	test: 121740.8214645	best: 121740.8214645 (870)	total: 4.85s	remaining: 50.8s
    871:	learn: 96096.5933900	test: 121739.3186857	best: 121739.3186857 (871)	total: 4.85s	remaining: 50.8s
    872:	learn: 96071.1817812	test: 121733.0620506	best: 121733.0620506 (872)	total: 4.86s	remaining: 50.8s
    873:	learn: 96046.5124792	test: 121730.1076930	best: 121730.1076930 (873)	total: 4.87s	remaining: 50.8s
    874:	learn: 96023.1931297	test: 121711.5920280	best: 121711.5920280 (874)	total: 4.87s	remaining: 50.8s
    875:	learn: 96000.1055458	test: 121724.0245575	best: 121711.5920280 (874)	total: 4.88s	remaining: 50.8s
    876:	learn: 95978.3456981	test: 121726.3561269	best: 121711.5920280 (874)	total: 4.88s	remaining: 50.8s
    877:	learn: 95953.0813659	test: 121720.5860402	best: 121711.5920280 (874)	total: 4.89s	remaining: 50.8s
    878:	learn: 95928.8911857	test: 121702.3980981	best: 121702.3980981 (878)	total: 4.89s	remaining: 50.8s
    879:	learn: 95912.5701612	test: 121701.4163326	best: 121701.4163326 (879)	total: 4.9s	remaining: 50.8s
    880:	learn: 95893.9966077	test: 121697.0751484	best: 121697.0751484 (880)	total: 4.91s	remaining: 50.8s
    881:	learn: 95885.5781997	test: 121699.4808173	best: 121697.0751484 (880)	total: 4.91s	remaining: 50.8s
    882:	learn: 95850.0411526	test: 121683.8407528	best: 121683.8407528 (882)	total: 4.92s	remaining: 50.8s
    883:	learn: 95832.6129154	test: 121683.8650774	best: 121683.8407528 (882)	total: 4.92s	remaining: 50.8s
    884:	learn: 95816.6049851	test: 121683.6226088	best: 121683.6226088 (884)	total: 4.93s	remaining: 50.8s
    885:	learn: 95800.8212611	test: 121680.7600787	best: 121680.7600787 (885)	total: 4.93s	remaining: 50.8s
    886:	learn: 95777.0106622	test: 121670.0671093	best: 121670.0671093 (886)	total: 4.94s	remaining: 50.8s
    887:	learn: 95753.6781681	test: 121657.8787034	best: 121657.8787034 (887)	total: 4.95s	remaining: 50.8s
    888:	learn: 95729.2152516	test: 121643.1651507	best: 121643.1651507 (888)	total: 4.95s	remaining: 50.8s
    889:	learn: 95710.0995795	test: 121636.0846221	best: 121636.0846221 (889)	total: 4.96s	remaining: 50.8s
    890:	learn: 95690.4300668	test: 121626.9663897	best: 121626.9663897 (890)	total: 4.96s	remaining: 50.8s
    891:	learn: 95677.8088259	test: 121621.6076691	best: 121621.6076691 (891)	total: 4.97s	remaining: 50.8s
    892:	learn: 95651.4116059	test: 121605.1551997	best: 121605.1551997 (892)	total: 4.98s	remaining: 50.8s
    893:	learn: 95625.9186581	test: 121585.3093328	best: 121585.3093328 (893)	total: 4.98s	remaining: 50.7s
    894:	learn: 95598.4456077	test: 121571.7699965	best: 121571.7699965 (894)	total: 4.99s	remaining: 50.7s
    895:	learn: 95570.8687955	test: 121565.8419551	best: 121565.8419551 (895)	total: 4.99s	remaining: 50.7s
    896:	learn: 95536.8375161	test: 121538.6904739	best: 121538.6904739 (896)	total: 5s	remaining: 50.7s
    897:	learn: 95518.2318103	test: 121532.0125622	best: 121532.0125622 (897)	total: 5s	remaining: 50.7s
    898:	learn: 95491.7532283	test: 121523.8721295	best: 121523.8721295 (898)	total: 5.01s	remaining: 50.7s
    899:	learn: 95471.7361076	test: 121524.1889594	best: 121523.8721295 (898)	total: 5.02s	remaining: 50.7s
    900:	learn: 95446.9925613	test: 121526.1348021	best: 121523.8721295 (898)	total: 5.02s	remaining: 50.7s
    901:	learn: 95417.5632233	test: 121522.2777321	best: 121522.2777321 (901)	total: 5.03s	remaining: 50.7s
    902:	learn: 95400.8080140	test: 121536.6462714	best: 121522.2777321 (901)	total: 5.04s	remaining: 50.7s
    903:	learn: 95365.2447649	test: 121511.4099144	best: 121511.4099144 (903)	total: 5.04s	remaining: 50.7s
    904:	learn: 95350.8087872	test: 121503.6412870	best: 121503.6412870 (904)	total: 5.05s	remaining: 50.7s
    905:	learn: 95326.1790505	test: 121493.6097228	best: 121493.6097228 (905)	total: 5.05s	remaining: 50.7s
    906:	learn: 95303.2075414	test: 121490.6699972	best: 121490.6699972 (906)	total: 5.06s	remaining: 50.7s
    907:	learn: 95288.3364811	test: 121488.1797717	best: 121488.1797717 (907)	total: 5.07s	remaining: 50.7s
    908:	learn: 95275.2724684	test: 121482.2112368	best: 121482.2112368 (908)	total: 5.07s	remaining: 50.7s
    909:	learn: 95258.3233888	test: 121466.7750565	best: 121466.7750565 (909)	total: 5.08s	remaining: 50.7s
    910:	learn: 95243.6469728	test: 121461.4357390	best: 121461.4357390 (910)	total: 5.08s	remaining: 50.7s
    911:	learn: 95219.9420665	test: 121457.9520343	best: 121457.9520343 (911)	total: 5.09s	remaining: 50.7s
    912:	learn: 95194.9698854	test: 121447.9090385	best: 121447.9090385 (912)	total: 5.09s	remaining: 50.7s
    913:	learn: 95177.0861610	test: 121436.4068067	best: 121436.4068067 (913)	total: 5.1s	remaining: 50.7s
    914:	learn: 95142.7825988	test: 121420.5773812	best: 121420.5773812 (914)	total: 5.11s	remaining: 50.7s
    915:	learn: 95114.5043197	test: 121409.0734143	best: 121409.0734143 (915)	total: 5.11s	remaining: 50.7s
    916:	learn: 95094.3324802	test: 121399.7385876	best: 121399.7385876 (916)	total: 5.12s	remaining: 50.7s
    917:	learn: 95075.0796199	test: 121400.8163717	best: 121399.7385876 (916)	total: 5.13s	remaining: 50.7s
    918:	learn: 95056.0911003	test: 121401.4163755	best: 121399.7385876 (916)	total: 5.13s	remaining: 50.7s
    919:	learn: 95038.3703516	test: 121391.9873929	best: 121391.9873929 (919)	total: 5.14s	remaining: 50.7s
    920:	learn: 95025.4058527	test: 121377.7391635	best: 121377.7391635 (920)	total: 5.15s	remaining: 50.7s
    921:	learn: 95005.6074868	test: 121365.8854105	best: 121365.8854105 (921)	total: 5.15s	remaining: 50.7s
    922:	learn: 94981.9245659	test: 121350.8419891	best: 121350.8419891 (922)	total: 5.16s	remaining: 50.7s
    923:	learn: 94953.0479794	test: 121324.6094051	best: 121324.6094051 (923)	total: 5.17s	remaining: 50.8s
    924:	learn: 94926.1930415	test: 121326.7787938	best: 121324.6094051 (923)	total: 5.17s	remaining: 50.8s
    925:	learn: 94910.3193065	test: 121323.1516503	best: 121323.1516503 (925)	total: 5.18s	remaining: 50.8s
    926:	learn: 94884.3784853	test: 121325.5383822	best: 121323.1516503 (925)	total: 5.19s	remaining: 50.8s
    927:	learn: 94858.6754254	test: 121321.5233092	best: 121321.5233092 (927)	total: 5.19s	remaining: 50.8s
    928:	learn: 94838.8064814	test: 121330.9289500	best: 121321.5233092 (927)	total: 5.2s	remaining: 50.8s
    929:	learn: 94822.8573127	test: 121320.1886799	best: 121320.1886799 (929)	total: 5.21s	remaining: 50.8s
    930:	learn: 94806.9831717	test: 121311.1358917	best: 121311.1358917 (930)	total: 5.21s	remaining: 50.8s
    931:	learn: 94792.7518921	test: 121308.8233774	best: 121308.8233774 (931)	total: 5.22s	remaining: 50.8s
    932:	learn: 94767.7658770	test: 121301.7054948	best: 121301.7054948 (932)	total: 5.23s	remaining: 50.8s
    933:	learn: 94745.7957730	test: 121294.7585453	best: 121294.7585453 (933)	total: 5.23s	remaining: 50.8s
    934:	learn: 94724.2741184	test: 121289.5279765	best: 121289.5279765 (934)	total: 5.24s	remaining: 50.8s
    935:	learn: 94710.4487279	test: 121287.4283733	best: 121287.4283733 (935)	total: 5.25s	remaining: 50.8s
    936:	learn: 94679.4111860	test: 121291.7621024	best: 121287.4283733 (935)	total: 5.25s	remaining: 50.8s
    937:	learn: 94654.5369212	test: 121285.1838473	best: 121285.1838473 (937)	total: 5.26s	remaining: 50.8s
    938:	learn: 94631.3141479	test: 121267.0767766	best: 121267.0767766 (938)	total: 5.26s	remaining: 50.8s
    939:	learn: 94604.2796814	test: 121250.4169200	best: 121250.4169200 (939)	total: 5.27s	remaining: 50.8s
    940:	learn: 94577.0342954	test: 121236.3611952	best: 121236.3611952 (940)	total: 5.28s	remaining: 50.8s
    941:	learn: 94552.3035878	test: 121234.5792993	best: 121234.5792993 (941)	total: 5.28s	remaining: 50.8s
    942:	learn: 94525.4255624	test: 121219.6495318	best: 121219.6495318 (942)	total: 5.29s	remaining: 50.8s
    943:	learn: 94510.6608389	test: 121219.8833829	best: 121219.6495318 (942)	total: 5.29s	remaining: 50.8s
    944:	learn: 94482.9278212	test: 121223.6999988	best: 121219.6495318 (942)	total: 5.3s	remaining: 50.8s
    945:	learn: 94451.7478634	test: 121208.3210488	best: 121208.3210488 (945)	total: 5.31s	remaining: 50.8s
    946:	learn: 94437.8451119	test: 121204.6738863	best: 121204.6738863 (946)	total: 5.31s	remaining: 50.8s
    947:	learn: 94411.5630925	test: 121190.8415420	best: 121190.8415420 (947)	total: 5.32s	remaining: 50.8s
    948:	learn: 94396.6763464	test: 121185.9811275	best: 121185.9811275 (948)	total: 5.32s	remaining: 50.8s
    949:	learn: 94366.8061025	test: 121164.1858441	best: 121164.1858441 (949)	total: 5.33s	remaining: 50.8s
    950:	learn: 94344.2757753	test: 121143.3870130	best: 121143.3870130 (950)	total: 5.34s	remaining: 50.8s
    951:	learn: 94325.3423217	test: 121152.3454547	best: 121143.3870130 (950)	total: 5.34s	remaining: 50.8s
    952:	learn: 94301.7652268	test: 121137.1865948	best: 121137.1865948 (952)	total: 5.35s	remaining: 50.8s
    953:	learn: 94280.0306454	test: 121127.9505902	best: 121127.9505902 (953)	total: 5.36s	remaining: 50.8s
    954:	learn: 94258.3339372	test: 121116.8084138	best: 121116.8084138 (954)	total: 5.36s	remaining: 50.8s
    955:	learn: 94234.3851833	test: 121114.3752863	best: 121114.3752863 (955)	total: 5.37s	remaining: 50.8s
    956:	learn: 94211.2335711	test: 121108.4656035	best: 121108.4656035 (956)	total: 5.37s	remaining: 50.8s
    957:	learn: 94185.5580951	test: 121099.5702311	best: 121099.5702311 (957)	total: 5.38s	remaining: 50.8s
    958:	learn: 94159.8319435	test: 121082.4449039	best: 121082.4449039 (958)	total: 5.39s	remaining: 50.8s
    959:	learn: 94124.1321713	test: 121053.0075807	best: 121053.0075807 (959)	total: 5.39s	remaining: 50.8s
    960:	learn: 94113.3867503	test: 121044.5940078	best: 121044.5940078 (960)	total: 5.4s	remaining: 50.8s
    961:	learn: 94096.9674331	test: 121026.3615234	best: 121026.3615234 (961)	total: 5.4s	remaining: 50.8s
    962:	learn: 94076.9370659	test: 121028.0306305	best: 121026.3615234 (961)	total: 5.41s	remaining: 50.8s
    963:	learn: 94061.6001241	test: 121027.1912467	best: 121026.3615234 (961)	total: 5.41s	remaining: 50.8s
    964:	learn: 94046.8144578	test: 121017.3411942	best: 121017.3411942 (964)	total: 5.42s	remaining: 50.8s
    965:	learn: 94006.3277491	test: 120987.0021843	best: 120987.0021843 (965)	total: 5.43s	remaining: 50.8s
    966:	learn: 93985.2116653	test: 120982.0162026	best: 120982.0162026 (966)	total: 5.43s	remaining: 50.8s
    967:	learn: 93935.3701713	test: 120945.7064867	best: 120945.7064867 (967)	total: 5.44s	remaining: 50.7s
    968:	learn: 93921.6025397	test: 120946.4762750	best: 120945.7064867 (967)	total: 5.44s	remaining: 50.7s
    969:	learn: 93908.5895998	test: 120942.0798005	best: 120942.0798005 (969)	total: 5.45s	remaining: 50.7s
    970:	learn: 93886.5968086	test: 120938.2629250	best: 120938.2629250 (970)	total: 5.46s	remaining: 50.7s
    971:	learn: 93865.6564855	test: 120930.0987396	best: 120930.0987396 (971)	total: 5.46s	remaining: 50.7s
    972:	learn: 93843.6420684	test: 120926.1126462	best: 120926.1126462 (972)	total: 5.47s	remaining: 50.7s
    973:	learn: 93795.6007746	test: 120891.1405551	best: 120891.1405551 (973)	total: 5.47s	remaining: 50.7s
    974:	learn: 93755.3248356	test: 120856.4781505	best: 120856.4781505 (974)	total: 5.48s	remaining: 50.7s
    975:	learn: 93739.6438833	test: 120838.8167974	best: 120838.8167974 (975)	total: 5.48s	remaining: 50.7s
    976:	learn: 93723.1153440	test: 120838.7506986	best: 120838.7506986 (976)	total: 5.49s	remaining: 50.7s
    977:	learn: 93703.7998018	test: 120835.3334105	best: 120835.3334105 (977)	total: 5.5s	remaining: 50.7s
    978:	learn: 93687.8690848	test: 120822.3712869	best: 120822.3712869 (978)	total: 5.5s	remaining: 50.7s
    979:	learn: 93670.4538322	test: 120811.1981785	best: 120811.1981785 (979)	total: 5.51s	remaining: 50.7s
    980:	learn: 93661.1312688	test: 120807.0308524	best: 120807.0308524 (980)	total: 5.51s	remaining: 50.7s
    981:	learn: 93641.9088827	test: 120805.4073080	best: 120805.4073080 (981)	total: 5.52s	remaining: 50.7s
    982:	learn: 93620.3538957	test: 120799.5617465	best: 120799.5617465 (982)	total: 5.52s	remaining: 50.7s
    983:	learn: 93597.5428161	test: 120796.6768621	best: 120796.6768621 (983)	total: 5.53s	remaining: 50.7s
    984:	learn: 93574.3798368	test: 120791.0308868	best: 120791.0308868 (984)	total: 5.53s	remaining: 50.7s
    985:	learn: 93562.5779921	test: 120789.1998064	best: 120789.1998064 (985)	total: 5.54s	remaining: 50.7s
    986:	learn: 93531.9176820	test: 120769.4822306	best: 120769.4822306 (986)	total: 5.55s	remaining: 50.7s
    987:	learn: 93519.6665159	test: 120763.9051120	best: 120763.9051120 (987)	total: 5.55s	remaining: 50.7s
    988:	learn: 93504.3742033	test: 120754.2561851	best: 120754.2561851 (988)	total: 5.56s	remaining: 50.6s
    989:	learn: 93479.6310732	test: 120747.8956578	best: 120747.8956578 (989)	total: 5.56s	remaining: 50.6s
    990:	learn: 93457.6569338	test: 120736.7031891	best: 120736.7031891 (990)	total: 5.57s	remaining: 50.6s
    991:	learn: 93440.9087309	test: 120726.0002756	best: 120726.0002756 (991)	total: 5.58s	remaining: 50.6s
    992:	learn: 93418.7045394	test: 120717.6406011	best: 120717.6406011 (992)	total: 5.58s	remaining: 50.6s
    993:	learn: 93392.8564483	test: 120721.9654604	best: 120717.6406011 (992)	total: 5.59s	remaining: 50.6s
    994:	learn: 93374.9814470	test: 120717.5854201	best: 120717.5854201 (994)	total: 5.59s	remaining: 50.6s
    995:	learn: 93353.4529707	test: 120708.7562955	best: 120708.7562955 (995)	total: 5.6s	remaining: 50.6s
    996:	learn: 93332.2412945	test: 120703.3889190	best: 120703.3889190 (996)	total: 5.6s	remaining: 50.6s
    997:	learn: 93318.7001659	test: 120698.8798902	best: 120698.8798902 (997)	total: 5.61s	remaining: 50.6s
    998:	learn: 93302.8237767	test: 120694.2443140	best: 120694.2443140 (998)	total: 5.61s	remaining: 50.6s
    999:	learn: 93290.2134631	test: 120692.6799485	best: 120692.6799485 (999)	total: 5.62s	remaining: 50.6s
    1000:	learn: 93271.9982437	test: 120699.2647434	best: 120692.6799485 (999)	total: 5.62s	remaining: 50.6s
    1001:	learn: 93243.6584536	test: 120678.1853222	best: 120678.1853222 (1001)	total: 5.63s	remaining: 50.6s
    1002:	learn: 93225.1156571	test: 120668.9498209	best: 120668.9498209 (1002)	total: 5.63s	remaining: 50.5s
    1003:	learn: 93204.8228687	test: 120655.8028461	best: 120655.8028461 (1003)	total: 5.64s	remaining: 50.5s
    1004:	learn: 93188.2129523	test: 120657.8681152	best: 120655.8028461 (1003)	total: 5.64s	remaining: 50.5s
    1005:	learn: 93172.9175865	test: 120643.7037529	best: 120643.7037529 (1005)	total: 5.65s	remaining: 50.5s
    1006:	learn: 93160.2477576	test: 120640.6063837	best: 120640.6063837 (1006)	total: 5.66s	remaining: 50.5s
    1007:	learn: 93139.2366990	test: 120631.6448482	best: 120631.6448482 (1007)	total: 5.66s	remaining: 50.5s
    1008:	learn: 93123.5991652	test: 120631.7785514	best: 120631.6448482 (1007)	total: 5.67s	remaining: 50.5s
    1009:	learn: 93099.9518742	test: 120629.5440896	best: 120629.5440896 (1009)	total: 5.67s	remaining: 50.5s
    1010:	learn: 93071.3943587	test: 120609.0246962	best: 120609.0246962 (1010)	total: 5.68s	remaining: 50.5s
    1011:	learn: 93056.0701959	test: 120588.4648544	best: 120588.4648544 (1011)	total: 5.68s	remaining: 50.5s
    1012:	learn: 93030.9501045	test: 120575.5039188	best: 120575.5039188 (1012)	total: 5.69s	remaining: 50.5s
    1013:	learn: 93002.1804198	test: 120557.4269648	best: 120557.4269648 (1013)	total: 5.7s	remaining: 50.5s
    1014:	learn: 92981.1870972	test: 120543.2722388	best: 120543.2722388 (1014)	total: 5.7s	remaining: 50.5s
    1015:	learn: 92959.7986605	test: 120531.6905794	best: 120531.6905794 (1015)	total: 5.71s	remaining: 50.5s
    1016:	learn: 92935.0776433	test: 120536.1345408	best: 120531.6905794 (1015)	total: 5.71s	remaining: 50.5s
    1017:	learn: 92899.2826137	test: 120511.9892307	best: 120511.9892307 (1017)	total: 5.72s	remaining: 50.5s
    1018:	learn: 92875.8865171	test: 120511.9559718	best: 120511.9559718 (1018)	total: 5.72s	remaining: 50.5s
    1019:	learn: 92855.4461168	test: 120508.4183002	best: 120508.4183002 (1019)	total: 5.73s	remaining: 50.5s
    1020:	learn: 92834.3409756	test: 120513.3901828	best: 120508.4183002 (1019)	total: 5.74s	remaining: 50.5s
    1021:	learn: 92824.3289167	test: 120509.6501797	best: 120508.4183002 (1019)	total: 5.74s	remaining: 50.5s
    1022:	learn: 92798.2406402	test: 120491.6341471	best: 120491.6341471 (1022)	total: 5.75s	remaining: 50.5s
    1023:	learn: 92776.6743497	test: 120478.6457384	best: 120478.6457384 (1023)	total: 5.75s	remaining: 50.5s
    1024:	learn: 92751.2913463	test: 120466.0121417	best: 120466.0121417 (1024)	total: 5.76s	remaining: 50.5s
    1025:	learn: 92701.9916320	test: 120427.4584793	best: 120427.4584793 (1025)	total: 5.77s	remaining: 50.5s
    1026:	learn: 92673.5933031	test: 120407.2128831	best: 120407.2128831 (1026)	total: 5.78s	remaining: 50.5s
    1027:	learn: 92651.2547965	test: 120408.4882612	best: 120407.2128831 (1026)	total: 5.78s	remaining: 50.5s
    1028:	learn: 92636.7496367	test: 120404.5352856	best: 120404.5352856 (1028)	total: 5.79s	remaining: 50.5s
    1029:	learn: 92609.0660398	test: 120384.6044697	best: 120384.6044697 (1029)	total: 5.79s	remaining: 50.5s
    1030:	learn: 92578.4231759	test: 120367.0120629	best: 120367.0120629 (1030)	total: 5.8s	remaining: 50.5s
    1031:	learn: 92557.7934385	test: 120358.2025649	best: 120358.2025649 (1031)	total: 5.81s	remaining: 50.5s
    1032:	learn: 92532.2607187	test: 120338.5933504	best: 120338.5933504 (1032)	total: 5.81s	remaining: 50.5s
    1033:	learn: 92508.6478973	test: 120334.8992597	best: 120334.8992597 (1033)	total: 5.82s	remaining: 50.5s
    1034:	learn: 92486.7299218	test: 120322.4995953	best: 120322.4995953 (1034)	total: 5.83s	remaining: 50.5s
    1035:	learn: 92471.3477784	test: 120323.0428541	best: 120322.4995953 (1034)	total: 5.83s	remaining: 50.5s
    1036:	learn: 92455.5002295	test: 120311.7594598	best: 120311.7594598 (1036)	total: 5.84s	remaining: 50.5s
    1037:	learn: 92428.0802739	test: 120300.9689787	best: 120300.9689787 (1037)	total: 5.85s	remaining: 50.5s
    1038:	learn: 92404.7204994	test: 120291.2907920	best: 120291.2907920 (1038)	total: 5.85s	remaining: 50.5s
    1039:	learn: 92392.6481777	test: 120284.8045715	best: 120284.8045715 (1039)	total: 5.86s	remaining: 50.5s
    1040:	learn: 92369.4637645	test: 120278.9908191	best: 120278.9908191 (1040)	total: 5.87s	remaining: 50.5s
    1041:	learn: 92352.4209972	test: 120282.8621636	best: 120278.9908191 (1040)	total: 5.87s	remaining: 50.5s
    1042:	learn: 92337.1911517	test: 120271.9464205	best: 120271.9464205 (1042)	total: 5.88s	remaining: 50.5s
    1043:	learn: 92313.0158206	test: 120257.3971746	best: 120257.3971746 (1043)	total: 5.88s	remaining: 50.5s
    1044:	learn: 92297.4311269	test: 120247.5161088	best: 120247.5161088 (1044)	total: 5.89s	remaining: 50.5s
    1045:	learn: 92268.9884400	test: 120238.5636666	best: 120238.5636666 (1045)	total: 5.9s	remaining: 50.5s
    1046:	learn: 92233.2692550	test: 120198.2232892	best: 120198.2232892 (1046)	total: 5.91s	remaining: 50.5s
    1047:	learn: 92221.1015442	test: 120193.9269033	best: 120193.9269033 (1047)	total: 5.91s	remaining: 50.5s
    1048:	learn: 92198.2160861	test: 120187.5302010	best: 120187.5302010 (1048)	total: 5.92s	remaining: 50.5s
    1049:	learn: 92189.4302505	test: 120190.8893644	best: 120187.5302010 (1048)	total: 5.92s	remaining: 50.5s
    1050:	learn: 92163.5083378	test: 120190.9423255	best: 120187.5302010 (1048)	total: 5.93s	remaining: 50.5s
    1051:	learn: 92148.7060559	test: 120206.1964448	best: 120187.5302010 (1048)	total: 5.93s	remaining: 50.5s
    1052:	learn: 92127.2493824	test: 120193.6558434	best: 120187.5302010 (1048)	total: 5.94s	remaining: 50.5s
    1053:	learn: 92103.8673059	test: 120179.6635562	best: 120179.6635562 (1053)	total: 5.95s	remaining: 50.5s
    1054:	learn: 92080.8173508	test: 120174.5495769	best: 120174.5495769 (1054)	total: 5.95s	remaining: 50.5s
    1055:	learn: 92065.4086712	test: 120176.8310866	best: 120174.5495769 (1054)	total: 5.96s	remaining: 50.5s
    1056:	learn: 92034.6123886	test: 120158.5726449	best: 120158.5726449 (1056)	total: 5.97s	remaining: 50.5s
    1057:	learn: 92028.7646422	test: 120155.5271029	best: 120155.5271029 (1057)	total: 5.97s	remaining: 50.5s
    1058:	learn: 92010.7031471	test: 120146.7346072	best: 120146.7346072 (1058)	total: 5.98s	remaining: 50.5s
    1059:	learn: 91986.8471180	test: 120127.9242538	best: 120127.9242538 (1059)	total: 5.99s	remaining: 50.5s
    1060:	learn: 91962.2371934	test: 120130.9641102	best: 120127.9242538 (1059)	total: 5.99s	remaining: 50.5s
    1061:	learn: 91938.1489161	test: 120112.0695924	best: 120112.0695924 (1061)	total: 6s	remaining: 50.5s
    1062:	learn: 91923.2471185	test: 120102.6271200	best: 120102.6271200 (1062)	total: 6s	remaining: 50.5s
    1063:	learn: 91900.7513341	test: 120085.4856725	best: 120085.4856725 (1063)	total: 6.01s	remaining: 50.5s
    1064:	learn: 91879.0458244	test: 120072.4645924	best: 120072.4645924 (1064)	total: 6.02s	remaining: 50.5s
    1065:	learn: 91866.6224822	test: 120066.0604365	best: 120066.0604365 (1065)	total: 6.02s	remaining: 50.5s
    1066:	learn: 91849.7625675	test: 120065.7209601	best: 120065.7209601 (1066)	total: 6.03s	remaining: 50.5s
    1067:	learn: 91819.6753671	test: 120039.3785068	best: 120039.3785068 (1067)	total: 6.03s	remaining: 50.5s
    1068:	learn: 91796.3990750	test: 120022.7838158	best: 120022.7838158 (1068)	total: 6.04s	remaining: 50.5s
    1069:	learn: 91775.4740814	test: 120017.8070263	best: 120017.8070263 (1069)	total: 6.04s	remaining: 50.4s
    1070:	learn: 91741.4184258	test: 119996.4295800	best: 119996.4295800 (1070)	total: 6.05s	remaining: 50.4s
    1071:	learn: 91715.9275887	test: 119991.9501219	best: 119991.9501219 (1071)	total: 6.06s	remaining: 50.4s
    1072:	learn: 91703.1321894	test: 119992.0119167	best: 119991.9501219 (1071)	total: 6.06s	remaining: 50.5s
    1073:	learn: 91686.5672104	test: 119985.4812546	best: 119985.4812546 (1073)	total: 6.07s	remaining: 50.5s
    1074:	learn: 91659.6415229	test: 119977.3236896	best: 119977.3236896 (1074)	total: 6.08s	remaining: 50.5s
    1075:	learn: 91647.6727087	test: 119978.6606586	best: 119977.3236896 (1074)	total: 6.08s	remaining: 50.5s
    1076:	learn: 91624.0449927	test: 119976.5341536	best: 119976.5341536 (1076)	total: 6.09s	remaining: 50.5s
    1077:	learn: 91601.8235489	test: 119970.9095238	best: 119970.9095238 (1077)	total: 6.1s	remaining: 50.5s
    1078:	learn: 91577.3337574	test: 119961.9474015	best: 119961.9474015 (1078)	total: 6.1s	remaining: 50.5s
    1079:	learn: 91563.2537082	test: 119953.3917111	best: 119953.3917111 (1079)	total: 6.11s	remaining: 50.5s
    1080:	learn: 91544.8147828	test: 119944.3530635	best: 119944.3530635 (1080)	total: 6.12s	remaining: 50.5s
    1081:	learn: 91532.3435579	test: 119941.6033682	best: 119941.6033682 (1081)	total: 6.12s	remaining: 50.5s
    1082:	learn: 91512.7097485	test: 119945.1638906	best: 119941.6033682 (1081)	total: 6.13s	remaining: 50.5s
    1083:	learn: 91490.9896978	test: 119938.8657429	best: 119938.8657429 (1083)	total: 6.13s	remaining: 50.5s
    1084:	learn: 91470.6628789	test: 119922.8555594	best: 119922.8555594 (1084)	total: 6.14s	remaining: 50.5s
    1085:	learn: 91448.3930863	test: 119903.9779441	best: 119903.9779441 (1085)	total: 6.15s	remaining: 50.5s
    1086:	learn: 91424.7631295	test: 119892.4933108	best: 119892.4933108 (1086)	total: 6.16s	remaining: 50.5s
    1087:	learn: 91385.4334600	test: 119868.0973795	best: 119868.0973795 (1087)	total: 6.16s	remaining: 50.5s
    1088:	learn: 91365.0236452	test: 119858.1971539	best: 119858.1971539 (1088)	total: 6.17s	remaining: 50.5s
    1089:	learn: 91347.4195264	test: 119846.7651916	best: 119846.7651916 (1089)	total: 6.17s	remaining: 50.5s
    1090:	learn: 91329.9028080	test: 119843.3988627	best: 119843.3988627 (1090)	total: 6.18s	remaining: 50.5s
    1091:	learn: 91312.4963173	test: 119833.2367826	best: 119833.2367826 (1091)	total: 6.18s	remaining: 50.4s
    1092:	learn: 91296.5992478	test: 119843.7261174	best: 119833.2367826 (1091)	total: 6.19s	remaining: 50.4s
    1093:	learn: 91285.0138112	test: 119848.7432648	best: 119833.2367826 (1091)	total: 6.2s	remaining: 50.4s
    1094:	learn: 91260.2578483	test: 119821.6357760	best: 119821.6357760 (1094)	total: 6.2s	remaining: 50.4s
    1095:	learn: 91237.6524230	test: 119810.3944786	best: 119810.3944786 (1095)	total: 6.21s	remaining: 50.4s
    1096:	learn: 91214.7953307	test: 119797.2707072	best: 119797.2707072 (1096)	total: 6.21s	remaining: 50.4s
    1097:	learn: 91199.8594861	test: 119798.3439968	best: 119797.2707072 (1096)	total: 6.22s	remaining: 50.4s
    1098:	learn: 91188.5246278	test: 119796.3311196	best: 119796.3311196 (1098)	total: 6.22s	remaining: 50.4s
    1099:	learn: 91171.1071973	test: 119793.6417793	best: 119793.6417793 (1099)	total: 6.23s	remaining: 50.4s
    1100:	learn: 91129.8859786	test: 119805.3403828	best: 119793.6417793 (1099)	total: 6.24s	remaining: 50.4s
    1101:	learn: 91112.0174063	test: 119799.1411436	best: 119793.6417793 (1099)	total: 6.24s	remaining: 50.4s
    1102:	learn: 91089.8856742	test: 119786.0375738	best: 119786.0375738 (1102)	total: 6.25s	remaining: 50.4s
    1103:	learn: 91070.5214081	test: 119782.0884147	best: 119782.0884147 (1103)	total: 6.25s	remaining: 50.4s
    1104:	learn: 91044.7765174	test: 119775.0872747	best: 119775.0872747 (1104)	total: 6.26s	remaining: 50.4s
    1105:	learn: 91019.5922750	test: 119748.9809200	best: 119748.9809200 (1105)	total: 6.26s	remaining: 50.4s
    1106:	learn: 91006.2834483	test: 119741.2654999	best: 119741.2654999 (1106)	total: 6.27s	remaining: 50.4s
    1107:	learn: 90985.7032757	test: 119734.0644002	best: 119734.0644002 (1107)	total: 6.28s	remaining: 50.4s
    1108:	learn: 90966.9126357	test: 119722.1124886	best: 119722.1124886 (1108)	total: 6.28s	remaining: 50.4s
    1109:	learn: 90946.5734368	test: 119710.0036138	best: 119710.0036138 (1109)	total: 6.29s	remaining: 50.4s
    1110:	learn: 90922.5483000	test: 119715.4240289	best: 119710.0036138 (1109)	total: 6.29s	remaining: 50.3s
    1111:	learn: 90902.0893287	test: 119724.9373390	best: 119710.0036138 (1109)	total: 6.3s	remaining: 50.3s
    1112:	learn: 90893.9261393	test: 119722.1668171	best: 119710.0036138 (1109)	total: 6.3s	remaining: 50.3s
    1113:	learn: 90872.3918491	test: 119711.6296261	best: 119710.0036138 (1109)	total: 6.31s	remaining: 50.3s
    1114:	learn: 90855.3492654	test: 119699.1356741	best: 119699.1356741 (1114)	total: 6.31s	remaining: 50.3s
    1115:	learn: 90846.4401864	test: 119694.2018725	best: 119694.2018725 (1115)	total: 6.32s	remaining: 50.3s
    1116:	learn: 90829.4802237	test: 119672.6750924	best: 119672.6750924 (1116)	total: 6.33s	remaining: 50.3s
    1117:	learn: 90817.6146097	test: 119664.4500345	best: 119664.4500345 (1117)	total: 6.33s	remaining: 50.3s
    1118:	learn: 90797.9848857	test: 119652.6991256	best: 119652.6991256 (1118)	total: 6.34s	remaining: 50.3s
    1119:	learn: 90781.3387956	test: 119649.6901960	best: 119649.6901960 (1119)	total: 6.34s	remaining: 50.3s
    1120:	learn: 90766.4894488	test: 119641.2252155	best: 119641.2252155 (1120)	total: 6.35s	remaining: 50.3s
    1121:	learn: 90752.5988788	test: 119624.0839487	best: 119624.0839487 (1121)	total: 6.35s	remaining: 50.3s
    1122:	learn: 90734.9299696	test: 119615.2018048	best: 119615.2018048 (1122)	total: 6.36s	remaining: 50.2s
    1123:	learn: 90721.1725947	test: 119614.8902836	best: 119614.8902836 (1123)	total: 6.36s	remaining: 50.2s
    1124:	learn: 90699.7996402	test: 119605.3492038	best: 119605.3492038 (1124)	total: 6.37s	remaining: 50.2s
    1125:	learn: 90686.3209882	test: 119588.5473744	best: 119588.5473744 (1125)	total: 6.37s	remaining: 50.2s
    1126:	learn: 90669.1308221	test: 119586.9103437	best: 119586.9103437 (1126)	total: 6.38s	remaining: 50.2s
    1127:	learn: 90657.3397726	test: 119589.6767451	best: 119586.9103437 (1126)	total: 6.38s	remaining: 50.2s
    1128:	learn: 90636.0859819	test: 119588.1617834	best: 119586.9103437 (1126)	total: 6.39s	remaining: 50.2s
    1129:	learn: 90614.3741061	test: 119575.1661971	best: 119575.1661971 (1129)	total: 6.39s	remaining: 50.2s
    1130:	learn: 90593.7223658	test: 119565.1458762	best: 119565.1458762 (1130)	total: 6.4s	remaining: 50.2s
    1131:	learn: 90579.2949003	test: 119560.2341041	best: 119560.2341041 (1131)	total: 6.41s	remaining: 50.2s
    1132:	learn: 90562.6222487	test: 119559.6758060	best: 119559.6758060 (1132)	total: 6.41s	remaining: 50.2s
    1133:	learn: 90529.8850755	test: 119541.6353233	best: 119541.6353233 (1133)	total: 6.42s	remaining: 50.2s
    1134:	learn: 90511.3789212	test: 119546.0289452	best: 119541.6353233 (1133)	total: 6.42s	remaining: 50.2s
    1135:	learn: 90495.4527259	test: 119543.3086720	best: 119541.6353233 (1133)	total: 6.43s	remaining: 50.2s
    1136:	learn: 90483.0361182	test: 119542.9782576	best: 119541.6353233 (1133)	total: 6.43s	remaining: 50.2s
    1137:	learn: 90468.4351080	test: 119531.3409782	best: 119531.3409782 (1137)	total: 6.44s	remaining: 50.2s
    1138:	learn: 90457.8613194	test: 119528.2910422	best: 119528.2910422 (1138)	total: 6.45s	remaining: 50.1s
    1139:	learn: 90440.0316589	test: 119524.9076114	best: 119524.9076114 (1139)	total: 6.45s	remaining: 50.1s
    1140:	learn: 90424.4992738	test: 119520.7340397	best: 119520.7340397 (1140)	total: 6.46s	remaining: 50.1s
    1141:	learn: 90411.2684212	test: 119524.6096701	best: 119520.7340397 (1140)	total: 6.46s	remaining: 50.1s
    1142:	learn: 90381.4727604	test: 119518.8077916	best: 119518.8077916 (1142)	total: 6.47s	remaining: 50.1s
    1143:	learn: 90368.6767027	test: 119517.0371991	best: 119517.0371991 (1143)	total: 6.47s	remaining: 50.1s
    1144:	learn: 90348.7036287	test: 119507.5461433	best: 119507.5461433 (1144)	total: 6.48s	remaining: 50.1s
    1145:	learn: 90336.2627961	test: 119505.8822356	best: 119505.8822356 (1145)	total: 6.49s	remaining: 50.1s
    1146:	learn: 90315.5223754	test: 119494.0768359	best: 119494.0768359 (1146)	total: 6.49s	remaining: 50.1s
    1147:	learn: 90296.2321366	test: 119484.1088301	best: 119484.1088301 (1147)	total: 6.5s	remaining: 50.1s
    1148:	learn: 90279.1415672	test: 119475.5658191	best: 119475.5658191 (1148)	total: 6.5s	remaining: 50.1s
    1149:	learn: 90256.7985310	test: 119459.9678770	best: 119459.9678770 (1149)	total: 6.51s	remaining: 50.1s
    1150:	learn: 90236.0915080	test: 119465.2204496	best: 119459.9678770 (1149)	total: 6.51s	remaining: 50.1s
    1151:	learn: 90221.3455945	test: 119452.8848807	best: 119452.8848807 (1151)	total: 6.52s	remaining: 50.1s
    1152:	learn: 90203.0428880	test: 119446.0982808	best: 119446.0982808 (1152)	total: 6.52s	remaining: 50.1s
    1153:	learn: 90183.7578666	test: 119444.6352117	best: 119444.6352117 (1153)	total: 6.53s	remaining: 50s
    1154:	learn: 90160.4639679	test: 119448.0748816	best: 119444.6352117 (1153)	total: 6.53s	remaining: 50s
    1155:	learn: 90142.2610880	test: 119449.3051525	best: 119444.6352117 (1153)	total: 6.54s	remaining: 50s
    1156:	learn: 90129.3739917	test: 119440.9371449	best: 119440.9371449 (1156)	total: 6.54s	remaining: 50s
    1157:	learn: 90115.5287203	test: 119442.3294769	best: 119440.9371449 (1156)	total: 6.55s	remaining: 50s
    1158:	learn: 90084.0788137	test: 119419.0957132	best: 119419.0957132 (1158)	total: 6.56s	remaining: 50s
    1159:	learn: 90073.4890406	test: 119424.2604702	best: 119419.0957132 (1158)	total: 6.56s	remaining: 50s
    1160:	learn: 90056.3978549	test: 119416.4691392	best: 119416.4691392 (1160)	total: 6.57s	remaining: 50s
    1161:	learn: 90046.8395344	test: 119422.0895956	best: 119416.4691392 (1160)	total: 6.57s	remaining: 50s
    1162:	learn: 90024.5048877	test: 119418.8511775	best: 119416.4691392 (1160)	total: 6.58s	remaining: 50s
    1163:	learn: 90006.1011118	test: 119412.6711985	best: 119412.6711985 (1163)	total: 6.59s	remaining: 50s
    1164:	learn: 89974.1517470	test: 119385.8081331	best: 119385.8081331 (1164)	total: 6.59s	remaining: 50s
    1165:	learn: 89962.1700517	test: 119368.9662312	best: 119368.9662312 (1165)	total: 6.6s	remaining: 50s
    1166:	learn: 89950.0337718	test: 119363.7738768	best: 119363.7738768 (1166)	total: 6.6s	remaining: 50s
    1167:	learn: 89935.5363784	test: 119363.0025732	best: 119363.0025732 (1167)	total: 6.61s	remaining: 50s
    1168:	learn: 89920.6209799	test: 119355.8899765	best: 119355.8899765 (1168)	total: 6.61s	remaining: 50s
    1169:	learn: 89903.5923431	test: 119352.9034799	best: 119352.9034799 (1169)	total: 6.62s	remaining: 50s
    1170:	learn: 89889.1688574	test: 119348.4798011	best: 119348.4798011 (1170)	total: 6.62s	remaining: 49.9s
    1171:	learn: 89877.6765914	test: 119347.4225620	best: 119347.4225620 (1171)	total: 6.63s	remaining: 49.9s
    1172:	learn: 89864.0414192	test: 119342.9312767	best: 119342.9312767 (1172)	total: 6.63s	remaining: 49.9s
    1173:	learn: 89852.1275875	test: 119336.5802986	best: 119336.5802986 (1173)	total: 6.64s	remaining: 49.9s
    1174:	learn: 89831.8051653	test: 119333.4034615	best: 119333.4034615 (1174)	total: 6.65s	remaining: 49.9s
    1175:	learn: 89810.4107505	test: 119317.9279703	best: 119317.9279703 (1175)	total: 6.65s	remaining: 49.9s
    1176:	learn: 89797.0085867	test: 119321.4691231	best: 119317.9279703 (1175)	total: 6.66s	remaining: 49.9s
    1177:	learn: 89775.4635845	test: 119305.0983099	best: 119305.0983099 (1177)	total: 6.66s	remaining: 49.9s
    1178:	learn: 89767.2930487	test: 119301.9434345	best: 119301.9434345 (1178)	total: 6.67s	remaining: 49.9s
    1179:	learn: 89749.2323135	test: 119290.8360548	best: 119290.8360548 (1179)	total: 6.67s	remaining: 49.9s
    1180:	learn: 89736.1210586	test: 119283.3032620	best: 119283.3032620 (1180)	total: 6.68s	remaining: 49.9s
    1181:	learn: 89720.5072393	test: 119281.6018125	best: 119281.6018125 (1181)	total: 6.68s	remaining: 49.9s
    1182:	learn: 89700.6544462	test: 119261.0728549	best: 119261.0728549 (1182)	total: 6.69s	remaining: 49.9s
    1183:	learn: 89687.6952098	test: 119253.0594054	best: 119253.0594054 (1183)	total: 6.7s	remaining: 49.9s
    1184:	learn: 89663.6757713	test: 119246.9373762	best: 119246.9373762 (1184)	total: 6.7s	remaining: 49.8s
    1185:	learn: 89649.2790605	test: 119231.7261109	best: 119231.7261109 (1185)	total: 6.71s	remaining: 49.8s
    1186:	learn: 89636.1697086	test: 119223.7515582	best: 119223.7515582 (1186)	total: 6.71s	remaining: 49.8s
    1187:	learn: 89615.7786521	test: 119213.8816887	best: 119213.8816887 (1187)	total: 6.72s	remaining: 49.8s
    1188:	learn: 89600.1497050	test: 119217.7027826	best: 119213.8816887 (1187)	total: 6.72s	remaining: 49.8s
    1189:	learn: 89580.3932684	test: 119212.2695939	best: 119212.2695939 (1189)	total: 6.73s	remaining: 49.8s
    1190:	learn: 89557.9702454	test: 119219.6123483	best: 119212.2695939 (1189)	total: 6.73s	remaining: 49.8s
    1191:	learn: 89540.5088957	test: 119208.8089957	best: 119208.8089957 (1191)	total: 6.74s	remaining: 49.8s
    1192:	learn: 89521.9736181	test: 119200.1798056	best: 119200.1798056 (1192)	total: 6.75s	remaining: 49.8s
    1193:	learn: 89503.1155606	test: 119192.2609541	best: 119192.2609541 (1193)	total: 6.75s	remaining: 49.8s
    1194:	learn: 89469.4502816	test: 119191.8427395	best: 119191.8427395 (1194)	total: 6.76s	remaining: 49.8s
    1195:	learn: 89443.1140431	test: 119174.4073425	best: 119174.4073425 (1195)	total: 6.77s	remaining: 49.8s
    1196:	learn: 89426.3544592	test: 119155.7758867	best: 119155.7758867 (1196)	total: 6.77s	remaining: 49.8s
    1197:	learn: 89410.7541111	test: 119149.5327694	best: 119149.5327694 (1197)	total: 6.78s	remaining: 49.8s
    1198:	learn: 89396.6308058	test: 119147.2487039	best: 119147.2487039 (1198)	total: 6.78s	remaining: 49.8s
    1199:	learn: 89381.7308916	test: 119141.1570556	best: 119141.1570556 (1199)	total: 6.79s	remaining: 49.8s
    1200:	learn: 89365.8542591	test: 119135.4645449	best: 119135.4645449 (1200)	total: 6.79s	remaining: 49.8s
    1201:	learn: 89354.6955920	test: 119132.7328048	best: 119132.7328048 (1201)	total: 6.8s	remaining: 49.8s
    1202:	learn: 89341.9973602	test: 119118.2269258	best: 119118.2269258 (1202)	total: 6.81s	remaining: 49.8s
    1203:	learn: 89325.4440267	test: 119113.1711584	best: 119113.1711584 (1203)	total: 6.81s	remaining: 49.8s
    1204:	learn: 89304.9765566	test: 119098.5125743	best: 119098.5125743 (1204)	total: 6.82s	remaining: 49.8s
    1205:	learn: 89294.5073061	test: 119100.2841141	best: 119098.5125743 (1204)	total: 6.83s	remaining: 49.8s
    1206:	learn: 89283.3743905	test: 119095.4822697	best: 119095.4822697 (1206)	total: 6.83s	remaining: 49.8s
    1207:	learn: 89264.9899953	test: 119081.3096222	best: 119081.3096222 (1207)	total: 6.83s	remaining: 49.8s
    1208:	learn: 89246.7793445	test: 119080.2463710	best: 119080.2463710 (1208)	total: 6.84s	remaining: 49.7s
    1209:	learn: 89233.2384820	test: 119084.7327579	best: 119080.2463710 (1208)	total: 6.85s	remaining: 49.7s
    1210:	learn: 89200.4710259	test: 119068.3565753	best: 119068.3565753 (1210)	total: 6.85s	remaining: 49.7s
    1211:	learn: 89183.2178522	test: 119077.0782132	best: 119068.3565753 (1210)	total: 6.86s	remaining: 49.7s
    1212:	learn: 89164.8333396	test: 119064.4813282	best: 119064.4813282 (1212)	total: 6.87s	remaining: 49.7s
    1213:	learn: 89152.3014388	test: 119055.6887180	best: 119055.6887180 (1213)	total: 6.87s	remaining: 49.7s
    1214:	learn: 89140.2027044	test: 119069.5402672	best: 119055.6887180 (1213)	total: 6.88s	remaining: 49.7s
    1215:	learn: 89107.9065792	test: 119087.4495347	best: 119055.6887180 (1213)	total: 6.88s	remaining: 49.7s
    1216:	learn: 89089.3674982	test: 119078.9027093	best: 119055.6887180 (1213)	total: 6.89s	remaining: 49.7s
    1217:	learn: 89074.6765591	test: 119072.3489535	best: 119055.6887180 (1213)	total: 6.89s	remaining: 49.7s
    1218:	learn: 89059.6770178	test: 119066.0316788	best: 119055.6887180 (1213)	total: 6.9s	remaining: 49.7s
    1219:	learn: 89043.7452625	test: 119074.1162022	best: 119055.6887180 (1213)	total: 6.91s	remaining: 49.7s
    1220:	learn: 89032.6625885	test: 119069.1459528	best: 119055.6887180 (1213)	total: 6.91s	remaining: 49.7s
    1221:	learn: 89004.3430773	test: 119054.7053338	best: 119054.7053338 (1221)	total: 6.92s	remaining: 49.7s
    1222:	learn: 88978.0676589	test: 119051.8827978	best: 119051.8827978 (1222)	total: 6.93s	remaining: 49.7s
    1223:	learn: 88964.6215702	test: 119047.8458099	best: 119047.8458099 (1223)	total: 6.93s	remaining: 49.7s
    1224:	learn: 88947.2112432	test: 119043.9496741	best: 119043.9496741 (1224)	total: 6.94s	remaining: 49.7s
    1225:	learn: 88934.5458277	test: 119039.7613304	best: 119039.7613304 (1225)	total: 6.94s	remaining: 49.7s
    1226:	learn: 88917.0558942	test: 119037.5567416	best: 119037.5567416 (1226)	total: 6.95s	remaining: 49.7s
    1227:	learn: 88904.3617802	test: 119045.2048356	best: 119037.5567416 (1226)	total: 6.96s	remaining: 49.7s
    1228:	learn: 88881.6476175	test: 119039.5009416	best: 119037.5567416 (1226)	total: 6.96s	remaining: 49.7s
    1229:	learn: 88859.6737832	test: 119032.0530768	best: 119032.0530768 (1229)	total: 6.97s	remaining: 49.7s
    1230:	learn: 88846.7547914	test: 119028.2757818	best: 119028.2757818 (1230)	total: 6.97s	remaining: 49.7s
    1231:	learn: 88829.7571027	test: 119024.7992680	best: 119024.7992680 (1231)	total: 6.98s	remaining: 49.7s
    1232:	learn: 88813.2258471	test: 119012.1777904	best: 119012.1777904 (1232)	total: 6.98s	remaining: 49.7s
    1233:	learn: 88797.9619519	test: 119006.5427569	best: 119006.5427569 (1233)	total: 6.99s	remaining: 49.7s
    1234:	learn: 88781.2185565	test: 119004.7478902	best: 119004.7478902 (1234)	total: 7s	remaining: 49.6s
    1235:	learn: 88766.0810312	test: 119001.4040656	best: 119001.4040656 (1235)	total: 7s	remaining: 49.6s
    1236:	learn: 88746.2660270	test: 119003.8696546	best: 119001.4040656 (1235)	total: 7.01s	remaining: 49.6s
    1237:	learn: 88735.4093469	test: 118997.8376307	best: 118997.8376307 (1237)	total: 7.01s	remaining: 49.6s
    1238:	learn: 88719.4516764	test: 118998.8003459	best: 118997.8376307 (1237)	total: 7.02s	remaining: 49.6s
    1239:	learn: 88706.4543414	test: 119002.0454865	best: 118997.8376307 (1237)	total: 7.03s	remaining: 49.6s
    1240:	learn: 88690.6399136	test: 118999.4034733	best: 118997.8376307 (1237)	total: 7.03s	remaining: 49.6s
    1241:	learn: 88678.1578704	test: 118988.8569514	best: 118988.8569514 (1241)	total: 7.04s	remaining: 49.6s
    1242:	learn: 88661.6686608	test: 118981.7382163	best: 118981.7382163 (1242)	total: 7.04s	remaining: 49.6s
    1243:	learn: 88643.5491303	test: 118977.4634404	best: 118977.4634404 (1243)	total: 7.05s	remaining: 49.6s
    1244:	learn: 88633.1487098	test: 118973.4436516	best: 118973.4436516 (1244)	total: 7.06s	remaining: 49.6s
    1245:	learn: 88624.5018726	test: 118969.0587551	best: 118969.0587551 (1245)	total: 7.07s	remaining: 49.6s
    1246:	learn: 88612.6489362	test: 118964.7190596	best: 118964.7190596 (1246)	total: 7.07s	remaining: 49.6s
    1247:	learn: 88599.1251576	test: 118965.7167996	best: 118964.7190596 (1246)	total: 7.08s	remaining: 49.6s
    1248:	learn: 88572.8372773	test: 118944.0121652	best: 118944.0121652 (1248)	total: 7.08s	remaining: 49.6s
    1249:	learn: 88554.7828128	test: 118951.7862774	best: 118944.0121652 (1248)	total: 7.09s	remaining: 49.6s
    1250:	learn: 88531.1656032	test: 118941.2771672	best: 118941.2771672 (1250)	total: 7.1s	remaining: 49.6s
    1251:	learn: 88516.1253774	test: 118935.0812847	best: 118935.0812847 (1251)	total: 7.1s	remaining: 49.6s
    1252:	learn: 88498.4451577	test: 118930.9156052	best: 118930.9156052 (1252)	total: 7.11s	remaining: 49.6s
    1253:	learn: 88476.1238830	test: 118925.4872516	best: 118925.4872516 (1253)	total: 7.12s	remaining: 49.6s
    1254:	learn: 88460.2408902	test: 118918.4856651	best: 118918.4856651 (1254)	total: 7.12s	remaining: 49.6s
    1255:	learn: 88426.9209251	test: 118898.4667638	best: 118898.4667638 (1255)	total: 7.13s	remaining: 49.6s
    1256:	learn: 88420.7233602	test: 118894.9595480	best: 118894.9595480 (1256)	total: 7.13s	remaining: 49.6s
    1257:	learn: 88399.4163379	test: 118883.3808149	best: 118883.3808149 (1257)	total: 7.14s	remaining: 49.6s
    1258:	learn: 88385.3137708	test: 118888.5333039	best: 118883.3808149 (1257)	total: 7.15s	remaining: 49.6s
    1259:	learn: 88352.8508469	test: 118866.6827052	best: 118866.6827052 (1259)	total: 7.16s	remaining: 49.6s
    1260:	learn: 88335.2067391	test: 118856.2212591	best: 118856.2212591 (1260)	total: 7.16s	remaining: 49.6s
    1261:	learn: 88323.5370746	test: 118849.2609659	best: 118849.2609659 (1261)	total: 7.17s	remaining: 49.6s
    1262:	learn: 88297.6684618	test: 118828.3605996	best: 118828.3605996 (1262)	total: 7.17s	remaining: 49.6s
    1263:	learn: 88277.4494637	test: 118824.8683421	best: 118824.8683421 (1263)	total: 7.18s	remaining: 49.6s
    1264:	learn: 88256.2873609	test: 118818.3726306	best: 118818.3726306 (1264)	total: 7.18s	remaining: 49.6s
    1265:	learn: 88240.2330756	test: 118818.0855207	best: 118818.0855207 (1265)	total: 7.19s	remaining: 49.6s
    1266:	learn: 88227.5622783	test: 118826.6373323	best: 118818.0855207 (1265)	total: 7.2s	remaining: 49.6s
    1267:	learn: 88213.6660039	test: 118828.6333773	best: 118818.0855207 (1265)	total: 7.2s	remaining: 49.6s
    1268:	learn: 88196.3191106	test: 118828.5186652	best: 118818.0855207 (1265)	total: 7.21s	remaining: 49.6s
    1269:	learn: 88181.6280078	test: 118819.4704017	best: 118818.0855207 (1265)	total: 7.21s	remaining: 49.6s
    1270:	learn: 88164.5985456	test: 118809.4557972	best: 118809.4557972 (1270)	total: 7.22s	remaining: 49.6s
    1271:	learn: 88148.2398311	test: 118810.6459396	best: 118809.4557972 (1270)	total: 7.23s	remaining: 49.6s
    1272:	learn: 88137.2858729	test: 118814.8124963	best: 118809.4557972 (1270)	total: 7.23s	remaining: 49.6s
    1273:	learn: 88121.8255773	test: 118815.1612955	best: 118809.4557972 (1270)	total: 7.24s	remaining: 49.6s
    1274:	learn: 88104.2830440	test: 118820.4354603	best: 118809.4557972 (1270)	total: 7.25s	remaining: 49.6s
    1275:	learn: 88088.4298171	test: 118817.9296458	best: 118809.4557972 (1270)	total: 7.25s	remaining: 49.6s
    1276:	learn: 88077.7819643	test: 118822.1180030	best: 118809.4557972 (1270)	total: 7.26s	remaining: 49.6s
    1277:	learn: 88063.3053936	test: 118818.2413139	best: 118809.4557972 (1270)	total: 7.26s	remaining: 49.6s
    1278:	learn: 88050.9411350	test: 118803.7833488	best: 118803.7833488 (1278)	total: 7.27s	remaining: 49.6s
    1279:	learn: 88030.2632878	test: 118799.0583056	best: 118799.0583056 (1279)	total: 7.28s	remaining: 49.6s
    1280:	learn: 88016.7035725	test: 118799.9028758	best: 118799.0583056 (1279)	total: 7.29s	remaining: 49.6s
    1281:	learn: 88002.6815286	test: 118795.6384154	best: 118795.6384154 (1281)	total: 7.29s	remaining: 49.6s
    1282:	learn: 87989.6906547	test: 118785.0918205	best: 118785.0918205 (1282)	total: 7.3s	remaining: 49.6s
    1283:	learn: 87970.1521805	test: 118778.9640864	best: 118778.9640864 (1283)	total: 7.3s	remaining: 49.6s
    1284:	learn: 87961.9889820	test: 118764.3574787	best: 118764.3574787 (1284)	total: 7.31s	remaining: 49.6s
    1285:	learn: 87945.2915558	test: 118755.0375405	best: 118755.0375405 (1285)	total: 7.32s	remaining: 49.6s
    1286:	learn: 87914.7963848	test: 118734.7248217	best: 118734.7248217 (1286)	total: 7.33s	remaining: 49.6s
    1287:	learn: 87902.3249154	test: 118738.9109739	best: 118734.7248217 (1286)	total: 7.33s	remaining: 49.6s
    1288:	learn: 87878.5121332	test: 118726.5450400	best: 118726.5450400 (1288)	total: 7.34s	remaining: 49.6s
    1289:	learn: 87866.2754805	test: 118728.3675205	best: 118726.5450400 (1288)	total: 7.34s	remaining: 49.6s
    1290:	learn: 87853.1351872	test: 118729.3145715	best: 118726.5450400 (1288)	total: 7.35s	remaining: 49.6s
    1291:	learn: 87839.5904400	test: 118727.6253347	best: 118726.5450400 (1288)	total: 7.36s	remaining: 49.6s
    1292:	learn: 87823.1968037	test: 118722.9873050	best: 118722.9873050 (1292)	total: 7.36s	remaining: 49.6s
    1293:	learn: 87799.9401147	test: 118715.7850301	best: 118715.7850301 (1293)	total: 7.37s	remaining: 49.6s
    1294:	learn: 87785.2196287	test: 118711.2995969	best: 118711.2995969 (1294)	total: 7.38s	remaining: 49.6s
    1295:	learn: 87770.9474204	test: 118705.5511396	best: 118705.5511396 (1295)	total: 7.38s	remaining: 49.6s
    1296:	learn: 87757.4265906	test: 118698.3395101	best: 118698.3395101 (1296)	total: 7.39s	remaining: 49.6s
    1297:	learn: 87740.0727004	test: 118688.6751138	best: 118688.6751138 (1297)	total: 7.4s	remaining: 49.6s
    1298:	learn: 87714.8885858	test: 118680.2774019	best: 118680.2774019 (1298)	total: 7.4s	remaining: 49.6s
    1299:	learn: 87701.9486262	test: 118678.1964063	best: 118678.1964063 (1299)	total: 7.41s	remaining: 49.6s
    1300:	learn: 87682.1395127	test: 118673.7315505	best: 118673.7315505 (1300)	total: 7.42s	remaining: 49.6s
    1301:	learn: 87671.6403922	test: 118674.8520350	best: 118673.7315505 (1300)	total: 7.42s	remaining: 49.6s
    1302:	learn: 87657.6568843	test: 118672.8083505	best: 118672.8083505 (1302)	total: 7.43s	remaining: 49.6s
    1303:	learn: 87644.0298436	test: 118659.4323282	best: 118659.4323282 (1303)	total: 7.43s	remaining: 49.6s
    1304:	learn: 87632.4618560	test: 118655.6458985	best: 118655.6458985 (1304)	total: 7.44s	remaining: 49.6s
    1305:	learn: 87616.7015805	test: 118648.0727013	best: 118648.0727013 (1305)	total: 7.45s	remaining: 49.6s
    1306:	learn: 87604.8070562	test: 118651.3476540	best: 118648.0727013 (1305)	total: 7.46s	remaining: 49.6s
    1307:	learn: 87595.5086835	test: 118649.0500722	best: 118648.0727013 (1305)	total: 7.46s	remaining: 49.6s
    1308:	learn: 87574.5850975	test: 118644.0032642	best: 118644.0032642 (1308)	total: 7.47s	remaining: 49.6s
    1309:	learn: 87560.5906855	test: 118639.3812359	best: 118639.3812359 (1309)	total: 7.48s	remaining: 49.6s
    1310:	learn: 87542.8834616	test: 118627.2148481	best: 118627.2148481 (1310)	total: 7.48s	remaining: 49.6s
    1311:	learn: 87528.5820654	test: 118620.1240603	best: 118620.1240603 (1311)	total: 7.49s	remaining: 49.6s
    1312:	learn: 87508.7846389	test: 118620.1797126	best: 118620.1240603 (1311)	total: 7.49s	remaining: 49.6s
    1313:	learn: 87498.1726155	test: 118620.1494974	best: 118620.1240603 (1311)	total: 7.5s	remaining: 49.6s
    1314:	learn: 87488.4856268	test: 118625.4045570	best: 118620.1240603 (1311)	total: 7.51s	remaining: 49.6s
    1315:	learn: 87478.4470601	test: 118621.1174950	best: 118620.1240603 (1311)	total: 7.51s	remaining: 49.6s
    1316:	learn: 87461.6038752	test: 118616.9344906	best: 118616.9344906 (1316)	total: 7.52s	remaining: 49.6s
    1317:	learn: 87443.6564338	test: 118605.8500603	best: 118605.8500603 (1317)	total: 7.53s	remaining: 49.6s
    1318:	learn: 87427.4070025	test: 118601.7626904	best: 118601.7626904 (1318)	total: 7.53s	remaining: 49.6s
    1319:	learn: 87418.9332275	test: 118597.2549058	best: 118597.2549058 (1319)	total: 7.54s	remaining: 49.6s
    1320:	learn: 87407.0419010	test: 118601.1976060	best: 118597.2549058 (1319)	total: 7.54s	remaining: 49.6s
    1321:	learn: 87392.9077174	test: 118591.4726397	best: 118591.4726397 (1321)	total: 7.55s	remaining: 49.6s
    1322:	learn: 87377.0659340	test: 118600.7417562	best: 118591.4726397 (1321)	total: 7.55s	remaining: 49.6s
    1323:	learn: 87362.1541902	test: 118604.9765014	best: 118591.4726397 (1321)	total: 7.56s	remaining: 49.6s
    1324:	learn: 87338.1864787	test: 118590.7398976	best: 118590.7398976 (1324)	total: 7.57s	remaining: 49.6s
    1325:	learn: 87319.6963731	test: 118585.6684293	best: 118585.6684293 (1325)	total: 7.58s	remaining: 49.6s
    1326:	learn: 87296.3485291	test: 118591.3952847	best: 118585.6684293 (1325)	total: 7.58s	remaining: 49.6s
    1327:	learn: 87278.4232020	test: 118588.8214391	best: 118585.6684293 (1325)	total: 7.59s	remaining: 49.6s
    1328:	learn: 87267.5891773	test: 118585.2178417	best: 118585.2178417 (1328)	total: 7.59s	remaining: 49.5s
    1329:	learn: 87254.5364029	test: 118590.3859052	best: 118585.2178417 (1328)	total: 7.6s	remaining: 49.5s
    1330:	learn: 87239.7302435	test: 118590.5555611	best: 118585.2178417 (1328)	total: 7.61s	remaining: 49.5s
    1331:	learn: 87225.2782646	test: 118594.1935045	best: 118585.2178417 (1328)	total: 7.61s	remaining: 49.5s
    1332:	learn: 87216.9512509	test: 118596.3545790	best: 118585.2178417 (1328)	total: 7.62s	remaining: 49.5s
    1333:	learn: 87204.7142929	test: 118598.5922715	best: 118585.2178417 (1328)	total: 7.63s	remaining: 49.5s
    1334:	learn: 87192.9671009	test: 118590.6881603	best: 118585.2178417 (1328)	total: 7.63s	remaining: 49.5s
    1335:	learn: 87176.2060466	test: 118576.9615985	best: 118576.9615985 (1335)	total: 7.64s	remaining: 49.5s
    1336:	learn: 87156.2586851	test: 118563.8535831	best: 118563.8535831 (1336)	total: 7.65s	remaining: 49.5s
    1337:	learn: 87140.8105362	test: 118560.0880229	best: 118560.0880229 (1337)	total: 7.65s	remaining: 49.5s
    1338:	learn: 87129.5332773	test: 118556.5727244	best: 118556.5727244 (1338)	total: 7.66s	remaining: 49.5s
    1339:	learn: 87111.3479315	test: 118553.8444990	best: 118553.8444990 (1339)	total: 7.67s	remaining: 49.5s
    1340:	learn: 87099.2362669	test: 118554.8142023	best: 118553.8444990 (1339)	total: 7.67s	remaining: 49.5s
    1341:	learn: 87079.4757568	test: 118544.6755146	best: 118544.6755146 (1341)	total: 7.68s	remaining: 49.5s
    1342:	learn: 87059.9432524	test: 118532.5476306	best: 118532.5476306 (1342)	total: 7.68s	remaining: 49.5s
    1343:	learn: 87043.3683259	test: 118532.6959994	best: 118532.5476306 (1342)	total: 7.69s	remaining: 49.5s
    1344:	learn: 87028.6034496	test: 118529.3284182	best: 118529.3284182 (1344)	total: 7.7s	remaining: 49.5s
    1345:	learn: 87015.0601124	test: 118529.6316457	best: 118529.3284182 (1344)	total: 7.71s	remaining: 49.5s
    1346:	learn: 87001.2552096	test: 118523.5254868	best: 118523.5254868 (1346)	total: 7.71s	remaining: 49.5s
    1347:	learn: 86990.1242589	test: 118524.8726413	best: 118523.5254868 (1346)	total: 7.72s	remaining: 49.6s
    1348:	learn: 86968.4887954	test: 118527.7555798	best: 118523.5254868 (1346)	total: 7.73s	remaining: 49.6s
    1349:	learn: 86954.5397860	test: 118523.6082224	best: 118523.5254868 (1346)	total: 7.73s	remaining: 49.6s
    1350:	learn: 86945.3932493	test: 118526.7686397	best: 118523.5254868 (1346)	total: 7.74s	remaining: 49.6s
    1351:	learn: 86934.6623424	test: 118521.3483950	best: 118521.3483950 (1351)	total: 7.75s	remaining: 49.6s
    1352:	learn: 86922.9809282	test: 118515.5410744	best: 118515.5410744 (1352)	total: 7.75s	remaining: 49.6s
    1353:	learn: 86907.8433148	test: 118509.4632555	best: 118509.4632555 (1353)	total: 7.76s	remaining: 49.6s
    1354:	learn: 86894.7575477	test: 118507.2767215	best: 118507.2767215 (1354)	total: 7.77s	remaining: 49.6s
    1355:	learn: 86885.4050826	test: 118505.2347330	best: 118505.2347330 (1355)	total: 7.78s	remaining: 49.6s
    1356:	learn: 86874.3189253	test: 118509.2979363	best: 118505.2347330 (1355)	total: 7.78s	remaining: 49.6s
    1357:	learn: 86861.9412771	test: 118507.3923218	best: 118505.2347330 (1355)	total: 7.79s	remaining: 49.6s
    1358:	learn: 86844.4678328	test: 118505.7510372	best: 118505.2347330 (1355)	total: 7.8s	remaining: 49.6s
    1359:	learn: 86829.4656692	test: 118501.6923163	best: 118501.6923163 (1359)	total: 7.8s	remaining: 49.6s
    1360:	learn: 86809.0214341	test: 118496.7162466	best: 118496.7162466 (1360)	total: 7.81s	remaining: 49.6s
    1361:	learn: 86791.6710238	test: 118499.4098453	best: 118496.7162466 (1360)	total: 7.82s	remaining: 49.6s
    1362:	learn: 86772.4459195	test: 118493.6271398	best: 118493.6271398 (1362)	total: 7.83s	remaining: 49.6s
    1363:	learn: 86755.7690969	test: 118492.3148539	best: 118492.3148539 (1363)	total: 7.83s	remaining: 49.6s
    1364:	learn: 86741.0672626	test: 118486.5325780	best: 118486.5325780 (1364)	total: 7.84s	remaining: 49.6s
    1365:	learn: 86729.2061461	test: 118487.9297867	best: 118486.5325780 (1364)	total: 7.84s	remaining: 49.6s
    1366:	learn: 86712.4125253	test: 118490.7782866	best: 118486.5325780 (1364)	total: 7.85s	remaining: 49.6s
    1367:	learn: 86690.4429693	test: 118480.7724029	best: 118480.7724029 (1367)	total: 7.86s	remaining: 49.6s
    1368:	learn: 86668.0960142	test: 118466.2429663	best: 118466.2429663 (1368)	total: 7.86s	remaining: 49.6s
    1369:	learn: 86651.3792374	test: 118452.5025563	best: 118452.5025563 (1369)	total: 7.87s	remaining: 49.6s
    1370:	learn: 86624.2965938	test: 118440.0798105	best: 118440.0798105 (1370)	total: 7.88s	remaining: 49.6s
    1371:	learn: 86599.1213563	test: 118423.2958127	best: 118423.2958127 (1371)	total: 7.89s	remaining: 49.6s
    1372:	learn: 86594.2739969	test: 118425.7518309	best: 118423.2958127 (1371)	total: 7.89s	remaining: 49.6s
    1373:	learn: 86568.3100307	test: 118405.2109437	best: 118405.2109437 (1373)	total: 7.9s	remaining: 49.6s
    1374:	learn: 86547.7772286	test: 118399.3422822	best: 118399.3422822 (1374)	total: 7.91s	remaining: 49.6s
    1375:	learn: 86537.4927049	test: 118390.5588102	best: 118390.5588102 (1375)	total: 7.91s	remaining: 49.6s
    1376:	learn: 86528.7356397	test: 118387.5812517	best: 118387.5812517 (1376)	total: 7.92s	remaining: 49.6s
    1377:	learn: 86513.4552678	test: 118384.9884556	best: 118384.9884556 (1377)	total: 7.93s	remaining: 49.6s
    1378:	learn: 86498.5983820	test: 118377.9915690	best: 118377.9915690 (1378)	total: 7.93s	remaining: 49.6s
    1379:	learn: 86486.4028365	test: 118373.4129429	best: 118373.4129429 (1379)	total: 7.94s	remaining: 49.6s
    1380:	learn: 86468.1832007	test: 118365.3649779	best: 118365.3649779 (1380)	total: 7.95s	remaining: 49.6s
    1381:	learn: 86458.1418259	test: 118356.7502964	best: 118356.7502964 (1381)	total: 7.95s	remaining: 49.6s
    1382:	learn: 86449.1700155	test: 118355.1027251	best: 118355.1027251 (1382)	total: 7.96s	remaining: 49.6s
    1383:	learn: 86439.7779160	test: 118360.5961811	best: 118355.1027251 (1382)	total: 7.97s	remaining: 49.6s
    1384:	learn: 86434.4316555	test: 118361.0418310	best: 118355.1027251 (1382)	total: 7.97s	remaining: 49.6s
    1385:	learn: 86409.9078660	test: 118361.1167580	best: 118355.1027251 (1382)	total: 7.98s	remaining: 49.6s
    1386:	learn: 86398.9037956	test: 118367.1047591	best: 118355.1027251 (1382)	total: 7.99s	remaining: 49.6s
    1387:	learn: 86388.9228014	test: 118356.5794069	best: 118355.1027251 (1382)	total: 8s	remaining: 49.6s
    1388:	learn: 86378.3940071	test: 118354.4111695	best: 118354.4111695 (1388)	total: 8s	remaining: 49.6s
    1389:	learn: 86357.6436300	test: 118342.4859790	best: 118342.4859790 (1389)	total: 8.01s	remaining: 49.6s
    1390:	learn: 86343.7461184	test: 118336.1096942	best: 118336.1096942 (1390)	total: 8.02s	remaining: 49.6s
    1391:	learn: 86331.3866153	test: 118334.5391073	best: 118334.5391073 (1391)	total: 8.02s	remaining: 49.6s
    1392:	learn: 86319.9767781	test: 118329.7504721	best: 118329.7504721 (1392)	total: 8.03s	remaining: 49.6s
    1393:	learn: 86313.9622604	test: 118327.1690703	best: 118327.1690703 (1393)	total: 8.04s	remaining: 49.6s
    1394:	learn: 86301.1679996	test: 118323.3619003	best: 118323.3619003 (1394)	total: 8.04s	remaining: 49.6s
    1395:	learn: 86281.9349883	test: 118319.2952336	best: 118319.2952336 (1395)	total: 8.05s	remaining: 49.6s
    1396:	learn: 86250.1700193	test: 118314.4264816	best: 118314.4264816 (1396)	total: 8.06s	remaining: 49.6s
    1397:	learn: 86226.2800630	test: 118298.7506015	best: 118298.7506015 (1397)	total: 8.06s	remaining: 49.6s
    1398:	learn: 86203.6450130	test: 118296.1644950	best: 118296.1644950 (1398)	total: 8.07s	remaining: 49.6s
    1399:	learn: 86171.2206618	test: 118296.6178709	best: 118296.1644950 (1398)	total: 8.08s	remaining: 49.6s
    1400:	learn: 86152.7376496	test: 118284.0450284	best: 118284.0450284 (1400)	total: 8.08s	remaining: 49.6s
    1401:	learn: 86124.9239546	test: 118278.4855247	best: 118278.4855247 (1401)	total: 8.09s	remaining: 49.6s
    1402:	learn: 86114.8012389	test: 118273.6292581	best: 118273.6292581 (1402)	total: 8.1s	remaining: 49.6s
    1403:	learn: 86090.5910035	test: 118273.0958529	best: 118273.0958529 (1403)	total: 8.1s	remaining: 49.6s
    1404:	learn: 86079.0399866	test: 118265.9740572	best: 118265.9740572 (1404)	total: 8.11s	remaining: 49.6s
    1405:	learn: 86065.2784393	test: 118257.7031503	best: 118257.7031503 (1405)	total: 8.12s	remaining: 49.6s
    1406:	learn: 86051.9374298	test: 118250.0885119	best: 118250.0885119 (1406)	total: 8.12s	remaining: 49.6s
    1407:	learn: 86033.2435478	test: 118238.9853738	best: 118238.9853738 (1407)	total: 8.13s	remaining: 49.6s
    1408:	learn: 86012.0068694	test: 118222.6338199	best: 118222.6338199 (1408)	total: 8.13s	remaining: 49.6s
    1409:	learn: 85998.9988084	test: 118217.9426677	best: 118217.9426677 (1409)	total: 8.14s	remaining: 49.6s
    1410:	learn: 85974.4218173	test: 118215.7087481	best: 118215.7087481 (1410)	total: 8.15s	remaining: 49.6s
    1411:	learn: 85963.5535110	test: 118203.0605322	best: 118203.0605322 (1411)	total: 8.16s	remaining: 49.6s
    1412:	learn: 85952.2959386	test: 118197.4583067	best: 118197.4583067 (1412)	total: 8.16s	remaining: 49.6s
    1413:	learn: 85942.4307422	test: 118194.5356549	best: 118194.5356549 (1413)	total: 8.17s	remaining: 49.6s
    1414:	learn: 85932.0035042	test: 118197.7281546	best: 118194.5356549 (1413)	total: 8.18s	remaining: 49.6s
    1415:	learn: 85916.8629808	test: 118200.7878073	best: 118194.5356549 (1413)	total: 8.18s	remaining: 49.6s
    1416:	learn: 85898.9272157	test: 118190.2212797	best: 118190.2212797 (1416)	total: 8.19s	remaining: 49.6s
    1417:	learn: 85888.8396249	test: 118191.2024433	best: 118190.2212797 (1416)	total: 8.2s	remaining: 49.6s
    1418:	learn: 85875.7936251	test: 118189.4938827	best: 118189.4938827 (1418)	total: 8.2s	remaining: 49.6s
    1419:	learn: 85870.4045717	test: 118187.2212548	best: 118187.2212548 (1419)	total: 8.21s	remaining: 49.6s
    1420:	learn: 85848.1877113	test: 118181.9160103	best: 118181.9160103 (1420)	total: 8.21s	remaining: 49.6s
    1421:	learn: 85837.3323749	test: 118185.0067636	best: 118181.9160103 (1420)	total: 8.22s	remaining: 49.6s
    1422:	learn: 85816.9605677	test: 118183.5131667	best: 118181.9160103 (1420)	total: 8.23s	remaining: 49.6s
    1423:	learn: 85807.0985257	test: 118185.7330184	best: 118181.9160103 (1420)	total: 8.23s	remaining: 49.6s
    1424:	learn: 85799.4672710	test: 118188.7235616	best: 118181.9160103 (1420)	total: 8.24s	remaining: 49.6s
    1425:	learn: 85784.7395223	test: 118191.0470151	best: 118181.9160103 (1420)	total: 8.25s	remaining: 49.6s
    1426:	learn: 85765.1389748	test: 118202.3048190	best: 118181.9160103 (1420)	total: 8.25s	remaining: 49.6s
    1427:	learn: 85753.6490620	test: 118184.6407374	best: 118181.9160103 (1420)	total: 8.26s	remaining: 49.6s
    1428:	learn: 85732.6254567	test: 118191.3112131	best: 118181.9160103 (1420)	total: 8.26s	remaining: 49.6s
    1429:	learn: 85727.1203358	test: 118189.7406002	best: 118181.9160103 (1420)	total: 8.27s	remaining: 49.6s
    1430:	learn: 85715.6353597	test: 118181.3557327	best: 118181.3557327 (1430)	total: 8.28s	remaining: 49.6s
    1431:	learn: 85704.0177595	test: 118180.0387566	best: 118180.0387566 (1431)	total: 8.28s	remaining: 49.6s
    1432:	learn: 85689.8991151	test: 118159.2172665	best: 118159.2172665 (1432)	total: 8.29s	remaining: 49.6s
    1433:	learn: 85671.9671129	test: 118155.6252900	best: 118155.6252900 (1433)	total: 8.29s	remaining: 49.6s
    1434:	learn: 85659.9404304	test: 118144.6848645	best: 118144.6848645 (1434)	total: 8.3s	remaining: 49.6s
    1435:	learn: 85627.8761819	test: 118132.2724734	best: 118132.2724734 (1435)	total: 8.31s	remaining: 49.6s
    1436:	learn: 85610.2015492	test: 118133.4993519	best: 118132.2724734 (1435)	total: 8.32s	remaining: 49.6s
    1437:	learn: 85583.0341434	test: 118124.2223908	best: 118124.2223908 (1437)	total: 8.32s	remaining: 49.6s
    1438:	learn: 85563.3459630	test: 118123.0202684	best: 118123.0202684 (1438)	total: 8.33s	remaining: 49.6s
    1439:	learn: 85549.4570876	test: 118117.8347263	best: 118117.8347263 (1439)	total: 8.34s	remaining: 49.6s
    1440:	learn: 85537.1384467	test: 118118.3521714	best: 118117.8347263 (1439)	total: 8.34s	remaining: 49.5s
    1441:	learn: 85526.8444447	test: 118122.3102757	best: 118117.8347263 (1439)	total: 8.35s	remaining: 49.5s
    1442:	learn: 85505.0556096	test: 118106.2916139	best: 118106.2916139 (1442)	total: 8.35s	remaining: 49.5s
    1443:	learn: 85479.3080800	test: 118103.6112510	best: 118103.6112510 (1443)	total: 8.36s	remaining: 49.5s
    1444:	learn: 85471.0440106	test: 118101.8394985	best: 118101.8394985 (1444)	total: 8.36s	remaining: 49.5s
    1445:	learn: 85461.7354887	test: 118093.7915582	best: 118093.7915582 (1445)	total: 8.37s	remaining: 49.5s
    1446:	learn: 85450.9078742	test: 118093.2322793	best: 118093.2322793 (1446)	total: 8.37s	remaining: 49.5s
    1447:	learn: 85442.9150008	test: 118082.1382626	best: 118082.1382626 (1447)	total: 8.38s	remaining: 49.5s
    1448:	learn: 85428.1047754	test: 118081.0921891	best: 118081.0921891 (1448)	total: 8.38s	remaining: 49.5s
    1449:	learn: 85415.7255488	test: 118075.0878218	best: 118075.0878218 (1449)	total: 8.39s	remaining: 49.5s
    1450:	learn: 85403.9292057	test: 118059.2038220	best: 118059.2038220 (1450)	total: 8.39s	remaining: 49.5s
    1451:	learn: 85391.6218221	test: 118053.7964375	best: 118053.7964375 (1451)	total: 8.4s	remaining: 49.5s
    1452:	learn: 85373.7802744	test: 118058.6426380	best: 118053.7964375 (1451)	total: 8.4s	remaining: 49.4s
    1453:	learn: 85361.4918485	test: 118052.9685076	best: 118052.9685076 (1453)	total: 8.41s	remaining: 49.4s
    1454:	learn: 85352.7785940	test: 118048.2455211	best: 118048.2455211 (1454)	total: 8.42s	remaining: 49.4s
    1455:	learn: 85339.3397932	test: 118044.9019472	best: 118044.9019472 (1455)	total: 8.42s	remaining: 49.4s
    1456:	learn: 85331.0075862	test: 118053.5233286	best: 118044.9019472 (1455)	total: 8.43s	remaining: 49.4s
    1457:	learn: 85315.2807975	test: 118052.6465150	best: 118044.9019472 (1455)	total: 8.43s	remaining: 49.4s
    1458:	learn: 85302.0276852	test: 118038.8137188	best: 118038.8137188 (1458)	total: 8.44s	remaining: 49.4s
    1459:	learn: 85289.7228776	test: 118036.4274492	best: 118036.4274492 (1459)	total: 8.44s	remaining: 49.4s
    1460:	learn: 85276.8016857	test: 118031.1026817	best: 118031.1026817 (1460)	total: 8.45s	remaining: 49.4s
    1461:	learn: 85265.8285253	test: 118027.6372460	best: 118027.6372460 (1461)	total: 8.45s	remaining: 49.4s
    1462:	learn: 85245.0461859	test: 118035.8119496	best: 118027.6372460 (1461)	total: 8.46s	remaining: 49.4s
    1463:	learn: 85230.0880411	test: 118031.6126350	best: 118027.6372460 (1461)	total: 8.46s	remaining: 49.4s
    1464:	learn: 85217.2140492	test: 118032.5776907	best: 118027.6372460 (1461)	total: 8.47s	remaining: 49.3s
    1465:	learn: 85208.6573401	test: 118027.6566774	best: 118027.6372460 (1461)	total: 8.47s	remaining: 49.3s
    1466:	learn: 85182.5425897	test: 118012.3354065	best: 118012.3354065 (1466)	total: 8.48s	remaining: 49.3s
    1467:	learn: 85167.9218981	test: 118006.0954867	best: 118006.0954867 (1467)	total: 8.49s	remaining: 49.3s
    1468:	learn: 85158.7393960	test: 118006.1132307	best: 118006.0954867 (1467)	total: 8.49s	remaining: 49.3s
    1469:	learn: 85139.0352684	test: 117996.6527131	best: 117996.6527131 (1469)	total: 8.5s	remaining: 49.3s
    1470:	learn: 85123.5696019	test: 117990.9613830	best: 117990.9613830 (1470)	total: 8.51s	remaining: 49.3s
    1471:	learn: 85111.0500365	test: 117991.7036611	best: 117990.9613830 (1470)	total: 8.51s	remaining: 49.3s
    1472:	learn: 85084.7644240	test: 117993.2703097	best: 117990.9613830 (1470)	total: 8.52s	remaining: 49.3s
    1473:	learn: 85060.1961396	test: 117980.5102583	best: 117980.5102583 (1473)	total: 8.52s	remaining: 49.3s
    1474:	learn: 85047.6740820	test: 117981.5362455	best: 117980.5102583 (1473)	total: 8.53s	remaining: 49.3s
    1475:	learn: 85032.1848761	test: 117983.0056472	best: 117980.5102583 (1473)	total: 8.53s	remaining: 49.3s
    1476:	learn: 85018.3989585	test: 117982.3786872	best: 117980.5102583 (1473)	total: 8.54s	remaining: 49.3s
    1477:	learn: 85005.0097082	test: 117978.3944533	best: 117978.3944533 (1477)	total: 8.54s	remaining: 49.3s
    1478:	learn: 84981.5793792	test: 117965.7253279	best: 117965.7253279 (1478)	total: 8.55s	remaining: 49.3s
    1479:	learn: 84967.1141065	test: 117955.6743054	best: 117955.6743054 (1479)	total: 8.55s	remaining: 49.3s
    1480:	learn: 84946.6407609	test: 117946.3265894	best: 117946.3265894 (1480)	total: 8.56s	remaining: 49.2s
    1481:	learn: 84926.9480924	test: 117931.5172831	best: 117931.5172831 (1481)	total: 8.57s	remaining: 49.2s
    1482:	learn: 84903.6644031	test: 117911.7660940	best: 117911.7660940 (1482)	total: 8.57s	remaining: 49.2s
    1483:	learn: 84891.4678468	test: 117915.9138372	best: 117911.7660940 (1482)	total: 8.58s	remaining: 49.2s
    1484:	learn: 84871.4692331	test: 117904.8032132	best: 117904.8032132 (1484)	total: 8.58s	remaining: 49.2s
    1485:	learn: 84859.2208399	test: 117903.3137906	best: 117903.3137906 (1485)	total: 8.59s	remaining: 49.2s
    1486:	learn: 84853.9182460	test: 117903.5446446	best: 117903.3137906 (1485)	total: 8.59s	remaining: 49.2s
    1487:	learn: 84842.7440466	test: 117889.2928433	best: 117889.2928433 (1487)	total: 8.6s	remaining: 49.2s
    1488:	learn: 84832.2127899	test: 117884.0476619	best: 117884.0476619 (1488)	total: 8.6s	remaining: 49.2s
    1489:	learn: 84816.6698626	test: 117885.1586755	best: 117884.0476619 (1488)	total: 8.61s	remaining: 49.2s
    1490:	learn: 84807.7065015	test: 117879.9731775	best: 117879.9731775 (1490)	total: 8.62s	remaining: 49.2s
    1491:	learn: 84798.2600763	test: 117866.3402040	best: 117866.3402040 (1491)	total: 8.62s	remaining: 49.2s
    1492:	learn: 84786.5806329	test: 117864.0062604	best: 117864.0062604 (1492)	total: 8.63s	remaining: 49.1s
    1493:	learn: 84769.6200425	test: 117857.4816263	best: 117857.4816263 (1493)	total: 8.63s	remaining: 49.1s
    1494:	learn: 84745.2405682	test: 117842.4382356	best: 117842.4382356 (1494)	total: 8.64s	remaining: 49.1s
    1495:	learn: 84738.6107018	test: 117837.9654344	best: 117837.9654344 (1495)	total: 8.64s	remaining: 49.1s
    1496:	learn: 84729.8741205	test: 117830.5128560	best: 117830.5128560 (1496)	total: 8.65s	remaining: 49.1s
    1497:	learn: 84721.6630048	test: 117833.4985350	best: 117830.5128560 (1496)	total: 8.65s	remaining: 49.1s
    1498:	learn: 84703.5233770	test: 117838.7672953	best: 117830.5128560 (1496)	total: 8.66s	remaining: 49.1s
    1499:	learn: 84691.4084721	test: 117839.8179264	best: 117830.5128560 (1496)	total: 8.67s	remaining: 49.1s
    1500:	learn: 84678.9098139	test: 117835.2528544	best: 117830.5128560 (1496)	total: 8.68s	remaining: 49.1s
    1501:	learn: 84661.9912674	test: 117836.7675095	best: 117830.5128560 (1496)	total: 8.68s	remaining: 49.1s
    1502:	learn: 84645.1775485	test: 117835.1770159	best: 117830.5128560 (1496)	total: 8.69s	remaining: 49.1s
    1503:	learn: 84631.0419873	test: 117844.3008865	best: 117830.5128560 (1496)	total: 8.69s	remaining: 49.1s
    1504:	learn: 84622.7300520	test: 117846.3791286	best: 117830.5128560 (1496)	total: 8.7s	remaining: 49.1s
    1505:	learn: 84609.4336726	test: 117855.0586954	best: 117830.5128560 (1496)	total: 8.71s	remaining: 49.1s
    1506:	learn: 84599.0293219	test: 117855.2143609	best: 117830.5128560 (1496)	total: 8.71s	remaining: 49.1s
    1507:	learn: 84590.5069723	test: 117862.6557103	best: 117830.5128560 (1496)	total: 8.72s	remaining: 49.1s
    1508:	learn: 84570.5501565	test: 117860.9027101	best: 117830.5128560 (1496)	total: 8.72s	remaining: 49.1s
    1509:	learn: 84557.9291224	test: 117847.8305929	best: 117830.5128560 (1496)	total: 8.73s	remaining: 49.1s
    1510:	learn: 84546.3350822	test: 117843.2481375	best: 117830.5128560 (1496)	total: 8.73s	remaining: 49.1s
    1511:	learn: 84534.0002065	test: 117837.6677304	best: 117830.5128560 (1496)	total: 8.74s	remaining: 49.1s
    1512:	learn: 84518.6621588	test: 117837.6978110	best: 117830.5128560 (1496)	total: 8.74s	remaining: 49.1s
    1513:	learn: 84510.9118546	test: 117834.4060745	best: 117830.5128560 (1496)	total: 8.75s	remaining: 49s
    1514:	learn: 84495.7562938	test: 117824.2631175	best: 117824.2631175 (1514)	total: 8.76s	remaining: 49s
    1515:	learn: 84480.6763779	test: 117818.5032689	best: 117818.5032689 (1515)	total: 8.76s	remaining: 49s
    1516:	learn: 84471.2017104	test: 117814.2908961	best: 117814.2908961 (1516)	total: 8.77s	remaining: 49s
    1517:	learn: 84458.9329927	test: 117811.9314376	best: 117811.9314376 (1517)	total: 8.78s	remaining: 49s
    1518:	learn: 84427.7535455	test: 117798.1587805	best: 117798.1587805 (1518)	total: 8.78s	remaining: 49s
    1519:	learn: 84406.0950627	test: 117778.4418486	best: 117778.4418486 (1519)	total: 8.79s	remaining: 49s
    1520:	learn: 84389.8858386	test: 117769.9356491	best: 117769.9356491 (1520)	total: 8.79s	remaining: 49s
    1521:	learn: 84375.2868431	test: 117764.5697189	best: 117764.5697189 (1521)	total: 8.8s	remaining: 49s
    1522:	learn: 84369.0302903	test: 117762.9383687	best: 117762.9383687 (1522)	total: 8.8s	remaining: 49s
    1523:	learn: 84354.8946456	test: 117756.8834886	best: 117756.8834886 (1523)	total: 8.81s	remaining: 49s
    1524:	learn: 84346.8547104	test: 117756.3116856	best: 117756.3116856 (1524)	total: 8.82s	remaining: 49s
    1525:	learn: 84329.4047990	test: 117759.2855581	best: 117756.3116856 (1524)	total: 8.82s	remaining: 49s
    1526:	learn: 84313.3470288	test: 117760.7751197	best: 117756.3116856 (1524)	total: 8.83s	remaining: 49s
    1527:	learn: 84305.7877535	test: 117758.2471809	best: 117756.3116856 (1524)	total: 8.84s	remaining: 49s
    1528:	learn: 84292.0511166	test: 117746.2014041	best: 117746.2014041 (1528)	total: 8.84s	remaining: 49s
    1529:	learn: 84281.7502927	test: 117741.5315504	best: 117741.5315504 (1529)	total: 8.85s	remaining: 49s
    1530:	learn: 84272.0872708	test: 117741.8341545	best: 117741.5315504 (1529)	total: 8.86s	remaining: 49s
    1531:	learn: 84261.4102094	test: 117729.9204229	best: 117729.9204229 (1531)	total: 8.87s	remaining: 49s
    1532:	learn: 84252.8444449	test: 117729.6881476	best: 117729.6881476 (1532)	total: 8.87s	remaining: 49s
    1533:	learn: 84237.5274686	test: 117724.1189943	best: 117724.1189943 (1533)	total: 8.88s	remaining: 49s
    1534:	learn: 84223.5772478	test: 117728.6057436	best: 117724.1189943 (1533)	total: 8.88s	remaining: 49s
    1535:	learn: 84202.3160471	test: 117710.2400176	best: 117710.2400176 (1535)	total: 8.89s	remaining: 49s
    1536:	learn: 84189.1922461	test: 117701.9193904	best: 117701.9193904 (1536)	total: 8.89s	remaining: 49s
    1537:	learn: 84181.7529362	test: 117697.3424224	best: 117697.3424224 (1537)	total: 8.9s	remaining: 49s
    1538:	learn: 84164.7095827	test: 117691.6807295	best: 117691.6807295 (1538)	total: 8.9s	remaining: 49s
    1539:	learn: 84146.3853144	test: 117683.0296515	best: 117683.0296515 (1539)	total: 8.91s	remaining: 48.9s
    1540:	learn: 84127.3498053	test: 117679.6250117	best: 117679.6250117 (1540)	total: 8.91s	remaining: 48.9s
    1541:	learn: 84115.2906325	test: 117673.3254970	best: 117673.3254970 (1541)	total: 8.92s	remaining: 48.9s
    1542:	learn: 84095.5856744	test: 117666.0182229	best: 117666.0182229 (1542)	total: 8.93s	remaining: 48.9s
    1543:	learn: 84072.7424497	test: 117663.1852298	best: 117663.1852298 (1543)	total: 8.94s	remaining: 48.9s
    1544:	learn: 84055.4105537	test: 117658.2596021	best: 117658.2596021 (1544)	total: 8.94s	remaining: 48.9s
    1545:	learn: 84030.8250938	test: 117649.5941377	best: 117649.5941377 (1545)	total: 8.95s	remaining: 48.9s
    1546:	learn: 84007.2397207	test: 117642.0136015	best: 117642.0136015 (1546)	total: 8.96s	remaining: 48.9s
    1547:	learn: 83988.6384518	test: 117636.5277327	best: 117636.5277327 (1547)	total: 8.96s	remaining: 48.9s
    1548:	learn: 83976.0964770	test: 117642.6241319	best: 117636.5277327 (1547)	total: 8.97s	remaining: 48.9s
    1549:	learn: 83967.3340534	test: 117644.4912619	best: 117636.5277327 (1547)	total: 8.97s	remaining: 48.9s
    1550:	learn: 83958.2460084	test: 117640.4678396	best: 117636.5277327 (1547)	total: 8.98s	remaining: 48.9s
    1551:	learn: 83945.9782710	test: 117640.1666107	best: 117636.5277327 (1547)	total: 8.99s	remaining: 48.9s
    1552:	learn: 83934.3014464	test: 117645.1217015	best: 117636.5277327 (1547)	total: 8.99s	remaining: 48.9s
    1553:	learn: 83919.3301719	test: 117637.9388016	best: 117636.5277327 (1547)	total: 9s	remaining: 48.9s
    1554:	learn: 83908.2439350	test: 117625.8833056	best: 117625.8833056 (1554)	total: 9.01s	remaining: 48.9s
    1555:	learn: 83894.6892425	test: 117623.7231613	best: 117623.7231613 (1555)	total: 9.01s	remaining: 48.9s
    1556:	learn: 83877.4722780	test: 117611.7661859	best: 117611.7661859 (1556)	total: 9.02s	remaining: 48.9s
    1557:	learn: 83854.4663543	test: 117604.7291315	best: 117604.7291315 (1557)	total: 9.02s	remaining: 48.9s
    1558:	learn: 83848.1496827	test: 117598.8570056	best: 117598.8570056 (1558)	total: 9.03s	remaining: 48.9s
    1559:	learn: 83830.9432138	test: 117589.4168272	best: 117589.4168272 (1559)	total: 9.04s	remaining: 48.9s
    1560:	learn: 83818.4991815	test: 117585.9025870	best: 117585.9025870 (1560)	total: 9.04s	remaining: 48.9s
    1561:	learn: 83810.9101439	test: 117584.5771644	best: 117584.5771644 (1561)	total: 9.05s	remaining: 48.9s
    1562:	learn: 83800.9620471	test: 117583.0907541	best: 117583.0907541 (1562)	total: 9.05s	remaining: 48.9s
    1563:	learn: 83792.9000043	test: 117577.3909923	best: 117577.3909923 (1563)	total: 9.06s	remaining: 48.9s
    1564:	learn: 83779.2519026	test: 117563.5223809	best: 117563.5223809 (1564)	total: 9.06s	remaining: 48.8s
    1565:	learn: 83764.1295176	test: 117567.4086721	best: 117563.5223809 (1564)	total: 9.07s	remaining: 48.8s
    1566:	learn: 83746.7930219	test: 117553.6852381	best: 117553.6852381 (1566)	total: 9.07s	remaining: 48.8s
    1567:	learn: 83740.4191548	test: 117553.9096897	best: 117553.6852381 (1566)	total: 9.08s	remaining: 48.8s
    1568:	learn: 83725.0547115	test: 117544.0647107	best: 117544.0647107 (1568)	total: 9.08s	remaining: 48.8s
    1569:	learn: 83707.0633122	test: 117527.6484987	best: 117527.6484987 (1569)	total: 9.09s	remaining: 48.8s
    1570:	learn: 83701.1353096	test: 117527.1087452	best: 117527.1087452 (1570)	total: 9.1s	remaining: 48.8s
    1571:	learn: 83686.3011330	test: 117525.2496168	best: 117525.2496168 (1571)	total: 9.1s	remaining: 48.8s
    1572:	learn: 83675.2806621	test: 117539.7886019	best: 117525.2496168 (1571)	total: 9.11s	remaining: 48.8s
    1573:	learn: 83664.7207777	test: 117544.4215613	best: 117525.2496168 (1571)	total: 9.11s	remaining: 48.8s
    1574:	learn: 83655.5619182	test: 117548.2090575	best: 117525.2496168 (1571)	total: 9.12s	remaining: 48.8s
    1575:	learn: 83646.1485227	test: 117557.2539212	best: 117525.2496168 (1571)	total: 9.12s	remaining: 48.8s
    1576:	learn: 83628.6124069	test: 117557.3187354	best: 117525.2496168 (1571)	total: 9.13s	remaining: 48.7s
    1577:	learn: 83617.8899565	test: 117548.1831543	best: 117525.2496168 (1571)	total: 9.13s	remaining: 48.7s
    1578:	learn: 83609.3494824	test: 117542.6897597	best: 117525.2496168 (1571)	total: 9.14s	remaining: 48.7s
    1579:	learn: 83589.6249155	test: 117541.7165394	best: 117525.2496168 (1571)	total: 9.14s	remaining: 48.7s
    1580:	learn: 83576.8265089	test: 117540.5974336	best: 117525.2496168 (1571)	total: 9.15s	remaining: 48.7s
    1581:	learn: 83547.7614236	test: 117520.2732477	best: 117520.2732477 (1581)	total: 9.15s	remaining: 48.7s
    1582:	learn: 83538.8903400	test: 117515.9595410	best: 117515.9595410 (1582)	total: 9.16s	remaining: 48.7s
    1583:	learn: 83519.2435894	test: 117513.0573170	best: 117513.0573170 (1583)	total: 9.16s	remaining: 48.7s
    1584:	learn: 83508.1414091	test: 117516.0351857	best: 117513.0573170 (1583)	total: 9.17s	remaining: 48.7s
    1585:	learn: 83501.0281504	test: 117514.8769694	best: 117513.0573170 (1583)	total: 9.18s	remaining: 48.7s
    1586:	learn: 83488.4028766	test: 117507.5765119	best: 117507.5765119 (1586)	total: 9.18s	remaining: 48.7s
    1587:	learn: 83473.3231270	test: 117510.9088831	best: 117507.5765119 (1586)	total: 9.19s	remaining: 48.7s
    1588:	learn: 83456.9794321	test: 117492.8441181	best: 117492.8441181 (1588)	total: 9.2s	remaining: 48.7s
    1589:	learn: 83446.9432651	test: 117489.8649578	best: 117489.8649578 (1589)	total: 9.2s	remaining: 48.7s
    1590:	learn: 83432.6986810	test: 117482.1231989	best: 117482.1231989 (1590)	total: 9.21s	remaining: 48.7s
    1591:	learn: 83423.4640404	test: 117470.9691059	best: 117470.9691059 (1591)	total: 9.21s	remaining: 48.7s
    1592:	learn: 83415.4637619	test: 117473.2005177	best: 117470.9691059 (1591)	total: 9.22s	remaining: 48.6s
    1593:	learn: 83405.8914773	test: 117470.9985864	best: 117470.9691059 (1591)	total: 9.22s	remaining: 48.6s
    1594:	learn: 83394.4497216	test: 117464.5405634	best: 117464.5405634 (1594)	total: 9.23s	remaining: 48.6s
    1595:	learn: 83381.7486297	test: 117464.3973901	best: 117464.3973901 (1595)	total: 9.23s	remaining: 48.6s
    1596:	learn: 83374.7592804	test: 117463.1200356	best: 117463.1200356 (1596)	total: 9.24s	remaining: 48.6s
    1597:	learn: 83366.2397656	test: 117459.3053756	best: 117459.3053756 (1597)	total: 9.24s	remaining: 48.6s
    1598:	learn: 83353.0880736	test: 117452.6014234	best: 117452.6014234 (1598)	total: 9.25s	remaining: 48.6s
    1599:	learn: 83344.4388672	test: 117451.6224489	best: 117451.6224489 (1599)	total: 9.26s	remaining: 48.6s
    1600:	learn: 83322.0584410	test: 117422.2102163	best: 117422.2102163 (1600)	total: 9.26s	remaining: 48.6s
    1601:	learn: 83312.4296080	test: 117421.6960444	best: 117421.6960444 (1601)	total: 9.27s	remaining: 48.6s
    1602:	learn: 83295.1963446	test: 117415.4172929	best: 117415.4172929 (1602)	total: 9.27s	remaining: 48.6s
    1603:	learn: 83277.2759394	test: 117418.5451872	best: 117415.4172929 (1602)	total: 9.28s	remaining: 48.6s
    1604:	learn: 83255.5863685	test: 117389.7897638	best: 117389.7897638 (1604)	total: 9.28s	remaining: 48.6s
    1605:	learn: 83238.5079826	test: 117385.3624549	best: 117385.3624549 (1605)	total: 9.29s	remaining: 48.5s
    1606:	learn: 83229.7922754	test: 117379.8508009	best: 117379.8508009 (1606)	total: 9.29s	remaining: 48.5s
    1607:	learn: 83213.4504800	test: 117375.5078608	best: 117375.5078608 (1607)	total: 9.3s	remaining: 48.5s
    1608:	learn: 83206.5623323	test: 117374.5165763	best: 117374.5165763 (1608)	total: 9.3s	remaining: 48.5s
    1609:	learn: 83192.6057061	test: 117374.7233393	best: 117374.5165763 (1608)	total: 9.31s	remaining: 48.5s
    1610:	learn: 83180.8731447	test: 117369.7106942	best: 117369.7106942 (1610)	total: 9.31s	remaining: 48.5s
    1611:	learn: 83169.0659626	test: 117364.5693304	best: 117364.5693304 (1611)	total: 9.32s	remaining: 48.5s
    1612:	learn: 83160.2106722	test: 117368.0140649	best: 117364.5693304 (1611)	total: 9.32s	remaining: 48.5s
    1613:	learn: 83148.9461560	test: 117365.2602150	best: 117364.5693304 (1611)	total: 9.33s	remaining: 48.5s
    1614:	learn: 83133.9186672	test: 117367.2140680	best: 117364.5693304 (1611)	total: 9.34s	remaining: 48.5s
    1615:	learn: 83117.5942173	test: 117368.7522068	best: 117364.5693304 (1611)	total: 9.34s	remaining: 48.5s
    1616:	learn: 83110.2892224	test: 117370.2768760	best: 117364.5693304 (1611)	total: 9.35s	remaining: 48.5s
    1617:	learn: 83101.4168078	test: 117366.8179299	best: 117364.5693304 (1611)	total: 9.35s	remaining: 48.5s
    1618:	learn: 83092.2414887	test: 117363.4733312	best: 117363.4733312 (1618)	total: 9.36s	remaining: 48.4s
    1619:	learn: 83075.8676831	test: 117359.3372714	best: 117359.3372714 (1619)	total: 9.37s	remaining: 48.4s
    1620:	learn: 83067.9788049	test: 117348.3258289	best: 117348.3258289 (1620)	total: 9.37s	remaining: 48.4s
    1621:	learn: 83055.8257074	test: 117347.5146004	best: 117347.5146004 (1621)	total: 9.38s	remaining: 48.4s
    1622:	learn: 83043.8357623	test: 117341.0552997	best: 117341.0552997 (1622)	total: 9.38s	remaining: 48.4s
    1623:	learn: 83034.4800605	test: 117334.9334827	best: 117334.9334827 (1623)	total: 9.39s	remaining: 48.4s
    1624:	learn: 83021.9669811	test: 117333.6985182	best: 117333.6985182 (1624)	total: 9.39s	remaining: 48.4s
    1625:	learn: 83014.3095835	test: 117331.4243962	best: 117331.4243962 (1625)	total: 9.4s	remaining: 48.4s
    1626:	learn: 83000.2774398	test: 117328.1861613	best: 117328.1861613 (1626)	total: 9.4s	remaining: 48.4s
    1627:	learn: 82989.9927129	test: 117317.0356241	best: 117317.0356241 (1627)	total: 9.41s	remaining: 48.4s
    1628:	learn: 82982.2483962	test: 117312.8532618	best: 117312.8532618 (1628)	total: 9.41s	remaining: 48.4s
    1629:	learn: 82976.3995515	test: 117311.4376896	best: 117311.4376896 (1629)	total: 9.42s	remaining: 48.4s
    1630:	learn: 82964.7409596	test: 117313.2597849	best: 117311.4376896 (1629)	total: 9.43s	remaining: 48.4s
    1631:	learn: 82952.8469211	test: 117321.8094031	best: 117311.4376896 (1629)	total: 9.43s	remaining: 48.4s
    1632:	learn: 82945.6803830	test: 117320.6985469	best: 117311.4376896 (1629)	total: 9.44s	remaining: 48.4s
    1633:	learn: 82926.4684122	test: 117314.1838990	best: 117311.4376896 (1629)	total: 9.44s	remaining: 48.4s
    1634:	learn: 82907.9499685	test: 117311.6355272	best: 117311.4376896 (1629)	total: 9.45s	remaining: 48.3s
    1635:	learn: 82890.4197170	test: 117310.2668755	best: 117310.2668755 (1635)	total: 9.46s	remaining: 48.3s
    1636:	learn: 82882.2877656	test: 117307.5066021	best: 117307.5066021 (1636)	total: 9.46s	remaining: 48.3s
    1637:	learn: 82870.1847638	test: 117308.4773407	best: 117307.5066021 (1636)	total: 9.46s	remaining: 48.3s
    1638:	learn: 82860.2748058	test: 117305.5794836	best: 117305.5794836 (1638)	total: 9.47s	remaining: 48.3s
    1639:	learn: 82855.6774777	test: 117305.3672360	best: 117305.3672360 (1639)	total: 9.48s	remaining: 48.3s
    1640:	learn: 82839.1799168	test: 117294.8828289	best: 117294.8828289 (1640)	total: 9.48s	remaining: 48.3s
    1641:	learn: 82827.6151894	test: 117290.7772254	best: 117290.7772254 (1641)	total: 9.49s	remaining: 48.3s
    1642:	learn: 82811.7692718	test: 117296.0284138	best: 117290.7772254 (1641)	total: 9.49s	remaining: 48.3s
    1643:	learn: 82797.1630440	test: 117299.2173456	best: 117290.7772254 (1641)	total: 9.5s	remaining: 48.3s
    1644:	learn: 82784.8025480	test: 117307.8357577	best: 117290.7772254 (1641)	total: 9.5s	remaining: 48.3s
    1645:	learn: 82766.3186140	test: 117305.2731804	best: 117290.7772254 (1641)	total: 9.51s	remaining: 48.3s
    1646:	learn: 82752.7207206	test: 117299.7524915	best: 117290.7772254 (1641)	total: 9.52s	remaining: 48.3s
    1647:	learn: 82744.5533808	test: 117294.5253946	best: 117290.7772254 (1641)	total: 9.52s	remaining: 48.3s
    1648:	learn: 82729.7703728	test: 117295.2174322	best: 117290.7772254 (1641)	total: 9.53s	remaining: 48.3s
    1649:	learn: 82719.4026753	test: 117289.2659151	best: 117289.2659151 (1649)	total: 9.54s	remaining: 48.3s
    1650:	learn: 82706.5966052	test: 117282.4369973	best: 117282.4369973 (1650)	total: 9.54s	remaining: 48.3s
    1651:	learn: 82698.6793376	test: 117279.9443840	best: 117279.9443840 (1651)	total: 9.55s	remaining: 48.2s
    1652:	learn: 82687.0948229	test: 117276.2812957	best: 117276.2812957 (1652)	total: 9.55s	remaining: 48.2s
    1653:	learn: 82676.2116980	test: 117273.7757003	best: 117273.7757003 (1653)	total: 9.56s	remaining: 48.2s
    1654:	learn: 82664.6303939	test: 117269.9411312	best: 117269.9411312 (1654)	total: 9.56s	remaining: 48.2s
    1655:	learn: 82656.9626778	test: 117266.4780130	best: 117266.4780130 (1655)	total: 9.57s	remaining: 48.2s
    1656:	learn: 82642.0255337	test: 117259.7246559	best: 117259.7246559 (1656)	total: 9.57s	remaining: 48.2s
    1657:	learn: 82626.8223321	test: 117246.0884040	best: 117246.0884040 (1657)	total: 9.58s	remaining: 48.2s
    1658:	learn: 82613.4954591	test: 117242.9927906	best: 117242.9927906 (1658)	total: 9.59s	remaining: 48.2s
    1659:	learn: 82597.1658429	test: 117229.1152168	best: 117229.1152168 (1659)	total: 9.59s	remaining: 48.2s
    1660:	learn: 82588.6503265	test: 117227.8373820	best: 117227.8373820 (1660)	total: 9.6s	remaining: 48.2s
    1661:	learn: 82576.9542712	test: 117213.7201978	best: 117213.7201978 (1661)	total: 9.6s	remaining: 48.2s
    1662:	learn: 82567.2505749	test: 117211.3959454	best: 117211.3959454 (1662)	total: 9.61s	remaining: 48.2s
    1663:	learn: 82555.0584496	test: 117205.6999161	best: 117205.6999161 (1663)	total: 9.61s	remaining: 48.2s
    1664:	learn: 82546.1983732	test: 117204.4621017	best: 117204.4621017 (1664)	total: 9.62s	remaining: 48.2s
    1665:	learn: 82529.2675260	test: 117193.4837495	best: 117193.4837495 (1665)	total: 9.63s	remaining: 48.2s
    1666:	learn: 82513.7266057	test: 117204.3873205	best: 117193.4837495 (1665)	total: 9.63s	remaining: 48.2s
    1667:	learn: 82502.2291063	test: 117197.9080935	best: 117193.4837495 (1665)	total: 9.64s	remaining: 48.2s
    1668:	learn: 82495.6901062	test: 117199.7909395	best: 117193.4837495 (1665)	total: 9.64s	remaining: 48.1s
    1669:	learn: 82480.2311836	test: 117195.1721444	best: 117193.4837495 (1665)	total: 9.65s	remaining: 48.1s
    1670:	learn: 82469.0043083	test: 117190.1237447	best: 117190.1237447 (1670)	total: 9.66s	remaining: 48.1s
    1671:	learn: 82459.9853244	test: 117190.6001772	best: 117190.1237447 (1670)	total: 9.66s	remaining: 48.1s
    1672:	learn: 82443.7837258	test: 117191.6357137	best: 117190.1237447 (1670)	total: 9.67s	remaining: 48.1s
    1673:	learn: 82426.1872201	test: 117195.1943718	best: 117190.1237447 (1670)	total: 9.68s	remaining: 48.1s
    1674:	learn: 82410.0386194	test: 117185.3929994	best: 117185.3929994 (1674)	total: 9.68s	remaining: 48.1s
    1675:	learn: 82398.0869426	test: 117180.7852019	best: 117180.7852019 (1675)	total: 9.69s	remaining: 48.1s
    1676:	learn: 82386.5943702	test: 117175.8552430	best: 117175.8552430 (1676)	total: 9.7s	remaining: 48.1s
    1677:	learn: 82375.4878643	test: 117169.4711311	best: 117169.4711311 (1677)	total: 9.7s	remaining: 48.1s
    1678:	learn: 82363.5747272	test: 117166.5711025	best: 117166.5711025 (1678)	total: 9.71s	remaining: 48.1s
    1679:	learn: 82352.1204813	test: 117173.9948330	best: 117166.5711025 (1678)	total: 9.72s	remaining: 48.1s
    1680:	learn: 82335.4130916	test: 117170.1414430	best: 117166.5711025 (1678)	total: 9.72s	remaining: 48.1s
    1681:	learn: 82324.8965925	test: 117166.2873909	best: 117166.2873909 (1681)	total: 9.73s	remaining: 48.1s
    1682:	learn: 82312.8176060	test: 117161.7418773	best: 117161.7418773 (1682)	total: 9.73s	remaining: 48.1s
    1683:	learn: 82299.8611984	test: 117160.0976385	best: 117160.0976385 (1683)	total: 9.74s	remaining: 48.1s
    1684:	learn: 82290.4143435	test: 117161.2335986	best: 117160.0976385 (1683)	total: 9.75s	remaining: 48.1s
    1685:	learn: 82286.2770402	test: 117171.1466272	best: 117160.0976385 (1683)	total: 9.75s	remaining: 48.1s
    1686:	learn: 82275.8719425	test: 117166.5479257	best: 117160.0976385 (1683)	total: 9.76s	remaining: 48.1s
    1687:	learn: 82265.4505314	test: 117166.2319108	best: 117160.0976385 (1683)	total: 9.76s	remaining: 48.1s
    1688:	learn: 82257.6455753	test: 117166.2961923	best: 117160.0976385 (1683)	total: 9.77s	remaining: 48.1s
    1689:	learn: 82246.8943803	test: 117161.4954853	best: 117160.0976385 (1683)	total: 9.77s	remaining: 48.1s
    1690:	learn: 82237.0480462	test: 117160.7354953	best: 117160.0976385 (1683)	total: 9.78s	remaining: 48.1s
    1691:	learn: 82225.4654592	test: 117154.7849879	best: 117154.7849879 (1691)	total: 9.79s	remaining: 48.1s
    1692:	learn: 82209.2970884	test: 117151.1968651	best: 117151.1968651 (1692)	total: 9.79s	remaining: 48.1s
    1693:	learn: 82190.6727766	test: 117142.8884385	best: 117142.8884385 (1693)	total: 9.8s	remaining: 48s
    1694:	learn: 82181.9587675	test: 117137.2605198	best: 117137.2605198 (1694)	total: 9.81s	remaining: 48s
    1695:	learn: 82172.0380058	test: 117139.5806036	best: 117137.2605198 (1694)	total: 9.81s	remaining: 48s
    1696:	learn: 82162.5151797	test: 117135.9308597	best: 117135.9308597 (1696)	total: 9.82s	remaining: 48s
    1697:	learn: 82149.7329188	test: 117135.3924598	best: 117135.3924598 (1697)	total: 9.82s	remaining: 48s
    1698:	learn: 82139.4401805	test: 117144.7921564	best: 117135.3924598 (1697)	total: 9.83s	remaining: 48s
    1699:	learn: 82128.1933891	test: 117150.7682592	best: 117135.3924598 (1697)	total: 9.84s	remaining: 48s
    1700:	learn: 82103.8239768	test: 117132.5238631	best: 117132.5238631 (1700)	total: 9.84s	remaining: 48s
    1701:	learn: 82089.0744869	test: 117129.0153848	best: 117129.0153848 (1701)	total: 9.85s	remaining: 48s
    1702:	learn: 82078.7885469	test: 117127.1490149	best: 117127.1490149 (1702)	total: 9.86s	remaining: 48s
    1703:	learn: 82071.0075502	test: 117126.3228136	best: 117126.3228136 (1703)	total: 9.86s	remaining: 48s
    1704:	learn: 82052.9550012	test: 117114.7742714	best: 117114.7742714 (1704)	total: 9.87s	remaining: 48s
    1705:	learn: 82044.7406599	test: 117108.7310195	best: 117108.7310195 (1705)	total: 9.87s	remaining: 48s
    1706:	learn: 82026.5835395	test: 117107.5492409	best: 117107.5492409 (1706)	total: 9.88s	remaining: 48s
    1707:	learn: 82019.1021966	test: 117109.8805454	best: 117107.5492409 (1706)	total: 9.89s	remaining: 48s
    1708:	learn: 82013.7726446	test: 117110.9555876	best: 117107.5492409 (1706)	total: 9.89s	remaining: 48s
    1709:	learn: 82003.4614713	test: 117108.6715520	best: 117107.5492409 (1706)	total: 9.9s	remaining: 48s
    1710:	learn: 81991.1134577	test: 117106.7719607	best: 117106.7719607 (1710)	total: 9.91s	remaining: 48s
    1711:	learn: 81979.0032918	test: 117103.3494304	best: 117103.3494304 (1711)	total: 9.91s	remaining: 48s
    1712:	learn: 81968.0809519	test: 117103.1911940	best: 117103.1911940 (1712)	total: 9.92s	remaining: 48s
    1713:	learn: 81948.7017498	test: 117094.3191112	best: 117094.3191112 (1713)	total: 9.93s	remaining: 48s
    1714:	learn: 81933.1915614	test: 117089.7617570	best: 117089.7617570 (1714)	total: 9.93s	remaining: 48s
    1715:	learn: 81916.0784000	test: 117088.2700803	best: 117088.2700803 (1715)	total: 9.94s	remaining: 48s
    1716:	learn: 81904.0205450	test: 117080.9462806	best: 117080.9462806 (1716)	total: 9.95s	remaining: 48s
    1717:	learn: 81894.1251535	test: 117078.6194541	best: 117078.6194541 (1717)	total: 9.95s	remaining: 48s
    1718:	learn: 81887.8588406	test: 117078.7922607	best: 117078.6194541 (1717)	total: 9.96s	remaining: 48s
    1719:	learn: 81873.6956411	test: 117075.4359870	best: 117075.4359870 (1719)	total: 9.96s	remaining: 48s
    1720:	learn: 81859.6340950	test: 117078.2848481	best: 117075.4359870 (1719)	total: 9.97s	remaining: 48s
    1721:	learn: 81839.5126901	test: 117066.7129802	best: 117066.7129802 (1721)	total: 9.98s	remaining: 48s
    1722:	learn: 81829.6132500	test: 117079.0945593	best: 117066.7129802 (1721)	total: 9.98s	remaining: 47.9s
    1723:	learn: 81813.6831900	test: 117076.2978707	best: 117066.7129802 (1721)	total: 9.99s	remaining: 47.9s
    1724:	learn: 81801.5546044	test: 117074.0863871	best: 117066.7129802 (1721)	total: 9.99s	remaining: 47.9s
    1725:	learn: 81781.4711069	test: 117065.1621854	best: 117065.1621854 (1725)	total: 10s	remaining: 47.9s
    1726:	learn: 81770.3691537	test: 117066.8633964	best: 117065.1621854 (1725)	total: 10s	remaining: 47.9s
    1727:	learn: 81753.1494391	test: 117057.4568774	best: 117057.4568774 (1727)	total: 10s	remaining: 47.9s
    1728:	learn: 81745.5413853	test: 117052.4810872	best: 117052.4810872 (1728)	total: 10s	remaining: 47.9s
    1729:	learn: 81737.9836359	test: 117052.0527664	best: 117052.0527664 (1729)	total: 10s	remaining: 47.9s
    1730:	learn: 81727.2886926	test: 117050.8913926	best: 117050.8913926 (1730)	total: 10s	remaining: 47.9s
    1731:	learn: 81716.1237100	test: 117050.5291632	best: 117050.5291632 (1731)	total: 10s	remaining: 47.9s
    1732:	learn: 81705.4998636	test: 117046.5543627	best: 117046.5543627 (1732)	total: 10s	remaining: 47.9s
    1733:	learn: 81688.4681949	test: 117042.6877001	best: 117042.6877001 (1733)	total: 10s	remaining: 47.9s
    1734:	learn: 81677.4822732	test: 117037.9911313	best: 117037.9911313 (1734)	total: 10s	remaining: 47.9s
    1735:	learn: 81662.8007854	test: 117039.8671916	best: 117037.9911313 (1734)	total: 10.1s	remaining: 47.9s
    1736:	learn: 81647.5270335	test: 117036.6389036	best: 117036.6389036 (1736)	total: 10.1s	remaining: 47.9s
    1737:	learn: 81643.9143383	test: 117034.6002554	best: 117034.6002554 (1737)	total: 10.1s	remaining: 47.9s
    1738:	learn: 81629.0869250	test: 117031.5682582	best: 117031.5682582 (1738)	total: 10.1s	remaining: 47.8s
    1739:	learn: 81620.5865623	test: 117028.8869121	best: 117028.8869121 (1739)	total: 10.1s	remaining: 47.8s
    1740:	learn: 81602.3804592	test: 117021.0743925	best: 117021.0743925 (1740)	total: 10.1s	remaining: 47.8s
    1741:	learn: 81591.5248186	test: 117018.8059680	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1742:	learn: 81582.2589101	test: 117024.7072558	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1743:	learn: 81569.3982897	test: 117022.1957659	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1744:	learn: 81560.9090556	test: 117023.1099261	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1745:	learn: 81551.5084988	test: 117024.6178749	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1746:	learn: 81537.2387558	test: 117026.2607594	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1747:	learn: 81522.0631076	test: 117027.3043507	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1748:	learn: 81514.4699081	test: 117026.3754000	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1749:	learn: 81501.8789216	test: 117023.1403736	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1750:	learn: 81489.6230492	test: 117020.0413069	best: 117018.8059680 (1741)	total: 10.1s	remaining: 47.8s
    1751:	learn: 81472.5749064	test: 117015.3384731	best: 117015.3384731 (1751)	total: 10.1s	remaining: 47.8s
    1752:	learn: 81464.2082916	test: 117013.6285033	best: 117013.6285033 (1752)	total: 10.2s	remaining: 47.8s
    1753:	learn: 81449.5363910	test: 117013.1628627	best: 117013.1628627 (1753)	total: 10.2s	remaining: 47.7s
    1754:	learn: 81437.8213464	test: 117006.1683647	best: 117006.1683647 (1754)	total: 10.2s	remaining: 47.7s
    1755:	learn: 81428.7765576	test: 117000.7351196	best: 117000.7351196 (1755)	total: 10.2s	remaining: 47.7s
    1756:	learn: 81421.4081033	test: 116999.6786444	best: 116999.6786444 (1756)	total: 10.2s	remaining: 47.7s
    1757:	learn: 81412.3207054	test: 116991.5932697	best: 116991.5932697 (1757)	total: 10.2s	remaining: 47.7s
    1758:	learn: 81397.7253159	test: 116984.0524426	best: 116984.0524426 (1758)	total: 10.2s	remaining: 47.7s
    1759:	learn: 81389.0496475	test: 116980.7261564	best: 116980.7261564 (1759)	total: 10.2s	remaining: 47.7s
    1760:	learn: 81374.4096345	test: 116977.7016337	best: 116977.7016337 (1760)	total: 10.2s	remaining: 47.7s
    1761:	learn: 81357.8457134	test: 116984.9627349	best: 116977.7016337 (1760)	total: 10.2s	remaining: 47.7s
    1762:	learn: 81351.5443311	test: 116984.1837523	best: 116977.7016337 (1760)	total: 10.2s	remaining: 47.7s
    1763:	learn: 81332.1626165	test: 116967.7391764	best: 116967.7391764 (1763)	total: 10.2s	remaining: 47.7s
    1764:	learn: 81321.7769952	test: 116962.3239325	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.7s
    1765:	learn: 81310.4095055	test: 116965.7292418	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.7s
    1766:	learn: 81294.5322803	test: 116968.9724178	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.7s
    1767:	learn: 81281.5814634	test: 116965.5865214	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.7s
    1768:	learn: 81271.7259505	test: 116966.2438373	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.7s
    1769:	learn: 81263.8090584	test: 116962.9593653	best: 116962.3239325 (1764)	total: 10.2s	remaining: 47.6s
    1770:	learn: 81252.3570968	test: 116959.4004502	best: 116959.4004502 (1770)	total: 10.3s	remaining: 47.6s
    1771:	learn: 81238.7505235	test: 116948.3974451	best: 116948.3974451 (1771)	total: 10.3s	remaining: 47.6s
    1772:	learn: 81228.3542322	test: 116946.3816526	best: 116946.3816526 (1772)	total: 10.3s	remaining: 47.6s
    1773:	learn: 81212.3996750	test: 116945.0413794	best: 116945.0413794 (1773)	total: 10.3s	remaining: 47.6s
    1774:	learn: 81201.3033126	test: 116934.1946649	best: 116934.1946649 (1774)	total: 10.3s	remaining: 47.6s
    1775:	learn: 81189.7583336	test: 116931.5606682	best: 116931.5606682 (1775)	total: 10.3s	remaining: 47.6s
    1776:	learn: 81181.5629465	test: 116921.3781434	best: 116921.3781434 (1776)	total: 10.3s	remaining: 47.6s
    1777:	learn: 81169.6044040	test: 116913.4598982	best: 116913.4598982 (1777)	total: 10.3s	remaining: 47.6s
    1778:	learn: 81161.8788820	test: 116914.9965315	best: 116913.4598982 (1777)	total: 10.3s	remaining: 47.6s
    1779:	learn: 81151.3749453	test: 116912.4759049	best: 116912.4759049 (1779)	total: 10.3s	remaining: 47.6s
    1780:	learn: 81138.4915951	test: 116911.4045151	best: 116911.4045151 (1780)	total: 10.3s	remaining: 47.6s
    1781:	learn: 81127.4603211	test: 116912.9040969	best: 116911.4045151 (1780)	total: 10.3s	remaining: 47.6s
    1782:	learn: 81109.2972667	test: 116901.2545631	best: 116901.2545631 (1782)	total: 10.3s	remaining: 47.6s
    1783:	learn: 81103.0225664	test: 116900.6521366	best: 116900.6521366 (1783)	total: 10.3s	remaining: 47.5s
    1784:	learn: 81085.8420333	test: 116899.8584406	best: 116899.8584406 (1784)	total: 10.3s	remaining: 47.5s
    1785:	learn: 81077.5249636	test: 116901.5545120	best: 116899.8584406 (1784)	total: 10.3s	remaining: 47.5s
    1786:	learn: 81068.1010563	test: 116896.3490153	best: 116896.3490153 (1786)	total: 10.3s	remaining: 47.5s
    1787:	learn: 81055.9552219	test: 116900.0729090	best: 116896.3490153 (1786)	total: 10.3s	remaining: 47.5s
    1788:	learn: 81049.2624361	test: 116899.3226208	best: 116896.3490153 (1786)	total: 10.4s	remaining: 47.5s
    1789:	learn: 81036.7620104	test: 116890.9808873	best: 116890.9808873 (1789)	total: 10.4s	remaining: 47.5s
    1790:	learn: 81027.9287869	test: 116886.4231237	best: 116886.4231237 (1790)	total: 10.4s	remaining: 47.5s
    1791:	learn: 81017.9554027	test: 116881.8602430	best: 116881.8602430 (1791)	total: 10.4s	remaining: 47.5s
    1792:	learn: 81003.6953960	test: 116874.3931445	best: 116874.3931445 (1792)	total: 10.4s	remaining: 47.5s
    1793:	learn: 80990.5517864	test: 116873.9417883	best: 116873.9417883 (1793)	total: 10.4s	remaining: 47.5s
    1794:	learn: 80986.8598782	test: 116876.5892802	best: 116873.9417883 (1793)	total: 10.4s	remaining: 47.5s
    1795:	learn: 80971.0455555	test: 116883.7357355	best: 116873.9417883 (1793)	total: 10.4s	remaining: 47.5s
    1796:	learn: 80960.8475713	test: 116886.6394982	best: 116873.9417883 (1793)	total: 10.4s	remaining: 47.5s
    1797:	learn: 80948.9263165	test: 116873.5757969	best: 116873.5757969 (1797)	total: 10.4s	remaining: 47.5s
    1798:	learn: 80936.0201713	test: 116867.6871629	best: 116867.6871629 (1798)	total: 10.4s	remaining: 47.5s
    1799:	learn: 80927.9503135	test: 116868.6218565	best: 116867.6871629 (1798)	total: 10.4s	remaining: 47.4s
    1800:	learn: 80918.3437592	test: 116866.3004771	best: 116866.3004771 (1800)	total: 10.4s	remaining: 47.4s
    1801:	learn: 80906.6705916	test: 116869.3678300	best: 116866.3004771 (1800)	total: 10.4s	remaining: 47.4s
    1802:	learn: 80896.9530464	test: 116865.7492193	best: 116865.7492193 (1802)	total: 10.4s	remaining: 47.4s
    1803:	learn: 80887.1659291	test: 116866.3907038	best: 116865.7492193 (1802)	total: 10.4s	remaining: 47.4s
    1804:	learn: 80873.6700845	test: 116869.5879969	best: 116865.7492193 (1802)	total: 10.4s	remaining: 47.4s
    1805:	learn: 80863.6996346	test: 116875.3557433	best: 116865.7492193 (1802)	total: 10.4s	remaining: 47.4s
    1806:	learn: 80853.6141645	test: 116873.0517424	best: 116865.7492193 (1802)	total: 10.5s	remaining: 47.4s
    1807:	learn: 80841.4172344	test: 116863.9470719	best: 116863.9470719 (1807)	total: 10.5s	remaining: 47.4s
    1808:	learn: 80834.5884801	test: 116857.0072521	best: 116857.0072521 (1808)	total: 10.5s	remaining: 47.4s
    1809:	learn: 80817.9675631	test: 116853.8128231	best: 116853.8128231 (1809)	total: 10.5s	remaining: 47.4s
    1810:	learn: 80808.8332927	test: 116849.8954581	best: 116849.8954581 (1810)	total: 10.5s	remaining: 47.4s
    1811:	learn: 80800.8102862	test: 116845.4068599	best: 116845.4068599 (1811)	total: 10.5s	remaining: 47.4s
    1812:	learn: 80792.2161357	test: 116844.5023886	best: 116844.5023886 (1812)	total: 10.5s	remaining: 47.4s
    1813:	learn: 80782.6355813	test: 116838.4895298	best: 116838.4895298 (1813)	total: 10.5s	remaining: 47.4s
    1814:	learn: 80776.8943717	test: 116840.2705689	best: 116838.4895298 (1813)	total: 10.5s	remaining: 47.3s
    1815:	learn: 80767.7383276	test: 116835.7970883	best: 116835.7970883 (1815)	total: 10.5s	remaining: 47.3s
    1816:	learn: 80760.6445382	test: 116839.8229505	best: 116835.7970883 (1815)	total: 10.5s	remaining: 47.3s
    1817:	learn: 80749.0351384	test: 116839.1615290	best: 116835.7970883 (1815)	total: 10.5s	remaining: 47.3s
    1818:	learn: 80729.8525462	test: 116840.9062862	best: 116835.7970883 (1815)	total: 10.5s	remaining: 47.3s
    1819:	learn: 80717.8697256	test: 116834.3839169	best: 116834.3839169 (1819)	total: 10.5s	remaining: 47.3s
    1820:	learn: 80712.2908126	test: 116836.2203278	best: 116834.3839169 (1819)	total: 10.5s	remaining: 47.3s
    1821:	learn: 80703.2630077	test: 116829.4450349	best: 116829.4450349 (1821)	total: 10.5s	remaining: 47.3s
    1822:	learn: 80689.2036396	test: 116826.6539306	best: 116826.6539306 (1822)	total: 10.5s	remaining: 47.3s
    1823:	learn: 80678.1353359	test: 116824.2812053	best: 116824.2812053 (1823)	total: 10.5s	remaining: 47.3s
    1824:	learn: 80665.2968299	test: 116824.6685385	best: 116824.2812053 (1823)	total: 10.6s	remaining: 47.3s
    1825:	learn: 80649.8593935	test: 116810.3098903	best: 116810.3098903 (1825)	total: 10.6s	remaining: 47.3s
    1826:	learn: 80643.4006172	test: 116808.9777402	best: 116808.9777402 (1826)	total: 10.6s	remaining: 47.3s
    1827:	learn: 80638.1309958	test: 116817.8623118	best: 116808.9777402 (1826)	total: 10.6s	remaining: 47.3s
    1828:	learn: 80629.5266701	test: 116815.4204516	best: 116808.9777402 (1826)	total: 10.6s	remaining: 47.3s
    1829:	learn: 80619.7971192	test: 116810.2046564	best: 116808.9777402 (1826)	total: 10.6s	remaining: 47.3s
    1830:	learn: 80609.7608814	test: 116799.5687865	best: 116799.5687865 (1830)	total: 10.6s	remaining: 47.3s
    1831:	learn: 80589.3947949	test: 116799.8790605	best: 116799.5687865 (1830)	total: 10.6s	remaining: 47.3s
    1832:	learn: 80575.8447188	test: 116795.7153088	best: 116795.7153088 (1832)	total: 10.6s	remaining: 47.3s
    1833:	learn: 80565.1880796	test: 116795.3746088	best: 116795.3746088 (1833)	total: 10.6s	remaining: 47.3s
    1834:	learn: 80548.3197968	test: 116796.0707338	best: 116795.3746088 (1833)	total: 10.6s	remaining: 47.2s
    1835:	learn: 80538.0976641	test: 116795.1766625	best: 116795.1766625 (1835)	total: 10.6s	remaining: 47.2s
    1836:	learn: 80530.3399838	test: 116794.0360075	best: 116794.0360075 (1836)	total: 10.6s	remaining: 47.2s
    1837:	learn: 80516.4004839	test: 116788.5801776	best: 116788.5801776 (1837)	total: 10.6s	remaining: 47.2s
    1838:	learn: 80506.3497303	test: 116788.8374216	best: 116788.5801776 (1837)	total: 10.6s	remaining: 47.2s
    1839:	learn: 80491.7912662	test: 116777.2747979	best: 116777.2747979 (1839)	total: 10.6s	remaining: 47.2s
    1840:	learn: 80482.8451824	test: 116779.4023176	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1841:	learn: 80473.9833513	test: 116778.6964083	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1842:	learn: 80458.2154896	test: 116780.4673266	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1843:	learn: 80448.9903985	test: 116777.8718145	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1844:	learn: 80433.3093484	test: 116786.0767863	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1845:	learn: 80428.1793825	test: 116794.8208895	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1846:	learn: 80421.1991833	test: 116799.1268127	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1847:	learn: 80413.7755056	test: 116784.4313745	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1848:	learn: 80405.3057550	test: 116784.0534263	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1849:	learn: 80397.0195612	test: 116788.5542803	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1850:	learn: 80380.0936204	test: 116787.2086222	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.2s
    1851:	learn: 80368.9504263	test: 116783.3312747	best: 116777.2747979 (1839)	total: 10.7s	remaining: 47.1s
    1852:	learn: 80354.5908493	test: 116772.5863480	best: 116772.5863480 (1852)	total: 10.7s	remaining: 47.1s
    1853:	learn: 80348.2572616	test: 116772.6107971	best: 116772.5863480 (1852)	total: 10.7s	remaining: 47.1s
    1854:	learn: 80336.6000383	test: 116766.2927607	best: 116766.2927607 (1854)	total: 10.7s	remaining: 47.1s
    1855:	learn: 80327.3003629	test: 116755.9544383	best: 116755.9544383 (1855)	total: 10.7s	remaining: 47.1s
    1856:	learn: 80319.2447609	test: 116767.0050798	best: 116755.9544383 (1855)	total: 10.7s	remaining: 47.1s
    1857:	learn: 80311.6361951	test: 116764.8509772	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1858:	learn: 80305.2623713	test: 116766.9400249	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1859:	learn: 80290.0973798	test: 116775.0880627	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1860:	learn: 80281.3503580	test: 116771.4417934	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1861:	learn: 80267.9056014	test: 116768.7394677	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1862:	learn: 80250.7705755	test: 116775.9100012	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1863:	learn: 80239.1884572	test: 116772.1070994	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1864:	learn: 80227.3040829	test: 116766.6599415	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1865:	learn: 80214.3813496	test: 116760.1236113	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1866:	learn: 80206.6098588	test: 116771.0849952	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1867:	learn: 80197.1947295	test: 116782.8285017	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1868:	learn: 80192.8746387	test: 116781.7591410	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1869:	learn: 80185.9419090	test: 116782.4988483	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1870:	learn: 80169.8815953	test: 116789.4573510	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1871:	learn: 80162.8965066	test: 116788.7152526	best: 116755.9544383 (1855)	total: 10.8s	remaining: 47.1s
    1872:	learn: 80150.1208462	test: 116782.3949774	best: 116755.9544383 (1855)	total: 10.9s	remaining: 47.1s
    1873:	learn: 80131.9057886	test: 116772.1518778	best: 116755.9544383 (1855)	total: 10.9s	remaining: 47.1s
    1874:	learn: 80122.2789105	test: 116765.7039769	best: 116755.9544383 (1855)	total: 10.9s	remaining: 47.1s
    1875:	learn: 80102.9922727	test: 116757.5263142	best: 116755.9544383 (1855)	total: 10.9s	remaining: 47.1s
    1876:	learn: 80088.1139752	test: 116754.7109326	best: 116754.7109326 (1876)	total: 10.9s	remaining: 47.1s
    1877:	learn: 80079.4600394	test: 116751.4635490	best: 116751.4635490 (1877)	total: 10.9s	remaining: 47.1s
    1878:	learn: 80061.3026604	test: 116751.1540795	best: 116751.1540795 (1878)	total: 10.9s	remaining: 47.1s
    1879:	learn: 80052.9565426	test: 116749.4122806	best: 116749.4122806 (1879)	total: 10.9s	remaining: 47.1s
    1880:	learn: 80043.7545585	test: 116746.9825155	best: 116746.9825155 (1880)	total: 10.9s	remaining: 47.1s
    1881:	learn: 80027.5455734	test: 116748.0073186	best: 116746.9825155 (1880)	total: 10.9s	remaining: 47.1s
    1882:	learn: 80013.2460635	test: 116739.6023555	best: 116739.6023555 (1882)	total: 10.9s	remaining: 47.1s
    1883:	learn: 80007.5490556	test: 116736.0192974	best: 116736.0192974 (1883)	total: 10.9s	remaining: 47.1s
    1884:	learn: 79999.4497477	test: 116739.2427221	best: 116736.0192974 (1883)	total: 10.9s	remaining: 47.1s
    1885:	learn: 79989.5970968	test: 116734.7291479	best: 116734.7291479 (1885)	total: 10.9s	remaining: 47.1s
    1886:	learn: 79974.6371160	test: 116739.9341562	best: 116734.7291479 (1885)	total: 10.9s	remaining: 47s
    1887:	learn: 79968.4716537	test: 116737.6791234	best: 116734.7291479 (1885)	total: 10.9s	remaining: 47s
    1888:	learn: 79962.9082198	test: 116738.3997349	best: 116734.7291479 (1885)	total: 11s	remaining: 47s
    1889:	learn: 79955.0859404	test: 116737.4500016	best: 116734.7291479 (1885)	total: 11s	remaining: 47s
    1890:	learn: 79944.2051181	test: 116728.9653494	best: 116728.9653494 (1890)	total: 11s	remaining: 47s
    1891:	learn: 79934.5838797	test: 116719.1537800	best: 116719.1537800 (1891)	total: 11s	remaining: 47s
    1892:	learn: 79926.1196640	test: 116720.3038676	best: 116719.1537800 (1891)	total: 11s	remaining: 47s
    1893:	learn: 79916.5172448	test: 116714.1978504	best: 116714.1978504 (1893)	total: 11s	remaining: 47s
    1894:	learn: 79908.3641217	test: 116711.9682892	best: 116711.9682892 (1894)	total: 11s	remaining: 47s
    1895:	learn: 79898.0692880	test: 116708.6208999	best: 116708.6208999 (1895)	total: 11s	remaining: 47s
    1896:	learn: 79893.0098761	test: 116707.7886629	best: 116707.7886629 (1896)	total: 11s	remaining: 47s
    1897:	learn: 79882.7927061	test: 116711.9046375	best: 116707.7886629 (1896)	total: 11s	remaining: 47s
    1898:	learn: 79871.9192575	test: 116710.3894275	best: 116707.7886629 (1896)	total: 11s	remaining: 47s
    1899:	learn: 79854.4833038	test: 116696.9459647	best: 116696.9459647 (1899)	total: 11s	remaining: 47s
    1900:	learn: 79844.9127193	test: 116695.2708585	best: 116695.2708585 (1900)	total: 11s	remaining: 47s
    1901:	learn: 79829.9715735	test: 116699.8752103	best: 116695.2708585 (1900)	total: 11s	remaining: 46.9s
    1902:	learn: 79822.0305822	test: 116700.9599505	best: 116695.2708585 (1900)	total: 11s	remaining: 46.9s
    1903:	learn: 79808.4135146	test: 116698.9505528	best: 116695.2708585 (1900)	total: 11s	remaining: 46.9s
    1904:	learn: 79800.3288600	test: 116695.6295469	best: 116695.2708585 (1900)	total: 11s	remaining: 46.9s
    1905:	learn: 79789.0364607	test: 116699.4330827	best: 116695.2708585 (1900)	total: 11s	remaining: 46.9s
    1906:	learn: 79775.6996874	test: 116707.6650360	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1907:	learn: 79762.1618916	test: 116713.4889024	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1908:	learn: 79745.9205159	test: 116715.0639280	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1909:	learn: 79740.2872138	test: 116706.7582170	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1910:	learn: 79734.2398372	test: 116719.9594530	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1911:	learn: 79719.1715638	test: 116722.8715332	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1912:	learn: 79712.9820023	test: 116720.3374978	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1913:	learn: 79696.2731506	test: 116709.6904992	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1914:	learn: 79686.5752745	test: 116710.3638521	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1915:	learn: 79677.1790842	test: 116711.2522012	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.9s
    1916:	learn: 79659.6837845	test: 116701.8545033	best: 116695.2708585 (1900)	total: 11.1s	remaining: 46.8s
    1917:	learn: 79649.8122488	test: 116695.0342106	best: 116695.0342106 (1917)	total: 11.1s	remaining: 46.8s
    1918:	learn: 79640.7732240	test: 116690.8085539	best: 116690.8085539 (1918)	total: 11.1s	remaining: 46.8s
    1919:	learn: 79630.9737946	test: 116688.9831325	best: 116688.9831325 (1919)	total: 11.1s	remaining: 46.8s
    1920:	learn: 79616.7611226	test: 116682.9535700	best: 116682.9535700 (1920)	total: 11.1s	remaining: 46.8s
    1921:	learn: 79610.5190836	test: 116685.6936584	best: 116682.9535700 (1920)	total: 11.1s	remaining: 46.8s
    1922:	learn: 79600.8827905	test: 116684.2823622	best: 116682.9535700 (1920)	total: 11.1s	remaining: 46.8s
    1923:	learn: 79595.8294241	test: 116680.1467261	best: 116680.1467261 (1923)	total: 11.1s	remaining: 46.8s
    1924:	learn: 79589.8006483	test: 116679.4677861	best: 116679.4677861 (1924)	total: 11.2s	remaining: 46.8s
    1925:	learn: 79575.3295946	test: 116673.9251626	best: 116673.9251626 (1925)	total: 11.2s	remaining: 46.8s
    1926:	learn: 79563.0824359	test: 116666.4003145	best: 116666.4003145 (1926)	total: 11.2s	remaining: 46.8s
    1927:	learn: 79558.1283376	test: 116665.2431363	best: 116665.2431363 (1927)	total: 11.2s	remaining: 46.8s
    1928:	learn: 79549.5361414	test: 116665.3926233	best: 116665.2431363 (1927)	total: 11.2s	remaining: 46.8s
    1929:	learn: 79542.5799861	test: 116665.0333283	best: 116665.0333283 (1929)	total: 11.2s	remaining: 46.8s
    1930:	learn: 79535.5164537	test: 116662.9755829	best: 116662.9755829 (1930)	total: 11.2s	remaining: 46.7s
    1931:	learn: 79532.2962729	test: 116664.1058867	best: 116662.9755829 (1930)	total: 11.2s	remaining: 46.7s
    1932:	learn: 79513.6294687	test: 116658.3954690	best: 116658.3954690 (1932)	total: 11.2s	remaining: 46.7s
    1933:	learn: 79506.2128891	test: 116651.3763631	best: 116651.3763631 (1933)	total: 11.2s	remaining: 46.7s
    1934:	learn: 79495.3709131	test: 116648.5660320	best: 116648.5660320 (1934)	total: 11.2s	remaining: 46.7s
    1935:	learn: 79472.6112874	test: 116634.6627336	best: 116634.6627336 (1935)	total: 11.2s	remaining: 46.7s
    1936:	learn: 79462.0603834	test: 116631.9729354	best: 116631.9729354 (1936)	total: 11.2s	remaining: 46.7s
    1937:	learn: 79456.8934047	test: 116631.4001622	best: 116631.4001622 (1937)	total: 11.2s	remaining: 46.7s
    1938:	learn: 79440.8323863	test: 116630.1562435	best: 116630.1562435 (1938)	total: 11.2s	remaining: 46.7s
    1939:	learn: 79432.2524771	test: 116620.6159932	best: 116620.6159932 (1939)	total: 11.2s	remaining: 46.7s
    1940:	learn: 79424.7970112	test: 116618.6025164	best: 116618.6025164 (1940)	total: 11.2s	remaining: 46.7s
    1941:	learn: 79418.4610878	test: 116616.6413609	best: 116616.6413609 (1941)	total: 11.2s	remaining: 46.7s
    1942:	learn: 79412.3464728	test: 116610.2795183	best: 116610.2795183 (1942)	total: 11.3s	remaining: 46.7s
    1943:	learn: 79397.4339686	test: 116603.9419228	best: 116603.9419228 (1943)	total: 11.3s	remaining: 46.7s
    1944:	learn: 79385.5733514	test: 116593.7277373	best: 116593.7277373 (1944)	total: 11.3s	remaining: 46.7s
    1945:	learn: 79375.4477151	test: 116593.4254458	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.7s
    1946:	learn: 79366.1455792	test: 116595.8548363	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.7s
    1947:	learn: 79357.4949881	test: 116594.5583633	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.7s
    1948:	learn: 79346.5394685	test: 116596.6025504	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.6s
    1949:	learn: 79336.4051041	test: 116595.9454637	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.6s
    1950:	learn: 79327.5406937	test: 116594.4849038	best: 116593.4254458 (1945)	total: 11.3s	remaining: 46.6s
    1951:	learn: 79316.4571405	test: 116590.1489909	best: 116590.1489909 (1951)	total: 11.3s	remaining: 46.6s
    1952:	learn: 79301.1799092	test: 116583.3412501	best: 116583.3412501 (1952)	total: 11.3s	remaining: 46.6s
    1953:	learn: 79290.5911122	test: 116577.8858363	best: 116577.8858363 (1953)	total: 11.3s	remaining: 46.6s
    1954:	learn: 79279.7958035	test: 116572.2328288	best: 116572.2328288 (1954)	total: 11.3s	remaining: 46.6s
    1955:	learn: 79272.0713897	test: 116581.7954241	best: 116572.2328288 (1954)	total: 11.3s	remaining: 46.6s
    1956:	learn: 79254.7624817	test: 116572.2874440	best: 116572.2328288 (1954)	total: 11.3s	remaining: 46.6s
    1957:	learn: 79252.2733626	test: 116572.4793529	best: 116572.2328288 (1954)	total: 11.3s	remaining: 46.6s
    1958:	learn: 79239.3012600	test: 116564.7046933	best: 116564.7046933 (1958)	total: 11.3s	remaining: 46.6s
    1959:	learn: 79234.3327989	test: 116564.9103166	best: 116564.7046933 (1958)	total: 11.4s	remaining: 46.6s
    1960:	learn: 79228.5965599	test: 116564.2914978	best: 116564.2914978 (1960)	total: 11.4s	remaining: 46.6s
    1961:	learn: 79208.0423989	test: 116566.2889201	best: 116564.2914978 (1960)	total: 11.4s	remaining: 46.6s
    1962:	learn: 79193.9043671	test: 116560.7725463	best: 116560.7725463 (1962)	total: 11.4s	remaining: 46.5s
    1963:	learn: 79184.1727278	test: 116562.2345757	best: 116560.7725463 (1962)	total: 11.4s	remaining: 46.5s
    1964:	learn: 79170.5094054	test: 116558.8111570	best: 116558.8111570 (1964)	total: 11.4s	remaining: 46.5s
    1965:	learn: 79157.3702372	test: 116560.1411900	best: 116558.8111570 (1964)	total: 11.4s	remaining: 46.5s
    1966:	learn: 79146.9909641	test: 116556.2004243	best: 116556.2004243 (1966)	total: 11.4s	remaining: 46.5s
    1967:	learn: 79134.3751552	test: 116562.0503817	best: 116556.2004243 (1966)	total: 11.4s	remaining: 46.5s
    1968:	learn: 79123.0227404	test: 116561.7605568	best: 116556.2004243 (1966)	total: 11.4s	remaining: 46.5s
    1969:	learn: 79118.4518928	test: 116560.2890144	best: 116556.2004243 (1966)	total: 11.4s	remaining: 46.5s
    1970:	learn: 79109.4088816	test: 116556.3277092	best: 116556.2004243 (1966)	total: 11.4s	remaining: 46.5s
    1971:	learn: 79103.8794277	test: 116553.6237779	best: 116553.6237779 (1971)	total: 11.4s	remaining: 46.5s
    1972:	learn: 79093.1263746	test: 116547.4281438	best: 116547.4281438 (1972)	total: 11.4s	remaining: 46.5s
    1973:	learn: 79083.6073074	test: 116543.1252035	best: 116543.1252035 (1973)	total: 11.4s	remaining: 46.5s
    1974:	learn: 79078.6890525	test: 116542.6355757	best: 116542.6355757 (1974)	total: 11.4s	remaining: 46.5s
    1975:	learn: 79067.8121591	test: 116543.2739770	best: 116542.6355757 (1974)	total: 11.4s	remaining: 46.5s
    1976:	learn: 79061.2925617	test: 116540.1740446	best: 116540.1740446 (1976)	total: 11.4s	remaining: 46.5s
    1977:	learn: 79049.7198584	test: 116535.2986930	best: 116535.2986930 (1977)	total: 11.5s	remaining: 46.5s
    1978:	learn: 79033.9967492	test: 116525.0995608	best: 116525.0995608 (1978)	total: 11.5s	remaining: 46.5s
    1979:	learn: 79026.3762350	test: 116523.9997993	best: 116523.9997993 (1979)	total: 11.5s	remaining: 46.4s
    1980:	learn: 79016.2530805	test: 116517.6478341	best: 116517.6478341 (1980)	total: 11.5s	remaining: 46.4s
    1981:	learn: 79002.7770814	test: 116507.1987422	best: 116507.1987422 (1981)	total: 11.5s	remaining: 46.4s
    1982:	learn: 78989.5752015	test: 116501.9417721	best: 116501.9417721 (1982)	total: 11.5s	remaining: 46.4s
    1983:	learn: 78980.7652636	test: 116499.2321520	best: 116499.2321520 (1983)	total: 11.5s	remaining: 46.4s
    1984:	learn: 78971.9655512	test: 116498.1015759	best: 116498.1015759 (1984)	total: 11.5s	remaining: 46.4s
    1985:	learn: 78962.5898176	test: 116496.1640693	best: 116496.1640693 (1985)	total: 11.5s	remaining: 46.4s
    1986:	learn: 78950.4828357	test: 116491.7971186	best: 116491.7971186 (1986)	total: 11.5s	remaining: 46.4s
    1987:	learn: 78944.4926964	test: 116489.4589155	best: 116489.4589155 (1987)	total: 11.5s	remaining: 46.4s
    1988:	learn: 78933.9447204	test: 116481.2637108	best: 116481.2637108 (1988)	total: 11.5s	remaining: 46.4s
    1989:	learn: 78921.3123063	test: 116482.2525378	best: 116481.2637108 (1988)	total: 11.5s	remaining: 46.4s
    1990:	learn: 78906.9529546	test: 116475.7347252	best: 116475.7347252 (1990)	total: 11.5s	remaining: 46.4s
    1991:	learn: 78885.9826046	test: 116462.9842416	best: 116462.9842416 (1991)	total: 11.5s	remaining: 46.4s
    1992:	learn: 78879.3917553	test: 116460.8364653	best: 116460.8364653 (1992)	total: 11.5s	remaining: 46.4s
    1993:	learn: 78866.9224694	test: 116450.1262629	best: 116450.1262629 (1993)	total: 11.5s	remaining: 46.4s
    1994:	learn: 78859.3967953	test: 116443.1790067	best: 116443.1790067 (1994)	total: 11.6s	remaining: 46.4s
    1995:	learn: 78848.1661162	test: 116437.2539250	best: 116437.2539250 (1995)	total: 11.6s	remaining: 46.4s
    1996:	learn: 78842.2638530	test: 116435.3623695	best: 116435.3623695 (1996)	total: 11.6s	remaining: 46.4s
    1997:	learn: 78830.3954844	test: 116431.7352269	best: 116431.7352269 (1997)	total: 11.6s	remaining: 46.4s
    1998:	learn: 78817.9229772	test: 116431.9072588	best: 116431.7352269 (1997)	total: 11.6s	remaining: 46.3s
    1999:	learn: 78806.3483120	test: 116426.1215955	best: 116426.1215955 (1999)	total: 11.6s	remaining: 46.3s
    2000:	learn: 78791.7765570	test: 116432.8912440	best: 116426.1215955 (1999)	total: 11.6s	remaining: 46.3s
    2001:	learn: 78778.9117651	test: 116430.7398943	best: 116426.1215955 (1999)	total: 11.6s	remaining: 46.3s
    2002:	learn: 78766.4565743	test: 116435.2764478	best: 116426.1215955 (1999)	total: 11.6s	remaining: 46.3s
    2003:	learn: 78750.2512037	test: 116431.3211781	best: 116426.1215955 (1999)	total: 11.6s	remaining: 46.3s
    2004:	learn: 78740.6852872	test: 116423.2905393	best: 116423.2905393 (2004)	total: 11.6s	remaining: 46.3s
    2005:	learn: 78732.4701275	test: 116422.7156898	best: 116422.7156898 (2005)	total: 11.6s	remaining: 46.3s
    2006:	learn: 78719.8886791	test: 116422.5008022	best: 116422.5008022 (2006)	total: 11.6s	remaining: 46.3s
    2007:	learn: 78713.0835981	test: 116420.3054579	best: 116420.3054579 (2007)	total: 11.6s	remaining: 46.3s
    2008:	learn: 78705.5028681	test: 116417.9774895	best: 116417.9774895 (2008)	total: 11.6s	remaining: 46.3s
    2009:	learn: 78695.1786576	test: 116413.4354747	best: 116413.4354747 (2009)	total: 11.7s	remaining: 46.3s
    2010:	learn: 78687.5868879	test: 116405.5634924	best: 116405.5634924 (2010)	total: 11.7s	remaining: 46.3s
    2011:	learn: 78680.6040835	test: 116405.9072855	best: 116405.5634924 (2010)	total: 11.7s	remaining: 46.3s
    2012:	learn: 78668.9515833	test: 116402.6377823	best: 116402.6377823 (2012)	total: 11.7s	remaining: 46.3s
    2013:	learn: 78658.1224039	test: 116402.1327729	best: 116402.1327729 (2013)	total: 11.7s	remaining: 46.3s
    2014:	learn: 78648.2031656	test: 116401.4303772	best: 116401.4303772 (2014)	total: 11.7s	remaining: 46.3s
    2015:	learn: 78639.8110005	test: 116396.6719033	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2016:	learn: 78628.8085240	test: 116405.0204040	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2017:	learn: 78618.2403221	test: 116404.7385800	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2018:	learn: 78609.6312013	test: 116405.3764032	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2019:	learn: 78602.9624940	test: 116404.6389697	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2020:	learn: 78594.4934148	test: 116408.8364553	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2021:	learn: 78587.5962220	test: 116404.2949873	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2022:	learn: 78578.7432037	test: 116399.8659056	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2023:	learn: 78566.8074708	test: 116402.9775645	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.3s
    2024:	learn: 78557.0421848	test: 116402.2427683	best: 116396.6719033 (2015)	total: 11.7s	remaining: 46.2s
    2025:	learn: 78549.1428838	test: 116396.1825584	best: 116396.1825584 (2025)	total: 11.7s	remaining: 46.2s
    2026:	learn: 78537.5810228	test: 116399.7520767	best: 116396.1825584 (2025)	total: 11.8s	remaining: 46.2s
    2027:	learn: 78524.7314708	test: 116399.2389720	best: 116396.1825584 (2025)	total: 11.8s	remaining: 46.2s
    2028:	learn: 78517.7300401	test: 116395.8704641	best: 116395.8704641 (2028)	total: 11.8s	remaining: 46.2s
    2029:	learn: 78505.8316150	test: 116387.6782430	best: 116387.6782430 (2029)	total: 11.8s	remaining: 46.2s
    2030:	learn: 78496.4191356	test: 116384.8807223	best: 116384.8807223 (2030)	total: 11.8s	remaining: 46.2s
    2031:	learn: 78490.0274398	test: 116380.4285794	best: 116380.4285794 (2031)	total: 11.8s	remaining: 46.2s
    2032:	learn: 78481.0362147	test: 116381.0767262	best: 116380.4285794 (2031)	total: 11.8s	remaining: 46.2s
    2033:	learn: 78471.2218089	test: 116375.0078840	best: 116375.0078840 (2033)	total: 11.8s	remaining: 46.2s
    2034:	learn: 78457.4278929	test: 116372.3862584	best: 116372.3862584 (2034)	total: 11.8s	remaining: 46.2s
    2035:	learn: 78445.6048502	test: 116365.5390545	best: 116365.5390545 (2035)	total: 11.8s	remaining: 46.2s
    2036:	learn: 78429.1667208	test: 116355.9741348	best: 116355.9741348 (2036)	total: 11.8s	remaining: 46.2s
    2037:	learn: 78420.0184934	test: 116357.3737691	best: 116355.9741348 (2036)	total: 11.8s	remaining: 46.2s
    2038:	learn: 78407.9308008	test: 116358.5209039	best: 116355.9741348 (2036)	total: 11.8s	remaining: 46.2s
    2039:	learn: 78398.3315967	test: 116352.2710695	best: 116352.2710695 (2039)	total: 11.8s	remaining: 46.2s
    2040:	learn: 78387.1643104	test: 116352.2949651	best: 116352.2710695 (2039)	total: 11.8s	remaining: 46.2s
    2041:	learn: 78380.7867459	test: 116351.8945617	best: 116351.8945617 (2041)	total: 11.9s	remaining: 46.2s
    2042:	learn: 78372.4988309	test: 116346.1418158	best: 116346.1418158 (2042)	total: 11.9s	remaining: 46.2s
    2043:	learn: 78364.4801767	test: 116338.7383749	best: 116338.7383749 (2043)	total: 11.9s	remaining: 46.2s
    2044:	learn: 78355.9963679	test: 116337.1147145	best: 116337.1147145 (2044)	total: 11.9s	remaining: 46.2s
    2045:	learn: 78347.9729795	test: 116336.1115189	best: 116336.1115189 (2045)	total: 11.9s	remaining: 46.2s
    2046:	learn: 78337.9901864	test: 116327.4117464	best: 116327.4117464 (2046)	total: 11.9s	remaining: 46.2s
    2047:	learn: 78330.0214268	test: 116333.2274029	best: 116327.4117464 (2046)	total: 11.9s	remaining: 46.2s
    2048:	learn: 78321.8127541	test: 116334.9569756	best: 116327.4117464 (2046)	total: 11.9s	remaining: 46.2s
    2049:	learn: 78308.3558656	test: 116327.5287018	best: 116327.4117464 (2046)	total: 11.9s	remaining: 46.2s
    2050:	learn: 78299.9247304	test: 116321.9219911	best: 116321.9219911 (2050)	total: 11.9s	remaining: 46.2s
    2051:	learn: 78289.6508282	test: 116319.0878756	best: 116319.0878756 (2051)	total: 11.9s	remaining: 46.2s
    2052:	learn: 78280.8040059	test: 116319.0856959	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2053:	learn: 78275.0280247	test: 116324.9440469	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2054:	learn: 78265.5040505	test: 116325.0727285	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2055:	learn: 78258.7277935	test: 116323.7186525	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2056:	learn: 78250.7766903	test: 116322.9200438	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2057:	learn: 78245.6625233	test: 116322.8592546	best: 116319.0856959 (2052)	total: 11.9s	remaining: 46.1s
    2058:	learn: 78231.9827624	test: 116318.4886672	best: 116318.4886672 (2058)	total: 12s	remaining: 46.1s
    2059:	learn: 78225.5389835	test: 116319.8332176	best: 116318.4886672 (2058)	total: 12s	remaining: 46.1s
    2060:	learn: 78218.0580932	test: 116323.4198075	best: 116318.4886672 (2058)	total: 12s	remaining: 46.1s
    2061:	learn: 78204.6677450	test: 116323.2845487	best: 116318.4886672 (2058)	total: 12s	remaining: 46.1s
    2062:	learn: 78195.4189770	test: 116314.7308526	best: 116314.7308526 (2062)	total: 12s	remaining: 46.1s
    2063:	learn: 78186.9158460	test: 116310.5517441	best: 116310.5517441 (2063)	total: 12s	remaining: 46.1s
    2064:	learn: 78177.7617290	test: 116307.9379058	best: 116307.9379058 (2064)	total: 12s	remaining: 46.1s
    2065:	learn: 78172.0074355	test: 116307.2084383	best: 116307.2084383 (2065)	total: 12s	remaining: 46.1s
    2066:	learn: 78164.7608897	test: 116311.2436972	best: 116307.2084383 (2065)	total: 12s	remaining: 46.1s
    2067:	learn: 78155.6184589	test: 116314.9778906	best: 116307.2084383 (2065)	total: 12s	remaining: 46.1s
    2068:	learn: 78148.0142535	test: 116314.3024401	best: 116307.2084383 (2065)	total: 12s	remaining: 46.1s
    2069:	learn: 78143.0990613	test: 116314.8929582	best: 116307.2084383 (2065)	total: 12s	remaining: 46s
    2070:	learn: 78131.4696899	test: 116314.3203188	best: 116307.2084383 (2065)	total: 12s	remaining: 46s
    2071:	learn: 78116.4930657	test: 116306.1404498	best: 116306.1404498 (2071)	total: 12s	remaining: 46s
    2072:	learn: 78109.5892794	test: 116306.3957886	best: 116306.1404498 (2071)	total: 12s	remaining: 46s
    2073:	learn: 78100.1346925	test: 116311.2596959	best: 116306.1404498 (2071)	total: 12s	remaining: 46s
    2074:	learn: 78090.8842354	test: 116311.4386340	best: 116306.1404498 (2071)	total: 12s	remaining: 46s
    2075:	learn: 78084.7577664	test: 116308.9153596	best: 116306.1404498 (2071)	total: 12.1s	remaining: 46s
    2076:	learn: 78067.2738772	test: 116305.5227558	best: 116305.5227558 (2076)	total: 12.1s	remaining: 46s
    2077:	learn: 78058.9354837	test: 116302.9026700	best: 116302.9026700 (2077)	total: 12.1s	remaining: 46s
    2078:	learn: 78052.4078853	test: 116298.4920015	best: 116298.4920015 (2078)	total: 12.1s	remaining: 46s
    2079:	learn: 78048.5574770	test: 116293.5208112	best: 116293.5208112 (2079)	total: 12.1s	remaining: 46s
    2080:	learn: 78037.7016816	test: 116291.5770269	best: 116291.5770269 (2080)	total: 12.1s	remaining: 46s
    2081:	learn: 78031.9741144	test: 116284.4980615	best: 116284.4980615 (2081)	total: 12.1s	remaining: 46s
    2082:	learn: 78024.4939298	test: 116284.3202821	best: 116284.3202821 (2082)	total: 12.1s	remaining: 46s
    2083:	learn: 78016.3823891	test: 116283.7057288	best: 116283.7057288 (2083)	total: 12.1s	remaining: 46s
    2084:	learn: 78005.8611119	test: 116281.4190188	best: 116281.4190188 (2084)	total: 12.1s	remaining: 45.9s
    2085:	learn: 77998.9455170	test: 116280.2142553	best: 116280.2142553 (2085)	total: 12.1s	remaining: 45.9s
    2086:	learn: 77985.8374331	test: 116278.1857393	best: 116278.1857393 (2086)	total: 12.1s	remaining: 45.9s
    2087:	learn: 77977.1052285	test: 116278.4575082	best: 116278.1857393 (2086)	total: 12.1s	remaining: 45.9s
    2088:	learn: 77965.5263304	test: 116279.6035282	best: 116278.1857393 (2086)	total: 12.1s	remaining: 45.9s
    2089:	learn: 77957.7081105	test: 116278.6671682	best: 116278.1857393 (2086)	total: 12.1s	remaining: 45.9s
    2090:	learn: 77944.9948473	test: 116277.4876007	best: 116277.4876007 (2090)	total: 12.1s	remaining: 45.9s
    2091:	learn: 77937.1510485	test: 116275.3249950	best: 116275.3249950 (2091)	total: 12.1s	remaining: 45.9s
    2092:	learn: 77928.6746960	test: 116275.6483808	best: 116275.3249950 (2091)	total: 12.2s	remaining: 45.9s
    2093:	learn: 77915.4730771	test: 116274.5374948	best: 116274.5374948 (2093)	total: 12.2s	remaining: 45.9s
    2094:	learn: 77906.2845504	test: 116274.0042031	best: 116274.0042031 (2094)	total: 12.2s	remaining: 45.9s
    2095:	learn: 77891.0913239	test: 116274.7761623	best: 116274.0042031 (2094)	total: 12.2s	remaining: 45.9s
    2096:	learn: 77883.7451667	test: 116272.9314342	best: 116272.9314342 (2096)	total: 12.2s	remaining: 45.9s
    2097:	learn: 77879.3048687	test: 116273.3075347	best: 116272.9314342 (2096)	total: 12.2s	remaining: 45.9s
    2098:	learn: 77869.0697852	test: 116271.7537021	best: 116271.7537021 (2098)	total: 12.2s	remaining: 45.9s
    2099:	learn: 77859.6435150	test: 116265.8610826	best: 116265.8610826 (2099)	total: 12.2s	remaining: 45.9s
    2100:	learn: 77853.8481774	test: 116264.5645696	best: 116264.5645696 (2100)	total: 12.2s	remaining: 45.8s
    2101:	learn: 77847.3081510	test: 116265.6305263	best: 116264.5645696 (2100)	total: 12.2s	remaining: 45.8s
    2102:	learn: 77838.1102778	test: 116266.7331373	best: 116264.5645696 (2100)	total: 12.2s	remaining: 45.8s
    2103:	learn: 77832.5649493	test: 116259.8313066	best: 116259.8313066 (2103)	total: 12.2s	remaining: 45.8s
    2104:	learn: 77823.6636919	test: 116259.8362561	best: 116259.8313066 (2103)	total: 12.2s	remaining: 45.8s
    2105:	learn: 77814.7056568	test: 116258.1467244	best: 116258.1467244 (2105)	total: 12.2s	remaining: 45.8s
    2106:	learn: 77801.6870541	test: 116253.2277352	best: 116253.2277352 (2106)	total: 12.2s	remaining: 45.8s
    2107:	learn: 77788.8604522	test: 116253.3381928	best: 116253.2277352 (2106)	total: 12.2s	remaining: 45.8s
    2108:	learn: 77775.7912324	test: 116251.9597686	best: 116251.9597686 (2108)	total: 12.2s	remaining: 45.8s
    2109:	learn: 77761.3840572	test: 116249.8575266	best: 116249.8575266 (2109)	total: 12.2s	remaining: 45.8s
    2110:	learn: 77753.3275516	test: 116250.8291388	best: 116249.8575266 (2109)	total: 12.2s	remaining: 45.8s
    2111:	learn: 77744.3869287	test: 116245.5708128	best: 116245.5708128 (2111)	total: 12.3s	remaining: 45.8s
    2112:	learn: 77730.1406123	test: 116239.7097035	best: 116239.7097035 (2112)	total: 12.3s	remaining: 45.8s
    2113:	learn: 77722.7818011	test: 116240.9289427	best: 116239.7097035 (2112)	total: 12.3s	remaining: 45.8s
    2114:	learn: 77712.7204010	test: 116236.7359317	best: 116236.7359317 (2114)	total: 12.3s	remaining: 45.7s
    2115:	learn: 77705.9701081	test: 116237.0407785	best: 116236.7359317 (2114)	total: 12.3s	remaining: 45.7s
    2116:	learn: 77697.2720418	test: 116236.2160701	best: 116236.2160701 (2116)	total: 12.3s	remaining: 45.7s
    2117:	learn: 77689.9093227	test: 116231.2619743	best: 116231.2619743 (2117)	total: 12.3s	remaining: 45.7s
    2118:	learn: 77682.7199868	test: 116230.9179882	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2119:	learn: 77677.2228985	test: 116234.7368334	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2120:	learn: 77670.5841855	test: 116241.3919675	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2121:	learn: 77659.4534198	test: 116242.5586020	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2122:	learn: 77648.2577983	test: 116241.1688397	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2123:	learn: 77635.6106845	test: 116234.7799262	best: 116230.9179882 (2118)	total: 12.3s	remaining: 45.7s
    2124:	learn: 77627.1361776	test: 116228.5270905	best: 116228.5270905 (2124)	total: 12.3s	remaining: 45.7s
    2125:	learn: 77622.2548916	test: 116231.1586898	best: 116228.5270905 (2124)	total: 12.3s	remaining: 45.7s
    2126:	learn: 77617.0424890	test: 116224.5423662	best: 116224.5423662 (2126)	total: 12.3s	remaining: 45.7s
    2127:	learn: 77605.8952047	test: 116220.0172312	best: 116220.0172312 (2127)	total: 12.3s	remaining: 45.7s
    2128:	learn: 77602.2130954	test: 116215.3530968	best: 116215.3530968 (2128)	total: 12.4s	remaining: 45.7s
    2129:	learn: 77594.1156299	test: 116213.2420990	best: 116213.2420990 (2129)	total: 12.4s	remaining: 45.7s
    2130:	learn: 77587.2850181	test: 116212.2513723	best: 116212.2513723 (2130)	total: 12.4s	remaining: 45.6s
    2131:	learn: 77577.5372683	test: 116216.7171113	best: 116212.2513723 (2130)	total: 12.4s	remaining: 45.6s
    2132:	learn: 77564.0711732	test: 116207.5974558	best: 116207.5974558 (2132)	total: 12.4s	remaining: 45.6s
    2133:	learn: 77551.6172371	test: 116206.2099682	best: 116206.2099682 (2133)	total: 12.4s	remaining: 45.6s
    2134:	learn: 77543.2463174	test: 116203.2417282	best: 116203.2417282 (2134)	total: 12.4s	remaining: 45.6s
    2135:	learn: 77533.0356938	test: 116205.7031050	best: 116203.2417282 (2134)	total: 12.4s	remaining: 45.6s
    2136:	learn: 77523.7790068	test: 116206.5310652	best: 116203.2417282 (2134)	total: 12.4s	remaining: 45.6s
    2137:	learn: 77516.2153270	test: 116205.4675794	best: 116203.2417282 (2134)	total: 12.4s	remaining: 45.6s
    2138:	learn: 77512.7229150	test: 116205.0436023	best: 116203.2417282 (2134)	total: 12.4s	remaining: 45.6s
    2139:	learn: 77507.1002838	test: 116203.1521497	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.6s
    2140:	learn: 77495.0313787	test: 116210.4495337	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.6s
    2141:	learn: 77483.1194694	test: 116210.7603006	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.6s
    2142:	learn: 77474.8085437	test: 116210.0141083	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.6s
    2143:	learn: 77468.7277282	test: 116208.3765112	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.6s
    2144:	learn: 77464.0647725	test: 116205.2993341	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.5s
    2145:	learn: 77452.1381854	test: 116209.0314186	best: 116203.1521497 (2139)	total: 12.4s	remaining: 45.5s
    2146:	learn: 77447.1559078	test: 116202.8514475	best: 116202.8514475 (2146)	total: 12.4s	remaining: 45.5s
    2147:	learn: 77435.6809510	test: 116199.7348901	best: 116199.7348901 (2147)	total: 12.5s	remaining: 45.5s
    2148:	learn: 77430.5476873	test: 116202.3228086	best: 116199.7348901 (2147)	total: 12.5s	remaining: 45.5s
    2149:	learn: 77425.3928872	test: 116201.2483180	best: 116199.7348901 (2147)	total: 12.5s	remaining: 45.5s
    2150:	learn: 77417.8289572	test: 116200.1218827	best: 116199.7348901 (2147)	total: 12.5s	remaining: 45.5s
    2151:	learn: 77409.1963592	test: 116200.1531996	best: 116199.7348901 (2147)	total: 12.5s	remaining: 45.5s
    2152:	learn: 77400.3801112	test: 116196.6925869	best: 116196.6925869 (2152)	total: 12.5s	remaining: 45.5s
    2153:	learn: 77390.7263788	test: 116194.2464029	best: 116194.2464029 (2153)	total: 12.5s	remaining: 45.5s
    2154:	learn: 77383.0870013	test: 116204.5453745	best: 116194.2464029 (2153)	total: 12.5s	remaining: 45.5s
    2155:	learn: 77371.1691449	test: 116203.2494687	best: 116194.2464029 (2153)	total: 12.5s	remaining: 45.5s
    2156:	learn: 77355.6434179	test: 116194.3161541	best: 116194.2464029 (2153)	total: 12.5s	remaining: 45.5s
    2157:	learn: 77345.5609167	test: 116190.6081394	best: 116190.6081394 (2157)	total: 12.5s	remaining: 45.5s
    2158:	learn: 77336.9355099	test: 116188.1916434	best: 116188.1916434 (2158)	total: 12.5s	remaining: 45.5s
    2159:	learn: 77331.7693191	test: 116188.4610411	best: 116188.1916434 (2158)	total: 12.5s	remaining: 45.5s
    2160:	learn: 77324.1871866	test: 116186.3545013	best: 116186.3545013 (2160)	total: 12.5s	remaining: 45.5s
    2161:	learn: 77315.3379406	test: 116181.9568558	best: 116181.9568558 (2161)	total: 12.5s	remaining: 45.5s
    2162:	learn: 77305.2468319	test: 116175.8074238	best: 116175.8074238 (2162)	total: 12.6s	remaining: 45.5s
    2163:	learn: 77295.2282911	test: 116172.2823498	best: 116172.2823498 (2163)	total: 12.6s	remaining: 45.5s
    2164:	learn: 77280.6428172	test: 116167.7287963	best: 116167.7287963 (2164)	total: 12.6s	remaining: 45.5s
    2165:	learn: 77265.6022019	test: 116158.4377817	best: 116158.4377817 (2165)	total: 12.6s	remaining: 45.5s
    2166:	learn: 77257.4405629	test: 116160.8478767	best: 116158.4377817 (2165)	total: 12.6s	remaining: 45.4s
    2167:	learn: 77249.1839705	test: 116161.4644318	best: 116158.4377817 (2165)	total: 12.6s	remaining: 45.4s
    2168:	learn: 77240.4822182	test: 116155.5287314	best: 116155.5287314 (2168)	total: 12.6s	remaining: 45.4s
    2169:	learn: 77228.7176300	test: 116151.3956351	best: 116151.3956351 (2169)	total: 12.6s	remaining: 45.4s
    2170:	learn: 77218.6270586	test: 116145.1210352	best: 116145.1210352 (2170)	total: 12.6s	remaining: 45.4s
    2171:	learn: 77199.9756602	test: 116139.6339055	best: 116139.6339055 (2171)	total: 12.6s	remaining: 45.4s
    2172:	learn: 77193.1589156	test: 116135.2816183	best: 116135.2816183 (2172)	total: 12.6s	remaining: 45.4s
    2173:	learn: 77180.5453118	test: 116131.6732025	best: 116131.6732025 (2173)	total: 12.6s	remaining: 45.4s
    2174:	learn: 77173.2738400	test: 116134.0498372	best: 116131.6732025 (2173)	total: 12.6s	remaining: 45.4s
    2175:	learn: 77162.0926759	test: 116121.1054971	best: 116121.1054971 (2175)	total: 12.6s	remaining: 45.4s
    2176:	learn: 77154.4223918	test: 116122.7204501	best: 116121.1054971 (2175)	total: 12.6s	remaining: 45.4s
    2177:	learn: 77146.8844924	test: 116121.8298520	best: 116121.1054971 (2175)	total: 12.6s	remaining: 45.4s
    2178:	learn: 77140.5408759	test: 116122.2615077	best: 116121.1054971 (2175)	total: 12.6s	remaining: 45.4s
    2179:	learn: 77132.6749768	test: 116121.1987777	best: 116121.1054971 (2175)	total: 12.7s	remaining: 45.4s
    2180:	learn: 77127.9231411	test: 116119.3441799	best: 116119.3441799 (2180)	total: 12.7s	remaining: 45.4s
    2181:	learn: 77114.8497305	test: 116119.2011815	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2182:	learn: 77095.9406276	test: 116125.7254319	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2183:	learn: 77085.7040423	test: 116120.7108209	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2184:	learn: 77078.0667394	test: 116126.4797483	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2185:	learn: 77073.2479591	test: 116124.1288156	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2186:	learn: 77064.0364078	test: 116125.9785013	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2187:	learn: 77054.2165472	test: 116124.9760132	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2188:	learn: 77045.5172109	test: 116121.8824679	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.4s
    2189:	learn: 77035.6839725	test: 116121.1225558	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2190:	learn: 77023.5869867	test: 116125.2556273	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2191:	learn: 77014.3900078	test: 116127.3902476	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2192:	learn: 77004.2819190	test: 116131.0442707	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2193:	learn: 76998.0256197	test: 116126.6106011	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2194:	learn: 76993.1386190	test: 116125.6709919	best: 116119.2011815 (2181)	total: 12.7s	remaining: 45.3s
    2195:	learn: 76980.8355740	test: 116130.6213076	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2196:	learn: 76972.4431474	test: 116130.2791838	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2197:	learn: 76968.0503299	test: 116129.8542220	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2198:	learn: 76964.0337982	test: 116134.9056640	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2199:	learn: 76957.1694905	test: 116137.0994276	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2200:	learn: 76947.8533737	test: 116138.5754722	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2201:	learn: 76939.6287414	test: 116137.5260758	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2202:	learn: 76927.6779410	test: 116134.6366888	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2203:	learn: 76918.4021055	test: 116130.0697552	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2204:	learn: 76912.8244996	test: 116128.7517650	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2205:	learn: 76899.6716445	test: 116130.3239206	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2206:	learn: 76885.3509581	test: 116129.2630472	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2207:	learn: 76880.2472209	test: 116130.4476586	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2208:	learn: 76866.0580823	test: 116132.2245711	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2209:	learn: 76859.7028582	test: 116130.7773497	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2210:	learn: 76851.4252399	test: 116129.7403754	best: 116119.2011815 (2181)	total: 12.8s	remaining: 45.3s
    2211:	learn: 76843.1629288	test: 116128.3979779	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.3s
    2212:	learn: 76832.3545672	test: 116133.5715570	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2213:	learn: 76823.4281643	test: 116138.1609050	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2214:	learn: 76815.6956516	test: 116134.4685855	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2215:	learn: 76809.6218596	test: 116133.5632712	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2216:	learn: 76800.0303253	test: 116131.9480460	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2217:	learn: 76792.7620200	test: 116131.1661004	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2218:	learn: 76784.9602234	test: 116134.9984169	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2219:	learn: 76777.5346279	test: 116135.6658673	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2220:	learn: 76759.4992341	test: 116124.5667176	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2221:	learn: 76754.5402727	test: 116123.6150557	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2222:	learn: 76750.5325730	test: 116130.3073806	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2223:	learn: 76736.4306263	test: 116124.0985286	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2224:	learn: 76728.6186364	test: 116123.2311731	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2225:	learn: 76722.4171310	test: 116124.0156161	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.2s
    2226:	learn: 76711.0258099	test: 116123.1884973	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.1s
    2227:	learn: 76704.3778345	test: 116122.4015488	best: 116119.2011815 (2181)	total: 12.9s	remaining: 45.1s
    2228:	learn: 76692.7337615	test: 116113.9923248	best: 116113.9923248 (2228)	total: 12.9s	remaining: 45.1s
    2229:	learn: 76686.8448462	test: 116108.3189637	best: 116108.3189637 (2229)	total: 13s	remaining: 45.1s
    2230:	learn: 76674.7666421	test: 116106.2569990	best: 116106.2569990 (2230)	total: 13s	remaining: 45.1s
    2231:	learn: 76667.8866475	test: 116104.2655749	best: 116104.2655749 (2231)	total: 13s	remaining: 45.1s
    2232:	learn: 76658.1872558	test: 116102.0306816	best: 116102.0306816 (2232)	total: 13s	remaining: 45.1s
    2233:	learn: 76649.7402967	test: 116101.9501772	best: 116101.9501772 (2233)	total: 13s	remaining: 45.1s
    2234:	learn: 76637.9245619	test: 116100.0408069	best: 116100.0408069 (2234)	total: 13s	remaining: 45.1s
    2235:	learn: 76625.1980301	test: 116092.1638018	best: 116092.1638018 (2235)	total: 13s	remaining: 45.1s
    2236:	learn: 76620.1615215	test: 116096.0632409	best: 116092.1638018 (2235)	total: 13s	remaining: 45.1s
    2237:	learn: 76612.1080351	test: 116094.7757432	best: 116092.1638018 (2235)	total: 13s	remaining: 45.1s
    2238:	learn: 76603.9509733	test: 116092.8094009	best: 116092.1638018 (2235)	total: 13s	remaining: 45.1s
    2239:	learn: 76597.4821005	test: 116087.1239219	best: 116087.1239219 (2239)	total: 13s	remaining: 45.1s
    2240:	learn: 76592.5807233	test: 116091.0178080	best: 116087.1239219 (2239)	total: 13s	remaining: 45.1s
    2241:	learn: 76585.1051946	test: 116088.3302823	best: 116087.1239219 (2239)	total: 13s	remaining: 45.1s
    2242:	learn: 76575.1108051	test: 116084.1555718	best: 116084.1555718 (2242)	total: 13s	remaining: 45.1s
    2243:	learn: 76564.3596871	test: 116084.0760688	best: 116084.0760688 (2243)	total: 13s	remaining: 45.1s
    2244:	learn: 76558.1575189	test: 116081.9762846	best: 116081.9762846 (2244)	total: 13s	remaining: 45s
    2245:	learn: 76547.4718538	test: 116089.6287511	best: 116081.9762846 (2244)	total: 13s	remaining: 45s
    2246:	learn: 76535.9835035	test: 116087.8418621	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2247:	learn: 76529.1421094	test: 116086.4414994	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2248:	learn: 76524.2125140	test: 116086.1752292	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2249:	learn: 76516.8560087	test: 116086.1855779	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2250:	learn: 76506.1888590	test: 116083.7193479	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2251:	learn: 76499.4495230	test: 116087.3188486	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2252:	learn: 76492.1842974	test: 116085.7133176	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2253:	learn: 76485.5411369	test: 116085.7268831	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2254:	learn: 76473.5848833	test: 116086.7595275	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2255:	learn: 76462.9370502	test: 116087.1795734	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2256:	learn: 76457.7996268	test: 116092.6679194	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2257:	learn: 76447.8402930	test: 116087.8996229	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2258:	learn: 76438.2455232	test: 116084.0159157	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2259:	learn: 76426.4352895	test: 116083.4515107	best: 116081.9762846 (2244)	total: 13.1s	remaining: 45s
    2260:	learn: 76418.4582864	test: 116084.9716749	best: 116081.9762846 (2244)	total: 13.1s	remaining: 44.9s
    2261:	learn: 76408.5188530	test: 116081.7514813	best: 116081.7514813 (2261)	total: 13.1s	remaining: 44.9s
    2262:	learn: 76401.6173788	test: 116077.5864395	best: 116077.5864395 (2262)	total: 13.1s	remaining: 44.9s
    2263:	learn: 76394.0437659	test: 116074.8979776	best: 116074.8979776 (2263)	total: 13.1s	remaining: 44.9s
    2264:	learn: 76387.0426097	test: 116073.1912887	best: 116073.1912887 (2264)	total: 13.2s	remaining: 44.9s
    2265:	learn: 76366.8033717	test: 116060.4465810	best: 116060.4465810 (2265)	total: 13.2s	remaining: 44.9s
    2266:	learn: 76360.7911696	test: 116061.7999825	best: 116060.4465810 (2265)	total: 13.2s	remaining: 44.9s
    2267:	learn: 76352.3986408	test: 116061.5095188	best: 116060.4465810 (2265)	total: 13.2s	remaining: 44.9s
    2268:	learn: 76337.5579970	test: 116059.9496228	best: 116059.9496228 (2268)	total: 13.2s	remaining: 44.9s
    2269:	learn: 76326.5239891	test: 116059.1041984	best: 116059.1041984 (2269)	total: 13.2s	remaining: 44.9s
    2270:	learn: 76318.6149064	test: 116058.3949866	best: 116058.3949866 (2270)	total: 13.2s	remaining: 44.9s
    2271:	learn: 76306.8331995	test: 116058.8225433	best: 116058.3949866 (2270)	total: 13.2s	remaining: 44.9s
    2272:	learn: 76296.9033486	test: 116057.1048700	best: 116057.1048700 (2272)	total: 13.2s	remaining: 44.9s
    2273:	learn: 76292.1034948	test: 116056.6104136	best: 116056.6104136 (2273)	total: 13.2s	remaining: 44.9s
    2274:	learn: 76286.2837637	test: 116060.0410649	best: 116056.6104136 (2273)	total: 13.2s	remaining: 44.9s
    2275:	learn: 76279.5786166	test: 116056.0700012	best: 116056.0700012 (2275)	total: 13.2s	remaining: 44.9s
    2276:	learn: 76262.7125293	test: 116055.3650723	best: 116055.3650723 (2276)	total: 13.2s	remaining: 44.9s
    2277:	learn: 76254.6458742	test: 116055.7176941	best: 116055.3650723 (2276)	total: 13.2s	remaining: 44.8s
    2278:	learn: 76245.9802097	test: 116056.4361744	best: 116055.3650723 (2276)	total: 13.2s	remaining: 44.8s
    2279:	learn: 76230.7507568	test: 116057.6363959	best: 116055.3650723 (2276)	total: 13.2s	remaining: 44.8s
    2280:	learn: 76222.2400803	test: 116057.4567554	best: 116055.3650723 (2276)	total: 13.2s	remaining: 44.8s
    2281:	learn: 76215.0262844	test: 116056.9523897	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2282:	learn: 76204.0932185	test: 116061.1675585	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2283:	learn: 76198.8204526	test: 116063.1996848	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2284:	learn: 76187.9501920	test: 116066.4839601	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2285:	learn: 76176.6885328	test: 116058.7068510	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2286:	learn: 76167.0225968	test: 116068.5373557	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2287:	learn: 76162.2531282	test: 116067.9541116	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2288:	learn: 76154.1257477	test: 116067.2450886	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2289:	learn: 76142.9036902	test: 116065.5614094	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2290:	learn: 76134.2506434	test: 116066.2242759	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2291:	learn: 76126.5657503	test: 116063.7017688	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.8s
    2292:	learn: 76120.9436929	test: 116066.8943462	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2293:	learn: 76111.0489437	test: 116068.5922548	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2294:	learn: 76101.7296518	test: 116067.0776398	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2295:	learn: 76088.5604919	test: 116069.4895890	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2296:	learn: 76082.3700917	test: 116070.4764469	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2297:	learn: 76066.8318933	test: 116062.6881743	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2298:	learn: 76062.2209802	test: 116066.4813340	best: 116055.3650723 (2276)	total: 13.3s	remaining: 44.7s
    2299:	learn: 76055.0801768	test: 116065.9065859	best: 116055.3650723 (2276)	total: 13.4s	remaining: 44.7s
    2300:	learn: 76041.9016066	test: 116062.5691586	best: 116055.3650723 (2276)	total: 13.4s	remaining: 44.7s
    2301:	learn: 76036.2612113	test: 116065.8836060	best: 116055.3650723 (2276)	total: 13.4s	remaining: 44.7s
    2302:	learn: 76023.4945832	test: 116062.7508988	best: 116055.3650723 (2276)	total: 13.4s	remaining: 44.7s
    2303:	learn: 76007.7540620	test: 116053.0410864	best: 116053.0410864 (2303)	total: 13.4s	remaining: 44.7s
    2304:	learn: 75995.9812764	test: 116047.9574704	best: 116047.9574704 (2304)	total: 13.4s	remaining: 44.7s
    2305:	learn: 75985.7456895	test: 116055.7426695	best: 116047.9574704 (2304)	total: 13.4s	remaining: 44.7s
    2306:	learn: 75980.5132018	test: 116054.2513524	best: 116047.9574704 (2304)	total: 13.4s	remaining: 44.7s
    2307:	learn: 75972.4372105	test: 116051.5196950	best: 116047.9574704 (2304)	total: 13.4s	remaining: 44.7s
    2308:	learn: 75964.4689391	test: 116046.0393308	best: 116046.0393308 (2308)	total: 13.4s	remaining: 44.7s
    2309:	learn: 75955.6283026	test: 116045.9910384	best: 116045.9910384 (2309)	total: 13.4s	remaining: 44.6s
    2310:	learn: 75941.4211899	test: 116045.0702072	best: 116045.0702072 (2310)	total: 13.4s	remaining: 44.6s
    2311:	learn: 75930.8458896	test: 116041.4084703	best: 116041.4084703 (2311)	total: 13.4s	remaining: 44.6s
    2312:	learn: 75923.6608034	test: 116037.4753766	best: 116037.4753766 (2312)	total: 13.4s	remaining: 44.6s
    2313:	learn: 75919.8368160	test: 116036.4081324	best: 116036.4081324 (2313)	total: 13.4s	remaining: 44.6s
    2314:	learn: 75912.5492295	test: 116031.9681467	best: 116031.9681467 (2314)	total: 13.4s	remaining: 44.6s
    2315:	learn: 75901.0702930	test: 116036.9706104	best: 116031.9681467 (2314)	total: 13.4s	remaining: 44.6s
    2316:	learn: 75894.6664381	test: 116039.2777178	best: 116031.9681467 (2314)	total: 13.5s	remaining: 44.6s
    2317:	learn: 75884.8024031	test: 116035.0679389	best: 116031.9681467 (2314)	total: 13.5s	remaining: 44.6s
    2318:	learn: 75877.0753691	test: 116031.4501188	best: 116031.4501188 (2318)	total: 13.5s	remaining: 44.6s
    2319:	learn: 75871.5725454	test: 116030.3614059	best: 116030.3614059 (2319)	total: 13.5s	remaining: 44.6s
    2320:	learn: 75864.4520583	test: 116031.9454492	best: 116030.3614059 (2319)	total: 13.5s	remaining: 44.6s
    2321:	learn: 75853.7437604	test: 116027.1274375	best: 116027.1274375 (2321)	total: 13.5s	remaining: 44.6s
    2322:	learn: 75849.7661918	test: 116033.9565391	best: 116027.1274375 (2321)	total: 13.5s	remaining: 44.6s
    2323:	learn: 75841.5911404	test: 116033.4750811	best: 116027.1274375 (2321)	total: 13.5s	remaining: 44.6s
    2324:	learn: 75833.1034887	test: 116033.0165400	best: 116027.1274375 (2321)	total: 13.5s	remaining: 44.6s
    2325:	learn: 75824.5413632	test: 116026.8646668	best: 116026.8646668 (2325)	total: 13.5s	remaining: 44.6s
    2326:	learn: 75819.5636225	test: 116025.8279564	best: 116025.8279564 (2326)	total: 13.5s	remaining: 44.6s
    2327:	learn: 75811.8172692	test: 116020.6997584	best: 116020.6997584 (2327)	total: 13.5s	remaining: 44.6s
    2328:	learn: 75804.0134170	test: 116019.3366030	best: 116019.3366030 (2328)	total: 13.5s	remaining: 44.6s
    2329:	learn: 75794.0496611	test: 116013.8872145	best: 116013.8872145 (2329)	total: 13.5s	remaining: 44.6s
    2330:	learn: 75782.3502203	test: 116009.5454459	best: 116009.5454459 (2330)	total: 13.5s	remaining: 44.6s
    2331:	learn: 75774.7449160	test: 116006.1089010	best: 116006.1089010 (2331)	total: 13.6s	remaining: 44.6s
    2332:	learn: 75767.8063014	test: 116002.1323726	best: 116002.1323726 (2332)	total: 13.6s	remaining: 44.6s
    2333:	learn: 75758.1589099	test: 115998.2750444	best: 115998.2750444 (2333)	total: 13.6s	remaining: 44.6s
    2334:	learn: 75750.5144119	test: 115996.0711492	best: 115996.0711492 (2334)	total: 13.6s	remaining: 44.6s
    2335:	learn: 75739.5495907	test: 115991.2222631	best: 115991.2222631 (2335)	total: 13.6s	remaining: 44.6s
    2336:	learn: 75732.2588936	test: 115990.7362401	best: 115990.7362401 (2336)	total: 13.6s	remaining: 44.5s
    2337:	learn: 75723.0420658	test: 115981.7887853	best: 115981.7887853 (2337)	total: 13.6s	remaining: 44.5s
    2338:	learn: 75716.7712228	test: 115979.9040470	best: 115979.9040470 (2338)	total: 13.6s	remaining: 44.5s
    2339:	learn: 75711.7419249	test: 115977.0081121	best: 115977.0081121 (2339)	total: 13.6s	remaining: 44.5s
    2340:	learn: 75698.9858071	test: 115977.1436406	best: 115977.0081121 (2339)	total: 13.6s	remaining: 44.5s
    2341:	learn: 75691.4761094	test: 115974.7159921	best: 115974.7159921 (2341)	total: 13.6s	remaining: 44.5s
    2342:	learn: 75682.6439238	test: 115973.9001149	best: 115973.9001149 (2342)	total: 13.6s	remaining: 44.5s
    2343:	learn: 75670.1655605	test: 115975.8334969	best: 115973.9001149 (2342)	total: 13.6s	remaining: 44.5s
    2344:	learn: 75659.2331992	test: 115976.8555687	best: 115973.9001149 (2342)	total: 13.6s	remaining: 44.5s
    2345:	learn: 75654.1584523	test: 115986.9178561	best: 115973.9001149 (2342)	total: 13.6s	remaining: 44.5s
    2346:	learn: 75640.3693050	test: 115987.9025764	best: 115973.9001149 (2342)	total: 13.6s	remaining: 44.5s
    2347:	learn: 75632.7922092	test: 115985.4812031	best: 115973.9001149 (2342)	total: 13.7s	remaining: 44.5s
    2348:	learn: 75626.1246977	test: 115985.7878526	best: 115973.9001149 (2342)	total: 13.7s	remaining: 44.5s
    2349:	learn: 75612.5344681	test: 115979.9707078	best: 115973.9001149 (2342)	total: 13.7s	remaining: 44.5s
    2350:	learn: 75602.6152658	test: 115979.9918281	best: 115973.9001149 (2342)	total: 13.7s	remaining: 44.5s
    2351:	learn: 75597.3394765	test: 115977.3072954	best: 115973.9001149 (2342)	total: 13.7s	remaining: 44.5s
    2352:	learn: 75576.8292832	test: 115973.8106772	best: 115973.8106772 (2352)	total: 13.7s	remaining: 44.5s
    2353:	learn: 75569.5554714	test: 115974.1679022	best: 115973.8106772 (2352)	total: 13.7s	remaining: 44.4s
    2354:	learn: 75562.2332255	test: 115972.0197915	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2355:	learn: 75552.8691290	test: 115974.2656795	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2356:	learn: 75544.2367420	test: 115973.5597689	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2357:	learn: 75534.4172933	test: 115976.4701387	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2358:	learn: 75522.6046163	test: 115982.6998937	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2359:	learn: 75512.0506460	test: 115981.5785067	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2360:	learn: 75497.4698628	test: 115972.8619718	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2361:	learn: 75491.6318486	test: 115974.1789082	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2362:	learn: 75479.0740013	test: 115976.9742861	best: 115972.0197915 (2354)	total: 13.7s	remaining: 44.4s
    2363:	learn: 75472.2819977	test: 115976.6699036	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2364:	learn: 75466.4971947	test: 115981.3266449	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2365:	learn: 75461.6624360	test: 115986.5078303	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2366:	learn: 75456.1955127	test: 115987.9415714	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2367:	learn: 75444.4873283	test: 115976.1228770	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2368:	learn: 75436.5217552	test: 115975.9312043	best: 115972.0197915 (2354)	total: 13.8s	remaining: 44.4s
    2369:	learn: 75428.7426771	test: 115971.2462583	best: 115971.2462583 (2369)	total: 13.8s	remaining: 44.4s
    2370:	learn: 75423.3873405	test: 115970.5020612	best: 115970.5020612 (2370)	total: 13.8s	remaining: 44.4s
    2371:	learn: 75415.2500069	test: 115969.2708210	best: 115969.2708210 (2371)	total: 13.8s	remaining: 44.4s
    2372:	learn: 75410.7974894	test: 115963.5950218	best: 115963.5950218 (2372)	total: 13.8s	remaining: 44.4s
    2373:	learn: 75400.2918076	test: 115961.2325645	best: 115961.2325645 (2373)	total: 13.8s	remaining: 44.4s
    2374:	learn: 75392.1382515	test: 115956.5039199	best: 115956.5039199 (2374)	total: 13.8s	remaining: 44.4s
    2375:	learn: 75385.4655839	test: 115956.6627092	best: 115956.5039199 (2374)	total: 13.8s	remaining: 44.4s
    2376:	learn: 75373.5136721	test: 115950.9250355	best: 115950.9250355 (2376)	total: 13.8s	remaining: 44.3s
    2377:	learn: 75365.6368138	test: 115949.6856164	best: 115949.6856164 (2377)	total: 13.8s	remaining: 44.3s
    2378:	learn: 75356.9417803	test: 115942.9881474	best: 115942.9881474 (2378)	total: 13.8s	remaining: 44.3s
    2379:	learn: 75350.2732136	test: 115947.6460435	best: 115942.9881474 (2378)	total: 13.8s	remaining: 44.3s
    2380:	learn: 75344.7966074	test: 115946.2499547	best: 115942.9881474 (2378)	total: 13.8s	remaining: 44.3s
    2381:	learn: 75334.6578809	test: 115945.0095699	best: 115942.9881474 (2378)	total: 13.9s	remaining: 44.3s
    2382:	learn: 75323.2589708	test: 115951.1348687	best: 115942.9881474 (2378)	total: 13.9s	remaining: 44.3s
    2383:	learn: 75315.6578897	test: 115945.9577062	best: 115942.9881474 (2378)	total: 13.9s	remaining: 44.3s
    2384:	learn: 75300.5944566	test: 115940.1424653	best: 115940.1424653 (2384)	total: 13.9s	remaining: 44.3s
    2385:	learn: 75293.5514918	test: 115939.0534257	best: 115939.0534257 (2385)	total: 13.9s	remaining: 44.3s
    2386:	learn: 75285.1063737	test: 115935.9958680	best: 115935.9958680 (2386)	total: 13.9s	remaining: 44.3s
    2387:	learn: 75279.2485688	test: 115935.3006605	best: 115935.3006605 (2387)	total: 13.9s	remaining: 44.3s
    2388:	learn: 75270.8494774	test: 115933.4376446	best: 115933.4376446 (2388)	total: 13.9s	remaining: 44.3s
    2389:	learn: 75263.1085782	test: 115934.0730950	best: 115933.4376446 (2388)	total: 13.9s	remaining: 44.3s
    2390:	learn: 75246.3439370	test: 115932.2048112	best: 115932.2048112 (2390)	total: 13.9s	remaining: 44.3s
    2391:	learn: 75240.5880653	test: 115930.6246213	best: 115930.6246213 (2391)	total: 13.9s	remaining: 44.3s
    2392:	learn: 75236.6827992	test: 115928.7976768	best: 115928.7976768 (2392)	total: 13.9s	remaining: 44.2s
    2393:	learn: 75231.6101167	test: 115929.1794364	best: 115928.7976768 (2392)	total: 13.9s	remaining: 44.2s
    2394:	learn: 75224.0574438	test: 115926.7942212	best: 115926.7942212 (2394)	total: 13.9s	remaining: 44.2s
    2395:	learn: 75215.5316076	test: 115924.5343131	best: 115924.5343131 (2395)	total: 13.9s	remaining: 44.2s
    2396:	learn: 75210.0583746	test: 115926.5207696	best: 115924.5343131 (2395)	total: 13.9s	remaining: 44.2s
    2397:	learn: 75199.1866208	test: 115926.4227310	best: 115924.5343131 (2395)	total: 13.9s	remaining: 44.2s
    2398:	learn: 75192.7455943	test: 115927.6632200	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2399:	learn: 75178.9258743	test: 115930.5187812	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2400:	learn: 75174.8124701	test: 115930.0116719	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2401:	learn: 75168.1700272	test: 115930.1832988	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2402:	learn: 75161.6685881	test: 115930.2232131	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2403:	learn: 75151.2295987	test: 115927.2885128	best: 115924.5343131 (2395)	total: 14s	remaining: 44.2s
    2404:	learn: 75141.8079226	test: 115918.7589191	best: 115918.7589191 (2404)	total: 14s	remaining: 44.2s
    2405:	learn: 75134.1609837	test: 115916.6197068	best: 115916.6197068 (2405)	total: 14s	remaining: 44.2s
    2406:	learn: 75124.7582558	test: 115916.3197860	best: 115916.3197860 (2406)	total: 14s	remaining: 44.2s
    2407:	learn: 75120.0831197	test: 115919.5131399	best: 115916.3197860 (2406)	total: 14s	remaining: 44.1s
    2408:	learn: 75112.4005268	test: 115918.4690104	best: 115916.3197860 (2406)	total: 14s	remaining: 44.1s
    2409:	learn: 75103.2340423	test: 115911.5662915	best: 115911.5662915 (2409)	total: 14s	remaining: 44.1s
    2410:	learn: 75096.4991391	test: 115915.1926471	best: 115911.5662915 (2409)	total: 14s	remaining: 44.1s
    2411:	learn: 75092.7151824	test: 115915.0696971	best: 115911.5662915 (2409)	total: 14s	remaining: 44.1s
    2412:	learn: 75086.1963872	test: 115912.9127568	best: 115911.5662915 (2409)	total: 14s	remaining: 44.1s
    2413:	learn: 75082.2266717	test: 115909.3372872	best: 115909.3372872 (2413)	total: 14s	remaining: 44.1s
    2414:	learn: 75077.5705657	test: 115907.2125941	best: 115907.2125941 (2414)	total: 14s	remaining: 44.1s
    2415:	learn: 75070.8957405	test: 115905.8170552	best: 115905.8170552 (2415)	total: 14s	remaining: 44.1s
    2416:	learn: 75066.6361414	test: 115904.9059403	best: 115904.9059403 (2416)	total: 14.1s	remaining: 44.1s
    2417:	learn: 75060.2961277	test: 115904.0899889	best: 115904.0899889 (2417)	total: 14.1s	remaining: 44.1s
    2418:	learn: 75050.8128282	test: 115899.7394033	best: 115899.7394033 (2418)	total: 14.1s	remaining: 44.1s
    2419:	learn: 75044.4636546	test: 115900.1583569	best: 115899.7394033 (2418)	total: 14.1s	remaining: 44.1s
    2420:	learn: 75040.7473716	test: 115899.4426583	best: 115899.4426583 (2420)	total: 14.1s	remaining: 44.1s
    2421:	learn: 75036.5241324	test: 115895.4479769	best: 115895.4479769 (2421)	total: 14.1s	remaining: 44.1s
    2422:	learn: 75032.1712600	test: 115895.7144170	best: 115895.4479769 (2421)	total: 14.1s	remaining: 44.1s
    2423:	learn: 75027.8400463	test: 115894.5348938	best: 115894.5348938 (2423)	total: 14.1s	remaining: 44.1s
    2424:	learn: 75022.2484157	test: 115893.8863069	best: 115893.8863069 (2424)	total: 14.1s	remaining: 44s
    2425:	learn: 75015.3904511	test: 115885.5720994	best: 115885.5720994 (2425)	total: 14.1s	remaining: 44s
    2426:	learn: 75006.1068410	test: 115887.4087877	best: 115885.5720994 (2425)	total: 14.1s	remaining: 44s
    2427:	learn: 74997.1608518	test: 115884.6438171	best: 115884.6438171 (2427)	total: 14.1s	remaining: 44s
    2428:	learn: 74988.2691470	test: 115882.9707777	best: 115882.9707777 (2428)	total: 14.1s	remaining: 44s
    2429:	learn: 74981.3187146	test: 115881.2403145	best: 115881.2403145 (2429)	total: 14.1s	remaining: 44s
    2430:	learn: 74970.3200495	test: 115879.0380698	best: 115879.0380698 (2430)	total: 14.1s	remaining: 44s
    2431:	learn: 74961.6436120	test: 115877.6683550	best: 115877.6683550 (2431)	total: 14.1s	remaining: 44s
    2432:	learn: 74956.8544635	test: 115876.7130497	best: 115876.7130497 (2432)	total: 14.1s	remaining: 44s
    2433:	learn: 74944.0727316	test: 115874.7052202	best: 115874.7052202 (2433)	total: 14.2s	remaining: 44s
    2434:	learn: 74939.7496982	test: 115873.7358671	best: 115873.7358671 (2434)	total: 14.2s	remaining: 44s
    2435:	learn: 74933.6329302	test: 115871.6690913	best: 115871.6690913 (2435)	total: 14.2s	remaining: 44s
    2436:	learn: 74924.1327684	test: 115861.7714226	best: 115861.7714226 (2436)	total: 14.2s	remaining: 44s
    2437:	learn: 74917.2310538	test: 115857.6886037	best: 115857.6886037 (2437)	total: 14.2s	remaining: 44s
    2438:	learn: 74914.3372100	test: 115857.2785759	best: 115857.2785759 (2438)	total: 14.2s	remaining: 44s
    2439:	learn: 74906.7881501	test: 115849.3141355	best: 115849.3141355 (2439)	total: 14.2s	remaining: 43.9s
    2440:	learn: 74896.4103047	test: 115848.1941363	best: 115848.1941363 (2440)	total: 14.2s	remaining: 43.9s
    2441:	learn: 74891.7212062	test: 115847.2638102	best: 115847.2638102 (2441)	total: 14.2s	remaining: 43.9s
    2442:	learn: 74877.5621044	test: 115836.8170481	best: 115836.8170481 (2442)	total: 14.2s	remaining: 43.9s
    2443:	learn: 74866.8204101	test: 115832.8042072	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2444:	learn: 74852.1363094	test: 115836.0891817	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2445:	learn: 74845.4076708	test: 115835.4828553	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2446:	learn: 74833.6923005	test: 115836.8308285	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2447:	learn: 74824.1862247	test: 115837.1276630	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2448:	learn: 74817.4585007	test: 115835.3156911	best: 115832.8042072 (2443)	total: 14.2s	remaining: 43.9s
    2449:	learn: 74806.8416164	test: 115831.1875889	best: 115831.1875889 (2449)	total: 14.2s	remaining: 43.9s
    2450:	learn: 74798.1120404	test: 115832.5246570	best: 115831.1875889 (2449)	total: 14.2s	remaining: 43.9s
    2451:	learn: 74789.8007927	test: 115826.0748671	best: 115826.0748671 (2451)	total: 14.3s	remaining: 43.9s
    2452:	learn: 74781.4104554	test: 115824.4888522	best: 115824.4888522 (2452)	total: 14.3s	remaining: 43.9s
    2453:	learn: 74776.7130023	test: 115824.6625174	best: 115824.4888522 (2452)	total: 14.3s	remaining: 43.9s
    2454:	learn: 74767.4925862	test: 115818.5244047	best: 115818.5244047 (2454)	total: 14.3s	remaining: 43.9s
    2455:	learn: 74753.4300480	test: 115814.3348072	best: 115814.3348072 (2455)	total: 14.3s	remaining: 43.9s
    2456:	learn: 74743.2931709	test: 115816.4763470	best: 115814.3348072 (2455)	total: 14.3s	remaining: 43.9s
    2457:	learn: 74736.9311973	test: 115812.8572373	best: 115812.8572373 (2457)	total: 14.3s	remaining: 43.8s
    2458:	learn: 74723.6903108	test: 115809.6126541	best: 115809.6126541 (2458)	total: 14.3s	remaining: 43.8s
    2459:	learn: 74715.4796650	test: 115808.1887910	best: 115808.1887910 (2459)	total: 14.3s	remaining: 43.8s
    2460:	learn: 74705.8588610	test: 115811.8077643	best: 115808.1887910 (2459)	total: 14.3s	remaining: 43.8s
    2461:	learn: 74698.5801831	test: 115808.1575005	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2462:	learn: 74692.0789229	test: 115811.6384914	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2463:	learn: 74678.8078301	test: 115814.4430072	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2464:	learn: 74672.5363712	test: 115815.0000862	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2465:	learn: 74665.2069224	test: 115812.5277934	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2466:	learn: 74660.4844842	test: 115809.4483090	best: 115808.1575005 (2461)	total: 14.3s	remaining: 43.8s
    2467:	learn: 74649.6392684	test: 115806.5743507	best: 115806.5743507 (2467)	total: 14.3s	remaining: 43.8s
    2468:	learn: 74644.7873111	test: 115806.9913335	best: 115806.5743507 (2467)	total: 14.4s	remaining: 43.8s
    2469:	learn: 74637.7820256	test: 115807.3503039	best: 115806.5743507 (2467)	total: 14.4s	remaining: 43.8s
    2470:	learn: 74633.4804393	test: 115805.7568438	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.8s
    2471:	learn: 74629.0169247	test: 115809.3966463	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.8s
    2472:	learn: 74623.0378213	test: 115813.3583449	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.8s
    2473:	learn: 74610.5180778	test: 115820.1056337	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2474:	learn: 74605.7158646	test: 115816.6228482	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2475:	learn: 74596.6351378	test: 115813.4756761	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2476:	learn: 74583.9965875	test: 115810.3486403	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2477:	learn: 74577.5891945	test: 115809.5425603	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2478:	learn: 74568.0557215	test: 115811.7557872	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2479:	learn: 74559.5801675	test: 115808.8792995	best: 115805.7568438 (2470)	total: 14.4s	remaining: 43.7s
    2480:	learn: 74550.2936650	test: 115801.2142078	best: 115801.2142078 (2480)	total: 14.4s	remaining: 43.7s
    2481:	learn: 74545.9960739	test: 115800.7290234	best: 115800.7290234 (2481)	total: 14.4s	remaining: 43.7s
    2482:	learn: 74539.4258720	test: 115794.8025010	best: 115794.8025010 (2482)	total: 14.4s	remaining: 43.7s
    2483:	learn: 74535.4551381	test: 115792.3391717	best: 115792.3391717 (2483)	total: 14.4s	remaining: 43.7s
    2484:	learn: 74525.5567176	test: 115783.5866245	best: 115783.5866245 (2484)	total: 14.5s	remaining: 43.7s
    2485:	learn: 74513.7158003	test: 115786.2175622	best: 115783.5866245 (2484)	total: 14.5s	remaining: 43.7s
    2486:	learn: 74504.7635990	test: 115783.2785637	best: 115783.2785637 (2486)	total: 14.5s	remaining: 43.7s
    2487:	learn: 74500.3385625	test: 115779.5926345	best: 115779.5926345 (2487)	total: 14.5s	remaining: 43.7s
    2488:	learn: 74496.0899901	test: 115779.5883656	best: 115779.5883656 (2488)	total: 14.5s	remaining: 43.7s
    2489:	learn: 74489.3237150	test: 115778.8733782	best: 115778.8733782 (2489)	total: 14.5s	remaining: 43.7s
    2490:	learn: 74472.8628380	test: 115769.0751745	best: 115769.0751745 (2490)	total: 14.5s	remaining: 43.7s
    2491:	learn: 74463.1662798	test: 115769.2357633	best: 115769.0751745 (2490)	total: 14.5s	remaining: 43.7s
    2492:	learn: 74450.8341701	test: 115766.1685385	best: 115766.1685385 (2492)	total: 14.5s	remaining: 43.7s
    2493:	learn: 74442.2159653	test: 115764.4924500	best: 115764.4924500 (2493)	total: 14.5s	remaining: 43.7s
    2494:	learn: 74435.9542022	test: 115764.3858691	best: 115764.3858691 (2494)	total: 14.5s	remaining: 43.7s
    2495:	learn: 74426.8218861	test: 115763.5724397	best: 115763.5724397 (2495)	total: 14.5s	remaining: 43.7s
    2496:	learn: 74420.7154413	test: 115760.5145742	best: 115760.5145742 (2496)	total: 14.5s	remaining: 43.7s
    2497:	learn: 74414.5670211	test: 115758.7281803	best: 115758.7281803 (2497)	total: 14.5s	remaining: 43.7s
    2498:	learn: 74406.8171658	test: 115761.7597827	best: 115758.7281803 (2497)	total: 14.5s	remaining: 43.6s
    2499:	learn: 74399.5570555	test: 115762.2623136	best: 115758.7281803 (2497)	total: 14.5s	remaining: 43.6s
    2500:	learn: 74389.2723590	test: 115766.9351163	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2501:	learn: 74377.4140453	test: 115761.5787210	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2502:	learn: 74367.7698236	test: 115762.1476482	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2503:	learn: 74359.6300969	test: 115761.9747252	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2504:	learn: 74353.9162002	test: 115762.4937465	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2505:	learn: 74342.9193635	test: 115762.4218915	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2506:	learn: 74333.7690877	test: 115763.6170709	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2507:	learn: 74326.3415627	test: 115764.4019901	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2508:	learn: 74319.7494799	test: 115766.4813692	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2509:	learn: 74313.5639251	test: 115769.9930654	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2510:	learn: 74296.4938841	test: 115766.7146947	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2511:	learn: 74286.3569816	test: 115765.2341173	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2512:	learn: 74279.8994015	test: 115763.0565778	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2513:	learn: 74275.1603197	test: 115769.3215775	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2514:	learn: 74267.3044099	test: 115770.8313248	best: 115758.7281803 (2497)	total: 14.6s	remaining: 43.6s
    2515:	learn: 74262.2438683	test: 115769.7962859	best: 115758.7281803 (2497)	total: 14.7s	remaining: 43.6s
    2516:	learn: 74251.8006464	test: 115764.2559055	best: 115758.7281803 (2497)	total: 14.7s	remaining: 43.6s
    2517:	learn: 74239.9513426	test: 115761.3092655	best: 115758.7281803 (2497)	total: 14.7s	remaining: 43.6s
    2518:	learn: 74231.3275388	test: 115759.0743790	best: 115758.7281803 (2497)	total: 14.7s	remaining: 43.6s
    2519:	learn: 74222.7074288	test: 115750.3092208	best: 115750.3092208 (2519)	total: 14.7s	remaining: 43.6s
    2520:	learn: 74214.3747303	test: 115750.3524406	best: 115750.3092208 (2519)	total: 14.7s	remaining: 43.6s
    2521:	learn: 74209.4244493	test: 115751.8449611	best: 115750.3092208 (2519)	total: 14.7s	remaining: 43.6s
    2522:	learn: 74198.2784772	test: 115748.3002719	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.6s
    2523:	learn: 74194.0544462	test: 115759.7847085	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2524:	learn: 74187.5069745	test: 115757.5640622	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2525:	learn: 74180.2805623	test: 115756.8005082	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2526:	learn: 74170.1958443	test: 115755.3086032	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2527:	learn: 74163.2245017	test: 115756.2596469	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2528:	learn: 74156.4259777	test: 115756.5862781	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2529:	learn: 74148.4431251	test: 115760.0956094	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2530:	learn: 74145.6616744	test: 115759.7259362	best: 115748.3002719 (2522)	total: 14.7s	remaining: 43.5s
    2531:	learn: 74135.4310768	test: 115760.4166681	best: 115748.3002719 (2522)	total: 14.8s	remaining: 43.5s
    2532:	learn: 74125.3978814	test: 115755.6857885	best: 115748.3002719 (2522)	total: 14.8s	remaining: 43.5s
    2533:	learn: 74117.3490328	test: 115752.7998810	best: 115748.3002719 (2522)	total: 14.8s	remaining: 43.5s
    2534:	learn: 74107.5022765	test: 115748.0485171	best: 115748.0485171 (2534)	total: 14.8s	remaining: 43.5s
    2535:	learn: 74101.2844523	test: 115747.6244172	best: 115747.6244172 (2535)	total: 14.8s	remaining: 43.5s
    2536:	learn: 74094.5398180	test: 115746.2852841	best: 115746.2852841 (2536)	total: 14.8s	remaining: 43.5s
    2537:	learn: 74079.8265159	test: 115734.8455968	best: 115734.8455968 (2537)	total: 14.8s	remaining: 43.5s
    2538:	learn: 74073.6497220	test: 115731.3144719	best: 115731.3144719 (2538)	total: 14.8s	remaining: 43.5s
    2539:	learn: 74066.7450600	test: 115729.2568163	best: 115729.2568163 (2539)	total: 14.8s	remaining: 43.5s
    2540:	learn: 74059.0891359	test: 115725.7924535	best: 115725.7924535 (2540)	total: 14.8s	remaining: 43.5s
    2541:	learn: 74051.9770012	test: 115724.4196801	best: 115724.4196801 (2541)	total: 14.8s	remaining: 43.5s
    2542:	learn: 74047.2034471	test: 115723.1615602	best: 115723.1615602 (2542)	total: 14.8s	remaining: 43.5s
    2543:	learn: 74037.7327832	test: 115727.5863470	best: 115723.1615602 (2542)	total: 14.8s	remaining: 43.4s
    2544:	learn: 74025.0886700	test: 115722.1005462	best: 115722.1005462 (2544)	total: 14.8s	remaining: 43.4s
    2545:	learn: 74017.7790307	test: 115720.7112878	best: 115720.7112878 (2545)	total: 14.8s	remaining: 43.4s
    2546:	learn: 74010.6984593	test: 115721.6643750	best: 115720.7112878 (2545)	total: 14.8s	remaining: 43.4s
    2547:	learn: 74002.9541990	test: 115719.3213454	best: 115719.3213454 (2547)	total: 14.8s	remaining: 43.4s
    2548:	learn: 73993.0699589	test: 115718.1930242	best: 115718.1930242 (2548)	total: 14.8s	remaining: 43.4s
    2549:	learn: 73984.8098183	test: 115718.3923200	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2550:	learn: 73975.9302751	test: 115720.3105969	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2551:	learn: 73970.5611319	test: 115719.5049182	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2552:	learn: 73965.1918867	test: 115720.5085537	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2553:	learn: 73955.1903499	test: 115722.7332740	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2554:	learn: 73949.0274897	test: 115723.1966979	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2555:	learn: 73938.6289272	test: 115722.3264716	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2556:	learn: 73933.2742401	test: 115723.6354875	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2557:	learn: 73924.5283208	test: 115730.9928292	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.4s
    2558:	learn: 73919.5334083	test: 115730.0975805	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.3s
    2559:	learn: 73909.2208784	test: 115725.9175038	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.3s
    2560:	learn: 73899.2885200	test: 115722.9232072	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.3s
    2561:	learn: 73890.9910347	test: 115719.3185704	best: 115718.1930242 (2548)	total: 14.9s	remaining: 43.3s
    2562:	learn: 73881.5124109	test: 115708.1362187	best: 115708.1362187 (2562)	total: 14.9s	remaining: 43.3s
    2563:	learn: 73874.4618384	test: 115710.6025018	best: 115708.1362187 (2562)	total: 14.9s	remaining: 43.3s
    2564:	learn: 73862.8802493	test: 115710.7578762	best: 115708.1362187 (2562)	total: 14.9s	remaining: 43.3s
    2565:	learn: 73857.7243830	test: 115707.0217207	best: 115707.0217207 (2565)	total: 14.9s	remaining: 43.3s
    2566:	learn: 73849.1542079	test: 115706.6483365	best: 115706.6483365 (2566)	total: 15s	remaining: 43.3s
    2567:	learn: 73837.7449120	test: 115700.7854376	best: 115700.7854376 (2567)	total: 15s	remaining: 43.3s
    2568:	learn: 73830.5949806	test: 115706.5441514	best: 115700.7854376 (2567)	total: 15s	remaining: 43.3s
    2569:	learn: 73820.7075357	test: 115701.6177118	best: 115700.7854376 (2567)	total: 15s	remaining: 43.3s
    2570:	learn: 73812.5727614	test: 115697.6594142	best: 115697.6594142 (2570)	total: 15s	remaining: 43.3s
    2571:	learn: 73803.4539897	test: 115694.5389782	best: 115694.5389782 (2571)	total: 15s	remaining: 43.3s
    2572:	learn: 73799.5018416	test: 115694.6319384	best: 115694.5389782 (2571)	total: 15s	remaining: 43.3s
    2573:	learn: 73793.2885446	test: 115692.2813601	best: 115692.2813601 (2573)	total: 15s	remaining: 43.3s
    2574:	learn: 73784.8472090	test: 115695.2396454	best: 115692.2813601 (2573)	total: 15s	remaining: 43.3s
    2575:	learn: 73780.0490135	test: 115694.0528916	best: 115692.2813601 (2573)	total: 15s	remaining: 43.2s
    2576:	learn: 73764.6239348	test: 115685.2922354	best: 115685.2922354 (2576)	total: 15s	remaining: 43.2s
    2577:	learn: 73757.0931813	test: 115682.0390055	best: 115682.0390055 (2577)	total: 15s	remaining: 43.2s
    2578:	learn: 73749.9667433	test: 115680.1524506	best: 115680.1524506 (2578)	total: 15s	remaining: 43.2s
    2579:	learn: 73741.6803655	test: 115678.5224965	best: 115678.5224965 (2579)	total: 15s	remaining: 43.2s
    2580:	learn: 73731.8019964	test: 115678.8823908	best: 115678.5224965 (2579)	total: 15s	remaining: 43.2s
    2581:	learn: 73726.8397327	test: 115678.2037785	best: 115678.2037785 (2581)	total: 15s	remaining: 43.2s
    2582:	learn: 73722.8224887	test: 115669.4964258	best: 115669.4964258 (2582)	total: 15s	remaining: 43.2s
    2583:	learn: 73712.7077109	test: 115672.3950174	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2584:	learn: 73704.0856459	test: 115673.1883368	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2585:	learn: 73693.3655334	test: 115672.1925052	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2586:	learn: 73683.5082535	test: 115674.3209386	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2587:	learn: 73676.0168874	test: 115675.4641339	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2588:	learn: 73669.9328928	test: 115674.9919934	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2589:	learn: 73667.0367638	test: 115678.8683888	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2590:	learn: 73657.3192888	test: 115680.7552901	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2591:	learn: 73648.6776416	test: 115682.9436721	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2592:	learn: 73641.2204237	test: 115683.8420779	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.2s
    2593:	learn: 73630.8127868	test: 115677.8262521	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2594:	learn: 73622.6093372	test: 115677.5367345	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2595:	learn: 73615.8097553	test: 115675.8681311	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2596:	learn: 73607.7033853	test: 115674.3468917	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2597:	learn: 73600.1432801	test: 115671.0062657	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2598:	learn: 73590.7852606	test: 115670.4885053	best: 115669.4964258 (2582)	total: 15.1s	remaining: 43.1s
    2599:	learn: 73584.3376884	test: 115669.0669048	best: 115669.0669048 (2599)	total: 15.1s	remaining: 43.1s
    2600:	learn: 73577.0896796	test: 115669.5197102	best: 115669.0669048 (2599)	total: 15.2s	remaining: 43.1s
    2601:	learn: 73569.5413334	test: 115669.2625542	best: 115669.0669048 (2599)	total: 15.2s	remaining: 43.1s
    2602:	learn: 73560.3024715	test: 115669.9929033	best: 115669.0669048 (2599)	total: 15.2s	remaining: 43.1s
    2603:	learn: 73554.6200675	test: 115662.6696839	best: 115662.6696839 (2603)	total: 15.2s	remaining: 43.1s
    2604:	learn: 73543.4750719	test: 115659.1712155	best: 115659.1712155 (2604)	total: 15.2s	remaining: 43.1s
    2605:	learn: 73535.7120992	test: 115655.5455251	best: 115655.5455251 (2605)	total: 15.2s	remaining: 43.1s
    2606:	learn: 73526.1813425	test: 115656.9375979	best: 115655.5455251 (2605)	total: 15.2s	remaining: 43.1s
    2607:	learn: 73516.0019346	test: 115651.0134598	best: 115651.0134598 (2607)	total: 15.2s	remaining: 43.1s
    2608:	learn: 73507.0132867	test: 115648.2639056	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43.1s
    2609:	learn: 73500.7561217	test: 115651.8325578	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43s
    2610:	learn: 73494.5536731	test: 115655.0829092	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43s
    2611:	learn: 73487.6582768	test: 115653.2987594	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43s
    2612:	learn: 73480.5753708	test: 115650.4847227	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43s
    2613:	learn: 73474.8680465	test: 115650.5093327	best: 115648.2639056 (2608)	total: 15.2s	remaining: 43s
    2614:	learn: 73462.8171493	test: 115645.7053159	best: 115645.7053159 (2614)	total: 15.2s	remaining: 43s
    2615:	learn: 73459.3425955	test: 115645.6819296	best: 115645.6819296 (2615)	total: 15.2s	remaining: 43s
    2616:	learn: 73455.3916280	test: 115645.0588092	best: 115645.0588092 (2616)	total: 15.2s	remaining: 43s
    2617:	learn: 73445.9160515	test: 115641.2137451	best: 115641.2137451 (2617)	total: 15.2s	remaining: 43s
    2618:	learn: 73437.9890431	test: 115643.5576558	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2619:	learn: 73433.5253655	test: 115649.7407265	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2620:	learn: 73425.9444974	test: 115649.5169363	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2621:	learn: 73419.6619794	test: 115648.4354075	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2622:	learn: 73414.1269643	test: 115646.7231458	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2623:	learn: 73407.8227172	test: 115645.5444212	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2624:	learn: 73399.7790038	test: 115643.3275238	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2625:	learn: 73392.8695495	test: 115644.6501472	best: 115641.2137451 (2617)	total: 15.3s	remaining: 43s
    2626:	learn: 73386.8060908	test: 115644.9585758	best: 115641.2137451 (2617)	total: 15.3s	remaining: 42.9s
    2627:	learn: 73377.5056101	test: 115638.4056784	best: 115638.4056784 (2627)	total: 15.3s	remaining: 42.9s
    2628:	learn: 73370.6299837	test: 115639.4137092	best: 115638.4056784 (2627)	total: 15.3s	remaining: 42.9s
    2629:	learn: 73363.2540128	test: 115629.9688527	best: 115629.9688527 (2629)	total: 15.3s	remaining: 42.9s
    2630:	learn: 73352.1300932	test: 115626.3390991	best: 115626.3390991 (2630)	total: 15.3s	remaining: 42.9s
    2631:	learn: 73342.5615735	test: 115622.1149221	best: 115622.1149221 (2631)	total: 15.3s	remaining: 42.9s
    2632:	learn: 73330.7374335	test: 115617.6500782	best: 115617.6500782 (2632)	total: 15.3s	remaining: 42.9s
    2633:	learn: 73321.9776636	test: 115618.1841656	best: 115617.6500782 (2632)	total: 15.3s	remaining: 42.9s
    2634:	learn: 73315.5189798	test: 115618.1635001	best: 115617.6500782 (2632)	total: 15.3s	remaining: 42.9s
    2635:	learn: 73307.3761431	test: 115616.9960129	best: 115616.9960129 (2635)	total: 15.4s	remaining: 42.9s
    2636:	learn: 73299.3528025	test: 115614.8161226	best: 115614.8161226 (2636)	total: 15.4s	remaining: 42.9s
    2637:	learn: 73292.1680386	test: 115605.4915523	best: 115605.4915523 (2637)	total: 15.4s	remaining: 42.9s
    2638:	learn: 73283.7879173	test: 115602.3317475	best: 115602.3317475 (2638)	total: 15.4s	remaining: 42.9s
    2639:	learn: 73275.6671442	test: 115602.8087071	best: 115602.3317475 (2638)	total: 15.4s	remaining: 42.9s
    2640:	learn: 73272.0935620	test: 115601.2708898	best: 115601.2708898 (2640)	total: 15.4s	remaining: 42.9s
    2641:	learn: 73262.9094842	test: 115599.6422129	best: 115599.6422129 (2641)	total: 15.4s	remaining: 42.9s
    2642:	learn: 73251.4036980	test: 115597.1372365	best: 115597.1372365 (2642)	total: 15.4s	remaining: 42.9s
    2643:	learn: 73242.3844868	test: 115597.6227662	best: 115597.1372365 (2642)	total: 15.4s	remaining: 42.9s
    2644:	learn: 73238.7753752	test: 115595.4862961	best: 115595.4862961 (2644)	total: 15.4s	remaining: 42.9s
    2645:	learn: 73232.6135186	test: 115590.0368182	best: 115590.0368182 (2645)	total: 15.4s	remaining: 42.9s
    2646:	learn: 73228.7868350	test: 115587.7916248	best: 115587.7916248 (2646)	total: 15.4s	remaining: 42.9s
    2647:	learn: 73218.0453032	test: 115580.6525650	best: 115580.6525650 (2647)	total: 15.4s	remaining: 42.9s
    2648:	learn: 73209.7342504	test: 115574.4140249	best: 115574.4140249 (2648)	total: 15.4s	remaining: 42.9s
    2649:	learn: 73201.5045498	test: 115570.3524309	best: 115570.3524309 (2649)	total: 15.4s	remaining: 42.9s
    2650:	learn: 73185.0588713	test: 115566.4670924	best: 115566.4670924 (2650)	total: 15.5s	remaining: 42.8s
    2651:	learn: 73178.9358939	test: 115563.6389083	best: 115563.6389083 (2651)	total: 15.5s	remaining: 42.8s
    2652:	learn: 73175.1604302	test: 115568.9160677	best: 115563.6389083 (2651)	total: 15.5s	remaining: 42.8s
    2653:	learn: 73168.5875261	test: 115564.7075060	best: 115563.6389083 (2651)	total: 15.5s	remaining: 42.8s
    2654:	learn: 73162.6336159	test: 115562.4915285	best: 115562.4915285 (2654)	total: 15.5s	remaining: 42.8s
    2655:	learn: 73157.5266833	test: 115563.5910970	best: 115562.4915285 (2654)	total: 15.5s	remaining: 42.8s
    2656:	learn: 73152.3832684	test: 115563.3572229	best: 115562.4915285 (2654)	total: 15.5s	remaining: 42.8s
    2657:	learn: 73146.4966232	test: 115563.9739277	best: 115562.4915285 (2654)	total: 15.5s	remaining: 42.8s
    2658:	learn: 73140.3689959	test: 115560.9540910	best: 115560.9540910 (2658)	total: 15.5s	remaining: 42.8s
    2659:	learn: 73130.1577684	test: 115556.5814815	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2660:	learn: 73119.2074436	test: 115560.8691937	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2661:	learn: 73110.8936312	test: 115562.6095659	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2662:	learn: 73097.8739586	test: 115557.0099694	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2663:	learn: 73092.9565821	test: 115557.2563271	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2664:	learn: 73085.1347758	test: 115559.1161256	best: 115556.5814815 (2659)	total: 15.5s	remaining: 42.8s
    2665:	learn: 73077.7083390	test: 115555.0920793	best: 115555.0920793 (2665)	total: 15.5s	remaining: 42.8s
    2666:	learn: 73069.0340411	test: 115545.1835070	best: 115545.1835070 (2666)	total: 15.6s	remaining: 42.8s
    2667:	learn: 73062.4836385	test: 115550.6605912	best: 115545.1835070 (2666)	total: 15.6s	remaining: 42.8s
    2668:	learn: 73055.5318849	test: 115550.6662229	best: 115545.1835070 (2666)	total: 15.6s	remaining: 42.8s
    2669:	learn: 73049.2209813	test: 115547.3574679	best: 115545.1835070 (2666)	total: 15.6s	remaining: 42.8s
    2670:	learn: 73037.9369197	test: 115540.4465600	best: 115540.4465600 (2670)	total: 15.6s	remaining: 42.7s
    2671:	learn: 73022.3482151	test: 115536.4017689	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2672:	learn: 73018.8671459	test: 115542.5320382	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2673:	learn: 73010.1850200	test: 115544.6903087	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2674:	learn: 73005.3324665	test: 115540.3517801	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2675:	learn: 73000.3195411	test: 115540.5764360	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2676:	learn: 72995.6181463	test: 115545.6644939	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2677:	learn: 72989.5798443	test: 115545.2294696	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2678:	learn: 72981.8753552	test: 115545.7949580	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2679:	learn: 72968.4709557	test: 115537.7525270	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2680:	learn: 72961.9346609	test: 115538.0511916	best: 115536.4017689 (2671)	total: 15.6s	remaining: 42.7s
    2681:	learn: 72948.4710421	test: 115540.9946649	best: 115536.4017689 (2671)	total: 15.7s	remaining: 42.7s
    2682:	learn: 72943.5084842	test: 115542.1229623	best: 115536.4017689 (2671)	total: 15.7s	remaining: 42.7s
    2683:	learn: 72936.8642115	test: 115541.3551220	best: 115536.4017689 (2671)	total: 15.7s	remaining: 42.7s
    2684:	learn: 72930.2925880	test: 115539.3095952	best: 115536.4017689 (2671)	total: 15.7s	remaining: 42.7s
    2685:	learn: 72925.7011170	test: 115535.0217238	best: 115535.0217238 (2685)	total: 15.7s	remaining: 42.7s
    2686:	learn: 72921.2014561	test: 115532.8626891	best: 115532.8626891 (2686)	total: 15.7s	remaining: 42.7s
    2687:	learn: 72917.1321912	test: 115530.8310070	best: 115530.8310070 (2687)	total: 15.7s	remaining: 42.7s
    2688:	learn: 72911.1784872	test: 115530.4494876	best: 115530.4494876 (2688)	total: 15.7s	remaining: 42.7s
    2689:	learn: 72901.5713448	test: 115530.0093228	best: 115530.0093228 (2689)	total: 15.7s	remaining: 42.7s
    2690:	learn: 72884.2435379	test: 115531.2082664	best: 115530.0093228 (2689)	total: 15.7s	remaining: 42.7s
    2691:	learn: 72877.8211910	test: 115528.9809666	best: 115528.9809666 (2691)	total: 15.7s	remaining: 42.7s
    2692:	learn: 72871.0324707	test: 115534.0935756	best: 115528.9809666 (2691)	total: 15.7s	remaining: 42.7s
    2693:	learn: 72860.0983333	test: 115528.4598705	best: 115528.4598705 (2693)	total: 15.7s	remaining: 42.6s
    2694:	learn: 72854.6734731	test: 115528.4963231	best: 115528.4598705 (2693)	total: 15.7s	remaining: 42.6s
    2695:	learn: 72848.2409269	test: 115523.1387614	best: 115523.1387614 (2695)	total: 15.7s	remaining: 42.6s
    2696:	learn: 72841.5056753	test: 115520.5796487	best: 115520.5796487 (2696)	total: 15.7s	remaining: 42.6s
    2697:	learn: 72835.6272593	test: 115519.0667995	best: 115519.0667995 (2697)	total: 15.7s	remaining: 42.6s
    2698:	learn: 72826.6822829	test: 115515.2033360	best: 115515.2033360 (2698)	total: 15.8s	remaining: 42.6s
    2699:	learn: 72817.3233392	test: 115517.3987950	best: 115515.2033360 (2698)	total: 15.8s	remaining: 42.6s
    2700:	learn: 72807.2196144	test: 115515.5245470	best: 115515.2033360 (2698)	total: 15.8s	remaining: 42.6s
    2701:	learn: 72800.2141463	test: 115512.1308969	best: 115512.1308969 (2701)	total: 15.8s	remaining: 42.6s
    2702:	learn: 72792.5447439	test: 115511.8620832	best: 115511.8620832 (2702)	total: 15.8s	remaining: 42.6s
    2703:	learn: 72788.5768146	test: 115511.4397742	best: 115511.4397742 (2703)	total: 15.8s	remaining: 42.6s
    2704:	learn: 72780.3789853	test: 115504.0458471	best: 115504.0458471 (2704)	total: 15.8s	remaining: 42.6s
    2705:	learn: 72770.8257265	test: 115500.0326160	best: 115500.0326160 (2705)	total: 15.8s	remaining: 42.6s
    2706:	learn: 72764.7202585	test: 115500.1905673	best: 115500.0326160 (2705)	total: 15.8s	remaining: 42.6s
    2707:	learn: 72759.8861005	test: 115499.3594780	best: 115499.3594780 (2707)	total: 15.8s	remaining: 42.6s
    2708:	learn: 72750.3706320	test: 115500.9918168	best: 115499.3594780 (2707)	total: 15.8s	remaining: 42.6s
    2709:	learn: 72743.0083690	test: 115498.1470545	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.6s
    2710:	learn: 72734.8867260	test: 115499.8548225	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.5s
    2711:	learn: 72724.1601959	test: 115501.3781973	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.5s
    2712:	learn: 72718.9317219	test: 115502.0831771	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.5s
    2713:	learn: 72713.5027187	test: 115502.6890780	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.5s
    2714:	learn: 72704.0991889	test: 115507.9165183	best: 115498.1470545 (2709)	total: 15.8s	remaining: 42.5s
    2715:	learn: 72699.0447803	test: 115508.6503568	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2716:	learn: 72694.2912022	test: 115506.2940672	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2717:	learn: 72690.3846829	test: 115503.1400103	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2718:	learn: 72679.3698976	test: 115500.8631268	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2719:	learn: 72673.7887184	test: 115501.1649190	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2720:	learn: 72665.8612964	test: 115501.0547975	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2721:	learn: 72660.8001724	test: 115498.2326422	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2722:	learn: 72652.8064709	test: 115499.3005401	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2723:	learn: 72645.3053184	test: 115503.8913113	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2724:	learn: 72637.3736041	test: 115503.3560733	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.5s
    2725:	learn: 72630.1839559	test: 115500.2203885	best: 115498.1470545 (2709)	total: 15.9s	remaining: 42.4s
    2726:	learn: 72615.4465713	test: 115497.0619813	best: 115497.0619813 (2726)	total: 15.9s	remaining: 42.4s
    2727:	learn: 72610.0162516	test: 115497.7786595	best: 115497.0619813 (2726)	total: 15.9s	remaining: 42.4s
    2728:	learn: 72600.9835102	test: 115499.5252634	best: 115497.0619813 (2726)	total: 15.9s	remaining: 42.4s
    2729:	learn: 72595.9735972	test: 115498.3833406	best: 115497.0619813 (2726)	total: 15.9s	remaining: 42.4s
    2730:	learn: 72589.6125295	test: 115497.0216749	best: 115497.0216749 (2730)	total: 15.9s	remaining: 42.4s
    2731:	learn: 72581.5780279	test: 115495.8272629	best: 115495.8272629 (2731)	total: 15.9s	remaining: 42.4s
    2732:	learn: 72574.1705682	test: 115492.9677993	best: 115492.9677993 (2732)	total: 15.9s	remaining: 42.4s
    2733:	learn: 72570.7024341	test: 115491.0400340	best: 115491.0400340 (2733)	total: 16s	remaining: 42.4s
    2734:	learn: 72555.6775933	test: 115482.4945875	best: 115482.4945875 (2734)	total: 16s	remaining: 42.4s
    2735:	learn: 72549.3881879	test: 115483.4605643	best: 115482.4945875 (2734)	total: 16s	remaining: 42.4s
    2736:	learn: 72541.0543777	test: 115484.3205961	best: 115482.4945875 (2734)	total: 16s	remaining: 42.4s
    2737:	learn: 72531.5757173	test: 115478.1322333	best: 115478.1322333 (2737)	total: 16s	remaining: 42.4s
    2738:	learn: 72522.4915448	test: 115477.4925145	best: 115477.4925145 (2738)	total: 16s	remaining: 42.4s
    2739:	learn: 72515.4884843	test: 115472.3545776	best: 115472.3545776 (2739)	total: 16s	remaining: 42.4s
    2740:	learn: 72510.0249122	test: 115474.7686259	best: 115472.3545776 (2739)	total: 16s	remaining: 42.4s
    2741:	learn: 72505.3634672	test: 115470.9884992	best: 115470.9884992 (2741)	total: 16s	remaining: 42.4s
    2742:	learn: 72495.9544418	test: 115474.1228964	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2743:	learn: 72488.9844525	test: 115473.0869194	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2744:	learn: 72483.3438746	test: 115476.3045379	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2745:	learn: 72471.0374964	test: 115476.3947826	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2746:	learn: 72463.3080618	test: 115480.0829535	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2747:	learn: 72455.2314437	test: 115471.9217637	best: 115470.9884992 (2741)	total: 16s	remaining: 42.3s
    2748:	learn: 72445.1965372	test: 115468.3088851	best: 115468.3088851 (2748)	total: 16s	remaining: 42.3s
    2749:	learn: 72438.7999847	test: 115465.7336922	best: 115465.7336922 (2749)	total: 16s	remaining: 42.3s
    2750:	learn: 72432.7691550	test: 115465.6103167	best: 115465.6103167 (2750)	total: 16.1s	remaining: 42.3s
    2751:	learn: 72428.6701914	test: 115471.8673414	best: 115465.6103167 (2750)	total: 16.1s	remaining: 42.3s
    2752:	learn: 72415.2995332	test: 115466.6266478	best: 115465.6103167 (2750)	total: 16.1s	remaining: 42.3s
    2753:	learn: 72408.3531722	test: 115464.7286795	best: 115464.7286795 (2753)	total: 16.1s	remaining: 42.3s
    2754:	learn: 72402.1211390	test: 115461.1890878	best: 115461.1890878 (2754)	total: 16.1s	remaining: 42.3s
    2755:	learn: 72389.9067931	test: 115456.6147579	best: 115456.6147579 (2755)	total: 16.1s	remaining: 42.3s
    2756:	learn: 72384.1258090	test: 115455.0048142	best: 115455.0048142 (2756)	total: 16.1s	remaining: 42.3s
    2757:	learn: 72377.6388762	test: 115454.7193885	best: 115454.7193885 (2757)	total: 16.1s	remaining: 42.3s
    2758:	learn: 72371.4987409	test: 115452.4185543	best: 115452.4185543 (2758)	total: 16.1s	remaining: 42.2s
    2759:	learn: 72363.8670759	test: 115451.2177871	best: 115451.2177871 (2759)	total: 16.1s	remaining: 42.2s
    2760:	learn: 72354.4907091	test: 115445.8828671	best: 115445.8828671 (2760)	total: 16.1s	remaining: 42.2s
    2761:	learn: 72344.4310737	test: 115441.1332937	best: 115441.1332937 (2761)	total: 16.1s	remaining: 42.2s
    2762:	learn: 72338.3840912	test: 115439.1223364	best: 115439.1223364 (2762)	total: 16.1s	remaining: 42.2s
    2763:	learn: 72334.7648472	test: 115434.4010028	best: 115434.4010028 (2763)	total: 16.1s	remaining: 42.2s
    2764:	learn: 72329.7104388	test: 115434.1117901	best: 115434.1117901 (2764)	total: 16.1s	remaining: 42.2s
    2765:	learn: 72322.9686615	test: 115435.8478449	best: 115434.1117901 (2764)	total: 16.1s	remaining: 42.2s
    2766:	learn: 72315.7694840	test: 115435.1652559	best: 115434.1117901 (2764)	total: 16.1s	remaining: 42.2s
    2767:	learn: 72306.4566749	test: 115434.1608517	best: 115434.1117901 (2764)	total: 16.2s	remaining: 42.2s
    2768:	learn: 72297.6999130	test: 115434.6011282	best: 115434.1117901 (2764)	total: 16.2s	remaining: 42.2s
    2769:	learn: 72288.4342685	test: 115431.8371618	best: 115431.8371618 (2769)	total: 16.2s	remaining: 42.2s
    2770:	learn: 72282.1421381	test: 115429.8322826	best: 115429.8322826 (2770)	total: 16.2s	remaining: 42.2s
    2771:	learn: 72275.0966316	test: 115424.7372180	best: 115424.7372180 (2771)	total: 16.2s	remaining: 42.2s
    2772:	learn: 72271.1649222	test: 115420.7317467	best: 115420.7317467 (2772)	total: 16.2s	remaining: 42.2s
    2773:	learn: 72267.7407999	test: 115417.9223019	best: 115417.9223019 (2773)	total: 16.2s	remaining: 42.2s
    2774:	learn: 72260.4923658	test: 115421.5765626	best: 115417.9223019 (2773)	total: 16.2s	remaining: 42.2s
    2775:	learn: 72244.9722431	test: 115413.1111096	best: 115413.1111096 (2775)	total: 16.2s	remaining: 42.1s
    2776:	learn: 72239.2788036	test: 115411.9858239	best: 115411.9858239 (2776)	total: 16.2s	remaining: 42.1s
    2777:	learn: 72228.3123499	test: 115408.9696454	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2778:	learn: 72224.1707905	test: 115417.3128852	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2779:	learn: 72212.3090516	test: 115418.4951984	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2780:	learn: 72201.9574298	test: 115418.3281105	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2781:	learn: 72198.8773039	test: 115419.8448285	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2782:	learn: 72191.7492161	test: 115419.7413604	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2783:	learn: 72182.1777219	test: 115419.2629693	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2784:	learn: 72177.9484216	test: 115423.3407848	best: 115408.9696454 (2777)	total: 16.2s	remaining: 42.1s
    2785:	learn: 72171.4321503	test: 115420.9978557	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42.1s
    2786:	learn: 72162.8713020	test: 115419.7629173	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42.1s
    2787:	learn: 72156.6652269	test: 115414.8894794	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42.1s
    2788:	learn: 72150.6131478	test: 115418.2469277	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42.1s
    2789:	learn: 72143.0668138	test: 115415.6388353	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42.1s
    2790:	learn: 72136.9614776	test: 115416.0829865	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42s
    2791:	learn: 72130.3483457	test: 115417.5360657	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42s
    2792:	learn: 72120.9568491	test: 115416.4398820	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42s
    2793:	learn: 72113.8447563	test: 115414.4188630	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42s
    2794:	learn: 72109.4791294	test: 115409.1495393	best: 115408.9696454 (2777)	total: 16.3s	remaining: 42s
    2795:	learn: 72105.3803086	test: 115408.7773980	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2796:	learn: 72100.4018502	test: 115409.8770013	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2797:	learn: 72092.5040513	test: 115409.1638315	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2798:	learn: 72083.9104086	test: 115410.1760388	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2799:	learn: 72078.1488527	test: 115409.3698250	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2800:	learn: 72073.3473053	test: 115410.0915128	best: 115408.7773980 (2795)	total: 16.3s	remaining: 42s
    2801:	learn: 72064.7988746	test: 115406.0716053	best: 115406.0716053 (2801)	total: 16.4s	remaining: 42s
    2802:	learn: 72050.7445471	test: 115396.3783063	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2803:	learn: 72043.1652023	test: 115401.3138838	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2804:	learn: 72036.0037368	test: 115400.8393800	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2805:	learn: 72030.8092367	test: 115401.3750720	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2806:	learn: 72024.9132635	test: 115403.1386631	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2807:	learn: 72017.3717715	test: 115404.2808967	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2808:	learn: 72013.2040049	test: 115403.0875747	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2809:	learn: 72007.8057332	test: 115401.3566317	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2810:	learn: 72001.5558255	test: 115405.8005367	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2811:	learn: 71993.6183282	test: 115405.8673571	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2812:	learn: 71987.6973371	test: 115403.9631376	best: 115396.3783063 (2802)	total: 16.4s	remaining: 42s
    2813:	learn: 71984.3604644	test: 115406.5095025	best: 115396.3783063 (2802)	total: 16.4s	remaining: 41.9s
    2814:	learn: 71979.6018545	test: 115411.6470553	best: 115396.3783063 (2802)	total: 16.4s	remaining: 41.9s
    2815:	learn: 71974.2931908	test: 115410.4934508	best: 115396.3783063 (2802)	total: 16.4s	remaining: 41.9s
    2816:	learn: 71963.3604357	test: 115414.4389312	best: 115396.3783063 (2802)	total: 16.4s	remaining: 41.9s
    2817:	learn: 71955.8313671	test: 115413.5793387	best: 115396.3783063 (2802)	total: 16.4s	remaining: 41.9s
    2818:	learn: 71944.3618930	test: 115413.5770208	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2819:	learn: 71937.0955528	test: 115415.2406141	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2820:	learn: 71932.5149402	test: 115416.9744928	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2821:	learn: 71925.1548969	test: 115416.7455157	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2822:	learn: 71918.9585328	test: 115415.9404733	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2823:	learn: 71914.2784678	test: 115414.5269594	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2824:	learn: 71906.7077741	test: 115415.7956864	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2825:	learn: 71897.8807536	test: 115407.9570369	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2826:	learn: 71892.3842425	test: 115406.6104311	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2827:	learn: 71885.5686128	test: 115407.2404949	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2828:	learn: 71878.1054720	test: 115407.4554281	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2829:	learn: 71866.2376194	test: 115408.0573268	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2830:	learn: 71854.8523780	test: 115400.9072905	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2831:	learn: 71847.1887930	test: 115403.1860052	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2832:	learn: 71840.0961378	test: 115397.1493773	best: 115396.3783063 (2802)	total: 16.5s	remaining: 41.9s
    2833:	learn: 71830.6459241	test: 115395.7712052	best: 115395.7712052 (2833)	total: 16.5s	remaining: 41.8s
    2834:	learn: 71822.0094604	test: 115393.2392938	best: 115393.2392938 (2834)	total: 16.6s	remaining: 41.8s
    2835:	learn: 71815.0239560	test: 115391.6287276	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2836:	learn: 71810.3421047	test: 115395.9486193	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2837:	learn: 71807.1491512	test: 115396.6117917	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2838:	learn: 71801.6270310	test: 115396.6434450	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2839:	learn: 71790.8978231	test: 115392.6606186	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2840:	learn: 71782.0009269	test: 115394.8480436	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2841:	learn: 71772.1738575	test: 115394.7468891	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2842:	learn: 71766.0777869	test: 115394.6066153	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2843:	learn: 71758.8939184	test: 115394.8980613	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2844:	learn: 71749.2320526	test: 115392.9293260	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2845:	learn: 71741.1528586	test: 115394.4300655	best: 115391.6287276 (2835)	total: 16.6s	remaining: 41.8s
    2846:	learn: 71724.6783119	test: 115383.2383178	best: 115383.2383178 (2846)	total: 16.6s	remaining: 41.8s
    2847:	learn: 71717.3732395	test: 115380.9470315	best: 115380.9470315 (2847)	total: 16.6s	remaining: 41.8s
    2848:	learn: 71711.2361307	test: 115380.6181906	best: 115380.6181906 (2848)	total: 16.6s	remaining: 41.8s
    2849:	learn: 71707.3356890	test: 115380.6762335	best: 115380.6181906 (2848)	total: 16.7s	remaining: 41.8s
    2850:	learn: 71697.2314265	test: 115384.6905912	best: 115380.6181906 (2848)	total: 16.7s	remaining: 41.8s
    2851:	learn: 71692.6642590	test: 115385.4775181	best: 115380.6181906 (2848)	total: 16.7s	remaining: 41.8s
    2852:	learn: 71688.4063766	test: 115387.8118340	best: 115380.6181906 (2848)	total: 16.7s	remaining: 41.8s
    2853:	learn: 71679.1804911	test: 115381.6342939	best: 115380.6181906 (2848)	total: 16.7s	remaining: 41.8s
    2854:	learn: 71671.9278318	test: 115378.1570875	best: 115378.1570875 (2854)	total: 16.7s	remaining: 41.8s
    2855:	learn: 71664.8111414	test: 115378.6145889	best: 115378.1570875 (2854)	total: 16.7s	remaining: 41.8s
    2856:	learn: 71657.0209849	test: 115379.0451434	best: 115378.1570875 (2854)	total: 16.7s	remaining: 41.7s
    2857:	learn: 71648.6404036	test: 115373.0993748	best: 115373.0993748 (2857)	total: 16.7s	remaining: 41.7s
    2858:	learn: 71644.2032812	test: 115372.3697483	best: 115372.3697483 (2858)	total: 16.7s	remaining: 41.7s
    2859:	learn: 71639.9010772	test: 115370.8145694	best: 115370.8145694 (2859)	total: 16.7s	remaining: 41.7s
    2860:	learn: 71630.8149851	test: 115368.1235274	best: 115368.1235274 (2860)	total: 16.7s	remaining: 41.7s
    2861:	learn: 71627.6072343	test: 115364.2326864	best: 115364.2326864 (2861)	total: 16.7s	remaining: 41.7s
    2862:	learn: 71622.8420002	test: 115365.3308992	best: 115364.2326864 (2861)	total: 16.7s	remaining: 41.7s
    2863:	learn: 71613.0097683	test: 115369.3398087	best: 115364.2326864 (2861)	total: 16.7s	remaining: 41.7s
    2864:	learn: 71607.5137237	test: 115371.8960325	best: 115364.2326864 (2861)	total: 16.7s	remaining: 41.7s
    2865:	learn: 71599.7755075	test: 115375.4436498	best: 115364.2326864 (2861)	total: 16.7s	remaining: 41.7s
    2866:	learn: 71594.1678016	test: 115376.5929501	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.7s
    2867:	learn: 71583.0886869	test: 115374.8641847	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.7s
    2868:	learn: 71579.3726894	test: 115377.4250288	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.7s
    2869:	learn: 71566.7770213	test: 115373.1017056	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.7s
    2870:	learn: 71563.9200479	test: 115371.1105977	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.7s
    2871:	learn: 71554.1707870	test: 115377.1923133	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2872:	learn: 71543.1383703	test: 115376.7486996	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2873:	learn: 71538.6422857	test: 115376.9361413	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2874:	learn: 71522.5494816	test: 115378.0177876	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2875:	learn: 71517.5932341	test: 115374.6551269	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2876:	learn: 71514.4761009	test: 115372.9042228	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2877:	learn: 71510.4749110	test: 115372.1575106	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2878:	learn: 71503.9160076	test: 115372.7586089	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2879:	learn: 71498.5072342	test: 115371.3470238	best: 115364.2326864 (2861)	total: 16.8s	remaining: 41.6s
    2880:	learn: 71484.3277825	test: 115362.4258739	best: 115362.4258739 (2880)	total: 16.8s	remaining: 41.6s
    2881:	learn: 71475.2699656	test: 115361.7034787	best: 115361.7034787 (2881)	total: 16.8s	remaining: 41.6s
    2882:	learn: 71470.2944072	test: 115361.8117633	best: 115361.7034787 (2881)	total: 16.8s	remaining: 41.6s
    2883:	learn: 71462.9564232	test: 115360.1857729	best: 115360.1857729 (2883)	total: 16.9s	remaining: 41.6s
    2884:	learn: 71457.6558502	test: 115360.7080476	best: 115360.1857729 (2883)	total: 16.9s	remaining: 41.6s
    2885:	learn: 71454.3034456	test: 115352.9811438	best: 115352.9811438 (2885)	total: 16.9s	remaining: 41.6s
    2886:	learn: 71445.1594890	test: 115353.2297140	best: 115352.9811438 (2885)	total: 16.9s	remaining: 41.6s
    2887:	learn: 71441.1855555	test: 115352.6934000	best: 115352.6934000 (2887)	total: 16.9s	remaining: 41.6s
    2888:	learn: 71438.1617797	test: 115351.0105586	best: 115351.0105586 (2888)	total: 16.9s	remaining: 41.5s
    2889:	learn: 71433.8170256	test: 115347.8467985	best: 115347.8467985 (2889)	total: 16.9s	remaining: 41.5s
    2890:	learn: 71423.7145569	test: 115345.9725653	best: 115345.9725653 (2890)	total: 16.9s	remaining: 41.5s
    2891:	learn: 71417.2607741	test: 115348.5689860	best: 115345.9725653 (2890)	total: 16.9s	remaining: 41.5s
    2892:	learn: 71405.3145178	test: 115348.2274734	best: 115345.9725653 (2890)	total: 16.9s	remaining: 41.5s
    2893:	learn: 71399.7035337	test: 115346.5090194	best: 115345.9725653 (2890)	total: 16.9s	remaining: 41.5s
    2894:	learn: 71388.9433750	test: 115340.4187461	best: 115340.4187461 (2894)	total: 16.9s	remaining: 41.5s
    2895:	learn: 71378.5968574	test: 115339.0150529	best: 115339.0150529 (2895)	total: 16.9s	remaining: 41.5s
    2896:	learn: 71373.3675393	test: 115339.9290509	best: 115339.0150529 (2895)	total: 16.9s	remaining: 41.5s
    2897:	learn: 71367.2100611	test: 115339.2801374	best: 115339.0150529 (2895)	total: 16.9s	remaining: 41.5s
    2898:	learn: 71357.8333844	test: 115336.0975491	best: 115336.0975491 (2898)	total: 16.9s	remaining: 41.5s
    2899:	learn: 71352.1500180	test: 115341.5404767	best: 115336.0975491 (2898)	total: 16.9s	remaining: 41.5s
    2900:	learn: 71348.7623745	test: 115345.3070055	best: 115336.0975491 (2898)	total: 16.9s	remaining: 41.5s
    2901:	learn: 71342.1183420	test: 115339.6393478	best: 115336.0975491 (2898)	total: 17s	remaining: 41.5s
    2902:	learn: 71334.8181222	test: 115330.6426891	best: 115330.6426891 (2902)	total: 17s	remaining: 41.5s
    2903:	learn: 71327.6364015	test: 115329.1356679	best: 115329.1356679 (2903)	total: 17s	remaining: 41.5s
    2904:	learn: 71323.3729656	test: 115332.2141449	best: 115329.1356679 (2903)	total: 17s	remaining: 41.4s
    2905:	learn: 71316.6167084	test: 115328.8397307	best: 115328.8397307 (2905)	total: 17s	remaining: 41.4s
    2906:	learn: 71313.3826397	test: 115327.4267780	best: 115327.4267780 (2906)	total: 17s	remaining: 41.4s
    2907:	learn: 71307.8526178	test: 115326.9360117	best: 115326.9360117 (2907)	total: 17s	remaining: 41.4s
    2908:	learn: 71302.7137608	test: 115325.6542894	best: 115325.6542894 (2908)	total: 17s	remaining: 41.4s
    2909:	learn: 71293.6597390	test: 115325.8650732	best: 115325.6542894 (2908)	total: 17s	remaining: 41.4s
    2910:	learn: 71285.9637467	test: 115326.8099631	best: 115325.6542894 (2908)	total: 17s	remaining: 41.4s
    2911:	learn: 71279.9623782	test: 115326.1640261	best: 115325.6542894 (2908)	total: 17s	remaining: 41.4s
    2912:	learn: 71273.0641233	test: 115326.5874204	best: 115325.6542894 (2908)	total: 17s	remaining: 41.4s
    2913:	learn: 71268.3770361	test: 115324.7518319	best: 115324.7518319 (2913)	total: 17s	remaining: 41.4s
    2914:	learn: 71263.3148687	test: 115324.1206116	best: 115324.1206116 (2914)	total: 17s	remaining: 41.4s
    2915:	learn: 71263.0527831	test: 115326.5001822	best: 115324.1206116 (2914)	total: 17s	remaining: 41.4s
    2916:	learn: 71253.6622340	test: 115330.0890587	best: 115324.1206116 (2914)	total: 17s	remaining: 41.4s
    2917:	learn: 71246.0242725	test: 115328.2659826	best: 115324.1206116 (2914)	total: 17s	remaining: 41.4s
    2918:	learn: 71236.5643010	test: 115334.2910360	best: 115324.1206116 (2914)	total: 17.1s	remaining: 41.4s
    2919:	learn: 71233.6308448	test: 115332.6693146	best: 115324.1206116 (2914)	total: 17.1s	remaining: 41.4s
    2920:	learn: 71226.6530727	test: 115334.0881788	best: 115324.1206116 (2914)	total: 17.1s	remaining: 41.4s
    2921:	learn: 71218.6374579	test: 115330.0807034	best: 115324.1206116 (2914)	total: 17.1s	remaining: 41.4s
    2922:	learn: 71214.0294146	test: 115318.6491752	best: 115318.6491752 (2922)	total: 17.1s	remaining: 41.4s
    2923:	learn: 71212.1208382	test: 115318.4605582	best: 115318.4605582 (2923)	total: 17.1s	remaining: 41.3s
    2924:	learn: 71202.9725627	test: 115317.2608594	best: 115317.2608594 (2924)	total: 17.1s	remaining: 41.3s
    2925:	learn: 71200.1982379	test: 115313.4409333	best: 115313.4409333 (2925)	total: 17.1s	remaining: 41.3s
    2926:	learn: 71195.6182531	test: 115311.6158851	best: 115311.6158851 (2926)	total: 17.1s	remaining: 41.3s
    2927:	learn: 71194.5212183	test: 115313.4245767	best: 115311.6158851 (2926)	total: 17.1s	remaining: 41.3s
    2928:	learn: 71187.9970891	test: 115310.3183485	best: 115310.3183485 (2928)	total: 17.1s	remaining: 41.3s
    2929:	learn: 71184.9098749	test: 115308.1180162	best: 115308.1180162 (2929)	total: 17.1s	remaining: 41.3s
    2930:	learn: 71175.4672529	test: 115308.8860242	best: 115308.1180162 (2929)	total: 17.1s	remaining: 41.3s
    2931:	learn: 71166.9938067	test: 115307.1365537	best: 115307.1365537 (2931)	total: 17.1s	remaining: 41.3s
    2932:	learn: 71161.3142013	test: 115306.0489881	best: 115306.0489881 (2932)	total: 17.1s	remaining: 41.3s
    2933:	learn: 71155.2186581	test: 115305.1950349	best: 115305.1950349 (2933)	total: 17.1s	remaining: 41.3s
    2934:	learn: 71146.4470390	test: 115304.9871496	best: 115304.9871496 (2934)	total: 17.1s	remaining: 41.3s
    2935:	learn: 71137.1929000	test: 115303.7790217	best: 115303.7790217 (2935)	total: 17.2s	remaining: 41.3s
    2936:	learn: 71133.2335931	test: 115300.0658959	best: 115300.0658959 (2936)	total: 17.2s	remaining: 41.3s
    2937:	learn: 71126.6859452	test: 115297.9508264	best: 115297.9508264 (2937)	total: 17.2s	remaining: 41.3s
    2938:	learn: 71122.7299803	test: 115295.8623536	best: 115295.8623536 (2938)	total: 17.2s	remaining: 41.3s
    2939:	learn: 71116.5874056	test: 115294.5965243	best: 115294.5965243 (2939)	total: 17.2s	remaining: 41.3s
    2940:	learn: 71110.3829478	test: 115293.6270453	best: 115293.6270453 (2940)	total: 17.2s	remaining: 41.2s
    2941:	learn: 71103.3921416	test: 115293.7321270	best: 115293.6270453 (2940)	total: 17.2s	remaining: 41.2s
    2942:	learn: 71098.8492253	test: 115288.9381284	best: 115288.9381284 (2942)	total: 17.2s	remaining: 41.2s
    2943:	learn: 71093.5531994	test: 115292.3038180	best: 115288.9381284 (2942)	total: 17.2s	remaining: 41.2s
    2944:	learn: 71089.4019525	test: 115291.9217191	best: 115288.9381284 (2942)	total: 17.2s	remaining: 41.2s
    2945:	learn: 71082.7470338	test: 115290.7590543	best: 115288.9381284 (2942)	total: 17.2s	remaining: 41.2s
    2946:	learn: 71074.1088634	test: 115287.0261426	best: 115287.0261426 (2946)	total: 17.2s	remaining: 41.2s
    2947:	learn: 71068.1011235	test: 115285.6843983	best: 115285.6843983 (2947)	total: 17.2s	remaining: 41.2s
    2948:	learn: 71061.0624814	test: 115288.8033643	best: 115285.6843983 (2947)	total: 17.2s	remaining: 41.2s
    2949:	learn: 71055.0763235	test: 115287.5330783	best: 115285.6843983 (2947)	total: 17.2s	remaining: 41.2s
    2950:	learn: 71050.7642567	test: 115287.1068379	best: 115285.6843983 (2947)	total: 17.2s	remaining: 41.2s
    2951:	learn: 71046.1500038	test: 115285.1354697	best: 115285.1354697 (2951)	total: 17.2s	remaining: 41.2s
    2952:	learn: 71043.2950012	test: 115283.5674202	best: 115283.5674202 (2952)	total: 17.3s	remaining: 41.2s
    2953:	learn: 71039.2634082	test: 115284.2039854	best: 115283.5674202 (2952)	total: 17.3s	remaining: 41.2s
    2954:	learn: 71033.3516413	test: 115283.4358810	best: 115283.4358810 (2954)	total: 17.3s	remaining: 41.2s
    2955:	learn: 71025.6662179	test: 115281.8745123	best: 115281.8745123 (2955)	total: 17.3s	remaining: 41.2s
    2956:	learn: 71019.8862580	test: 115281.7540440	best: 115281.7540440 (2956)	total: 17.3s	remaining: 41.2s
    2957:	learn: 71012.1010083	test: 115285.4474569	best: 115281.7540440 (2956)	total: 17.3s	remaining: 41.2s
    2958:	learn: 71003.3872351	test: 115283.0480645	best: 115281.7540440 (2956)	total: 17.3s	remaining: 41.2s
    2959:	learn: 70989.5973328	test: 115280.2743293	best: 115280.2743293 (2959)	total: 17.3s	remaining: 41.1s
    2960:	learn: 70983.0797500	test: 115280.3270763	best: 115280.2743293 (2959)	total: 17.3s	remaining: 41.1s
    2961:	learn: 70977.4098801	test: 115280.8737822	best: 115280.2743293 (2959)	total: 17.3s	remaining: 41.1s
    2962:	learn: 70972.1845057	test: 115280.9897554	best: 115280.2743293 (2959)	total: 17.3s	remaining: 41.1s
    2963:	learn: 70969.1219251	test: 115285.5245539	best: 115280.2743293 (2959)	total: 17.3s	remaining: 41.1s
    2964:	learn: 70960.1816237	test: 115277.8294135	best: 115277.8294135 (2964)	total: 17.3s	remaining: 41.1s
    2965:	learn: 70950.7682118	test: 115278.6435630	best: 115277.8294135 (2964)	total: 17.3s	remaining: 41.1s
    2966:	learn: 70942.7457471	test: 115277.7465944	best: 115277.7465944 (2966)	total: 17.3s	remaining: 41.1s
    2967:	learn: 70936.6751513	test: 115279.5337833	best: 115277.7465944 (2966)	total: 17.4s	remaining: 41.1s
    2968:	learn: 70928.6067660	test: 115281.5631172	best: 115277.7465944 (2966)	total: 17.4s	remaining: 41.1s
    2969:	learn: 70924.5799424	test: 115281.2256023	best: 115277.7465944 (2966)	total: 17.4s	remaining: 41.1s
    2970:	learn: 70914.8089195	test: 115278.1541674	best: 115277.7465944 (2966)	total: 17.4s	remaining: 41.1s
    2971:	learn: 70907.4078609	test: 115276.3421186	best: 115276.3421186 (2971)	total: 17.4s	remaining: 41.1s
    2972:	learn: 70901.8073121	test: 115274.1302116	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2973:	learn: 70898.3975535	test: 115278.3342319	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2974:	learn: 70892.1560686	test: 115277.5078684	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2975:	learn: 70887.3485064	test: 115278.3265178	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2976:	learn: 70873.8454003	test: 115279.9281208	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2977:	learn: 70869.0233343	test: 115280.3127324	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2978:	learn: 70865.1373273	test: 115278.4666168	best: 115274.1302116 (2972)	total: 17.4s	remaining: 41.1s
    2979:	learn: 70858.7181307	test: 115273.9766240	best: 115273.9766240 (2979)	total: 17.4s	remaining: 41s
    2980:	learn: 70852.0414960	test: 115272.1887348	best: 115272.1887348 (2980)	total: 17.4s	remaining: 41s
    2981:	learn: 70851.9280130	test: 115273.5077951	best: 115272.1887348 (2980)	total: 17.4s	remaining: 41s
    2982:	learn: 70848.0480037	test: 115272.0338401	best: 115272.0338401 (2982)	total: 17.4s	remaining: 41s
    2983:	learn: 70844.0326151	test: 115275.0854432	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2984:	learn: 70837.2944370	test: 115275.0937357	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2985:	learn: 70826.6637653	test: 115278.3009583	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2986:	learn: 70824.1300820	test: 115277.9455236	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2987:	learn: 70816.9016872	test: 115274.7313475	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2988:	learn: 70808.2358892	test: 115275.7003447	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2989:	learn: 70804.7697692	test: 115274.9678942	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2990:	learn: 70795.9795371	test: 115276.9887898	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2991:	learn: 70793.7458567	test: 115274.9944696	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2992:	learn: 70790.3359611	test: 115274.8238080	best: 115272.0338401 (2982)	total: 17.5s	remaining: 41s
    2993:	learn: 70780.7587897	test: 115269.2888143	best: 115269.2888143 (2993)	total: 17.5s	remaining: 41s
    2994:	learn: 70776.2338082	test: 115270.3384881	best: 115269.2888143 (2993)	total: 17.5s	remaining: 41s
    2995:	learn: 70769.7805235	test: 115267.6135289	best: 115267.6135289 (2995)	total: 17.5s	remaining: 41s
    2996:	learn: 70764.9182902	test: 115270.1745190	best: 115267.6135289 (2995)	total: 17.5s	remaining: 41s
    2997:	learn: 70758.9143179	test: 115272.9685160	best: 115267.6135289 (2995)	total: 17.5s	remaining: 41s
    2998:	learn: 70748.8918989	test: 115268.8287082	best: 115267.6135289 (2995)	total: 17.5s	remaining: 41s
    2999:	learn: 70745.2038940	test: 115264.1975403	best: 115264.1975403 (2999)	total: 17.6s	remaining: 41s
    3000:	learn: 70737.6262456	test: 115266.2189864	best: 115264.1975403 (2999)	total: 17.6s	remaining: 41s
    3001:	learn: 70726.5938449	test: 115265.4681428	best: 115264.1975403 (2999)	total: 17.6s	remaining: 41s
    3002:	learn: 70720.5219817	test: 115263.1568360	best: 115263.1568360 (3002)	total: 17.6s	remaining: 41s
    3003:	learn: 70712.9089262	test: 115265.0322529	best: 115263.1568360 (3002)	total: 17.6s	remaining: 40.9s
    3004:	learn: 70709.3211972	test: 115270.1243277	best: 115263.1568360 (3002)	total: 17.6s	remaining: 40.9s
    3005:	learn: 70700.9036137	test: 115270.3969584	best: 115263.1568360 (3002)	total: 17.6s	remaining: 40.9s
    3006:	learn: 70692.9628375	test: 115266.2591675	best: 115263.1568360 (3002)	total: 17.6s	remaining: 40.9s
    3007:	learn: 70675.9083678	test: 115258.3445549	best: 115258.3445549 (3007)	total: 17.6s	remaining: 40.9s
    3008:	learn: 70666.9417818	test: 115255.2498096	best: 115255.2498096 (3008)	total: 17.6s	remaining: 40.9s
    3009:	learn: 70653.3838016	test: 115247.5813508	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3010:	learn: 70648.6031324	test: 115247.8563169	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3011:	learn: 70643.2807545	test: 115250.3157100	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3012:	learn: 70642.1427411	test: 115249.2284749	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3013:	learn: 70638.8923142	test: 115253.4134104	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3014:	learn: 70631.7390057	test: 115252.1166121	best: 115247.5813508 (3009)	total: 17.6s	remaining: 40.9s
    3015:	learn: 70623.9575444	test: 115251.6570221	best: 115247.5813508 (3009)	total: 17.7s	remaining: 40.9s
    3016:	learn: 70619.9173919	test: 115252.0972215	best: 115247.5813508 (3009)	total: 17.7s	remaining: 40.9s
    3017:	learn: 70611.5790448	test: 115246.9786765	best: 115246.9786765 (3017)	total: 17.7s	remaining: 40.9s
    3018:	learn: 70600.8216478	test: 115248.7175438	best: 115246.9786765 (3017)	total: 17.7s	remaining: 40.9s
    3019:	learn: 70592.3403207	test: 115245.2648178	best: 115245.2648178 (3019)	total: 17.7s	remaining: 40.9s
    3020:	learn: 70583.8133473	test: 115242.1322140	best: 115242.1322140 (3020)	total: 17.7s	remaining: 40.9s
    3021:	learn: 70575.3345330	test: 115241.0179915	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3022:	learn: 70571.7864783	test: 115243.6795063	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3023:	learn: 70568.0461325	test: 115242.2914769	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3024:	learn: 70562.5483850	test: 115244.5742956	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3025:	learn: 70556.8326290	test: 115244.0204160	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3026:	learn: 70550.9942305	test: 115246.5161735	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3027:	learn: 70546.6151217	test: 115247.5961864	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3028:	learn: 70536.1949113	test: 115246.4461881	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3029:	learn: 70531.6495491	test: 115245.0384873	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3030:	learn: 70529.3926881	test: 115244.8631827	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3031:	learn: 70522.2082702	test: 115244.1382744	best: 115241.0179915 (3021)	total: 17.7s	remaining: 40.8s
    3032:	learn: 70515.3225823	test: 115244.7884191	best: 115241.0179915 (3021)	total: 17.8s	remaining: 40.8s
    3033:	learn: 70509.8910977	test: 115240.8331432	best: 115240.8331432 (3033)	total: 17.8s	remaining: 40.8s
    3034:	learn: 70506.0016563	test: 115239.8678963	best: 115239.8678963 (3034)	total: 17.8s	remaining: 40.8s
    3035:	learn: 70499.7577090	test: 115239.2635040	best: 115239.2635040 (3035)	total: 17.8s	remaining: 40.8s
    3036:	learn: 70491.1954361	test: 115237.7132988	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.8s
    3037:	learn: 70485.6634212	test: 115241.6594884	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.8s
    3038:	learn: 70481.2018635	test: 115242.8008823	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3039:	learn: 70475.3978706	test: 115243.7880753	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3040:	learn: 70467.4417830	test: 115241.1293061	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3041:	learn: 70463.8964670	test: 115245.6190281	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3042:	learn: 70463.7859428	test: 115244.7644935	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3043:	learn: 70455.2218386	test: 115238.9514359	best: 115237.7132988 (3036)	total: 17.8s	remaining: 40.7s
    3044:	learn: 70440.4365983	test: 115234.6718717	best: 115234.6718717 (3044)	total: 17.8s	remaining: 40.7s
    3045:	learn: 70435.6561733	test: 115231.7436220	best: 115231.7436220 (3045)	total: 17.8s	remaining: 40.7s
    3046:	learn: 70427.7766977	test: 115230.5884146	best: 115230.5884146 (3046)	total: 17.8s	remaining: 40.7s
    3047:	learn: 70422.2178426	test: 115230.9971597	best: 115230.5884146 (3046)	total: 17.8s	remaining: 40.7s
    3048:	learn: 70415.4991818	test: 115227.3861217	best: 115227.3861217 (3048)	total: 17.8s	remaining: 40.7s
    3049:	learn: 70411.7705316	test: 115231.4606141	best: 115227.3861217 (3048)	total: 17.8s	remaining: 40.7s
    3050:	learn: 70406.5944802	test: 115229.8361349	best: 115227.3861217 (3048)	total: 17.9s	remaining: 40.7s
    3051:	learn: 70394.5703821	test: 115227.1267571	best: 115227.1267571 (3051)	total: 17.9s	remaining: 40.7s
    3052:	learn: 70380.4387798	test: 115229.1419304	best: 115227.1267571 (3051)	total: 17.9s	remaining: 40.7s
    3053:	learn: 70373.0217578	test: 115222.2586088	best: 115222.2586088 (3053)	total: 17.9s	remaining: 40.7s
    3054:	learn: 70365.0905689	test: 115220.5203976	best: 115220.5203976 (3054)	total: 17.9s	remaining: 40.6s
    3055:	learn: 70360.4298365	test: 115218.3081529	best: 115218.3081529 (3055)	total: 17.9s	remaining: 40.6s
    3056:	learn: 70352.2741651	test: 115217.7465513	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3057:	learn: 70344.9838225	test: 115219.4198202	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3058:	learn: 70339.6398388	test: 115223.8882898	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3059:	learn: 70330.7646647	test: 115227.8180921	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3060:	learn: 70324.3597693	test: 115227.1795337	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3061:	learn: 70314.0344064	test: 115221.7169893	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3062:	learn: 70309.4137623	test: 115221.4770282	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3063:	learn: 70298.7025469	test: 115218.7352919	best: 115217.7465513 (3056)	total: 17.9s	remaining: 40.6s
    3064:	learn: 70291.5404418	test: 115215.6835766	best: 115215.6835766 (3064)	total: 17.9s	remaining: 40.6s
    3065:	learn: 70286.8141702	test: 115211.4188355	best: 115211.4188355 (3065)	total: 17.9s	remaining: 40.6s
    3066:	learn: 70282.5049617	test: 115210.2313297	best: 115210.2313297 (3066)	total: 17.9s	remaining: 40.6s
    3067:	learn: 70274.8244669	test: 115215.2654484	best: 115210.2313297 (3066)	total: 18s	remaining: 40.6s
    3068:	learn: 70268.1858617	test: 115213.0209722	best: 115210.2313297 (3066)	total: 18s	remaining: 40.6s
    3069:	learn: 70261.5914209	test: 115213.8136240	best: 115210.2313297 (3066)	total: 18s	remaining: 40.6s
    3070:	learn: 70255.0817615	test: 115216.8462783	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3071:	learn: 70249.8364311	test: 115220.0739251	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3072:	learn: 70246.4108453	test: 115222.6915967	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3073:	learn: 70240.4249676	test: 115220.1686631	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3074:	learn: 70236.6058047	test: 115223.4663284	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3075:	learn: 70229.7144775	test: 115220.2137935	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3076:	learn: 70224.2755413	test: 115219.4660392	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3077:	learn: 70217.0627092	test: 115217.7819571	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3078:	learn: 70211.9872617	test: 115222.7436590	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3079:	learn: 70197.7708259	test: 115218.6915770	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3080:	learn: 70193.2823415	test: 115218.3114255	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3081:	learn: 70188.2950313	test: 115215.6104010	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3082:	learn: 70183.2020140	test: 115218.9042843	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3083:	learn: 70178.3605885	test: 115217.6863075	best: 115210.2313297 (3066)	total: 18s	remaining: 40.5s
    3084:	learn: 70170.4953250	test: 115216.9396818	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.5s
    3085:	learn: 70162.9805620	test: 115213.6364173	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.5s
    3086:	learn: 70154.6273600	test: 115212.0089307	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.5s
    3087:	learn: 70150.9318450	test: 115211.2672669	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.5s
    3088:	learn: 70147.7347567	test: 115216.0570665	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.4s
    3089:	learn: 70140.0114354	test: 115212.3467742	best: 115210.2313297 (3066)	total: 18.1s	remaining: 40.4s
    3090:	learn: 70128.0967550	test: 115205.0336042	best: 115205.0336042 (3090)	total: 18.1s	remaining: 40.4s
    3091:	learn: 70118.2056109	test: 115189.4124006	best: 115189.4124006 (3091)	total: 18.1s	remaining: 40.4s
    3092:	learn: 70111.3613005	test: 115188.7931531	best: 115188.7931531 (3092)	total: 18.1s	remaining: 40.4s
    3093:	learn: 70102.7448704	test: 115186.7530634	best: 115186.7530634 (3093)	total: 18.1s	remaining: 40.4s
    3094:	learn: 70098.6471377	test: 115184.2648025	best: 115184.2648025 (3094)	total: 18.1s	remaining: 40.4s
    3095:	learn: 70091.6613275	test: 115182.8405927	best: 115182.8405927 (3095)	total: 18.1s	remaining: 40.4s
    3096:	learn: 70086.4933436	test: 115182.9343793	best: 115182.8405927 (3095)	total: 18.1s	remaining: 40.4s
    3097:	learn: 70076.5530349	test: 115177.7061597	best: 115177.7061597 (3097)	total: 18.1s	remaining: 40.4s
    3098:	learn: 70069.2477630	test: 115175.5694349	best: 115175.5694349 (3098)	total: 18.1s	remaining: 40.4s
    3099:	learn: 70065.5936642	test: 115173.7273598	best: 115173.7273598 (3099)	total: 18.1s	remaining: 40.4s
    3100:	learn: 70059.6788958	test: 115172.5303210	best: 115172.5303210 (3100)	total: 18.1s	remaining: 40.4s
    3101:	learn: 70054.8379448	test: 115171.1539006	best: 115171.1539006 (3101)	total: 18.2s	remaining: 40.4s
    3102:	learn: 70047.8795695	test: 115170.7997687	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.4s
    3103:	learn: 70045.7345543	test: 115172.2514297	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.4s
    3104:	learn: 70038.8463422	test: 115173.5107623	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3105:	learn: 70029.7838923	test: 115174.4051100	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3106:	learn: 70025.8187807	test: 115174.9658782	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3107:	learn: 70020.6475028	test: 115175.4432923	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3108:	learn: 70014.7156405	test: 115172.3699839	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3109:	learn: 70012.8823582	test: 115174.4756131	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3110:	learn: 70007.7711254	test: 115172.6089867	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3111:	learn: 70002.8801854	test: 115171.1106418	best: 115170.7997687 (3102)	total: 18.2s	remaining: 40.3s
    3112:	learn: 69993.9620079	test: 115167.2668606	best: 115167.2668606 (3112)	total: 18.2s	remaining: 40.3s
    3113:	learn: 69992.7955783	test: 115169.5016735	best: 115167.2668606 (3112)	total: 18.2s	remaining: 40.3s
    3114:	learn: 69984.5873817	test: 115167.7003456	best: 115167.2668606 (3112)	total: 18.2s	remaining: 40.3s
    3115:	learn: 69976.9934237	test: 115167.5942045	best: 115167.2668606 (3112)	total: 18.2s	remaining: 40.3s
    3116:	learn: 69970.2122059	test: 115164.6133452	best: 115164.6133452 (3116)	total: 18.2s	remaining: 40.3s
    3117:	learn: 69965.0130222	test: 115163.1503595	best: 115163.1503595 (3117)	total: 18.3s	remaining: 40.3s
    3118:	learn: 69957.9059965	test: 115162.9608382	best: 115162.9608382 (3118)	total: 18.3s	remaining: 40.3s
    3119:	learn: 69949.9065521	test: 115159.5699264	best: 115159.5699264 (3119)	total: 18.3s	remaining: 40.3s
    3120:	learn: 69942.8323413	test: 115158.7851256	best: 115158.7851256 (3120)	total: 18.3s	remaining: 40.3s
    3121:	learn: 69938.3898222	test: 115158.6416332	best: 115158.6416332 (3121)	total: 18.3s	remaining: 40.3s
    3122:	learn: 69930.5517925	test: 115158.9522523	best: 115158.6416332 (3121)	total: 18.3s	remaining: 40.3s
    3123:	learn: 69928.8577322	test: 115155.6553934	best: 115155.6553934 (3123)	total: 18.3s	remaining: 40.3s
    3124:	learn: 69922.7253233	test: 115155.0091341	best: 115155.0091341 (3124)	total: 18.3s	remaining: 40.3s
    3125:	learn: 69916.4227713	test: 115151.5990383	best: 115151.5990383 (3125)	total: 18.3s	remaining: 40.2s
    3126:	learn: 69910.4382008	test: 115150.4524567	best: 115150.4524567 (3126)	total: 18.3s	remaining: 40.2s
    3127:	learn: 69905.4548566	test: 115150.5176249	best: 115150.4524567 (3126)	total: 18.3s	remaining: 40.2s
    3128:	learn: 69900.3922520	test: 115146.5139813	best: 115146.5139813 (3128)	total: 18.3s	remaining: 40.2s
    3129:	learn: 69893.6874337	test: 115147.3559618	best: 115146.5139813 (3128)	total: 18.3s	remaining: 40.2s
    3130:	learn: 69888.8189830	test: 115145.4172137	best: 115145.4172137 (3130)	total: 18.3s	remaining: 40.2s
    3131:	learn: 69884.1464705	test: 115144.5213490	best: 115144.5213490 (3131)	total: 18.3s	remaining: 40.2s
    3132:	learn: 69876.4114833	test: 115140.5799004	best: 115140.5799004 (3132)	total: 18.3s	remaining: 40.2s
    3133:	learn: 69867.7863114	test: 115142.9598019	best: 115140.5799004 (3132)	total: 18.3s	remaining: 40.2s
    3134:	learn: 69865.5360960	test: 115143.3824855	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3135:	learn: 69858.6481979	test: 115143.7029080	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3136:	learn: 69853.5767660	test: 115142.4373561	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3137:	learn: 69846.0310591	test: 115145.3301534	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3138:	learn: 69839.9531289	test: 115142.4088666	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3139:	learn: 69832.2859901	test: 115148.8563483	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3140:	learn: 69827.3946404	test: 115147.8062719	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3141:	learn: 69822.8038374	test: 115146.9893153	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3142:	learn: 69813.3456491	test: 115146.1293044	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3143:	learn: 69810.1580544	test: 115146.7783191	best: 115140.5799004 (3132)	total: 18.4s	remaining: 40.2s
    3144:	learn: 69800.0100617	test: 115139.7548387	best: 115139.7548387 (3144)	total: 18.4s	remaining: 40.2s
    3145:	learn: 69791.7528112	test: 115137.9302259	best: 115137.9302259 (3145)	total: 18.4s	remaining: 40.1s
    3146:	learn: 69784.7051718	test: 115136.3134647	best: 115136.3134647 (3146)	total: 18.4s	remaining: 40.1s
    3147:	learn: 69780.9290486	test: 115136.9328702	best: 115136.3134647 (3146)	total: 18.4s	remaining: 40.1s
    3148:	learn: 69776.1861405	test: 115136.8455893	best: 115136.3134647 (3146)	total: 18.4s	remaining: 40.1s
    3149:	learn: 69771.2219362	test: 115136.9861578	best: 115136.3134647 (3146)	total: 18.5s	remaining: 40.1s
    3150:	learn: 69760.4576534	test: 115134.1778704	best: 115134.1778704 (3150)	total: 18.5s	remaining: 40.1s
    3151:	learn: 69757.1354171	test: 115133.8657310	best: 115133.8657310 (3151)	total: 18.5s	remaining: 40.1s
    3152:	learn: 69753.4775384	test: 115136.9977982	best: 115133.8657310 (3151)	total: 18.5s	remaining: 40.1s
    3153:	learn: 69747.2370423	test: 115135.3897312	best: 115133.8657310 (3151)	total: 18.5s	remaining: 40.1s
    3154:	learn: 69740.8936281	test: 115127.3385792	best: 115127.3385792 (3154)	total: 18.5s	remaining: 40.1s
    3155:	learn: 69736.8280178	test: 115129.8325837	best: 115127.3385792 (3154)	total: 18.5s	remaining: 40.1s
    3156:	learn: 69732.3729047	test: 115129.4001296	best: 115127.3385792 (3154)	total: 18.5s	remaining: 40.1s
    3157:	learn: 69727.0165373	test: 115129.0192359	best: 115127.3385792 (3154)	total: 18.5s	remaining: 40.1s
    3158:	learn: 69718.5775165	test: 115124.8787999	best: 115124.8787999 (3158)	total: 18.5s	remaining: 40.1s
    3159:	learn: 69711.8031020	test: 115121.9945928	best: 115121.9945928 (3159)	total: 18.5s	remaining: 40.1s
    3160:	learn: 69705.7530685	test: 115120.9267002	best: 115120.9267002 (3160)	total: 18.5s	remaining: 40.1s
    3161:	learn: 69699.3114082	test: 115125.8261473	best: 115120.9267002 (3160)	total: 18.5s	remaining: 40.1s
    3162:	learn: 69693.1082482	test: 115123.2039537	best: 115120.9267002 (3160)	total: 18.5s	remaining: 40.1s
    3163:	learn: 69685.1836308	test: 115124.7522133	best: 115120.9267002 (3160)	total: 18.5s	remaining: 40.1s
    3164:	learn: 69681.5687449	test: 115126.5224975	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40.1s
    3165:	learn: 69671.8698228	test: 115124.1485375	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40.1s
    3166:	learn: 69668.6231752	test: 115123.1640749	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40.1s
    3167:	learn: 69665.7783709	test: 115124.7003556	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40.1s
    3168:	learn: 69661.2827709	test: 115124.0036262	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3169:	learn: 69655.5905771	test: 115127.5225513	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3170:	learn: 69654.0029756	test: 115126.5546237	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3171:	learn: 69644.8360949	test: 115129.3505435	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3172:	learn: 69637.3600712	test: 115126.4160239	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3173:	learn: 69623.6309571	test: 115131.4663189	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3174:	learn: 69618.6532969	test: 115129.8815133	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3175:	learn: 69616.3794354	test: 115130.0081753	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3176:	learn: 69606.9924989	test: 115125.2237529	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3177:	learn: 69599.6441333	test: 115130.1441342	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3178:	learn: 69591.1835954	test: 115128.7810747	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3179:	learn: 69584.1079397	test: 115130.6301661	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3180:	learn: 69576.1115116	test: 115128.6938863	best: 115120.9267002 (3160)	total: 18.6s	remaining: 40s
    3181:	learn: 69567.6153100	test: 115125.0639875	best: 115120.9267002 (3160)	total: 18.7s	remaining: 40s
    3182:	learn: 69560.7871708	test: 115124.1079388	best: 115120.9267002 (3160)	total: 18.7s	remaining: 40s
    3183:	learn: 69550.6701844	test: 115125.0984914	best: 115120.9267002 (3160)	total: 18.7s	remaining: 40s
    3184:	learn: 69540.5742355	test: 115123.9387227	best: 115120.9267002 (3160)	total: 18.7s	remaining: 40s
    3185:	learn: 69535.3381240	test: 115124.7679467	best: 115120.9267002 (3160)	total: 18.7s	remaining: 39.9s
    3186:	learn: 69530.5174618	test: 115123.2563687	best: 115120.9267002 (3160)	total: 18.7s	remaining: 39.9s
    3187:	learn: 69525.3922346	test: 115122.8012690	best: 115120.9267002 (3160)	total: 18.7s	remaining: 39.9s
    3188:	learn: 69512.5800956	test: 115115.2941097	best: 115115.2941097 (3188)	total: 18.7s	remaining: 39.9s
    3189:	learn: 69508.7244168	test: 115112.8765478	best: 115112.8765478 (3189)	total: 18.7s	remaining: 39.9s
    3190:	learn: 69503.7029844	test: 115109.2738786	best: 115109.2738786 (3190)	total: 18.7s	remaining: 39.9s
    3191:	learn: 69500.3891355	test: 115105.7198919	best: 115105.7198919 (3191)	total: 18.7s	remaining: 39.9s
    3192:	learn: 69494.0197095	test: 115110.9333603	best: 115105.7198919 (3191)	total: 18.7s	remaining: 39.9s
    3193:	learn: 69489.9394216	test: 115111.7129971	best: 115105.7198919 (3191)	total: 18.7s	remaining: 39.9s
    3194:	learn: 69482.6261917	test: 115110.8913413	best: 115105.7198919 (3191)	total: 18.7s	remaining: 39.9s
    3195:	learn: 69474.6279245	test: 115105.5876831	best: 115105.5876831 (3195)	total: 18.7s	remaining: 39.9s
    3196:	learn: 69467.3722739	test: 115104.2378451	best: 115104.2378451 (3196)	total: 18.7s	remaining: 39.9s
    3197:	learn: 69460.2143061	test: 115107.0838410	best: 115104.2378451 (3196)	total: 18.8s	remaining: 39.9s
    3198:	learn: 69456.5385272	test: 115109.2922563	best: 115104.2378451 (3196)	total: 18.8s	remaining: 39.9s
    3199:	learn: 69453.0156024	test: 115112.1713561	best: 115104.2378451 (3196)	total: 18.8s	remaining: 39.9s
    3200:	learn: 69447.1551930	test: 115110.1045243	best: 115104.2378451 (3196)	total: 18.8s	remaining: 39.9s
    3201:	learn: 69441.0372866	test: 115100.5857312	best: 115100.5857312 (3201)	total: 18.8s	remaining: 39.9s
    3202:	learn: 69435.8581840	test: 115099.0404806	best: 115099.0404806 (3202)	total: 18.8s	remaining: 39.9s
    3203:	learn: 69424.3227157	test: 115091.3794011	best: 115091.3794011 (3203)	total: 18.8s	remaining: 39.8s
    3204:	learn: 69417.1267970	test: 115082.5745887	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3205:	learn: 69413.0122795	test: 115083.3458732	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3206:	learn: 69403.1624196	test: 115083.6030107	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3207:	learn: 69400.5623690	test: 115087.2379853	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3208:	learn: 69395.4158016	test: 115084.3769505	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3209:	learn: 69389.6769494	test: 115086.7876825	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3210:	learn: 69387.5508736	test: 115086.6281635	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3211:	learn: 69381.5328013	test: 115085.7336414	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3212:	learn: 69374.6981028	test: 115084.2011071	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3213:	learn: 69366.4335060	test: 115083.3453874	best: 115082.5745887 (3204)	total: 18.8s	remaining: 39.8s
    3214:	learn: 69360.3081505	test: 115080.2872244	best: 115080.2872244 (3214)	total: 18.8s	remaining: 39.8s
    3215:	learn: 69354.2066595	test: 115081.6865358	best: 115080.2872244 (3214)	total: 18.9s	remaining: 39.8s
    3216:	learn: 69347.1513764	test: 115082.3927560	best: 115080.2872244 (3214)	total: 18.9s	remaining: 39.8s
    3217:	learn: 69342.4485378	test: 115079.9058809	best: 115079.9058809 (3217)	total: 18.9s	remaining: 39.8s
    3218:	learn: 69336.7679395	test: 115078.6124528	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.8s
    3219:	learn: 69332.2762284	test: 115080.1775832	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3220:	learn: 69325.7312892	test: 115082.7544691	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3221:	learn: 69323.2400072	test: 115084.7553510	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3222:	learn: 69318.0436294	test: 115087.9175579	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3223:	learn: 69314.0282828	test: 115087.4832930	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3224:	learn: 69307.5548485	test: 115087.3673133	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3225:	learn: 69304.5623224	test: 115087.8215008	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3226:	learn: 69297.0302497	test: 115086.2790285	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3227:	learn: 69291.4042406	test: 115084.2162696	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3228:	learn: 69286.8904353	test: 115082.4625251	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3229:	learn: 69284.2878193	test: 115082.3776670	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3230:	learn: 69279.2349692	test: 115082.1894814	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3231:	learn: 69270.6331289	test: 115079.0740691	best: 115078.6124528 (3218)	total: 18.9s	remaining: 39.7s
    3232:	learn: 69262.5642748	test: 115067.7114248	best: 115067.7114248 (3232)	total: 19s	remaining: 39.7s
    3233:	learn: 69256.6045030	test: 115068.4846087	best: 115067.7114248 (3232)	total: 19s	remaining: 39.7s
    3234:	learn: 69249.4352767	test: 115070.3826059	best: 115067.7114248 (3232)	total: 19s	remaining: 39.7s
    3235:	learn: 69243.5523372	test: 115067.0909414	best: 115067.0909414 (3235)	total: 19s	remaining: 39.7s
    3236:	learn: 69243.0000074	test: 115066.6194025	best: 115066.6194025 (3236)	total: 19s	remaining: 39.6s
    3237:	learn: 69235.0829562	test: 115072.9927514	best: 115066.6194025 (3236)	total: 19s	remaining: 39.6s
    3238:	learn: 69227.9115135	test: 115068.1954483	best: 115066.6194025 (3236)	total: 19s	remaining: 39.6s
    3239:	learn: 69225.0031149	test: 115067.8780512	best: 115066.6194025 (3236)	total: 19s	remaining: 39.6s
    3240:	learn: 69218.1864278	test: 115065.8799777	best: 115065.8799777 (3240)	total: 19s	remaining: 39.6s
    3241:	learn: 69210.4066520	test: 115068.5098777	best: 115065.8799777 (3240)	total: 19s	remaining: 39.6s
    3242:	learn: 69205.6456428	test: 115066.8184993	best: 115065.8799777 (3240)	total: 19s	remaining: 39.6s
    3243:	learn: 69199.4290317	test: 115060.6740099	best: 115060.6740099 (3243)	total: 19s	remaining: 39.6s
    3244:	learn: 69192.8674065	test: 115063.9728262	best: 115060.6740099 (3243)	total: 19s	remaining: 39.6s
    3245:	learn: 69184.7275980	test: 115059.5116579	best: 115059.5116579 (3245)	total: 19s	remaining: 39.6s
    3246:	learn: 69175.1794608	test: 115057.5527686	best: 115057.5527686 (3246)	total: 19s	remaining: 39.6s
    3247:	learn: 69165.7597426	test: 115055.7173231	best: 115055.7173231 (3247)	total: 19s	remaining: 39.6s
    3248:	learn: 69161.8026142	test: 115056.4649266	best: 115055.7173231 (3247)	total: 19s	remaining: 39.6s
    3249:	learn: 69153.0582148	test: 115058.7717809	best: 115055.7173231 (3247)	total: 19.1s	remaining: 39.6s
    3250:	learn: 69143.5137740	test: 115056.8564618	best: 115055.7173231 (3247)	total: 19.1s	remaining: 39.6s
    3251:	learn: 69132.0486173	test: 115051.1548754	best: 115051.1548754 (3251)	total: 19.1s	remaining: 39.6s
    3252:	learn: 69130.4275004	test: 115050.9424721	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3253:	learn: 69123.5414746	test: 115051.2512030	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3254:	learn: 69118.7898853	test: 115052.9987465	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3255:	learn: 69115.1755498	test: 115051.9785965	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3256:	learn: 69103.8033421	test: 115054.0698485	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3257:	learn: 69099.9919089	test: 115051.9317412	best: 115050.9424721 (3252)	total: 19.1s	remaining: 39.5s
    3258:	learn: 69089.8141403	test: 115049.3355581	best: 115049.3355581 (3258)	total: 19.1s	remaining: 39.5s
    3259:	learn: 69086.2943651	test: 115050.7058147	best: 115049.3355581 (3258)	total: 19.1s	remaining: 39.5s
    3260:	learn: 69078.4166574	test: 115048.5729732	best: 115048.5729732 (3260)	total: 19.1s	remaining: 39.5s
    3261:	learn: 69073.7721161	test: 115046.7980003	best: 115046.7980003 (3261)	total: 19.1s	remaining: 39.5s
    3262:	learn: 69069.4893324	test: 115045.7773212	best: 115045.7773212 (3262)	total: 19.1s	remaining: 39.5s
    3263:	learn: 69062.1208777	test: 115044.3931505	best: 115044.3931505 (3263)	total: 19.1s	remaining: 39.5s
    3264:	learn: 69059.4556418	test: 115043.6488403	best: 115043.6488403 (3264)	total: 19.1s	remaining: 39.5s
    3265:	learn: 69050.3820383	test: 115042.1166638	best: 115042.1166638 (3265)	total: 19.1s	remaining: 39.5s
    3266:	learn: 69044.1790514	test: 115041.1628095	best: 115041.1628095 (3266)	total: 19.2s	remaining: 39.5s
    3267:	learn: 69039.3822939	test: 115039.1158397	best: 115039.1158397 (3267)	total: 19.2s	remaining: 39.5s
    3268:	learn: 69035.0038352	test: 115037.5975356	best: 115037.5975356 (3268)	total: 19.2s	remaining: 39.5s
    3269:	learn: 69031.5458672	test: 115035.0817930	best: 115035.0817930 (3269)	total: 19.2s	remaining: 39.5s
    3270:	learn: 69025.0334940	test: 115035.0312848	best: 115035.0312848 (3270)	total: 19.2s	remaining: 39.5s
    3271:	learn: 69015.6898507	test: 115029.0582217	best: 115029.0582217 (3271)	total: 19.2s	remaining: 39.4s
    3272:	learn: 69007.4921805	test: 115027.7262178	best: 115027.7262178 (3272)	total: 19.2s	remaining: 39.4s
    3273:	learn: 69003.1864833	test: 115027.3400137	best: 115027.3400137 (3273)	total: 19.2s	remaining: 39.4s
    3274:	learn: 68995.8513867	test: 115028.9168255	best: 115027.3400137 (3273)	total: 19.2s	remaining: 39.4s
    3275:	learn: 68991.7831084	test: 115027.7646828	best: 115027.3400137 (3273)	total: 19.2s	remaining: 39.4s
    3276:	learn: 68990.4814744	test: 115026.5875458	best: 115026.5875458 (3276)	total: 19.2s	remaining: 39.4s
    3277:	learn: 68982.2764398	test: 115025.0386463	best: 115025.0386463 (3277)	total: 19.2s	remaining: 39.4s
    3278:	learn: 68976.5108496	test: 115023.9328153	best: 115023.9328153 (3278)	total: 19.2s	remaining: 39.4s
    3279:	learn: 68971.4954538	test: 115023.9007620	best: 115023.9007620 (3279)	total: 19.2s	remaining: 39.4s
    3280:	learn: 68969.7652212	test: 115021.7719397	best: 115021.7719397 (3280)	total: 19.2s	remaining: 39.4s
    3281:	learn: 68965.2110322	test: 115021.1525557	best: 115021.1525557 (3281)	total: 19.2s	remaining: 39.4s
    3282:	learn: 68961.8700396	test: 115018.3362003	best: 115018.3362003 (3282)	total: 19.3s	remaining: 39.4s
    3283:	learn: 68955.2251497	test: 115019.0714452	best: 115018.3362003 (3282)	total: 19.3s	remaining: 39.4s
    3284:	learn: 68949.5919961	test: 115018.7772877	best: 115018.3362003 (3282)	total: 19.3s	remaining: 39.4s
    3285:	learn: 68943.8626453	test: 115016.4340158	best: 115016.4340158 (3285)	total: 19.3s	remaining: 39.4s
    3286:	learn: 68934.2317190	test: 115012.0769441	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3287:	learn: 68931.7444420	test: 115022.6641702	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3288:	learn: 68925.9235742	test: 115020.5793846	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3289:	learn: 68919.3879047	test: 115018.2962022	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3290:	learn: 68914.1251959	test: 115014.2637310	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3291:	learn: 68910.5586276	test: 115015.0110089	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.4s
    3292:	learn: 68905.4200080	test: 115016.2520395	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.3s
    3293:	learn: 68900.8563514	test: 115014.2344162	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.3s
    3294:	learn: 68898.1007831	test: 115013.7937857	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.3s
    3295:	learn: 68891.0722639	test: 115015.9448061	best: 115012.0769441 (3286)	total: 19.3s	remaining: 39.3s
    3296:	learn: 68878.2675161	test: 115008.9209772	best: 115008.9209772 (3296)	total: 19.3s	remaining: 39.3s
    3297:	learn: 68870.6105471	test: 115007.8355887	best: 115007.8355887 (3297)	total: 19.3s	remaining: 39.3s
    3298:	learn: 68866.0246082	test: 115007.9272404	best: 115007.8355887 (3297)	total: 19.4s	remaining: 39.3s
    3299:	learn: 68856.5665173	test: 115001.2971293	best: 115001.2971293 (3299)	total: 19.4s	remaining: 39.3s
    3300:	learn: 68851.8167714	test: 115002.5275949	best: 115001.2971293 (3299)	total: 19.4s	remaining: 39.3s
    3301:	learn: 68846.8561784	test: 115000.9253614	best: 115000.9253614 (3301)	total: 19.4s	remaining: 39.3s
    3302:	learn: 68838.5990208	test: 114999.3708460	best: 114999.3708460 (3302)	total: 19.4s	remaining: 39.3s
    3303:	learn: 68831.8679167	test: 114998.0810798	best: 114998.0810798 (3303)	total: 19.4s	remaining: 39.3s
    3304:	learn: 68826.5262666	test: 114997.5765639	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3305:	learn: 68823.4127053	test: 114998.9427110	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3306:	learn: 68819.8709206	test: 114998.7412705	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3307:	learn: 68817.7701753	test: 114998.8486706	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3308:	learn: 68813.4515643	test: 115000.4334605	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3309:	learn: 68807.3020052	test: 115001.2138078	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3310:	learn: 68804.1907197	test: 115000.1074578	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3311:	learn: 68793.9105851	test: 115000.4654409	best: 114997.5765639 (3304)	total: 19.4s	remaining: 39.3s
    3312:	learn: 68787.5924656	test: 114996.1901327	best: 114996.1901327 (3312)	total: 19.4s	remaining: 39.2s
    3313:	learn: 68782.3714417	test: 114996.4531309	best: 114996.1901327 (3312)	total: 19.5s	remaining: 39.2s
    3314:	learn: 68773.4687466	test: 114994.5391345	best: 114994.5391345 (3314)	total: 19.5s	remaining: 39.2s
    3315:	learn: 68767.2926255	test: 114995.2835753	best: 114994.5391345 (3314)	total: 19.5s	remaining: 39.2s
    3316:	learn: 68762.7773499	test: 114995.0053623	best: 114994.5391345 (3314)	total: 19.5s	remaining: 39.2s
    3317:	learn: 68753.2146025	test: 114993.2043637	best: 114993.2043637 (3317)	total: 19.5s	remaining: 39.2s
    3318:	learn: 68746.7375543	test: 114989.3049006	best: 114989.3049006 (3318)	total: 19.5s	remaining: 39.2s
    3319:	learn: 68741.9316688	test: 114987.0403529	best: 114987.0403529 (3319)	total: 19.5s	remaining: 39.2s
    3320:	learn: 68734.3936638	test: 114987.7394656	best: 114987.0403529 (3319)	total: 19.5s	remaining: 39.2s
    3321:	learn: 68729.8900379	test: 114985.8689546	best: 114985.8689546 (3321)	total: 19.5s	remaining: 39.2s
    3322:	learn: 68723.4549255	test: 114980.7834433	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3323:	learn: 68716.3362729	test: 114986.9966930	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3324:	learn: 68706.5966730	test: 114989.2802291	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3325:	learn: 68697.6678357	test: 114984.5674105	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3326:	learn: 68693.4321511	test: 114985.7912164	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3327:	learn: 68689.3019984	test: 114985.0604304	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3328:	learn: 68686.4319190	test: 114985.0609638	best: 114980.7834433 (3322)	total: 19.5s	remaining: 39.2s
    3329:	learn: 68679.6112967	test: 114983.0985744	best: 114980.7834433 (3322)	total: 19.6s	remaining: 39.2s
    3330:	learn: 68673.5766561	test: 114976.1888548	best: 114976.1888548 (3330)	total: 19.6s	remaining: 39.2s
    3331:	learn: 68664.9516453	test: 114975.9914418	best: 114975.9914418 (3331)	total: 19.6s	remaining: 39.2s
    3332:	learn: 68658.5111055	test: 114974.2060904	best: 114974.2060904 (3332)	total: 19.6s	remaining: 39.2s
    3333:	learn: 68655.1772931	test: 114974.3831580	best: 114974.2060904 (3332)	total: 19.6s	remaining: 39.1s
    3334:	learn: 68648.5689470	test: 114973.6750087	best: 114973.6750087 (3334)	total: 19.6s	remaining: 39.1s
    3335:	learn: 68646.1731579	test: 114976.3955105	best: 114973.6750087 (3334)	total: 19.6s	remaining: 39.1s
    3336:	learn: 68633.8120613	test: 114969.6412025	best: 114969.6412025 (3336)	total: 19.6s	remaining: 39.1s
    3337:	learn: 68627.2702210	test: 114959.8002905	best: 114959.8002905 (3337)	total: 19.6s	remaining: 39.1s
    3338:	learn: 68624.0338529	test: 114960.0298135	best: 114959.8002905 (3337)	total: 19.6s	remaining: 39.1s
    3339:	learn: 68615.8787692	test: 114953.8322041	best: 114953.8322041 (3339)	total: 19.6s	remaining: 39.1s
    3340:	learn: 68609.8234710	test: 114953.5482744	best: 114953.5482744 (3340)	total: 19.6s	remaining: 39.1s
    3341:	learn: 68605.2698986	test: 114954.5756401	best: 114953.5482744 (3340)	total: 19.6s	remaining: 39.1s
    3342:	learn: 68597.5260753	test: 114954.6987887	best: 114953.5482744 (3340)	total: 19.6s	remaining: 39.1s
    3343:	learn: 68592.6814282	test: 114955.6476963	best: 114953.5482744 (3340)	total: 19.6s	remaining: 39.1s
    3344:	learn: 68588.7621030	test: 114953.7974959	best: 114953.5482744 (3340)	total: 19.7s	remaining: 39.1s
    3345:	learn: 68586.9328199	test: 114954.4791981	best: 114953.5482744 (3340)	total: 19.7s	remaining: 39.1s
    3346:	learn: 68580.8790256	test: 114952.4266736	best: 114952.4266736 (3346)	total: 19.7s	remaining: 39.1s
    3347:	learn: 68572.1633283	test: 114950.0359423	best: 114950.0359423 (3347)	total: 19.7s	remaining: 39.1s
    3348:	learn: 68567.5633055	test: 114950.3562232	best: 114950.0359423 (3347)	total: 19.7s	remaining: 39.1s
    3349:	learn: 68561.7838873	test: 114949.8851402	best: 114949.8851402 (3349)	total: 19.7s	remaining: 39.1s
    3350:	learn: 68556.2446678	test: 114951.7827659	best: 114949.8851402 (3349)	total: 19.7s	remaining: 39.1s
    3351:	learn: 68549.6943121	test: 114950.8910088	best: 114949.8851402 (3349)	total: 19.7s	remaining: 39.1s
    3352:	learn: 68543.3592891	test: 114950.0128174	best: 114949.8851402 (3349)	total: 19.7s	remaining: 39.1s
    3353:	learn: 68538.1338340	test: 114950.4205332	best: 114949.8851402 (3349)	total: 19.7s	remaining: 39.1s
    3354:	learn: 68534.2751094	test: 114949.3488559	best: 114949.3488559 (3354)	total: 19.7s	remaining: 39s
    3355:	learn: 68530.0194736	test: 114948.4537561	best: 114948.4537561 (3355)	total: 19.7s	remaining: 39s
    3356:	learn: 68524.3780737	test: 114947.5678807	best: 114947.5678807 (3356)	total: 19.7s	remaining: 39s
    3357:	learn: 68516.9827118	test: 114945.0050247	best: 114945.0050247 (3357)	total: 19.7s	remaining: 39s
    3358:	learn: 68510.8309110	test: 114947.9050161	best: 114945.0050247 (3357)	total: 19.7s	remaining: 39s
    3359:	learn: 68503.9021603	test: 114948.2347485	best: 114945.0050247 (3357)	total: 19.7s	remaining: 39s
    3360:	learn: 68498.2184374	test: 114945.7973894	best: 114945.0050247 (3357)	total: 19.7s	remaining: 39s
    3361:	learn: 68494.9967136	test: 114943.3491453	best: 114943.3491453 (3361)	total: 19.8s	remaining: 39s
    3362:	learn: 68492.2703412	test: 114943.5064783	best: 114943.3491453 (3361)	total: 19.8s	remaining: 39s
    3363:	learn: 68489.1781686	test: 114945.5769575	best: 114943.3491453 (3361)	total: 19.8s	remaining: 39s
    3364:	learn: 68483.9435970	test: 114943.9880890	best: 114943.3491453 (3361)	total: 19.8s	remaining: 39s
    3365:	learn: 68479.8054886	test: 114943.8033305	best: 114943.3491453 (3361)	total: 19.8s	remaining: 39s
    3366:	learn: 68474.6873514	test: 114942.2768559	best: 114942.2768559 (3366)	total: 19.8s	remaining: 39s
    3367:	learn: 68469.1494260	test: 114942.2253564	best: 114942.2253564 (3367)	total: 19.8s	remaining: 39s
    3368:	learn: 68465.3959347	test: 114944.4450643	best: 114942.2253564 (3367)	total: 19.8s	remaining: 39s
    3369:	learn: 68463.1971783	test: 114946.1563913	best: 114942.2253564 (3367)	total: 19.8s	remaining: 39s
    3370:	learn: 68456.4224298	test: 114945.1461658	best: 114942.2253564 (3367)	total: 19.8s	remaining: 39s
    3371:	learn: 68449.3543345	test: 114943.3719702	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3372:	learn: 68441.4124757	test: 114943.3795403	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3373:	learn: 68438.9908532	test: 114949.8740929	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3374:	learn: 68434.3923949	test: 114947.6921066	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3375:	learn: 68426.8717073	test: 114942.3818135	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3376:	learn: 68420.8419119	test: 114945.5289307	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3377:	learn: 68414.3489217	test: 114944.0458443	best: 114942.2253564 (3367)	total: 19.8s	remaining: 38.9s
    3378:	learn: 68408.2193104	test: 114942.9030970	best: 114942.2253564 (3367)	total: 19.9s	remaining: 38.9s
    3379:	learn: 68402.8428581	test: 114943.5035401	best: 114942.2253564 (3367)	total: 19.9s	remaining: 38.9s
    3380:	learn: 68393.9302261	test: 114944.6891996	best: 114942.2253564 (3367)	total: 19.9s	remaining: 38.9s
    3381:	learn: 68390.2581408	test: 114942.5261612	best: 114942.2253564 (3367)	total: 19.9s	remaining: 38.9s
    3382:	learn: 68384.2993375	test: 114940.2949280	best: 114940.2949280 (3382)	total: 19.9s	remaining: 38.9s
    3383:	learn: 68378.4284594	test: 114938.7889599	best: 114938.7889599 (3383)	total: 19.9s	remaining: 38.9s
    3384:	learn: 68373.7790261	test: 114934.7426535	best: 114934.7426535 (3384)	total: 19.9s	remaining: 38.9s
    3385:	learn: 68362.7563842	test: 114927.5223081	best: 114927.5223081 (3385)	total: 19.9s	remaining: 38.9s
    3386:	learn: 68359.6970393	test: 114927.6243120	best: 114927.5223081 (3385)	total: 19.9s	remaining: 38.9s
    3387:	learn: 68355.8496878	test: 114926.1719470	best: 114926.1719470 (3387)	total: 19.9s	remaining: 38.9s
    3388:	learn: 68350.4881060	test: 114926.5741506	best: 114926.1719470 (3387)	total: 19.9s	remaining: 38.8s
    3389:	learn: 68345.2428864	test: 114925.5213393	best: 114925.5213393 (3389)	total: 19.9s	remaining: 38.8s
    3390:	learn: 68341.3680530	test: 114925.3787323	best: 114925.3787323 (3390)	total: 19.9s	remaining: 38.8s
    3391:	learn: 68334.3561784	test: 114925.3907687	best: 114925.3787323 (3390)	total: 19.9s	remaining: 38.8s
    3392:	learn: 68331.3351970	test: 114925.0738309	best: 114925.0738309 (3392)	total: 19.9s	remaining: 38.8s
    3393:	learn: 68325.4456625	test: 114922.7627061	best: 114922.7627061 (3393)	total: 19.9s	remaining: 38.8s
    3394:	learn: 68318.2128361	test: 114925.2941537	best: 114922.7627061 (3393)	total: 19.9s	remaining: 38.8s
    3395:	learn: 68312.1829773	test: 114923.3535161	best: 114922.7627061 (3393)	total: 20s	remaining: 38.8s
    3396:	learn: 68310.2018576	test: 114923.2376950	best: 114922.7627061 (3393)	total: 20s	remaining: 38.8s
    3397:	learn: 68301.6946557	test: 114926.4523484	best: 114922.7627061 (3393)	total: 20s	remaining: 38.8s
    3398:	learn: 68294.6750241	test: 114924.6290304	best: 114922.7627061 (3393)	total: 20s	remaining: 38.8s
    3399:	learn: 68281.2653748	test: 114921.3413851	best: 114921.3413851 (3399)	total: 20s	remaining: 38.8s
    3400:	learn: 68279.4618170	test: 114921.0345518	best: 114921.0345518 (3400)	total: 20s	remaining: 38.8s
    3401:	learn: 68275.4350515	test: 114922.4143321	best: 114921.0345518 (3400)	total: 20s	remaining: 38.8s
    3402:	learn: 68271.2103272	test: 114921.2770993	best: 114921.0345518 (3400)	total: 20s	remaining: 38.8s
    3403:	learn: 68263.0123850	test: 114920.0507839	best: 114920.0507839 (3403)	total: 20s	remaining: 38.8s
    3404:	learn: 68258.4067629	test: 114924.9716071	best: 114920.0507839 (3403)	total: 20s	remaining: 38.8s
    3405:	learn: 68255.8292228	test: 114925.2812945	best: 114920.0507839 (3403)	total: 20s	remaining: 38.7s
    3406:	learn: 68252.3475498	test: 114924.6074982	best: 114920.0507839 (3403)	total: 20s	remaining: 38.7s
    3407:	learn: 68245.0628131	test: 114919.4647218	best: 114919.4647218 (3407)	total: 20s	remaining: 38.7s
    3408:	learn: 68239.0458874	test: 114916.3928145	best: 114916.3928145 (3408)	total: 20s	remaining: 38.7s
    3409:	learn: 68234.9938619	test: 114915.6125871	best: 114915.6125871 (3409)	total: 20s	remaining: 38.7s
    3410:	learn: 68228.6011607	test: 114912.5417354	best: 114912.5417354 (3410)	total: 20s	remaining: 38.7s
    3411:	learn: 68222.0418627	test: 114907.3380483	best: 114907.3380483 (3411)	total: 20s	remaining: 38.7s
    3412:	learn: 68218.9082985	test: 114907.1525290	best: 114907.1525290 (3412)	total: 20.1s	remaining: 38.7s
    3413:	learn: 68212.0589701	test: 114905.0905026	best: 114905.0905026 (3413)	total: 20.1s	remaining: 38.7s
    3414:	learn: 68205.7965194	test: 114900.1117408	best: 114900.1117408 (3414)	total: 20.1s	remaining: 38.7s
    3415:	learn: 68198.8210323	test: 114896.5915089	best: 114896.5915089 (3415)	total: 20.1s	remaining: 38.7s
    3416:	learn: 68195.0467051	test: 114895.3017888	best: 114895.3017888 (3416)	total: 20.1s	remaining: 38.7s
    3417:	learn: 68192.3770856	test: 114899.9471199	best: 114895.3017888 (3416)	total: 20.1s	remaining: 38.7s
    3418:	learn: 68186.8618024	test: 114894.1841396	best: 114894.1841396 (3418)	total: 20.1s	remaining: 38.7s
    3419:	learn: 68182.9739322	test: 114893.4661038	best: 114893.4661038 (3419)	total: 20.1s	remaining: 38.7s
    3420:	learn: 68181.2384462	test: 114893.1893456	best: 114893.1893456 (3420)	total: 20.1s	remaining: 38.7s
    3421:	learn: 68174.6964797	test: 114890.3318156	best: 114890.3318156 (3421)	total: 20.1s	remaining: 38.6s
    3422:	learn: 68169.6536438	test: 114886.5900959	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3423:	learn: 68160.3493603	test: 114890.9173371	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3424:	learn: 68155.9476997	test: 114892.5946698	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3425:	learn: 68151.9323909	test: 114891.5415746	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3426:	learn: 68148.8054857	test: 114892.0377784	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3427:	learn: 68142.4392497	test: 114889.9182227	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3428:	learn: 68138.0667255	test: 114890.2214119	best: 114886.5900959 (3422)	total: 20.1s	remaining: 38.6s
    3429:	learn: 68130.2769258	test: 114890.2859566	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3430:	learn: 68127.6104319	test: 114891.6553577	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3431:	learn: 68120.7682940	test: 114894.1244594	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3432:	learn: 68114.2949096	test: 114897.6990727	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3433:	learn: 68104.8169581	test: 114896.0120315	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3434:	learn: 68101.0402930	test: 114897.3937308	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3435:	learn: 68091.8454235	test: 114895.8225763	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3436:	learn: 68082.2217264	test: 114895.1022541	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3437:	learn: 68077.9768008	test: 114895.8588064	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3438:	learn: 68070.4917472	test: 114891.7091971	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3439:	learn: 68064.4851059	test: 114889.3468130	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3440:	learn: 68057.8682776	test: 114888.8828560	best: 114886.5900959 (3422)	total: 20.2s	remaining: 38.6s
    3441:	learn: 68050.4961150	test: 114886.1900518	best: 114886.1900518 (3441)	total: 20.2s	remaining: 38.5s
    3442:	learn: 68044.9059531	test: 114880.0455201	best: 114880.0455201 (3442)	total: 20.2s	remaining: 38.5s
    3443:	learn: 68040.8612804	test: 114881.3069565	best: 114880.0455201 (3442)	total: 20.2s	remaining: 38.5s
    3444:	learn: 68034.5407373	test: 114885.7572837	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3445:	learn: 68029.6605656	test: 114884.0164056	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3446:	learn: 68029.1825102	test: 114881.9177143	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3447:	learn: 68022.0192740	test: 114887.8680150	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3448:	learn: 68013.1373627	test: 114881.5048638	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3449:	learn: 68007.6008778	test: 114881.5292466	best: 114880.0455201 (3442)	total: 20.3s	remaining: 38.5s
    3450:	learn: 68002.0214733	test: 114876.8825779	best: 114876.8825779 (3450)	total: 20.3s	remaining: 38.5s
    3451:	learn: 67994.0250435	test: 114875.3094921	best: 114875.3094921 (3451)	total: 20.3s	remaining: 38.5s
    3452:	learn: 67987.9413974	test: 114874.9409723	best: 114874.9409723 (3452)	total: 20.3s	remaining: 38.5s
    3453:	learn: 67983.2439820	test: 114873.2838819	best: 114873.2838819 (3453)	total: 20.3s	remaining: 38.5s
    3454:	learn: 67974.2644919	test: 114872.6088561	best: 114872.6088561 (3454)	total: 20.3s	remaining: 38.5s
    3455:	learn: 67967.2244232	test: 114872.9741507	best: 114872.6088561 (3454)	total: 20.3s	remaining: 38.5s
    3456:	learn: 67956.7881466	test: 114867.8951376	best: 114867.8951376 (3456)	total: 20.3s	remaining: 38.5s
    3457:	learn: 67951.0275841	test: 114865.7564528	best: 114865.7564528 (3457)	total: 20.3s	remaining: 38.5s
    3458:	learn: 67945.2144560	test: 114864.7670312	best: 114864.7670312 (3458)	total: 20.3s	remaining: 38.5s
    3459:	learn: 67940.6606468	test: 114866.1877012	best: 114864.7670312 (3458)	total: 20.3s	remaining: 38.5s
    3460:	learn: 67936.1921329	test: 114864.1769813	best: 114864.1769813 (3460)	total: 20.4s	remaining: 38.5s
    3461:	learn: 67928.6249305	test: 114861.7196981	best: 114861.7196981 (3461)	total: 20.4s	remaining: 38.4s
    3462:	learn: 67919.0140321	test: 114857.9433274	best: 114857.9433274 (3462)	total: 20.4s	remaining: 38.4s
    3463:	learn: 67913.2001288	test: 114855.4743120	best: 114855.4743120 (3463)	total: 20.4s	remaining: 38.4s
    3464:	learn: 67906.7101676	test: 114846.9500517	best: 114846.9500517 (3464)	total: 20.4s	remaining: 38.4s
    3465:	learn: 67904.5223982	test: 114848.7141301	best: 114846.9500517 (3464)	total: 20.4s	remaining: 38.4s
    3466:	learn: 67898.2023201	test: 114847.2777897	best: 114846.9500517 (3464)	total: 20.4s	remaining: 38.4s
    3467:	learn: 67895.5411199	test: 114847.6313628	best: 114846.9500517 (3464)	total: 20.4s	remaining: 38.4s
    3468:	learn: 67890.5506125	test: 114845.8559610	best: 114845.8559610 (3468)	total: 20.4s	remaining: 38.4s
    3469:	learn: 67880.7832222	test: 114841.5189994	best: 114841.5189994 (3469)	total: 20.4s	remaining: 38.4s
    3470:	learn: 67875.9353008	test: 114841.0279594	best: 114841.0279594 (3470)	total: 20.4s	remaining: 38.4s
    3471:	learn: 67866.4103529	test: 114847.1567322	best: 114841.0279594 (3470)	total: 20.4s	remaining: 38.4s
    3472:	learn: 67859.4876556	test: 114844.3918845	best: 114841.0279594 (3470)	total: 20.4s	remaining: 38.4s
    3473:	learn: 67856.8035131	test: 114842.2278561	best: 114841.0279594 (3470)	total: 20.4s	remaining: 38.4s
    3474:	learn: 67850.6780325	test: 114844.6187471	best: 114841.0279594 (3470)	total: 20.4s	remaining: 38.4s
    3475:	learn: 67842.3696822	test: 114838.7123677	best: 114838.7123677 (3475)	total: 20.5s	remaining: 38.4s
    3476:	learn: 67839.0837018	test: 114838.0592122	best: 114838.0592122 (3476)	total: 20.5s	remaining: 38.4s
    3477:	learn: 67835.3146834	test: 114838.0090047	best: 114838.0090047 (3477)	total: 20.5s	remaining: 38.4s
    3478:	learn: 67827.6201328	test: 114838.3356258	best: 114838.0090047 (3477)	total: 20.5s	remaining: 38.4s
    3479:	learn: 67822.3099121	test: 114836.9526179	best: 114836.9526179 (3479)	total: 20.5s	remaining: 38.4s
    3480:	learn: 67817.7205522	test: 114836.2825665	best: 114836.2825665 (3480)	total: 20.5s	remaining: 38.4s
    3481:	learn: 67814.1646896	test: 114837.0831584	best: 114836.2825665 (3480)	total: 20.5s	remaining: 38.4s
    3482:	learn: 67809.4436428	test: 114834.8560500	best: 114834.8560500 (3482)	total: 20.5s	remaining: 38.4s
    3483:	learn: 67806.9637072	test: 114835.1136758	best: 114834.8560500 (3482)	total: 20.5s	remaining: 38.3s
    3484:	learn: 67801.1977085	test: 114833.1472414	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3485:	learn: 67795.4618304	test: 114834.0902982	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3486:	learn: 67791.4068013	test: 114835.7021496	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3487:	learn: 67784.9599078	test: 114835.2921009	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3488:	learn: 67780.3163276	test: 114837.2044029	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3489:	learn: 67775.9343938	test: 114835.9686222	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3490:	learn: 67768.9564657	test: 114837.7375308	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3491:	learn: 67763.0483258	test: 114833.5044572	best: 114833.1472414 (3484)	total: 20.5s	remaining: 38.3s
    3492:	learn: 67754.6031993	test: 114836.3907286	best: 114833.1472414 (3484)	total: 20.6s	remaining: 38.3s
    3493:	learn: 67747.3458541	test: 114838.1636367	best: 114833.1472414 (3484)	total: 20.6s	remaining: 38.3s
    3494:	learn: 67741.4417659	test: 114836.6843274	best: 114833.1472414 (3484)	total: 20.6s	remaining: 38.3s
    3495:	learn: 67735.9587858	test: 114835.6234306	best: 114833.1472414 (3484)	total: 20.6s	remaining: 38.3s
    3496:	learn: 67733.3698421	test: 114835.6163891	best: 114833.1472414 (3484)	total: 20.6s	remaining: 38.3s
    3497:	learn: 67722.0437901	test: 114832.4170502	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.3s
    3498:	learn: 67718.1440254	test: 114834.1021849	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.3s
    3499:	learn: 67709.7614558	test: 114835.5209172	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3500:	learn: 67703.1496412	test: 114835.2993467	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3501:	learn: 67699.3228205	test: 114838.6958542	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3502:	learn: 67690.8072920	test: 114836.7278694	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3503:	learn: 67685.0188871	test: 114834.8307004	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3504:	learn: 67678.3470196	test: 114838.0499837	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3505:	learn: 67670.7133419	test: 114840.3535335	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3506:	learn: 67658.9867004	test: 114840.9630106	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3507:	learn: 67658.2766615	test: 114841.1123530	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3508:	learn: 67654.8203288	test: 114842.3880608	best: 114832.4170502 (3497)	total: 20.6s	remaining: 38.2s
    3509:	learn: 67649.1186502	test: 114843.9448499	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3510:	learn: 67640.5087951	test: 114843.3410505	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3511:	learn: 67636.2319838	test: 114839.4087409	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3512:	learn: 67633.1688861	test: 114838.8047225	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3513:	learn: 67629.7173684	test: 114838.2897759	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3514:	learn: 67627.4392084	test: 114838.8581669	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3515:	learn: 67625.5897065	test: 114835.5364488	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.2s
    3516:	learn: 67617.9362416	test: 114832.5760953	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.1s
    3517:	learn: 67610.8764722	test: 114833.6456693	best: 114832.4170502 (3497)	total: 20.7s	remaining: 38.1s
    3518:	learn: 67606.3293028	test: 114831.6117827	best: 114831.6117827 (3518)	total: 20.7s	remaining: 38.1s
    3519:	learn: 67604.3806727	test: 114829.3677517	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3520:	learn: 67599.7438418	test: 114833.7266600	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3521:	learn: 67593.4223633	test: 114834.1447433	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3522:	learn: 67585.9693023	test: 114833.4148506	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3523:	learn: 67579.5689534	test: 114836.8604397	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3524:	learn: 67576.5879439	test: 114836.6925435	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3525:	learn: 67573.2902555	test: 114835.5080446	best: 114829.3677517 (3519)	total: 20.7s	remaining: 38.1s
    3526:	learn: 67569.3436925	test: 114832.4348991	best: 114829.3677517 (3519)	total: 20.8s	remaining: 38.1s
    3527:	learn: 67563.6161162	test: 114834.3275689	best: 114829.3677517 (3519)	total: 20.8s	remaining: 38.1s
    3528:	learn: 67558.7181280	test: 114832.9854078	best: 114829.3677517 (3519)	total: 20.8s	remaining: 38.1s
    3529:	learn: 67554.1569514	test: 114833.8300820	best: 114829.3677517 (3519)	total: 20.8s	remaining: 38.1s
    3530:	learn: 67546.1192760	test: 114833.7086475	best: 114829.3677517 (3519)	total: 20.8s	remaining: 38.1s
    3531:	learn: 67539.8743877	test: 114825.4260075	best: 114825.4260075 (3531)	total: 20.8s	remaining: 38.1s
    3532:	learn: 67531.7896674	test: 114820.8192322	best: 114820.8192322 (3532)	total: 20.8s	remaining: 38s
    3533:	learn: 67526.3490524	test: 114823.6338252	best: 114820.8192322 (3532)	total: 20.8s	remaining: 38s
    3534:	learn: 67523.2624059	test: 114823.1443563	best: 114820.8192322 (3532)	total: 20.8s	remaining: 38s
    3535:	learn: 67513.6977840	test: 114817.1052089	best: 114817.1052089 (3535)	total: 20.8s	remaining: 38s
    3536:	learn: 67509.1881498	test: 114817.4240991	best: 114817.1052089 (3535)	total: 20.8s	remaining: 38s
    3537:	learn: 67502.3504404	test: 114816.2788011	best: 114816.2788011 (3537)	total: 20.8s	remaining: 38s
    3538:	learn: 67500.4436457	test: 114817.1763492	best: 114816.2788011 (3537)	total: 20.8s	remaining: 38s
    3539:	learn: 67497.5370067	test: 114817.0451977	best: 114816.2788011 (3537)	total: 20.8s	remaining: 38s
    3540:	learn: 67493.0737046	test: 114817.4843733	best: 114816.2788011 (3537)	total: 20.8s	remaining: 38s
    3541:	learn: 67488.1571395	test: 114817.1289977	best: 114816.2788011 (3537)	total: 20.8s	remaining: 38s
    3542:	learn: 67480.4200951	test: 114814.7384117	best: 114814.7384117 (3542)	total: 20.8s	remaining: 38s
    3543:	learn: 67476.0825713	test: 114816.8068915	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3544:	learn: 67462.0810542	test: 114816.0727793	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3545:	learn: 67456.5955998	test: 114815.4559429	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3546:	learn: 67449.3724812	test: 114815.9889099	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3547:	learn: 67442.0818899	test: 114817.5314984	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3548:	learn: 67437.7916251	test: 114817.4171837	best: 114814.7384117 (3542)	total: 20.9s	remaining: 38s
    3549:	learn: 67432.7313669	test: 114814.4894016	best: 114814.4894016 (3549)	total: 20.9s	remaining: 38s
    3550:	learn: 67425.8633620	test: 114807.7606860	best: 114807.7606860 (3550)	total: 20.9s	remaining: 37.9s
    3551:	learn: 67420.1543777	test: 114804.9962939	best: 114804.9962939 (3551)	total: 20.9s	remaining: 37.9s
    3552:	learn: 67413.3928780	test: 114808.1442034	best: 114804.9962939 (3551)	total: 20.9s	remaining: 37.9s
    3553:	learn: 67410.1528765	test: 114807.9154342	best: 114804.9962939 (3551)	total: 20.9s	remaining: 37.9s
    3554:	learn: 67405.1088391	test: 114807.0083939	best: 114804.9962939 (3551)	total: 20.9s	remaining: 37.9s
    3555:	learn: 67401.6995229	test: 114807.8125297	best: 114804.9962939 (3551)	total: 20.9s	remaining: 37.9s
    3556:	learn: 67396.3366478	test: 114803.8675197	best: 114803.8675197 (3556)	total: 20.9s	remaining: 37.9s
    3557:	learn: 67387.4495356	test: 114802.8158859	best: 114802.8158859 (3557)	total: 20.9s	remaining: 37.9s
    3558:	learn: 67382.5324878	test: 114807.0507674	best: 114802.8158859 (3557)	total: 20.9s	remaining: 37.9s
    3559:	learn: 67378.2223230	test: 114805.3066593	best: 114802.8158859 (3557)	total: 20.9s	remaining: 37.9s
    3560:	learn: 67374.4410386	test: 114807.8451046	best: 114802.8158859 (3557)	total: 21s	remaining: 37.9s
    3561:	learn: 67371.3114577	test: 114807.8067844	best: 114802.8158859 (3557)	total: 21s	remaining: 37.9s
    3562:	learn: 67365.1992523	test: 114802.2244022	best: 114802.2244022 (3562)	total: 21s	remaining: 37.9s
    3563:	learn: 67357.3625580	test: 114802.1412638	best: 114802.1412638 (3563)	total: 21s	remaining: 37.9s
    3564:	learn: 67345.6792651	test: 114797.2283042	best: 114797.2283042 (3564)	total: 21s	remaining: 37.9s
    3565:	learn: 67335.6150049	test: 114794.0597661	best: 114794.0597661 (3565)	total: 21s	remaining: 37.9s
    3566:	learn: 67331.2239326	test: 114792.5812196	best: 114792.5812196 (3566)	total: 21s	remaining: 37.9s
    3567:	learn: 67325.9074691	test: 114790.9561090	best: 114790.9561090 (3567)	total: 21s	remaining: 37.8s
    3568:	learn: 67322.4305183	test: 114788.3027271	best: 114788.3027271 (3568)	total: 21s	remaining: 37.8s
    3569:	learn: 67314.6421860	test: 114790.0181723	best: 114788.3027271 (3568)	total: 21s	remaining: 37.8s
    3570:	learn: 67309.7028521	test: 114788.5830862	best: 114788.3027271 (3568)	total: 21s	remaining: 37.8s
    3571:	learn: 67303.5002774	test: 114785.6862051	best: 114785.6862051 (3571)	total: 21s	remaining: 37.8s
    3572:	learn: 67299.6210368	test: 114783.8127876	best: 114783.8127876 (3572)	total: 21s	remaining: 37.8s
    3573:	learn: 67297.2860319	test: 114782.9246305	best: 114782.9246305 (3573)	total: 21s	remaining: 37.8s
    3574:	learn: 67289.6884599	test: 114781.6522956	best: 114781.6522956 (3574)	total: 21s	remaining: 37.8s
    3575:	learn: 67281.0049959	test: 114779.0129854	best: 114779.0129854 (3575)	total: 21s	remaining: 37.8s
    3576:	learn: 67275.0843299	test: 114779.2713170	best: 114779.0129854 (3575)	total: 21s	remaining: 37.8s
    3577:	learn: 67274.1315713	test: 114779.9759651	best: 114779.0129854 (3575)	total: 21.1s	remaining: 37.8s
    3578:	learn: 67268.7186624	test: 114779.4397233	best: 114779.0129854 (3575)	total: 21.1s	remaining: 37.8s
    3579:	learn: 67263.1421081	test: 114777.2675066	best: 114777.2675066 (3579)	total: 21.1s	remaining: 37.8s
    3580:	learn: 67256.4801949	test: 114777.7844662	best: 114777.2675066 (3579)	total: 21.1s	remaining: 37.8s
    3581:	learn: 67251.1298499	test: 114774.3884573	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.8s
    3582:	learn: 67247.6092163	test: 114775.4222722	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.8s
    3583:	learn: 67241.5146624	test: 114775.9455263	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.8s
    3584:	learn: 67232.8976096	test: 114776.2588598	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.8s
    3585:	learn: 67226.8310906	test: 114777.0916068	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.7s
    3586:	learn: 67223.6779635	test: 114775.7661866	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.7s
    3587:	learn: 67218.8358803	test: 114776.5117967	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.7s
    3588:	learn: 67215.5590004	test: 114775.5508484	best: 114774.3884573 (3581)	total: 21.1s	remaining: 37.7s
    3589:	learn: 67212.1961905	test: 114773.4422661	best: 114773.4422661 (3589)	total: 21.1s	remaining: 37.7s
    3590:	learn: 67206.7838072	test: 114773.0770225	best: 114773.0770225 (3590)	total: 21.1s	remaining: 37.7s
    3591:	learn: 67201.3248299	test: 114772.0862575	best: 114772.0862575 (3591)	total: 21.1s	remaining: 37.7s
    3592:	learn: 67198.1861061	test: 114770.0045811	best: 114770.0045811 (3592)	total: 21.1s	remaining: 37.7s
    3593:	learn: 67190.6776628	test: 114765.6071821	best: 114765.6071821 (3593)	total: 21.2s	remaining: 37.7s
    3594:	learn: 67182.1900633	test: 114763.4161087	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3595:	learn: 67172.8226933	test: 114771.6628284	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3596:	learn: 67169.3701617	test: 114770.8577873	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3597:	learn: 67162.2867332	test: 114769.3812772	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3598:	learn: 67157.1665815	test: 114770.1287393	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3599:	learn: 67155.4658626	test: 114766.2916676	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3600:	learn: 67150.1062905	test: 114765.2376154	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3601:	learn: 67143.7728901	test: 114764.5984210	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3602:	learn: 67140.6686521	test: 114767.0487949	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3603:	learn: 67135.1507759	test: 114766.8083657	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3604:	learn: 67128.8704397	test: 114766.0140241	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3605:	learn: 67119.7123816	test: 114767.2260608	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3606:	learn: 67108.5328666	test: 114766.6577834	best: 114763.4161087 (3594)	total: 21.2s	remaining: 37.7s
    3607:	learn: 67102.5349657	test: 114770.0751958	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.7s
    3608:	learn: 67099.3916501	test: 114769.5027001	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.7s
    3609:	learn: 67089.6507546	test: 114767.3460528	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.7s
    3610:	learn: 67085.5019686	test: 114764.6866149	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.6s
    3611:	learn: 67081.0466242	test: 114767.4034359	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.6s
    3612:	learn: 67076.8249374	test: 114767.5618213	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.6s
    3613:	learn: 67073.3896793	test: 114767.6372952	best: 114763.4161087 (3594)	total: 21.3s	remaining: 37.6s
    3614:	learn: 67070.1108756	test: 114762.7870430	best: 114762.7870430 (3614)	total: 21.3s	remaining: 37.6s
    3615:	learn: 67063.7085625	test: 114760.3845022	best: 114760.3845022 (3615)	total: 21.3s	remaining: 37.6s
    3616:	learn: 67058.6790811	test: 114763.5352961	best: 114760.3845022 (3615)	total: 21.3s	remaining: 37.6s
    3617:	learn: 67052.4072462	test: 114768.2636759	best: 114760.3845022 (3615)	total: 21.3s	remaining: 37.6s
    3618:	learn: 67046.3592566	test: 114765.2192488	best: 114760.3845022 (3615)	total: 21.3s	remaining: 37.6s
    3619:	learn: 67041.2784905	test: 114763.3452838	best: 114760.3845022 (3615)	total: 21.3s	remaining: 37.6s
    3620:	learn: 67031.9733797	test: 114758.2994007	best: 114758.2994007 (3620)	total: 21.3s	remaining: 37.6s
    3621:	learn: 67025.8717707	test: 114755.3784059	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3622:	learn: 67021.2563127	test: 114755.6084459	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3623:	learn: 67015.8034685	test: 114756.5214344	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3624:	learn: 67012.0609265	test: 114758.1740442	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3625:	learn: 67006.2592065	test: 114757.3983162	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3626:	learn: 67000.3315925	test: 114756.8864644	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3627:	learn: 66994.0816719	test: 114757.6640085	best: 114755.3784059 (3621)	total: 21.4s	remaining: 37.6s
    3628:	learn: 66986.1427614	test: 114754.7197213	best: 114754.7197213 (3628)	total: 21.4s	remaining: 37.6s
    3629:	learn: 66983.3817624	test: 114753.9852255	best: 114753.9852255 (3629)	total: 21.4s	remaining: 37.6s
    3630:	learn: 66978.2519710	test: 114750.5688462	best: 114750.5688462 (3630)	total: 21.4s	remaining: 37.6s
    3631:	learn: 66973.2078859	test: 114754.2657849	best: 114750.5688462 (3630)	total: 21.4s	remaining: 37.5s
    3632:	learn: 66968.9545945	test: 114750.4046749	best: 114750.4046749 (3632)	total: 21.4s	remaining: 37.5s
    3633:	learn: 66964.5955656	test: 114749.8130491	best: 114749.8130491 (3633)	total: 21.4s	remaining: 37.5s
    3634:	learn: 66959.7812086	test: 114747.2490988	best: 114747.2490988 (3634)	total: 21.4s	remaining: 37.5s
    3635:	learn: 66954.7806863	test: 114747.4728166	best: 114747.2490988 (3634)	total: 21.4s	remaining: 37.5s
    3636:	learn: 66948.4545362	test: 114742.5821826	best: 114742.5821826 (3636)	total: 21.4s	remaining: 37.5s
    3637:	learn: 66943.3232775	test: 114738.3425634	best: 114738.3425634 (3637)	total: 21.5s	remaining: 37.5s
    3638:	learn: 66938.4663035	test: 114738.2480583	best: 114738.2480583 (3638)	total: 21.5s	remaining: 37.5s
    3639:	learn: 66934.1884886	test: 114737.7516526	best: 114737.7516526 (3639)	total: 21.5s	remaining: 37.5s
    3640:	learn: 66925.9025683	test: 114738.1539511	best: 114737.7516526 (3639)	total: 21.5s	remaining: 37.5s
    3641:	learn: 66920.5846964	test: 114739.2709219	best: 114737.7516526 (3639)	total: 21.5s	remaining: 37.5s
    3642:	learn: 66916.7076950	test: 114738.7104835	best: 114737.7516526 (3639)	total: 21.5s	remaining: 37.5s
    3643:	learn: 66910.6036050	test: 114735.9796979	best: 114735.9796979 (3643)	total: 21.5s	remaining: 37.5s
    3644:	learn: 66903.6873280	test: 114732.3783030	best: 114732.3783030 (3644)	total: 21.5s	remaining: 37.5s
    3645:	learn: 66899.8916329	test: 114731.3339460	best: 114731.3339460 (3645)	total: 21.5s	remaining: 37.5s
    3646:	learn: 66895.6625957	test: 114730.5995034	best: 114730.5995034 (3646)	total: 21.5s	remaining: 37.5s
    3647:	learn: 66894.1616535	test: 114730.5766395	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.5s
    3648:	learn: 66886.7088251	test: 114731.9312642	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.5s
    3649:	learn: 66881.7462449	test: 114733.5693997	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.4s
    3650:	learn: 66878.9114321	test: 114731.3967280	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.4s
    3651:	learn: 66872.0158906	test: 114732.7352784	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.4s
    3652:	learn: 66868.2531306	test: 114732.1181115	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.4s
    3653:	learn: 66865.0201590	test: 114732.7317454	best: 114730.5766395 (3647)	total: 21.5s	remaining: 37.4s
    3654:	learn: 66862.0237160	test: 114730.3405433	best: 114730.3405433 (3654)	total: 21.6s	remaining: 37.4s
    3655:	learn: 66858.6270383	test: 114732.3222666	best: 114730.3405433 (3654)	total: 21.6s	remaining: 37.4s
    3656:	learn: 66854.3357181	test: 114729.8334935	best: 114729.8334935 (3656)	total: 21.6s	remaining: 37.4s
    3657:	learn: 66850.1787632	test: 114729.0839126	best: 114729.0839126 (3657)	total: 21.6s	remaining: 37.4s
    3658:	learn: 66845.0831740	test: 114732.5264754	best: 114729.0839126 (3657)	total: 21.6s	remaining: 37.4s
    3659:	learn: 66837.0977986	test: 114731.0582868	best: 114729.0839126 (3657)	total: 21.6s	remaining: 37.4s
    3660:	learn: 66832.2242853	test: 114727.5649012	best: 114727.5649012 (3660)	total: 21.6s	remaining: 37.4s
    3661:	learn: 66825.3372884	test: 114722.5957187	best: 114722.5957187 (3661)	total: 21.6s	remaining: 37.4s
    3662:	learn: 66822.7627986	test: 114723.7775679	best: 114722.5957187 (3661)	total: 21.6s	remaining: 37.4s
    3663:	learn: 66814.7574221	test: 114726.5925292	best: 114722.5957187 (3661)	total: 21.6s	remaining: 37.4s
    3664:	learn: 66810.9384969	test: 114725.2887892	best: 114722.5957187 (3661)	total: 21.6s	remaining: 37.4s
    3665:	learn: 66805.3902598	test: 114724.7433944	best: 114722.5957187 (3661)	total: 21.6s	remaining: 37.3s
    3666:	learn: 66800.0252934	test: 114722.5410315	best: 114722.5410315 (3666)	total: 21.6s	remaining: 37.3s
    3667:	learn: 66793.1111767	test: 114726.7851143	best: 114722.5410315 (3666)	total: 21.6s	remaining: 37.3s
    3668:	learn: 66786.8252685	test: 114722.6669865	best: 114722.5410315 (3666)	total: 21.6s	remaining: 37.3s
    3669:	learn: 66778.8776144	test: 114717.2587316	best: 114717.2587316 (3669)	total: 21.6s	remaining: 37.3s
    3670:	learn: 66771.2477977	test: 114715.9328884	best: 114715.9328884 (3670)	total: 21.6s	remaining: 37.3s
    3671:	learn: 66767.1217565	test: 114722.6739700	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3672:	learn: 66761.9258845	test: 114722.9735920	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3673:	learn: 66753.0160409	test: 114722.1728111	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3674:	learn: 66748.1726830	test: 114721.6542009	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3675:	learn: 66741.9293394	test: 114723.9405141	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3676:	learn: 66734.9344652	test: 114721.0593491	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3677:	learn: 66729.9642776	test: 114719.7835453	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3678:	learn: 66721.6424573	test: 114716.3508849	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3679:	learn: 66712.1194173	test: 114719.3375454	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3680:	learn: 66705.7898397	test: 114717.4334501	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3681:	learn: 66700.8400715	test: 114716.5049913	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3682:	learn: 66693.6097127	test: 114717.4412245	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3683:	learn: 66686.0818971	test: 114717.7741425	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.3s
    3684:	learn: 66680.4977661	test: 114718.6550509	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.2s
    3685:	learn: 66670.6959654	test: 114719.6384440	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.2s
    3686:	learn: 66669.0601331	test: 114718.8054182	best: 114715.9328884 (3670)	total: 21.7s	remaining: 37.2s
    3687:	learn: 66664.7145411	test: 114719.3337344	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3688:	learn: 66654.7820470	test: 114719.1466170	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3689:	learn: 66651.1158252	test: 114722.8264634	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3690:	learn: 66646.4631744	test: 114720.9937178	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3691:	learn: 66642.5839820	test: 114722.8056235	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3692:	learn: 66638.0881775	test: 114723.9324816	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3693:	learn: 66635.0761965	test: 114724.0443667	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3694:	learn: 66630.9309159	test: 114721.7266457	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3695:	learn: 66626.0959235	test: 114720.5784267	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3696:	learn: 66618.2261094	test: 114720.1759460	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3697:	learn: 66615.2734797	test: 114722.6090309	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3698:	learn: 66610.5199920	test: 114725.8065595	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3699:	learn: 66604.8536138	test: 114721.2247892	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.2s
    3700:	learn: 66602.2600179	test: 114720.4069866	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.1s
    3701:	learn: 66601.6220696	test: 114720.4297633	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.1s
    3702:	learn: 66595.2547967	test: 114718.4086937	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.1s
    3703:	learn: 66590.2103757	test: 114721.3427889	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.1s
    3704:	learn: 66585.0826993	test: 114719.0935856	best: 114715.9328884 (3670)	total: 21.8s	remaining: 37.1s
    3705:	learn: 66580.2895846	test: 114717.3992623	best: 114715.9328884 (3670)	total: 21.9s	remaining: 37.1s
    3706:	learn: 66574.9520471	test: 114716.8098950	best: 114715.9328884 (3670)	total: 21.9s	remaining: 37.1s
    3707:	learn: 66571.5706180	test: 114716.6934304	best: 114715.9328884 (3670)	total: 21.9s	remaining: 37.1s
    3708:	learn: 66569.3702373	test: 114716.8856450	best: 114715.9328884 (3670)	total: 21.9s	remaining: 37.1s
    3709:	learn: 66559.7403426	test: 114714.8173610	best: 114714.8173610 (3709)	total: 21.9s	remaining: 37.1s
    3710:	learn: 66551.9873412	test: 114717.2109480	best: 114714.8173610 (3709)	total: 21.9s	remaining: 37.1s
    3711:	learn: 66547.4699880	test: 114715.1708141	best: 114714.8173610 (3709)	total: 21.9s	remaining: 37.1s
    3712:	learn: 66545.1960533	test: 114714.7246257	best: 114714.7246257 (3712)	total: 21.9s	remaining: 37.1s
    3713:	learn: 66540.3377832	test: 114714.0578658	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3714:	learn: 66533.4019683	test: 114718.0287162	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3715:	learn: 66528.0198856	test: 114716.9558497	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3716:	learn: 66525.1579993	test: 114718.9043649	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3717:	learn: 66515.9495470	test: 114719.6802638	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3718:	learn: 66510.3635818	test: 114717.8238606	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37.1s
    3719:	learn: 66507.4739638	test: 114719.5212336	best: 114714.0578658 (3713)	total: 21.9s	remaining: 37s
    3720:	learn: 66503.4950672	test: 114720.2703075	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3721:	learn: 66499.2967124	test: 114718.3384694	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3722:	learn: 66495.1958340	test: 114721.2001957	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3723:	learn: 66490.8835614	test: 114720.2903878	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3724:	learn: 66485.1501634	test: 114721.1774573	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3725:	learn: 66480.2198550	test: 114726.3062628	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3726:	learn: 66478.4661018	test: 114724.4644241	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3727:	learn: 66473.4710343	test: 114724.9377451	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3728:	learn: 66470.7762525	test: 114723.7276371	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3729:	learn: 66464.0115893	test: 114723.2255911	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3730:	learn: 66460.3132025	test: 114724.6108988	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3731:	learn: 66456.1497377	test: 114721.9499586	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3732:	learn: 66450.6270717	test: 114719.0927682	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3733:	learn: 66446.0031022	test: 114717.8752465	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3734:	learn: 66438.5352142	test: 114716.8854866	best: 114714.0578658 (3713)	total: 22s	remaining: 37s
    3735:	learn: 66434.8369936	test: 114715.1047136	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3736:	learn: 66430.0969785	test: 114716.3794230	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3737:	learn: 66427.4696661	test: 114720.4724356	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3738:	learn: 66421.7812295	test: 114720.8216835	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3739:	learn: 66418.6201353	test: 114721.7708953	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3740:	learn: 66411.5681636	test: 114721.8257606	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3741:	learn: 66407.7251162	test: 114724.4525112	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3742:	learn: 66401.7810239	test: 114724.7198797	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3743:	learn: 66398.4767470	test: 114725.1161958	best: 114714.0578658 (3713)	total: 22.1s	remaining: 37s
    3744:	learn: 66392.5565866	test: 114726.4143002	best: 114714.0578658 (3713)	total: 22.1s	remaining: 36.9s
    3745:	learn: 66388.9261112	test: 114725.2716784	best: 114714.0578658 (3713)	total: 22.1s	remaining: 36.9s
    3746:	learn: 66385.2333900	test: 114725.3220814	best: 114714.0578658 (3713)	total: 22.1s	remaining: 36.9s
    3747:	learn: 66379.5787685	test: 114724.1020222	best: 114714.0578658 (3713)	total: 22.1s	remaining: 36.9s
    3748:	learn: 66375.0666776	test: 114724.5834222	best: 114714.0578658 (3713)	total: 22.1s	remaining: 36.9s
    3749:	learn: 66371.3399437	test: 114721.4440606	best: 114714.0578658 (3713)	total: 22.2s	remaining: 36.9s
    3750:	learn: 66363.8565410	test: 114719.5412794	best: 114714.0578658 (3713)	total: 22.2s	remaining: 36.9s
    3751:	learn: 66359.5202185	test: 114718.6986323	best: 114714.0578658 (3713)	total: 22.2s	remaining: 36.9s
    3752:	learn: 66352.8817180	test: 114717.2408194	best: 114714.0578658 (3713)	total: 22.2s	remaining: 36.9s
    3753:	learn: 66344.5444883	test: 114713.8158172	best: 114713.8158172 (3753)	total: 22.2s	remaining: 36.9s
    3754:	learn: 66341.7250104	test: 114713.2218884	best: 114713.2218884 (3754)	total: 22.2s	remaining: 36.9s
    3755:	learn: 66335.8382465	test: 114711.7807519	best: 114711.7807519 (3755)	total: 22.2s	remaining: 36.9s
    3756:	learn: 66330.1960612	test: 114713.2642154	best: 114711.7807519 (3755)	total: 22.2s	remaining: 36.9s
    3757:	learn: 66323.4010321	test: 114713.3344746	best: 114711.7807519 (3755)	total: 22.2s	remaining: 36.9s
    3758:	learn: 66319.1112146	test: 114709.9899256	best: 114709.9899256 (3758)	total: 22.2s	remaining: 36.9s
    3759:	learn: 66314.0923631	test: 114710.5818493	best: 114709.9899256 (3758)	total: 22.2s	remaining: 36.9s
    3760:	learn: 66309.9106349	test: 114707.5367404	best: 114707.5367404 (3760)	total: 22.2s	remaining: 36.9s
    3761:	learn: 66297.9044915	test: 114705.4084672	best: 114705.4084672 (3761)	total: 22.2s	remaining: 36.9s
    3762:	learn: 66291.5207196	test: 114705.3433328	best: 114705.3433328 (3762)	total: 22.3s	remaining: 36.9s
    3763:	learn: 66289.5423709	test: 114704.5611717	best: 114704.5611717 (3763)	total: 22.3s	remaining: 36.9s
    3764:	learn: 66283.1251388	test: 114703.6685600	best: 114703.6685600 (3764)	total: 22.3s	remaining: 36.9s
    3765:	learn: 66278.6674637	test: 114703.7796394	best: 114703.6685600 (3764)	total: 22.3s	remaining: 36.9s
    3766:	learn: 66268.2299607	test: 114697.1077236	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3767:	learn: 66261.8052663	test: 114698.5970431	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3768:	learn: 66256.2947884	test: 114697.9906236	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3769:	learn: 66251.8605635	test: 114697.2573223	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3770:	learn: 66245.6242012	test: 114699.0066900	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3771:	learn: 66238.4582833	test: 114698.9187803	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.9s
    3772:	learn: 66233.0418248	test: 114699.0032988	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.8s
    3773:	learn: 66223.9868993	test: 114702.3999431	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.8s
    3774:	learn: 66220.3518246	test: 114699.8627616	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.8s
    3775:	learn: 66215.7484872	test: 114702.9256136	best: 114697.1077236 (3766)	total: 22.3s	remaining: 36.8s
    3776:	learn: 66210.5217253	test: 114700.9969110	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3777:	learn: 66203.4574748	test: 114700.1712095	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3778:	learn: 66198.8584296	test: 114701.2134393	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3779:	learn: 66192.8864035	test: 114703.2804490	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3780:	learn: 66186.4918991	test: 114701.7924155	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3781:	learn: 66182.0173750	test: 114701.8575210	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3782:	learn: 66177.3236165	test: 114701.0863646	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3783:	learn: 66172.0130719	test: 114702.9697787	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3784:	learn: 66166.8733477	test: 114697.4105252	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3785:	learn: 66164.4532347	test: 114701.2884096	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3786:	learn: 66157.7818446	test: 114699.9347356	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3787:	learn: 66150.4812611	test: 114697.9347766	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3788:	learn: 66147.1531858	test: 114698.0354846	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3789:	learn: 66143.8227724	test: 114700.5707243	best: 114697.1077236 (3766)	total: 22.4s	remaining: 36.8s
    3790:	learn: 66138.5404860	test: 114698.4294754	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3791:	learn: 66131.5946353	test: 114697.3947131	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3792:	learn: 66125.1211917	test: 114697.9145561	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3793:	learn: 66116.2520012	test: 114698.5102906	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3794:	learn: 66114.0829043	test: 114697.4580506	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3795:	learn: 66104.8040977	test: 114698.1932254	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3796:	learn: 66102.3814017	test: 114697.1870133	best: 114697.1077236 (3766)	total: 22.5s	remaining: 36.8s
    3797:	learn: 66097.2977161	test: 114696.6024957	best: 114696.6024957 (3797)	total: 22.5s	remaining: 36.7s
    3798:	learn: 66091.3984784	test: 114695.1182131	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3799:	learn: 66086.9670689	test: 114697.9140215	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3800:	learn: 66081.1937600	test: 114699.9842977	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3801:	learn: 66076.5987328	test: 114699.7066639	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3802:	learn: 66070.7912145	test: 114701.4210980	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3803:	learn: 66063.9891592	test: 114702.4812518	best: 114695.1182131 (3798)	total: 22.5s	remaining: 36.7s
    3804:	learn: 66058.8534751	test: 114701.5662001	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3805:	learn: 66053.4196142	test: 114701.1788856	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3806:	learn: 66045.8915101	test: 114702.4073368	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3807:	learn: 66037.0658272	test: 114703.0263249	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3808:	learn: 66034.4969324	test: 114701.8075789	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3809:	learn: 66031.0397641	test: 114702.9209272	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3810:	learn: 66027.3744316	test: 114699.6378609	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3811:	learn: 66022.2413533	test: 114697.8539584	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3812:	learn: 66012.2495857	test: 114698.2291638	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3813:	learn: 66006.9790288	test: 114699.0055442	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3814:	learn: 65996.8329887	test: 114696.9396835	best: 114695.1182131 (3798)	total: 22.6s	remaining: 36.7s
    3815:	learn: 65992.4614708	test: 114692.8951111	best: 114692.8951111 (3815)	total: 22.6s	remaining: 36.7s
    3816:	learn: 65986.5029588	test: 114689.7371450	best: 114689.7371450 (3816)	total: 22.6s	remaining: 36.7s
    3817:	learn: 65981.8592388	test: 114690.8265538	best: 114689.7371450 (3816)	total: 22.6s	remaining: 36.7s
    3818:	learn: 65977.6366992	test: 114689.3228357	best: 114689.3228357 (3818)	total: 22.6s	remaining: 36.7s
    3819:	learn: 65974.7761718	test: 114688.6721599	best: 114688.6721599 (3819)	total: 22.7s	remaining: 36.7s
    3820:	learn: 65971.3458973	test: 114686.7324234	best: 114686.7324234 (3820)	total: 22.7s	remaining: 36.6s
    3821:	learn: 65965.4367880	test: 114684.0938029	best: 114684.0938029 (3821)	total: 22.7s	remaining: 36.6s
    3822:	learn: 65955.6615755	test: 114681.0559155	best: 114681.0559155 (3822)	total: 22.7s	remaining: 36.6s
    3823:	learn: 65950.9756164	test: 114680.6459923	best: 114680.6459923 (3823)	total: 22.7s	remaining: 36.6s
    3824:	learn: 65948.0046347	test: 114675.9427328	best: 114675.9427328 (3824)	total: 22.7s	remaining: 36.6s
    3825:	learn: 65938.0095320	test: 114675.4643928	best: 114675.4643928 (3825)	total: 22.7s	remaining: 36.6s
    3826:	learn: 65932.6024824	test: 114672.7054297	best: 114672.7054297 (3826)	total: 22.7s	remaining: 36.6s
    3827:	learn: 65926.1890824	test: 114670.3166098	best: 114670.3166098 (3827)	total: 22.7s	remaining: 36.6s
    3828:	learn: 65921.7281411	test: 114667.9017591	best: 114667.9017591 (3828)	total: 22.7s	remaining: 36.6s
    3829:	learn: 65918.2098006	test: 114675.6483132	best: 114667.9017591 (3828)	total: 22.7s	remaining: 36.6s
    3830:	learn: 65910.3239445	test: 114675.5011684	best: 114667.9017591 (3828)	total: 22.7s	remaining: 36.6s
    3831:	learn: 65902.0964082	test: 114671.1825509	best: 114667.9017591 (3828)	total: 22.7s	remaining: 36.6s
    3832:	learn: 65899.3892775	test: 114670.7096151	best: 114667.9017591 (3828)	total: 22.7s	remaining: 36.6s
    3833:	learn: 65895.2084362	test: 114668.3539436	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3834:	learn: 65889.6898842	test: 114670.4416647	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3835:	learn: 65887.6201318	test: 114669.8665499	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3836:	learn: 65881.2108152	test: 114670.6918158	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3837:	learn: 65879.6958944	test: 114670.5257703	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3838:	learn: 65875.6082514	test: 114671.2111309	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3839:	learn: 65874.1030330	test: 114670.2358052	best: 114667.9017591 (3828)	total: 22.8s	remaining: 36.6s
    3840:	learn: 65864.8481945	test: 114666.2579616	best: 114666.2579616 (3840)	total: 22.8s	remaining: 36.6s
    3841:	learn: 65859.1622107	test: 114661.7094779	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.6s
    3842:	learn: 65855.6619862	test: 114663.5720348	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3843:	learn: 65850.5495654	test: 114667.0578579	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3844:	learn: 65846.4790454	test: 114666.2183954	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3845:	learn: 65844.8462655	test: 114665.9704364	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3846:	learn: 65834.1590371	test: 114666.3760087	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3847:	learn: 65828.9936651	test: 114664.6335114	best: 114661.7094779 (3841)	total: 22.8s	remaining: 36.5s
    3848:	learn: 65824.3751813	test: 114663.8396876	best: 114661.7094779 (3841)	total: 22.9s	remaining: 36.5s
    3849:	learn: 65819.3192976	test: 114660.7097940	best: 114660.7097940 (3849)	total: 22.9s	remaining: 36.5s
    3850:	learn: 65813.8960802	test: 114660.3545150	best: 114660.3545150 (3850)	total: 22.9s	remaining: 36.5s
    3851:	learn: 65810.4313777	test: 114662.0319871	best: 114660.3545150 (3850)	total: 22.9s	remaining: 36.5s
    3852:	learn: 65805.8106294	test: 114662.8946506	best: 114660.3545150 (3850)	total: 22.9s	remaining: 36.5s
    3853:	learn: 65802.2702071	test: 114659.7493123	best: 114659.7493123 (3853)	total: 22.9s	remaining: 36.5s
    3854:	learn: 65798.4881330	test: 114659.4214859	best: 114659.4214859 (3854)	total: 22.9s	remaining: 36.5s
    3855:	learn: 65793.7360447	test: 114659.6107954	best: 114659.4214859 (3854)	total: 22.9s	remaining: 36.5s
    3856:	learn: 65788.5695583	test: 114658.0469487	best: 114658.0469487 (3856)	total: 22.9s	remaining: 36.5s
    3857:	learn: 65785.3925201	test: 114656.9697605	best: 114656.9697605 (3857)	total: 22.9s	remaining: 36.5s
    3858:	learn: 65776.9682591	test: 114658.3776781	best: 114656.9697605 (3857)	total: 22.9s	remaining: 36.5s
    3859:	learn: 65770.5917141	test: 114656.9740591	best: 114656.9697605 (3857)	total: 22.9s	remaining: 36.5s
    3860:	learn: 65764.7098613	test: 114659.5402414	best: 114656.9697605 (3857)	total: 22.9s	remaining: 36.5s
    3861:	learn: 65753.9362813	test: 114653.6301861	best: 114653.6301861 (3861)	total: 22.9s	remaining: 36.5s
    3862:	learn: 65748.2286041	test: 114652.2561961	best: 114652.2561961 (3862)	total: 22.9s	remaining: 36.5s
    3863:	learn: 65743.2874989	test: 114651.6843089	best: 114651.6843089 (3863)	total: 23s	remaining: 36.5s
    3864:	learn: 65740.1632836	test: 114651.8623545	best: 114651.6843089 (3863)	total: 23s	remaining: 36.5s
    3865:	learn: 65735.1306940	test: 114650.6201409	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3866:	learn: 65730.9983368	test: 114654.9624047	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3867:	learn: 65725.9563110	test: 114654.6777653	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3868:	learn: 65720.2931703	test: 114651.6659081	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3869:	learn: 65713.3562169	test: 114652.5732533	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3870:	learn: 65700.5423092	test: 114651.7332117	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3871:	learn: 65694.4792706	test: 114651.7687387	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3872:	learn: 65689.4183059	test: 114650.8009962	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3873:	learn: 65685.4557274	test: 114650.9105206	best: 114650.6201409 (3865)	total: 23s	remaining: 36.4s
    3874:	learn: 65680.5222370	test: 114648.9804500	best: 114648.9804500 (3874)	total: 23s	remaining: 36.4s
    3875:	learn: 65673.7479776	test: 114647.3015332	best: 114647.3015332 (3875)	total: 23s	remaining: 36.4s
    3876:	learn: 65671.0767440	test: 114641.3951771	best: 114641.3951771 (3876)	total: 23s	remaining: 36.4s
    3877:	learn: 65666.6113083	test: 114643.3075757	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3878:	learn: 65662.6781818	test: 114642.8785722	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3879:	learn: 65657.9460856	test: 114644.8739894	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3880:	learn: 65651.1981044	test: 114648.2369042	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3881:	learn: 65646.7093676	test: 114647.7689155	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3882:	learn: 65640.0669758	test: 114645.6468974	best: 114641.3951771 (3876)	total: 23.1s	remaining: 36.4s
    3883:	learn: 65627.3057717	test: 114638.5434825	best: 114638.5434825 (3883)	total: 23.1s	remaining: 36.4s
    3884:	learn: 65620.8052450	test: 114636.9028519	best: 114636.9028519 (3884)	total: 23.1s	remaining: 36.4s
    3885:	learn: 65609.4712219	test: 114633.7320565	best: 114633.7320565 (3885)	total: 23.1s	remaining: 36.4s
    3886:	learn: 65607.2099611	test: 114632.5395326	best: 114632.5395326 (3886)	total: 23.1s	remaining: 36.4s
    3887:	learn: 65600.6158970	test: 114631.2174356	best: 114631.2174356 (3887)	total: 23.1s	remaining: 36.4s
    3888:	learn: 65598.1666943	test: 114631.0911167	best: 114631.0911167 (3888)	total: 23.1s	remaining: 36.4s
    3889:	learn: 65589.3552107	test: 114628.9984305	best: 114628.9984305 (3889)	total: 23.1s	remaining: 36.4s
    3890:	learn: 65584.0334036	test: 114629.4436623	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.4s
    3891:	learn: 65574.3953155	test: 114631.7186049	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.4s
    3892:	learn: 65571.2128451	test: 114630.5009415	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.4s
    3893:	learn: 65568.2982307	test: 114629.5877166	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3894:	learn: 65561.4435639	test: 114629.5741154	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3895:	learn: 65558.6263709	test: 114631.9256335	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3896:	learn: 65552.9722241	test: 114631.8694350	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3897:	learn: 65545.1911048	test: 114631.6471378	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3898:	learn: 65540.0219767	test: 114632.2756570	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3899:	learn: 65535.3931051	test: 114632.2298209	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3900:	learn: 65529.6386158	test: 114631.9925562	best: 114628.9984305 (3889)	total: 23.2s	remaining: 36.3s
    3901:	learn: 65521.5910704	test: 114626.9147056	best: 114626.9147056 (3901)	total: 23.2s	remaining: 36.3s
    3902:	learn: 65517.3904644	test: 114625.6610415	best: 114625.6610415 (3902)	total: 23.2s	remaining: 36.3s
    3903:	learn: 65510.9589767	test: 114626.7189450	best: 114625.6610415 (3902)	total: 23.3s	remaining: 36.3s
    3904:	learn: 65504.4835353	test: 114626.7109460	best: 114625.6610415 (3902)	total: 23.3s	remaining: 36.3s
    3905:	learn: 65498.4431093	test: 114626.3136069	best: 114625.6610415 (3902)	total: 23.3s	remaining: 36.3s
    3906:	learn: 65494.2929136	test: 114626.0460566	best: 114625.6610415 (3902)	total: 23.3s	remaining: 36.3s
    3907:	learn: 65489.5686722	test: 114625.1802478	best: 114625.1802478 (3907)	total: 23.3s	remaining: 36.3s
    3908:	learn: 65481.5389994	test: 114629.6099120	best: 114625.1802478 (3907)	total: 23.3s	remaining: 36.3s
    3909:	learn: 65473.9035501	test: 114624.1895606	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3910:	learn: 65470.9673945	test: 114625.8043520	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3911:	learn: 65468.3138038	test: 114625.3707946	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3912:	learn: 65467.7200695	test: 114625.2167501	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3913:	learn: 65464.1953552	test: 114627.5448927	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3914:	learn: 65462.7230555	test: 114627.0294338	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.3s
    3915:	learn: 65459.7092120	test: 114626.1880188	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.2s
    3916:	learn: 65456.2073776	test: 114625.1929863	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.2s
    3917:	learn: 65452.2849462	test: 114624.4915813	best: 114624.1895606 (3909)	total: 23.3s	remaining: 36.2s
    3918:	learn: 65447.1231388	test: 114620.2874273	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3919:	learn: 65436.6222903	test: 114624.0977604	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3920:	learn: 65431.5671881	test: 114623.5490497	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3921:	learn: 65426.1868839	test: 114624.5981829	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3922:	learn: 65423.5421969	test: 114622.2303325	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3923:	learn: 65417.0787307	test: 114623.5619885	best: 114620.2874273 (3918)	total: 23.4s	remaining: 36.2s
    3924:	learn: 65408.9851238	test: 114618.2479882	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3925:	learn: 65403.4262434	test: 114621.1705046	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3926:	learn: 65399.7617214	test: 114620.8293132	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3927:	learn: 65393.0716316	test: 114622.2130179	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3928:	learn: 65387.4163167	test: 114620.2456613	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3929:	learn: 65383.0349072	test: 114620.1574584	best: 114618.2479882 (3924)	total: 23.4s	remaining: 36.2s
    3930:	learn: 65378.0321458	test: 114618.2453963	best: 114618.2453963 (3930)	total: 23.4s	remaining: 36.2s
    3931:	learn: 65371.6781548	test: 114618.6614540	best: 114618.2453963 (3930)	total: 23.4s	remaining: 36.2s
    3932:	learn: 65365.6979061	test: 114617.1138933	best: 114617.1138933 (3932)	total: 23.4s	remaining: 36.2s
    3933:	learn: 65360.6108377	test: 114616.3864540	best: 114616.3864540 (3933)	total: 23.4s	remaining: 36.1s
    3934:	learn: 65355.9653345	test: 114620.7416308	best: 114616.3864540 (3933)	total: 23.4s	remaining: 36.1s
    3935:	learn: 65350.0137085	test: 114618.0116178	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3936:	learn: 65345.4190119	test: 114616.5822585	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3937:	learn: 65338.5757239	test: 114616.5795427	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3938:	learn: 65330.8617284	test: 114621.0110864	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3939:	learn: 65328.0436208	test: 114618.3268821	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3940:	learn: 65324.3974709	test: 114618.5760809	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3941:	learn: 65319.3952044	test: 114617.4708193	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3942:	learn: 65311.7373207	test: 114617.5978732	best: 114616.3864540 (3933)	total: 23.5s	remaining: 36.1s
    3943:	learn: 65302.2167041	test: 114613.3573206	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3944:	learn: 65295.0001217	test: 114614.7087653	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3945:	learn: 65290.3770823	test: 114615.6484457	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3946:	learn: 65284.8102529	test: 114620.1121054	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3947:	learn: 65280.1957961	test: 114619.2780566	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3948:	learn: 65275.9030138	test: 114618.3204752	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36.1s
    3949:	learn: 65270.8030175	test: 114619.9301443	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36s
    3950:	learn: 65265.7448506	test: 114615.8734413	best: 114613.3573206 (3943)	total: 23.5s	remaining: 36s
    3951:	learn: 65259.5461504	test: 114607.3497707	best: 114607.3497707 (3951)	total: 23.5s	remaining: 36s
    3952:	learn: 65255.5877491	test: 114608.7458931	best: 114607.3497707 (3951)	total: 23.6s	remaining: 36s
    3953:	learn: 65249.5735013	test: 114607.4095959	best: 114607.3497707 (3951)	total: 23.6s	remaining: 36s
    3954:	learn: 65246.6398577	test: 114607.1899447	best: 114607.1899447 (3954)	total: 23.6s	remaining: 36s
    3955:	learn: 65240.1304209	test: 114603.6539288	best: 114603.6539288 (3955)	total: 23.6s	remaining: 36s
    3956:	learn: 65236.0431141	test: 114602.8865809	best: 114602.8865809 (3956)	total: 23.6s	remaining: 36s
    3957:	learn: 65233.9403797	test: 114603.3400035	best: 114602.8865809 (3956)	total: 23.6s	remaining: 36s
    3958:	learn: 65229.4190136	test: 114599.6188174	best: 114599.6188174 (3958)	total: 23.6s	remaining: 36s
    3959:	learn: 65224.8798700	test: 114598.3164802	best: 114598.3164802 (3959)	total: 23.6s	remaining: 36s
    3960:	learn: 65219.9838020	test: 114594.3618444	best: 114594.3618444 (3960)	total: 23.6s	remaining: 36s
    3961:	learn: 65214.9213299	test: 114592.1850183	best: 114592.1850183 (3961)	total: 23.6s	remaining: 36s
    3962:	learn: 65210.0721640	test: 114594.2277644	best: 114592.1850183 (3961)	total: 23.6s	remaining: 36s
    3963:	learn: 65205.8802377	test: 114595.0061346	best: 114592.1850183 (3961)	total: 23.6s	remaining: 36s
    3964:	learn: 65201.5372609	test: 114595.4234353	best: 114592.1850183 (3961)	total: 23.6s	remaining: 36s
    3965:	learn: 65196.5093689	test: 114593.4981183	best: 114592.1850183 (3961)	total: 23.6s	remaining: 36s
    3966:	learn: 65191.2362310	test: 114591.9363320	best: 114591.9363320 (3966)	total: 23.6s	remaining: 35.9s
    3967:	learn: 65185.6372960	test: 114594.8250302	best: 114591.9363320 (3966)	total: 23.6s	remaining: 35.9s
    3968:	learn: 65182.7412308	test: 114595.3926131	best: 114591.9363320 (3966)	total: 23.6s	remaining: 35.9s
    3969:	learn: 65177.4058940	test: 114595.0521076	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3970:	learn: 65172.1018781	test: 114595.2211133	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3971:	learn: 65167.3786740	test: 114592.1593253	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3972:	learn: 65163.8303398	test: 114594.3825827	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3973:	learn: 65157.4178555	test: 114595.9580316	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3974:	learn: 65152.2678697	test: 114598.5768145	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3975:	learn: 65145.8288215	test: 114593.5457463	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3976:	learn: 65140.1818290	test: 114595.5443080	best: 114591.9363320 (3966)	total: 23.7s	remaining: 35.9s
    3977:	learn: 65134.3910405	test: 114591.7025459	best: 114591.7025459 (3977)	total: 23.7s	remaining: 35.9s
    3978:	learn: 65129.8386650	test: 114589.8450363	best: 114589.8450363 (3978)	total: 23.7s	remaining: 35.9s
    3979:	learn: 65127.2454957	test: 114587.5576019	best: 114587.5576019 (3979)	total: 23.7s	remaining: 35.9s
    3980:	learn: 65121.9537497	test: 114586.7539846	best: 114586.7539846 (3980)	total: 23.7s	remaining: 35.9s
    3981:	learn: 65116.5446885	test: 114589.1428145	best: 114586.7539846 (3980)	total: 23.7s	remaining: 35.9s
    3982:	learn: 65110.5754041	test: 114586.7424784	best: 114586.7424784 (3982)	total: 23.7s	remaining: 35.8s
    3983:	learn: 65105.8392401	test: 114579.6595397	best: 114579.6595397 (3983)	total: 23.7s	remaining: 35.8s
    3984:	learn: 65096.9118176	test: 114577.1088447	best: 114577.1088447 (3984)	total: 23.7s	remaining: 35.8s
    3985:	learn: 65091.3647179	test: 114576.4097492	best: 114576.4097492 (3985)	total: 23.7s	remaining: 35.8s
    3986:	learn: 65086.5497242	test: 114578.1562785	best: 114576.4097492 (3985)	total: 23.8s	remaining: 35.8s
    3987:	learn: 65080.7853473	test: 114575.4356029	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3988:	learn: 65077.5925265	test: 114575.8012093	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3989:	learn: 65075.5381097	test: 114578.0247763	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3990:	learn: 65071.5601401	test: 114581.5873204	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3991:	learn: 65068.1878369	test: 114583.4330866	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3992:	learn: 65062.7307421	test: 114580.1320571	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3993:	learn: 65059.3864160	test: 114579.0107100	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3994:	learn: 65053.9151117	test: 114577.5928146	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3995:	learn: 65048.6125879	test: 114577.1264913	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3996:	learn: 65045.8979938	test: 114579.4975287	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3997:	learn: 65041.2597371	test: 114582.9039878	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3998:	learn: 65035.8823734	test: 114584.7553095	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.8s
    3999:	learn: 65030.2034314	test: 114584.1586036	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.7s
    4000:	learn: 65027.3305541	test: 114585.3724643	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.7s
    4001:	learn: 65024.6410970	test: 114585.4436893	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.7s
    4002:	learn: 65019.8067031	test: 114583.5398698	best: 114575.4356029 (3987)	total: 23.8s	remaining: 35.7s
    4003:	learn: 65014.0464509	test: 114580.6438884	best: 114575.4356029 (3987)	total: 23.9s	remaining: 35.7s
    4004:	learn: 65007.8754547	test: 114580.3457339	best: 114575.4356029 (3987)	total: 23.9s	remaining: 35.7s
    4005:	learn: 65005.9829493	test: 114578.5297042	best: 114575.4356029 (3987)	total: 23.9s	remaining: 35.7s
    4006:	learn: 65001.2041084	test: 114576.8669833	best: 114575.4356029 (3987)	total: 23.9s	remaining: 35.7s
    4007:	learn: 64996.0987727	test: 114575.1361778	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4008:	learn: 64990.7362857	test: 114576.2278330	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4009:	learn: 64986.8276093	test: 114577.0993146	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4010:	learn: 64979.8206287	test: 114578.5579322	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4011:	learn: 64976.0580457	test: 114578.7553722	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4012:	learn: 64972.2023820	test: 114577.5597642	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4013:	learn: 64966.5232490	test: 114576.7958396	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4014:	learn: 64962.4252378	test: 114581.6497486	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.7s
    4015:	learn: 64959.8245997	test: 114579.3282549	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.6s
    4016:	learn: 64955.5750775	test: 114579.5569169	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.6s
    4017:	learn: 64950.8351469	test: 114579.8648424	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.6s
    4018:	learn: 64948.1368657	test: 114579.4947945	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.6s
    4019:	learn: 64940.8873612	test: 114577.4730811	best: 114575.1361778 (4007)	total: 23.9s	remaining: 35.6s
    4020:	learn: 64936.1061316	test: 114576.7024752	best: 114575.1361778 (4007)	total: 24s	remaining: 35.6s
    4021:	learn: 64929.1129366	test: 114575.0767604	best: 114575.0767604 (4021)	total: 24s	remaining: 35.6s
    4022:	learn: 64922.9850702	test: 114574.0525686	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4023:	learn: 64920.5577893	test: 114575.3695491	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4024:	learn: 64915.2599056	test: 114575.7941816	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4025:	learn: 64912.9522226	test: 114577.3185528	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4026:	learn: 64903.2169169	test: 114581.5319840	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4027:	learn: 64898.1308340	test: 114579.4921507	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4028:	learn: 64894.6845317	test: 114579.0319133	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4029:	learn: 64891.1671089	test: 114577.7201280	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4030:	learn: 64884.7104193	test: 114583.7202607	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4031:	learn: 64880.8255722	test: 114582.9027111	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4032:	learn: 64876.8503071	test: 114581.1103076	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4033:	learn: 64873.9760300	test: 114581.0053900	best: 114574.0525686 (4022)	total: 24s	remaining: 35.6s
    4034:	learn: 64869.0254530	test: 114580.1393070	best: 114574.0525686 (4022)	total: 24s	remaining: 35.5s
    4035:	learn: 64859.6785185	test: 114578.7212700	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4036:	learn: 64853.9897352	test: 114578.4083724	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4037:	learn: 64850.0039493	test: 114577.3700239	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4038:	learn: 64848.0045390	test: 114577.4383954	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4039:	learn: 64843.3259082	test: 114576.8707438	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4040:	learn: 64834.8356376	test: 114578.6863294	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4041:	learn: 64829.8505240	test: 114577.8385920	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4042:	learn: 64827.1357404	test: 114577.7017293	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4043:	learn: 64823.3517710	test: 114581.4095312	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4044:	learn: 64819.0596015	test: 114579.7042235	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4045:	learn: 64815.6108173	test: 114581.4523212	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4046:	learn: 64809.8535581	test: 114581.7556048	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4047:	learn: 64803.1473591	test: 114580.4097268	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4048:	learn: 64798.4493636	test: 114581.1946400	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4049:	learn: 64794.8464226	test: 114580.8676224	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4050:	learn: 64789.5458980	test: 114578.9781684	best: 114574.0525686 (4022)	total: 24.1s	remaining: 35.5s
    4051:	learn: 64786.5244265	test: 114580.7909693	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.5s
    4052:	learn: 64781.9154600	test: 114582.5923117	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.5s
    4053:	learn: 64777.6943038	test: 114582.1736403	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4054:	learn: 64772.5609398	test: 114583.0004560	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4055:	learn: 64766.7443869	test: 114584.4960061	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4056:	learn: 64762.2146526	test: 114580.2392565	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4057:	learn: 64758.9640364	test: 114579.4562867	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4058:	learn: 64748.0995732	test: 114577.6957711	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4059:	learn: 64744.1408778	test: 114578.1954657	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4060:	learn: 64741.6127036	test: 114578.9142148	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4061:	learn: 64735.4671941	test: 114578.6453546	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4062:	learn: 64731.9094072	test: 114579.3795294	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4063:	learn: 64729.0971438	test: 114579.8985395	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4064:	learn: 64724.1411761	test: 114577.5612737	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4065:	learn: 64717.7835772	test: 114577.1672345	best: 114574.0525686 (4022)	total: 24.2s	remaining: 35.4s
    4066:	learn: 64714.6656408	test: 114576.5588489	best: 114574.0525686 (4022)	total: 24.3s	remaining: 35.4s
    4067:	learn: 64710.6092848	test: 114574.3460294	best: 114574.0525686 (4022)	total: 24.3s	remaining: 35.4s
    4068:	learn: 64703.3258526	test: 114573.2797362	best: 114573.2797362 (4068)	total: 24.3s	remaining: 35.4s
    4069:	learn: 64697.8719695	test: 114570.6559293	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.4s
    4070:	learn: 64694.9871754	test: 114570.9423307	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.4s
    4071:	learn: 64690.6968502	test: 114571.1092491	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.4s
    4072:	learn: 64687.3331933	test: 114572.5768273	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.4s
    4073:	learn: 64684.3957211	test: 114571.4353538	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4074:	learn: 64677.4512846	test: 114572.6976438	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4075:	learn: 64673.0444641	test: 114571.6849770	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4076:	learn: 64667.5811335	test: 114572.3460136	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4077:	learn: 64663.3914091	test: 114574.2910067	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4078:	learn: 64657.5527370	test: 114576.4855495	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4079:	learn: 64652.9057064	test: 114577.0942752	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4080:	learn: 64648.3867712	test: 114574.6155522	best: 114570.6559293 (4069)	total: 24.3s	remaining: 35.3s
    4081:	learn: 64644.2946285	test: 114574.6634672	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4082:	learn: 64640.4211602	test: 114573.1661620	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4083:	learn: 64635.2982403	test: 114571.5311372	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4084:	learn: 64628.7071588	test: 114574.1552829	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4085:	learn: 64626.2349305	test: 114576.1779066	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4086:	learn: 64622.8340896	test: 114577.8512575	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4087:	learn: 64617.9246802	test: 114576.2962077	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4088:	learn: 64612.7899086	test: 114575.3743573	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4089:	learn: 64607.9417850	test: 114574.7848548	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4090:	learn: 64601.6739205	test: 114571.4881039	best: 114570.6559293 (4069)	total: 24.4s	remaining: 35.3s
    4091:	learn: 64598.4217972	test: 114569.9107415	best: 114569.9107415 (4091)	total: 24.4s	remaining: 35.2s
    4092:	learn: 64588.8562106	test: 114568.9009672	best: 114568.9009672 (4092)	total: 24.4s	remaining: 35.2s
    4093:	learn: 64585.7833377	test: 114568.8300119	best: 114568.8300119 (4093)	total: 24.4s	remaining: 35.2s
    4094:	learn: 64578.1797483	test: 114568.7084915	best: 114568.7084915 (4094)	total: 24.4s	remaining: 35.2s
    4095:	learn: 64573.2108314	test: 114566.2639387	best: 114566.2639387 (4095)	total: 24.4s	remaining: 35.2s
    4096:	learn: 64568.3221171	test: 114565.0129974	best: 114565.0129974 (4096)	total: 24.4s	remaining: 35.2s
    4097:	learn: 64564.0012215	test: 114561.0313767	best: 114561.0313767 (4097)	total: 24.4s	remaining: 35.2s
    4098:	learn: 64557.0594413	test: 114557.3176597	best: 114557.3176597 (4098)	total: 24.5s	remaining: 35.2s
    4099:	learn: 64553.5736000	test: 114557.6354424	best: 114557.3176597 (4098)	total: 24.5s	remaining: 35.2s
    4100:	learn: 64549.3271159	test: 114558.4942223	best: 114557.3176597 (4098)	total: 24.5s	remaining: 35.2s
    4101:	learn: 64546.8187290	test: 114557.1244609	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4102:	learn: 64541.2475026	test: 114558.3888132	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4103:	learn: 64537.4346179	test: 114558.0633373	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4104:	learn: 64532.4125921	test: 114557.9319610	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4105:	learn: 64528.6955710	test: 114557.5311940	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4106:	learn: 64524.9717796	test: 114558.0090631	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.2s
    4107:	learn: 64519.2052245	test: 114558.4280945	best: 114557.1244609 (4101)	total: 24.5s	remaining: 35.1s
    4108:	learn: 64514.9586138	test: 114555.7014220	best: 114555.7014220 (4108)	total: 24.5s	remaining: 35.1s
    4109:	learn: 64509.6596741	test: 114553.3572750	best: 114553.3572750 (4109)	total: 24.5s	remaining: 35.1s
    4110:	learn: 64506.3651346	test: 114552.6537409	best: 114552.6537409 (4110)	total: 24.5s	remaining: 35.1s
    4111:	learn: 64498.6399335	test: 114549.7410878	best: 114549.7410878 (4111)	total: 24.5s	remaining: 35.1s
    4112:	learn: 64495.5427436	test: 114547.0308528	best: 114547.0308528 (4112)	total: 24.5s	remaining: 35.1s
    4113:	learn: 64491.8265050	test: 114550.4753966	best: 114547.0308528 (4112)	total: 24.5s	remaining: 35.1s
    4114:	learn: 64486.3889835	test: 114549.9561576	best: 114547.0308528 (4112)	total: 24.5s	remaining: 35.1s
    4115:	learn: 64483.9176688	test: 114549.9218392	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4116:	learn: 64479.8635942	test: 114551.3494061	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4117:	learn: 64474.9765395	test: 114551.7576400	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4118:	learn: 64468.1271133	test: 114553.7146528	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4119:	learn: 64464.3428975	test: 114554.3832966	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4120:	learn: 64457.8693311	test: 114554.6392040	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4121:	learn: 64452.1071731	test: 114553.0692247	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4122:	learn: 64446.3018568	test: 114551.0093930	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35.1s
    4123:	learn: 64441.6165957	test: 114553.1114853	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4124:	learn: 64439.8667035	test: 114553.4431670	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4125:	learn: 64434.0919735	test: 114551.7821410	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4126:	learn: 64430.4369625	test: 114550.2731060	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4127:	learn: 64424.8320539	test: 114554.0936519	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4128:	learn: 64420.4920709	test: 114555.6436346	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4129:	learn: 64417.0305812	test: 114553.8030914	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4130:	learn: 64411.7331350	test: 114558.0785271	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4131:	learn: 64408.3389257	test: 114556.8508214	best: 114547.0308528 (4112)	total: 24.6s	remaining: 35s
    4132:	learn: 64401.4646387	test: 114555.6462742	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4133:	learn: 64396.8936550	test: 114555.3675269	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4134:	learn: 64393.8919620	test: 114555.1537021	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4135:	learn: 64390.7452277	test: 114555.7115604	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4136:	learn: 64386.5304829	test: 114557.6387180	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4137:	learn: 64382.2273089	test: 114557.0904830	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4138:	learn: 64375.1404468	test: 114560.6697980	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4139:	learn: 64371.6657128	test: 114559.4909258	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4140:	learn: 64369.1208394	test: 114558.5921729	best: 114547.0308528 (4112)	total: 24.7s	remaining: 35s
    4141:	learn: 64361.0353703	test: 114555.7571074	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4142:	learn: 64355.1600467	test: 114555.8666776	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4143:	learn: 64352.6098928	test: 114557.3285617	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4144:	learn: 64348.2713261	test: 114557.8924108	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4145:	learn: 64343.5629938	test: 114556.8941293	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4146:	learn: 64336.4921360	test: 114555.9447324	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4147:	learn: 64332.5043265	test: 114554.9522381	best: 114547.0308528 (4112)	total: 24.7s	remaining: 34.9s
    4148:	learn: 64326.9412800	test: 114549.8333481	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4149:	learn: 64322.0337661	test: 114550.3140069	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4150:	learn: 64313.5745207	test: 114553.1770111	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4151:	learn: 64306.7605485	test: 114556.5040892	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4152:	learn: 64299.2345704	test: 114553.3786176	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4153:	learn: 64294.6892469	test: 114554.6103315	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4154:	learn: 64289.6389126	test: 114556.6869330	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4155:	learn: 64286.1591652	test: 114555.5401123	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4156:	learn: 64280.7432175	test: 114558.5598820	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4157:	learn: 64278.1424281	test: 114557.2829896	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.9s
    4158:	learn: 64275.8282544	test: 114555.0827800	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4159:	learn: 64270.8696176	test: 114554.4305341	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4160:	learn: 64267.2681493	test: 114556.4994455	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4161:	learn: 64260.8102135	test: 114555.0490407	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4162:	learn: 64255.1322594	test: 114553.1360337	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4163:	learn: 64249.0827690	test: 114553.1055723	best: 114547.0308528 (4112)	total: 24.8s	remaining: 34.8s
    4164:	learn: 64247.5491084	test: 114549.8407336	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4165:	learn: 64241.0554126	test: 114550.3193967	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4166:	learn: 64232.6217313	test: 114549.7130777	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4167:	learn: 64228.3892055	test: 114549.8982913	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4168:	learn: 64222.0780784	test: 114553.8849239	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4169:	learn: 64217.4760877	test: 114552.2410289	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4170:	learn: 64214.0059607	test: 114550.6818175	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4171:	learn: 64210.7497302	test: 114551.2742020	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4172:	learn: 64207.7588992	test: 114549.7039811	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4173:	learn: 64203.1347024	test: 114550.1598763	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4174:	learn: 64198.9259063	test: 114548.0568463	best: 114547.0308528 (4112)	total: 24.9s	remaining: 34.8s
    4175:	learn: 64195.8962733	test: 114546.7000141	best: 114546.7000141 (4175)	total: 24.9s	remaining: 34.7s
    4176:	learn: 64190.9834728	test: 114545.0794971	best: 114545.0794971 (4176)	total: 24.9s	remaining: 34.7s
    4177:	learn: 64185.9148619	test: 114544.8329424	best: 114544.8329424 (4177)	total: 24.9s	remaining: 34.7s
    4178:	learn: 64181.1438091	test: 114547.6736000	best: 114544.8329424 (4177)	total: 24.9s	remaining: 34.7s
    4179:	learn: 64175.5014917	test: 114546.9777615	best: 114544.8329424 (4177)	total: 24.9s	remaining: 34.7s
    4180:	learn: 64168.7128466	test: 114550.6639883	best: 114544.8329424 (4177)	total: 24.9s	remaining: 34.7s
    4181:	learn: 64163.5454762	test: 114551.0423868	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4182:	learn: 64160.8171955	test: 114551.5195648	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4183:	learn: 64155.4332845	test: 114549.0052414	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4184:	learn: 64149.9915448	test: 114550.0900471	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4185:	learn: 64145.9668543	test: 114551.1738503	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4186:	learn: 64141.5150094	test: 114551.2705900	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4187:	learn: 64136.2791757	test: 114549.2853494	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4188:	learn: 64133.9531227	test: 114549.3682212	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4189:	learn: 64127.8866985	test: 114544.9916689	best: 114544.8329424 (4177)	total: 25s	remaining: 34.7s
    4190:	learn: 64120.4030167	test: 114542.5894260	best: 114542.5894260 (4190)	total: 25s	remaining: 34.7s
    4191:	learn: 64115.1991664	test: 114541.8364669	best: 114541.8364669 (4191)	total: 25s	remaining: 34.7s
    4192:	learn: 64108.3504453	test: 114542.0997329	best: 114541.8364669 (4191)	total: 25s	remaining: 34.7s
    4193:	learn: 64104.7064388	test: 114539.6611403	best: 114539.6611403 (4193)	total: 25s	remaining: 34.7s
    4194:	learn: 64098.9973023	test: 114536.4377668	best: 114536.4377668 (4194)	total: 25s	remaining: 34.7s
    4195:	learn: 64095.0070440	test: 114539.4203219	best: 114536.4377668 (4194)	total: 25s	remaining: 34.6s
    4196:	learn: 64090.7367623	test: 114538.4169260	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4197:	learn: 64084.4386868	test: 114540.7377681	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4198:	learn: 64079.4647715	test: 114541.2975295	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4199:	learn: 64073.7644488	test: 114540.6810002	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4200:	learn: 64068.6682317	test: 114540.4579347	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4201:	learn: 64064.4009173	test: 114538.3040865	best: 114536.4377668 (4194)	total: 25.1s	remaining: 34.6s
    4202:	learn: 64058.7004580	test: 114533.4186112	best: 114533.4186112 (4202)	total: 25.1s	remaining: 34.6s
    4203:	learn: 64053.0221405	test: 114534.8757788	best: 114533.4186112 (4202)	total: 25.1s	remaining: 34.6s
    4204:	learn: 64047.0367757	test: 114532.1866196	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4205:	learn: 64043.6979495	test: 114534.0997839	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4206:	learn: 64036.8954458	test: 114535.7194909	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4207:	learn: 64032.9762568	test: 114534.2532784	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4208:	learn: 64027.1097764	test: 114533.6481683	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4209:	learn: 64022.9218206	test: 114535.2392154	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4210:	learn: 64019.9058967	test: 114535.0474284	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4211:	learn: 64014.0992435	test: 114535.6687500	best: 114532.1866196 (4204)	total: 25.1s	remaining: 34.6s
    4212:	learn: 64010.7097743	test: 114536.3776619	best: 114532.1866196 (4204)	total: 25.2s	remaining: 34.6s
    4213:	learn: 64003.5918335	test: 114531.5954111	best: 114531.5954111 (4213)	total: 25.2s	remaining: 34.5s
    4214:	learn: 64001.7145588	test: 114531.7553997	best: 114531.5954111 (4213)	total: 25.2s	remaining: 34.5s
    4215:	learn: 63995.8754351	test: 114528.4018809	best: 114528.4018809 (4215)	total: 25.2s	remaining: 34.5s
    4216:	learn: 63991.6224836	test: 114527.5515795	best: 114527.5515795 (4216)	total: 25.2s	remaining: 34.5s
    4217:	learn: 63986.4130697	test: 114530.0817892	best: 114527.5515795 (4216)	total: 25.2s	remaining: 34.5s
    4218:	learn: 63979.7886922	test: 114529.7880172	best: 114527.5515795 (4216)	total: 25.2s	remaining: 34.5s
    4219:	learn: 63976.3969318	test: 114527.7430060	best: 114527.5515795 (4216)	total: 25.2s	remaining: 34.5s
    4220:	learn: 63970.7613766	test: 114526.5825418	best: 114526.5825418 (4220)	total: 25.2s	remaining: 34.5s
    4221:	learn: 63966.9648378	test: 114523.8488219	best: 114523.8488219 (4221)	total: 25.2s	remaining: 34.5s
    4222:	learn: 63963.6960291	test: 114522.6748726	best: 114522.6748726 (4222)	total: 25.2s	remaining: 34.5s
    4223:	learn: 63959.8384483	test: 114523.2027134	best: 114522.6748726 (4222)	total: 25.2s	remaining: 34.5s
    4224:	learn: 63956.0850206	test: 114524.1737991	best: 114522.6748726 (4222)	total: 25.2s	remaining: 34.5s
    4225:	learn: 63954.2092862	test: 114523.0407339	best: 114522.6748726 (4222)	total: 25.2s	remaining: 34.5s
    4226:	learn: 63949.6447453	test: 114522.5556745	best: 114522.5556745 (4226)	total: 25.3s	remaining: 34.5s
    4227:	learn: 63946.7011361	test: 114520.7725352	best: 114520.7725352 (4227)	total: 25.3s	remaining: 34.5s
    4228:	learn: 63938.9694933	test: 114515.3455173	best: 114515.3455173 (4228)	total: 25.3s	remaining: 34.5s
    4229:	learn: 63933.8117436	test: 114518.6462271	best: 114515.3455173 (4228)	total: 25.3s	remaining: 34.5s
    4230:	learn: 63928.9855950	test: 114517.3066860	best: 114515.3455173 (4228)	total: 25.3s	remaining: 34.5s
    4231:	learn: 63921.3467570	test: 114515.6538028	best: 114515.3455173 (4228)	total: 25.3s	remaining: 34.5s
    4232:	learn: 63918.3522461	test: 114514.0609638	best: 114514.0609638 (4232)	total: 25.3s	remaining: 34.5s
    4233:	learn: 63915.9055317	test: 114514.7117095	best: 114514.0609638 (4232)	total: 25.3s	remaining: 34.5s
    4234:	learn: 63915.7545838	test: 114514.5832980	best: 114514.0609638 (4232)	total: 25.3s	remaining: 34.4s
    4235:	learn: 63911.1217645	test: 114515.4870704	best: 114514.0609638 (4232)	total: 25.3s	remaining: 34.4s
    4236:	learn: 63907.9370746	test: 114514.5931488	best: 114514.0609638 (4232)	total: 25.3s	remaining: 34.4s
    4237:	learn: 63902.5796116	test: 114513.3356397	best: 114513.3356397 (4237)	total: 25.3s	remaining: 34.4s
    4238:	learn: 63899.1015180	test: 114510.4380365	best: 114510.4380365 (4238)	total: 25.3s	remaining: 34.4s
    4239:	learn: 63896.6225103	test: 114512.7745082	best: 114510.4380365 (4238)	total: 25.3s	remaining: 34.4s
    4240:	learn: 63893.9830016	test: 114515.7243761	best: 114510.4380365 (4238)	total: 25.3s	remaining: 34.4s
    4241:	learn: 63889.5343466	test: 114515.1802214	best: 114510.4380365 (4238)	total: 25.3s	remaining: 34.4s
    4242:	learn: 63882.8977462	test: 114514.9579052	best: 114510.4380365 (4238)	total: 25.4s	remaining: 34.4s
    4243:	learn: 63876.9623777	test: 114514.3378426	best: 114510.4380365 (4238)	total: 25.4s	remaining: 34.4s
    4244:	learn: 63862.6279048	test: 114503.3083375	best: 114503.3083375 (4244)	total: 25.4s	remaining: 34.4s
    4245:	learn: 63857.5960764	test: 114504.5588687	best: 114503.3083375 (4244)	total: 25.4s	remaining: 34.4s
    4246:	learn: 63853.9225767	test: 114503.4727862	best: 114503.3083375 (4244)	total: 25.4s	remaining: 34.4s
    4247:	learn: 63839.6469563	test: 114493.1553490	best: 114493.1553490 (4247)	total: 25.4s	remaining: 34.4s
    4248:	learn: 63834.6102881	test: 114492.5502924	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.4s
    4249:	learn: 63829.2476573	test: 114493.9965391	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.4s
    4250:	learn: 63824.1989797	test: 114498.0856285	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.4s
    4251:	learn: 63821.1219939	test: 114497.6854216	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.4s
    4252:	learn: 63818.4759797	test: 114498.4071643	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4253:	learn: 63814.5886925	test: 114500.0550244	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4254:	learn: 63810.5543426	test: 114498.7491078	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4255:	learn: 63804.8737418	test: 114498.6531166	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4256:	learn: 63800.0206903	test: 114501.6007518	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4257:	learn: 63796.5771940	test: 114501.5080923	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4258:	learn: 63792.4302648	test: 114500.2186056	best: 114492.5502924 (4248)	total: 25.4s	remaining: 34.3s
    4259:	learn: 63786.9629948	test: 114502.0345959	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4260:	learn: 63780.9850681	test: 114504.0384706	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4261:	learn: 63777.7662002	test: 114502.3302760	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4262:	learn: 63771.5687051	test: 114506.1189719	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4263:	learn: 63767.4256263	test: 114504.9009013	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4264:	learn: 63762.8114869	test: 114505.0175263	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4265:	learn: 63757.8662350	test: 114505.3047361	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4266:	learn: 63754.4365033	test: 114505.4454051	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4267:	learn: 63749.1342677	test: 114505.3215217	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.3s
    4268:	learn: 63744.0827102	test: 114509.8103434	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4269:	learn: 63739.1290009	test: 114511.1269130	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4270:	learn: 63735.6944172	test: 114512.5291884	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4271:	learn: 63733.9140856	test: 114512.6988758	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4272:	learn: 63729.0731785	test: 114509.8764192	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4273:	learn: 63726.8817237	test: 114511.1537620	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4274:	learn: 63721.8624705	test: 114515.5248192	best: 114492.5502924 (4248)	total: 25.5s	remaining: 34.2s
    4275:	learn: 63714.5515441	test: 114512.6253723	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4276:	learn: 63711.4663171	test: 114513.5689588	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4277:	learn: 63707.2912463	test: 114513.1940219	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4278:	learn: 63703.2726378	test: 114516.7052090	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4279:	learn: 63699.6683952	test: 114516.8443310	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4280:	learn: 63695.7087914	test: 114516.6205887	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4281:	learn: 63690.7431728	test: 114517.4896972	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4282:	learn: 63682.4156944	test: 114516.8537112	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4283:	learn: 63678.4617832	test: 114516.5631699	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4284:	learn: 63672.9172405	test: 114517.2991414	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.2s
    4285:	learn: 63669.6647963	test: 114516.5228081	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4286:	learn: 63665.6849387	test: 114515.3513843	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4287:	learn: 63661.4125008	test: 114514.9610571	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4288:	learn: 63653.9814233	test: 114514.8449748	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4289:	learn: 63650.3666329	test: 114512.7569662	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4290:	learn: 63647.3826944	test: 114513.7196684	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4291:	learn: 63642.9458306	test: 114512.5731231	best: 114492.5502924 (4248)	total: 25.6s	remaining: 34.1s
    4292:	learn: 63637.8176843	test: 114510.1912905	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4293:	learn: 63631.7894564	test: 114510.7032375	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4294:	learn: 63630.0614609	test: 114510.8502561	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4295:	learn: 63625.5296857	test: 114509.6833336	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4296:	learn: 63620.6808082	test: 114508.5327683	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4297:	learn: 63614.9753379	test: 114507.7361769	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4298:	learn: 63611.4644380	test: 114504.2650327	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4299:	learn: 63608.2883134	test: 114503.3840588	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4300:	learn: 63603.9826905	test: 114504.4245960	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4301:	learn: 63601.8658487	test: 114504.5410820	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34.1s
    4302:	learn: 63596.3204395	test: 114507.1703302	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4303:	learn: 63590.8588330	test: 114504.8570971	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4304:	learn: 63589.7000605	test: 114504.8564061	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4305:	learn: 63582.2482076	test: 114505.4303238	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4306:	learn: 63578.7595898	test: 114504.6996170	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4307:	learn: 63573.3644660	test: 114501.5501335	best: 114492.5502924 (4248)	total: 25.7s	remaining: 34s
    4308:	learn: 63570.4228649	test: 114501.0922772	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4309:	learn: 63561.7602403	test: 114498.9525675	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4310:	learn: 63556.6549191	test: 114498.7656813	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4311:	learn: 63554.9658035	test: 114498.9194662	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4312:	learn: 63552.4378227	test: 114499.3285656	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4313:	learn: 63543.1157107	test: 114502.8965307	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4314:	learn: 63538.1346642	test: 114500.2764944	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4315:	learn: 63536.8509735	test: 114498.9459216	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4316:	learn: 63532.8326824	test: 114497.2315376	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4317:	learn: 63527.3871508	test: 114495.8575656	best: 114492.5502924 (4248)	total: 25.8s	remaining: 34s
    4318:	learn: 63522.5519595	test: 114492.0284138	best: 114492.0284138 (4318)	total: 25.8s	remaining: 33.9s
    4319:	learn: 63515.4922908	test: 114491.5223545	best: 114491.5223545 (4319)	total: 25.8s	remaining: 33.9s
    4320:	learn: 63511.4605445	test: 114492.2956820	best: 114491.5223545 (4319)	total: 25.8s	remaining: 33.9s
    4321:	learn: 63505.4859789	test: 114491.0501599	best: 114491.0501599 (4321)	total: 25.8s	remaining: 33.9s
    4322:	learn: 63498.5927355	test: 114491.4836995	best: 114491.0501599 (4321)	total: 25.8s	remaining: 33.9s
    4323:	learn: 63493.7305272	test: 114491.2696873	best: 114491.0501599 (4321)	total: 25.8s	remaining: 33.9s
    4324:	learn: 63491.5709300	test: 114494.5143494	best: 114491.0501599 (4321)	total: 25.8s	remaining: 33.9s
    4325:	learn: 63486.5476908	test: 114493.1922963	best: 114491.0501599 (4321)	total: 25.8s	remaining: 33.9s
    4326:	learn: 63483.1827110	test: 114489.9384443	best: 114489.9384443 (4326)	total: 25.9s	remaining: 33.9s
    4327:	learn: 63479.4953745	test: 114488.2311257	best: 114488.2311257 (4327)	total: 25.9s	remaining: 33.9s
    4328:	learn: 63474.9275305	test: 114485.5147332	best: 114485.5147332 (4328)	total: 25.9s	remaining: 33.9s
    4329:	learn: 63469.3165933	test: 114484.8391658	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4330:	learn: 63463.8539511	test: 114485.6281371	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4331:	learn: 63459.2424618	test: 114486.7263491	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4332:	learn: 63453.6104794	test: 114491.1934725	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4333:	learn: 63450.3617426	test: 114494.5152927	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4334:	learn: 63447.9677222	test: 114494.6600218	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4335:	learn: 63441.0019207	test: 114494.8785843	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4336:	learn: 63439.1429530	test: 114494.0823013	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.9s
    4337:	learn: 63434.7875141	test: 114492.9709434	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.8s
    4338:	learn: 63430.8976392	test: 114496.2450456	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.8s
    4339:	learn: 63420.7860904	test: 114497.3035996	best: 114484.8391658 (4329)	total: 25.9s	remaining: 33.8s
    4340:	learn: 63416.4473194	test: 114496.8954850	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4341:	learn: 63413.4549107	test: 114499.4410058	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4342:	learn: 63407.8902194	test: 114495.4719077	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4343:	learn: 63401.0879417	test: 114494.2175059	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4344:	learn: 63393.7868290	test: 114492.2446288	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4345:	learn: 63392.1441186	test: 114492.4169619	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4346:	learn: 63388.9562010	test: 114492.4423788	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4347:	learn: 63386.7254852	test: 114495.0718640	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4348:	learn: 63384.6744942	test: 114495.4158803	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4349:	learn: 63382.5635079	test: 114495.5923371	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4350:	learn: 63380.7831544	test: 114495.5088376	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4351:	learn: 63379.0948633	test: 114495.1799353	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4352:	learn: 63374.9654886	test: 114494.6784482	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4353:	learn: 63370.9317652	test: 114493.0598795	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4354:	learn: 63367.4626050	test: 114493.5446771	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4355:	learn: 63360.8183481	test: 114492.3730829	best: 114484.8391658 (4329)	total: 26s	remaining: 33.8s
    4356:	learn: 63354.7088954	test: 114490.7332238	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4357:	learn: 63349.6391936	test: 114491.2129425	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4358:	learn: 63346.2378272	test: 114492.4754665	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4359:	learn: 63344.4948153	test: 114492.4006997	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4360:	learn: 63342.0627909	test: 114490.4739848	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4361:	learn: 63339.5199983	test: 114490.9608721	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4362:	learn: 63337.2692502	test: 114489.5989576	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4363:	learn: 63333.9356995	test: 114490.0976152	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4364:	learn: 63329.2413116	test: 114489.5720119	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4365:	learn: 63324.6028288	test: 114490.6537485	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4366:	learn: 63319.6228773	test: 114490.9177633	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4367:	learn: 63317.1491157	test: 114490.3780442	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4368:	learn: 63311.5540032	test: 114489.1033336	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4369:	learn: 63307.8614594	test: 114486.9371515	best: 114484.8391658 (4329)	total: 26.1s	remaining: 33.7s
    4370:	learn: 63300.8426258	test: 114484.2243065	best: 114484.2243065 (4370)	total: 26.1s	remaining: 33.7s
    4371:	learn: 63296.3032930	test: 114486.8583084	best: 114484.2243065 (4370)	total: 26.1s	remaining: 33.7s
    4372:	learn: 63294.1044208	test: 114485.1587359	best: 114484.2243065 (4370)	total: 26.2s	remaining: 33.7s
    4373:	learn: 63287.3017833	test: 114484.2551227	best: 114484.2243065 (4370)	total: 26.2s	remaining: 33.7s
    4374:	learn: 63283.1474150	test: 114484.1531589	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4375:	learn: 63278.2874697	test: 114486.5487885	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4376:	learn: 63272.8953766	test: 114485.2427962	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4377:	learn: 63267.3613480	test: 114486.4925821	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4378:	learn: 63263.0822320	test: 114484.6721751	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4379:	learn: 63259.8248944	test: 114485.3720729	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4380:	learn: 63256.3146112	test: 114484.6330632	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4381:	learn: 63252.5612904	test: 114484.9957028	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4382:	learn: 63250.0208856	test: 114484.7219445	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4383:	learn: 63242.6348172	test: 114485.1552051	best: 114484.1531589 (4374)	total: 26.2s	remaining: 33.6s
    4384:	learn: 63237.2890314	test: 114482.3652782	best: 114482.3652782 (4384)	total: 26.2s	remaining: 33.6s
    4385:	learn: 63228.2681556	test: 114486.1043567	best: 114482.3652782 (4384)	total: 26.2s	remaining: 33.6s
    4386:	learn: 63221.9155510	test: 114484.9230277	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4387:	learn: 63218.3098326	test: 114484.7056494	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4388:	learn: 63212.8273470	test: 114487.3794930	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4389:	learn: 63210.2775120	test: 114486.5737330	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4390:	learn: 63205.5122915	test: 114484.6471461	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4391:	learn: 63199.2302139	test: 114483.3981260	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4392:	learn: 63194.0846259	test: 114483.3995419	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.6s
    4393:	learn: 63190.7067085	test: 114485.1632816	best: 114482.3652782 (4384)	total: 26.3s	remaining: 33.5s
    4394:	learn: 63183.9445434	test: 114482.2125402	best: 114482.2125402 (4394)	total: 26.3s	remaining: 33.5s
    4395:	learn: 63181.0004739	test: 114484.9628176	best: 114482.2125402 (4394)	total: 26.3s	remaining: 33.5s
    4396:	learn: 63173.8690527	test: 114480.6229548	best: 114480.6229548 (4396)	total: 26.3s	remaining: 33.5s
    4397:	learn: 63169.1217346	test: 114479.6567948	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4398:	learn: 63165.4454646	test: 114483.2511970	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4399:	learn: 63156.7543586	test: 114483.3112754	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4400:	learn: 63149.0191809	test: 114483.7961626	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4401:	learn: 63145.7086469	test: 114483.0465731	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4402:	learn: 63144.4838062	test: 114484.2541970	best: 114479.6567948 (4397)	total: 26.3s	remaining: 33.5s
    4403:	learn: 63140.0208867	test: 114483.6607876	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4404:	learn: 63136.2736583	test: 114484.1390268	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4405:	learn: 63130.2566770	test: 114483.9217908	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4406:	learn: 63125.5947461	test: 114481.0650456	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4407:	learn: 63116.0678816	test: 114481.9204186	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4408:	learn: 63108.1982190	test: 114483.6792949	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4409:	learn: 63097.1672915	test: 114483.5071445	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.5s
    4410:	learn: 63091.7869642	test: 114480.6524233	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.4s
    4411:	learn: 63084.0423591	test: 114480.1767328	best: 114479.6567948 (4397)	total: 26.4s	remaining: 33.4s
    4412:	learn: 63081.0767941	test: 114478.5978554	best: 114478.5978554 (4412)	total: 26.4s	remaining: 33.4s
    4413:	learn: 63077.8013654	test: 114479.9416983	best: 114478.5978554 (4412)	total: 26.4s	remaining: 33.4s
    4414:	learn: 63072.5093041	test: 114475.3662864	best: 114475.3662864 (4414)	total: 26.4s	remaining: 33.4s
    4415:	learn: 63066.9481749	test: 114474.3627061	best: 114474.3627061 (4415)	total: 26.4s	remaining: 33.4s
    4416:	learn: 63063.5832981	test: 114475.0902791	best: 114474.3627061 (4415)	total: 26.4s	remaining: 33.4s
    4417:	learn: 63057.6439361	test: 114472.5597562	best: 114472.5597562 (4417)	total: 26.4s	remaining: 33.4s
    4418:	learn: 63051.4439042	test: 114471.5012343	best: 114471.5012343 (4418)	total: 26.4s	remaining: 33.4s
    4419:	learn: 63047.5804275	test: 114470.7863375	best: 114470.7863375 (4419)	total: 26.4s	remaining: 33.4s
    4420:	learn: 63041.5891792	test: 114469.1192694	best: 114469.1192694 (4420)	total: 26.5s	remaining: 33.4s
    4421:	learn: 63036.2721896	test: 114467.8045694	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.4s
    4422:	learn: 63029.4980254	test: 114469.1584287	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.4s
    4423:	learn: 63024.0585481	test: 114470.0043119	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.4s
    4424:	learn: 63023.1307784	test: 114469.5476288	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.4s
    4425:	learn: 63020.9177294	test: 114467.9715372	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.4s
    4426:	learn: 63016.8521976	test: 114467.9392111	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.3s
    4427:	learn: 63013.8786954	test: 114468.5263612	best: 114467.8045694 (4421)	total: 26.5s	remaining: 33.3s
    4428:	learn: 63009.0307941	test: 114464.8938597	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4429:	learn: 63003.8752210	test: 114465.1228446	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4430:	learn: 62994.9262214	test: 114466.7239805	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4431:	learn: 62990.1950631	test: 114470.7025297	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4432:	learn: 62982.9619997	test: 114468.6312796	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4433:	learn: 62979.5742717	test: 114467.6392685	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4434:	learn: 62970.6766458	test: 114472.1707311	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4435:	learn: 62964.2526489	test: 114469.8337375	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4436:	learn: 62961.0639880	test: 114469.6022867	best: 114464.8938597 (4428)	total: 26.5s	remaining: 33.3s
    4437:	learn: 62959.5257393	test: 114469.7793146	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4438:	learn: 62952.1523874	test: 114467.8275190	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4439:	learn: 62945.6496589	test: 114468.5087485	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4440:	learn: 62940.6113435	test: 114471.4180852	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4441:	learn: 62938.0994886	test: 114471.0527657	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4442:	learn: 62933.7301026	test: 114470.9416436	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.3s
    4443:	learn: 62930.7397452	test: 114472.3851533	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4444:	learn: 62925.4902641	test: 114469.0978495	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4445:	learn: 62919.6168264	test: 114467.3130667	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4446:	learn: 62914.6344608	test: 114465.8734044	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4447:	learn: 62909.6425924	test: 114464.9596759	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4448:	learn: 62904.0574227	test: 114467.9868413	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4449:	learn: 62900.0419859	test: 114468.6439558	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4450:	learn: 62895.5345024	test: 114467.1531907	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4451:	learn: 62889.0043960	test: 114466.1278049	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4452:	learn: 62887.2976479	test: 114465.7516324	best: 114464.8938597 (4428)	total: 26.6s	remaining: 33.2s
    4453:	learn: 62884.9507914	test: 114465.0075503	best: 114464.8938597 (4428)	total: 26.7s	remaining: 33.2s
    4454:	learn: 62882.8650978	test: 114462.7378579	best: 114462.7378579 (4454)	total: 26.7s	remaining: 33.2s
    4455:	learn: 62876.4014766	test: 114459.7724982	best: 114459.7724982 (4455)	total: 26.7s	remaining: 33.2s
    4456:	learn: 62871.4474676	test: 114459.0094195	best: 114459.0094195 (4456)	total: 26.7s	remaining: 33.2s
    4457:	learn: 62863.7055632	test: 114453.8720968	best: 114453.8720968 (4457)	total: 26.7s	remaining: 33.2s
    4458:	learn: 62860.6527529	test: 114453.8008351	best: 114453.8008351 (4458)	total: 26.7s	remaining: 33.2s
    4459:	learn: 62855.0783034	test: 114455.2356087	best: 114453.8008351 (4458)	total: 26.7s	remaining: 33.1s
    4460:	learn: 62852.0295014	test: 114451.6162309	best: 114451.6162309 (4460)	total: 26.7s	remaining: 33.1s
    4461:	learn: 62848.5296915	test: 114448.2849057	best: 114448.2849057 (4461)	total: 26.7s	remaining: 33.1s
    4462:	learn: 62842.3162916	test: 114446.5709389	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4463:	learn: 62836.0701637	test: 114447.8087867	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4464:	learn: 62830.4414578	test: 114447.3700996	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4465:	learn: 62826.0707095	test: 114448.8247770	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4466:	learn: 62817.6430540	test: 114452.4052994	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4467:	learn: 62813.9784508	test: 114449.3571271	best: 114446.5709389 (4462)	total: 26.7s	remaining: 33.1s
    4468:	learn: 62808.9441193	test: 114446.1707127	best: 114446.1707127 (4468)	total: 26.7s	remaining: 33.1s
    4469:	learn: 62804.8924358	test: 114447.2536706	best: 114446.1707127 (4468)	total: 26.7s	remaining: 33.1s
    4470:	learn: 62797.6760500	test: 114447.7873649	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4471:	learn: 62794.5110308	test: 114449.2772760	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4472:	learn: 62789.2988727	test: 114448.3902182	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4473:	learn: 62786.8849131	test: 114448.7778954	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4474:	learn: 62782.3231868	test: 114448.9568642	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4475:	learn: 62779.6033060	test: 114447.8257768	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33.1s
    4476:	learn: 62776.8707258	test: 114449.7762125	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4477:	learn: 62773.4501874	test: 114452.6305946	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4478:	learn: 62770.4393688	test: 114452.5120131	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4479:	learn: 62767.4795347	test: 114450.3411328	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4480:	learn: 62762.6773945	test: 114449.3601587	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4481:	learn: 62759.0812621	test: 114448.5751001	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4482:	learn: 62754.4799484	test: 114449.9365486	best: 114446.1707127 (4468)	total: 26.8s	remaining: 33s
    4483:	learn: 62747.1266538	test: 114444.8364828	best: 114444.8364828 (4483)	total: 26.8s	remaining: 33s
    4484:	learn: 62740.5734624	test: 114443.3051111	best: 114443.3051111 (4484)	total: 26.8s	remaining: 33s
    4485:	learn: 62734.5663729	test: 114445.9570333	best: 114443.3051111 (4484)	total: 26.8s	remaining: 33s
    4486:	learn: 62733.1458968	test: 114445.3102137	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4487:	learn: 62727.8169955	test: 114447.8651349	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4488:	learn: 62724.0055295	test: 114448.6717390	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4489:	learn: 62719.6755955	test: 114446.8433237	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4490:	learn: 62715.7057129	test: 114446.2570179	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4491:	learn: 62711.5856607	test: 114446.3146179	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4492:	learn: 62705.9244179	test: 114446.0529109	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4493:	learn: 62699.7757176	test: 114450.1732856	best: 114443.3051111 (4484)	total: 26.9s	remaining: 33s
    4494:	learn: 62697.0263711	test: 114449.6266144	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4495:	learn: 62690.2117072	test: 114448.2112316	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4496:	learn: 62686.0784917	test: 114454.4195127	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4497:	learn: 62680.9920124	test: 114452.4159968	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4498:	learn: 62677.3884989	test: 114452.3421892	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4499:	learn: 62670.9945583	test: 114453.2547160	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4500:	learn: 62669.5553194	test: 114453.9268518	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4501:	learn: 62664.2687341	test: 114453.9114933	best: 114443.3051111 (4484)	total: 26.9s	remaining: 32.9s
    4502:	learn: 62658.3480825	test: 114451.6754141	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4503:	learn: 62650.0275497	test: 114450.8957538	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4504:	learn: 62647.5577481	test: 114451.0558053	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4505:	learn: 62646.4399827	test: 114450.0430670	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4506:	learn: 62639.4012514	test: 114450.3193461	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4507:	learn: 62635.2196841	test: 114450.4454774	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4508:	learn: 62631.8462111	test: 114449.3707797	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4509:	learn: 62627.3203106	test: 114447.0794680	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4510:	learn: 62623.0868823	test: 114449.5894299	best: 114443.3051111 (4484)	total: 27s	remaining: 32.9s
    4511:	learn: 62615.4282246	test: 114455.0075987	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4512:	learn: 62610.7865792	test: 114455.9519283	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4513:	learn: 62607.7937718	test: 114455.2967704	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4514:	learn: 62599.8817615	test: 114456.0155725	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4515:	learn: 62597.1335517	test: 114458.8769116	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4516:	learn: 62590.9657780	test: 114462.7781234	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4517:	learn: 62587.6997216	test: 114462.5549516	best: 114443.3051111 (4484)	total: 27s	remaining: 32.8s
    4518:	learn: 62584.6446496	test: 114464.8240668	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4519:	learn: 62581.6632675	test: 114466.9085883	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4520:	learn: 62577.8788545	test: 114466.4372722	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4521:	learn: 62571.8306893	test: 114465.6017871	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4522:	learn: 62567.8182869	test: 114465.8764410	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4523:	learn: 62565.3919736	test: 114464.7842786	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4524:	learn: 62557.9534822	test: 114465.0112326	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4525:	learn: 62553.3176343	test: 114466.3795230	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4526:	learn: 62549.7048323	test: 114463.9503575	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4527:	learn: 62543.2258669	test: 114465.1134038	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4528:	learn: 62540.3949791	test: 114465.5985348	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4529:	learn: 62534.8925293	test: 114466.1448725	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4530:	learn: 62531.8444404	test: 114465.9217882	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4531:	learn: 62528.4810358	test: 114466.0351376	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.8s
    4532:	learn: 62525.4558630	test: 114469.1804173	best: 114443.3051111 (4484)	total: 27.1s	remaining: 32.7s
    4533:	learn: 62520.5987412	test: 114471.2989140	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4534:	learn: 62515.6034741	test: 114474.5910874	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4535:	learn: 62511.4082095	test: 114472.2677592	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4536:	learn: 62507.5705422	test: 114471.2795014	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4537:	learn: 62503.0160475	test: 114472.0092988	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4538:	learn: 62496.3986663	test: 114471.4344779	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4539:	learn: 62491.5679247	test: 114471.1167582	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4540:	learn: 62486.7247543	test: 114464.3187867	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4541:	learn: 62481.2615698	test: 114465.2148236	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4542:	learn: 62477.0391807	test: 114466.1004831	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4543:	learn: 62471.0175166	test: 114465.3054183	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4544:	learn: 62465.3089367	test: 114465.5837839	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4545:	learn: 62459.9538063	test: 114461.7766036	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4546:	learn: 62455.9081611	test: 114464.6022127	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4547:	learn: 62446.9256350	test: 114467.3616994	best: 114443.3051111 (4484)	total: 27.2s	remaining: 32.7s
    4548:	learn: 62442.5415183	test: 114466.6633231	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.7s
    4549:	learn: 62439.4484377	test: 114466.2067510	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4550:	learn: 62434.9623341	test: 114466.4856681	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4551:	learn: 62431.0011326	test: 114465.4443914	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4552:	learn: 62427.3747361	test: 114461.9369270	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4553:	learn: 62422.3088198	test: 114460.5640516	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4554:	learn: 62419.0647139	test: 114459.3722740	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4555:	learn: 62408.2904162	test: 114459.7766080	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4556:	learn: 62402.2885539	test: 114457.8768781	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4557:	learn: 62399.3111246	test: 114458.5665971	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4558:	learn: 62394.4511255	test: 114454.9702063	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4559:	learn: 62391.7379589	test: 114454.3337974	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4560:	learn: 62385.3822087	test: 114455.9471478	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4561:	learn: 62380.3786698	test: 114454.8245549	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4562:	learn: 62376.1244438	test: 114456.3500065	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4563:	learn: 62372.2728886	test: 114455.3528959	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4564:	learn: 62367.2865510	test: 114454.2955764	best: 114443.3051111 (4484)	total: 27.3s	remaining: 32.6s
    4565:	learn: 62362.8290500	test: 114454.3942005	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.6s
    4566:	learn: 62361.1662240	test: 114454.4442575	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4567:	learn: 62357.2787377	test: 114452.4257746	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4568:	learn: 62353.0344433	test: 114451.9452496	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4569:	learn: 62346.6635070	test: 114451.1606798	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4570:	learn: 62342.0411753	test: 114451.8383364	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4571:	learn: 62336.9980065	test: 114451.7627460	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4572:	learn: 62332.0617727	test: 114454.5440882	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4573:	learn: 62327.9022515	test: 114455.3184562	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4574:	learn: 62326.4916722	test: 114455.4326181	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4575:	learn: 62321.4935890	test: 114455.3344465	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4576:	learn: 62318.0495744	test: 114452.6357007	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4577:	learn: 62314.4583967	test: 114455.1973544	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4578:	learn: 62309.6123276	test: 114452.3652600	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4579:	learn: 62306.3986472	test: 114454.3737016	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4580:	learn: 62301.1231337	test: 114454.9207857	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4581:	learn: 62296.8026725	test: 114453.2855429	best: 114443.3051111 (4484)	total: 27.4s	remaining: 32.5s
    4582:	learn: 62290.9552062	test: 114452.9310244	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.5s
    4583:	learn: 62290.7755368	test: 114453.4148425	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4584:	learn: 62287.0490988	test: 114454.6389478	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4585:	learn: 62284.2595307	test: 114455.3652248	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4586:	learn: 62275.2358588	test: 114454.4607697	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4587:	learn: 62271.3292165	test: 114454.7332667	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4588:	learn: 62263.3601752	test: 114453.9328658	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4589:	learn: 62261.6938006	test: 114454.3011739	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4590:	learn: 62258.6284642	test: 114455.6398329	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4591:	learn: 62253.1205182	test: 114453.8612545	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4592:	learn: 62245.4220814	test: 114453.1560503	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4593:	learn: 62242.5834576	test: 114454.3749338	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4594:	learn: 62237.6691948	test: 114456.1960222	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4595:	learn: 62231.0311341	test: 114456.9952687	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4596:	learn: 62227.7700196	test: 114456.4112189	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4597:	learn: 62223.4851529	test: 114454.3852807	best: 114443.3051111 (4484)	total: 27.5s	remaining: 32.4s
    4598:	learn: 62215.0491063	test: 114455.8603082	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.4s
    4599:	learn: 62208.0704992	test: 114454.3354865	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4600:	learn: 62203.1239306	test: 114455.8611614	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4601:	learn: 62200.0804661	test: 114455.7395390	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4602:	learn: 62195.1585618	test: 114459.7072712	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4603:	learn: 62192.5356795	test: 114458.0319810	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4604:	learn: 62187.3721231	test: 114455.9099707	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4605:	learn: 62182.1194554	test: 114454.2022202	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4606:	learn: 62177.5717594	test: 114452.3629166	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4607:	learn: 62175.1102809	test: 114452.0650490	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4608:	learn: 62172.2904773	test: 114452.9331889	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4609:	learn: 62169.4042338	test: 114449.4467164	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4610:	learn: 62163.7266437	test: 114448.1431990	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4611:	learn: 62162.4182559	test: 114447.5109080	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4612:	learn: 62159.9958504	test: 114447.4190654	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4613:	learn: 62159.6914709	test: 114447.0928471	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4614:	learn: 62156.7845165	test: 114446.6934299	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4615:	learn: 62153.1527596	test: 114447.1823114	best: 114443.3051111 (4484)	total: 27.6s	remaining: 32.3s
    4616:	learn: 62150.5967390	test: 114447.2139608	best: 114443.3051111 (4484)	total: 27.7s	remaining: 32.2s
    4617:	learn: 62142.4911234	test: 114443.1415574	best: 114443.1415574 (4617)	total: 27.7s	remaining: 32.2s
    4618:	learn: 62138.3066950	test: 114445.0002576	best: 114443.1415574 (4617)	total: 27.7s	remaining: 32.2s
    4619:	learn: 62134.9730814	test: 114442.7022489	best: 114442.7022489 (4619)	total: 27.7s	remaining: 32.2s
    4620:	learn: 62129.5374017	test: 114441.1891074	best: 114441.1891074 (4620)	total: 27.7s	remaining: 32.2s
    4621:	learn: 62128.3893942	test: 114440.7547638	best: 114440.7547638 (4621)	total: 27.7s	remaining: 32.2s
    4622:	learn: 62124.6237768	test: 114442.6157120	best: 114440.7547638 (4621)	total: 27.7s	remaining: 32.2s
    4623:	learn: 62118.4301048	test: 114441.6440618	best: 114440.7547638 (4621)	total: 27.7s	remaining: 32.2s
    4624:	learn: 62115.0004877	test: 114442.1888413	best: 114440.7547638 (4621)	total: 27.7s	remaining: 32.2s
    4625:	learn: 62110.4642399	test: 114438.7393637	best: 114438.7393637 (4625)	total: 27.7s	remaining: 32.2s
    4626:	learn: 62109.4698524	test: 114438.6733636	best: 114438.6733636 (4626)	total: 27.7s	remaining: 32.2s
    4627:	learn: 62106.4728807	test: 114439.5520296	best: 114438.6733636 (4626)	total: 27.7s	remaining: 32.2s
    4628:	learn: 62104.5215504	test: 114436.4860551	best: 114436.4860551 (4628)	total: 27.7s	remaining: 32.2s
    4629:	learn: 62102.0852461	test: 114436.0510886	best: 114436.0510886 (4629)	total: 27.7s	remaining: 32.2s
    4630:	learn: 62095.6304828	test: 114436.9321252	best: 114436.0510886 (4629)	total: 27.7s	remaining: 32.2s
    4631:	learn: 62093.2008766	test: 114436.9780581	best: 114436.0510886 (4629)	total: 27.7s	remaining: 32.1s
    4632:	learn: 62087.8743952	test: 114437.5834900	best: 114436.0510886 (4629)	total: 27.7s	remaining: 32.1s
    4633:	learn: 62083.4354753	test: 114437.3168184	best: 114436.0510886 (4629)	total: 27.8s	remaining: 32.1s
    4634:	learn: 62078.5656919	test: 114437.3892011	best: 114436.0510886 (4629)	total: 27.8s	remaining: 32.1s
    4635:	learn: 62073.5096470	test: 114436.8940744	best: 114436.0510886 (4629)	total: 27.8s	remaining: 32.1s
    4636:	learn: 62071.4837527	test: 114435.7776623	best: 114435.7776623 (4636)	total: 27.8s	remaining: 32.1s
    4637:	learn: 62065.8388524	test: 114435.6047418	best: 114435.6047418 (4637)	total: 27.8s	remaining: 32.1s
    4638:	learn: 62062.9555578	test: 114435.7312165	best: 114435.6047418 (4637)	total: 27.8s	remaining: 32.1s
    4639:	learn: 62057.2451233	test: 114436.2595628	best: 114435.6047418 (4637)	total: 27.8s	remaining: 32.1s
    4640:	learn: 62052.0101089	test: 114437.1938110	best: 114435.6047418 (4637)	total: 27.8s	remaining: 32.1s
    4641:	learn: 62043.9194854	test: 114436.2040315	best: 114435.6047418 (4637)	total: 27.8s	remaining: 32.1s
    4642:	learn: 62041.0428478	test: 114433.1480169	best: 114433.1480169 (4642)	total: 27.8s	remaining: 32.1s
    4643:	learn: 62035.9936530	test: 114432.5342881	best: 114432.5342881 (4643)	total: 27.8s	remaining: 32.1s
    4644:	learn: 62029.9145513	test: 114431.7040518	best: 114431.7040518 (4644)	total: 27.8s	remaining: 32.1s
    4645:	learn: 62026.4718106	test: 114430.6874963	best: 114430.6874963 (4645)	total: 27.8s	remaining: 32.1s
    4646:	learn: 62020.7908282	test: 114429.2706641	best: 114429.2706641 (4646)	total: 27.8s	remaining: 32.1s
    4647:	learn: 62017.1592849	test: 114429.1212387	best: 114429.1212387 (4647)	total: 27.8s	remaining: 32.1s
    4648:	learn: 62012.9329474	test: 114427.6924365	best: 114427.6924365 (4648)	total: 27.9s	remaining: 32.1s
    4649:	learn: 62008.7668702	test: 114427.6423314	best: 114427.6423314 (4649)	total: 27.9s	remaining: 32.1s
    4650:	learn: 62005.5314491	test: 114426.3944015	best: 114426.3944015 (4650)	total: 27.9s	remaining: 32s
    4651:	learn: 62004.3054234	test: 114426.2078672	best: 114426.2078672 (4651)	total: 27.9s	remaining: 32s
    4652:	learn: 61998.8585322	test: 114424.8297841	best: 114424.8297841 (4652)	total: 27.9s	remaining: 32s
    4653:	learn: 61996.1321022	test: 114425.4202034	best: 114424.8297841 (4652)	total: 27.9s	remaining: 32s
    4654:	learn: 61989.0980856	test: 114425.6313424	best: 114424.8297841 (4652)	total: 27.9s	remaining: 32s
    4655:	learn: 61985.3024170	test: 114425.6211341	best: 114424.8297841 (4652)	total: 27.9s	remaining: 32s
    4656:	learn: 61979.3907550	test: 114424.6359461	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4657:	learn: 61973.8453434	test: 114424.6647998	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4658:	learn: 61968.6282179	test: 114425.2724789	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4659:	learn: 61962.6020876	test: 114428.2908178	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4660:	learn: 61959.0406572	test: 114431.5574981	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4661:	learn: 61955.9889735	test: 114430.1275424	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4662:	learn: 61950.4490691	test: 114427.3509987	best: 114424.6359461 (4656)	total: 27.9s	remaining: 32s
    4663:	learn: 61941.9851163	test: 114425.6951687	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4664:	learn: 61939.6529039	test: 114426.1578345	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4665:	learn: 61934.0102727	test: 114430.7820358	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4666:	learn: 61928.7159425	test: 114430.5359839	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4667:	learn: 61924.8158877	test: 114426.5719376	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4668:	learn: 61919.5906104	test: 114426.2949809	best: 114424.6359461 (4656)	total: 28s	remaining: 32s
    4669:	learn: 61915.1305128	test: 114424.2481298	best: 114424.2481298 (4669)	total: 28s	remaining: 32s
    4670:	learn: 61909.1948362	test: 114421.0998382	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4671:	learn: 61905.1199255	test: 114422.2751903	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4672:	learn: 61900.1505193	test: 114423.7692024	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4673:	learn: 61897.0627583	test: 114425.0709293	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4674:	learn: 61891.4695037	test: 114424.9775249	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4675:	learn: 61886.9477519	test: 114426.6590215	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4676:	learn: 61884.2827213	test: 114429.0327007	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4677:	learn: 61879.2261111	test: 114428.6261467	best: 114421.0998382 (4670)	total: 28s	remaining: 31.9s
    4678:	learn: 61875.8606370	test: 114428.4885267	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4679:	learn: 61874.8570437	test: 114428.4690471	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4680:	learn: 61867.3873742	test: 114429.0798384	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4681:	learn: 61864.9527400	test: 114427.7205987	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4682:	learn: 61859.3920866	test: 114427.4523151	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4683:	learn: 61852.7414992	test: 114423.3666302	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4684:	learn: 61849.9310555	test: 114423.4912565	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4685:	learn: 61845.3647935	test: 114424.9046074	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4686:	learn: 61840.7346924	test: 114424.7249678	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4687:	learn: 61834.6862349	test: 114422.5872881	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4688:	learn: 61831.3794338	test: 114421.6106265	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.9s
    4689:	learn: 61827.5745681	test: 114421.6495282	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.8s
    4690:	learn: 61826.2050631	test: 114421.9053858	best: 114421.0998382 (4670)	total: 28.1s	remaining: 31.8s
    4691:	learn: 61821.8460487	test: 114420.3089497	best: 114420.3089497 (4691)	total: 28.1s	remaining: 31.8s
    4692:	learn: 61813.6262122	test: 114417.3960544	best: 114417.3960544 (4692)	total: 28.1s	remaining: 31.8s
    4693:	learn: 61811.2117587	test: 114418.6461364	best: 114417.3960544 (4692)	total: 28.2s	remaining: 31.8s
    4694:	learn: 61800.7670463	test: 114410.5095398	best: 114410.5095398 (4694)	total: 28.2s	remaining: 31.8s
    4695:	learn: 61795.7073778	test: 114411.0974987	best: 114410.5095398 (4694)	total: 28.2s	remaining: 31.8s
    4696:	learn: 61791.2074627	test: 114411.8465897	best: 114410.5095398 (4694)	total: 28.2s	remaining: 31.8s
    4697:	learn: 61785.5790398	test: 114410.1085115	best: 114410.1085115 (4697)	total: 28.2s	remaining: 31.8s
    4698:	learn: 61781.4624726	test: 114408.7995544	best: 114408.7995544 (4698)	total: 28.2s	remaining: 31.8s
    4699:	learn: 61777.8781814	test: 114407.8706031	best: 114407.8706031 (4699)	total: 28.2s	remaining: 31.8s
    4700:	learn: 61773.3474057	test: 114405.5865360	best: 114405.5865360 (4700)	total: 28.2s	remaining: 31.8s
    4701:	learn: 61770.4531241	test: 114405.4281303	best: 114405.4281303 (4701)	total: 28.2s	remaining: 31.8s
    4702:	learn: 61765.3625116	test: 114404.7532514	best: 114404.7532514 (4702)	total: 28.2s	remaining: 31.8s
    4703:	learn: 61759.5373329	test: 114402.0490491	best: 114402.0490491 (4703)	total: 28.2s	remaining: 31.8s
    4704:	learn: 61754.8221562	test: 114401.1933687	best: 114401.1933687 (4704)	total: 28.2s	remaining: 31.8s
    4705:	learn: 61748.9229933	test: 114395.1359468	best: 114395.1359468 (4705)	total: 28.2s	remaining: 31.8s
    4706:	learn: 61742.6263104	test: 114392.3035164	best: 114392.3035164 (4706)	total: 28.2s	remaining: 31.7s
    4707:	learn: 61736.9746343	test: 114390.5884362	best: 114390.5884362 (4707)	total: 28.2s	remaining: 31.7s
    4708:	learn: 61729.7025758	test: 114390.0127559	best: 114390.0127559 (4708)	total: 28.2s	remaining: 31.7s
    4709:	learn: 61726.2733195	test: 114391.3322248	best: 114390.0127559 (4708)	total: 28.2s	remaining: 31.7s
    4710:	learn: 61722.2792085	test: 114392.5482271	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4711:	learn: 61718.7281519	test: 114395.7155975	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4712:	learn: 61714.5234248	test: 114395.4716782	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4713:	learn: 61711.5696573	test: 114395.0543883	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4714:	learn: 61707.8323136	test: 114394.2945875	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4715:	learn: 61703.0067110	test: 114391.8975566	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4716:	learn: 61699.4604425	test: 114390.5652868	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4717:	learn: 61693.0963803	test: 114390.7663284	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4718:	learn: 61689.7477185	test: 114392.2632014	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4719:	learn: 61686.2895944	test: 114392.8091570	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4720:	learn: 61683.2726848	test: 114393.1905524	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4721:	learn: 61679.8716355	test: 114393.6688407	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4722:	learn: 61675.2079512	test: 114392.6496534	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.7s
    4723:	learn: 61669.4391440	test: 114393.7062207	best: 114390.0127559 (4708)	total: 28.3s	remaining: 31.6s
    4724:	learn: 61663.3142531	test: 114389.2558738	best: 114389.2558738 (4724)	total: 28.3s	remaining: 31.6s
    4725:	learn: 61657.2657338	test: 114387.1914116	best: 114387.1914116 (4725)	total: 28.3s	remaining: 31.6s
    4726:	learn: 61651.5691788	test: 114388.5029800	best: 114387.1914116 (4725)	total: 28.4s	remaining: 31.6s
    4727:	learn: 61647.0414373	test: 114383.1971388	best: 114383.1971388 (4727)	total: 28.4s	remaining: 31.6s
    4728:	learn: 61642.6846443	test: 114385.3924436	best: 114383.1971388 (4727)	total: 28.4s	remaining: 31.6s
    4729:	learn: 61638.5742468	test: 114387.7191647	best: 114383.1971388 (4727)	total: 28.4s	remaining: 31.6s
    4730:	learn: 61634.1839525	test: 114385.6434276	best: 114383.1971388 (4727)	total: 28.4s	remaining: 31.6s
    4731:	learn: 61628.8140956	test: 114386.6332050	best: 114383.1971388 (4727)	total: 28.4s	remaining: 31.6s
    4732:	learn: 61623.6670961	test: 114383.1627066	best: 114383.1627066 (4732)	total: 28.4s	remaining: 31.6s
    4733:	learn: 61617.6424579	test: 114382.7675108	best: 114382.7675108 (4733)	total: 28.4s	remaining: 31.6s
    4734:	learn: 61611.1018188	test: 114381.4619390	best: 114381.4619390 (4734)	total: 28.4s	remaining: 31.6s
    4735:	learn: 61608.3640110	test: 114381.3700337	best: 114381.3700337 (4735)	total: 28.4s	remaining: 31.6s
    4736:	learn: 61606.3755725	test: 114383.0555969	best: 114381.3700337 (4735)	total: 28.4s	remaining: 31.6s
    4737:	learn: 61600.5768459	test: 114383.9711453	best: 114381.3700337 (4735)	total: 28.4s	remaining: 31.6s
    4738:	learn: 61596.2636320	test: 114382.0918221	best: 114381.3700337 (4735)	total: 28.4s	remaining: 31.6s
    4739:	learn: 61592.3652786	test: 114377.5095048	best: 114377.5095048 (4739)	total: 28.4s	remaining: 31.6s
    4740:	learn: 61590.2850150	test: 114377.5898160	best: 114377.5095048 (4739)	total: 28.4s	remaining: 31.5s
    4741:	learn: 61586.3790270	test: 114377.3820389	best: 114377.3820389 (4741)	total: 28.4s	remaining: 31.5s
    4742:	learn: 61581.7455011	test: 114376.9822403	best: 114376.9822403 (4742)	total: 28.5s	remaining: 31.5s
    4743:	learn: 61577.6483832	test: 114377.0725504	best: 114376.9822403 (4742)	total: 28.5s	remaining: 31.5s
    4744:	learn: 61572.7237576	test: 114375.7093960	best: 114375.7093960 (4744)	total: 28.5s	remaining: 31.5s
    4745:	learn: 61570.2276888	test: 114377.6629156	best: 114375.7093960 (4744)	total: 28.5s	remaining: 31.5s
    4746:	learn: 61564.6606958	test: 114378.5505025	best: 114375.7093960 (4744)	total: 28.5s	remaining: 31.5s
    4747:	learn: 61559.6213344	test: 114375.6489604	best: 114375.6489604 (4747)	total: 28.5s	remaining: 31.5s
    4748:	learn: 61554.4478244	test: 114374.1730708	best: 114374.1730708 (4748)	total: 28.5s	remaining: 31.5s
    4749:	learn: 61546.4790956	test: 114371.2987043	best: 114371.2987043 (4749)	total: 28.5s	remaining: 31.5s
    4750:	learn: 61541.6202131	test: 114362.5030498	best: 114362.5030498 (4750)	total: 28.5s	remaining: 31.5s
    4751:	learn: 61538.6605100	test: 114362.1733194	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4752:	learn: 61534.8083300	test: 114364.4837450	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4753:	learn: 61530.9773348	test: 114364.2300361	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4754:	learn: 61528.1716254	test: 114365.7012260	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4755:	learn: 61523.8608924	test: 114364.4028080	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4756:	learn: 61519.9750903	test: 114365.3851632	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.5s
    4757:	learn: 61514.9896695	test: 114366.0873059	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.4s
    4758:	learn: 61510.8274408	test: 114365.6910500	best: 114362.1733194 (4751)	total: 28.5s	remaining: 31.4s
    4759:	learn: 61504.5075687	test: 114368.1795279	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4760:	learn: 61500.7889094	test: 114369.6477157	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4761:	learn: 61500.5794850	test: 114369.2779097	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4762:	learn: 61496.8365565	test: 114374.6255539	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4763:	learn: 61489.2422238	test: 114377.2782957	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4764:	learn: 61484.1938689	test: 114382.5352612	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4765:	learn: 61480.0214947	test: 114382.3526818	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4766:	learn: 61476.4189444	test: 114381.0619367	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4767:	learn: 61473.4008066	test: 114379.9551878	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4768:	learn: 61468.2960681	test: 114381.0815697	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4769:	learn: 61465.6507755	test: 114380.1649098	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4770:	learn: 61460.9754750	test: 114381.3369940	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4771:	learn: 61457.3995819	test: 114382.2368962	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4772:	learn: 61452.8681315	test: 114381.0708332	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.4s
    4773:	learn: 61449.7598534	test: 114381.9088259	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.3s
    4774:	learn: 61445.3338824	test: 114383.4622920	best: 114362.1733194 (4751)	total: 28.6s	remaining: 31.3s
    4775:	learn: 61439.8549221	test: 114381.8240888	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4776:	learn: 61431.9732924	test: 114380.0169440	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4777:	learn: 61429.6882198	test: 114379.9739864	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4778:	learn: 61425.6561692	test: 114376.7120884	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4779:	learn: 61421.6913598	test: 114377.8954161	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4780:	learn: 61417.9581734	test: 114376.1565309	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4781:	learn: 61414.3032759	test: 114377.1636362	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4782:	learn: 61409.0988787	test: 114377.3800951	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4783:	learn: 61405.5447891	test: 114371.5285156	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4784:	learn: 61400.9863207	test: 114366.9196515	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4785:	learn: 61397.2987237	test: 114366.5569689	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4786:	learn: 61390.8617306	test: 114364.8845277	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4787:	learn: 61385.6214819	test: 114363.1660590	best: 114362.1733194 (4751)	total: 28.7s	remaining: 31.3s
    4788:	learn: 61380.2950618	test: 114361.1694608	best: 114361.1694608 (4788)	total: 28.7s	remaining: 31.3s
    4789:	learn: 61374.3201168	test: 114358.8780993	best: 114358.8780993 (4789)	total: 28.7s	remaining: 31.3s
    4790:	learn: 61366.9960493	test: 114358.4508648	best: 114358.4508648 (4790)	total: 28.7s	remaining: 31.3s
    4791:	learn: 61363.7868261	test: 114357.9876593	best: 114357.9876593 (4791)	total: 28.7s	remaining: 31.2s
    4792:	learn: 61358.1101250	test: 114356.5679424	best: 114356.5679424 (4792)	total: 28.8s	remaining: 31.2s
    4793:	learn: 61351.9280211	test: 114351.8662654	best: 114351.8662654 (4793)	total: 28.8s	remaining: 31.2s
    4794:	learn: 61348.6845744	test: 114351.5722681	best: 114351.5722681 (4794)	total: 28.8s	remaining: 31.2s
    4795:	learn: 61344.8083564	test: 114351.0922210	best: 114351.0922210 (4795)	total: 28.8s	remaining: 31.2s
    4796:	learn: 61337.2311569	test: 114349.2587032	best: 114349.2587032 (4796)	total: 28.8s	remaining: 31.2s
    4797:	learn: 61333.5027200	test: 114350.2293021	best: 114349.2587032 (4796)	total: 28.8s	remaining: 31.2s
    4798:	learn: 61330.3764225	test: 114346.6360226	best: 114346.6360226 (4798)	total: 28.8s	remaining: 31.2s
    4799:	learn: 61324.2479670	test: 114345.9462593	best: 114345.9462593 (4799)	total: 28.8s	remaining: 31.2s
    4800:	learn: 61319.1446295	test: 114344.3860011	best: 114344.3860011 (4800)	total: 28.8s	remaining: 31.2s
    4801:	learn: 61315.8642898	test: 114344.8670604	best: 114344.3860011 (4800)	total: 28.8s	remaining: 31.2s
    4802:	learn: 61313.2595737	test: 114341.3033590	best: 114341.3033590 (4802)	total: 28.8s	remaining: 31.2s
    4803:	learn: 61310.9025355	test: 114341.4719161	best: 114341.3033590 (4802)	total: 28.8s	remaining: 31.2s
    4804:	learn: 61307.8972718	test: 114340.8278921	best: 114340.8278921 (4804)	total: 28.8s	remaining: 31.2s
    4805:	learn: 61302.4206177	test: 114342.3976682	best: 114340.8278921 (4804)	total: 28.8s	remaining: 31.2s
    4806:	learn: 61298.8644099	test: 114342.0226532	best: 114340.8278921 (4804)	total: 28.9s	remaining: 31.2s
    4807:	learn: 61295.2347980	test: 114341.1682411	best: 114340.8278921 (4804)	total: 28.9s	remaining: 31.2s
    4808:	learn: 61290.6400543	test: 114339.6271525	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.2s
    4809:	learn: 61287.1058460	test: 114339.6554171	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.2s
    4810:	learn: 61284.1138516	test: 114340.7958258	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4811:	learn: 61279.5118003	test: 114340.6775996	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4812:	learn: 61273.7947696	test: 114340.0330650	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4813:	learn: 61269.8276647	test: 114342.3091202	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4814:	learn: 61266.9991243	test: 114342.0373350	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4815:	learn: 61263.5685062	test: 114341.8097392	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4816:	learn: 61258.4739260	test: 114342.9893961	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4817:	learn: 61255.6879807	test: 114342.5211477	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4818:	learn: 61250.3925508	test: 114351.3260570	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4819:	learn: 61247.5163717	test: 114351.8397390	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4820:	learn: 61243.7896334	test: 114352.4488590	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4821:	learn: 61241.4579699	test: 114351.3871469	best: 114339.6271525 (4808)	total: 28.9s	remaining: 31.1s
    4822:	learn: 61234.2515141	test: 114349.9388618	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4823:	learn: 61228.5613774	test: 114348.0231756	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4824:	learn: 61227.2353580	test: 114347.9229911	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4825:	learn: 61221.0294538	test: 114347.3323664	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4826:	learn: 61216.5298531	test: 114347.2340143	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4827:	learn: 61211.5054465	test: 114347.1552417	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4828:	learn: 61208.3722216	test: 114352.8727456	best: 114339.6271525 (4808)	total: 29s	remaining: 31.1s
    4829:	learn: 61205.8505608	test: 114355.3963067	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4830:	learn: 61200.4999329	test: 114356.8748234	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4831:	learn: 61196.8112028	test: 114356.6508691	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4832:	learn: 61192.6198602	test: 114353.3662170	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4833:	learn: 61188.0658348	test: 114353.1343265	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4834:	learn: 61183.4874675	test: 114354.3060662	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4835:	learn: 61178.1592792	test: 114351.8724429	best: 114339.6271525 (4808)	total: 29s	remaining: 31s
    4836:	learn: 61173.5272625	test: 114352.6780325	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4837:	learn: 61168.8578547	test: 114352.3171041	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4838:	learn: 61164.3825613	test: 114353.8355332	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4839:	learn: 61158.6818856	test: 114353.9875987	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4840:	learn: 61152.5245341	test: 114353.4431790	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4841:	learn: 61150.0377979	test: 114352.8155699	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4842:	learn: 61145.6549404	test: 114352.1148364	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4843:	learn: 61141.9405340	test: 114350.9482649	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4844:	learn: 61137.4002369	test: 114349.7736820	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4845:	learn: 61135.0012497	test: 114349.4604757	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4846:	learn: 61126.9844334	test: 114349.9931030	best: 114339.6271525 (4808)	total: 29.1s	remaining: 31s
    4847:	learn: 61123.6372102	test: 114351.2614018	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4848:	learn: 61118.6846853	test: 114352.4553289	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4849:	learn: 61115.5186241	test: 114349.7416399	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4850:	learn: 61113.2026458	test: 114349.7407272	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4851:	learn: 61109.2516804	test: 114349.5135575	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4852:	learn: 61106.9192658	test: 114349.7817148	best: 114339.6271525 (4808)	total: 29.1s	remaining: 30.9s
    4853:	learn: 61104.5458447	test: 114348.4434979	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4854:	learn: 61100.6243763	test: 114346.9635186	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4855:	learn: 61096.3837898	test: 114347.7747191	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4856:	learn: 61092.3894100	test: 114349.8939878	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4857:	learn: 61087.7471017	test: 114349.8946275	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4858:	learn: 61082.2251276	test: 114346.8042794	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4859:	learn: 61076.7008148	test: 114345.4792636	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4860:	learn: 61073.9754055	test: 114345.3415279	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4861:	learn: 61070.1325522	test: 114343.5974503	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4862:	learn: 61068.3397553	test: 114342.7161554	best: 114339.6271525 (4808)	total: 29.2s	remaining: 30.9s
    4863:	learn: 61063.0242066	test: 114338.9973233	best: 114338.9973233 (4863)	total: 29.2s	remaining: 30.9s
    4864:	learn: 61058.2277748	test: 114337.7495967	best: 114337.7495967 (4864)	total: 29.2s	remaining: 30.8s
    4865:	learn: 61055.9999444	test: 114335.5142514	best: 114335.5142514 (4865)	total: 29.2s	remaining: 30.8s
    4866:	learn: 61053.9843500	test: 114336.3994350	best: 114335.5142514 (4865)	total: 29.2s	remaining: 30.8s
    4867:	learn: 61048.5763492	test: 114340.6633999	best: 114335.5142514 (4865)	total: 29.2s	remaining: 30.8s
    4868:	learn: 61046.0106662	test: 114340.3197642	best: 114335.5142514 (4865)	total: 29.2s	remaining: 30.8s
    4869:	learn: 61041.9240882	test: 114340.9375391	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4870:	learn: 61037.7603099	test: 114342.1367819	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4871:	learn: 61028.5258867	test: 114340.0433701	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4872:	learn: 61025.8129881	test: 114339.4561524	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4873:	learn: 61021.7390787	test: 114338.8767034	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4874:	learn: 61018.8393920	test: 114338.2739883	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4875:	learn: 61013.4805513	test: 114335.9655551	best: 114335.5142514 (4865)	total: 29.3s	remaining: 30.8s
    4876:	learn: 61009.8803669	test: 114332.4985170	best: 114332.4985170 (4876)	total: 29.3s	remaining: 30.8s
    4877:	learn: 61005.7767725	test: 114330.4594733	best: 114330.4594733 (4877)	total: 29.3s	remaining: 30.8s
    4878:	learn: 61003.8386628	test: 114330.7236887	best: 114330.4594733 (4877)	total: 29.3s	remaining: 30.8s
    4879:	learn: 61001.0992891	test: 114330.7393587	best: 114330.4594733 (4877)	total: 29.3s	remaining: 30.7s
    4880:	learn: 60998.7264021	test: 114330.2246230	best: 114330.2246230 (4880)	total: 29.3s	remaining: 30.7s
    4881:	learn: 60991.3786155	test: 114328.3567642	best: 114328.3567642 (4881)	total: 29.3s	remaining: 30.7s
    4882:	learn: 60986.6898996	test: 114328.1048689	best: 114328.1048689 (4882)	total: 29.3s	remaining: 30.7s
    4883:	learn: 60981.8272265	test: 114325.9438806	best: 114325.9438806 (4883)	total: 29.3s	remaining: 30.7s
    4884:	learn: 60978.4875391	test: 114324.0986643	best: 114324.0986643 (4884)	total: 29.3s	remaining: 30.7s
    4885:	learn: 60971.8978849	test: 114321.4389418	best: 114321.4389418 (4885)	total: 29.4s	remaining: 30.7s
    4886:	learn: 60967.0387440	test: 114319.5677417	best: 114319.5677417 (4886)	total: 29.4s	remaining: 30.7s
    4887:	learn: 60965.3899522	test: 114320.1758258	best: 114319.5677417 (4886)	total: 29.4s	remaining: 30.7s
    4888:	learn: 60962.0110431	test: 114318.9132559	best: 114318.9132559 (4888)	total: 29.4s	remaining: 30.7s
    4889:	learn: 60958.0002407	test: 114319.5178725	best: 114318.9132559 (4888)	total: 29.4s	remaining: 30.7s
    4890:	learn: 60953.2918747	test: 114318.9826821	best: 114318.9132559 (4888)	total: 29.4s	remaining: 30.7s
    4891:	learn: 60949.6789230	test: 114318.3452277	best: 114318.3452277 (4891)	total: 29.4s	remaining: 30.7s
    4892:	learn: 60947.9083190	test: 114316.4680642	best: 114316.4680642 (4892)	total: 29.4s	remaining: 30.7s
    4893:	learn: 60943.6792547	test: 114318.7463530	best: 114316.4680642 (4892)	total: 29.4s	remaining: 30.7s
    4894:	learn: 60937.0173105	test: 114318.1540396	best: 114316.4680642 (4892)	total: 29.4s	remaining: 30.7s
    4895:	learn: 60932.4710284	test: 114315.6129486	best: 114315.6129486 (4895)	total: 29.4s	remaining: 30.7s
    4896:	learn: 60928.1787372	test: 114315.4414135	best: 114315.4414135 (4896)	total: 29.4s	remaining: 30.7s
    4897:	learn: 60925.7743257	test: 114318.0466605	best: 114315.4414135 (4896)	total: 29.4s	remaining: 30.7s
    4898:	learn: 60922.9526630	test: 114317.9230297	best: 114315.4414135 (4896)	total: 29.4s	remaining: 30.7s
    4899:	learn: 60920.0521957	test: 114317.6258429	best: 114315.4414135 (4896)	total: 29.4s	remaining: 30.6s
    4900:	learn: 60914.1751447	test: 114316.2329071	best: 114315.4414135 (4896)	total: 29.5s	remaining: 30.6s
    4901:	learn: 60911.3312358	test: 114316.0392873	best: 114315.4414135 (4896)	total: 29.5s	remaining: 30.6s
    4902:	learn: 60906.6449880	test: 114313.6114021	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4903:	learn: 60902.2687344	test: 114315.5718556	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4904:	learn: 60899.7123294	test: 114314.6771670	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4905:	learn: 60895.0219084	test: 114314.5087853	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4906:	learn: 60891.7665194	test: 114317.8577288	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4907:	learn: 60886.5251365	test: 114318.2171601	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4908:	learn: 60881.5008830	test: 114316.6771299	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4909:	learn: 60877.6048696	test: 114314.6447337	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4910:	learn: 60873.6681841	test: 114316.2769858	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4911:	learn: 60869.6247292	test: 114318.5466005	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4912:	learn: 60863.7495017	test: 114316.0539230	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4913:	learn: 60859.9665203	test: 114315.7730805	best: 114313.6114021 (4902)	total: 29.5s	remaining: 30.6s
    4914:	learn: 60855.3757748	test: 114311.8861456	best: 114311.8861456 (4914)	total: 29.5s	remaining: 30.6s
    4915:	learn: 60849.2101320	test: 114312.5067656	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.6s
    4916:	learn: 60844.6210653	test: 114314.7783449	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.6s
    4917:	learn: 60841.5221890	test: 114314.7568175	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.5s
    4918:	learn: 60835.9760409	test: 114312.8255487	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.5s
    4919:	learn: 60828.1830234	test: 114312.5638256	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.5s
    4920:	learn: 60824.6865789	test: 114313.5527016	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.5s
    4921:	learn: 60820.9360312	test: 114313.0228629	best: 114311.8861456 (4914)	total: 29.6s	remaining: 30.5s
    4922:	learn: 60813.8460555	test: 114311.7040027	best: 114311.7040027 (4922)	total: 29.6s	remaining: 30.5s
    4923:	learn: 60810.0275084	test: 114313.8066978	best: 114311.7040027 (4922)	total: 29.6s	remaining: 30.5s
    4924:	learn: 60806.0218530	test: 114313.1328205	best: 114311.7040027 (4922)	total: 29.6s	remaining: 30.5s
    4925:	learn: 60799.3567277	test: 114309.3159153	best: 114309.3159153 (4925)	total: 29.6s	remaining: 30.5s
    4926:	learn: 60791.8794448	test: 114308.1091660	best: 114308.1091660 (4926)	total: 29.6s	remaining: 30.5s
    4927:	learn: 60786.9110659	test: 114308.4322385	best: 114308.1091660 (4926)	total: 29.6s	remaining: 30.5s
    4928:	learn: 60783.0558857	test: 114307.8856414	best: 114307.8856414 (4928)	total: 29.6s	remaining: 30.5s
    4929:	learn: 60781.7065523	test: 114307.1596331	best: 114307.1596331 (4929)	total: 29.6s	remaining: 30.5s
    4930:	learn: 60775.7527853	test: 114307.8244389	best: 114307.1596331 (4929)	total: 29.6s	remaining: 30.5s
    4931:	learn: 60771.6877557	test: 114304.7067731	best: 114304.7067731 (4931)	total: 29.6s	remaining: 30.5s
    4932:	learn: 60766.0700685	test: 114301.7421757	best: 114301.7421757 (4932)	total: 29.7s	remaining: 30.5s
    4933:	learn: 60763.4232978	test: 114299.2186644	best: 114299.2186644 (4933)	total: 29.7s	remaining: 30.5s
    4934:	learn: 60756.9275943	test: 114299.5523718	best: 114299.2186644 (4933)	total: 29.7s	remaining: 30.4s
    4935:	learn: 60753.9663917	test: 114299.0599567	best: 114299.0599567 (4935)	total: 29.7s	remaining: 30.4s
    4936:	learn: 60751.8783932	test: 114298.5666182	best: 114298.5666182 (4936)	total: 29.7s	remaining: 30.4s
    4937:	learn: 60746.9298135	test: 114297.6036680	best: 114297.6036680 (4937)	total: 29.7s	remaining: 30.4s
    4938:	learn: 60740.8300544	test: 114296.1894042	best: 114296.1894042 (4938)	total: 29.7s	remaining: 30.4s
    4939:	learn: 60733.3956933	test: 114297.1175831	best: 114296.1894042 (4938)	total: 29.7s	remaining: 30.4s
    4940:	learn: 60730.7952777	test: 114296.9113973	best: 114296.1894042 (4938)	total: 29.7s	remaining: 30.4s
    4941:	learn: 60718.8722088	test: 114289.2382089	best: 114289.2382089 (4941)	total: 29.7s	remaining: 30.4s
    4942:	learn: 60714.5379280	test: 114293.1163051	best: 114289.2382089 (4941)	total: 29.7s	remaining: 30.4s
    4943:	learn: 60710.6251959	test: 114292.7306406	best: 114289.2382089 (4941)	total: 29.7s	remaining: 30.4s
    4944:	learn: 60703.7283281	test: 114291.4508409	best: 114289.2382089 (4941)	total: 29.7s	remaining: 30.4s
    4945:	learn: 60701.8276116	test: 114291.0357371	best: 114289.2382089 (4941)	total: 29.7s	remaining: 30.4s
    4946:	learn: 60696.2426305	test: 114291.8727375	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4947:	learn: 60691.7037336	test: 114289.8283919	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4948:	learn: 60690.7234261	test: 114289.7704602	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4949:	learn: 60687.9337281	test: 114291.9187916	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4950:	learn: 60682.6655769	test: 114291.1680996	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4951:	learn: 60678.1380127	test: 114291.0008821	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4952:	learn: 60675.6480133	test: 114290.3962609	best: 114289.2382089 (4941)	total: 29.8s	remaining: 30.4s
    4953:	learn: 60671.0325613	test: 114289.2158257	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.4s
    4954:	learn: 60668.6071689	test: 114289.3300669	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4955:	learn: 60666.1669255	test: 114289.6360178	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4956:	learn: 60662.7477146	test: 114289.3872383	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4957:	learn: 60654.8784586	test: 114292.3731121	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4958:	learn: 60651.7948565	test: 114292.6111410	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4959:	learn: 60646.9404277	test: 114294.1312635	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4960:	learn: 60642.5812873	test: 114294.7476452	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4961:	learn: 60637.3497311	test: 114295.7192783	best: 114289.2158257 (4953)	total: 29.8s	remaining: 30.3s
    4962:	learn: 60633.7389101	test: 114293.9770001	best: 114289.2158257 (4953)	total: 29.9s	remaining: 30.3s
    4963:	learn: 60628.5259715	test: 114294.2299603	best: 114289.2158257 (4953)	total: 29.9s	remaining: 30.3s
    4964:	learn: 60624.8469540	test: 114290.1399447	best: 114289.2158257 (4953)	total: 29.9s	remaining: 30.3s
    4965:	learn: 60619.1277054	test: 114288.1690071	best: 114288.1690071 (4965)	total: 29.9s	remaining: 30.3s
    4966:	learn: 60613.4135928	test: 114285.9407957	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4967:	learn: 60608.4569726	test: 114287.6007931	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4968:	learn: 60605.1591083	test: 114289.2332474	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4969:	learn: 60602.1965224	test: 114290.2221674	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4970:	learn: 60596.9466909	test: 114288.7888744	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4971:	learn: 60594.3271167	test: 114289.0257014	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4972:	learn: 60592.4594063	test: 114288.7479788	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.3s
    4973:	learn: 60585.9086476	test: 114289.0178225	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.2s
    4974:	learn: 60583.1846050	test: 114290.1631057	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.2s
    4975:	learn: 60579.1775375	test: 114290.5483585	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.2s
    4976:	learn: 60577.1381094	test: 114289.9864585	best: 114285.9407957 (4966)	total: 29.9s	remaining: 30.2s
    4977:	learn: 60572.0108025	test: 114290.2202516	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4978:	learn: 60564.1937312	test: 114290.7517502	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4979:	learn: 60560.7252899	test: 114292.1037875	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4980:	learn: 60557.9747370	test: 114290.7383080	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4981:	learn: 60553.9312778	test: 114294.3684825	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4982:	learn: 60552.4601768	test: 114294.5859438	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4983:	learn: 60543.4133162	test: 114292.4027573	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4984:	learn: 60537.0751836	test: 114292.6935751	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4985:	learn: 60533.8433252	test: 114293.9052111	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4986:	learn: 60527.9342792	test: 114293.5370074	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4987:	learn: 60526.4317299	test: 114295.8986312	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4988:	learn: 60519.3761014	test: 114294.6426502	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4989:	learn: 60512.7032349	test: 114295.2593421	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4990:	learn: 60509.2787373	test: 114292.5530506	best: 114285.9407957 (4966)	total: 30s	remaining: 30.2s
    4991:	learn: 60504.3462394	test: 114292.0670022	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4992:	learn: 60498.7813684	test: 114290.2930805	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4993:	learn: 60493.2524873	test: 114290.1506250	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4994:	learn: 60489.7302284	test: 114292.2325127	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4995:	learn: 60486.5253637	test: 114291.5437513	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4996:	learn: 60484.3436138	test: 114291.3188839	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4997:	learn: 60479.9888441	test: 114290.9679825	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4998:	learn: 60473.0912578	test: 114292.4130403	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    4999:	learn: 60468.9333690	test: 114290.0666240	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5000:	learn: 60465.1008338	test: 114291.2130679	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5001:	learn: 60462.5561858	test: 114290.5665479	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5002:	learn: 60457.7203802	test: 114290.9965074	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5003:	learn: 60455.9295995	test: 114290.0506643	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5004:	learn: 60447.4994693	test: 114288.3742214	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5005:	learn: 60445.0347542	test: 114288.0075979	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5006:	learn: 60442.3127555	test: 114286.7921290	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5007:	learn: 60438.6778060	test: 114287.4505514	best: 114285.9407957 (4966)	total: 30.1s	remaining: 30.1s
    5008:	learn: 60436.3771742	test: 114286.8421397	best: 114285.9407957 (4966)	total: 30.2s	remaining: 30s
    5009:	learn: 60432.1257723	test: 114289.3385812	best: 114285.9407957 (4966)	total: 30.2s	remaining: 30s
    5010:	learn: 60426.5662684	test: 114288.8309906	best: 114285.9407957 (4966)	total: 30.2s	remaining: 30s
    5011:	learn: 60422.4012021	test: 114287.7348562	best: 114285.9407957 (4966)	total: 30.2s	remaining: 30s
    5012:	learn: 60418.6473210	test: 114285.6748995	best: 114285.6748995 (5012)	total: 30.2s	remaining: 30s
    5013:	learn: 60412.0473482	test: 114285.4369465	best: 114285.4369465 (5013)	total: 30.2s	remaining: 30s
    5014:	learn: 60408.1502371	test: 114282.4360918	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5015:	learn: 60405.1615490	test: 114287.5513485	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5016:	learn: 60398.7721226	test: 114287.3682004	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5017:	learn: 60394.9348103	test: 114283.8727387	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5018:	learn: 60388.7777831	test: 114283.8047708	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5019:	learn: 60385.5854451	test: 114284.1751720	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5020:	learn: 60383.3967788	test: 114286.3431784	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5021:	learn: 60379.2921598	test: 114286.5946290	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5022:	learn: 60375.5289556	test: 114288.1565516	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5023:	learn: 60369.9320505	test: 114288.7997925	best: 114282.4360918 (5014)	total: 30.2s	remaining: 30s
    5024:	learn: 60367.7881314	test: 114288.5483316	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5025:	learn: 60365.3617624	test: 114289.4274914	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5026:	learn: 60362.7088426	test: 114290.2165726	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5027:	learn: 60358.2436222	test: 114291.4123951	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5028:	learn: 60354.0729848	test: 114291.4058295	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5029:	learn: 60349.0736766	test: 114291.9291081	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5030:	learn: 60346.6453816	test: 114292.5491014	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5031:	learn: 60343.9795056	test: 114293.0793958	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5032:	learn: 60341.7101876	test: 114292.8646359	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5033:	learn: 60339.2483236	test: 114292.8310549	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5034:	learn: 60336.0490871	test: 114292.8154481	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5035:	learn: 60330.8012881	test: 114292.5030237	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5036:	learn: 60325.4687933	test: 114293.3647934	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5037:	learn: 60321.9127116	test: 114290.4263677	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5038:	learn: 60314.3956249	test: 114293.3411541	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5039:	learn: 60310.3045458	test: 114294.6822363	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.9s
    5040:	learn: 60302.5301061	test: 114295.0966373	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.8s
    5041:	learn: 60298.9908367	test: 114293.8856932	best: 114282.4360918 (5014)	total: 30.3s	remaining: 29.8s
    5042:	learn: 60293.6831452	test: 114292.5815239	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5043:	learn: 60289.6843719	test: 114292.2710890	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5044:	learn: 60286.3610102	test: 114290.6514310	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5045:	learn: 60280.2091362	test: 114290.4092631	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5046:	learn: 60275.0771643	test: 114290.6971790	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5047:	learn: 60271.3005184	test: 114289.1220866	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5048:	learn: 60267.8949735	test: 114289.5145433	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5049:	learn: 60265.3507521	test: 114288.9571809	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5050:	learn: 60262.7059317	test: 114288.4634142	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5051:	learn: 60254.8645267	test: 114284.5272042	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5052:	learn: 60249.1707539	test: 114283.5009948	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5053:	learn: 60244.1882100	test: 114285.6742647	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5054:	learn: 60241.5965756	test: 114285.1177268	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5055:	learn: 60238.9187363	test: 114283.9902749	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5056:	learn: 60234.5232634	test: 114282.8020532	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.8s
    5057:	learn: 60232.7574792	test: 114283.2349963	best: 114282.4360918 (5014)	total: 30.4s	remaining: 29.7s
    5058:	learn: 60229.8381117	test: 114281.3673820	best: 114281.3673820 (5058)	total: 30.4s	remaining: 29.7s
    5059:	learn: 60227.2162410	test: 114282.0597971	best: 114281.3673820 (5058)	total: 30.5s	remaining: 29.7s
    5060:	learn: 60221.8784301	test: 114283.8349256	best: 114281.3673820 (5058)	total: 30.5s	remaining: 29.7s
    5061:	learn: 60216.3003453	test: 114279.9427644	best: 114279.9427644 (5061)	total: 30.5s	remaining: 29.7s
    5062:	learn: 60212.9410782	test: 114281.6979126	best: 114279.9427644 (5061)	total: 30.5s	remaining: 29.7s
    5063:	learn: 60211.7409519	test: 114283.0331876	best: 114279.9427644 (5061)	total: 30.5s	remaining: 29.7s
    5064:	learn: 60206.0783031	test: 114278.4495644	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5065:	learn: 60200.7742151	test: 114279.8744318	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5066:	learn: 60195.0053090	test: 114279.9771361	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5067:	learn: 60191.5034975	test: 114280.4094282	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5068:	learn: 60187.7940551	test: 114279.2696148	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5069:	learn: 60180.9287945	test: 114281.6181753	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5070:	learn: 60179.9318133	test: 114281.1229134	best: 114278.4495644 (5064)	total: 30.5s	remaining: 29.7s
    5071:	learn: 60170.7553885	test: 114276.3221055	best: 114276.3221055 (5071)	total: 30.5s	remaining: 29.7s
    5072:	learn: 60167.5707413	test: 114278.0792967	best: 114276.3221055 (5071)	total: 30.5s	remaining: 29.7s
    5073:	learn: 60160.9316667	test: 114278.6059577	best: 114276.3221055 (5071)	total: 30.5s	remaining: 29.6s
    5074:	learn: 60155.8999693	test: 114276.4160260	best: 114276.3221055 (5071)	total: 30.5s	remaining: 29.6s
    5075:	learn: 60152.0256569	test: 114276.9567168	best: 114276.3221055 (5071)	total: 30.6s	remaining: 29.6s
    5076:	learn: 60145.0463437	test: 114279.2459260	best: 114276.3221055 (5071)	total: 30.6s	remaining: 29.6s
    5077:	learn: 60142.5057203	test: 114278.6834747	best: 114276.3221055 (5071)	total: 30.6s	remaining: 29.6s
    5078:	learn: 60139.8353745	test: 114278.5672623	best: 114276.3221055 (5071)	total: 30.6s	remaining: 29.6s
    5079:	learn: 60136.8391742	test: 114274.4327805	best: 114274.4327805 (5079)	total: 30.6s	remaining: 29.6s
    5080:	learn: 60133.3378462	test: 114273.9260128	best: 114273.9260128 (5080)	total: 30.6s	remaining: 29.6s
    5081:	learn: 60129.2937051	test: 114271.3334389	best: 114271.3334389 (5081)	total: 30.6s	remaining: 29.6s
    5082:	learn: 60126.0767604	test: 114268.1799434	best: 114268.1799434 (5082)	total: 30.6s	remaining: 29.6s
    5083:	learn: 60122.7340375	test: 114268.4599194	best: 114268.1799434 (5082)	total: 30.6s	remaining: 29.6s
    5084:	learn: 60114.1326729	test: 114265.9840575	best: 114265.9840575 (5084)	total: 30.6s	remaining: 29.6s
    5085:	learn: 60110.8303826	test: 114265.0957183	best: 114265.0957183 (5085)	total: 30.6s	remaining: 29.6s
    5086:	learn: 60104.2262039	test: 114264.4259436	best: 114264.4259436 (5086)	total: 30.6s	remaining: 29.6s
    5087:	learn: 60099.7872276	test: 114263.4162802	best: 114263.4162802 (5087)	total: 30.6s	remaining: 29.6s
    5088:	learn: 60096.4293362	test: 114263.4545667	best: 114263.4162802 (5087)	total: 30.6s	remaining: 29.6s
    5089:	learn: 60093.1339291	test: 114262.8562167	best: 114262.8562167 (5089)	total: 30.6s	remaining: 29.6s
    5090:	learn: 60091.3637391	test: 114262.4673487	best: 114262.4673487 (5090)	total: 30.6s	remaining: 29.5s
    5091:	learn: 60087.0489975	test: 114262.7117064	best: 114262.4673487 (5090)	total: 30.6s	remaining: 29.5s
    5092:	learn: 60082.1772482	test: 114260.3987778	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5093:	learn: 60077.8094827	test: 114261.8842531	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5094:	learn: 60073.5862481	test: 114263.5021665	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5095:	learn: 60071.0477138	test: 114263.4221103	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5096:	learn: 60067.7883766	test: 114263.7484179	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5097:	learn: 60063.1517505	test: 114263.2995583	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5098:	learn: 60059.2341192	test: 114263.4511701	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5099:	learn: 60052.8901467	test: 114266.0404234	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5100:	learn: 60049.5334425	test: 114265.7633018	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5101:	learn: 60048.3319810	test: 114265.2592594	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5102:	learn: 60046.2712635	test: 114265.1371607	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5103:	learn: 60039.0917022	test: 114261.6995732	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5104:	learn: 60036.2176012	test: 114261.1602033	best: 114260.3987778 (5092)	total: 30.7s	remaining: 29.5s
    5105:	learn: 60027.0816446	test: 114256.2388692	best: 114256.2388692 (5105)	total: 30.7s	remaining: 29.5s
    5106:	learn: 60023.7439115	test: 114255.9909977	best: 114255.9909977 (5106)	total: 30.7s	remaining: 29.5s
    5107:	learn: 60022.2971410	test: 114256.0511800	best: 114255.9909977 (5106)	total: 30.8s	remaining: 29.5s
    5108:	learn: 60019.7933479	test: 114254.7754165	best: 114254.7754165 (5108)	total: 30.8s	remaining: 29.4s
    5109:	learn: 60016.6279599	test: 114256.5832130	best: 114254.7754165 (5108)	total: 30.8s	remaining: 29.4s
    5110:	learn: 60014.5637156	test: 114256.1358235	best: 114254.7754165 (5108)	total: 30.8s	remaining: 29.4s
    5111:	learn: 60009.9924226	test: 114256.8077842	best: 114254.7754165 (5108)	total: 30.8s	remaining: 29.4s
    5112:	learn: 60005.7460919	test: 114254.3130274	best: 114254.3130274 (5112)	total: 30.8s	remaining: 29.4s
    5113:	learn: 59999.5734581	test: 114254.6432164	best: 114254.3130274 (5112)	total: 30.8s	remaining: 29.4s
    5114:	learn: 59992.3695445	test: 114255.4660935	best: 114254.3130274 (5112)	total: 30.8s	remaining: 29.4s
    5115:	learn: 59989.7653998	test: 114255.0328740	best: 114254.3130274 (5112)	total: 30.8s	remaining: 29.4s
    5116:	learn: 59982.7732309	test: 114254.7124009	best: 114254.3130274 (5112)	total: 30.8s	remaining: 29.4s
    5117:	learn: 59975.5935199	test: 114253.1092164	best: 114253.1092164 (5117)	total: 30.8s	remaining: 29.4s
    5118:	learn: 59971.3877027	test: 114253.3535594	best: 114253.1092164 (5117)	total: 30.8s	remaining: 29.4s
    5119:	learn: 59966.0966297	test: 114253.6477202	best: 114253.1092164 (5117)	total: 30.8s	remaining: 29.4s
    5120:	learn: 59964.1212572	test: 114251.6559983	best: 114251.6559983 (5120)	total: 30.8s	remaining: 29.4s
    5121:	learn: 59961.6826619	test: 114253.4063830	best: 114251.6559983 (5120)	total: 30.8s	remaining: 29.4s
    5122:	learn: 59959.2172555	test: 114253.4736441	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.4s
    5123:	learn: 59955.9456108	test: 114252.9807127	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.4s
    5124:	learn: 59955.0727838	test: 114252.5057890	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.4s
    5125:	learn: 59953.0245833	test: 114253.1901557	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.4s
    5126:	learn: 59949.9633042	test: 114253.0696325	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.3s
    5127:	learn: 59945.1670961	test: 114252.1361922	best: 114251.6559983 (5120)	total: 30.9s	remaining: 29.3s
    5128:	learn: 59941.5654670	test: 114250.9146309	best: 114250.9146309 (5128)	total: 30.9s	remaining: 29.3s
    5129:	learn: 59937.5289587	test: 114248.8095384	best: 114248.8095384 (5129)	total: 30.9s	remaining: 29.3s
    5130:	learn: 59928.5287732	test: 114243.3223833	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5131:	learn: 59924.1904418	test: 114244.9245091	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5132:	learn: 59920.0536825	test: 114244.6616685	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5133:	learn: 59916.7721497	test: 114248.2833640	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5134:	learn: 59910.5961645	test: 114248.1084920	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5135:	learn: 59906.2728488	test: 114248.9516778	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5136:	learn: 59900.2782795	test: 114250.2364720	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5137:	learn: 59897.0077731	test: 114248.7190259	best: 114243.3223833 (5130)	total: 30.9s	remaining: 29.3s
    5138:	learn: 59893.0996943	test: 114245.6057187	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5139:	learn: 59888.3876809	test: 114246.3801921	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5140:	learn: 59883.9170130	test: 114244.9008242	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5141:	learn: 59880.7300277	test: 114248.6274219	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5142:	learn: 59874.3435864	test: 114248.5504251	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5143:	learn: 59869.7277318	test: 114249.0302142	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5144:	learn: 59865.8746736	test: 114248.1335146	best: 114243.3223833 (5130)	total: 31s	remaining: 29.3s
    5145:	learn: 59859.9313729	test: 114248.0105082	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5146:	learn: 59855.0421573	test: 114248.0378232	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5147:	learn: 59852.5871361	test: 114248.6587393	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5148:	learn: 59849.8555280	test: 114249.3807756	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5149:	learn: 59844.8466278	test: 114248.1988073	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5150:	learn: 59842.8047714	test: 114247.4380489	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5151:	learn: 59837.8835693	test: 114248.7926683	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5152:	learn: 59833.8895628	test: 114246.5488943	best: 114243.3223833 (5130)	total: 31s	remaining: 29.2s
    5153:	learn: 59831.1550628	test: 114249.6883825	best: 114243.3223833 (5130)	total: 31.1s	remaining: 29.2s
    5154:	learn: 59826.2155371	test: 114251.3149155	best: 114243.3223833 (5130)	total: 31.1s	remaining: 29.2s
    5155:	learn: 59820.0407479	test: 114248.9134027	best: 114243.3223833 (5130)	total: 31.1s	remaining: 29.2s
    5156:	learn: 59811.6653573	test: 114246.4516745	best: 114243.3223833 (5130)	total: 31.1s	remaining: 29.2s
    5157:	learn: 59805.6851065	test: 114240.8578843	best: 114240.8578843 (5157)	total: 31.1s	remaining: 29.2s
    5158:	learn: 59802.5144617	test: 114239.6333975	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.2s
    5159:	learn: 59799.4351220	test: 114242.6782794	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.2s
    5160:	learn: 59793.1762106	test: 114243.1745376	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.2s
    5161:	learn: 59790.3224661	test: 114243.1137029	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.2s
    5162:	learn: 59786.4894770	test: 114243.1354973	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5163:	learn: 59781.6260836	test: 114242.0057175	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5164:	learn: 59774.6601158	test: 114242.3548429	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5165:	learn: 59768.4278664	test: 114242.9342791	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5166:	learn: 59763.3800172	test: 114244.3271902	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5167:	learn: 59761.3225664	test: 114242.8853523	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5168:	learn: 59756.8263364	test: 114244.0724753	best: 114239.6333975 (5158)	total: 31.1s	remaining: 29.1s
    5169:	learn: 59753.0794923	test: 114243.4971969	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5170:	learn: 59749.4777842	test: 114242.1633198	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5171:	learn: 59745.8917742	test: 114242.4743671	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5172:	learn: 59743.2457719	test: 114241.3059814	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5173:	learn: 59738.2626047	test: 114243.2504361	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5174:	learn: 59735.2427501	test: 114245.5482897	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5175:	learn: 59730.4038443	test: 114247.5059960	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5176:	learn: 59724.4943315	test: 114248.6512770	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5177:	learn: 59720.5126388	test: 114249.0511095	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5178:	learn: 59719.1906544	test: 114249.7045882	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29.1s
    5179:	learn: 59716.3063295	test: 114248.4899117	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5180:	learn: 59711.5406241	test: 114248.6271973	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5181:	learn: 59709.7144863	test: 114249.1747612	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5182:	learn: 59705.1970274	test: 114250.3863092	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5183:	learn: 59702.5754548	test: 114250.3661878	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5184:	learn: 59697.2201244	test: 114250.1578543	best: 114239.6333975 (5158)	total: 31.2s	remaining: 29s
    5185:	learn: 59693.2466957	test: 114249.1560878	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5186:	learn: 59688.8066862	test: 114246.0977316	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5187:	learn: 59685.5968702	test: 114244.5014683	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5188:	learn: 59679.8740414	test: 114243.2027534	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5189:	learn: 59675.8100213	test: 114245.2955881	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5190:	learn: 59672.6894027	test: 114244.5506588	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5191:	learn: 59669.8267606	test: 114243.0994452	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5192:	learn: 59667.3775805	test: 114241.7713286	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5193:	learn: 59664.3281725	test: 114242.3130941	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5194:	learn: 59659.3767980	test: 114243.4619780	best: 114239.6333975 (5158)	total: 31.3s	remaining: 29s
    5195:	learn: 59654.0087471	test: 114237.2723203	best: 114237.2723203 (5195)	total: 31.3s	remaining: 28.9s
    5196:	learn: 59651.3319998	test: 114236.2602210	best: 114236.2602210 (5196)	total: 31.3s	remaining: 28.9s
    5197:	learn: 59648.1940923	test: 114234.6400518	best: 114234.6400518 (5197)	total: 31.3s	remaining: 28.9s
    5198:	learn: 59644.7262791	test: 114233.2334075	best: 114233.2334075 (5198)	total: 31.3s	remaining: 28.9s
    5199:	learn: 59640.5690878	test: 114233.2103190	best: 114233.2103190 (5199)	total: 31.3s	remaining: 28.9s
    5200:	learn: 59636.4443965	test: 114234.4970769	best: 114233.2103190 (5199)	total: 31.3s	remaining: 28.9s
    5201:	learn: 59629.8741809	test: 114234.2859469	best: 114233.2103190 (5199)	total: 31.3s	remaining: 28.9s
    5202:	learn: 59625.8933539	test: 114235.3892001	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5203:	learn: 59622.0530251	test: 114236.7315467	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5204:	learn: 59616.8812479	test: 114239.3991731	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5205:	learn: 59613.7931711	test: 114236.0647654	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5206:	learn: 59610.6563169	test: 114235.0145706	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5207:	learn: 59605.9627352	test: 114235.6951802	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5208:	learn: 59603.7452009	test: 114236.2973275	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5209:	learn: 59601.1294899	test: 114238.8082567	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5210:	learn: 59597.5408263	test: 114238.8139493	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5211:	learn: 59591.3699019	test: 114238.1256539	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.9s
    5212:	learn: 59587.3081057	test: 114239.4114413	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5213:	learn: 59584.4361247	test: 114237.8529392	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5214:	learn: 59582.3243641	test: 114239.2784069	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5215:	learn: 59578.0117462	test: 114239.8424618	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5216:	learn: 59571.5159242	test: 114239.4200691	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5217:	learn: 59565.2254844	test: 114239.1597708	best: 114233.2103190 (5199)	total: 31.4s	remaining: 28.8s
    5218:	learn: 59560.8618842	test: 114238.9068832	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5219:	learn: 59555.9473183	test: 114239.5614975	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5220:	learn: 59550.1119127	test: 114239.3189061	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5221:	learn: 59544.6499029	test: 114236.9229351	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5222:	learn: 59539.0658583	test: 114238.6563157	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5223:	learn: 59537.6505675	test: 114238.7982157	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5224:	learn: 59535.2642281	test: 114238.9285134	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5225:	learn: 59532.5689743	test: 114238.7403051	best: 114233.2103190 (5199)	total: 31.5s	remaining: 28.8s
    5226:	learn: 59523.3529654	test: 114231.4446876	best: 114231.4446876 (5226)	total: 31.5s	remaining: 28.8s
    5227:	learn: 59516.8730917	test: 114230.3189786	best: 114230.3189786 (5227)	total: 31.5s	remaining: 28.8s
    5228:	learn: 59514.0865614	test: 114230.7107743	best: 114230.3189786 (5227)	total: 31.5s	remaining: 28.8s
    5229:	learn: 59509.2362583	test: 114231.6445055	best: 114230.3189786 (5227)	total: 31.5s	remaining: 28.7s
    5230:	learn: 59505.5209127	test: 114231.1099155	best: 114230.3189786 (5227)	total: 31.5s	remaining: 28.7s
    5231:	learn: 59499.3640574	test: 114229.5766733	best: 114229.5766733 (5231)	total: 31.5s	remaining: 28.7s
    5232:	learn: 59496.6155857	test: 114230.3602355	best: 114229.5766733 (5231)	total: 31.5s	remaining: 28.7s
    5233:	learn: 59491.2527686	test: 114231.7620788	best: 114229.5766733 (5231)	total: 31.5s	remaining: 28.7s
    5234:	learn: 59488.3892335	test: 114229.3581935	best: 114229.3581935 (5234)	total: 31.5s	remaining: 28.7s
    5235:	learn: 59482.7861884	test: 114229.5689823	best: 114229.3581935 (5234)	total: 31.6s	remaining: 28.7s
    5236:	learn: 59477.1413019	test: 114228.2298554	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5237:	learn: 59473.7343521	test: 114229.2346137	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5238:	learn: 59471.2057124	test: 114230.0109320	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5239:	learn: 59467.3142181	test: 114230.2542720	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5240:	learn: 59461.8340543	test: 114230.4849009	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5241:	learn: 59456.5481941	test: 114229.4450381	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5242:	learn: 59450.3525228	test: 114228.3232274	best: 114228.2298554 (5236)	total: 31.6s	remaining: 28.7s
    5243:	learn: 59447.5341033	test: 114227.5308518	best: 114227.5308518 (5243)	total: 31.6s	remaining: 28.7s
    5244:	learn: 59443.3312100	test: 114226.2093717	best: 114226.2093717 (5244)	total: 31.6s	remaining: 28.7s
    5245:	learn: 59440.4101006	test: 114224.2051916	best: 114224.2051916 (5245)	total: 31.6s	remaining: 28.7s
    5246:	learn: 59436.7159556	test: 114222.5566135	best: 114222.5566135 (5246)	total: 31.6s	remaining: 28.6s
    5247:	learn: 59432.4731659	test: 114222.8624464	best: 114222.5566135 (5246)	total: 31.6s	remaining: 28.6s
    5248:	learn: 59428.9541736	test: 114222.5501230	best: 114222.5501230 (5248)	total: 31.6s	remaining: 28.6s
    5249:	learn: 59424.6175576	test: 114222.5538521	best: 114222.5501230 (5248)	total: 31.6s	remaining: 28.6s
    5250:	learn: 59422.3430448	test: 114223.2262726	best: 114222.5501230 (5248)	total: 31.7s	remaining: 28.6s
    5251:	learn: 59419.8668172	test: 114224.0091845	best: 114222.5501230 (5248)	total: 31.7s	remaining: 28.6s
    5252:	learn: 59408.8294747	test: 114215.4781368	best: 114215.4781368 (5252)	total: 31.7s	remaining: 28.6s
    5253:	learn: 59402.9121005	test: 114214.9195242	best: 114214.9195242 (5253)	total: 31.7s	remaining: 28.6s
    5254:	learn: 59398.8768030	test: 114213.5905354	best: 114213.5905354 (5254)	total: 31.7s	remaining: 28.6s
    5255:	learn: 59396.4903002	test: 114215.8175270	best: 114213.5905354 (5254)	total: 31.7s	remaining: 28.6s
    5256:	learn: 59392.9411111	test: 114213.1126141	best: 114213.1126141 (5256)	total: 31.7s	remaining: 28.6s
    5257:	learn: 59384.6547640	test: 114211.3263838	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5258:	learn: 59381.2962867	test: 114212.5314351	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5259:	learn: 59379.3762350	test: 114216.2312969	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5260:	learn: 59376.0910513	test: 114217.2040522	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5261:	learn: 59371.1743016	test: 114216.2670248	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5262:	learn: 59366.4725450	test: 114219.0781745	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5263:	learn: 59363.1176068	test: 114219.9007290	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.6s
    5264:	learn: 59359.3508023	test: 114220.9137994	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.5s
    5265:	learn: 59352.1413995	test: 114222.9032138	best: 114211.3263838 (5257)	total: 31.7s	remaining: 28.5s
    5266:	learn: 59348.1207239	test: 114223.2243623	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5267:	learn: 59345.2241509	test: 114221.4047495	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5268:	learn: 59339.0924615	test: 114221.0224637	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5269:	learn: 59336.1909294	test: 114221.1998158	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5270:	learn: 59331.8519456	test: 114220.6762020	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5271:	learn: 59326.7007341	test: 114218.4952173	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5272:	learn: 59323.3719474	test: 114221.1673946	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5273:	learn: 59319.7187371	test: 114219.2188468	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5274:	learn: 59312.3005747	test: 114220.1460127	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5275:	learn: 59306.3386059	test: 114223.0302279	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5276:	learn: 59302.0304684	test: 114223.0863582	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5277:	learn: 59296.2613824	test: 114222.0488147	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5278:	learn: 59288.9263372	test: 114221.9408054	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5279:	learn: 59283.1964427	test: 114222.2447514	best: 114211.3263838 (5257)	total: 31.8s	remaining: 28.5s
    5280:	learn: 59279.3167902	test: 114221.9214451	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.5s
    5281:	learn: 59270.6073906	test: 114219.8161168	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.5s
    5282:	learn: 59266.8492553	test: 114221.0668934	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5283:	learn: 59264.5349126	test: 114221.0260267	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5284:	learn: 59259.6944000	test: 114221.9144092	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5285:	learn: 59257.1612121	test: 114221.2898619	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5286:	learn: 59250.8835319	test: 114221.1745749	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5287:	learn: 59243.7912342	test: 114222.4751475	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5288:	learn: 59241.7611829	test: 114223.0492963	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5289:	learn: 59239.3145530	test: 114222.7821055	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5290:	learn: 59236.7749775	test: 114223.2096439	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5291:	learn: 59234.2947180	test: 114224.5470210	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5292:	learn: 59226.7539016	test: 114223.1341434	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5293:	learn: 59220.8448833	test: 114223.2767001	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5294:	learn: 59216.8328088	test: 114221.9780980	best: 114211.3263838 (5257)	total: 31.9s	remaining: 28.4s
    5295:	learn: 59213.1703544	test: 114222.4311240	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5296:	learn: 59211.0194200	test: 114223.1646386	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5297:	learn: 59207.6879853	test: 114222.2033073	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5298:	learn: 59202.8038249	test: 114220.8395672	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5299:	learn: 59200.3910506	test: 114218.6850786	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5300:	learn: 59198.8708101	test: 114217.1815663	best: 114211.3263838 (5257)	total: 32s	remaining: 28.4s
    5301:	learn: 59194.0122788	test: 114215.7688467	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5302:	learn: 59188.8352590	test: 114215.7141542	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5303:	learn: 59186.7416562	test: 114215.1599112	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5304:	learn: 59184.3863976	test: 114215.8473157	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5305:	learn: 59180.5184281	test: 114217.1272819	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5306:	learn: 59173.6030227	test: 114214.4006603	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5307:	learn: 59170.6687342	test: 114212.9891809	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5308:	learn: 59167.9038464	test: 114213.2395144	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5309:	learn: 59163.9839985	test: 114212.9640885	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5310:	learn: 59159.3211417	test: 114212.5019885	best: 114211.3263838 (5257)	total: 32s	remaining: 28.3s
    5311:	learn: 59155.6346240	test: 114212.6016217	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5312:	learn: 59153.9397745	test: 114212.0315691	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5313:	learn: 59151.8660317	test: 114211.7219360	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5314:	learn: 59146.6629465	test: 114211.5694361	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5315:	learn: 59143.0445211	test: 114215.2706212	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5316:	learn: 59140.5821549	test: 114215.1085312	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5317:	learn: 59138.5537581	test: 114216.0727326	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.3s
    5318:	learn: 59135.3600830	test: 114216.7163599	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5319:	learn: 59132.6753652	test: 114215.8974540	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5320:	learn: 59129.0104736	test: 114217.6615845	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5321:	learn: 59127.0435139	test: 114217.2817901	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5322:	learn: 59123.0736951	test: 114217.3487887	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5323:	learn: 59117.3473190	test: 114216.8415960	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5324:	learn: 59110.7812630	test: 114213.6762196	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5325:	learn: 59105.6578435	test: 114216.5518536	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5326:	learn: 59099.6507976	test: 114214.9571877	best: 114211.3263838 (5257)	total: 32.1s	remaining: 28.2s
    5327:	learn: 59095.7713548	test: 114213.9691066	best: 114211.3263838 (5257)	total: 32.2s	remaining: 28.2s
    5328:	learn: 59094.6014137	test: 114213.3873645	best: 114211.3263838 (5257)	total: 32.2s	remaining: 28.2s
    5329:	learn: 59090.3142702	test: 114213.0972847	best: 114211.3263838 (5257)	total: 32.2s	remaining: 28.2s
    5330:	learn: 59086.0989677	test: 114213.7154519	best: 114211.3263838 (5257)	total: 32.2s	remaining: 28.2s
    5331:	learn: 59081.1901691	test: 114211.2296341	best: 114211.2296341 (5331)	total: 32.2s	remaining: 28.2s
    5332:	learn: 59078.6762928	test: 114210.1443237	best: 114210.1443237 (5332)	total: 32.2s	remaining: 28.2s
    5333:	learn: 59075.1212917	test: 114210.7497178	best: 114210.1443237 (5332)	total: 32.2s	remaining: 28.2s
    5334:	learn: 59072.3248127	test: 114209.3390196	best: 114209.3390196 (5334)	total: 32.2s	remaining: 28.2s
    5335:	learn: 59066.9715609	test: 114209.0180202	best: 114209.0180202 (5335)	total: 32.2s	remaining: 28.1s
    5336:	learn: 59060.6513117	test: 114207.2179395	best: 114207.2179395 (5336)	total: 32.2s	remaining: 28.1s
    5337:	learn: 59058.0697412	test: 114206.6139613	best: 114206.6139613 (5337)	total: 32.2s	remaining: 28.1s
    5338:	learn: 59056.3400691	test: 114207.6954327	best: 114206.6139613 (5337)	total: 32.2s	remaining: 28.1s
    5339:	learn: 59051.6644836	test: 114206.9866000	best: 114206.6139613 (5337)	total: 32.2s	remaining: 28.1s
    5340:	learn: 59050.2857594	test: 114205.7956066	best: 114205.7956066 (5340)	total: 32.2s	remaining: 28.1s
    5341:	learn: 59047.6401858	test: 114205.0876432	best: 114205.0876432 (5341)	total: 32.2s	remaining: 28.1s
    5342:	learn: 59043.7235554	test: 114204.2030070	best: 114204.2030070 (5342)	total: 32.2s	remaining: 28.1s
    5343:	learn: 59041.7000134	test: 114204.0439362	best: 114204.0439362 (5343)	total: 32.2s	remaining: 28.1s
    5344:	learn: 59037.3699484	test: 114204.8454170	best: 114204.0439362 (5343)	total: 32.3s	remaining: 28.1s
    5345:	learn: 59033.5491890	test: 114206.3407320	best: 114204.0439362 (5343)	total: 32.3s	remaining: 28.1s
    5346:	learn: 59028.2208618	test: 114205.1993059	best: 114204.0439362 (5343)	total: 32.3s	remaining: 28.1s
    5347:	learn: 59025.8531701	test: 114203.5575402	best: 114203.5575402 (5347)	total: 32.3s	remaining: 28.1s
    5348:	learn: 59023.0220233	test: 114203.2079267	best: 114203.2079267 (5348)	total: 32.3s	remaining: 28.1s
    5349:	learn: 59014.6534433	test: 114200.9693989	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28.1s
    5350:	learn: 59010.8419460	test: 114201.0023675	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28.1s
    5351:	learn: 59004.2772877	test: 114201.6705143	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5352:	learn: 59000.1982061	test: 114201.9066666	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5353:	learn: 58997.1059651	test: 114202.5759995	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5354:	learn: 58994.9284329	test: 114203.4477112	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5355:	learn: 58992.4516820	test: 114203.5061030	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5356:	learn: 58985.8720910	test: 114202.5310252	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5357:	learn: 58980.2204467	test: 114201.1520198	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5358:	learn: 58976.6854792	test: 114201.4061127	best: 114200.9693989 (5349)	total: 32.3s	remaining: 28s
    5359:	learn: 58974.3781962	test: 114199.9321559	best: 114199.9321559 (5359)	total: 32.3s	remaining: 28s
    5360:	learn: 58971.8430063	test: 114199.0462122	best: 114199.0462122 (5360)	total: 32.4s	remaining: 28s
    5361:	learn: 58969.1765018	test: 114197.5826965	best: 114197.5826965 (5361)	total: 32.4s	remaining: 28s
    5362:	learn: 58966.2367813	test: 114198.6652242	best: 114197.5826965 (5361)	total: 32.4s	remaining: 28s
    5363:	learn: 58959.1988678	test: 114198.2839068	best: 114197.5826965 (5361)	total: 32.4s	remaining: 28s
    5364:	learn: 58948.4714554	test: 114190.5369241	best: 114190.5369241 (5364)	total: 32.4s	remaining: 28s
    5365:	learn: 58944.8352014	test: 114191.0579492	best: 114190.5369241 (5364)	total: 32.4s	remaining: 28s
    5366:	learn: 58940.9045089	test: 114189.7409066	best: 114189.7409066 (5366)	total: 32.4s	remaining: 28s
    5367:	learn: 58935.2994868	test: 114189.9258016	best: 114189.7409066 (5366)	total: 32.4s	remaining: 28s
    5368:	learn: 58929.0960754	test: 114189.8093703	best: 114189.7409066 (5366)	total: 32.4s	remaining: 27.9s
    5369:	learn: 58925.5048274	test: 114189.1128045	best: 114189.1128045 (5369)	total: 32.4s	remaining: 27.9s
    5370:	learn: 58915.9186039	test: 114191.7227162	best: 114189.1128045 (5369)	total: 32.4s	remaining: 27.9s
    5371:	learn: 58910.4282533	test: 114191.2945967	best: 114189.1128045 (5369)	total: 32.4s	remaining: 27.9s
    5372:	learn: 58905.1887772	test: 114191.3190060	best: 114189.1128045 (5369)	total: 32.4s	remaining: 27.9s
    5373:	learn: 58901.9872142	test: 114190.4741821	best: 114189.1128045 (5369)	total: 32.4s	remaining: 27.9s
    5374:	learn: 58895.9484993	test: 114188.7826876	best: 114188.7826876 (5374)	total: 32.4s	remaining: 27.9s
    5375:	learn: 58892.5712289	test: 114188.3460814	best: 114188.3460814 (5375)	total: 32.4s	remaining: 27.9s
    5376:	learn: 58889.6601843	test: 114189.0958058	best: 114188.3460814 (5375)	total: 32.4s	remaining: 27.9s
    5377:	learn: 58885.1031519	test: 114190.5343941	best: 114188.3460814 (5375)	total: 32.5s	remaining: 27.9s
    5378:	learn: 58882.0380441	test: 114188.4698246	best: 114188.3460814 (5375)	total: 32.5s	remaining: 27.9s
    5379:	learn: 58877.4446617	test: 114186.1499407	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5380:	learn: 58874.3593533	test: 114187.7746358	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5381:	learn: 58871.6015058	test: 114188.3289346	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5382:	learn: 58868.6462936	test: 114188.7469977	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5383:	learn: 58864.3917147	test: 114188.3064185	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5384:	learn: 58859.8975321	test: 114190.7173685	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.9s
    5385:	learn: 58857.2006815	test: 114191.4215308	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5386:	learn: 58851.6365019	test: 114190.1604565	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5387:	learn: 58847.8667466	test: 114191.4057743	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5388:	learn: 58845.3845889	test: 114191.8345429	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5389:	learn: 58841.7904536	test: 114190.0346289	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5390:	learn: 58838.2916976	test: 114188.7193926	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5391:	learn: 58833.6020786	test: 114189.0293881	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5392:	learn: 58828.4464773	test: 114189.6694640	best: 114186.1499407 (5379)	total: 32.5s	remaining: 27.8s
    5393:	learn: 58821.5867952	test: 114188.2555002	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5394:	learn: 58818.5571578	test: 114190.0643020	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5395:	learn: 58816.7070371	test: 114189.6283436	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5396:	learn: 58811.9115697	test: 114189.2879233	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5397:	learn: 58807.9039350	test: 114189.5960556	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5398:	learn: 58805.4426862	test: 114189.2914769	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5399:	learn: 58803.1120738	test: 114189.0300455	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5400:	learn: 58798.8138585	test: 114188.1686476	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5401:	learn: 58795.5397411	test: 114187.4014559	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.8s
    5402:	learn: 58791.3225077	test: 114186.5212435	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5403:	learn: 58785.7401454	test: 114188.4847815	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5404:	learn: 58781.6748386	test: 114190.6470192	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5405:	learn: 58776.9262914	test: 114191.4130484	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5406:	learn: 58774.9005611	test: 114191.7823795	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5407:	learn: 58769.5276352	test: 114191.7296343	best: 114186.1499407 (5379)	total: 32.6s	remaining: 27.7s
    5408:	learn: 58766.3600761	test: 114191.5988074	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5409:	learn: 58763.2013796	test: 114190.6082491	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5410:	learn: 58760.3059273	test: 114190.2379823	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5411:	learn: 58753.7897309	test: 114189.2664040	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5412:	learn: 58750.4881676	test: 114189.4124807	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5413:	learn: 58747.2651139	test: 114189.2989044	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5414:	learn: 58745.0526681	test: 114189.1247919	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5415:	learn: 58740.6562728	test: 114190.4632575	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5416:	learn: 58737.7881453	test: 114188.8645173	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5417:	learn: 58734.6977011	test: 114188.4748777	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5418:	learn: 58728.7336058	test: 114188.4567239	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5419:	learn: 58725.0036281	test: 114189.7563562	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.7s
    5420:	learn: 58721.1861628	test: 114192.0996151	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.6s
    5421:	learn: 58717.4549053	test: 114192.3919109	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.6s
    5422:	learn: 58711.5001242	test: 114193.1938237	best: 114186.1499407 (5379)	total: 32.7s	remaining: 27.6s
    5423:	learn: 58706.7159430	test: 114193.1993085	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5424:	learn: 58702.2233597	test: 114193.1614867	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5425:	learn: 58695.2181998	test: 114196.2468797	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5426:	learn: 58689.5891940	test: 114195.2593472	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5427:	learn: 58686.6968354	test: 114194.8017458	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5428:	learn: 58683.6953992	test: 114194.9078348	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5429:	learn: 58679.8837681	test: 114195.0210610	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5430:	learn: 58677.5133872	test: 114196.1201291	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5431:	learn: 58671.9091122	test: 114194.3972523	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5432:	learn: 58667.0764197	test: 114192.0675274	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5433:	learn: 58664.6028556	test: 114191.2670420	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5434:	learn: 58661.6566117	test: 114194.0674656	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5435:	learn: 58657.1595826	test: 114195.1343357	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5436:	learn: 58653.3521351	test: 114194.0092227	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5437:	learn: 58650.3220047	test: 114194.2926257	best: 114186.1499407 (5379)	total: 32.8s	remaining: 27.6s
    5438:	learn: 58647.2617703	test: 114195.5159864	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.6s
    5439:	learn: 58644.6129199	test: 114194.7187881	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5440:	learn: 58641.1385313	test: 114192.4955425	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5441:	learn: 58638.5160670	test: 114190.7381055	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5442:	learn: 58634.5924894	test: 114191.0556361	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5443:	learn: 58627.9126653	test: 114190.3415416	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5444:	learn: 58624.2008898	test: 114190.3399963	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5445:	learn: 58621.8257836	test: 114190.5078975	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5446:	learn: 58617.5039723	test: 114186.4961384	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5447:	learn: 58612.5998137	test: 114186.4615698	best: 114186.1499407 (5379)	total: 32.9s	remaining: 27.5s
    5448:	learn: 58608.1152682	test: 114185.1133819	best: 114185.1133819 (5448)	total: 32.9s	remaining: 27.5s
    5449:	learn: 58604.5884978	test: 114185.1513928	best: 114185.1133819 (5448)	total: 32.9s	remaining: 27.5s
    5450:	learn: 58598.8670127	test: 114184.8879576	best: 114184.8879576 (5450)	total: 32.9s	remaining: 27.5s
    5451:	learn: 58596.7859560	test: 114184.5739394	best: 114184.5739394 (5451)	total: 32.9s	remaining: 27.5s
    5452:	learn: 58592.6716997	test: 114186.8364034	best: 114184.5739394 (5451)	total: 32.9s	remaining: 27.5s
    5453:	learn: 58589.8166093	test: 114185.3626780	best: 114184.5739394 (5451)	total: 33s	remaining: 27.5s
    5454:	learn: 58585.7337401	test: 114182.1486327	best: 114182.1486327 (5454)	total: 33s	remaining: 27.5s
    5455:	learn: 58582.7238969	test: 114182.1328258	best: 114182.1328258 (5455)	total: 33s	remaining: 27.5s
    5456:	learn: 58578.8158840	test: 114184.5317160	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5457:	learn: 58575.1818285	test: 114186.4598503	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5458:	learn: 58572.4010509	test: 114186.9046662	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5459:	learn: 58566.6256682	test: 114186.7183403	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5460:	learn: 58562.7900050	test: 114187.9732585	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5461:	learn: 58558.7454010	test: 114188.4225589	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5462:	learn: 58554.9978117	test: 114188.1712245	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5463:	learn: 58553.6981338	test: 114192.0453596	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5464:	learn: 58551.8157621	test: 114193.1917202	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5465:	learn: 58549.4027489	test: 114192.6212858	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5466:	learn: 58545.7940457	test: 114190.2739581	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5467:	learn: 58543.2313896	test: 114189.5574340	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5468:	learn: 58538.7751860	test: 114189.0599795	best: 114182.1328258 (5455)	total: 33s	remaining: 27.4s
    5469:	learn: 58535.8250579	test: 114188.3232613	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.4s
    5470:	learn: 58533.4087787	test: 114190.1107532	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.4s
    5471:	learn: 58528.9465861	test: 114187.6228063	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.4s
    5472:	learn: 58526.3810178	test: 114187.0434294	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.4s
    5473:	learn: 58523.9540320	test: 114187.6440461	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.3s
    5474:	learn: 58520.3428246	test: 114184.8108808	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.3s
    5475:	learn: 58517.1207899	test: 114183.6311787	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.3s
    5476:	learn: 58512.9903119	test: 114183.2516644	best: 114182.1328258 (5455)	total: 33.1s	remaining: 27.3s
    5477:	learn: 58509.2476641	test: 114182.1097016	best: 114182.1097016 (5477)	total: 33.1s	remaining: 27.3s
    5478:	learn: 58508.1313556	test: 114182.0109511	best: 114182.0109511 (5478)	total: 33.1s	remaining: 27.3s
    5479:	learn: 58504.6640649	test: 114180.2590316	best: 114180.2590316 (5479)	total: 33.1s	remaining: 27.3s
    5480:	learn: 58501.4030705	test: 114179.4446374	best: 114179.4446374 (5480)	total: 33.1s	remaining: 27.3s
    5481:	learn: 58497.4930387	test: 114172.8471204	best: 114172.8471204 (5481)	total: 33.1s	remaining: 27.3s
    5482:	learn: 58495.7220681	test: 114173.9257990	best: 114172.8471204 (5481)	total: 33.1s	remaining: 27.3s
    5483:	learn: 58491.1373708	test: 114174.6376611	best: 114172.8471204 (5481)	total: 33.1s	remaining: 27.3s
    5484:	learn: 58487.9418414	test: 114173.5297449	best: 114172.8471204 (5481)	total: 33.1s	remaining: 27.3s
    5485:	learn: 58484.1289680	test: 114173.5033342	best: 114172.8471204 (5481)	total: 33.1s	remaining: 27.3s
    5486:	learn: 58480.2740902	test: 114173.0865313	best: 114172.8471204 (5481)	total: 33.2s	remaining: 27.3s
    5487:	learn: 58475.5883073	test: 114174.9420145	best: 114172.8471204 (5481)	total: 33.2s	remaining: 27.3s
    5488:	learn: 58471.4531217	test: 114173.1974960	best: 114172.8471204 (5481)	total: 33.2s	remaining: 27.3s
    5489:	learn: 58468.1470736	test: 114174.4041118	best: 114172.8471204 (5481)	total: 33.2s	remaining: 27.3s
    5490:	learn: 58465.2422633	test: 114174.0445991	best: 114172.8471204 (5481)	total: 33.2s	remaining: 27.2s
    5491:	learn: 58459.4847204	test: 114172.3091640	best: 114172.3091640 (5491)	total: 33.2s	remaining: 27.2s
    5492:	learn: 58453.7441243	test: 114171.6498982	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5493:	learn: 58445.4932582	test: 114174.8064167	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5494:	learn: 58440.9354070	test: 114178.2578078	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5495:	learn: 58436.5453998	test: 114177.5162536	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5496:	learn: 58428.5248929	test: 114175.3352853	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5497:	learn: 58421.5326491	test: 114173.9617740	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5498:	learn: 58416.4026855	test: 114174.8176424	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5499:	learn: 58414.3845628	test: 114173.2554884	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5500:	learn: 58410.8162874	test: 114173.3807173	best: 114171.6498982 (5492)	total: 33.2s	remaining: 27.2s
    5501:	learn: 58407.3683998	test: 114170.2414951	best: 114170.2414951 (5501)	total: 33.2s	remaining: 27.2s
    5502:	learn: 58403.3300576	test: 114169.0998242	best: 114169.0998242 (5502)	total: 33.3s	remaining: 27.2s
    5503:	learn: 58400.6732077	test: 114168.6059980	best: 114168.6059980 (5503)	total: 33.3s	remaining: 27.2s
    5504:	learn: 58397.9211178	test: 114169.3797585	best: 114168.6059980 (5503)	total: 33.3s	remaining: 27.2s
    5505:	learn: 58395.7152280	test: 114169.5949342	best: 114168.6059980 (5503)	total: 33.3s	remaining: 27.2s
    5506:	learn: 58389.2530601	test: 114168.0635425	best: 114168.0635425 (5506)	total: 33.3s	remaining: 27.1s
    5507:	learn: 58381.0283007	test: 114162.4171524	best: 114162.4171524 (5507)	total: 33.3s	remaining: 27.1s
    5508:	learn: 58377.7994067	test: 114159.8518580	best: 114159.8518580 (5508)	total: 33.3s	remaining: 27.1s
    5509:	learn: 58374.7227580	test: 114158.7641198	best: 114158.7641198 (5509)	total: 33.3s	remaining: 27.1s
    5510:	learn: 58373.1963890	test: 114158.8794384	best: 114158.7641198 (5509)	total: 33.3s	remaining: 27.1s
    5511:	learn: 58367.2890277	test: 114154.7712085	best: 114154.7712085 (5511)	total: 33.3s	remaining: 27.1s
    5512:	learn: 58360.1617493	test: 114154.9791264	best: 114154.7712085 (5511)	total: 33.3s	remaining: 27.1s
    5513:	learn: 58357.8482210	test: 114153.4145089	best: 114153.4145089 (5513)	total: 33.3s	remaining: 27.1s
    5514:	learn: 58356.0741076	test: 114153.0081461	best: 114153.0081461 (5514)	total: 33.3s	remaining: 27.1s
    5515:	learn: 58351.7579454	test: 114153.5849931	best: 114153.0081461 (5514)	total: 33.3s	remaining: 27.1s
    5516:	learn: 58347.7354584	test: 114151.8478652	best: 114151.8478652 (5516)	total: 33.3s	remaining: 27.1s
    5517:	learn: 58343.2623617	test: 114151.4119810	best: 114151.4119810 (5517)	total: 33.3s	remaining: 27.1s
    5518:	learn: 58340.5955916	test: 114149.6901909	best: 114149.6901909 (5518)	total: 33.3s	remaining: 27.1s
    5519:	learn: 58337.3825990	test: 114148.1066090	best: 114148.1066090 (5519)	total: 33.4s	remaining: 27.1s
    5520:	learn: 58332.8194058	test: 114148.7163041	best: 114148.1066090 (5519)	total: 33.4s	remaining: 27.1s
    5521:	learn: 58331.0971906	test: 114148.3400684	best: 114148.1066090 (5519)	total: 33.4s	remaining: 27.1s
    5522:	learn: 58328.7788385	test: 114148.8325550	best: 114148.1066090 (5519)	total: 33.4s	remaining: 27.1s
    5523:	learn: 58323.1634500	test: 114147.2147597	best: 114147.2147597 (5523)	total: 33.4s	remaining: 27s
    5524:	learn: 58317.3017209	test: 114146.3821035	best: 114146.3821035 (5524)	total: 33.4s	remaining: 27s
    5525:	learn: 58313.8443487	test: 114147.2672149	best: 114146.3821035 (5524)	total: 33.4s	remaining: 27s
    5526:	learn: 58308.6810313	test: 114146.3801790	best: 114146.3801790 (5526)	total: 33.4s	remaining: 27s
    5527:	learn: 58305.0875037	test: 114145.5887877	best: 114145.5887877 (5527)	total: 33.4s	remaining: 27s
    5528:	learn: 58301.6399856	test: 114146.4285016	best: 114145.5887877 (5527)	total: 33.4s	remaining: 27s
    5529:	learn: 58297.0573135	test: 114145.2940488	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5530:	learn: 58295.6012486	test: 114149.1935455	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5531:	learn: 58290.8659345	test: 114150.3587877	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5532:	learn: 58289.6782260	test: 114150.9711974	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5533:	learn: 58287.9288746	test: 114150.9611950	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5534:	learn: 58282.9845052	test: 114152.1192590	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5535:	learn: 58278.7940187	test: 114153.5987723	best: 114145.2940488 (5529)	total: 33.4s	remaining: 27s
    5536:	learn: 58277.5569923	test: 114154.1431098	best: 114145.2940488 (5529)	total: 33.5s	remaining: 27s
    5537:	learn: 58272.8268878	test: 114152.9794529	best: 114145.2940488 (5529)	total: 33.5s	remaining: 27s
    5538:	learn: 58270.7773336	test: 114153.6358246	best: 114145.2940488 (5529)	total: 33.5s	remaining: 27s
    5539:	learn: 58266.8664591	test: 114149.6878287	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5540:	learn: 58264.8449767	test: 114151.1342802	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5541:	learn: 58258.9130174	test: 114154.4116805	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5542:	learn: 58255.7973775	test: 114154.0771118	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5543:	learn: 58251.7698356	test: 114155.7726083	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5544:	learn: 58247.8154369	test: 114155.9038725	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5545:	learn: 58244.7107211	test: 114154.8243450	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5546:	learn: 58243.0329504	test: 114154.4676700	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5547:	learn: 58237.5710696	test: 114152.3892528	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5548:	learn: 58233.6612285	test: 114150.6773166	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5549:	learn: 58232.0175007	test: 114150.3419675	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5550:	learn: 58227.5165307	test: 114149.0558668	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5551:	learn: 58224.8845338	test: 114149.2315752	best: 114145.2940488 (5529)	total: 33.5s	remaining: 26.9s
    5552:	learn: 58218.9097758	test: 114151.5196539	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.9s
    5553:	learn: 58214.3228795	test: 114151.6969183	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.9s
    5554:	learn: 58212.3641939	test: 114150.2783153	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.9s
    5555:	learn: 58204.9840461	test: 114146.7621012	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.9s
    5556:	learn: 58199.7596557	test: 114147.5461533	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.9s
    5557:	learn: 58196.8762578	test: 114148.4339581	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5558:	learn: 58194.4808822	test: 114148.0898472	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5559:	learn: 58189.7997218	test: 114148.1941233	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5560:	learn: 58186.6144115	test: 114147.0866226	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5561:	learn: 58184.0290598	test: 114150.6857583	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5562:	learn: 58180.8746076	test: 114148.5442850	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5563:	learn: 58177.8200821	test: 114147.9478898	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5564:	learn: 58176.0836594	test: 114147.4965317	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5565:	learn: 58172.6737906	test: 114146.0692095	best: 114145.2940488 (5529)	total: 33.6s	remaining: 26.8s
    5566:	learn: 58168.3998416	test: 114144.6236879	best: 114144.6236879 (5566)	total: 33.6s	remaining: 26.8s
    5567:	learn: 58165.9464941	test: 114144.1184272	best: 114144.1184272 (5567)	total: 33.6s	remaining: 26.8s
    5568:	learn: 58162.9767504	test: 114147.3916886	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.8s
    5569:	learn: 58158.9454673	test: 114149.7071329	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.8s
    5570:	learn: 58153.9693685	test: 114146.9624013	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.8s
    5571:	learn: 58148.1173856	test: 114145.9234414	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.8s
    5572:	learn: 58145.4471129	test: 114148.2728299	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.8s
    5573:	learn: 58143.5449454	test: 114148.5869741	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5574:	learn: 58141.6206014	test: 114150.5821407	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5575:	learn: 58140.4236907	test: 114150.7557282	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5576:	learn: 58138.0528229	test: 114150.1435815	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5577:	learn: 58136.9070462	test: 114150.6572690	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5578:	learn: 58135.6264526	test: 114148.7837813	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5579:	learn: 58133.1023549	test: 114149.6036815	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5580:	learn: 58130.3397111	test: 114149.3900839	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5581:	learn: 58126.3692441	test: 114153.0024590	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5582:	learn: 58122.7909801	test: 114152.8908858	best: 114144.1184272 (5567)	total: 33.7s	remaining: 26.7s
    5583:	learn: 58118.9987471	test: 114152.2330649	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5584:	learn: 58117.3136239	test: 114150.0968355	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5585:	learn: 58115.7082900	test: 114149.7666507	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5586:	learn: 58112.2337221	test: 114149.1518924	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5587:	learn: 58107.6252339	test: 114147.0858779	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5588:	learn: 58106.6776622	test: 114147.3908198	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5589:	learn: 58104.1259985	test: 114147.3508574	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.7s
    5590:	learn: 58102.0506656	test: 114148.8761998	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5591:	learn: 58098.7911283	test: 114149.3547674	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5592:	learn: 58097.2279470	test: 114149.0479631	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5593:	learn: 58094.5153979	test: 114146.6932243	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5594:	learn: 58090.1026056	test: 114146.1179195	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5595:	learn: 58082.5541693	test: 114146.4795451	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5596:	learn: 58079.2204975	test: 114145.3258016	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5597:	learn: 58077.7691572	test: 114144.6828159	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5598:	learn: 58074.4735002	test: 114144.2522805	best: 114144.1184272 (5567)	total: 33.8s	remaining: 26.6s
    5599:	learn: 58070.0286960	test: 114143.5391710	best: 114143.5391710 (5599)	total: 33.9s	remaining: 26.6s
    5600:	learn: 58068.9633085	test: 114143.6149325	best: 114143.5391710 (5599)	total: 33.9s	remaining: 26.6s
    5601:	learn: 58064.0432842	test: 114142.7648039	best: 114142.7648039 (5601)	total: 33.9s	remaining: 26.6s
    5602:	learn: 58057.3288599	test: 114139.3774784	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5603:	learn: 58053.1687891	test: 114139.5656912	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5604:	learn: 58051.2132075	test: 114140.2347980	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5605:	learn: 58049.1964086	test: 114140.2968205	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5606:	learn: 58046.3261524	test: 114143.5113066	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5607:	learn: 58043.7053247	test: 114144.2077118	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.6s
    5608:	learn: 58041.4921847	test: 114143.2028665	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.5s
    5609:	learn: 58036.5940750	test: 114142.1865149	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.5s
    5610:	learn: 58032.7849630	test: 114139.4113483	best: 114139.3774784 (5602)	total: 33.9s	remaining: 26.5s
    5611:	learn: 58029.5927660	test: 114138.4254479	best: 114138.4254479 (5611)	total: 33.9s	remaining: 26.5s
    5612:	learn: 58023.5570535	test: 114137.2481261	best: 114137.2481261 (5612)	total: 33.9s	remaining: 26.5s
    5613:	learn: 58022.4068804	test: 114137.5357587	best: 114137.2481261 (5612)	total: 33.9s	remaining: 26.5s
    5614:	learn: 58015.7326201	test: 114136.2716316	best: 114136.2716316 (5614)	total: 33.9s	remaining: 26.5s
    5615:	learn: 58012.7561595	test: 114136.7742801	best: 114136.2716316 (5614)	total: 34s	remaining: 26.5s
    5616:	learn: 58008.7541511	test: 114134.1075879	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5617:	learn: 58006.6453384	test: 114134.8003440	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5618:	learn: 58003.2447830	test: 114136.5337042	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5619:	learn: 58001.7194344	test: 114136.2702376	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5620:	learn: 57997.5352903	test: 114138.5035580	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5621:	learn: 57994.2128928	test: 114139.5722091	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5622:	learn: 57991.2928743	test: 114140.1022972	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5623:	learn: 57989.5173511	test: 114139.6270286	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5624:	learn: 57984.9487164	test: 114137.7193069	best: 114134.1075879 (5616)	total: 34s	remaining: 26.5s
    5625:	learn: 57981.2857874	test: 114140.2963998	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5626:	learn: 57976.6042867	test: 114142.1090498	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5627:	learn: 57974.1587094	test: 114141.7223721	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5628:	learn: 57971.6704664	test: 114141.5367681	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5629:	learn: 57968.9218483	test: 114142.6576517	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5630:	learn: 57965.4330300	test: 114142.5821870	best: 114134.1075879 (5616)	total: 34s	remaining: 26.4s
    5631:	learn: 57963.5477128	test: 114142.4332403	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5632:	learn: 57961.7269797	test: 114143.0797184	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5633:	learn: 57957.7398486	test: 114141.8432832	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5634:	learn: 57951.4360497	test: 114141.7840199	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5635:	learn: 57947.4329566	test: 114141.6155505	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5636:	learn: 57943.9892680	test: 114140.1349565	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5637:	learn: 57939.9872912	test: 114141.4099204	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5638:	learn: 57934.9610791	test: 114142.0578406	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5639:	learn: 57931.4685213	test: 114142.3568543	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5640:	learn: 57925.0969279	test: 114143.8062334	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5641:	learn: 57923.6045136	test: 114143.5652547	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.4s
    5642:	learn: 57920.5916940	test: 114143.4319767	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5643:	learn: 57916.0305852	test: 114143.3768736	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5644:	learn: 57913.7234134	test: 114143.5608052	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5645:	learn: 57908.8997645	test: 114144.4345486	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5646:	learn: 57903.6261071	test: 114144.5458087	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5647:	learn: 57900.5244967	test: 114143.0847470	best: 114134.1075879 (5616)	total: 34.1s	remaining: 26.3s
    5648:	learn: 57896.4943193	test: 114142.4396225	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5649:	learn: 57895.4300729	test: 114142.0894045	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5650:	learn: 57892.2200736	test: 114142.2950513	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5651:	learn: 57890.4699757	test: 114144.3874550	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5652:	learn: 57886.9783360	test: 114145.4318869	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5653:	learn: 57884.0925747	test: 114145.4732623	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5654:	learn: 57876.6013560	test: 114143.7101574	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5655:	learn: 57870.9882039	test: 114142.9487458	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5656:	learn: 57869.5536397	test: 114143.1075982	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5657:	learn: 57864.3711624	test: 114142.7170451	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.3s
    5658:	learn: 57862.4033381	test: 114141.4602694	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5659:	learn: 57860.2499376	test: 114142.0841112	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5660:	learn: 57855.1340333	test: 114141.7198231	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5661:	learn: 57849.9143699	test: 114141.7871263	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5662:	learn: 57847.5283702	test: 114140.7026114	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5663:	learn: 57843.3328178	test: 114138.9494125	best: 114134.1075879 (5616)	total: 34.2s	remaining: 26.2s
    5664:	learn: 57839.7059274	test: 114139.5772080	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5665:	learn: 57836.8459003	test: 114139.8307932	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5666:	learn: 57834.6552626	test: 114139.4083417	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5667:	learn: 57827.7336589	test: 114139.4989668	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5668:	learn: 57821.6108178	test: 114140.3474957	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5669:	learn: 57817.5212046	test: 114140.8052022	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5670:	learn: 57815.3118282	test: 114143.6133078	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5671:	learn: 57812.0717438	test: 114143.1065738	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5672:	learn: 57810.8929079	test: 114143.4429039	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5673:	learn: 57805.2002148	test: 114140.8328290	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5674:	learn: 57800.6819869	test: 114137.7467505	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.2s
    5675:	learn: 57795.7446933	test: 114136.8545455	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5676:	learn: 57794.2040588	test: 114136.9879466	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5677:	learn: 57793.1367686	test: 114137.0674123	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5678:	learn: 57790.6046652	test: 114137.4430809	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5679:	learn: 57787.2462205	test: 114138.6351588	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5680:	learn: 57784.4798167	test: 114137.4799615	best: 114134.1075879 (5616)	total: 34.3s	remaining: 26.1s
    5681:	learn: 57777.8891300	test: 114138.6148464	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5682:	learn: 57775.8437773	test: 114138.6340551	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5683:	learn: 57771.5781716	test: 114137.1728233	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5684:	learn: 57768.9304688	test: 114137.6593143	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5685:	learn: 57764.6268411	test: 114138.5612155	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5686:	learn: 57763.1670271	test: 114138.3624685	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5687:	learn: 57758.2949702	test: 114137.0086989	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5688:	learn: 57752.4896047	test: 114136.1342176	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5689:	learn: 57750.0926178	test: 114135.9187506	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5690:	learn: 57747.0081244	test: 114134.2560973	best: 114134.1075879 (5616)	total: 34.4s	remaining: 26.1s
    5691:	learn: 57744.0604592	test: 114133.9557932	best: 114133.9557932 (5691)	total: 34.4s	remaining: 26.1s
    5692:	learn: 57739.5400208	test: 114132.5354754	best: 114132.5354754 (5692)	total: 34.4s	remaining: 26s
    5693:	learn: 57737.0271373	test: 114131.1529951	best: 114131.1529951 (5693)	total: 34.4s	remaining: 26s
    5694:	learn: 57728.8214196	test: 114127.7291432	best: 114127.7291432 (5694)	total: 34.4s	remaining: 26s
    5695:	learn: 57725.8873259	test: 114126.4143654	best: 114126.4143654 (5695)	total: 34.4s	remaining: 26s
    5696:	learn: 57724.4886598	test: 114126.6682910	best: 114126.4143654 (5695)	total: 34.4s	remaining: 26s
    5697:	learn: 57723.6535278	test: 114126.9720685	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5698:	learn: 57718.5148947	test: 114128.0451819	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5699:	learn: 57714.2361619	test: 114128.8440897	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5700:	learn: 57709.5931163	test: 114129.2207162	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5701:	learn: 57701.1724288	test: 114127.6378659	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5702:	learn: 57698.5606122	test: 114130.4827370	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5703:	learn: 57695.4626848	test: 114133.0123419	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5704:	learn: 57693.1995837	test: 114134.8948280	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5705:	learn: 57689.7315186	test: 114134.4376239	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5706:	learn: 57685.8621888	test: 114132.3144059	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5707:	learn: 57681.2613800	test: 114131.4452671	best: 114126.4143654 (5695)	total: 34.5s	remaining: 26s
    5708:	learn: 57678.7949725	test: 114130.6416817	best: 114126.4143654 (5695)	total: 34.5s	remaining: 25.9s
    5709:	learn: 57676.1776374	test: 114130.8161642	best: 114126.4143654 (5695)	total: 34.5s	remaining: 25.9s
    5710:	learn: 57671.5138185	test: 114131.0626767	best: 114126.4143654 (5695)	total: 34.5s	remaining: 25.9s
    5711:	learn: 57666.1822670	test: 114131.0363553	best: 114126.4143654 (5695)	total: 34.5s	remaining: 25.9s
    5712:	learn: 57662.4123064	test: 114131.2913612	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5713:	learn: 57658.5216849	test: 114132.1189326	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5714:	learn: 57654.8289576	test: 114131.3689639	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5715:	learn: 57648.3777205	test: 114129.3831905	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5716:	learn: 57646.2057915	test: 114129.1633942	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5717:	learn: 57639.8008119	test: 114127.4566698	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5718:	learn: 57637.0249503	test: 114128.3735202	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5719:	learn: 57633.8587912	test: 114130.4141865	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5720:	learn: 57629.8138401	test: 114130.5068725	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5721:	learn: 57626.9699980	test: 114130.5952585	best: 114126.4143654 (5695)	total: 34.6s	remaining: 25.9s
    5722:	learn: 57619.1388834	test: 114124.9135934	best: 114124.9135934 (5722)	total: 34.6s	remaining: 25.9s
    5723:	learn: 57616.6995166	test: 114125.2828708	best: 114124.9135934 (5722)	total: 34.6s	remaining: 25.9s
    5724:	learn: 57613.6301158	test: 114124.7573891	best: 114124.7573891 (5724)	total: 34.6s	remaining: 25.9s
    5725:	learn: 57610.2250580	test: 114124.0145459	best: 114124.0145459 (5725)	total: 34.6s	remaining: 25.9s
    5726:	learn: 57606.4202175	test: 114122.7496492	best: 114122.7496492 (5726)	total: 34.6s	remaining: 25.8s
    5727:	learn: 57602.1278224	test: 114121.1432672	best: 114121.1432672 (5727)	total: 34.7s	remaining: 25.8s
    5728:	learn: 57598.2774512	test: 114120.1483305	best: 114120.1483305 (5728)	total: 34.7s	remaining: 25.8s
    5729:	learn: 57595.9020520	test: 114120.3793924	best: 114120.1483305 (5728)	total: 34.7s	remaining: 25.8s
    5730:	learn: 57593.7854791	test: 114120.7099433	best: 114120.1483305 (5728)	total: 34.7s	remaining: 25.8s
    5731:	learn: 57589.3560374	test: 114120.1315360	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5732:	learn: 57583.7270936	test: 114121.9372074	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5733:	learn: 57580.3651020	test: 114121.8426232	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5734:	learn: 57576.7593210	test: 114121.3475795	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5735:	learn: 57573.0435645	test: 114124.4466598	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5736:	learn: 57567.9135112	test: 114123.6802727	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5737:	learn: 57566.2621537	test: 114123.5184791	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5738:	learn: 57565.6262264	test: 114124.7342705	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5739:	learn: 57562.0460038	test: 114124.1840628	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5740:	learn: 57558.2700047	test: 114123.0566479	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5741:	learn: 57556.1510621	test: 114123.5780171	best: 114120.1315360 (5731)	total: 34.7s	remaining: 25.8s
    5742:	learn: 57553.0137804	test: 114122.4132963	best: 114120.1315360 (5731)	total: 34.8s	remaining: 25.8s
    5743:	learn: 57550.9190905	test: 114122.8741299	best: 114120.1315360 (5731)	total: 34.8s	remaining: 25.8s
    5744:	learn: 57546.7167373	test: 114121.0385003	best: 114120.1315360 (5731)	total: 34.8s	remaining: 25.8s
    5745:	learn: 57543.6204992	test: 114120.8939605	best: 114120.1315360 (5731)	total: 34.8s	remaining: 25.7s
    5746:	learn: 57539.1346233	test: 114121.6632034	best: 114120.1315360 (5731)	total: 34.8s	remaining: 25.7s
    5747:	learn: 57533.1756235	test: 114119.7329078	best: 114119.7329078 (5747)	total: 34.8s	remaining: 25.7s
    5748:	learn: 57532.5366582	test: 114118.4616712	best: 114118.4616712 (5748)	total: 34.8s	remaining: 25.7s
    5749:	learn: 57527.4792973	test: 114118.6151377	best: 114118.4616712 (5748)	total: 34.8s	remaining: 25.7s
    5750:	learn: 57526.2818238	test: 114118.9906589	best: 114118.4616712 (5748)	total: 34.8s	remaining: 25.7s
    5751:	learn: 57521.7304915	test: 114118.5143926	best: 114118.4616712 (5748)	total: 34.8s	remaining: 25.7s
    5752:	learn: 57517.2462044	test: 114122.0773758	best: 114118.4616712 (5748)	total: 34.8s	remaining: 25.7s
    5753:	learn: 57512.6503907	test: 114117.1728669	best: 114117.1728669 (5753)	total: 34.8s	remaining: 25.7s
    5754:	learn: 57509.6100283	test: 114115.5574145	best: 114115.5574145 (5754)	total: 34.8s	remaining: 25.7s
    5755:	learn: 57506.3098573	test: 114114.0636302	best: 114114.0636302 (5755)	total: 34.8s	remaining: 25.7s
    5756:	learn: 57503.4014958	test: 114112.6613616	best: 114112.6613616 (5756)	total: 34.8s	remaining: 25.7s
    5757:	learn: 57497.5306952	test: 114112.2386267	best: 114112.2386267 (5757)	total: 34.9s	remaining: 25.7s
    5758:	learn: 57493.6835578	test: 114112.9280681	best: 114112.2386267 (5757)	total: 34.9s	remaining: 25.7s
    5759:	learn: 57488.8331413	test: 114110.6229902	best: 114110.6229902 (5759)	total: 34.9s	remaining: 25.7s
    5760:	learn: 57485.2566929	test: 114110.3485004	best: 114110.3485004 (5760)	total: 34.9s	remaining: 25.7s
    5761:	learn: 57482.1295042	test: 114109.5126746	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.7s
    5762:	learn: 57479.4474376	test: 114111.3823401	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5763:	learn: 57474.5665800	test: 114113.4510902	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5764:	learn: 57472.2197160	test: 114112.8082374	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5765:	learn: 57467.7872289	test: 114114.8539613	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5766:	learn: 57465.0082853	test: 114116.1521272	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5767:	learn: 57462.5764242	test: 114116.3115961	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5768:	learn: 57459.2112429	test: 114116.2345213	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5769:	learn: 57452.4337999	test: 114116.9300167	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5770:	learn: 57450.1239718	test: 114114.5429407	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5771:	learn: 57446.3697440	test: 114115.1192265	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5772:	learn: 57441.2613773	test: 114114.4796268	best: 114109.5126746 (5761)	total: 34.9s	remaining: 25.6s
    5773:	learn: 57439.0002827	test: 114115.5229484	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5774:	learn: 57433.8641423	test: 114116.1718657	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5775:	learn: 57430.0075787	test: 114115.7835831	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5776:	learn: 57425.2216768	test: 114115.1638377	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5777:	learn: 57420.3698045	test: 114114.0099566	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5778:	learn: 57417.9915744	test: 114113.3648242	best: 114109.5126746 (5761)	total: 35s	remaining: 25.6s
    5779:	learn: 57414.4323528	test: 114112.9587034	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5780:	learn: 57410.3161010	test: 114113.3240018	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5781:	learn: 57409.7238768	test: 114112.7430681	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5782:	learn: 57406.6215254	test: 114112.3942319	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5783:	learn: 57403.1002527	test: 114112.5837728	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5784:	learn: 57398.7746786	test: 114112.4384639	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5785:	learn: 57395.5885823	test: 114110.1734074	best: 114109.5126746 (5761)	total: 35s	remaining: 25.5s
    5786:	learn: 57390.4025078	test: 114107.8169756	best: 114107.8169756 (5786)	total: 35s	remaining: 25.5s
    5787:	learn: 57385.7433801	test: 114107.6215157	best: 114107.6215157 (5787)	total: 35s	remaining: 25.5s
    5788:	learn: 57382.5360963	test: 114107.5424630	best: 114107.5424630 (5788)	total: 35s	remaining: 25.5s
    5789:	learn: 57377.4095758	test: 114104.8259454	best: 114104.8259454 (5789)	total: 35s	remaining: 25.5s
    5790:	learn: 57373.2704275	test: 114105.4168064	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.5s
    5791:	learn: 57371.8419318	test: 114107.9016222	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.5s
    5792:	learn: 57367.5424820	test: 114108.6435735	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.5s
    5793:	learn: 57366.1936961	test: 114107.7715465	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.5s
    5794:	learn: 57365.1907324	test: 114107.6644574	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.5s
    5795:	learn: 57360.7199571	test: 114108.2887590	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5796:	learn: 57357.0352191	test: 114107.1783665	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5797:	learn: 57355.1561217	test: 114108.7756477	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5798:	learn: 57352.7639550	test: 114108.5398387	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5799:	learn: 57349.0371840	test: 114109.3808610	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5800:	learn: 57345.1337278	test: 114107.5986516	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5801:	learn: 57342.2269293	test: 114106.7021946	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5802:	learn: 57338.4751215	test: 114107.2189084	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5803:	learn: 57331.7130123	test: 114106.1744372	best: 114104.8259454 (5789)	total: 35.1s	remaining: 25.4s
    5804:	learn: 57327.9669075	test: 114104.6048070	best: 114104.6048070 (5804)	total: 35.1s	remaining: 25.4s
    5805:	learn: 57323.5783773	test: 114104.1260379	best: 114104.1260379 (5805)	total: 35.1s	remaining: 25.4s
    5806:	learn: 57320.7301686	test: 114103.4715187	best: 114103.4715187 (5806)	total: 35.2s	remaining: 25.4s
    5807:	learn: 57317.1843807	test: 114103.9246066	best: 114103.4715187 (5806)	total: 35.2s	remaining: 25.4s
    5808:	learn: 57314.1365155	test: 114103.8272209	best: 114103.4715187 (5806)	total: 35.2s	remaining: 25.4s
    5809:	learn: 57309.1522046	test: 114103.0600281	best: 114103.0600281 (5809)	total: 35.2s	remaining: 25.4s
    5810:	learn: 57307.0629410	test: 114103.4097116	best: 114103.0600281 (5809)	total: 35.2s	remaining: 25.4s
    5811:	learn: 57302.5848636	test: 114101.3264202	best: 114101.3264202 (5811)	total: 35.2s	remaining: 25.4s
    5812:	learn: 57299.7127743	test: 114101.9871289	best: 114101.3264202 (5811)	total: 35.2s	remaining: 25.3s
    5813:	learn: 57295.9630043	test: 114102.5144239	best: 114101.3264202 (5811)	total: 35.2s	remaining: 25.3s
    5814:	learn: 57292.4211209	test: 114104.1180461	best: 114101.3264202 (5811)	total: 35.2s	remaining: 25.3s
    5815:	learn: 57287.2526808	test: 114099.8586536	best: 114099.8586536 (5815)	total: 35.2s	remaining: 25.3s
    5816:	learn: 57285.0130323	test: 114099.1554684	best: 114099.1554684 (5816)	total: 35.2s	remaining: 25.3s
    5817:	learn: 57281.4268221	test: 114098.3075130	best: 114098.3075130 (5817)	total: 35.2s	remaining: 25.3s
    5818:	learn: 57279.7155364	test: 114098.6543641	best: 114098.3075130 (5817)	total: 35.2s	remaining: 25.3s
    5819:	learn: 57275.0865960	test: 114098.5263847	best: 114098.3075130 (5817)	total: 35.2s	remaining: 25.3s
    5820:	learn: 57272.0198486	test: 114099.9119880	best: 114098.3075130 (5817)	total: 35.2s	remaining: 25.3s
    5821:	learn: 57270.3412758	test: 114099.3772510	best: 114098.3075130 (5817)	total: 35.2s	remaining: 25.3s
    5822:	learn: 57265.8245118	test: 114099.3245954	best: 114098.3075130 (5817)	total: 35.3s	remaining: 25.3s
    5823:	learn: 57264.2297943	test: 114098.7176165	best: 114098.3075130 (5817)	total: 35.3s	remaining: 25.3s
    5824:	learn: 57260.9723130	test: 114099.0389851	best: 114098.3075130 (5817)	total: 35.3s	remaining: 25.3s
    5825:	learn: 57257.3830042	test: 114099.3524179	best: 114098.3075130 (5817)	total: 35.3s	remaining: 25.3s
    5826:	learn: 57253.3007360	test: 114098.8706243	best: 114098.3075130 (5817)	total: 35.3s	remaining: 25.3s
    5827:	learn: 57246.1689330	test: 114097.3156193	best: 114097.3156193 (5827)	total: 35.3s	remaining: 25.3s
    5828:	learn: 57241.7675825	test: 114096.3937480	best: 114096.3937480 (5828)	total: 35.3s	remaining: 25.3s
    5829:	learn: 57238.3791986	test: 114096.3675068	best: 114096.3675068 (5829)	total: 35.3s	remaining: 25.2s
    5830:	learn: 57235.1850467	test: 114095.6500634	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5831:	learn: 57232.6505240	test: 114097.3882384	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5832:	learn: 57230.3712143	test: 114096.3436461	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5833:	learn: 57226.4221863	test: 114098.2862312	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5834:	learn: 57222.1744532	test: 114098.2848887	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5835:	learn: 57216.5318883	test: 114098.4453286	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5836:	learn: 57211.5893102	test: 114098.8658935	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5837:	learn: 57206.6525044	test: 114098.1106592	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5838:	learn: 57204.3626469	test: 114098.0550740	best: 114095.6500634 (5830)	total: 35.3s	remaining: 25.2s
    5839:	learn: 57199.1699444	test: 114097.6158152	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.2s
    5840:	learn: 57196.1078232	test: 114097.7456394	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.2s
    5841:	learn: 57191.8951121	test: 114099.0425749	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.2s
    5842:	learn: 57188.8161584	test: 114101.8639068	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.2s
    5843:	learn: 57185.1673449	test: 114102.3460659	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.2s
    5844:	learn: 57183.1060075	test: 114102.0497442	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.1s
    5845:	learn: 57181.1653080	test: 114100.7101285	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.1s
    5846:	learn: 57178.9030951	test: 114100.2554082	best: 114095.6500634 (5830)	total: 35.4s	remaining: 25.1s
    5847:	learn: 57174.0312703	test: 114095.5241141	best: 114095.5241141 (5847)	total: 35.4s	remaining: 25.1s
    5848:	learn: 57167.6302911	test: 114095.0204660	best: 114095.0204660 (5848)	total: 35.4s	remaining: 25.1s
    5849:	learn: 57160.7685770	test: 114096.9933513	best: 114095.0204660 (5848)	total: 35.4s	remaining: 25.1s
    5850:	learn: 57155.8016417	test: 114098.0113795	best: 114095.0204660 (5848)	total: 35.4s	remaining: 25.1s
    5851:	learn: 57152.0831029	test: 114097.4507057	best: 114095.0204660 (5848)	total: 35.4s	remaining: 25.1s
    5852:	learn: 57147.5568851	test: 114095.9989447	best: 114095.0204660 (5848)	total: 35.4s	remaining: 25.1s
    5853:	learn: 57144.5138054	test: 114093.3473921	best: 114093.3473921 (5853)	total: 35.4s	remaining: 25.1s
    5854:	learn: 57142.3262774	test: 114093.6452669	best: 114093.3473921 (5853)	total: 35.4s	remaining: 25.1s
    5855:	learn: 57139.2835887	test: 114090.7610420	best: 114090.7610420 (5855)	total: 35.5s	remaining: 25.1s
    5856:	learn: 57136.3724394	test: 114090.1616520	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5857:	learn: 57135.0337225	test: 114090.4374242	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5858:	learn: 57129.8230768	test: 114093.0371311	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5859:	learn: 57127.3044745	test: 114096.2248607	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5860:	learn: 57121.7044047	test: 114095.9305784	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5861:	learn: 57119.2817478	test: 114095.3529993	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25.1s
    5862:	learn: 57111.7621751	test: 114090.8973601	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25s
    5863:	learn: 57108.4000234	test: 114091.1922936	best: 114090.1616520 (5856)	total: 35.5s	remaining: 25s
    5864:	learn: 57101.7578675	test: 114088.6283225	best: 114088.6283225 (5864)	total: 35.5s	remaining: 25s
    5865:	learn: 57096.2636598	test: 114084.5412783	best: 114084.5412783 (5865)	total: 35.5s	remaining: 25s
    5866:	learn: 57092.8365170	test: 114084.3950228	best: 114084.3950228 (5866)	total: 35.5s	remaining: 25s
    5867:	learn: 57087.8001997	test: 114086.4772240	best: 114084.3950228 (5866)	total: 35.5s	remaining: 25s
    5868:	learn: 57083.3102088	test: 114085.8514727	best: 114084.3950228 (5866)	total: 35.5s	remaining: 25s
    5869:	learn: 57079.8432287	test: 114085.0577846	best: 114084.3950228 (5866)	total: 35.5s	remaining: 25s
    5870:	learn: 57077.8687516	test: 114085.0932289	best: 114084.3950228 (5866)	total: 35.6s	remaining: 25s
    5871:	learn: 57073.3358599	test: 114084.2570012	best: 114084.2570012 (5871)	total: 35.6s	remaining: 25s
    5872:	learn: 57070.1985089	test: 114084.6087410	best: 114084.2570012 (5871)	total: 35.6s	remaining: 25s
    5873:	learn: 57067.3445341	test: 114085.3030511	best: 114084.2570012 (5871)	total: 35.6s	remaining: 25s
    5874:	learn: 57064.4689856	test: 114086.0752703	best: 114084.2570012 (5871)	total: 35.6s	remaining: 25s
    5875:	learn: 57061.1645398	test: 114085.0400150	best: 114084.2570012 (5871)	total: 35.6s	remaining: 25s
    5876:	learn: 57057.3127425	test: 114082.8651981	best: 114082.8651981 (5876)	total: 35.6s	remaining: 25s
    5877:	learn: 57054.1369184	test: 114082.3315989	best: 114082.3315989 (5877)	total: 35.6s	remaining: 25s
    5878:	learn: 57049.8157013	test: 114081.3785837	best: 114081.3785837 (5878)	total: 35.6s	remaining: 25s
    5879:	learn: 57045.2073416	test: 114080.1856778	best: 114080.1856778 (5879)	total: 35.6s	remaining: 25s
    5880:	learn: 57039.3401652	test: 114079.6146886	best: 114079.6146886 (5880)	total: 35.6s	remaining: 24.9s
    5881:	learn: 57033.7243042	test: 114080.9365477	best: 114079.6146886 (5880)	total: 35.6s	remaining: 24.9s
    5882:	learn: 57030.0052703	test: 114078.8173548	best: 114078.8173548 (5882)	total: 35.6s	remaining: 24.9s
    5883:	learn: 57025.8264588	test: 114080.6754226	best: 114078.8173548 (5882)	total: 35.6s	remaining: 24.9s
    5884:	learn: 57021.9571055	test: 114080.1900248	best: 114078.8173548 (5882)	total: 35.6s	remaining: 24.9s
    5885:	learn: 57018.3196508	test: 114078.4299905	best: 114078.4299905 (5885)	total: 35.7s	remaining: 24.9s
    5886:	learn: 57012.3490334	test: 114080.8400781	best: 114078.4299905 (5885)	total: 35.7s	remaining: 24.9s
    5887:	learn: 57010.9427389	test: 114080.6368247	best: 114078.4299905 (5885)	total: 35.7s	remaining: 24.9s
    5888:	learn: 57007.8490383	test: 114080.6867220	best: 114078.4299905 (5885)	total: 35.7s	remaining: 24.9s
    5889:	learn: 57004.2828594	test: 114077.1475745	best: 114077.1475745 (5889)	total: 35.7s	remaining: 24.9s
    5890:	learn: 56999.8305551	test: 114075.6022747	best: 114075.6022747 (5890)	total: 35.7s	remaining: 24.9s
    5891:	learn: 56996.3163895	test: 114075.5977330	best: 114075.5977330 (5891)	total: 35.7s	remaining: 24.9s
    5892:	learn: 56992.1455307	test: 114072.7213651	best: 114072.7213651 (5892)	total: 35.7s	remaining: 24.9s
    5893:	learn: 56989.6049704	test: 114071.6974877	best: 114071.6974877 (5893)	total: 35.7s	remaining: 24.9s
    5894:	learn: 56985.2529499	test: 114071.9343035	best: 114071.6974877 (5893)	total: 35.7s	remaining: 24.9s
    5895:	learn: 56981.4610623	test: 114072.4560537	best: 114071.6974877 (5893)	total: 35.7s	remaining: 24.9s
    5896:	learn: 56979.9070895	test: 114072.1892277	best: 114071.6974877 (5893)	total: 35.7s	remaining: 24.9s
    5897:	learn: 56977.1325764	test: 114072.0695405	best: 114071.6974877 (5893)	total: 35.7s	remaining: 24.9s
    5898:	learn: 56973.0508089	test: 114071.2518366	best: 114071.2518366 (5898)	total: 35.7s	remaining: 24.8s
    5899:	learn: 56970.1560191	test: 114071.6930469	best: 114071.2518366 (5898)	total: 35.7s	remaining: 24.8s
    5900:	learn: 56967.8121438	test: 114073.6042707	best: 114071.2518366 (5898)	total: 35.8s	remaining: 24.8s
    5901:	learn: 56966.5962355	test: 114073.8912855	best: 114071.2518366 (5898)	total: 35.8s	remaining: 24.8s
    5902:	learn: 56963.8158830	test: 114069.0759848	best: 114069.0759848 (5902)	total: 35.8s	remaining: 24.8s
    5903:	learn: 56959.7458469	test: 114066.3599633	best: 114066.3599633 (5903)	total: 35.8s	remaining: 24.8s
    5904:	learn: 56958.1530857	test: 114065.7795137	best: 114065.7795137 (5904)	total: 35.8s	remaining: 24.8s
    5905:	learn: 56952.8814367	test: 114064.9196820	best: 114064.9196820 (5905)	total: 35.8s	remaining: 24.8s
    5906:	learn: 56948.4800180	test: 114064.3798323	best: 114064.3798323 (5906)	total: 35.8s	remaining: 24.8s
    5907:	learn: 56945.1542182	test: 114064.2494319	best: 114064.2494319 (5907)	total: 35.8s	remaining: 24.8s
    5908:	learn: 56943.4343773	test: 114063.8839885	best: 114063.8839885 (5908)	total: 35.8s	remaining: 24.8s
    5909:	learn: 56937.4662348	test: 114063.6897375	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5910:	learn: 56933.4541522	test: 114064.4361059	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5911:	learn: 56929.7878082	test: 114064.9228834	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5912:	learn: 56929.4703325	test: 114065.7452000	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5913:	learn: 56923.1331167	test: 114070.1313883	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5914:	learn: 56919.7260532	test: 114068.4506365	best: 114063.6897375 (5909)	total: 35.8s	remaining: 24.8s
    5915:	learn: 56917.2325421	test: 114068.6511946	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5916:	learn: 56914.0636821	test: 114067.2949334	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5917:	learn: 56911.7559495	test: 114067.2629143	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5918:	learn: 56908.6343578	test: 114068.2891543	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5919:	learn: 56904.3627419	test: 114067.2950397	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5920:	learn: 56902.1725624	test: 114068.0513299	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5921:	learn: 56896.6825055	test: 114068.3545209	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5922:	learn: 56894.0456755	test: 114067.3801593	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5923:	learn: 56890.1424676	test: 114065.9413899	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5924:	learn: 56886.3938158	test: 114068.6147209	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5925:	learn: 56882.3977024	test: 114066.5696520	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5926:	learn: 56880.2183727	test: 114067.7365468	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5927:	learn: 56877.0486431	test: 114066.1915240	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5928:	learn: 56873.3776202	test: 114065.2064469	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5929:	learn: 56870.4435720	test: 114064.2232259	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5930:	learn: 56866.8665555	test: 114064.5280024	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5931:	learn: 56865.6568937	test: 114064.5624746	best: 114063.6897375 (5909)	total: 35.9s	remaining: 24.7s
    5932:	learn: 56862.7998954	test: 114065.7341277	best: 114063.6897375 (5909)	total: 36s	remaining: 24.6s
    5933:	learn: 56857.5026592	test: 114063.3463860	best: 114063.3463860 (5933)	total: 36s	remaining: 24.6s
    5934:	learn: 56856.4608189	test: 114064.2487944	best: 114063.3463860 (5933)	total: 36s	remaining: 24.6s
    5935:	learn: 56854.6247632	test: 114063.3051284	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5936:	learn: 56851.1288050	test: 114064.1814560	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5937:	learn: 56848.1825622	test: 114063.9704400	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5938:	learn: 56846.0089500	test: 114063.9405041	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5939:	learn: 56845.4229056	test: 114063.9161410	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5940:	learn: 56840.4696360	test: 114066.6261064	best: 114063.3051284 (5935)	total: 36s	remaining: 24.6s
    5941:	learn: 56838.1915035	test: 114060.9085351	best: 114060.9085351 (5941)	total: 36s	remaining: 24.6s
    5942:	learn: 56835.6880654	test: 114060.2660072	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5943:	learn: 56831.9077537	test: 114060.3579086	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5944:	learn: 56831.8434465	test: 114060.3433712	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5945:	learn: 56829.1267674	test: 114061.1566951	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5946:	learn: 56825.8438632	test: 114061.4397906	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5947:	learn: 56822.9195178	test: 114061.1106170	best: 114060.2660072 (5942)	total: 36s	remaining: 24.6s
    5948:	learn: 56819.0522561	test: 114059.1444969	best: 114059.1444969 (5948)	total: 36s	remaining: 24.5s
    5949:	learn: 56816.2154692	test: 114059.8206681	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5950:	learn: 56814.0798989	test: 114060.5894149	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5951:	learn: 56812.1473536	test: 114060.3028342	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5952:	learn: 56808.2160664	test: 114060.1627437	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5953:	learn: 56804.0071694	test: 114061.3306948	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5954:	learn: 56799.9194116	test: 114061.9500948	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5955:	learn: 56796.8681344	test: 114061.8691532	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5956:	learn: 56793.1327866	test: 114061.3096010	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5957:	learn: 56789.7029339	test: 114061.1813726	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5958:	learn: 56783.7541080	test: 114061.6497688	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5959:	learn: 56780.3300140	test: 114062.8693629	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5960:	learn: 56778.6736771	test: 114062.6431228	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5961:	learn: 56775.7806742	test: 114062.2807198	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5962:	learn: 56773.3008240	test: 114062.6021426	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5963:	learn: 56769.9872452	test: 114062.8794198	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.5s
    5964:	learn: 56767.0858760	test: 114061.9870330	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.4s
    5965:	learn: 56763.4890263	test: 114059.4685558	best: 114059.1444969 (5948)	total: 36.1s	remaining: 24.4s
    5966:	learn: 56761.4601836	test: 114059.2530523	best: 114059.1444969 (5948)	total: 36.2s	remaining: 24.4s
    5967:	learn: 56758.4543871	test: 114058.6774588	best: 114058.6774588 (5967)	total: 36.2s	remaining: 24.4s
    5968:	learn: 56755.3602919	test: 114059.2076226	best: 114058.6774588 (5967)	total: 36.2s	remaining: 24.4s
    5969:	learn: 56751.4748228	test: 114057.1432589	best: 114057.1432589 (5969)	total: 36.2s	remaining: 24.4s
    5970:	learn: 56750.5035309	test: 114056.1128129	best: 114056.1128129 (5970)	total: 36.2s	remaining: 24.4s
    5971:	learn: 56745.1367503	test: 114053.0183045	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5972:	learn: 56744.0977381	test: 114053.4861485	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5973:	learn: 56740.8630600	test: 114054.0294787	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5974:	learn: 56739.8808004	test: 114053.9926340	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5975:	learn: 56735.3171684	test: 114054.1731260	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5976:	learn: 56733.2251737	test: 114054.9421191	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5977:	learn: 56731.9518256	test: 114053.9299263	best: 114053.0183045 (5971)	total: 36.2s	remaining: 24.4s
    5978:	learn: 56729.7207142	test: 114052.1405400	best: 114052.1405400 (5978)	total: 36.2s	remaining: 24.4s
    5979:	learn: 56725.7027361	test: 114052.0958158	best: 114052.0958158 (5979)	total: 36.2s	remaining: 24.4s
    5980:	learn: 56723.8547406	test: 114051.4745426	best: 114051.4745426 (5980)	total: 36.2s	remaining: 24.3s
    5981:	learn: 56719.5165124	test: 114051.0428786	best: 114051.0428786 (5981)	total: 36.2s	remaining: 24.3s
    5982:	learn: 56715.4077299	test: 114051.0898199	best: 114051.0428786 (5981)	total: 36.2s	remaining: 24.3s
    5983:	learn: 56711.2002820	test: 114049.3409802	best: 114049.3409802 (5983)	total: 36.3s	remaining: 24.3s
    5984:	learn: 56707.8970373	test: 114050.0201122	best: 114049.3409802 (5983)	total: 36.3s	remaining: 24.3s
    5985:	learn: 56703.2824855	test: 114049.9301017	best: 114049.3409802 (5983)	total: 36.3s	remaining: 24.3s
    5986:	learn: 56698.6898060	test: 114047.4912050	best: 114047.4912050 (5986)	total: 36.3s	remaining: 24.3s
    5987:	learn: 56694.5760170	test: 114047.3384977	best: 114047.3384977 (5987)	total: 36.3s	remaining: 24.3s
    5988:	learn: 56690.5188739	test: 114046.7054197	best: 114046.7054197 (5988)	total: 36.3s	remaining: 24.3s
    5989:	learn: 56689.3526930	test: 114045.5656045	best: 114045.5656045 (5989)	total: 36.3s	remaining: 24.3s
    5990:	learn: 56685.0180217	test: 114044.8225192	best: 114044.8225192 (5990)	total: 36.3s	remaining: 24.3s
    5991:	learn: 56684.5124427	test: 114044.8105270	best: 114044.8105270 (5991)	total: 36.3s	remaining: 24.3s
    5992:	learn: 56681.6370472	test: 114044.6665446	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.3s
    5993:	learn: 56679.2904984	test: 114045.7495840	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.3s
    5994:	learn: 56675.9870764	test: 114045.4253064	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.3s
    5995:	learn: 56672.1359066	test: 114045.5204576	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.3s
    5996:	learn: 56669.1076166	test: 114046.4952147	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.3s
    5997:	learn: 56666.8442145	test: 114047.4248386	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.2s
    5998:	learn: 56661.9204074	test: 114045.4103333	best: 114044.6665446 (5992)	total: 36.3s	remaining: 24.2s
    5999:	learn: 56657.1878377	test: 114046.0631199	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6000:	learn: 56652.7774838	test: 114045.7602450	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6001:	learn: 56651.8898003	test: 114045.4291694	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6002:	learn: 56648.2193312	test: 114050.2152514	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6003:	learn: 56645.0749716	test: 114050.1599751	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6004:	learn: 56642.4593232	test: 114051.3485949	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6005:	learn: 56639.7080606	test: 114052.8230736	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6006:	learn: 56634.5068665	test: 114052.9053892	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6007:	learn: 56630.7123260	test: 114051.0009131	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6008:	learn: 56627.4136430	test: 114051.9983672	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6009:	learn: 56622.9238138	test: 114052.8361084	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6010:	learn: 56622.2091127	test: 114052.5920093	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6011:	learn: 56618.0665999	test: 114052.6383483	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6012:	learn: 56613.5561917	test: 114052.4457527	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6013:	learn: 56609.7430517	test: 114051.7744797	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.2s
    6014:	learn: 56606.6548868	test: 114053.5605233	best: 114044.6665446 (5992)	total: 36.4s	remaining: 24.1s
    6015:	learn: 56603.7568798	test: 114054.5810245	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6016:	learn: 56600.9391171	test: 114054.0316988	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6017:	learn: 56597.9302850	test: 114052.7557937	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6018:	learn: 56595.8436142	test: 114053.0261966	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6019:	learn: 56592.1027804	test: 114051.3375759	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6020:	learn: 56587.6366418	test: 114051.0469999	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6021:	learn: 56582.9204513	test: 114048.9780153	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6022:	learn: 56577.4708725	test: 114048.1248172	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6023:	learn: 56574.3638669	test: 114046.6002862	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6024:	learn: 56568.0816717	test: 114046.5697630	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6025:	learn: 56565.0507491	test: 114045.7727449	best: 114044.6665446 (5992)	total: 36.5s	remaining: 24.1s
    6026:	learn: 56560.4112214	test: 114044.3355779	best: 114044.3355779 (6026)	total: 36.5s	remaining: 24.1s
    6027:	learn: 56550.8672461	test: 114037.0237110	best: 114037.0237110 (6027)	total: 36.5s	remaining: 24.1s
    6028:	learn: 56546.8470655	test: 114037.2253458	best: 114037.0237110 (6027)	total: 36.5s	remaining: 24.1s
    6029:	learn: 56542.7520899	test: 114035.6231694	best: 114035.6231694 (6029)	total: 36.5s	remaining: 24.1s
    6030:	learn: 56536.4793732	test: 114036.0236761	best: 114035.6231694 (6029)	total: 36.5s	remaining: 24.1s
    6031:	learn: 56532.4457731	test: 114036.5477692	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6032:	learn: 56527.6607483	test: 114037.5095872	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6033:	learn: 56525.7058369	test: 114036.3992885	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6034:	learn: 56519.6545321	test: 114036.5672931	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6035:	learn: 56517.5129104	test: 114036.2954184	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6036:	learn: 56514.9252145	test: 114037.6217252	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6037:	learn: 56511.5619401	test: 114038.0805494	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6038:	learn: 56509.0949287	test: 114037.0240272	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6039:	learn: 56504.6398506	test: 114036.7972374	best: 114035.6231694 (6029)	total: 36.6s	remaining: 24s
    6040:	learn: 56498.5209737	test: 114033.5142131	best: 114033.5142131 (6040)	total: 36.6s	remaining: 24s
    6041:	learn: 56496.6938756	test: 114033.4669708	best: 114033.4669708 (6041)	total: 36.6s	remaining: 24s
    6042:	learn: 56494.0123683	test: 114032.1669797	best: 114032.1669797 (6042)	total: 36.6s	remaining: 24s
    6043:	learn: 56491.4335155	test: 114035.4201521	best: 114032.1669797 (6042)	total: 36.6s	remaining: 24s
    6044:	learn: 56491.3855186	test: 114035.1633949	best: 114032.1669797 (6042)	total: 36.6s	remaining: 24s
    6045:	learn: 56485.2775206	test: 114035.0049026	best: 114032.1669797 (6042)	total: 36.6s	remaining: 24s
    6046:	learn: 56480.2990964	test: 114033.2862101	best: 114032.1669797 (6042)	total: 36.7s	remaining: 24s
    6047:	learn: 56477.6766096	test: 114032.7820942	best: 114032.1669797 (6042)	total: 36.7s	remaining: 24s
    6048:	learn: 56470.1695117	test: 114031.0523306	best: 114031.0523306 (6048)	total: 36.7s	remaining: 24s
    6049:	learn: 56468.5002087	test: 114031.3161251	best: 114031.0523306 (6048)	total: 36.7s	remaining: 23.9s
    6050:	learn: 56462.7672108	test: 114031.6764849	best: 114031.0523306 (6048)	total: 36.7s	remaining: 23.9s
    6051:	learn: 56456.5594534	test: 114029.5543813	best: 114029.5543813 (6051)	total: 36.7s	remaining: 23.9s
    6052:	learn: 56454.2271289	test: 114029.5720651	best: 114029.5543813 (6051)	total: 36.7s	remaining: 23.9s
    6053:	learn: 56448.5678440	test: 114027.1114939	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6054:	learn: 56444.0361385	test: 114029.5483404	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6055:	learn: 56440.4202173	test: 114029.5127235	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6056:	learn: 56436.3337690	test: 114027.4985455	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6057:	learn: 56432.7002049	test: 114029.7230311	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6058:	learn: 56429.5211676	test: 114028.9017925	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6059:	learn: 56429.1067687	test: 114029.6804674	best: 114027.1114939 (6053)	total: 36.7s	remaining: 23.9s
    6060:	learn: 56425.3767174	test: 114027.8112171	best: 114027.1114939 (6053)	total: 36.8s	remaining: 23.9s
    6061:	learn: 56422.3027147	test: 114028.9378459	best: 114027.1114939 (6053)	total: 36.8s	remaining: 23.9s
    6062:	learn: 56418.2999112	test: 114027.6175970	best: 114027.1114939 (6053)	total: 36.8s	remaining: 23.9s
    6063:	learn: 56416.1619517	test: 114026.1963918	best: 114026.1963918 (6063)	total: 36.8s	remaining: 23.9s
    6064:	learn: 56409.9594106	test: 114025.3432929	best: 114025.3432929 (6064)	total: 36.8s	remaining: 23.9s
    6065:	learn: 56407.8705253	test: 114026.4432146	best: 114025.3432929 (6064)	total: 36.8s	remaining: 23.9s
    6066:	learn: 56404.9450135	test: 114025.2915534	best: 114025.2915534 (6066)	total: 36.8s	remaining: 23.9s
    6067:	learn: 56400.8693825	test: 114024.0488751	best: 114024.0488751 (6067)	total: 36.8s	remaining: 23.8s
    6068:	learn: 56393.9976316	test: 114024.0461575	best: 114024.0461575 (6068)	total: 36.8s	remaining: 23.8s
    6069:	learn: 56391.8415117	test: 114024.6066340	best: 114024.0461575 (6068)	total: 36.8s	remaining: 23.8s
    6070:	learn: 56387.5782919	test: 114022.3145782	best: 114022.3145782 (6070)	total: 36.8s	remaining: 23.8s
    6071:	learn: 56384.8313449	test: 114022.1653999	best: 114022.1653999 (6071)	total: 36.8s	remaining: 23.8s
    6072:	learn: 56382.0690884	test: 114025.3208071	best: 114022.1653999 (6071)	total: 36.8s	remaining: 23.8s
    6073:	learn: 56377.6013248	test: 114027.6348078	best: 114022.1653999 (6071)	total: 36.8s	remaining: 23.8s
    6074:	learn: 56373.5075262	test: 114028.7359788	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6075:	learn: 56369.4179325	test: 114030.1263708	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6076:	learn: 56366.2152312	test: 114029.5506673	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6077:	learn: 56363.0436414	test: 114030.1358339	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6078:	learn: 56357.7662655	test: 114028.1704416	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6079:	learn: 56353.1240297	test: 114025.7397867	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6080:	learn: 56351.5250833	test: 114025.2758255	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6081:	learn: 56345.2746477	test: 114026.8199989	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6082:	learn: 56341.2132886	test: 114030.9726827	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6083:	learn: 56336.1315914	test: 114030.2000743	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6084:	learn: 56331.8437784	test: 114030.9003655	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.8s
    6085:	learn: 56325.9730681	test: 114030.4555505	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.7s
    6086:	learn: 56319.9304688	test: 114027.5855851	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.7s
    6087:	learn: 56316.0093483	test: 114027.5614411	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.7s
    6088:	learn: 56310.7914303	test: 114026.0617092	best: 114022.1653999 (6071)	total: 36.9s	remaining: 23.7s
    6089:	learn: 56309.0072740	test: 114024.6258211	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6090:	learn: 56305.7501230	test: 114024.7320399	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6091:	learn: 56301.3780804	test: 114025.1049454	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6092:	learn: 56298.4876510	test: 114024.0446983	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6093:	learn: 56295.6609806	test: 114026.0547989	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6094:	learn: 56290.1908275	test: 114026.0438078	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6095:	learn: 56286.1431981	test: 114025.5432832	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6096:	learn: 56283.3823399	test: 114024.1742167	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6097:	learn: 56281.6688242	test: 114026.7736463	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6098:	learn: 56277.0286729	test: 114025.0990358	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6099:	learn: 56274.1623431	test: 114024.6724260	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6100:	learn: 56271.1992481	test: 114023.7109063	best: 114022.1653999 (6071)	total: 37s	remaining: 23.7s
    6101:	learn: 56267.3846355	test: 114029.5399583	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.7s
    6102:	learn: 56263.3377450	test: 114029.3116488	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.7s
    6103:	learn: 56256.6107193	test: 114029.5037093	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.7s
    6104:	learn: 56253.5191893	test: 114028.8062831	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.7s
    6105:	learn: 56247.9238893	test: 114025.7388502	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6106:	learn: 56242.0442900	test: 114028.2948604	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6107:	learn: 56237.7754645	test: 114028.8557083	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6108:	learn: 56234.1488368	test: 114027.4498695	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6109:	learn: 56231.1601537	test: 114028.2163747	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6110:	learn: 56228.3599500	test: 114029.4644807	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6111:	learn: 56228.1376806	test: 114029.2076165	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6112:	learn: 56225.6760130	test: 114028.8832776	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6113:	learn: 56217.4970222	test: 114025.2320423	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6114:	learn: 56214.1648477	test: 114024.2849635	best: 114022.1653999 (6071)	total: 37.1s	remaining: 23.6s
    6115:	learn: 56212.6193009	test: 114024.5149345	best: 114022.1653999 (6071)	total: 37.2s	remaining: 23.6s
    6116:	learn: 56211.4408740	test: 114023.2980263	best: 114022.1653999 (6071)	total: 37.2s	remaining: 23.6s
    6117:	learn: 56206.4482142	test: 114018.9302566	best: 114018.9302566 (6117)	total: 37.2s	remaining: 23.6s
    6118:	learn: 56204.4349229	test: 114017.5624428	best: 114017.5624428 (6118)	total: 37.2s	remaining: 23.6s
    6119:	learn: 56201.5859997	test: 114016.1615712	best: 114016.1615712 (6119)	total: 37.2s	remaining: 23.6s
    6120:	learn: 56196.9651914	test: 114014.8361439	best: 114014.8361439 (6120)	total: 37.2s	remaining: 23.6s
    6121:	learn: 56195.1205619	test: 114014.7129995	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.6s
    6122:	learn: 56192.5822551	test: 114016.7551693	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.6s
    6123:	learn: 56185.9820311	test: 114016.5432751	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.6s
    6124:	learn: 56181.3398349	test: 114018.7329880	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.5s
    6125:	learn: 56177.4631120	test: 114019.2805185	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.5s
    6126:	learn: 56172.4882387	test: 114020.3808045	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.5s
    6127:	learn: 56168.3047040	test: 114019.9290501	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.5s
    6128:	learn: 56164.8334503	test: 114018.0852988	best: 114014.7129995 (6121)	total: 37.2s	remaining: 23.5s
    6129:	learn: 56162.4216435	test: 114017.2034433	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6130:	learn: 56159.3202762	test: 114017.1509969	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6131:	learn: 56156.8024040	test: 114016.8223628	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6132:	learn: 56153.5168249	test: 114017.0179016	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6133:	learn: 56151.8757638	test: 114016.0536594	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6134:	learn: 56149.0376176	test: 114015.3922660	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6135:	learn: 56148.6418512	test: 114015.0088188	best: 114014.7129995 (6121)	total: 37.3s	remaining: 23.5s
    6136:	learn: 56143.9414413	test: 114014.4727265	best: 114014.4727265 (6136)	total: 37.3s	remaining: 23.5s
    6137:	learn: 56142.8288681	test: 114015.0303578	best: 114014.4727265 (6136)	total: 37.3s	remaining: 23.5s
    6138:	learn: 56138.9859819	test: 114014.1607098	best: 114014.1607098 (6138)	total: 37.3s	remaining: 23.5s
    6139:	learn: 56138.1514893	test: 114014.2658987	best: 114014.1607098 (6138)	total: 37.3s	remaining: 23.5s
    6140:	learn: 56136.0377039	test: 114013.7556994	best: 114013.7556994 (6140)	total: 37.3s	remaining: 23.5s
    6141:	learn: 56132.1770016	test: 114014.6547710	best: 114013.7556994 (6140)	total: 37.3s	remaining: 23.5s
    6142:	learn: 56129.2727855	test: 114013.1817291	best: 114013.1817291 (6142)	total: 37.3s	remaining: 23.4s
    6143:	learn: 56124.9171342	test: 114013.8205621	best: 114013.1817291 (6142)	total: 37.4s	remaining: 23.4s
    6144:	learn: 56124.4672289	test: 114014.3867885	best: 114013.1817291 (6142)	total: 37.4s	remaining: 23.4s
    6145:	learn: 56123.5024517	test: 114013.1019409	best: 114013.1019409 (6145)	total: 37.4s	remaining: 23.4s
    6146:	learn: 56120.4558458	test: 114012.9468561	best: 114012.9468561 (6146)	total: 37.4s	remaining: 23.4s
    6147:	learn: 56116.9498723	test: 114014.1691844	best: 114012.9468561 (6146)	total: 37.4s	remaining: 23.4s
    6148:	learn: 56114.5044758	test: 114013.5938637	best: 114012.9468561 (6146)	total: 37.4s	remaining: 23.4s
    6149:	learn: 56110.8151787	test: 114009.8429600	best: 114009.8429600 (6149)	total: 37.4s	remaining: 23.4s
    6150:	learn: 56106.6464287	test: 114008.8595121	best: 114008.8595121 (6150)	total: 37.4s	remaining: 23.4s
    6151:	learn: 56099.4135396	test: 114004.5911811	best: 114004.5911811 (6151)	total: 37.4s	remaining: 23.4s
    6152:	learn: 56097.2364779	test: 114005.4050229	best: 114004.5911811 (6151)	total: 37.4s	remaining: 23.4s
    6153:	learn: 56093.0455870	test: 114004.7747891	best: 114004.5911811 (6151)	total: 37.4s	remaining: 23.4s
    6154:	learn: 56090.2203439	test: 114003.7360547	best: 114003.7360547 (6154)	total: 37.4s	remaining: 23.4s
    6155:	learn: 56088.5789048	test: 114002.1405879	best: 114002.1405879 (6155)	total: 37.4s	remaining: 23.4s
    6156:	learn: 56086.2671534	test: 114001.7111651	best: 114001.7111651 (6156)	total: 37.5s	remaining: 23.4s
    6157:	learn: 56082.4129371	test: 114003.0842003	best: 114001.7111651 (6156)	total: 37.5s	remaining: 23.4s
    6158:	learn: 56078.5244857	test: 114003.0831460	best: 114001.7111651 (6156)	total: 37.5s	remaining: 23.4s
    6159:	learn: 56075.3123285	test: 114002.8194629	best: 114001.7111651 (6156)	total: 37.5s	remaining: 23.4s
    6160:	learn: 56073.4326124	test: 114002.8194409	best: 114001.7111651 (6156)	total: 37.5s	remaining: 23.4s
    6161:	learn: 56070.3071035	test: 114001.1582341	best: 114001.1582341 (6161)	total: 37.5s	remaining: 23.4s
    6162:	learn: 56064.5588580	test: 114000.5859261	best: 114000.5859261 (6162)	total: 37.5s	remaining: 23.3s
    6163:	learn: 56059.7551869	test: 113996.9264544	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6164:	learn: 56056.5240932	test: 113997.4631619	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6165:	learn: 56051.0254137	test: 113998.3520793	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6166:	learn: 56046.3920626	test: 113998.7496652	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6167:	learn: 56042.7779441	test: 114000.3674589	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6168:	learn: 56040.2315498	test: 114000.8166753	best: 113996.9264544 (6163)	total: 37.5s	remaining: 23.3s
    6169:	learn: 56037.3936547	test: 114001.0944392	best: 113996.9264544 (6163)	total: 37.6s	remaining: 23.3s
    6170:	learn: 56035.0430445	test: 114000.8694391	best: 113996.9264544 (6163)	total: 37.6s	remaining: 23.3s
    6171:	learn: 56028.8010575	test: 114000.6913171	best: 113996.9264544 (6163)	total: 37.6s	remaining: 23.3s
    6172:	learn: 56019.4638273	test: 113993.6006377	best: 113993.6006377 (6172)	total: 37.6s	remaining: 23.3s
    6173:	learn: 56011.3642741	test: 113991.0382469	best: 113991.0382469 (6173)	total: 37.6s	remaining: 23.3s
    6174:	learn: 56008.7693225	test: 113990.7397045	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6175:	learn: 56006.3018473	test: 113990.9305593	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6176:	learn: 56001.8290413	test: 113993.6231936	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6177:	learn: 55995.4211137	test: 113992.8856425	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6178:	learn: 55990.6787496	test: 113994.9066682	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6179:	learn: 55988.4774197	test: 113994.3348848	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6180:	learn: 55985.4497463	test: 113991.7747161	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.3s
    6181:	learn: 55985.0626419	test: 113991.6041205	best: 113990.7397045 (6174)	total: 37.6s	remaining: 23.2s
    6182:	learn: 55979.7461461	test: 113988.9784027	best: 113988.9784027 (6182)	total: 37.7s	remaining: 23.2s
    6183:	learn: 55978.7494165	test: 113988.8633084	best: 113988.8633084 (6183)	total: 37.7s	remaining: 23.2s
    6184:	learn: 55975.5384308	test: 113989.5793193	best: 113988.8633084 (6183)	total: 37.7s	remaining: 23.2s
    6185:	learn: 55972.9146765	test: 113989.8209638	best: 113988.8633084 (6183)	total: 37.7s	remaining: 23.2s
    6186:	learn: 55969.0782823	test: 113988.3991913	best: 113988.3991913 (6186)	total: 37.7s	remaining: 23.2s
    6187:	learn: 55964.3818693	test: 113984.5582754	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6188:	learn: 55959.0442513	test: 113987.4676308	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6189:	learn: 55955.1592937	test: 113994.1988626	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6190:	learn: 55951.8421741	test: 113996.4351159	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6191:	learn: 55948.6104860	test: 113996.0388139	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6192:	learn: 55945.1502031	test: 113995.4195369	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6193:	learn: 55945.0077497	test: 113995.3897855	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6194:	learn: 55943.1980673	test: 113995.4267192	best: 113984.5582754 (6187)	total: 37.7s	remaining: 23.2s
    6195:	learn: 55939.1496490	test: 113995.7080022	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.2s
    6196:	learn: 55933.4362242	test: 113989.0487651	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.2s
    6197:	learn: 55930.1533941	test: 113989.5286764	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.2s
    6198:	learn: 55927.5160892	test: 113990.6785266	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.2s
    6199:	learn: 55923.8462058	test: 113991.4719470	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.2s
    6200:	learn: 55920.7376338	test: 113992.4508321	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6201:	learn: 55916.3694046	test: 113990.6866283	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6202:	learn: 55913.4875289	test: 113991.2087907	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6203:	learn: 55910.3187335	test: 113989.2286239	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6204:	learn: 55907.1017231	test: 113989.3645903	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6205:	learn: 55901.4691082	test: 113988.1107189	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6206:	learn: 55897.0970516	test: 113989.8291993	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6207:	learn: 55894.8018748	test: 113991.1677444	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6208:	learn: 55892.7849444	test: 113990.8949557	best: 113984.5582754 (6187)	total: 37.8s	remaining: 23.1s
    6209:	learn: 55888.0878458	test: 113990.7064594	best: 113984.5582754 (6187)	total: 37.9s	remaining: 23.1s
    6210:	learn: 55882.4288003	test: 113984.2034144	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6211:	learn: 55878.3313212	test: 113985.3396589	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6212:	learn: 55874.8369980	test: 113984.9903723	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6213:	learn: 55871.5125308	test: 113985.1626475	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6214:	learn: 55868.5120425	test: 113985.4430743	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6215:	learn: 55866.6225193	test: 113987.5315686	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6216:	learn: 55866.4822819	test: 113987.5181097	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6217:	learn: 55865.1422231	test: 113987.7588021	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6218:	learn: 55859.7857251	test: 113987.5352422	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23.1s
    6219:	learn: 55856.1037818	test: 113988.2577102	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23s
    6220:	learn: 55853.6416735	test: 113987.2814051	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23s
    6221:	learn: 55851.6866133	test: 113986.9453359	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23s
    6222:	learn: 55847.7649008	test: 113987.3503453	best: 113984.2034144 (6210)	total: 37.9s	remaining: 23s
    6223:	learn: 55847.2066095	test: 113987.3295009	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6224:	learn: 55842.1706160	test: 113987.3767846	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6225:	learn: 55837.2260657	test: 113987.6882329	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6226:	learn: 55834.4843394	test: 113990.4760672	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6227:	learn: 55828.4339376	test: 113990.2019635	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6228:	learn: 55823.0852326	test: 113990.3305418	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6229:	learn: 55818.3219371	test: 113992.8515600	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6230:	learn: 55816.3616341	test: 113993.2147572	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6231:	learn: 55813.2585557	test: 113996.4474473	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6232:	learn: 55806.5511892	test: 113997.0469882	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6233:	learn: 55802.0598287	test: 113996.6303288	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6234:	learn: 55798.8930283	test: 113996.4480423	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6235:	learn: 55792.7804186	test: 113996.6639830	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6236:	learn: 55787.7312976	test: 113996.4851498	best: 113984.2034144 (6210)	total: 38s	remaining: 23s
    6237:	learn: 55783.4907669	test: 113996.8032054	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6238:	learn: 55778.5298432	test: 113996.6780592	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6239:	learn: 55774.7243271	test: 113997.4448861	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6240:	learn: 55770.1482890	test: 114000.1986885	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6241:	learn: 55766.5203399	test: 114002.2881916	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6242:	learn: 55761.3806571	test: 114006.0340931	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6243:	learn: 55756.4697433	test: 114004.4781623	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6244:	learn: 55752.2636288	test: 114003.6199285	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6245:	learn: 55749.2435910	test: 114002.0101974	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6246:	learn: 55744.5342110	test: 114001.7669428	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6247:	learn: 55739.8582225	test: 114001.9211600	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6248:	learn: 55737.4376465	test: 114001.7623401	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6249:	learn: 55735.5097904	test: 114001.7116681	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6250:	learn: 55733.0745230	test: 114001.9858324	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6251:	learn: 55731.2977982	test: 114001.1947300	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6252:	learn: 55729.6900067	test: 114000.9096043	best: 113984.2034144 (6210)	total: 38.1s	remaining: 22.9s
    6253:	learn: 55726.3508116	test: 114000.0829597	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.9s
    6254:	learn: 55723.6739112	test: 113999.0497689	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6255:	learn: 55721.4350422	test: 113998.0631400	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6256:	learn: 55717.8606295	test: 113997.5963128	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6257:	learn: 55714.0016578	test: 113998.9452602	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6258:	learn: 55711.5770974	test: 113998.5151357	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6259:	learn: 55708.1163897	test: 113998.7143691	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6260:	learn: 55705.5559118	test: 113998.0871080	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6261:	learn: 55702.7799872	test: 113997.6767184	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6262:	learn: 55699.5764888	test: 113997.1897418	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6263:	learn: 55695.0821670	test: 113996.2181634	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6264:	learn: 55692.7978779	test: 113998.1930777	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6265:	learn: 55690.9001676	test: 113998.7090550	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6266:	learn: 55687.9568018	test: 113996.2083791	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6267:	learn: 55684.1934235	test: 113996.4952441	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6268:	learn: 55682.6971208	test: 113998.1701968	best: 113984.2034144 (6210)	total: 38.2s	remaining: 22.8s
    6269:	learn: 55678.1716527	test: 113996.3701155	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.8s
    6270:	learn: 55672.1326841	test: 113996.1624578	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.8s
    6271:	learn: 55668.5537613	test: 113996.4538181	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6272:	learn: 55665.0319439	test: 113995.8553417	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6273:	learn: 55662.1560567	test: 113995.8633034	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6274:	learn: 55657.6074865	test: 113997.8498783	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6275:	learn: 55654.8217626	test: 113995.6207006	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6276:	learn: 55651.8951254	test: 113995.7133523	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6277:	learn: 55648.3755008	test: 113995.5462919	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6278:	learn: 55646.1968373	test: 113995.3985711	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6279:	learn: 55641.0453147	test: 113995.3629138	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6280:	learn: 55638.3574209	test: 113994.7674555	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6281:	learn: 55636.1846138	test: 113994.2875109	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6282:	learn: 55631.3593634	test: 113993.8413231	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6283:	learn: 55627.5003590	test: 113994.1699442	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6284:	learn: 55624.7599214	test: 113995.4639855	best: 113984.2034144 (6210)	total: 38.3s	remaining: 22.7s
    6285:	learn: 55621.6632828	test: 113992.0991589	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.7s
    6286:	learn: 55616.2934529	test: 113991.2865412	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.7s
    6287:	learn: 55613.9846930	test: 113989.7804994	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6288:	learn: 55609.7997365	test: 113990.1816499	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6289:	learn: 55604.5983041	test: 113991.1776820	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6290:	learn: 55599.4407560	test: 113990.3690336	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6291:	learn: 55596.6178586	test: 113990.0314234	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6292:	learn: 55592.8787383	test: 113990.8979977	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6293:	learn: 55589.6238221	test: 113990.9614502	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6294:	learn: 55586.2481993	test: 113989.9272311	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6295:	learn: 55583.6491388	test: 113989.5991969	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6296:	learn: 55577.7205503	test: 113988.9910360	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6297:	learn: 55573.3856044	test: 113986.4541584	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6298:	learn: 55571.3108264	test: 113986.3230392	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6299:	learn: 55566.2442452	test: 113985.3255974	best: 113984.2034144 (6210)	total: 38.4s	remaining: 22.6s
    6300:	learn: 55562.8759766	test: 113985.0850145	best: 113984.2034144 (6210)	total: 38.5s	remaining: 22.6s
    6301:	learn: 55560.3931502	test: 113984.2548598	best: 113984.2034144 (6210)	total: 38.5s	remaining: 22.6s
    6302:	learn: 55553.2205783	test: 113983.2021824	best: 113983.2021824 (6302)	total: 38.5s	remaining: 22.6s
    6303:	learn: 55550.1861490	test: 113984.5449194	best: 113983.2021824 (6302)	total: 38.5s	remaining: 22.6s
    6304:	learn: 55545.4180229	test: 113984.7079162	best: 113983.2021824 (6302)	total: 38.5s	remaining: 22.6s
    6305:	learn: 55541.6086524	test: 113982.0708971	best: 113982.0708971 (6305)	total: 38.5s	remaining: 22.5s
    6306:	learn: 55537.8797205	test: 113980.8767755	best: 113980.8767755 (6306)	total: 38.5s	remaining: 22.5s
    6307:	learn: 55533.2702019	test: 113981.8167816	best: 113980.8767755 (6306)	total: 38.5s	remaining: 22.5s
    6308:	learn: 55528.3349847	test: 113982.8265462	best: 113980.8767755 (6306)	total: 38.5s	remaining: 22.5s
    6309:	learn: 55523.2833921	test: 113981.2216343	best: 113980.8767755 (6306)	total: 38.5s	remaining: 22.5s
    6310:	learn: 55519.3037530	test: 113980.8723184	best: 113980.8723184 (6310)	total: 38.5s	remaining: 22.5s
    6311:	learn: 55514.8915902	test: 113980.6888492	best: 113980.6888492 (6311)	total: 38.5s	remaining: 22.5s
    6312:	learn: 55512.1597193	test: 113978.4056934	best: 113978.4056934 (6312)	total: 38.5s	remaining: 22.5s
    6313:	learn: 55506.3524236	test: 113977.0506444	best: 113977.0506444 (6313)	total: 38.5s	remaining: 22.5s
    6314:	learn: 55503.3287091	test: 113977.4083975	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6315:	learn: 55499.6429606	test: 113977.7711233	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6316:	learn: 55494.9780334	test: 113978.0964417	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6317:	learn: 55491.2025419	test: 113979.0666892	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6318:	learn: 55487.8216166	test: 113979.3592854	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6319:	learn: 55483.7693846	test: 113977.9640000	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6320:	learn: 55479.7944790	test: 113977.5504922	best: 113977.0506444 (6313)	total: 38.6s	remaining: 22.5s
    6321:	learn: 55476.3555797	test: 113976.8645357	best: 113976.8645357 (6321)	total: 38.6s	remaining: 22.5s
    6322:	learn: 55474.6478125	test: 113977.5757386	best: 113976.8645357 (6321)	total: 38.6s	remaining: 22.5s
    6323:	learn: 55472.0664237	test: 113976.8519619	best: 113976.8519619 (6323)	total: 38.6s	remaining: 22.4s
    6324:	learn: 55469.4353673	test: 113975.9992138	best: 113975.9992138 (6324)	total: 38.6s	remaining: 22.4s
    6325:	learn: 55466.0402664	test: 113976.4366620	best: 113975.9992138 (6324)	total: 38.6s	remaining: 22.4s
    6326:	learn: 55462.9087122	test: 113978.7736236	best: 113975.9992138 (6324)	total: 38.6s	remaining: 22.4s
    6327:	learn: 55459.7402622	test: 113978.9574198	best: 113975.9992138 (6324)	total: 38.6s	remaining: 22.4s
    6328:	learn: 55456.3396891	test: 113978.2823175	best: 113975.9992138 (6324)	total: 38.6s	remaining: 22.4s
    6329:	learn: 55454.8591905	test: 113979.5197075	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6330:	learn: 55451.2166227	test: 113976.1824154	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6331:	learn: 55447.8438362	test: 113976.8981144	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6332:	learn: 55447.0065458	test: 113976.7179492	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6333:	learn: 55442.0067056	test: 113977.8446633	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6334:	learn: 55438.8269902	test: 113977.7172605	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6335:	learn: 55434.4453981	test: 113977.8371546	best: 113975.9992138 (6324)	total: 38.7s	remaining: 22.4s
    6336:	learn: 55431.8019794	test: 113974.7113116	best: 113974.7113116 (6336)	total: 38.7s	remaining: 22.4s
    6337:	learn: 55428.6573630	test: 113974.2151641	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.4s
    6338:	learn: 55423.3847134	test: 113976.4198033	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.4s
    6339:	learn: 55421.2106195	test: 113976.7418779	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.4s
    6340:	learn: 55417.4601523	test: 113977.0198559	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.3s
    6341:	learn: 55415.7092943	test: 113976.2349344	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.3s
    6342:	learn: 55408.2917247	test: 113975.2342821	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.3s
    6343:	learn: 55405.5495313	test: 113974.3238136	best: 113974.2151641 (6337)	total: 38.7s	remaining: 22.3s
    6344:	learn: 55401.9830302	test: 113974.1683268	best: 113974.1683268 (6344)	total: 38.8s	remaining: 22.3s
    6345:	learn: 55398.6021236	test: 113973.4296304	best: 113973.4296304 (6345)	total: 38.8s	remaining: 22.3s
    6346:	learn: 55393.1944432	test: 113971.3423741	best: 113971.3423741 (6346)	total: 38.8s	remaining: 22.3s
    6347:	learn: 55390.6368311	test: 113973.8927848	best: 113971.3423741 (6346)	total: 38.8s	remaining: 22.3s
    6348:	learn: 55385.3133844	test: 113972.7602466	best: 113971.3423741 (6346)	total: 38.8s	remaining: 22.3s
    6349:	learn: 55380.3879336	test: 113974.0342764	best: 113971.3423741 (6346)	total: 38.8s	remaining: 22.3s
    6350:	learn: 55377.5493601	test: 113973.2795414	best: 113971.3423741 (6346)	total: 38.8s	remaining: 22.3s
    6351:	learn: 55373.8227048	test: 113970.9011470	best: 113970.9011470 (6351)	total: 38.8s	remaining: 22.3s
    6352:	learn: 55369.6862449	test: 113971.4851364	best: 113970.9011470 (6351)	total: 38.8s	remaining: 22.3s
    6353:	learn: 55368.2209612	test: 113971.2724285	best: 113970.9011470 (6351)	total: 38.8s	remaining: 22.3s
    6354:	learn: 55364.3044331	test: 113971.1970815	best: 113970.9011470 (6351)	total: 38.8s	remaining: 22.3s
    6355:	learn: 55360.7079744	test: 113970.7945556	best: 113970.7945556 (6355)	total: 38.8s	remaining: 22.3s
    6356:	learn: 55359.0097891	test: 113968.5261117	best: 113968.5261117 (6356)	total: 38.8s	remaining: 22.2s
    6357:	learn: 55355.3108870	test: 113968.8541021	best: 113968.5261117 (6356)	total: 38.8s	remaining: 22.2s
    6358:	learn: 55351.1651303	test: 113968.6917611	best: 113968.5261117 (6356)	total: 38.8s	remaining: 22.2s
    6359:	learn: 55349.5910046	test: 113968.1355835	best: 113968.1355835 (6359)	total: 38.8s	remaining: 22.2s
    6360:	learn: 55345.6027802	test: 113969.8982129	best: 113968.1355835 (6359)	total: 38.8s	remaining: 22.2s
    6361:	learn: 55341.0102561	test: 113973.6852260	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6362:	learn: 55337.5649281	test: 113975.5445659	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6363:	learn: 55333.9909766	test: 113975.6592345	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6364:	learn: 55329.8768386	test: 113974.7720932	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6365:	learn: 55326.5286302	test: 113974.5590734	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6366:	learn: 55324.0437189	test: 113974.2613684	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6367:	learn: 55322.8589403	test: 113975.3319326	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6368:	learn: 55321.4098730	test: 113975.7795251	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6369:	learn: 55316.9886327	test: 113975.6585405	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6370:	learn: 55314.2078448	test: 113975.7945091	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6371:	learn: 55310.5551641	test: 113975.2593171	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6372:	learn: 55305.6439745	test: 113976.6232186	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.2s
    6373:	learn: 55305.5432364	test: 113976.5368769	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.1s
    6374:	learn: 55304.2401643	test: 113976.3874806	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.1s
    6375:	learn: 55301.8746944	test: 113975.9938232	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.1s
    6376:	learn: 55298.7783966	test: 113975.1591381	best: 113968.1355835 (6359)	total: 38.9s	remaining: 22.1s
    6377:	learn: 55298.6393193	test: 113974.5083754	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6378:	learn: 55293.7636142	test: 113974.3843013	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6379:	learn: 55291.4832784	test: 113974.5145309	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6380:	learn: 55289.4163855	test: 113973.7289920	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6381:	learn: 55283.1941182	test: 113972.8479113	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6382:	learn: 55280.0323185	test: 113972.9917283	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6383:	learn: 55276.1613874	test: 113972.5608689	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6384:	learn: 55273.2425367	test: 113972.0571372	best: 113968.1355835 (6359)	total: 39s	remaining: 22.1s
    6385:	learn: 55269.0097009	test: 113967.9426426	best: 113967.9426426 (6385)	total: 39s	remaining: 22.1s
    6386:	learn: 55264.0238650	test: 113967.2671691	best: 113967.2671691 (6386)	total: 39s	remaining: 22.1s
    6387:	learn: 55257.7272577	test: 113966.3960278	best: 113966.3960278 (6387)	total: 39s	remaining: 22.1s
    6388:	learn: 55254.8287896	test: 113964.2772699	best: 113964.2772699 (6388)	total: 39s	remaining: 22.1s
    6389:	learn: 55251.5432974	test: 113963.9249585	best: 113963.9249585 (6389)	total: 39s	remaining: 22s
    6390:	learn: 55247.1187773	test: 113963.5632060	best: 113963.5632060 (6390)	total: 39s	remaining: 22s
    6391:	learn: 55243.3612940	test: 113963.6410813	best: 113963.5632060 (6390)	total: 39s	remaining: 22s
    6392:	learn: 55239.5248053	test: 113963.8616356	best: 113963.5632060 (6390)	total: 39s	remaining: 22s
    6393:	learn: 55237.4252719	test: 113964.9087587	best: 113963.5632060 (6390)	total: 39s	remaining: 22s
    6394:	learn: 55233.3355138	test: 113965.9755638	best: 113963.5632060 (6390)	total: 39.1s	remaining: 22s
    6395:	learn: 55229.4385581	test: 113966.5588086	best: 113963.5632060 (6390)	total: 39.1s	remaining: 22s
    6396:	learn: 55226.3850784	test: 113965.9099618	best: 113963.5632060 (6390)	total: 39.1s	remaining: 22s
    6397:	learn: 55223.9712937	test: 113963.8023656	best: 113963.5632060 (6390)	total: 39.1s	remaining: 22s
    6398:	learn: 55221.8809411	test: 113962.9108745	best: 113962.9108745 (6398)	total: 39.1s	remaining: 22s
    6399:	learn: 55216.8125315	test: 113960.4088223	best: 113960.4088223 (6399)	total: 39.1s	remaining: 22s
    6400:	learn: 55213.8019574	test: 113959.8489797	best: 113959.8489797 (6400)	total: 39.1s	remaining: 22s
    6401:	learn: 55211.2558200	test: 113960.3715494	best: 113959.8489797 (6400)	total: 39.1s	remaining: 22s
    6402:	learn: 55207.3892159	test: 113958.4284701	best: 113958.4284701 (6402)	total: 39.1s	remaining: 22s
    6403:	learn: 55206.0740274	test: 113957.7581253	best: 113957.7581253 (6403)	total: 39.1s	remaining: 22s
    6404:	learn: 55201.6865828	test: 113954.8309941	best: 113954.8309941 (6404)	total: 39.1s	remaining: 22s
    6405:	learn: 55197.6886644	test: 113955.5872210	best: 113954.8309941 (6404)	total: 39.1s	remaining: 21.9s
    6406:	learn: 55193.7005978	test: 113957.7851127	best: 113954.8309941 (6404)	total: 39.1s	remaining: 21.9s
    6407:	learn: 55191.8623305	test: 113957.6573171	best: 113954.8309941 (6404)	total: 39.1s	remaining: 21.9s
    6408:	learn: 55188.7770281	test: 113955.7147198	best: 113954.8309941 (6404)	total: 39.1s	remaining: 21.9s
    6409:	learn: 55184.3861804	test: 113952.1029386	best: 113952.1029386 (6409)	total: 39.1s	remaining: 21.9s
    6410:	learn: 55183.0960791	test: 113954.9402257	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6411:	learn: 55179.9527574	test: 113955.1339102	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6412:	learn: 55176.5782949	test: 113957.1490480	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6413:	learn: 55173.9241938	test: 113956.8050735	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6414:	learn: 55171.8363555	test: 113955.1361144	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6415:	learn: 55168.1304439	test: 113955.3893945	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6416:	learn: 55165.2872141	test: 113955.3089068	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6417:	learn: 55161.2625463	test: 113955.9425456	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6418:	learn: 55156.7080775	test: 113955.5399113	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6419:	learn: 55153.4330175	test: 113955.5216080	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6420:	learn: 55148.2423852	test: 113958.0846236	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6421:	learn: 55143.1019075	test: 113960.8910019	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.9s
    6422:	learn: 55138.0872088	test: 113961.0802254	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.8s
    6423:	learn: 55132.1778885	test: 113960.8210080	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.8s
    6424:	learn: 55125.7419058	test: 113958.2754299	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.8s
    6425:	learn: 55121.4782859	test: 113959.1389233	best: 113952.1029386 (6409)	total: 39.2s	remaining: 21.8s
    6426:	learn: 55119.4102317	test: 113959.1635483	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6427:	learn: 55116.0722930	test: 113957.8117167	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6428:	learn: 55112.5050883	test: 113959.0559761	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6429:	learn: 55110.9799057	test: 113958.3738386	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6430:	learn: 55107.8052288	test: 113956.7827485	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6431:	learn: 55104.4873127	test: 113956.0250158	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6432:	learn: 55099.2983889	test: 113954.6741855	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6433:	learn: 55097.5740546	test: 113954.4456481	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6434:	learn: 55093.7418383	test: 113954.4383728	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6435:	learn: 55089.7595073	test: 113953.9305025	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6436:	learn: 55085.9360638	test: 113953.6070441	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6437:	learn: 55083.8179898	test: 113953.0053169	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6438:	learn: 55080.0317478	test: 113952.3322753	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.8s
    6439:	learn: 55076.0803463	test: 113954.5624322	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.7s
    6440:	learn: 55072.5135403	test: 113954.7394168	best: 113952.1029386 (6409)	total: 39.3s	remaining: 21.7s
    6441:	learn: 55068.8022555	test: 113955.3612611	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6442:	learn: 55065.4446748	test: 113956.9783345	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6443:	learn: 55061.7012820	test: 113957.3501972	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6444:	learn: 55059.4382782	test: 113958.7585577	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6445:	learn: 55057.3026061	test: 113958.4793188	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6446:	learn: 55052.0107636	test: 113957.5771338	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6447:	learn: 55049.7447093	test: 113956.4283440	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6448:	learn: 55045.2879430	test: 113955.7412548	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6449:	learn: 55043.6264334	test: 113955.4550697	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6450:	learn: 55042.2968166	test: 113958.1786020	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6451:	learn: 55039.8692245	test: 113958.1364199	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6452:	learn: 55037.2087812	test: 113957.4107118	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6453:	learn: 55034.5822913	test: 113956.8556293	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6454:	learn: 55032.7211316	test: 113957.6553415	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6455:	learn: 55028.6725461	test: 113960.4290530	best: 113952.1029386 (6409)	total: 39.4s	remaining: 21.7s
    6456:	learn: 55025.6784787	test: 113960.9765181	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6457:	learn: 55025.4395101	test: 113960.2305376	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6458:	learn: 55023.0699576	test: 113960.3516821	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6459:	learn: 55019.4743108	test: 113960.5224585	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6460:	learn: 55015.1215244	test: 113961.1220598	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6461:	learn: 55012.1520918	test: 113959.8710387	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6462:	learn: 55008.7648293	test: 113957.9507622	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6463:	learn: 55005.9149053	test: 113959.1544314	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6464:	learn: 55004.3027014	test: 113960.3264566	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6465:	learn: 55002.8022134	test: 113962.2449674	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6466:	learn: 54999.6208946	test: 113961.5493077	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6467:	learn: 54997.3016046	test: 113962.1146440	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6468:	learn: 54994.6772359	test: 113960.4755844	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6469:	learn: 54991.3323394	test: 113959.7889406	best: 113952.1029386 (6409)	total: 39.5s	remaining: 21.6s
    6470:	learn: 54986.0369818	test: 113959.2877795	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6471:	learn: 54984.7572123	test: 113957.6203218	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6472:	learn: 54980.7798305	test: 113956.5446439	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6473:	learn: 54978.3706211	test: 113957.7999752	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6474:	learn: 54975.8187355	test: 113957.2907689	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6475:	learn: 54975.7396132	test: 113956.8786611	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.6s
    6476:	learn: 54971.4901590	test: 113956.1543670	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6477:	learn: 54967.0279639	test: 113954.3393612	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6478:	learn: 54962.4955189	test: 113954.6636096	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6479:	learn: 54959.3017100	test: 113954.0113230	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6480:	learn: 54956.7952435	test: 113953.1626702	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6481:	learn: 54954.6259083	test: 113953.0596179	best: 113952.1029386 (6409)	total: 39.6s	remaining: 21.5s
    6482:	learn: 54950.6783045	test: 113952.7750596	best: 113952.1029386 (6409)	total: 39.7s	remaining: 21.5s
    6483:	learn: 54948.6220950	test: 113952.3469284	best: 113952.1029386 (6409)	total: 39.7s	remaining: 21.5s
    6484:	learn: 54946.9140173	test: 113949.0482631	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6485:	learn: 54944.5605956	test: 113949.0722621	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6486:	learn: 54944.2907535	test: 113949.6588831	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6487:	learn: 54942.9549532	test: 113949.5614286	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6488:	learn: 54937.2053540	test: 113951.3991953	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6489:	learn: 54934.7428600	test: 113952.4175877	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6490:	learn: 54930.7077360	test: 113951.3335311	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6491:	learn: 54925.9114515	test: 113950.9189069	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6492:	learn: 54923.8120244	test: 113950.6040088	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.5s
    6493:	learn: 54920.8291182	test: 113949.8423795	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.4s
    6494:	learn: 54918.6663305	test: 113949.1255677	best: 113949.0482631 (6484)	total: 39.7s	remaining: 21.4s
    6495:	learn: 54915.2735082	test: 113948.6797101	best: 113948.6797101 (6495)	total: 39.7s	remaining: 21.4s
    6496:	learn: 54912.7386081	test: 113948.7948980	best: 113948.6797101 (6495)	total: 39.8s	remaining: 21.4s
    6497:	learn: 54909.4262058	test: 113949.2714375	best: 113948.6797101 (6495)	total: 39.8s	remaining: 21.4s
    6498:	learn: 54908.2222473	test: 113950.4474693	best: 113948.6797101 (6495)	total: 39.8s	remaining: 21.4s
    6499:	learn: 54908.1913000	test: 113950.0046376	best: 113948.6797101 (6495)	total: 39.8s	remaining: 21.4s
    6500:	learn: 54900.3593141	test: 113946.6078023	best: 113946.6078023 (6500)	total: 39.8s	remaining: 21.4s
    6501:	learn: 54896.9416125	test: 113945.0112115	best: 113945.0112115 (6501)	total: 39.8s	remaining: 21.4s
    6502:	learn: 54894.6040272	test: 113947.1807652	best: 113945.0112115 (6501)	total: 39.8s	remaining: 21.4s
    6503:	learn: 54888.5335465	test: 113945.9654296	best: 113945.0112115 (6501)	total: 39.8s	remaining: 21.4s
    6504:	learn: 54883.8007687	test: 113943.0275600	best: 113943.0275600 (6504)	total: 39.8s	remaining: 21.4s
    6505:	learn: 54881.4351015	test: 113942.9124618	best: 113942.9124618 (6505)	total: 39.8s	remaining: 21.4s
    6506:	learn: 54878.6018063	test: 113943.5850871	best: 113942.9124618 (6505)	total: 39.8s	remaining: 21.4s
    6507:	learn: 54875.9832492	test: 113943.8192822	best: 113942.9124618 (6505)	total: 39.8s	remaining: 21.4s
    6508:	learn: 54875.5734664	test: 113943.3352757	best: 113942.9124618 (6505)	total: 39.8s	remaining: 21.4s
    6509:	learn: 54871.4765500	test: 113944.9383882	best: 113942.9124618 (6505)	total: 39.8s	remaining: 21.4s
    6510:	learn: 54868.7112939	test: 113944.1285011	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.4s
    6511:	learn: 54867.3129333	test: 113943.5398163	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.4s
    6512:	learn: 54864.4177180	test: 113944.2015589	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6513:	learn: 54859.5273276	test: 113946.7387319	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6514:	learn: 54856.5624906	test: 113946.2353491	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6515:	learn: 54853.0971859	test: 113944.8657264	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6516:	learn: 54849.8086186	test: 113944.4096331	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6517:	learn: 54846.8245644	test: 113943.7349598	best: 113942.9124618 (6505)	total: 39.9s	remaining: 21.3s
    6518:	learn: 54841.8729042	test: 113941.1466921	best: 113941.1466921 (6518)	total: 39.9s	remaining: 21.3s
    6519:	learn: 54840.3110486	test: 113939.6343394	best: 113939.6343394 (6519)	total: 39.9s	remaining: 21.3s
    6520:	learn: 54837.5587502	test: 113938.6949016	best: 113938.6949016 (6520)	total: 39.9s	remaining: 21.3s
    6521:	learn: 54834.9338923	test: 113937.8411800	best: 113937.8411800 (6521)	total: 39.9s	remaining: 21.3s
    6522:	learn: 54831.9568111	test: 113936.6592949	best: 113936.6592949 (6522)	total: 40s	remaining: 21.3s
    6523:	learn: 54826.6042400	test: 113936.9085940	best: 113936.6592949 (6522)	total: 40s	remaining: 21.3s
    6524:	learn: 54823.4080725	test: 113934.9965073	best: 113934.9965073 (6524)	total: 40s	remaining: 21.3s
    6525:	learn: 54819.8702883	test: 113934.3145108	best: 113934.3145108 (6525)	total: 40s	remaining: 21.3s
    6526:	learn: 54816.3965526	test: 113932.8783556	best: 113932.8783556 (6526)	total: 40s	remaining: 21.3s
    6527:	learn: 54811.2991826	test: 113930.9094584	best: 113930.9094584 (6527)	total: 40s	remaining: 21.3s
    6528:	learn: 54808.1454561	test: 113932.2723056	best: 113930.9094584 (6527)	total: 40s	remaining: 21.3s
    6529:	learn: 54803.3523964	test: 113930.9139046	best: 113930.9094584 (6527)	total: 40s	remaining: 21.3s
    6530:	learn: 54799.7136966	test: 113930.2726448	best: 113930.2726448 (6530)	total: 40s	remaining: 21.3s
    6531:	learn: 54797.4399642	test: 113930.2668733	best: 113930.2668733 (6531)	total: 40s	remaining: 21.3s
    6532:	learn: 54795.2597154	test: 113930.2431972	best: 113930.2431972 (6532)	total: 40s	remaining: 21.2s
    6533:	learn: 54788.5263395	test: 113926.7084006	best: 113926.7084006 (6533)	total: 40s	remaining: 21.2s
    6534:	learn: 54782.2911295	test: 113927.2295914	best: 113926.7084006 (6533)	total: 40.1s	remaining: 21.2s
    6535:	learn: 54780.0278201	test: 113927.3463253	best: 113926.7084006 (6533)	total: 40.1s	remaining: 21.2s
    6536:	learn: 54777.9338801	test: 113926.4601472	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6537:	learn: 54774.4952526	test: 113927.2123813	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6538:	learn: 54770.4638226	test: 113929.0563009	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6539:	learn: 54765.6279617	test: 113928.9164267	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6540:	learn: 54760.8668496	test: 113927.2187082	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6541:	learn: 54758.1418163	test: 113927.8984890	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6542:	learn: 54755.5904769	test: 113927.7969095	best: 113926.4601472 (6536)	total: 40.1s	remaining: 21.2s
    6543:	learn: 54753.3218709	test: 113924.1002887	best: 113924.1002887 (6543)	total: 40.1s	remaining: 21.2s
    6544:	learn: 54750.3042139	test: 113925.0452118	best: 113924.1002887 (6543)	total: 40.1s	remaining: 21.2s
    6545:	learn: 54742.9465924	test: 113921.7265556	best: 113921.7265556 (6545)	total: 40.1s	remaining: 21.2s
    6546:	learn: 54739.5495220	test: 113920.4320153	best: 113920.4320153 (6546)	total: 40.1s	remaining: 21.2s
    6547:	learn: 54736.3029935	test: 113920.4478498	best: 113920.4320153 (6546)	total: 40.1s	remaining: 21.2s
    6548:	learn: 54732.1401195	test: 113919.5284558	best: 113919.5284558 (6548)	total: 40.1s	remaining: 21.2s
    6549:	learn: 54728.2004451	test: 113918.7632879	best: 113918.7632879 (6549)	total: 40.2s	remaining: 21.1s
    6550:	learn: 54723.6741321	test: 113918.3757761	best: 113918.3757761 (6550)	total: 40.2s	remaining: 21.1s
    6551:	learn: 54720.7785948	test: 113918.6651147	best: 113918.3757761 (6550)	total: 40.2s	remaining: 21.1s
    6552:	learn: 54718.8201506	test: 113918.0947374	best: 113918.0947374 (6552)	total: 40.2s	remaining: 21.1s
    6553:	learn: 54714.8011264	test: 113917.0656393	best: 113917.0656393 (6553)	total: 40.2s	remaining: 21.1s
    6554:	learn: 54711.1708808	test: 113917.0733693	best: 113917.0656393 (6553)	total: 40.2s	remaining: 21.1s
    6555:	learn: 54706.5998099	test: 113916.8246799	best: 113916.8246799 (6555)	total: 40.2s	remaining: 21.1s
    6556:	learn: 54705.3443711	test: 113916.6873362	best: 113916.6873362 (6556)	total: 40.2s	remaining: 21.1s
    6557:	learn: 54702.6279316	test: 113917.6648295	best: 113916.6873362 (6556)	total: 40.2s	remaining: 21.1s
    6558:	learn: 54698.6414230	test: 113915.3856047	best: 113915.3856047 (6558)	total: 40.2s	remaining: 21.1s
    6559:	learn: 54696.5818718	test: 113914.9728044	best: 113914.9728044 (6559)	total: 40.2s	remaining: 21.1s
    6560:	learn: 54694.4260778	test: 113915.1909661	best: 113914.9728044 (6559)	total: 40.2s	remaining: 21.1s
    6561:	learn: 54694.0266128	test: 113914.7264458	best: 113914.7264458 (6561)	total: 40.2s	remaining: 21.1s
    6562:	learn: 54691.9830605	test: 113914.3919262	best: 113914.3919262 (6562)	total: 40.2s	remaining: 21.1s
    6563:	learn: 54689.1147096	test: 113914.7547799	best: 113914.3919262 (6562)	total: 40.2s	remaining: 21.1s
    6564:	learn: 54687.9212928	test: 113914.4582076	best: 113914.3919262 (6562)	total: 40.2s	remaining: 21.1s
    6565:	learn: 54684.6102686	test: 113914.0527804	best: 113914.0527804 (6565)	total: 40.2s	remaining: 21s
    6566:	learn: 54682.8288055	test: 113912.3138210	best: 113912.3138210 (6566)	total: 40.3s	remaining: 21s
    6567:	learn: 54677.0594291	test: 113911.3760363	best: 113911.3760363 (6567)	total: 40.3s	remaining: 21s
    6568:	learn: 54673.2528066	test: 113908.6403415	best: 113908.6403415 (6568)	total: 40.3s	remaining: 21s
    6569:	learn: 54668.6800496	test: 113908.0206477	best: 113908.0206477 (6569)	total: 40.3s	remaining: 21s
    6570:	learn: 54666.8391663	test: 113908.7189600	best: 113908.0206477 (6569)	total: 40.3s	remaining: 21s
    6571:	learn: 54664.1177302	test: 113908.1091392	best: 113908.0206477 (6569)	total: 40.3s	remaining: 21s
    6572:	learn: 54661.3599779	test: 113905.8488479	best: 113905.8488479 (6572)	total: 40.3s	remaining: 21s
    6573:	learn: 54659.0911493	test: 113904.4834424	best: 113904.4834424 (6573)	total: 40.3s	remaining: 21s
    6574:	learn: 54655.7513441	test: 113904.9619198	best: 113904.4834424 (6573)	total: 40.3s	remaining: 21s
    6575:	learn: 54652.4129213	test: 113904.1048310	best: 113904.1048310 (6575)	total: 40.3s	remaining: 21s
    6576:	learn: 54651.5004382	test: 113904.0887631	best: 113904.0887631 (6576)	total: 40.3s	remaining: 21s
    6577:	learn: 54648.3723698	test: 113902.8975847	best: 113902.8975847 (6577)	total: 40.3s	remaining: 21s
    6578:	learn: 54645.2795082	test: 113902.4233941	best: 113902.4233941 (6578)	total: 40.3s	remaining: 21s
    6579:	learn: 54642.7315955	test: 113902.4634886	best: 113902.4233941 (6578)	total: 40.3s	remaining: 21s
    6580:	learn: 54634.2249055	test: 113895.8055150	best: 113895.8055150 (6580)	total: 40.4s	remaining: 21s
    6581:	learn: 54631.8439276	test: 113895.5594251	best: 113895.5594251 (6581)	total: 40.4s	remaining: 21s
    6582:	learn: 54629.7040420	test: 113894.7814615	best: 113894.7814615 (6582)	total: 40.4s	remaining: 21s
    6583:	learn: 54626.7587028	test: 113898.1132107	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6584:	learn: 54622.8584960	test: 113898.4450555	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6585:	learn: 54620.0954899	test: 113897.8545084	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6586:	learn: 54617.1073234	test: 113897.1438442	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6587:	learn: 54613.4107999	test: 113897.1881509	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6588:	learn: 54610.9823208	test: 113898.1254699	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6589:	learn: 54608.6130804	test: 113896.8416956	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6590:	learn: 54605.7964641	test: 113896.9293997	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6591:	learn: 54601.9922119	test: 113896.6520091	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6592:	learn: 54595.8504563	test: 113896.9083752	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6593:	learn: 54592.6546534	test: 113896.3963220	best: 113894.7814615 (6582)	total: 40.4s	remaining: 20.9s
    6594:	learn: 54591.0562399	test: 113894.1883686	best: 113894.1883686 (6594)	total: 40.4s	remaining: 20.9s
    6595:	learn: 54587.8248919	test: 113894.8044810	best: 113894.1883686 (6594)	total: 40.4s	remaining: 20.9s
    6596:	learn: 54586.5548741	test: 113896.3140865	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.9s
    6597:	learn: 54585.3749654	test: 113895.9558324	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.9s
    6598:	learn: 54581.2237118	test: 113895.2774958	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.9s
    6599:	learn: 54576.7218783	test: 113895.1808171	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.9s
    6600:	learn: 54570.7648272	test: 113895.0640720	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6601:	learn: 54569.2655722	test: 113895.4533411	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6602:	learn: 54566.4164679	test: 113894.9579149	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6603:	learn: 54562.7126136	test: 113894.5207701	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6604:	learn: 54561.4013353	test: 113894.7719027	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6605:	learn: 54558.3964310	test: 113894.6100877	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6606:	learn: 54554.5916759	test: 113894.8379698	best: 113894.1883686 (6594)	total: 40.5s	remaining: 20.8s
    6607:	learn: 54552.2462196	test: 113894.0409464	best: 113894.0409464 (6607)	total: 40.5s	remaining: 20.8s
    6608:	learn: 54548.1133004	test: 113894.3828996	best: 113894.0409464 (6607)	total: 40.5s	remaining: 20.8s
    6609:	learn: 54545.2998588	test: 113892.9167153	best: 113892.9167153 (6609)	total: 40.5s	remaining: 20.8s
    6610:	learn: 54542.0004123	test: 113892.8159103	best: 113892.8159103 (6610)	total: 40.6s	remaining: 20.8s
    6611:	learn: 54537.5387622	test: 113889.9888426	best: 113889.9888426 (6611)	total: 40.6s	remaining: 20.8s
    6612:	learn: 54533.0165227	test: 113889.7686974	best: 113889.7686974 (6612)	total: 40.6s	remaining: 20.8s
    6613:	learn: 54528.1881925	test: 113890.5135745	best: 113889.7686974 (6612)	total: 40.6s	remaining: 20.8s
    6614:	learn: 54523.9235213	test: 113890.3659176	best: 113889.7686974 (6612)	total: 40.6s	remaining: 20.8s
    6615:	learn: 54519.3006486	test: 113888.2650733	best: 113888.2650733 (6615)	total: 40.6s	remaining: 20.8s
    6616:	learn: 54516.8520622	test: 113888.2370355	best: 113888.2370355 (6616)	total: 40.6s	remaining: 20.8s
    6617:	learn: 54513.5417657	test: 113887.2946759	best: 113887.2946759 (6617)	total: 40.6s	remaining: 20.7s
    6618:	learn: 54508.6590755	test: 113888.1348891	best: 113887.2946759 (6617)	total: 40.6s	remaining: 20.7s
    6619:	learn: 54505.2061674	test: 113889.5315137	best: 113887.2946759 (6617)	total: 40.6s	remaining: 20.7s
    6620:	learn: 54501.0203524	test: 113888.6346243	best: 113887.2946759 (6617)	total: 40.6s	remaining: 20.7s
    6621:	learn: 54498.2186666	test: 113887.4053643	best: 113887.2946759 (6617)	total: 40.6s	remaining: 20.7s
    6622:	learn: 54495.3289285	test: 113887.0309397	best: 113887.0309397 (6622)	total: 40.6s	remaining: 20.7s
    6623:	learn: 54492.3588193	test: 113885.6815830	best: 113885.6815830 (6623)	total: 40.6s	remaining: 20.7s
    6624:	learn: 54487.4858683	test: 113884.4701572	best: 113884.4701572 (6624)	total: 40.6s	remaining: 20.7s
    6625:	learn: 54483.9641201	test: 113883.2194771	best: 113883.2194771 (6625)	total: 40.7s	remaining: 20.7s
    6626:	learn: 54481.3382647	test: 113883.2188719	best: 113883.2188719 (6626)	total: 40.7s	remaining: 20.7s
    6627:	learn: 54475.1550438	test: 113879.4652313	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6628:	learn: 54473.3279997	test: 113879.6593518	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6629:	learn: 54469.9499653	test: 113880.0890627	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6630:	learn: 54465.2525524	test: 113880.1604155	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6631:	learn: 54462.3862505	test: 113882.2885764	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6632:	learn: 54459.4075443	test: 113883.1460069	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6633:	learn: 54457.8984665	test: 113886.2902610	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.7s
    6634:	learn: 54454.1950733	test: 113886.6207609	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6635:	learn: 54448.4860966	test: 113886.6679166	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6636:	learn: 54446.9053280	test: 113886.8605382	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6637:	learn: 54445.9212754	test: 113887.3378215	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6638:	learn: 54442.4931253	test: 113886.4765471	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6639:	learn: 54438.2054991	test: 113888.3772800	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6640:	learn: 54434.4721100	test: 113886.7210669	best: 113879.4652313 (6627)	total: 40.7s	remaining: 20.6s
    6641:	learn: 54432.1350054	test: 113886.4542661	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6642:	learn: 54428.2194872	test: 113885.8027548	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6643:	learn: 54424.4447310	test: 113884.5175741	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6644:	learn: 54422.1803790	test: 113884.2831110	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6645:	learn: 54420.9392456	test: 113884.0869185	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6646:	learn: 54417.3147884	test: 113883.9315637	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6647:	learn: 54411.9346474	test: 113881.2570395	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6648:	learn: 54405.9083797	test: 113879.6281876	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6649:	learn: 54402.0162190	test: 113880.8486127	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.6s
    6650:	learn: 54399.3644724	test: 113884.6418276	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6651:	learn: 54395.6313170	test: 113884.9989219	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6652:	learn: 54393.0965206	test: 113884.4730841	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6653:	learn: 54390.9877092	test: 113884.3710104	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6654:	learn: 54388.4737709	test: 113885.0974721	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6655:	learn: 54386.6748884	test: 113884.8410084	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6656:	learn: 54383.9460473	test: 113886.0166898	best: 113879.4652313 (6627)	total: 40.8s	remaining: 20.5s
    6657:	learn: 54381.8797204	test: 113884.7936513	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6658:	learn: 54377.7236901	test: 113886.6883195	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6659:	learn: 54373.8115561	test: 113885.0465056	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6660:	learn: 54370.6619476	test: 113885.1259247	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6661:	learn: 54366.9165175	test: 113884.5640888	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6662:	learn: 54362.0840062	test: 113884.5251868	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6663:	learn: 54358.5518913	test: 113883.8297501	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6664:	learn: 54354.7232909	test: 113885.4706309	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6665:	learn: 54352.9905962	test: 113885.0657427	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.5s
    6666:	learn: 54349.5789293	test: 113885.4148213	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6667:	learn: 54346.8062931	test: 113884.1479577	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6668:	learn: 54343.2771200	test: 113884.5646485	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6669:	learn: 54339.6715840	test: 113886.1721993	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6670:	learn: 54337.4591921	test: 113887.1122145	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6671:	learn: 54336.8847237	test: 113887.3225296	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6672:	learn: 54333.0132883	test: 113885.4171955	best: 113879.4652313 (6627)	total: 40.9s	remaining: 20.4s
    6673:	learn: 54329.2717176	test: 113884.2692697	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6674:	learn: 54325.9103334	test: 113881.8770482	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6675:	learn: 54322.0489936	test: 113882.6836502	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6676:	learn: 54320.8168199	test: 113884.6181027	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6677:	learn: 54316.2979524	test: 113884.5289037	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6678:	learn: 54313.5730289	test: 113884.5464014	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6679:	learn: 54309.1195113	test: 113885.4696044	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6680:	learn: 54305.6861806	test: 113885.6651951	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6681:	learn: 54302.6769780	test: 113886.0484557	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6682:	learn: 54301.1622761	test: 113886.8735317	best: 113879.4652313 (6627)	total: 41s	remaining: 20.4s
    6683:	learn: 54297.4628796	test: 113888.4738945	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6684:	learn: 54296.6713659	test: 113888.2684528	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6685:	learn: 54291.6277716	test: 113887.4952005	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6686:	learn: 54288.3442183	test: 113887.5588223	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6687:	learn: 54284.3904234	test: 113887.9705059	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6688:	learn: 54282.1820246	test: 113888.2072937	best: 113879.4652313 (6627)	total: 41s	remaining: 20.3s
    6689:	learn: 54281.5826675	test: 113888.8029933	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6690:	learn: 54278.1558831	test: 113889.2783869	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6691:	learn: 54275.6284110	test: 113890.2284593	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6692:	learn: 54269.7727924	test: 113887.8586965	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6693:	learn: 54265.6592461	test: 113887.7535805	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6694:	learn: 54262.5017288	test: 113886.2684089	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6695:	learn: 54257.6476895	test: 113886.5267972	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6696:	learn: 54254.6769498	test: 113884.8369432	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6697:	learn: 54251.2372921	test: 113884.8381105	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6698:	learn: 54248.2002264	test: 113883.6202586	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6699:	learn: 54246.2404707	test: 113884.1023948	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.3s
    6700:	learn: 54241.5887416	test: 113883.6099550	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.2s
    6701:	learn: 54239.0883339	test: 113883.7310908	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.2s
    6702:	learn: 54237.2251370	test: 113883.3464798	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.2s
    6703:	learn: 54235.9052694	test: 113883.2502365	best: 113879.4652313 (6627)	total: 41.1s	remaining: 20.2s
    6704:	learn: 54234.1671208	test: 113883.3152546	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6705:	learn: 54232.7089929	test: 113885.0105967	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6706:	learn: 54230.6992157	test: 113882.9790911	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6707:	learn: 54229.4035792	test: 113882.9935869	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6708:	learn: 54224.6807345	test: 113880.7238438	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6709:	learn: 54220.1231567	test: 113880.6195468	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6710:	learn: 54218.9763857	test: 113881.0908052	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6711:	learn: 54211.9906647	test: 113883.8881456	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6712:	learn: 54210.7210933	test: 113884.2640376	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6713:	learn: 54208.2249426	test: 113884.9471884	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6714:	learn: 54204.3580371	test: 113883.3842669	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6715:	learn: 54202.6694663	test: 113882.9313099	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6716:	learn: 54198.2264415	test: 113882.3460163	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.2s
    6717:	learn: 54195.9545213	test: 113883.3777760	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.1s
    6718:	learn: 54193.7698757	test: 113883.0781705	best: 113879.4652313 (6627)	total: 41.2s	remaining: 20.1s
    6719:	learn: 54190.4886380	test: 113883.2849707	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6720:	learn: 54188.7723341	test: 113883.7183485	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6721:	learn: 54185.2922939	test: 113883.5473397	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6722:	learn: 54181.5681182	test: 113883.5876913	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6723:	learn: 54178.1074429	test: 113883.3861974	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6724:	learn: 54175.4729280	test: 113885.4078886	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6725:	learn: 54174.6766104	test: 113884.3398813	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6726:	learn: 54170.9403967	test: 113885.5564075	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6727:	learn: 54167.4601021	test: 113885.7731963	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6728:	learn: 54163.8504231	test: 113885.2054114	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6729:	learn: 54161.2874168	test: 113883.8137268	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6730:	learn: 54157.7195510	test: 113882.8944327	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6731:	learn: 54151.7222012	test: 113880.9169744	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6732:	learn: 54150.4043985	test: 113881.9128644	best: 113879.4652313 (6627)	total: 41.3s	remaining: 20.1s
    6733:	learn: 54145.4409991	test: 113882.9361855	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20.1s
    6734:	learn: 54143.4580602	test: 113883.8522519	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20.1s
    6735:	learn: 54141.0581091	test: 113883.7002307	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6736:	learn: 54136.8615718	test: 113884.4935165	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6737:	learn: 54134.4201317	test: 113884.7481882	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6738:	learn: 54130.9094327	test: 113885.8209396	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6739:	learn: 54127.7651185	test: 113885.3829467	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6740:	learn: 54126.0632058	test: 113887.0193599	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6741:	learn: 54122.7976662	test: 113886.1882818	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6742:	learn: 54120.6566093	test: 113885.9975241	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6743:	learn: 54117.1215333	test: 113885.5260400	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6744:	learn: 54113.5230999	test: 113885.8184407	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6745:	learn: 54112.1356904	test: 113886.3110153	best: 113879.4652313 (6627)	total: 41.4s	remaining: 20s
    6746:	learn: 54107.3391587	test: 113886.5514271	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6747:	learn: 54103.4872283	test: 113888.1055105	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6748:	learn: 54101.0597495	test: 113887.5956514	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6749:	learn: 54096.6644072	test: 113887.6662099	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6750:	learn: 54093.4165091	test: 113887.2644475	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6751:	learn: 54088.4001953	test: 113889.4495587	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6752:	learn: 54086.1148431	test: 113888.5883147	best: 113879.4652313 (6627)	total: 41.5s	remaining: 20s
    6753:	learn: 54081.9445535	test: 113889.1957921	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6754:	learn: 54078.3547079	test: 113888.7434420	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6755:	learn: 54076.5723052	test: 113888.6414122	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6756:	learn: 54070.9073441	test: 113884.5561317	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6757:	learn: 54067.8592995	test: 113883.9288722	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6758:	learn: 54063.2649212	test: 113887.8176776	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6759:	learn: 54057.5545363	test: 113886.1689972	best: 113879.4652313 (6627)	total: 41.5s	remaining: 19.9s
    6760:	learn: 54054.7809449	test: 113885.6446452	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6761:	learn: 54051.1172731	test: 113886.8412279	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6762:	learn: 54049.3196656	test: 113887.1370375	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6763:	learn: 54048.2226597	test: 113886.9102407	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6764:	learn: 54047.1138059	test: 113886.7815248	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6765:	learn: 54045.3878079	test: 113885.7110524	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6766:	learn: 54042.0563917	test: 113888.1996492	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6767:	learn: 54040.0231278	test: 113888.4876332	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6768:	learn: 54036.6439591	test: 113889.2330299	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6769:	learn: 54032.2493531	test: 113888.3243387	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.9s
    6770:	learn: 54030.4833806	test: 113886.8414541	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.8s
    6771:	learn: 54027.9762277	test: 113885.7789946	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.8s
    6772:	learn: 54023.0913908	test: 113887.7711001	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.8s
    6773:	learn: 54020.9905447	test: 113885.6217583	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.8s
    6774:	learn: 54018.8044433	test: 113885.6920782	best: 113879.4652313 (6627)	total: 41.6s	remaining: 19.8s
    6775:	learn: 54016.2446129	test: 113888.1529669	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6776:	learn: 54013.2277669	test: 113888.9885052	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6777:	learn: 54010.5456100	test: 113889.5688958	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6778:	learn: 54007.2652794	test: 113889.4962849	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6779:	learn: 54000.6735915	test: 113889.4673863	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6780:	learn: 53998.8709747	test: 113888.8947723	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6781:	learn: 53997.0689187	test: 113889.4717052	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6782:	learn: 53995.0166991	test: 113889.5061630	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6783:	learn: 53992.0525391	test: 113889.6924829	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6784:	learn: 53988.9281639	test: 113890.4999956	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6785:	learn: 53986.5704334	test: 113889.7849023	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6786:	learn: 53984.7826204	test: 113890.9710443	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.8s
    6787:	learn: 53977.5225794	test: 113885.3201590	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.7s
    6788:	learn: 53976.7764500	test: 113886.1374900	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.7s
    6789:	learn: 53972.9042349	test: 113886.9419292	best: 113879.4652313 (6627)	total: 41.7s	remaining: 19.7s
    6790:	learn: 53969.6009661	test: 113887.9884995	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6791:	learn: 53967.3705140	test: 113888.0841185	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6792:	learn: 53964.5779167	test: 113887.7732865	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6793:	learn: 53963.1301927	test: 113886.5684314	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6794:	learn: 53958.1805110	test: 113888.3090535	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6795:	learn: 53956.3058731	test: 113888.2477243	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6796:	learn: 53954.5367958	test: 113887.5136217	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6797:	learn: 53949.9854980	test: 113886.4258924	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6798:	learn: 53947.5178308	test: 113885.4270153	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6799:	learn: 53947.4275738	test: 113884.9732521	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6800:	learn: 53941.1488576	test: 113884.1969933	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6801:	learn: 53939.5464842	test: 113884.3306315	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6802:	learn: 53936.1857788	test: 113883.8953454	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6803:	learn: 53931.6373711	test: 113883.5162472	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.7s
    6804:	learn: 53929.5491219	test: 113881.8275334	best: 113879.4652313 (6627)	total: 41.8s	remaining: 19.6s
    6805:	learn: 53925.7350527	test: 113882.3636404	best: 113879.4652313 (6627)	total: 41.9s	remaining: 19.6s
    6806:	learn: 53920.1466278	test: 113879.1876639	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6807:	learn: 53916.4810935	test: 113881.1842095	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6808:	learn: 53911.4053357	test: 113880.8936982	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6809:	learn: 53905.8349908	test: 113880.1031916	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6810:	learn: 53901.6989818	test: 113880.1116887	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6811:	learn: 53898.4493800	test: 113880.6963027	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6812:	learn: 53894.9552992	test: 113880.7592805	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6813:	learn: 53892.7969383	test: 113880.4790299	best: 113879.1876639 (6806)	total: 41.9s	remaining: 19.6s
    6814:	learn: 53890.8244953	test: 113879.0338334	best: 113879.0338334 (6814)	total: 41.9s	remaining: 19.6s
    6815:	learn: 53887.0499177	test: 113879.3066890	best: 113879.0338334 (6814)	total: 41.9s	remaining: 19.6s
    6816:	learn: 53882.6970957	test: 113878.9065611	best: 113878.9065611 (6816)	total: 41.9s	remaining: 19.6s
    6817:	learn: 53878.8350798	test: 113879.4911362	best: 113878.9065611 (6816)	total: 41.9s	remaining: 19.6s
    6818:	learn: 53875.3037660	test: 113879.8207293	best: 113878.9065611 (6816)	total: 41.9s	remaining: 19.6s
    6819:	learn: 53871.9042229	test: 113879.2471097	best: 113878.9065611 (6816)	total: 41.9s	remaining: 19.6s
    6820:	learn: 53867.1810067	test: 113876.9598249	best: 113876.9598249 (6820)	total: 41.9s	remaining: 19.6s
    6821:	learn: 53863.6926342	test: 113881.5881655	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6822:	learn: 53862.2100649	test: 113881.7994957	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6823:	learn: 53857.9278028	test: 113878.3182576	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6824:	learn: 53854.3260210	test: 113877.8370886	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6825:	learn: 53853.2550738	test: 113877.4417440	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6826:	learn: 53851.8677752	test: 113879.0233003	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6827:	learn: 53848.7463363	test: 113880.6988435	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6828:	learn: 53845.3637633	test: 113881.5436425	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6829:	learn: 53843.5724023	test: 113880.9223297	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6830:	learn: 53840.1818825	test: 113880.6692285	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6831:	learn: 53836.6116625	test: 113880.1084502	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6832:	learn: 53836.0714750	test: 113881.1462569	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6833:	learn: 53833.5268867	test: 113880.2282290	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6834:	learn: 53830.7488465	test: 113878.2150544	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6835:	learn: 53828.1267917	test: 113877.3020060	best: 113876.9598249 (6820)	total: 42s	remaining: 19.5s
    6836:	learn: 53825.7260285	test: 113877.1324005	best: 113876.9598249 (6820)	total: 42.1s	remaining: 19.5s
    6837:	learn: 53822.7136391	test: 113877.1820160	best: 113876.9598249 (6820)	total: 42.1s	remaining: 19.4s
    6838:	learn: 53820.5851592	test: 113876.1536287	best: 113876.1536287 (6838)	total: 42.1s	remaining: 19.4s
    6839:	learn: 53816.2384108	test: 113875.8795929	best: 113875.8795929 (6839)	total: 42.1s	remaining: 19.4s
    6840:	learn: 53814.4094849	test: 113876.1916097	best: 113875.8795929 (6839)	total: 42.1s	remaining: 19.4s
    6841:	learn: 53810.6118582	test: 113875.7823159	best: 113875.7823159 (6841)	total: 42.1s	remaining: 19.4s
    6842:	learn: 53807.2854708	test: 113873.7428048	best: 113873.7428048 (6842)	total: 42.1s	remaining: 19.4s
    6843:	learn: 53803.4459691	test: 113872.7149556	best: 113872.7149556 (6843)	total: 42.1s	remaining: 19.4s
    6844:	learn: 53800.4477777	test: 113873.4352983	best: 113872.7149556 (6843)	total: 42.1s	remaining: 19.4s
    6845:	learn: 53797.0759225	test: 113871.5215648	best: 113871.5215648 (6845)	total: 42.1s	remaining: 19.4s
    6846:	learn: 53791.4471357	test: 113872.7961020	best: 113871.5215648 (6845)	total: 42.1s	remaining: 19.4s
    6847:	learn: 53787.1863190	test: 113872.0051941	best: 113871.5215648 (6845)	total: 42.1s	remaining: 19.4s
    6848:	learn: 53783.7960980	test: 113871.1050645	best: 113871.1050645 (6848)	total: 42.1s	remaining: 19.4s
    6849:	learn: 53781.0973572	test: 113870.8245675	best: 113870.8245675 (6849)	total: 42.1s	remaining: 19.4s
    6850:	learn: 53778.4129214	test: 113870.0352334	best: 113870.0352334 (6850)	total: 42.1s	remaining: 19.4s
    6851:	learn: 53777.0391055	test: 113870.1089447	best: 113870.0352334 (6850)	total: 42.2s	remaining: 19.4s
    6852:	learn: 53773.8812161	test: 113869.2076032	best: 113869.2076032 (6852)	total: 42.2s	remaining: 19.4s
    6853:	learn: 53769.3666001	test: 113867.0267467	best: 113867.0267467 (6853)	total: 42.2s	remaining: 19.4s
    6854:	learn: 53766.6082974	test: 113864.6304005	best: 113864.6304005 (6854)	total: 42.2s	remaining: 19.4s
    6855:	learn: 53764.3294558	test: 113863.5866311	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6856:	learn: 53762.3065623	test: 113864.0233822	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6857:	learn: 53758.2225262	test: 113863.8598747	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6858:	learn: 53754.4665135	test: 113864.2801784	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6859:	learn: 53751.2233573	test: 113865.0704555	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6860:	learn: 53748.8893657	test: 113867.1342749	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6861:	learn: 53744.9024191	test: 113868.1729989	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6862:	learn: 53743.7830505	test: 113867.9655401	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6863:	learn: 53740.1147615	test: 113866.2866748	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6864:	learn: 53736.9258058	test: 113865.4475368	best: 113863.5866311 (6855)	total: 42.2s	remaining: 19.3s
    6865:	learn: 53735.0666575	test: 113865.8085042	best: 113863.5866311 (6855)	total: 42.3s	remaining: 19.3s
    6866:	learn: 53730.7032131	test: 113863.6927950	best: 113863.5866311 (6855)	total: 42.3s	remaining: 19.3s
    6867:	learn: 53727.9845938	test: 113863.8450747	best: 113863.5866311 (6855)	total: 42.3s	remaining: 19.3s
    6868:	learn: 53725.7148141	test: 113863.4443893	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.3s
    6869:	learn: 53723.5502424	test: 113863.9893113	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.3s
    6870:	learn: 53720.0676758	test: 113865.5661754	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.3s
    6871:	learn: 53717.9137389	test: 113866.3841213	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.3s
    6872:	learn: 53716.4175764	test: 113866.6048417	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6873:	learn: 53713.2566136	test: 113866.2987514	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6874:	learn: 53710.5273753	test: 113866.2937783	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6875:	learn: 53705.7614638	test: 113866.8521431	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6876:	learn: 53703.6848625	test: 113866.9585557	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6877:	learn: 53700.6817196	test: 113866.5648739	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6878:	learn: 53697.6140918	test: 113867.0758600	best: 113863.4443893 (6868)	total: 42.3s	remaining: 19.2s
    6879:	learn: 53695.5825109	test: 113866.7661079	best: 113863.4443893 (6868)	total: 42.4s	remaining: 19.2s
    6880:	learn: 53693.0468741	test: 113866.9024535	best: 113863.4443893 (6868)	total: 42.4s	remaining: 19.2s
    6881:	learn: 53685.5250852	test: 113863.4177930	best: 113863.4177930 (6881)	total: 42.4s	remaining: 19.2s
    6882:	learn: 53680.6440644	test: 113862.8431873	best: 113862.8431873 (6882)	total: 42.4s	remaining: 19.2s
    6883:	learn: 53677.2143430	test: 113862.4936061	best: 113862.4936061 (6883)	total: 42.4s	remaining: 19.2s
    6884:	learn: 53672.1552820	test: 113861.1104126	best: 113861.1104126 (6884)	total: 42.4s	remaining: 19.2s
    6885:	learn: 53667.8841844	test: 113860.5540693	best: 113860.5540693 (6885)	total: 42.4s	remaining: 19.2s
    6886:	learn: 53665.6743993	test: 113859.8394323	best: 113859.8394323 (6886)	total: 42.4s	remaining: 19.2s
    6887:	learn: 53662.7680770	test: 113859.2025667	best: 113859.2025667 (6887)	total: 42.4s	remaining: 19.2s
    6888:	learn: 53659.1317320	test: 113857.5866687	best: 113857.5866687 (6888)	total: 42.4s	remaining: 19.2s
    6889:	learn: 53655.8072256	test: 113855.7166167	best: 113855.7166167 (6889)	total: 42.4s	remaining: 19.1s
    6890:	learn: 53654.0031186	test: 113854.8852762	best: 113854.8852762 (6890)	total: 42.4s	remaining: 19.1s
    6891:	learn: 53650.1612373	test: 113854.5857597	best: 113854.5857597 (6891)	total: 42.4s	remaining: 19.1s
    6892:	learn: 53646.3955953	test: 113854.3065327	best: 113854.3065327 (6892)	total: 42.4s	remaining: 19.1s
    6893:	learn: 53643.4105995	test: 113853.8231868	best: 113853.8231868 (6893)	total: 42.5s	remaining: 19.1s
    6894:	learn: 53641.5312723	test: 113851.9072970	best: 113851.9072970 (6894)	total: 42.5s	remaining: 19.1s
    6895:	learn: 53637.5049336	test: 113851.2779643	best: 113851.2779643 (6895)	total: 42.5s	remaining: 19.1s
    6896:	learn: 53634.1779827	test: 113850.6726921	best: 113850.6726921 (6896)	total: 42.5s	remaining: 19.1s
    6897:	learn: 53632.0715236	test: 113850.4575159	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6898:	learn: 53629.2564598	test: 113850.6850753	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6899:	learn: 53625.0415952	test: 113854.5801558	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6900:	learn: 53621.6787824	test: 113854.6621759	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6901:	learn: 53618.6998385	test: 113854.3593667	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6902:	learn: 53616.5978639	test: 113853.9536302	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6903:	learn: 53611.6210004	test: 113853.0960113	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6904:	learn: 53609.5633076	test: 113853.9749807	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6905:	learn: 53608.1571036	test: 113854.0845375	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6906:	learn: 53606.0559447	test: 113854.6566707	best: 113850.4575159 (6897)	total: 42.5s	remaining: 19.1s
    6907:	learn: 53602.7958810	test: 113854.9354159	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6908:	learn: 53597.7063769	test: 113854.8361787	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6909:	learn: 53596.4907442	test: 113855.3406419	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6910:	learn: 53594.2387413	test: 113856.9934654	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6911:	learn: 53589.7771998	test: 113856.7765473	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6912:	learn: 53585.4459619	test: 113857.9637405	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6913:	learn: 53581.0841489	test: 113858.1706066	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6914:	learn: 53579.7356202	test: 113858.9532302	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6915:	learn: 53577.0049659	test: 113858.5541813	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6916:	learn: 53574.9207169	test: 113858.4215850	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6917:	learn: 53570.2961798	test: 113857.5928736	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6918:	learn: 53568.7195452	test: 113857.8187014	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6919:	learn: 53563.3217517	test: 113858.7817870	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6920:	learn: 53560.3838225	test: 113858.6905348	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6921:	learn: 53555.8791930	test: 113858.3164387	best: 113850.4575159 (6897)	total: 42.6s	remaining: 19s
    6922:	learn: 53554.1163854	test: 113858.4086473	best: 113850.4575159 (6897)	total: 42.7s	remaining: 19s
    6923:	learn: 53551.4827780	test: 113859.7126924	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6924:	learn: 53547.3636295	test: 113859.3452371	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6925:	learn: 53544.1744902	test: 113859.7273612	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6926:	learn: 53541.1430869	test: 113860.3448726	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6927:	learn: 53538.4915061	test: 113859.9253755	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6928:	learn: 53535.4991763	test: 113859.6854028	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6929:	learn: 53532.4425299	test: 113860.4100184	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6930:	learn: 53531.0847756	test: 113859.9802044	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6931:	learn: 53529.2519513	test: 113858.1067007	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6932:	learn: 53526.6402594	test: 113858.0742790	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6933:	learn: 53525.6126514	test: 113858.2441410	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6934:	learn: 53523.0660440	test: 113860.1047877	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6935:	learn: 53520.3447991	test: 113860.5259241	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6936:	learn: 53516.8974259	test: 113861.8150723	best: 113850.4575159 (6897)	total: 42.7s	remaining: 18.9s
    6937:	learn: 53513.8474992	test: 113862.0620967	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.9s
    6938:	learn: 53509.2584185	test: 113863.8213829	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.9s
    6939:	learn: 53507.3095311	test: 113863.8815329	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.9s
    6940:	learn: 53505.9837628	test: 113864.0272948	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.9s
    6941:	learn: 53503.5671513	test: 113863.1144514	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6942:	learn: 53501.4643719	test: 113862.9454715	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6943:	learn: 53500.6591159	test: 113861.4532070	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6944:	learn: 53497.6353764	test: 113860.7518039	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6945:	learn: 53495.8828525	test: 113861.4702115	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6946:	learn: 53491.4686945	test: 113860.5721759	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6947:	learn: 53489.0455533	test: 113860.9373828	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6948:	learn: 53486.2599643	test: 113862.8423300	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6949:	learn: 53483.8150848	test: 113863.0007272	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6950:	learn: 53478.7721463	test: 113864.4062988	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6951:	learn: 53477.5780882	test: 113863.7921136	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6952:	learn: 53474.9688913	test: 113865.0454565	best: 113850.4575159 (6897)	total: 42.8s	remaining: 18.8s
    6953:	learn: 53470.7825044	test: 113868.2537216	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.8s
    6954:	learn: 53464.1486132	test: 113867.5292044	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.8s
    6955:	learn: 53459.9613486	test: 113866.7153160	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.8s
    6956:	learn: 53456.2312685	test: 113866.5586155	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.8s
    6957:	learn: 53453.0671320	test: 113864.1752393	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6958:	learn: 53450.9451322	test: 113864.4253351	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6959:	learn: 53448.5804846	test: 113865.5436619	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6960:	learn: 53445.7574306	test: 113865.2044116	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6961:	learn: 53442.2304861	test: 113866.1706551	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6962:	learn: 53440.8745334	test: 113867.0841201	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6963:	learn: 53437.9195638	test: 113867.5827475	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6964:	learn: 53433.9219508	test: 113868.7259891	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6965:	learn: 53430.6875279	test: 113867.4660366	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6966:	learn: 53427.9533451	test: 113869.3906811	best: 113850.4575159 (6897)	total: 42.9s	remaining: 18.7s
    6967:	learn: 53424.1704578	test: 113870.8989315	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6968:	learn: 53421.2508153	test: 113871.5783334	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6969:	learn: 53418.7082174	test: 113870.3999209	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6970:	learn: 53416.3369782	test: 113870.4127960	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6971:	learn: 53413.4863405	test: 113872.5447097	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6972:	learn: 53411.4232574	test: 113872.8315108	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6973:	learn: 53408.9077567	test: 113872.7983528	best: 113850.4575159 (6897)	total: 43s	remaining: 18.7s
    6974:	learn: 53405.4412784	test: 113871.6345663	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6975:	learn: 53400.7374693	test: 113872.1122524	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6976:	learn: 53398.4383946	test: 113872.7990663	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6977:	learn: 53395.2595106	test: 113872.3409797	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6978:	learn: 53392.1691869	test: 113871.5246101	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6979:	learn: 53390.7000270	test: 113869.5423014	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6980:	learn: 53387.6959447	test: 113869.1791562	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6981:	learn: 53383.3949521	test: 113867.3176692	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6982:	learn: 53382.7500692	test: 113867.6686515	best: 113850.4575159 (6897)	total: 43s	remaining: 18.6s
    6983:	learn: 53379.3004123	test: 113869.3101719	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6984:	learn: 53376.4044429	test: 113870.6567951	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6985:	learn: 53373.8490348	test: 113870.1617558	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6986:	learn: 53369.4271796	test: 113870.0746912	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6987:	learn: 53366.9924057	test: 113870.2605096	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6988:	learn: 53363.5437485	test: 113871.2221267	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6989:	learn: 53358.9108196	test: 113869.9288177	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6990:	learn: 53357.3634577	test: 113870.2890974	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.6s
    6991:	learn: 53351.4988659	test: 113869.4320345	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6992:	learn: 53348.3279017	test: 113871.6950670	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6993:	learn: 53346.6004930	test: 113871.4229462	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6994:	learn: 53344.2502192	test: 113872.1224429	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6995:	learn: 53340.5324141	test: 113871.3682195	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6996:	learn: 53337.6671020	test: 113871.6012921	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6997:	learn: 53335.4410464	test: 113871.6436003	best: 113850.4575159 (6897)	total: 43.1s	remaining: 18.5s
    6998:	learn: 53331.4332847	test: 113872.8274253	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    6999:	learn: 53328.2065354	test: 113873.0897613	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7000:	learn: 53326.1719713	test: 113873.0728731	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7001:	learn: 53323.8649423	test: 113872.1178357	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7002:	learn: 53320.3984658	test: 113871.4680862	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7003:	learn: 53316.7865660	test: 113870.4544424	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7004:	learn: 53314.9462065	test: 113872.2651829	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7005:	learn: 53311.3024164	test: 113871.4303502	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7006:	learn: 53307.2373035	test: 113869.9868093	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.5s
    7007:	learn: 53305.1914391	test: 113870.9588109	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.4s
    7008:	learn: 53299.8746703	test: 113872.3017010	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.4s
    7009:	learn: 53297.5584926	test: 113872.3629029	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.4s
    7010:	learn: 53295.2616740	test: 113871.3237839	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.4s
    7011:	learn: 53292.5300170	test: 113871.2664743	best: 113850.4575159 (6897)	total: 43.2s	remaining: 18.4s
    7012:	learn: 53288.8199704	test: 113870.8825992	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7013:	learn: 53286.5958381	test: 113869.5495219	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7014:	learn: 53283.3237300	test: 113869.7915813	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7015:	learn: 53281.0428939	test: 113869.2498893	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7016:	learn: 53277.3951750	test: 113869.5834394	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7017:	learn: 53277.1242724	test: 113869.6025999	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7018:	learn: 53273.2275122	test: 113869.7274801	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7019:	learn: 53270.8979957	test: 113868.9459328	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7020:	learn: 53270.5331337	test: 113869.1980073	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7021:	learn: 53265.7597876	test: 113869.0557712	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7022:	learn: 53263.2863832	test: 113869.8440211	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7023:	learn: 53260.4227916	test: 113870.1251990	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7024:	learn: 53255.3442998	test: 113871.1892070	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.4s
    7025:	learn: 53253.4322503	test: 113871.7016973	best: 113850.4575159 (6897)	total: 43.3s	remaining: 18.3s
    7026:	learn: 53251.1918614	test: 113871.2084639	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7027:	learn: 53249.4581355	test: 113871.8834940	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7028:	learn: 53246.7867280	test: 113871.3620354	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7029:	learn: 53243.5726723	test: 113871.2282842	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7030:	learn: 53241.5262622	test: 113871.2784179	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7031:	learn: 53237.3763730	test: 113871.2795875	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7032:	learn: 53235.3709918	test: 113871.2314524	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7033:	learn: 53232.8209192	test: 113871.5252607	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7034:	learn: 53228.7840360	test: 113872.2253870	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7035:	learn: 53226.9943929	test: 113872.3372742	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7036:	learn: 53222.0719200	test: 113872.8170357	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7037:	learn: 53219.8862530	test: 113872.0794939	best: 113850.4575159 (6897)	total: 43.4s	remaining: 18.3s
    7038:	learn: 53216.5621747	test: 113871.2688136	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.3s
    7039:	learn: 53215.0189515	test: 113875.4422826	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.3s
    7040:	learn: 53213.5004895	test: 113875.0970310	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.3s
    7041:	learn: 53211.0121943	test: 113877.1250985	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.3s
    7042:	learn: 53208.1139383	test: 113876.9624588	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.3s
    7043:	learn: 53204.7289915	test: 113875.6791076	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7044:	learn: 53203.1921633	test: 113875.4826933	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7045:	learn: 53200.0772572	test: 113874.0401265	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7046:	learn: 53198.4268838	test: 113874.0591382	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7047:	learn: 53196.1111184	test: 113874.7826062	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7048:	learn: 53192.9653587	test: 113876.1039565	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7049:	learn: 53190.4063786	test: 113875.8274665	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7050:	learn: 53188.6898601	test: 113874.8798316	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7051:	learn: 53186.2969592	test: 113874.3964812	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7052:	learn: 53181.4446690	test: 113873.6642386	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7053:	learn: 53176.6142397	test: 113871.8744320	best: 113850.4575159 (6897)	total: 43.5s	remaining: 18.2s
    7054:	learn: 53173.3043254	test: 113872.2206400	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7055:	learn: 53169.9429335	test: 113873.8394521	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7056:	learn: 53168.8912939	test: 113873.9817346	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7057:	learn: 53167.6073519	test: 113873.4499682	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7058:	learn: 53164.6075000	test: 113874.2153891	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7059:	learn: 53161.2220798	test: 113875.4741008	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.2s
    7060:	learn: 53159.1274117	test: 113875.0671704	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7061:	learn: 53156.9178909	test: 113877.1890336	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7062:	learn: 53154.7322447	test: 113877.0455574	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7063:	learn: 53149.6302681	test: 113878.4183023	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7064:	learn: 53146.7440564	test: 113879.1623008	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7065:	learn: 53145.2781958	test: 113879.1286357	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7066:	learn: 53143.0794192	test: 113877.3748578	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7067:	learn: 53140.7720043	test: 113877.6756248	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7068:	learn: 53137.9124444	test: 113876.0405646	best: 113850.4575159 (6897)	total: 43.6s	remaining: 18.1s
    7069:	learn: 53136.2217335	test: 113876.3820390	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7070:	learn: 53132.7463882	test: 113878.0988024	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7071:	learn: 53130.9370532	test: 113878.1042485	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7072:	learn: 53129.5696330	test: 113878.7019037	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7073:	learn: 53125.9709430	test: 113877.2059215	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7074:	learn: 53120.4170787	test: 113875.5521651	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7075:	learn: 53116.5447112	test: 113874.8339737	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18.1s
    7076:	learn: 53114.8198759	test: 113875.4957961	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7077:	learn: 53111.8740598	test: 113875.1194012	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7078:	learn: 53107.9489264	test: 113874.2359023	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7079:	learn: 53106.2652607	test: 113874.4597893	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7080:	learn: 53103.5791622	test: 113874.2284538	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7081:	learn: 53101.3768942	test: 113872.8476846	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7082:	learn: 53096.5711737	test: 113872.9624522	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7083:	learn: 53093.0813715	test: 113874.1306571	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7084:	learn: 53089.4119867	test: 113872.5570188	best: 113850.4575159 (6897)	total: 43.7s	remaining: 18s
    7085:	learn: 53086.9972207	test: 113874.2919064	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7086:	learn: 53084.8685960	test: 113875.6338921	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7087:	learn: 53081.7942696	test: 113872.9816645	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7088:	learn: 53080.2996863	test: 113873.0937107	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7089:	learn: 53078.4577746	test: 113873.1289436	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7090:	learn: 53077.5215263	test: 113873.4446513	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7091:	learn: 53076.5986514	test: 113873.6917346	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7092:	learn: 53073.2284035	test: 113874.0992006	best: 113850.4575159 (6897)	total: 43.8s	remaining: 18s
    7093:	learn: 53070.3462426	test: 113873.2498977	best: 113850.4575159 (6897)	total: 43.8s	remaining: 17.9s
    7094:	learn: 53067.6825856	test: 113873.7294800	best: 113850.4575159 (6897)	total: 43.8s	remaining: 17.9s
    7095:	learn: 53064.6628866	test: 113873.4248245	best: 113850.4575159 (6897)	total: 43.8s	remaining: 17.9s
    7096:	learn: 53059.5234033	test: 113870.8826553	best: 113850.4575159 (6897)	total: 43.8s	remaining: 17.9s
    7097:	learn: 53057.9351157	test: 113870.9794474	best: 113850.4575159 (6897)	total: 43.8s	remaining: 17.9s
    Stopped by overfitting detector  (200 iterations wait)
    
    bestTest = 113850.4575
    bestIteration = 6897
    
    Shrink model to first 6898 iterations.
    




    <catboost.core.CatBoostRegressor at 0x2885bcdc100>




```python
cb_pred = cb.predict(X_test)
```


```python
mean_squared_error(y_test,cb_pred)**0.5
```




    113850.45751585696




```python
mean_absolute_error(y_test,cb_pred)
```




    59534.87393840312




```python
explained_variance_score(y_test,cb_pred)
```




    0.9022665492663613




```python
cb.predict(new_val)
```




    array([219119.32779009])




```python
df['price'][0]
```




    221900.0



# In this case, catboost outperformed our ann model


```python
r2_score(y_test,pred)
```




    0.8740931712874356




```python
r2_score(y_test,cb_pred)
```




    0.9022600122570067




```python

```
