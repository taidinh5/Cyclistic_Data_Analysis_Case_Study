## 🔄 Process Phase – Data Cleaning & Integrity

### 🔍 Combine All CSV Files
1. I will be using Google BigQuery to combine the 12 csv files into one big file.
2. First, I uploaded all 12 csv files into a dataset called "CyclisticTripData2024" and used SQL to merge them into one big table called "tripdata_merged".

<img width="806" height="682" alt="combinetripdata" src="https://github.com/user-attachments/assets/a52b6215-35f9-46b1-bc31-2ca096d1d5e4" />
<img width="545" height="299" alt="countoftotalrows" src="https://github.com/user-attachments/assets/c7217546-14a8-454e-92d9-7f1cedd8ec80" />

3. There are 5,860,568 rows total

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



