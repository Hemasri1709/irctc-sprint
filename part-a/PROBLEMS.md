# IRCTC Problem Discovery – Part A

## Summary

- Platform: IRCTC Next Generation eTicketing System
- Device: Desktop (Chrome)
- Problems Documented: 6
- Given Problems: 3
- Self-discovered Problems: 3

---

# Problem 1 — Tatkal Booking Crashes at 10:00 AM (Given)

## What is broken

When Tatkal booking opens at 10 AM, the website becomes extremely slow or crashes. Users experience session timeouts, delayed OTPs and booking failures.

## Affected Users

Passengers booking Tatkal tickets, especially office workers, emergency travellers and students.

Estimated users:
20–40 lakh during Tatkal opening.

## Frequency

Occurs daily during Tatkal booking.

## Current Flow

1. User opens IRCTC before 10 AM.
2. User searches train.
3. User selects Tatkal quota.
4. User fills passenger details.
5. User clicks Book Now.
6. Website freezes.
7. Session expires or HTTP error appears.
8. Ticket becomes unavailable.

## Where exactly it breaks

Step 6.

The server cannot handle the sudden traffic spike and provides no meaningful progress feedback.

---

# Problem 2 — Search Filters Do Not Work Reliably (Given)

## What is broken

Search filters reset unexpectedly or display trains that do not match the selected filters.

## Affected Users

Almost every IRCTC user searching for trains.

## Frequency

Observed frequently, especially during busy hours.

## Current Flow

1. User searches trains.
2. Results are displayed.
3. User selects Sleeper filter.
4. User selects Available filter.
5. Results refresh.
6. Waitlisted trains still appear.
7. Going back resets filters.

## Where exactly it breaks

Steps 5–7.

Filter state is not preserved consistently.

---

# Problem 3 — Seat Selection Resets (Given)

## What is broken

Selected berth preference is lost before booking confirmation.

## Affected Users

Families, senior citizens and passengers requiring lower berths.

## Frequency

Occurs intermittently.

## Current Flow

1. User selects train.
2. Seat preference is selected.
3. Lower berth chosen.
4. User proceeds.
5. Preference changes to Auto.
6. User goes back.
7. Selected berth is unavailable.

## Where exactly it breaks

Between Steps 4 and 5.

Seat preference is not retained.

---

# Problem 4 — Passenger Details Form is Long and Confusing (Self-discovered)

Screenshot:
assets/screenshots/passenger-details-form.png

## How I Found It

While attempting to book a train till the payment page.

## What is broken

The passenger details page contains too many fields in one long form. Optional and mandatory fields are mixed together, making it difficult to identify what needs to be filled.

## Affected Users

First-time users, elderly passengers and users booking multiple tickets.

## Frequency

Always.

## Current Flow

1. User clicks Book Now.
2. Passenger Details page opens.
3. Large form is displayed.
4. User searches for required fields.
5. User scrolls multiple times.
6. Optional fields create confusion.
7. User continues after checking all fields.

## Where exactly it breaks

Steps 3–6.

Poor information hierarchy increases booking time and confusion.

---

# Problem 5 — Review Journey Page Provides Poor Booking Feedback (Self-discovered)

Screenshot:
assets/screenshots/review-journey.png

## How I Found It

While reviewing booking before payment.

## What is broken

The review page shows booking details but provides no clear indication about the next step. Important information such as booking status and payment progress is not highlighted.

## Affected Users

All users before payment.

## Frequency

Always.

## Current Flow

1. User reviews journey.
2. Passenger details appear.
3. Fare summary appears.
4. User scrolls.
5. CAPTCHA appears below.
6. User enters CAPTCHA.
7. Continues to payment.

## Where exactly it breaks

Steps 4–6.

Important actions are hidden below the fold, reducing visibility.

---

# Problem 6 — Payment Methods Page is Cluttered (Self-discovered)

Screenshot:
assets/screenshots/payment-methods.png

## How I Found It

Reached the payment page without completing payment.

## What is broken

The payment page lists many payment options simultaneously with fee information, making it visually cluttered. The most commonly used payment methods are not prioritised.

## Affected Users

Every passenger completing ticket payment.

## Frequency

Always.

## Current Flow

1. User reaches payment page.
2. Multiple payment options appear.
3. User compares payment methods.
4. Convenience charges create confusion.
5. User selects payment.
6. Clicks Pay & Book.

## Where exactly it breaks

Steps 2–4.

The interface overloads users with too many choices and insufficient visual hierarchy.

---

# Conclusion

The documented problems demonstrate usability, navigation, information hierarchy and performance issues across the IRCTC booking experience. These findings form the basis for proposing UI improvements and AI-assisted solutions in Part B.