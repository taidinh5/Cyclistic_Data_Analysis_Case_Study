## 🔄 Process Phase – Data Cleaning & Integrity



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


CREATE TABLE CyclisticTripData2024.tripdata_merged AS (
  SELECT * FROM CyclisticTripData2024.jan
  UNION ALL
  SELECT * FROM CyclisticTripData2024.feb
  UNION ALL
  SELECT * FROM CyclisticTripData2024.mar
  UNION ALL
  SELECT * FROM CyclisticTripData2024.apr
  UNION ALL
  SELECT * FROM CyclisticTripData2024.may
  UNION ALL
  SELECT * FROM CyclisticTripData2024.jun
  UNION ALL
  SELECT * FROM CyclisticTripData2024.jul
  UNION ALL
  SELECT * FROM CyclisticTripData2024.aug
  UNION ALL
  SELECT * FROM CyclisticTripData2024.sep
  UNION ALL
  SELECT * FROM CyclisticTripData2024.oct
  UNION ALL
  SELECT * FROM CyclisticTripData2024.nov
  UNION ALL
  SELECT * FROM CyclisticTripData2024.dec
);


