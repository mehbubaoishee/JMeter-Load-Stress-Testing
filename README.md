# JMeter Performance Testing-1
**Name:** Mehbuba Alam Oishee  
**Batch No:** 17

---

### Project Description
This project performs **performance testing** on the **Restful Booker API**[](https://restful-booker.herokuapp.com) using **Apache JMeter**. 
The test simulates the following user scenario: **120,000 users over a 12-hour period** log in, create a booking with random data, and search for the created booking.

## Technology & Tools Used
- Apache JMeter 5.6.3 – main performance testing tool
- Standard Thread Groups + Flow Control Action (no plugins required)
- Gaussian Random Timer
- JSON Extractor
- HTML Dashboard Report Generator
- Microsoft Excel – for documenting test steps and results
- Git & GitHub – version control and submission  

## What I Have Done
- Created `booking.jmx` with Login, Create Booking (random firstname, lastname, totalprice), and Search Booking requests.
- Added global header Accept: */*
- Added Content-Type: application/json only where needed (Login and Create Booking).
- Added Gaussian Random Timer (Deviation 2000ms, Constant Delay 500ms).
- Performed load test in 3 steps (5 min, 10 min, 20 min increasing load) using multiple Thread Groups running consecutively.
- Performed stress test with gradually increasing concurrent users (up to 150) to identify bottleneck.
- Generated HTML dashboard reports for both tests.
- Documented steps and results in Excel file.

## Load Test Results
- Overall throughput: ~0.6–0.7 transactions/second
- Average response time: ~500–600 ms
- Error rate: 0%
- Server handled the simulated load successfully with no errors.

### Load Test Screenshots



## Stress Test Results
- Peak throughput: 0.67 transactions/second
- Error rate: 0.00%
- Average response time: 593 ms
- APDEX Score: 0.821
- No degradation or breakdown observed even at 150 concurrent users
- Bottleneck throughput: ~0.67 transactions/second (no failure point reached within tested load)

### Stress Test Screenshots


## Excel Reports
https://docs.google.com/spreadsheets/d/1EVR3Dfs4nw97w079L8FdaR7eWq8KDm9n89htA3c9VkQ/edit?usp=sharing

## How to Run the Tests
1. Open `booking.jmx` in JMeter
2. For load test: Enable the 3 "Step" groups, disable stress groups
3. Run in non-GUI: `jmeter -n -t booking.jmx -l load_test.jtl`
4. Generate report: `jmeter -g load_test.jtl -o LoadReport`
5. For stress test: Enable stress groups, disable load groups, use `stress_test.jtl` and `StressReport`
