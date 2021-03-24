# Pay by 95th percentile bandwidth

Basic bandwidth plans and cross-border acceleration bandwidth plans support the billing method of pay by 95th percentile bandwidth. If the bandwidth usage is high and the peak bandwidth cannot be estimated, we recommend that you use this billing method.

**Note:** Only users who are added in the whitelist can purchase basic bandwidth plans and cross-border acceleration bandwidth plans on a pay by 95th percentile bandwidth basis. If you are not in the whitelist and need to use this billing method, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).

## Billing method

The following formula shows how bandwidth usage is billed on a pay by 95th percentile bandwidth basis:

-   Calculation formula

    Total fee of each bandwidth plan = Max \(Average of minimum bandwidth guaranteed, 95th percentile bandwidth\) × Price of the month × Percentage of valid days

    Max \(Average of minimum bandwidth guaranteed, 95th percentile bandwidth\) represents the larger value between the average of minimum bandwidth guaranteed and the 95th percentile bandwidth of the month. For more information, see [Average of minimum bandwidth guaranteed](#section_k96_0zx_xtv) and [95th percentile bandwidth](#section_v7a_ghl_3l2).

-   Billing cycle

    Bills of pay by 95th percentile bandwidth plans are generated on a monthly basis.

-   Billing date

    The bill for the current billing cycle is issued on the first day of the next calendar month. For example, on April 1, 2017, the bill of the previous month \(00:00:00, March 1, 2017 to 23:59:59, March 31, 2017\) was issued. After a bill is issued, the fees are automatically deducted from your account balance. Make sure that you have a sufficient balance in your account. Otherwise, overdue payments may occur.


## Average of minimum bandwidth guaranteed

-   Calculate the average of minimum bandwidth guaranteed

    Average of minimum bandwidth guaranteed = Total sum of minimum bandwidth guaranteed each day during the month/Number of days that the pay by 95th percentile bandwidth plan is used

-   Calculate the minimum bandwidth guaranteed each day

    If the bandwidth plan is resized multiple times within a day, the minimum bandwidth guaranteed on the day equals the maximum bandwidth supported by the bandwidth plan on the day.

    **Note:** By default, the valid bandwidth range of a bandwidth plan is from 100 to 2,000 Mbit/s. To adjust the bandwidth value or the percentage of the minimum bandwidth guaranteed, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182188.console-base-top.dworkorder.18ae4882n3v6ZW#/ticket/createIndex).


## 95th percentile bandwidth

The 95th percentile bandwidth of a bandwidth plan refers to the total sum of the 95th percentile bandwidths of a month in all acceleration regions specified in the bandwidth plan. The 95th percentile bandwidth of a month in each acceleration region is calculated based on the following rules:

The peak bandwidth value is calculated every five minutes. Within each five-minute interval, the average values of both the inbound and outbound bandwidth are collected. Between the average values of the inbound and outbound bandwidth, the larger value is used as a data point. The collected data points are sorted in descending order. The top 5% of the data points are excluded and then the largest value among the remaining 95% of the data points is used as the 95th percentile bandwidth of the month.

For example, you have purchased a pay by 95th percentile bandwidth plan that has a peak bandwidth value of 300 Mbit/s. China \(Beijing\), China \(Shanghai\), and China \(Hangzhou\) are specified as acceleration regions.

-   The maximum bandwidths allocated to China \(Beijing\), China \(Shanghai\), and China \(Hangzhou\) are 100 Mbit/s, 80 Mbit/s, and 120 Mbit/s, respectively.
-   The 95th percentile bandwidths during a month in the China \(Beijing\), China \(Shanghai\), and China \(Hangzhou\) regions are calculated separately. Assume that the 95th percentile bandwidths in the regions are 80 Mbit/s, 50 Mbit/s, and 60 Mbit/s, respectively.
-   Therefore, the total 95th percentile bandwidth of the bandwidth plan is 80 Mbit/s + 50 Mbit/s + 60 Mbit/s = 190 Mbit/s.

## Percentage of valid days

Percentage of valid days = The number of days that the pay by 95th percentile bandwidth plan is used/The total number of calendar days of the month

## Examples

Scenarios:

-   You have purchased a basic bandwidth plan, the type of which is enhanced acceleration bandwidth. The billing method of the basic bandwidth plan is pay by 95th percentile bandwidth.
-   From June 1 to June 10, you set the bandwidth to 200 Mbit/s. From June 11 to June 20, you set the bandwidth to 300 Mbit/s. On June 20, you deleted the bandwidth plan.
-   China \(Beijing\), China \(Shanghai\), and China \(Hangzhou\) are specified as acceleration regions.
-   Assume that the price of each month is USD 55.

Calculation of fees:

-   From June 1 to June 10, the minimum bandwidth guaranteed is 60 Mbit/s per day. From June 11 to June 20, the minimum bandwidth guaranteed is 90 Mbit/s per day.

    Average of minimum bandwidth guaranteed = \(60 Mbit/s × 10 + 90 Mbit/s × 10\)/20 = 75 Mbit/s

-   The 95th percentile bandwidths in the China \(Beijing\), China \(Shanghai\), and China \(Hangzhou\) regions are calculated separately. Assume that the 95th percentile bandwidths in the regions are 30 Mbit/s, 30 Mbit/s, and 30 Mbit/s, respectively.

    The total 95th percentile bandwidth of the bandwidth plan = 30 Mbit/s + 30 Mbit/s + 30 Mbit/s = 90 Mbit/s

-   Choose the larger value between the average of minimum bandwidth guaranteed and the 95th percentile bandwidth, which is 90 Mbit/s.

    The price of each month is USD 55.

-   The total bandwidth usage fee of the month = 90 Mbit/s × USD 55 × 20/30 = USD 3,300

