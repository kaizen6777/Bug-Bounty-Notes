# BookMyShow Sensitive Data Exposure

- **ID Number**: A3:2017-Sensitive Data Exposure (OWASP TOP 10)
- **Name**: Sensitive Data Exposure
- **Reporter**: Akshay Mahajan
- **Submit Date**: 24/02/2021
- **Summary**: Sensitive information was being leaked on BookMyShow’s subdomain `https://fanhood-returns.bookmyshow.com/`.

## URL
`https://fanhood-returns.bookmyshow.com/`

## Platform
- **Operating System**: Windows 10
- **Browser**: Microsoft Edge

## Severity
**CRITICAL**

---

## Description

Sensitive Personally Identifiable Information (PII), including **name**, **phone number**, **delivery address**, and **payment mode**, was being exposed in the response when querying the order ID on a subdomain of BookMyShow. The expected result was the display of only the **order ID**, but the response also contained sensitive PII data.

---

## Steps to Reproduce
1. Visit the URL: `https://fanhood-returns.bookmyshow.com/` and enter a registered email ID.
2. The system returns the order ID, but upon intercepting the request with **Burp Suite**, sensitive information is revealed in the response.
3. Send the request to **Repeater** and observe the response that leaks the user’s PII.
4. Testing with different emails resulted in the same issue, exposing sensitive data for multiple users.

---

## Expected Result
Only the **order ID** should be visible in the response.

## Actual Result
The response includes the **entire order details**, including PII.

---

## Proof of Concept (POC)
Refer to the attached video for a detailed demonstration of this vulnerability.
