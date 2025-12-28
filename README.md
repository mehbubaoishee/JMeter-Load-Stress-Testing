# JMeter Performance Testing
**Name:** Mehbuba Alam Oishee  

---

### Project Description
This project performs **performance testing** on the **Restful Booker API** using **Apache JMeter**. The test simulates the following user scenario: **120,000 users over a 12-hour period** log in, create a booking with random data, and search for the created booking.

## Technology & Tools Used
- Apache JMeter 5.6.3 – main performance testing tool
- Standard Thread Groups + Flow Control Action (no plugins required)
- Gaussian Random Timer
- JSON Extractor
- HTML Dashboard Report Generator
- Microsoft Excel – for documenting test steps and results
- Git & GitHub – version control and submission

## How to Run the Tests
1. Open `booking.jmx` in JMeter
2. For load test: Enable the 3 "Step" groups, disable stress groups
3. Run in non-GUI: `jmeter -n -t booking.jmx -l load_test.jtl`
4. Generate report: `jmeter -g load_test.jtl -o LoadReport`
5. For stress test: Enable stress groups, disable load groups, use `stress_test.jtl` and `StressReport`

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

## Load Test Screenshots
<img width="1902" height="911" alt="Load-overall" src="https://github.com/user-attachments/assets/be4d3faf-ca5d-4499-aea0-86e2b134f537" />
<img width="1605" height="818" alt="Load-overall2" src="https://github.com/user-attachments/assets/d5cd528f-c963-4b02-a2e2-5de4bfe8408e" />

## Stress Test Results
- Peak throughput: 0.67 transactions/second
- Error rate: 0.00%
- Average response time: 593 ms
- APDEX Score: 0.821
- No degradation or breakdown observed even at 150 concurrent users
- Bottleneck throughput: ~0.67 transactions/second (no failure point reached within tested load)

## Stress Test Screenshots
<img width="1918" height="911" alt="stress-overall" src="https://github.com/user-attachments/assets/1f957e57-73d4-42f4-840b-21f697bcb7cf" />
<img width="1850" height="862" alt="stress-overall2" src="https://github.com/user-attachments/assets/f8b7b87c-8352-44a0-8667-3ef6c4495997" />
<img width="1850" height="862" alt="stress-overall2" src="https://github.com/user-attachments/assets/f8b7b87c-8352-44a0-8667-3ef6c4495997" />

