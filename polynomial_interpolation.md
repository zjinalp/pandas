
##### 📈 Polynomial Interpolation in Pandas

##### 🔢 Data Example

We have the following DataFrame:

| Index | Age   |
|-------|-------|
| 0     | 20.0  |
| 1     | NaN   |
| 2     | NaN   |
| 3     | 25.0  |
| 4     | NaN   |
| 5     | 40.0  |

We want to interpolate missing values using a **2nd-degree polynomial**.

---

##### 🧮 Step-by-Step Interpolation

###### ✅ Known Data Points

- (0, 20)
- (3, 25)
- (5, 40)

We want to fit a polynomial of the form:

```
f(x) = a₀ + a₁x + a₂x²
```

---

###### ⚙️ Step 1: Setup Equations

Using the known values:

1. f(0) = 20 ⇒  
   `a₀ = 20`

2. f(3) = 25 ⇒  
   `20 + 3a₁ + 9a₂ = 25` ⇒  
   `3a₁ + 9a₂ = 5`   (Equation 1)

3. f(5) = 40 ⇒  
   `20 + 5a₁ + 25a₂ = 40` ⇒  
   `5a₁ + 25a₂ = 20`  (Equation 2)

---

###### ✅ Step 2: Solve the System

Multiply Eq1 by 5:

```
15a₁ + 45a₂ = 25
```

Multiply Eq2 by 3:

```
15a₁ + 75a₂ = 60
```

Subtract:

```
(15a₁ + 75a₂) - (15a₁ + 45a₂) = 60 - 25  
→ 30a₂ = 35 → a₂ = 7/6
```

Now plug into Eq1:

```
3a₁ + 9*(7/6) = 5  
→ 3a₁ + 10.5 = 5 → a₁ = -11/6
```

---

###### ✅ Final Polynomial

```
f(x) = 20 - (11/6)x + (7/6)x²
```

---

###### 🔍 Step 3: Interpolate Missing Values

| x | f(x) Formula                  | Value   |
|---|-------------------------------|---------|
| 1 | 20 - (11/6)(1) + (7/6)(1)^2   | 19.33   |
| 2 | 20 - (11/6)(2) + (7/6)(4)     | 21.00   |
| 4 | 20 - (11/6)(4) + (7/6)(16)    | 31.33   |

---

###### 🟩 Final Interpolated Data

| Index | Age    |
|-------|--------|
| 0     | 20.00  |
| 1     | 19.33  |
| 2     | 21.00  |
| 3     | 25.00  |
| 4     | 31.33  |
| 5     | 40.00  |

---

###### 🧠 Summary

- **Polynomial interpolation** fits a smooth curve to known values.
- **Order 2** means it fits a quadratic (parabola).
- Better for capturing trends than linear interpolation.
- Be cautious with high-degree polynomials (can "wiggle" too much!).

---

> Want to visualize or compare with linear interpolation? Add graphs using `matplotlib` for better insight!
