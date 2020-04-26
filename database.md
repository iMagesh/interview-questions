## Database Interview Questions

### Write SQL query to find the 3rd highest salary from table without using TOP/limit keyword.

## Database have Venues like St. John’s hospital. Write a single query to fetch results for following search terms
St. John’s Hospital
St johns hospital
ST JOHN Hospital
John’s hospital
Similarity should be at-least 50%
Answer: Can use ilike (okish answer)
        Can use extensions i.e.., pg_trgm for postgres (Better answer)

