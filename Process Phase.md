## 🔄 Process Phase – Data Cleaning & Integrity

### 👏 Combine All CSV Files
1. I will be using Google BigQuery to combine the 12 csv files into one big file.
2. First, I uploaded all 12 csv files into a dataset called "CyclisticTripData2024" and used SQL to merge them into one big table called "tripdata_merged".

<img width="806" height="682" alt="combinetripdata" src="https://github.com/user-attachments/assets/a52b6215-35f9-46b1-bc31-2ca096d1d5e4" />

3. Before EDA, cleaning and manipulation, I'll create a backup
<img width="465" height="43" alt="tripdatamergedbackup" src="https://github.com/user-attachments/assets/716cbe9b-bfd9-4ed0-bda5-7a35e45b3763" />
<img width="214" height="64" alt="{DAB08F82-67E6-412D-A1AA-0F4942FB41C8}" src="https://github.com/user-attachments/assets/fd30ae45-fc63-4e09-93ae-db2e1ef7e374" />

---

### 🔭 Exploratory Data Analysis
1. Check table schema and metadata
<img width="448" height="419" alt="{44DD2051-6E63-4042-A414-D6556BB729B4}" src="https://github.com/user-attachments/assets/caca558b-42c9-42b4-b18b-d6d89ce80653" />
<img width="604" height="613" alt="{0268ABEB-BA10-4962-8616-3DC6EBF81DA8}" src="https://github.com/user-attachments/assets/04f7c28b-0ceb-46d3-a8d1-f38dd0048875" />

2. Check for NULLS across all columns
   
<img width="507" height="264" alt="{E53A13D6-8517-42CA-8DFE-1461F1D95047}" src="https://github.com/user-attachments/assets/7b6412d2-6a3b-4be5-b77c-84cd25d04920" />

2a. It appears only these columns have NULLS
   
<img width="1139" height="66" alt="{89400E6D-981F-4BC8-A93A-F43D32036773}" src="https://github.com/user-attachments/assets/2a74c50d-c5d0-4f0f-8dbe-47ff0fec15ba" />

3. Check for duplicate rows

<img width="502" height="328" alt="{8AFDC9AB-E8AA-4999-BC8A-972090CA9843}" src="https://github.com/user-attachments/assets/32867a3a-0edb-4c27-a495-b456763c6641" />

3a. It appears there are no duplicate rows
   
<img width="226" height="38" alt="{D59A0AF6-A6AF-42AA-9996-19CBB38438DA}" src="https://github.com/user-attachments/assets/862713f4-7a9f-4091-afba-ab785884e3da" />

4. Check `ride_id` character length
   
<img width="500" height="71" alt="{BA1F74BB-A0BF-4FD4-AAA4-0E13C70ADC11}" src="https://github.com/user-attachments/assets/b60ff81d-43a3-4b3e-9d29-0073d2848541" />

4a. It appears all ride_id have a length of 16 characters

<img width="192" height="54" alt="{BDDADF17-7539-4BD4-B24C-5B02B961EC59}" src="https://github.com/user-attachments/assets/93b1f69c-f594-4e0d-b1bf-e640f7db0d88" />

5. Check `rideable_type` types of rideables

<img width="496" height="72" alt="{F1E65908-82EC-4D2A-814B-48761A9DEFA1}" src="https://github.com/user-attachments/assets/c170f799-5667-4d95-992d-fbe3b3e77a0d" />

5a. It appears there are only 3 unique types of rideables

<img width="256" height="104" alt="{0647AA59-26FE-4883-A17F-B3505996F494}" src="https://github.com/user-attachments/assets/1a00d055-b9c8-447a-a094-4e9ee2b81dbb" />

6. Check `started_at` and `ended_at` to find ride durations that are longer than a day and shorter than a second

<img width="516" height="154" alt="{C4B80188-3605-4051-855E-D5CA58741824}" src="https://github.com/user-attachments/assets/79487f21-4486-4175-854c-db3cec470caf" />

6a. It appears we have approx 13k rides that are longer than a day or shorter than a second

<img width="196" height="59" alt="{9E165808-7930-4B4F-9A01-A6D084A7BFB8}" src="https://github.com/user-attachments/assets/7fccf65a-76f2-4555-9b64-f5bfb94232ca" />

7. Check `member_casual` types of users

<img width="502" height="76" alt="{86A97162-A3FD-4DDC-AEA1-1CB3941E0AB6}" src="https://github.com/user-attachments/assets/692c19ae-8148-4053-aa3b-401f98be6a2c" />

7a. It appears there are indeed 2 types of users, which aligns with our business task

<img width="262" height="86" alt="{830CB36A-49AD-4EDF-AFA4-FB39A1121A8A}" src="https://github.com/user-attachments/assets/b7610f46-4554-4f11-83c7-42e575c94f2a" />


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



