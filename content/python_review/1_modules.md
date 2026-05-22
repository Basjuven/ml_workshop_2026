---
numbering:
  title:
    offset: 0
---
(fundamentals)=
# Useful Modules

## Common NumPy Methods

Here we will see functions that will be used constantly before doing Machine Learning.

### Creating arrays

```{code-block} python
import numpy as np

a = np.array([1,2,3,4,5])
print(a)
```

```{tip} Output
[1 2 3 4 5]
```

### Generating a sequence of values
```{code-block} python
values = np.linspace(0,10,5)   # 5 numbers between 0 and 10
sequence = np.arange(0,10,2)   # in steps of 2

print(values)
print(sequence)
```

```{tip} Output
[ 0.   2.5  5.   7.5 10. ]<br>
[0 2 4 6 8]
```

### Basic statistical operations
```{code-block} python
data = np.array([23,25,24,26,28])

print("Mean", data.mean()) # calculates the arithmetic mean of the elements
print("Standard Deviation", data.std()) # calculates the standard deviation of a dataset
print("Minimum", data.min()) # finds the minimum value in an array
print("Maximum", data.max()) # finds the maximum value in an array
```

```{tip} Output
Mean 25.2<br>
Standard Deviation 1.7204650534085253<br>
Minimum 23<br>
Maximum 28
```

### Vectorized mathematical operations

```{code-block} python
x = np.linspace(0,5,5)

print(x**2)
print(np.sqrt(x))
print(np.log(x+1))
```

```{tip} Output
[ 0.      1.5625  6.25   14.0625 25.    ]<br>
[0.         1.11803399 1.58113883 1.93649167 2.23606798]<br>
[0.         0.81093022 1.25276297 1.55814462 1.79175947]
```

````{exercise} 

**Predict the result**

```python
import numpy as np
a = np.array([1,2,3])
print(a + 1)
```

A. Error  
B. [2,3,4]  
C. [1,2,3,1]  
D. 2

```{tip} View solution
:class: dropdown
Answer: **B**

NumPy applies the operation to each element automatically.
This is called vectorization.
```
````

---

## Common Pandas Methods

With the Pandas library, we can read a CSV file:

```{code-block} python
import pandas as pd

df = pd.read_csv("data.csv")
```

We can also create our own data using the DataFrame method:

```{code-block} python
import pandas as pd

df = pd.DataFrame({
    "star":["Sun","Alpha Centauri A","Sirius"],
    "mass":[1, 1.1, 2.02],
    "distance":[0.000016, 4.39, 8.6]
})
```

### Inspecting data

```{code-block} python
df.head() # shows the first rows of the DataFrame
df.info() # shows a summary of information about the DataFrame
df.describe() # shows descriptive statistics of the DataFrame columns
```

We can also obtain the maximum, minimum, and mean of specific columns.

```{code-block} python
df["mass"].mean()
df["distance"].max()
df["mass"].min()
```

To create new columns:

```{code-block} python
df["radius"] = 3,958.8* (df["mass"] / 1)**0.8
```

````{exercise} 

**What does `df.head(5)` do?**

A. Deletes data<br>
B. Shows the first 5 rows<br>
C. Sorts the table up to row 5<br>
D. Calculates the average of column 5

```{tip} View solution
:class: dropdown
Answer: **B**

It quickly inspects the first 5 rows of the dataset.
```
````

---

## Common Matplotlib Methods

Matplotlib is the base library for creating plots in Python.
It is powerful and very flexible, but more manual than Seaborn.

### Create a figure

```python
plt.figure(figsize=(6,4))
```

### Line plot

```python
plt.plot(x, y)
```

### Points (scatter)

```python
plt.scatter(x, y)
```

### Histogram

```python
plt.hist(data, bins=20)
```

### Labels

```python
plt.xlabel("Age")
plt.ylabel("Height")
plt.title("Relationship Between Age and Height")
```

### Legend

```python
plt.legend()
```

