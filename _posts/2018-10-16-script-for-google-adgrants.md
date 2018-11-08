---
title: Compliance Script for Google Ad Grants
categories: [code]
tags: [scripts, Google Ads, Google AdGrants, JavaScript]
---


In January 2018, Google Ad Grants substantially changed their 
[policy requirements](https://support.google.com/grants/topic/3500093) for grantees. 
(See [Google's Ad Grants Policy Compliance Guide](https://support.google.com/grants/answer/9042207)). 
Since maintaining our Google Ad account is not an explicit part of [RIM](https://www.rootedinmindfulness.org)'s
mission, we developed a script to evaluate our account for 
compliance to these policies. The script runs every morning around 6am and emails a report 
that delivers the results of each test (PASS/FAIL). In the event that a test fails, enough 
detail is provided to allow us to remedy the problem. 

## What do we test? 

We test everything that can be easily automated. An account that passes all the following tests will not necessarily be in compliance with the Ad Grants program. There are other compliance criteria that this script does not evaluate, *and*

>Google reserves the right to grant or deny an organization's application or participation at any time, for any reason, and to supplement or amend these eligibility guidelines at any time. -[Google Ad Grants Terms and Conditions](https://support.google.com/grants/answer/46103)

### Account Structure

<!---
At least 2 active ad groups per campaign each containing a set of closely related keywords and 2 active text ads.
Note: We do not check for "a set of closely related keywords".
-->

1. For each [campaign](https://support.google.com/google-ads/answer/6304), are there at least two active [ad groups](https://support.google.com/google-ads/answer/6298)?
2. For each [ad group](https://support.google.com/google-ads/answer/6298), are there at least two active [text ads](https://support.google.com/google-ads/answer/14093)?
3. Does the [account](https://support.google.com/google-ads/answer/1704396) have at least two [sitelink extensions](https://support.google.com/google-ads/answer/2375416)?
3. Does the [account](https://support.google.com/google-ads/answer/1704396) use [geo-targeting](https://support.google.com/google-ads/answer/1722043)?

### Account Performance

<!---
 All Ad Grants AdWords accounts must maintain a 5% click-through rate (CTR) each month (at the account level, not necessarily each keyword).
 -->
1. Is the click-through rate ([CTR](https://support.google.com/google-ads/answer/2615875)) for the account above 5% over the last 30 days? 

### Keywords

1. Does the [account](https://support.google.com/google-ads/answer/1704396) *NOT* have any single-word keywords?
2. Does the [account](https://support.google.com/google-ads/answer/1704396) *NOT* have any keywords with a [quality score](https://support.google.com/google-ads/answer/140351?hl=en) less than or equal to 2? 

### Links

1. Does the [account](https://support.google.com/google-ads/answer/1704396) *NOT* have any broken links?

