# 🔐 Cybersecurity Threat Insights

This project dives into a dataset of over **14,000 cybersecurity incidents**, exploring the evolving landscape of digital threats. From AI-driven exploits to IoT vulnerabilities, I used Python and data science to uncover:

- 🔍 Where attacks happen most
- 🧠 How attackers exploit systems
- 🛡️ What detection and prevention methods work
- 📊 Which domains (like AI, satellites, or SCADA) are most impacted

This project is part of my [#30DaysWithData](https://github.com/w-kibor/30DaysWithData) challenge, where I solve real-world problems through hands-on data science.

---

## 📌 Project Goal
To explore and visualize the distribution and types of cybersecurity attacks across various domains using real world incident data

## Objectives
- Perform end-to-end EDA on the cybersecurity attack dataset
- Create compelling visualizations to communicate insights
- Understand the attack → detection → solution pipeline
- (Coming soon) Build predictive models to assess attack impact

---

## Source of Data
I got the dataset I used for this project prom kaggle datasets [Cybersecurity Attacks and Defense dataset](https://www.kaggle.com/datasets/tannubarot/cybersecurity-attack-and-defence-dataset)
It contains over 14,000 real-world cybersecurity incidents, including detailed information on attack types, targeted systems, vulnerabilities exploited, detection methods, and solutions. The dataset covers 26 cybersecurity domains such as:

AI / ML Security

IoT & Embedded Systems

Cloud Security

Satellite Infrastructure

SCADA / Industrial Systems

Web Application Security

This rich dataset forms the foundation for exploring trends, extracting insights, and building intelligent defense strategies.


## 📊 Exploratory Data Analysis (EDA)
The dataset contains 14,134 records of real-world cybersecurity threats across 26 domains such as AI, IoT, mobile, satellites, and more.

Key steps and findings during EDA include:

### ✅ 1. Missing Values
i) I identified and summarized missing values
```
df.isna().sum()
```

ii) Dropped the unnamed: 15 column since it was almost entirely null (14087 out of 14134 rows) and likely a result of an extra comma in the CSV or a trailing column.
```
df.drop(columns=['Unnamed: 15'], inplace=True)
```

iii) For the remaining columns I filled in the missing values
```
# Fill missing values with reasonable defaults
df['Tools Used'].fillna('Not specified', inplace=True)
df['Target Type'].fillna('Unknown', inplace=True)
df['Vulnerability'].fillna('Unspecified', inplace=True)
df['MITRE Technique'].fillna('Not Mapped', inplace=True)
df['Impact'].fillna('Unknown', inplace=True)
df['Detection Method'].fillna('Unspecified', inplace=True)
df['Solution'].fillna('Not provided', inplace=True)
df['Tags'].fillna('General', inplace=True)
df['Source'].fillna('Not Available', inplace=True)

```

## ✅ 2. Most Common Attack Types
Next I checked for the most common types of attacks to occur which included:
        1. Hardware Interface Exploitation
        2. Wireless Attacks (Advanced)
        3. Dependancy Confusion
        4. Fuzzer Configuration
        5. Malicious Libraries
        6. Priveledge escalation
        7. Misuse of legitimate tools
        8. Removable Media Attack
        9. Data Exfiltration

![Top 10 Attack Types](C:\Users\Administrator\OneDrive\Pictures\New folder\Top 10 cyber attacks.png)
