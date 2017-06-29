
In this example, we shall explore a dataset I obtained from the Data dot UG website. This dataset contains information from 1839 face-to-face interviews done with small business owners around the country

The first step will be to retrieve the dataset and use it with pandas. 


```python
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
%matplotlib inline
```

After importing the libraries I intend to use, I'll navigate to the folder I intend to use.


```python
pwd
```




    u'/Users/Elizabeth/Documents/Notebooks'




```python
cd /Users/Elizabeth/Downloads
```

    /Users/Elizabeth/Downloads



```python
pwd
```




    u'/Users/Elizabeth/Downloads'




```python
sme = pd.read_csv('sme.csv')
```


```python
sme.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Interview number</th>
      <th>SECTOR</th>
      <th>REGION</th>
      <th>DISTRICT</th>
      <th>PARISH</th>
      <th>Language</th>
      <th>Role in Business</th>
      <th>What is your role in the business?</th>
      <th>Age of owner</th>
      <th>...</th>
      <th>Nationality of owner</th>
      <th>Primary Activity</th>
      <th>Secondary Activity</th>
      <th>How long has the business been operating?</th>
      <th>Legal status</th>
      <th>Where business operates from</th>
      <th>Keeping all physical receipts in an organized manner</th>
      <th>Book keeping for revenues (but not necessarily expenditures)</th>
      <th>Do full financials (Revenue and expense excluding tax accounting)</th>
      <th>Firms total sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>13.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>AGWEE</td>
      <td>English</td>
      <td>Owner</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>...</td>
      <td>Ugandan</td>
      <td>Food and beverage service activities</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>Single owner/sole proprietorship</td>
      <td>Informal premises (e.g. informal market, stree...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>0.0</td>
      <td>500000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>15.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>FOR GOD</td>
      <td>English</td>
      <td>Manager</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>...</td>
      <td>Ugandan</td>
      <td>Accommodation</td>
      <td>Food and beverage service activities</td>
      <td>9.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>8000000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>20.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>LABOUR LINE</td>
      <td>English</td>
      <td>Manager</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>...</td>
      <td>Ugandan</td>
      <td>Food and beverage service activities</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>5000000.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>21.0</td>
      <td>INFORMATION &amp; COMMUNICATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>QUEEN S AVENUE</td>
      <td>English</td>
      <td>Owner</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>...</td>
      <td>Ugandan</td>
      <td>Education</td>
      <td>Computer programming, consultancy and related ...</td>
      <td>5.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>2000000.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
sme = sme.drop('Unnamed: 0', axis = 1)
```


```python
sme = sme.drop(0)
```


```python
sme.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Interview number</th>
      <th>SECTOR</th>
      <th>REGION</th>
      <th>DISTRICT</th>
      <th>PARISH</th>
      <th>Language</th>
      <th>Role in Business</th>
      <th>What is your role in the business?</th>
      <th>Age of owner</th>
      <th>Gender of owner</th>
      <th>Nationality of owner</th>
      <th>Primary Activity</th>
      <th>Secondary Activity</th>
      <th>How long has the business been operating?</th>
      <th>Legal status</th>
      <th>Where business operates from</th>
      <th>Keeping all physical receipts in an organized manner</th>
      <th>Book keeping for revenues (but not necessarily expenditures)</th>
      <th>Do full financials (Revenue and expense excluding tax accounting)</th>
      <th>Firms total sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>13.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>AGWEE</td>
      <td>English</td>
      <td>Owner</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>Female</td>
      <td>Ugandan</td>
      <td>Food and beverage service activities</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>Single owner/sole proprietorship</td>
      <td>Informal premises (e.g. informal market, stree...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>0.0</td>
      <td>500000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>15.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>FOR GOD</td>
      <td>English</td>
      <td>Manager</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>Male</td>
      <td>Ugandan</td>
      <td>Accommodation</td>
      <td>Food and beverage service activities</td>
      <td>9.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>8000000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20.0</td>
      <td>ACCOMODATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>LABOUR LINE</td>
      <td>English</td>
      <td>Manager</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>Male</td>
      <td>Ugandan</td>
      <td>Food and beverage service activities</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>5000000.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>21.0</td>
      <td>INFORMATION &amp; COMMUNICATION</td>
      <td>NORTHERN</td>
      <td>GULU</td>
      <td>QUEEN S AVENUE</td>
      <td>English</td>
      <td>Owner</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>Female</td>
      <td>Ugandan</td>
      <td>Education</td>
      <td>Computer programming, consultancy and related ...</td>
      <td>5.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>1.0</td>
      <td>2000000.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>26.0</td>
      <td>REAL ESTATE</td>
      <td>WESTERN</td>
      <td>HOIMA</td>
      <td>CENTRAL WARD</td>
      <td>English</td>
      <td>Owner</td>
      <td>NaN</td>
      <td>35-50</td>
      <td>Male</td>
      <td>Ugandan</td>
      <td>Activities of head offices; management consult...</td>
      <td>Architectural and engineering activities; tech...</td>
      <td>15.0</td>
      <td>Privately held, limited company</td>
      <td>Formal business premises (e.g. office, busines...</td>
      <td>Yes</td>
      <td>No</td>
      <td>1.0</td>
      <td>1000000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
length = sme['How long has the business been operating?'].value_counts()
```


