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

![<img width="1482" height="687" alt="Top 10 cyber attacks" src="https://github.com/user-attachments/assets/046a9276-43d2-42c4-8639-5d26926d71ed" />
]

## ✅ 3. Targets of SQL Injection Attacks
Analyzed which systems and technologies are most frequently targeted by SQL Injection (SQLi) attacks. Web applications, login forms, and database-driven platforms appear most vulnerable, highlighting the need for secure input handling and database access control.
![Targets of SQL Injection Attacks]
<img width="1433" height="691" alt="target of sql injection" src="https://github.com/user-attachments/assets/7a3c6005-75af-4b1d-b2f9-c039b1cf61a4" />


## ✅ 4. Common Vulnerabilities
Extracted the most common security flaws exploited in cyber attacks. Frequent issues include unvalidated user inputs, weak encryption, outdated firmware, and misconfigured access controls — all of which create entry points for attackers.
![Common Vulnerabilities]

<img width="1455" height="691" alt="most common vulnerabilities" src="https://github.com/user-attachments/assets/9cad9159-fdb2-48fc-82e4-103ce7a87d24" />


## ✅ 5. Most Common Cyber Attack Impacts
Investigated the real-world consequences of different attacks. The most reported impacts include data breaches, financial losses, system downtime, unauthorized access, and full system takeovers — reinforcing the importance of proactive defense mechanisms.


<img width="1422" height="683" alt="Most common cyber attacks impact" src="https://github.com/user-attachments/assets/c5a31f47-7c72-4bec-ab9b-4a811e282ba4" />

## 🧠 Key Insights & Takeaways
### 1. 🔐 Credential Theft is Dominant

Credential theft appears twice (with minor case differences), making it the most frequently reported impact.

This suggests attackers overwhelmingly target user authentication systems — making strong password policies, multi-factor authentication (MFA), and credential vaulting essential defenses.

### 2. 💻 Remote Code Execution (RCE) is a Major Threat

"Remote Code Execution" also shows up twice, indicating inconsistent labeling but high frequency.

RCE allows attackers to take full control of a system remotely, which can lead to system compromise, lateral movement, or data exfiltration.

### 3. 📉 Data Labeling Inconsistencies Exist

Repeated terms with slight formatting differences (e.g., Remote Code Execution vs. Remote code execution) highlight the importance of data cleaning before modeling.

You could consider grouping duplicates to improve analysis accuracy.

### 4. 🧠 MITRE ATT&CK IDs Appear in Impact

Entries like T0856 and T0884 refer to specific techniques from the MITRE ATT&CK framework.

This means some records define “impact” using standardized tactic IDs, which might need to be separated or mapped for clearer interpretation.

### 5. 🧨 Full System & Account Compromise are Serious Consequences

These two are mid-frequency but highly critical. Once a system or account is fully compromised, attackers can escalate privileges, exfiltrate data, or disable systems.

### 6. ⚠️ Unauthorized Access is Common but Underreported

“Unauthorized access” shows up but seems less frequent — possibly because it’s often a precursor to other more severe impacts like credential theft or system compromise.

### 7. Hardware Interface Exploitation and Wireless Attacks (Advanced) are the most common, with counts exceeding 140, indicating significant risks in hardware and wireless security.

### 8.Dependency Confusion, Fuzzer Configuration, and Malicious Libraries follow with high counts (around 100-120), suggesting vulnerabilities in software dependencies and configuration settings are also widespread.

### 9.Malicious Library, Privilege Escalation, and Misuse of Legitimate Tools show moderate prevalence (around 60-80), highlighting the importance of monitoring legitimate tool usage and privilege management.

### 10.Removable Media Attack and Data Exfiltration have the lowest counts (around 40-60), indicating these are less frequent but still notable threats.

## 💡 Recommendations Based on Insights
Based on the insights, I recommend prioritizing security enhancements in hardware interfaces and wireless networks, as they are the most prevalent attack types. Additionally, addressing vulnerabilities in software dependencies and configuration settings could significantly reduce risks. Improving monitoring of legitimate tool usage and privilege management may also help mitigate moderate threats. Exploring simpler, customer-driven solutions could uncover new opportunities to strengthen defenses and gain a competitive edge.

For Organizations, I recommend focusing on protecting against credential theft, as it is the most frequent impact with a count above 35. Strengthening authentication measures, such as multi-factor authentication, can help mitigate this risk. Additionally, addressing remote code execution and unauthorized access, which also show significant counts (around 20-30), by enhancing system security patches and access controls is advisable. Regular monitoring and updating of systems to prevent full system compromise and account compromise should also be prioritized.

## ✅ Conclusion

This project provided valuable insights into modern cybersecurity threats, especially the prevalence of credential theft, code execution vulnerabilities, and insecure IoT infrastructure. It demonstrates the power of data analysis in identifying attack trends and reinforces the importance of proactive defenses.

Stay tuned for upcoming projects in my #30DaysWithData series, where I’ll continue exploring real-world datasets to build data-driven solutions.

Feel free to ⭐️ this repo or connect with me on [LinkedIn](https://www.linkedin.com/in/wilkister-kibor/) to share feedback or ideas!

