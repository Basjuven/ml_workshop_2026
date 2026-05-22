---
numbering:
  title:
    offset: 0
---
(variables)=
# Variables and Data Types

Before analyzing data, we first need to understand how Python stores information.

A **variable** is like a box where we store a value so we can use it later.

## Creating variables

```{code-block} python
temperature = 23
mass = 1.989e30
name = "Sun"

print(temperature)
print(mass)
print(name)
```

```{tip} Output
23<br>
1.989e+30<br>
Sun
```

## Basic data types

Python automatically detects the data type.

```{code-block} python
integer = 10
decimal = 3.14
text = "star"
boolean = True

print(type(integer))
print(type(decimal))
print(type(text))
print(type(boolean))
```

```{tip} Output
<class 'int'><br>
<class 'float'><br>
<class 'str'><br>
<class 'bool'>
```

## Operations with variables

We can use variables in physical calculations:

```{code-block} python
distance = 150_000_000      # km Earth-Sun
time = 500                  # light seconds
speed = distance/time

print(speed)
```

```{tip} Output
300000.0
```

You have just calculated the approximate speed of light.

## Strings (text)

```{code-block} python
star = "Betelgeuse"
message = "The observed star is " + star

print(message)
```

```{tip} Output
The observed star is Betelgeuse
```

## Booleans

They are used to make decisions.

```{code-block} python
temperature = 6000

is_hot = temperature > 5000
print(is_hot)
```

```{tip} Output
True
```

## Type conversion

```{code-block} python
number = "42"
number = int(number)

print(number + 8)
```

```{tip} Output
50
```

````{exercise}

**What data type is the result?**

```python
mass = 2
radius = 4.0
density = mass / radius
print(type(density))
```

A. int  
B. float  
C. str  
D. bool  

```{tip} View solution
:class: dropdown
Answer: **B**

When an integer is divided by a decimal number,
Python produces a decimal number (float).
```
````