```python
length = length.sort_index()
```


```python
length.head()
```




    1.0      4
    2.0     27
    3.0     70
    4.0    143
    5.0    160
    Name: How long has the business been operating?, dtype: int64




```python
index = length.index
```


```python
values= length.values
```


```python
values
```




    array([  4,  27,  70, 143, 160, 117, 112,  90,  64, 127,  20,  61,  16,
            38,  62,  19,  12,   8,   7,  35,   9,   6,   7,   5,  16,   1,
             5,   4,   3,  16,   2,   1,   1,   1,   6,   5,   1,   1,   1,
             5,   1,   1,   1,   1,   2,   1])




```python
plt.plot(index, values)
```




    [<matplotlib.lines.Line2D at 0x11bcb1610>]




![png](output_18_1.png)



```python
values = (length.cumsum()/length.sum()).values
```


```python
plt.plot(index, values)
plt.xticks(range(0,70,5))
```




    ([<matplotlib.axis.XTick at 0x11c19e6d0>,
      <matplotlib.axis.XTick at 0x11c12ed50>,
      <matplotlib.axis.XTick at 0x11c19ead0>,
      <matplotlib.axis.XTick at 0x11c4559d0>,
      <matplotlib.axis.XTick at 0x11c45d190>,
      <matplotlib.axis.XTick at 0x11c45d910>,
      <matplotlib.axis.XTick at 0x11c46a0d0>,
      <matplotlib.axis.XTick at 0x11c46a850>,
      <matplotlib.axis.XTick at 0x11c46afd0>,
      <matplotlib.axis.XTick at 0x11c474790>,
      <matplotlib.axis.XTick at 0x11c474f10>,
      <matplotlib.axis.XTick at 0x11c47c6d0>,
      <matplotlib.axis.XTick at 0x11c47ce50>,
      <matplotlib.axis.XTick at 0x11c486610>],
     <a list of 14 Text xticklabel objects>)




![png](output_20_1.png)


We can also obtain the survival function. This helps us know the percentage of businesses that survived up to a certain point.


```python
cdf = length.cumsum()/length.sum()
survival = 1- cdf
plt.plot(index, survival)
plt.xticks(range(0,70,5))
plt.title('Survival Function')
plt.xlabel('Percentage')
plt.ylabel('Years')
```




    <matplotlib.text.Text at 0x11c77b610>




![png](output_22_1.png)


Next we plot the hazard function. The hazard function is a plot that shows for every age the number of businesses that reached that age and did go beyond that point. It can help us estimate how many businesses end at each age.


```python
survival.head()
```




    1.0    0.996911
    2.0    0.976062
    3.0    0.922008
    4.0    0.811583
    5.0    0.688031
    Name: How long has the business been operating?, dtype: float64




```python
lam =[]
vals = survival.values.tolist()
for i in range(len(vals[:-1])):
    lam.append(((vals[i]-vals[i+1])/float(vals[i])))
plt.plot(index[1:], lam)   
```




    [<matplotlib.lines.Line2D at 0x11caf42d0>]




![png](output_25_1.png)


We can group the respondents by their regions as well as by the districts and then do some analysis.
First we shall start with the regions.


```python
by_region = sme.groupby('REGION')
```


