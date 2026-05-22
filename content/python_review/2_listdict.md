---
numbering:
  title:
    offset: 0

kernelspec:
  name: python3
  display_name: 'Python 3'
---

(lists_dictionaries)=
# Lists and Dictionaries

So far, we have stored only one value in each variable. But in science, we almost always work with **many data points at the same time**.

Python has structures for storing collections:

- **List** → an ordered collection of values
- **Dictionary** → a collection of key-value pairs, like a simple table

---

## Lists

A list stores multiple values in order.

```{code-block} python
temperatures = [5600, 5800, 6000, 6200]

print(temperatures)
```

```{tip} Output
[5600, 5800, 6000, 6200]
```

### Accessing elements

```{code-block} python
print(temperatures[0])   # first element
print(temperatures[2])   # third element
```

```{tip} Output
5600<br>
6000
```

NOTE: Python starts counting from **0**.

### Modifying values

```{code-block} python
temperatures[1] = 5900
print(temperatures)
```

```{tip} Output
[5600, 5900, 6000, 6200]
```

### Adding elements

```{code-block} python
temperatures.append(6500)
print(temperatures)
```

```{tip} Output
[5600, 5900, 6000, 6200, 6500]
```

### Length of a list

```{code-block} python
print(len(temperatures))
```

```{tip} Output
5
```

````{exercise}

**What does the code print?**

```python
planets = ["Mercury","Venus","Earth","Mars"]
print(planets[3])
```

A. Earth  
B. Mars  
C. Venus  
D. Error  

```{tip} View solution
:class: dropdown
Answer: **B**

Index 3 corresponds to the fourth element: Mars.
```
`````

---

## Dictionaries

A dictionary stores labeled information, like columns in a table.

```{code-block} python
star = {
    "name": "Sirius",
    "temperature": 9940,
    "distance": 8.6
}

print(star)
```

```{tip} Output
{'name': 'Sirius', 'temperature': 9940, 'distance': 8.6}
```

---

### Accessing values

```{code-block} python
print(star["name"])
print(star["temperature"])
```

```{tip} Output
Sirius<br>
9940
```

---

### Modifying values

```{code-block} python
star["temperature"] = 10000
print(star)
```

---

### Adding a new property

```{code-block} python
star["type"] = "White star"
print(star)
```

---

````{exercise}

**What happens?**

```python
object_data = {"mass":2.0,"radius":1.0}
print(object_data["mass"])
```

A. Error  
B. 2.0  
C. "mass"  
D. None  

```{tip} View solution
:class: dropdown
Answer: **B**

The dictionary returns the value associated with the key.
```
````

---

`````{exercise}

**Mini astronomical database**

Create a dictionary called `galaxy` with:

- name: Andromeda
- distance: 2.5 million light-years
- type: Spiral

Then print only the distance.

````{tip} Hint
:class: dropdown
```python
galaxy = {
    "name": "Andromeda",
    "distance": 2.5,
    "type": "Spiral"
}

print(galaxy["distance"])
```
````

`````