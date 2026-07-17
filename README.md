# 🧱 LEGO Data Analysis

This project explores real LEGO datasets using **Pandas** for data analysis and **Matplotlib** for data visualization.  
Throughout the notebook, we investigate colors, themes, sets, number of parts, trends over time, and relationships between tables through *foreign keys*.

---

## 🎨 Data Exploration — Colors

### How many LEGO colors exist?

We load the `colors.csv` file and count the number of unique color names.

### Transparent vs Opaque Colors

Using `groupby()`, we compare:

- Transparent colors (`is_trans == 't'`)
- Opaque colors (`is_trans == 'f'`)

---

## 🧱 LEGO Themes vs LEGO Sets

LEGO organizes its products by **themes** such as Star Wars, Batman, Harry Potter, and many more.  
Each theme contains multiple **sets**, which are the individual LEGO products sold in boxes.

---

## 📚 Exploring sets.csv

We load `sets.csv` and examine:

- The first and last rows  
- The year the earliest sets were released  
- The names of those first sets  
- How many sets and themes existed in the earliest year

---

## 🧩 Sets with the Most Parts

We sort the dataset by `num_parts` to identify the top 5 largest LEGO sets.

---

## 📈 Number of Sets Released per Year

Using `groupby()` + `count()`, we calculate how many sets were released each year.

We then compare:

- Sets released in **1955**  
- Sets released in **2019**

---

## 📉 Line Chart — Sets per Year

We plot the number of sets released per year using Matplotlib.  
Since the dataset ends in late 2020, we remove the last two years using slicing (`[:-2]`) to ensure only full calendar years are shown.

---

## 🔢 Aggregating Data with `.agg()`

We compute how many **unique themes** were released each year using:

```python
sets.groupby("year").agg(num_themes=("theme_id", "nunique"))
```

A line chart is then created, again excluding 2020 and 2021.

---

## 📊 Line Charts with Two Separate Axes

We calculate the **average number of parts per set** per year and compare:

- 1954  
- 2017  

A dual‑axis line chart is created:

- Axis 1 → number of sets released  
- Axis 2 → average number of parts  

---

## 🔵 Scatter Plot — Complexity Over Time

We plot a scatter chart of the average number of parts per year to observe trends.  
The chart clearly shows that LEGO sets have become more complex over the decades.

---

## 🏷 Number of Sets per LEGO Theme

We load `themes.csv` and count how many sets belong to each theme.  
By merging `sets` and `themes`, we obtain theme names and identify the **top 10 themes with the most sets**.

---

## 🗄 Schemas, Foreign Keys & Merging

We explain how:

- `sets.csv` uses `theme_id`  
- `themes.csv` uses `id`  

These fields form a **foreign key relationship**.

### Challenge: Star Wars

- Search for “Star Wars” in `themes.csv`  
- Count how many IDs correspond to this name  
- Use those IDs to find all Star Wars sets in `sets.csv`

---

## 🔗 Merging DataFrames Based on a Key

We create a DataFrame containing the number of sets per theme and merge it with `themes.csv` to retrieve theme names.

Finally, we visualize the top themes using a bar chart.
