![A/B Testing Image](Image/ab_testing_image.jpg)

# A/B Testing for Search Ranking System

## Project Overview

This project presents a data-driven analysis of an A/B test conducted at an online travel agency (OTA). The goal of the experiment was to evaluate a new search ranking system designed to improve the conversion rate of users. This document summarizes the methodology, analysis, and findings of the experiment to determine whether the new system should be rolled out.

## Methodology

The analysis was conducted using Python and a series of statistical tests to ensure the validity of the results. The key steps of the methodology are outlined below.

### 1. Data Preparation

- **Data Loading**: The analysis utilized two datasets: `sessions_data.csv` (containing session-level booking data) and `users_data.csv` (with user-level experiment group assignments).
- **Data Merging**: The two datasets were merged to create a comprehensive view, linking session activities to their respective user and experiment group (control or variant).

### 2. Metric Definition

Two key metrics were defined to evaluate the performance of the new search ranking system:

- **Primary Metric (Conversion Rate)**: A binary metric indicating whether a session resulted in a booking. This was the main success metric for the experiment.
- **Guardrail Metric (Time to Booking)**: The time taken from the start of a session to when a booking was made. This metric was monitored to ensure that the new system did not negatively impact the user experience by increasing the time to book.

### 3. Sanity Checks

- **Sample Ratio Mismatch (SRM) Test**: A Chi-Square test was performed to check for any significant difference in the number of users assigned to the control and variant groups. This ensures that the experiment groups are comparable and the test results are reliable.

### 4. Statistical Analysis

- **Hypothesis Testing**: Statistical tests were conducted to determine the significance of the effect of the new ranking system on both the primary and guardrail metrics. The analysis was performed with a 90% confidence level (alpha = 0.1).
- **Effect Size Calculation**: The practical significance of the changes was measured by calculating the effect size for both metrics. This helps in understanding the magnitude of the impact of the new system.

## Results and Achievements

The full analysis, including the detailed statistical test results (p-values), effect sizes for both primary and guardrail metrics, and the final decision logic, is documented in the Jupyter Notebook: `Notebooks/notebook.ipynb`.

The key achievements of this project include:
- A thorough and statistically rigorous evaluation of an A/B test.
- The development of a clear framework for making a data-driven decision on product changes.
- The delivery of a recommendation based on the analysis of the experiment results.

## Conclusion

The final recommendation on whether to roll out the new search ranking system is based on the statistical significance of the change in conversion rate and the impact on the time to booking. The detailed conclusion is available in the analysis notebook.

## Data Dictionary

### `sessions_data.csv`

| column | data type | description |
|--------|-----------|-------------|
| `session_id` | `string` | Unique session identifier (unique for each row) |
| `user_id` | `string` | Unique user identifier (non logged-in users have missing user_id values; each user can have multiple sessions) |
| `session_start_timestamp` | `string` | When a session started |
| `booking_timestamp` | `string` | When a booking was made (missing if no booking was made during a session) |
| `time_to_booking` | `float` | time from start of the session to booking, in minutes (missing if no booking was made during a session) |

### `users_data.csv`

| column | data type | description |
|--------|-----------|-------------|
| `user_id` | `string` | Unique user identifier (only logged-in users in this table) |
| `experiment_group` | `string` | control / variant split for the experiment (expected to be equal 50/50) |
