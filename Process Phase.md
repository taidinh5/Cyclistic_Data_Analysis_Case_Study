## 🔄 Process Phase – Data Cleaning & Integrity

### 👏 Combine All CSV Files
1. I will be using Google BigQuery to combine the 12 csv files into one big file.
2. First, I uploaded all 12 csv files into a dataset called "CyclisticTripData2024" and used SQL to merge them into one big table called "tripdata_merged".

<img width="806" height="682" alt="combinetripdata" src="https://github.com/user-attachments/assets/a52b6215-35f9-46b1-bc31-2ca096d1d5e4" />
<img width="545" height="299" alt="countoftotalrows" src="https://github.com/user-attachments/assets/c7217546-14a8-454e-92d9-7f1cedd8ec80" />

3. Before EDA, cleaning and manipulation, I'll create a backup
<img width="465" height="43" alt="tripdatamergedbackup" src="https://github.com/user-attachments/assets/716cbe9b-bfd9-4ed0-bda5-7a35e45b3763" />
<img width="214" height="64" alt="{DAB08F82-67E6-412D-A1AA-0F4942FB41C8}" src="https://github.com/user-attachments/assets/fd30ae45-fc63-4e09-93ae-db2e1ef7e374" />

---

### 🔭 Exploratory Data Analysis
1. Check table schema and metadata
<img width="448" height="419" alt="{44DD2051-6E63-4042-A414-D6556BB729B4}" src="https://github.com/user-attachments/assets/caca558b-42c9-42b4-b18b-d6d89ce80653" />
<img width="604" height="613" alt="{0268ABEB-BA10-4962-8616-3DC6EBF81DA8}" src="https://github.com/user-attachments/assets/04f7c28b-0ceb-46d3-a8d1-f38dd0048875" />


---

### 🧼 Data Cleaning Framework: CLEAN

I'll use a framework that guides the data cleaning process using five steps: **Conceptualize**, **Locate**, **Evaluate**, **Augment**, and **Note**.

---

### C – Conceptualize the Data

- Here, conceptualizing and understanding the dataset is the first step to identifying what I actually need to care about and prioritize. I'll examine which columns to keep and which columns to remove.
- Understand the business task:  
  _Determine how annual members and casual riders *use* Cyclistic bikes differently to help convert more casual riders into annual members._

- Assess Columns:
  - `ride_id` (irrelevant)
  - `rideable_type` (shows which bikes are preferred by each user type, important for usage pattern)
  - `started_at` (needed to extract usage-based trends like month, day, hour, important for comparing when each user type rides)
  - `ended_at` (needed to extract usage-based trends like month, day, hour, important for comparing when each user type rides)
  - `start_station_name` (irrelevant)
  - `start_station_id` (irrelevant)
  - `end_station_name` (irrelevant)
  - `end_station_id` (irrelevant)
  - `start_lat` (irrelevant)
  - `start_lng` (irrelevant)
  - `end_lat` (irrelevant)
  - `end_lng` (irrelevant)
  - `member_casual` (target group, business task is centered on comparing this group)

---

### L – Locate Solvable Issues

- Remove irrelevant columns (e.g., station names/IDs/coordinates)
- Standardize column names and data types
- Ensure ride duration is consistently formatted (buckets or minutes)
- Fix incorrect or default dates (e.g., "12/30/1899")

---

### E – Evaluate Unsolvable Issues

- Drop rows with critical missing data that can't be imputed
- Discard extreme outliers if unjustifiable (e.g., 24+ hr rides)
- Note any inconsistencies that couldn't be resolved (e.g., incomplete station data)

---

### A – Augment the Data

- Extract time components (`month`, `day`, `hour`) from datetime
- Bucket ride durations (e.g., Under 10, 10 to 30, etc.)
- Merge monthly files into one complete dataset
- Create backup of the cleaned table for version control

---

### N – Note and Document

- Record all changes made (column removals, type conversions, filters)
- Explain why each cleaning step was taken
- Save cleaned dataset as `all_trips_2024`
- Backup saved as `all_trips_2024_backup`
- Mention tools used: BigQuery, Power Query, etc.

---


















### 🧹 Data Cleaning Steps
1. Filter to check for missing or negative values in key columns (e.g. `started_at`, `ended_at`, `member_casual`)
2. Sort by ascending order to ensure logical consistency and spot outliers (e.g. potential negative durations, missing values, inconsistent string naming, wrong date range, wrong data type)
3. Use data type functions (e.g. =isnumber(), =istext()) to ensure data types are correct
4. Remove duplicates (Data tab -> Remove Duplicates)
5. Clean any strings with leading/missing spaces or inconsistent capitalization (e.g. =trim(), =clean(), =proper(), Find & Replace)
6. If there are Primary Keys that cannot be NULL (e.g. =COUNTIF(A:A, A1) ), if any result is > 1, it is duplicated
7. Check spelling (Review tab -> Spelling)
8. Apply data validation to columns with categorical values  



### 👨‍🔧 Data Manipulation Steps
1. aaa


### 🔍 Verification that data is clean
1. Filter and sort again to inspect 
2. COUNTBLANK() to detect any remaining missing values
3. Conditional format to detect invalid entries



