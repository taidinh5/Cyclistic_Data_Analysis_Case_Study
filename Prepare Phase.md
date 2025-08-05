## Prepare Phase

## 🔍 Guiding Questions
- Where is your data located?
- How is the data organized?
- Are there issues with bias or credibility (ROCCC)?
- How are you addressing licensing, privacy, security, and accessibility?
- How did you verify the data’s integrity?
- How does it help you answer your question?
- Are there any problems with the data?

### Where is the data located?
The data is publicly available from the Divvy bike-share program in Chicago.  
Can be accessed here: [Divvy Trip Data](https://divvy-tripdata.s3.amazonaws.com/index.html)

### How is the data organized?
- Data is stored in **monthly CSV files**
- Each file contains individual ride records with fields such as:
  - `ride_id`, `rideable_type`, `started_at`, `ended_at`
  - `start_station_name`, `end_station_name`
  - `member_casual` (user type: member or casual)

### ROCCC Data Credibility Check
- **R**eliable: Provided directly by Divvy, the official source
- **O**riginal: Raw trip-level data from actual users
- **C**omprehensive: Covers all rides with rich metadata
- **C**urrent: Files are recent and updated monthly
- **C**ited: Hosted on a government-affiliated platform

### Licensing, Privacy, and Security
- Data is open for public use (no login or license required)
- No personally identifiable information (PII) is included
- Complies with privacy and ethical data-sharing practices

### 🧪 How was the data verified?
- Data was inspected for:
  - Missing values
  - Inconsistent timestamps (e.g., negative ride durations)
  - Duplicate entries
- Only records with valid timestamps and locations are retained

### How does this data help answer the business task?
- The `member_casual` field lets us compare behavior between user types
- Fields like `started_at`, `rideable_type`, and station locations help analyze:
  - Ride duration
  - Ride frequency
  - Time of day and day of week trends
  - Station usage patterns

### Problems or limitations in the data
- Some rides have:
  - Missing station names
  - Zero or negative durations
- Station names may vary slightly across months
- Trip data doesn’t capture **demographics** or **user motivations**
