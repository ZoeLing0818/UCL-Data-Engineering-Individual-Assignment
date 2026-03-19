# Risk Flag Guidelines

## Purpose
This document explains the rule-based review indicators used in the prototype entity risk signal layer.

These indicators are intended to support prioritisation and manual review. They are not definitive measures of misconduct, fraud, money laundering, or sanctions breaches.

---

## 1. `new_entity_flag`
### Definition
Triggered when the entity was incorporated within the last 365 days.

### Why it matters
Recently incorporated companies may have limited operating history and reduced disclosure depth. Government KYC guidance specifically notes that recently incorporated UK companies may require additional supporting evidence, such as a certified extract of the shareholder register. 

### Review interpretation
This is a recency and limited-history indicator, not a misconduct indicator.

---

## 2. `missing_location_flag`
### Definition
Triggered when key location fields such as `post_town` or `postcode` are missing.

### Why it matters
Incomplete location information weakens the transparency and usability of the entity profile. This may reduce confidence in the completeness of basic registry information and complicate downstream verification.

### Review interpretation
This is a profile completeness indicator.

---

## 3. `no_accounts_filed_flag`
### Definition
Triggered when `account_category` indicates `NO ACCOUNTS FILED`.

### Why it matters
KYC guidance notes that companies trading for more than 18 months are expected to provide their latest report and accounts where applicable. A lack of filed accounts therefore reduces disclosure visibility and may justify additional review. 

### Review interpretation
This is a disclosure-availability indicator, not a direct risk conclusion.

---

## 4. `has_outstanding_mortgage_flag`
### Definition
Triggered when the entity has one or more outstanding registered charges or mortgages.

### Why it matters
Outstanding registered charges indicate the continued existence of active secured obligations or financing-related structure. This may increase the relevance of additional structural review.

### Review interpretation
This is a structural attention indicator, not evidence of financial distress.

---

## 5. `mixed_mortgage_profile_flag`
### Definition
Triggered when the entity has outstanding registered charges and also has part-satisfied or satisfied charge history.

### Why it matters
This combination indicates that the entity’s charge profile is not static. Instead, it reflects a more mixed and potentially more complex secured-obligation history.

### Review interpretation
This is a structural complexity indicator.

---

## General Interpretation Guidance
Signals should be interpreted together rather than in isolation. FCA guidance on MLTM highlights that suspicious activity is often identified only when multiple sources of KYC information, alerts, and other contextual data are considered together. 

A higher review score means the entity is more suitable for prioritised review, not that wrongdoing has been established.