```python
sales_by_region= by_region['REGION', 'Firms total sales'].median()
sales_by_region
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Firms total sales</th>
    </tr>
    <tr>
      <th>REGION</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CENTRAL</th>
      <td>900000.0</td>
    </tr>
    <tr>
      <th>EASTERN</th>
      <td>1100000.0</td>
    </tr>
    <tr>
      <th>KAMPALA</th>
      <td>1120000.0</td>
    </tr>
    <tr>
      <th>NORTHERN</th>
      <td>900000.0</td>
    </tr>
    <tr>
      <th>WESTERN</th>
      <td>1000000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
index = [0.5 + i for i in range(len(by_region))]
plt.bar(index, sales_by_region.values)
plt.xticks(index, sales_by_region.index, rotation=30)
```




    ([<matplotlib.axis.XTick at 0x11ac51a10>,
      <matplotlib.axis.XTick at 0x11af04150>,
      <matplotlib.axis.XTick at 0x11ac51090>,
      <matplotlib.axis.XTick at 0x11b851490>,
      <matplotlib.axis.XTick at 0x11b851c10>],
     <a list of 5 Text xticklabel objects>)




![png](output_29_1.png)



```python
sme.columns
```




    Index([u'Interview number', u'SECTOR', u'REGION', u'DISTRICT', u'PARISH',
           u'Language', u'Role in Business', u'What is your role in the business?',
           u'Age of owner', u'Gender of owner', u'Nationality of owner',
           u'Primary Activity', u'Secondary Activity',
           u'How long has the business been operating?', u'Legal status',
           u'Where business operates from',
           u'Keeping all physical receipts in an organized manner',
           u'Book keeping for revenues (but not necessarily expenditures)',
           u'Do full financials (Revenue and expense excluding tax accounting)',
           u'Firms total sales'],
          dtype='object')




```python
sme['Legal status'].value_counts()
```




    Single owner/sole proprietorship     969
    Privately held, limited company      145
    Partnership                          116
    Co-operative                          38
    Publicly listed company (PLC)          8
    Ngo                                    2
    Under the church                       2
    Association of members                 2
    NGO(Charity organisation               1
    Community based business               1
    NGo (church owned                      1
    Joint venture                          1
    Church founded                         1
    started by government                  1
    Church owned School                    1
    under the church                       1
    Family owned                           1
    Shareholding company.                  1
    Its an agency of nic                   1
    under  government  supervision         1
    We have not registered in any way      1
    Name: Legal status, dtype: int64




```python
legal_by_region = by_region['Legal status']
regions={}
for name, group in legal_by_region:
    regions[name]=group.value_counts()
```


```python
regions['CENTRAL'][:4]
```




    Single owner/sole proprietorship    371
    Partnership                          36
    Privately held, limited company      22
    Co-operative                          4
    Name: Legal status, dtype: int64




```python
regions['KAMPALA']
```




    Single owner/sole proprietorship    154
    Privately held, limited company      33
    Partnership                          17
    Co-operative                          1
    Shareholding company.                 1
    Publicly listed company (PLC)         1
    Name: Legal status, dtype: int64




```python
legal_df= pd.DataFrame(regions)
```


```python
legal_df.index.name='Legal status'
```


```python
legal_df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CENTRAL</th>
      <th>EASTERN</th>
      <th>KAMPALA</th>
      <th>NORTHERN</th>
      <th>WESTERN</th>
    </tr>
    <tr>
      <th>Legal status</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Association of members</th>
      <td>NaN</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Church founded</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Church owned School</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Co-operative</th>
      <td>4.0</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>8.0</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Community based business</th>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Family owned</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Its an agency of nic</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Joint venture</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>NGO(Charity organisation</th>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>NGo (church owned</th>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Ngo</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Partnership</th>
      <td>36.0</td>
      <td>30.0</td>
      <td>17.0</td>
      <td>15.0</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>Privately held, limited company</th>
      <td>22.0</td>
      <td>16.0</td>
      <td>33.0</td>
      <td>32.0</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>Publicly listed company (PLC)</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>Shareholding company.</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Single owner/sole proprietorship</th>
      <td>371.0</td>
      <td>110.0</td>
      <td>154.0</td>
      <td>100.0</td>
      <td>234.0</td>
    </tr>
    <tr>
      <th>Under the church</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>We have not registered in any way</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>started by government</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>under  government  supervision</th>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>under the church</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
legal_df = legal_df.rename_axis('REGION', axis ='columns')
```


```python

```
