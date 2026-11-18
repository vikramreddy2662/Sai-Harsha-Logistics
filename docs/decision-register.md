# Sai Harsha Logistics decision register

The [discovery prompt](codex-discovery-prompt.md) holds the complete interview backlog. This register records owner selections and related follow-ups.

| ID | Decision | Status | Owner selection | Recorded | Requirements affected |
| --- | --- | --- | --- | --- | --- |
| D14 | Business operating status and headquarters | Confirmed | Already operating in Telangana and Andhra Pradesh. Headquarters in Hyderabad, Telangana. | 2026-11-18 | Company profile, coverage page and operations discovery. |
| D02 | Freight service coverage | Confirmed | Option B. Domestic freight across India, including freight pickup and delivery at Indian ports. | 2026-11-18 | Freight service catalogue, quote form and port collection or delivery workflow. |
| D01 | First-release scope | Confirmed | Option B. Launch freight and passenger cab booking together, with live GPS and route-deviation alerts on every trip. | 2026-11-18 | Customer tracking, dispatch monitoring, driver workflow, GPS integration and launch acceptance criteria. |
| D03 | Pricing and booking confirmation | Confirmed | Option C. Show customer-facing estimates for both freight and passenger cab bookings. Staff confirm the final price and booking. | 2026-11-18 | Estimate rules, quote review and booking confirmation. |
| D06 | Launch GPS sources | Confirmed | Option C. Support vehicle GPS devices and driver phone location. | 2026-11-18 | Device and mobile tracking integrations, dispatch monitoring and route-deviation alerts. |

## Open follow-ups

| ID | Status | Outstanding decision or information |
| --- | --- | --- |
| D02 | Proposed | Identify the vehicle classes covered by existing permits and verify freight, passenger and port eligibility. Name the launch terminals and confirm their gate, appointment and document handoffs. |
| D03 | Proposed | Validate estimates against one redacted freight job and one redacted cab trip. Agree on rate factors, missing-rate fallback and customer acceptance of a revised final price. |
| D06 | Proposed | Confirm existing GPS providers, counts for owned and partner vehicles, and driver phone types. Validate background tracking, source handover, signal age and dispatch procedures when both feeds are unavailable. |
| D08, D15 | Proposed | Confirm payment methods and when to collect payment. Assign responsibility for invoices, consignment notes, e-way bill handling, delivery proof, and partner settlement. |
| D13 | Proposed | Confirm who responds to route deviations, breakdowns, failed deliveries and passenger assistance requests, including after hours. |
| D14 | Proposed | Confirm branch locations, if any. Confirm launch service details and fleet counts in a later round. |

### Launch GPS verification

The first-release scope applies to freight and cab trips, including those fulfilled by partner vehicles. Verify that each vehicle or assigned driver can supply GPS data through a supported source. Define how dispatch handles a missing or stale signal and how customers see the last known status. Confirm provider coverage and the operating rules during discovery.
