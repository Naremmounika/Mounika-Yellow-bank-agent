# Mounika Yellow Bank Agent

## Objective

This project implements a Gen AI Banking Agent for Yellow Bank using the Yellow.ai platform. The agent securely authenticates users and allows them to view their loan details through a structured multi-step workflow.

---

## Flow Overview

1. User requests to view loan details
2. Agent collects:

   * Registered Phone Number
   * Date of Birth (DOB)
3. OTP is generated using a mock API (Beeceptor)
4. OTP is displayed in chat (for testing purposes)
5. User enters OTP
6. OTP is verified
7. Loan accounts are fetched and displayed
8. User selects a loan account
9. Loan details are displayed using Dynamic Rich Media

---

## Authentication Logic

* OTP is generated via Beeceptor mock API
* Since it is a mock service, OTP is shown in the chat for testing
* User-entered OTP is compared with generated OTP
* Access is granted only when OTP is correct
* Incorrect OTP shows an error message

---

## APIs Used

### 1. Trigger OTP

* Method: POST
* Endpoint: `/trigger-otp`

Response:

```json
{
  "status": "success",
  "otp": "1234"
}
```

---

### 2. Loan Accounts

* Method: GET
* Endpoint: `/loan-accounts`

Returns a list of loan accounts associated with the user.

---

### 3. Loan Details

* Method: GET
* Endpoint: `/loan-details`

Returns detailed loan information such as:

* Tenure
* Interest Rate
* Principal Pending
* Interest Pending
* Nominee

---

## Token Optimization

The loan accounts API returns large data with multiple fields.
A projection method is used to extract only required fields such as:

* Loan Account ID
* Loan Type
* Tenure

This reduces token usage and improves response efficiency.

---

##  Edge Cases Handled

* Invalid OTP entered by user
* API failure scenarios
* User requests to change phone number mid-process
* Restarting authentication while retaining user intent
* Handling unexpected inputs

---

## Language Constraint

The bot is restricted to English language only.
If the user interacts in any other language, the bot politely declines and asks the user to continue in English.

---

## Screenshots

Screenshots of the bot flow, API configuration, OTP verification, and Dynamic Rich Media cards are included in this repository.

---

## Platform & Tools Used

* Yellow.ai (Bot Development Platform)
* Beeceptor (Mock API Service)

---

## Note

Since Yellow.ai is a no-code platform and export functionality is not available in this environment, the implementation is documented here using descriptions, API details, and screenshots.

---
