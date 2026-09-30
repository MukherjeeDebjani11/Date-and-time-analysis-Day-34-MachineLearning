# 📅 Day 34: Working with Date and Time Data in Pandas

> Part of my **100 Days of Machine Learning** journey, following the [CampusX](https://www.youtube.com/@campusx-official) playlist.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-013243?logo=numpy)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

---

## 📖 About

Date and time columns hide a lot of useful information. This notebook shows how to **convert, extract, and calculate** with datetime data using Pandas and NumPy, which is a key step in feature engineering for machine learning.

## 🎯 What I Learned

- Converting text columns to datetime with `pd.to_datetime()`
- Extracting date components: **year, month, day, day of week, week of year, quarter, semester**
- Checking weekdays vs weekends
- Getting month names and day names
- Extracting the **time** part (hour, minute, second) from a datetime
- Calculating **time differences** (days, months, years since a date)
- Working with a second dataset that has timestamps

## 🗂️ Repository Structure

```
├── Date-and-time-data.ipynb   # Main notebook
├── README.md                  # Project description
└── data/                      # Datasets used (if included)
```

## 🧰 Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Programming language |
| Pandas | Data handling and datetime methods |
| NumPy | Time delta calculations |
| JupyterLab | Interactive coding environment |

## 💡 Key Code Snippets

**Convert to datetime**
```python
date['date'] = pd.to_datetime(date['date'])
```

**Extract components**
```python
date['year']     = date['date'].dt.year
date['month']    = date['date'].dt.month
date['quarter']  = date['date'].dt.quarter
date['week']     = date['date'].dt.isocalendar().week
date['semester'] = (date['date'].dt.month > 6).astype(int) + 1
```

**Time since a date**
```python
today = pd.Timestamp.today()

# Days
(today - date['date']).dt.days

# Approximate months
np.round((today - date['date']).dt.days / 30.44, 0)
```

**Extract time from datetime**
```python
time['only_time'] = time['date'].dt.time
```

## ⚠️ Errors I Ran Into (and Fixed)

| Error | Cause | Fix |
|-------|-------|-----|
| `AttributeError: no attribute 'week'` | `.dt.week` removed in Pandas 2.0+ | Use `.dt.isocalendar().week` |
| `AttributeError: no attribute 'quater'` | Spelling mistake | Use `.dt.quarter` |
| `ValueError` with `np.timedelta64(1, 'M')` | Months have variable length | Divide days by `30.44` |
| `KeyError: 'time'` | Column name did not exist | Check names with `df.columns` |

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/MukherjeeDebjani11/REPO-NAME.git
   cd REPO-NAME
   ```
2. **Install the libraries**
   ```bash
   pip install pandas numpy jupyter
   ```
3. **Start Jupyter**
   ```bash
   jupyter lab
   ```
4. Open `Date-and-time-data.ipynb` and run the cells in order.

## 📚 Resources

- [CampusX 100 Days of Machine Learning (YouTube)](https://www.youtube.com/@campusx-official)
- [Pandas Time Series Documentation](https://pandas.pydata.org/docs/user_guide/timeseries.html)
- [Pandas `.dt` Accessor](https://pandas.pydata.org/docs/reference/series.html#datetime-properties)

## 🔜 What's Next

- Day 35 and onwards from the playlist
- Applying datetime features in a real ML pipeline

## 👩‍💻 Author

**Debjani Mukherjee**
B.Tech CSE student | Aspiring SDE / AI-ML Engineer

- GitHub: [MukherjeeDebjani11](https://github.com/MukherjeeDebjani11)
- LinkedIn: [debjani-m](https://linkedin.com/in/debjani-m)

---

⭐ If you found this helpful, consider giving the repo a star!
