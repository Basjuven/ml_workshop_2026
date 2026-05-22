---
numbering:
  title:
    offset: 0
---

# Python Libraries

So far, we have used Python as a calculator and to work with lists.

But in real life, nobody analyzes data that way.

Scientists, engineers, and analysts use **libraries**.

---

## What is a library?

A library is a set of tools already built by other people to solve specific problems.

It is like:

| Area | Tool |
|------|------|
| Carpentry | hammer |
| Mathematics | calculator |
| Data science | libraries |

Instead of programming everything from scratch, we use accumulated knowledge.

```{figure} figures/libraries.png
:name: libraries
:width: 100%

Different libraries used in data analysis and machine learning.
```

---

## Importing a library

```python
import numpy as np
```

This means:

> “Bring the advanced mathematical tools so we can use them.”

`np` is only a nickname, or alias, that lets us write less.

---

````{exercise}

**What does `import pandas as pd` mean?**

A. Create a variable called pandas<br>
B. Download pandas from the internet<br>
C. Bring external tools so they can be used in the program<br>
D. Create a new file

```{tip} View solution
:class: dropdown
Answer: **C**

Importing a library means bringing existing code so we can use its functions.
````

---

# NumPy — mathematics and vectors

NumPy allows us to work with **efficient numerical arrays**.

It is the foundation of almost all scientific computing in Python.

It is used when:
- there are many numbers
- we need speed
- we work with measurements

## Example

```{code-block} python
import numpy as np

temperatures = np.array([23, 25, 24, 26, 28])

print(temperatures.mean())
print(temperatures.max())
```

```{tip} Output
25.2<br>
28
```

---

## Difference from lists

```python
list_data = [1,2,3,4]
array = np.array([1,2,3,4])

list_data * 2
array * 2
```

```{tip} Output
[1, 2, 3, 4, 1, 2, 3, 4]<br>
array([2, 4, 6, 8])
```

---

# Pandas — smart tables

Pandas allows us to work with **real data tables**.

It is one of the most important tools for data analysis.

It is used when working with:

* CSV files
* surveys
* experimental measurements

## Example

With the Pandas library, we can read a document in CSV format:

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

---

# Matplotlib — plotting

Matplotlib allows us to visualize data.

It is the basic plotting tool in Python.

---

## Example

```python
import matplotlib.pyplot as plt

plt.plot([1,2,3],[4,5,6])
plt.show()
```

---

It is used when we want to:

- see trends
- explain results
- teach students

---

````{exercise}

**What is the purpose of plotting?**

A. Decorate the code<br>
B. See patterns in the data<br>
C. Speed up calculations<br>
D. Save files

```{tip} View solution
:class: dropdown

Answer: **B**

The human brain understands information better visually than numerically.
````

---

# Seaborn — statistical plots

Seaborn is an improvement over Matplotlib.

It creates clearer statistical plots automatically.

## Example

```python
import seaborn as sns

sns.histplot(df["grade"])
```

---

It is used when we want:

* clear histograms
* to compare groups
* to visualize distributions

---

````{exercise} 

**Why use Seaborn instead of Matplotlib?**

A. It is required  
B. It automatically creates statistical plots  
C. It is faster  
D. It does not use Python

```{tip} View solution
:class: dropdown
Answer: **B**

Seaborn is designed for data analysis, not only drawing.
```
````

---

# Future libraries (Machine Learning)

We will not use these yet, but they exist:

| Library      | Use                          |
| ------------ | ---------------------------- |
| scikit-learn | classic Machine Learning     |
| tensorflow   | neural networks              |
| pytorch      | deep learning research       |
| xgboost      | powerful predictive models   |

---

`````{tip}
First:

> understand data

Then:

> predict data

Machine Learning comes later.
`````

---

# Summary

| Library   | What it is used for      |
| ---------- | ------------------------ |
| NumPy      | numerical calculations   |
| Pandas     | data tables              |
| Matplotlib | basic plots              |
| Seaborn    | statistical plots        |

---

In data science, most of the work is NOT Machine Learning.
It is understanding the data.

`````{tip} Now your turn

1. In a code cell, add the comment ```importing libraries```. Remember Python comments: ```#``` for single-line comments and ```""" """``` for multi-line comments.

2. Finally, import the four libraries, with their respective aliases, that we will use.

The final result of your cell should be:

```{code-block} python
# importing libraries

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sb
import pandas as pd
```

`````