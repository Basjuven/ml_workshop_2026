---
numbering:
  title:
    offset: 0
---
(visualization)=
# Data Visualization

In this chapter, we review essential tools for visualizing data before moving into Machine Learning.
We will see how to create basic plots, improve their appearance, and combine Matplotlib with Seaborn for clear and reproducible results.

---

## Matplotlib

### Creating a figure and an axis
```{code-block} python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(figsize=(6,4))
````

### Line plot

```{code-block} python
x = [0,1,2,3,4]
y = [0,1,4,9,16]
plt.plot(x, y, label="y = x^2")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Example: line")
plt.legend()
plt.show()
```

### Scatter plot

```{code-block} python
plt.scatter(x, y, c="C1", marker="o")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Example: scatter")
plt.show()
```

### Histogram

```{code-block} python
import numpy as np
data = np.random.normal(loc=0, scale=1, size=500)
plt.hist(data, bins=30)
plt.title("Histogram of data (normal)")
plt.show()
```

### Subplots (multiple plots)

```{code-block} python
fig, axes = plt.subplots(1,2, figsize=(10,4))
axes[0].plot(x, y)
axes[0].set_title("Line")
axes[1].hist(data, bins=20)
axes[1].set_title("Histogram")
plt.tight_layout()
plt.show()
```

### Saving a figure

```{code-block} python
plt.plot(x,y)
plt.savefig("my_plot.png", dpi=150, bbox_inches="tight")
```

---

## Seaborn — statistical visualizations

Seaborn works on top of Matplotlib and usually produces more informative plots by default.

### Histogram with KDE

```{code-block} python
import seaborn as sns
sns.histplot(data, kde=True)
plt.title("Histogram + KDE")
plt.show()
```

### Scatter plot separated by category

```{code-block} python
# df is a DataFrame with columns 'x','y','class'
# example: sns.scatterplot(data=df, x="x", y="y", hue="class")
```

### Boxplot (comparing distributions)

```{code-block} python
# sns.boxplot(x="category", y="value", data=df)
```

### Countplot (counting categories)

```{code-block} python
# sns.countplot(x="class", data=df)
```

### Heatmap (correlation matrix)

```{code-block} python
# sns.heatmap(df.corr(), annot=True, fmt=".2f", cmap="coolwarm")
```

### Pairplot (quick exploration)

```{code-block} python
# sns.pairplot(df, hue="class", vars=["u","g","r"])
```

---

## Quick best practices

* Always add labels (`xlabel`, `ylabel`) and a title (`title`).
* Use `plt.tight_layout()` to prevent text from being cut off.
* For publication, save as PNG or PDF with high `dpi`.
* When using `hue` in Seaborn, check for class imbalance with a countplot.
* If you combine Seaborn and Matplotlib, place calls to `plt.*` after `sns.*` as needed.

---

## Guided exercise — Scientific visualization

In this exercise, you will analyze and visualize a **simulated astronomical signal**. Work in a notebook (Colab / Jupyter). Follow the steps and use the hints if you get stuck.

````{exercise}

**Analyze and visualize a simulated light curve**

Tasks (do them in order):

1. Create a time array `t` from 0 to 10 hours with 300 points using `np.linspace`.
2. Simulate a brightness signal `flux` consisting of:
   - baseline component = 1.5
   - periodic signal = `0.8 * np.sin(2*np.pi*t / P)` with period `P = 2.5`
   - Gaussian noise with `np.random.normal(0, 0.18, size=t.shape)`
   - therefore: `flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + noise`
3. Plot the light curve with Matplotlib:
   - x-axis = time (hours)
   - y-axis = relative brightness
   - add a title and labels
4. Plot a histogram of brightness with Seaborn showing KDE.
5. Make a scatter plot with a smoothed curve:
   - use `plt.plot(t, flux, ".", alpha=0.6, label="data")`
   - calculate a smoothed version with a simple filter: use a moving average with `window=7` and plot it on top as a continuous red line.
6. Save the final figure as `light_curve.png`.

**Submission:** copy the code you ran and paste the saved image.

````{tip} Step-by-step hints
:class: dropdown

- Step 1:  
  ```python
  import numpy as np
  t = np.linspace(0, 10, 300)
  ```

- Step 2:  
  ```python
  P = 2.5
  noise = np.random.normal(0, 0.18, size=t.shape)
  flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + noise
  ```

- Step 3 (basic Matplotlib):  
  ```python
  import matplotlib.pyplot as plt
  plt.figure(figsize=(8,4))
  plt.plot(t, flux, ".", alpha=0.6)
  plt.xlabel("Time (hours)")
  plt.ylabel("Relative brightness")
  plt.title("Simulated light curve")
  plt.show()
  ```

- Step 4 (Histogram with KDE):  
  ```python
  import seaborn as sns
  sns.histplot(flux, bins=30, kde=True)
  plt.title("Brightness distribution")
  plt.show()
  ```

- Step 5 (Simple moving average smoothing):  
  ```python
  window = 7
  kernel = np.ones(window) / window
  flux_smooth = np.convolve(flux, kernel, mode="same")
  plt.figure(figsize=(8,4))
  plt.plot(t, flux, ".", alpha=0.4, label="data")
  plt.plot(t, flux_smooth, "-", color="C3", linewidth=2, label="smoothed (mov. avg)")
  plt.legend()
  plt.show()
  ```

- Step 6 (Save figure):  
  ```python
  plt.savefig("light_curve.png", dpi=150, bbox_inches="tight")
  ```

If something does not work, check that you imported `numpy`, `matplotlib.pyplot`, and `seaborn` correctly before running the cells.
````

````{tip} Solution (complete code)
:class: dropdown

```python
# Suggested complete code (copy and run)
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# data
t = np.linspace(0,10,300)
P = 2.5
np.random.seed(42)  # for reproducibility in the example
noise = np.random.normal(0, 0.18, size=t.shape)
flux = 1.5 + 0.8 * np.sin(2*np.pi*t / P) + noise

# figure: light curve
plt.figure(figsize=(10,4))
plt.plot(t, flux, ".", alpha=0.6, label="data")
plt.xlabel("Time (hours)")
plt.ylabel("Relative brightness")
plt.title("Simulated light curve")
plt.legend()
plt.tight_layout()
plt.show()

# histogram with KDE
plt.figure(figsize=(6,3))
sns.histplot(flux, bins=30, kde=True)
plt.title("Brightness distribution")
plt.tight_layout()
plt.show()

# smoothing (moving average)
window = 7
kernel = np.ones(window)/window
flux_smooth = np.convolve(flux, kernel, mode="same")

plt.figure(figsize=(10,4))
plt.plot(t, flux, ".", alpha=0.35, label="data")
plt.plot(t, flux_smooth, "-", color="C3", linewidth=2, label="smoothed (mov. avg)")
plt.xlabel("Time (hours)")
plt.ylabel("Relative brightness")
plt.title("Light curve with smoothing")
plt.legend()
plt.tight_layout()

# save
plt.savefig("light_curve.png", dpi=150, bbox_inches="tight")
plt.show()
````

The image `light_curve.png` will be created in the working directory.
You can adjust `window` for more or less aggressive smoothing.