### Show plot

```python
plt.show()
```

---

## Example

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0,10,50)
y = np.sin(x)

plt.plot(x,y)
plt.title("Sine wave")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.show()
```

`````{tip} Output
```{figure} figures/sine.png
:width: 50%
```
`````

---

````{exercise}

**What type of plot does `plt.scatter(x, y)` create?**

A. Histogram<br>
B. Bar plot<br>
C. Scatter plot<br>
D. Pie chart

```{tip} View solution
:class: dropdown
Answer: **C**

`scatter` draws each observation as an individual point.
```
````

---

````{exercise}

**What is `plt.show()` used for?**

A. Saving the plot<br>
B. Showing the plot on the screen<br>
C. Deleting the plot<br>
D. Exporting to Excel

```{tip} View solution
:class: dropdown
Answer: **B**

It renders the figure on the screen.
```
````

---

# Common Seaborn Methods

Seaborn is a library based on Matplotlib but specialized in **data analysis**.

In real data science, Seaborn is used very often.

### Smart histogram

```python
sns.histplot(data=df, x="age")
```

### Relationship between variables

```python
sns.scatterplot(data=df, x="height", y="weight")
```

### Boxplot

```python
sns.boxplot(data=df, x="gender", y="salary")
```

### Category count

```python
sns.countplot(data=df, x="class")
```

### Correlations

```python
sns.heatmap(df.corr(), annot=True)
```

---

## Example

```python
import seaborn as sns
import pandas as pd

df = sns.load_dataset("tips")

sns.scatterplot(data=df, x="total_bill", y="tip", hue="sex")
```

`````{tip} Output
```{figure} figures/sex.png
:width: 50%
```
`````

---

````{exercise}

**What does `hue="sex"` do in Seaborn?**

A. Filters the data<br>
B. Changes the size of the points<br>
C. Colors by category<br>
D. Calculates the average

```{tip} View solution
:class: dropdown
Answer: **C**

It separates the data into categories using different colors.
```
````

---

````{exercise}

**Which plot is best for viewing correlations between variables?**

A. scatterplot<br>
B. heatmap<br>
C. countplot<br>
D. histplot

```{tip} View solution
:class: dropdown
Answer: **B**

A heatmap shows correlations among many variables at the same time.
```
````

---

`````{tip} Now your turn 

**Analyzing an astronomical signal**

A telescope measured the relative brightness of a star over time.
Variable stars change their brightness periodically due to physical pulsations.

Your job is to behave like a scientist:
load data → analyze it → discover the pattern.

## 1) Create the observation time

Create a time array from 0 to 10 hours with 200 measurements:

````{tip} Hint
:class: dropdown
Create a variable called `time` and use NumPy’s `linspace` method.
```python
import numpy as np

time = np.linspace(0,10,200)
```
````

---

## 2) Simulate the observed brightness

The star’s brightness approximately follows a sinusoidal signal
(a real physical oscillation) plus instrumental noise. Add the observed brightness:

```python
noise = np.random.normal(0,0.2,200)
brightness = 2 + np.sin(2*np.pi*time/3) + noise

brightness[:10]
```

---

## 3) Scientific statistics

Calculate:

* mean brightness
* maximum brightness
* standard deviation (variability of the star)

````{tip} Hint
:class: dropdown
```python
print("Mean:", brightness.mean())
print("Maximum:", brightness.max())
print("Standard deviation:", brightness.std())
```

The standard deviation measures how variable the star is.
````

---

## 4) Find the brightest moments

Find the index where the star was brightest:

```python
index_max = np.argmax(brightness)
print(time[index_max], brightness[index_max])
```

That was the moment of maximum luminosity.

---

## 5) Plot the observation

```python
import matplotlib.pyplot as plt

plt.plot(time, brightness)
plt.xlabel("Time (hours)")
plt.ylabel("Relative brightness")
plt.title("Light Curve of a Variable Star")
plt.show()
```

`````