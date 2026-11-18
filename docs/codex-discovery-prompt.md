# Sai Harsha Logistics full-stack application discovery prompt

Use this entire document as the prompt for Codex. The project is `vikramreddy2662/Sai-Harsha-Logistics`. Continue from the existing repository and read its instructions first. This document is a discovery brief. Business decisions, designs, costs, and launch commitments require owner confirmation.

## 1. Objective

Design a fast, mobile-friendly web application for a pan-India transport and logistics company. The public site should explain each service, help customers find a suitable vehicle, and convert visits into enquiries or booking requests. The operations dashboard should give dispatchers a clear view of leads, bookings, fleet availability, active trips, and incidents. Keep the frontend and backend independently maintainable and design for measured growth and predictable operating costs.

## 2. Owner-provided requirements

### Public website and bookings

- Serve businesses and individuals across India. Present freight and passenger transport as distinct services with separate forms, vehicle filters, and pricing inputs. Publish approved service descriptions, coverage, fleet information, and contact channels.
- Freight use cases include luggage and household goods, appliances, vegetables and crops, rice-mill loads, manufacturing goods, and industrial materials such as iron. The owner described loads up to roughly 5–10 tonnes. Use verified payloads per vehicle. Confirm whether references to import and export mean domestic movement for traders, cargo to or from ports, or cross-border services.
- Passenger services include trips for families and groups using 5- and 7-seat cars. Confirm vehicle seating conventions and passenger trip types. Initial examples across the fleet include Mahindra Bolero, Mahindra Jeeto, Tata Ace, Eicher trucks, vans, and cars. Both company and partner vehicles are used.
- Display customer-facing vehicle types, payload/seats, and availability information at the level the owner approves. Keep dispatch assignments, private vehicle records, and partner commercial terms within authorised roles.
- Provide English by default and offer Hindi, Telugu, and Tamil. Persist the user's choice. Propose translation coverage, review ownership, and message and PDF fallback rules. Handle Indian-language fonts, text wrapping, and layouts on small screens. Include accessible, purposeful animations and honour reduced-motion preferences.
- Give customers website booking, WhatsApp, phone, and email options. Admin confirmation should trigger a booking acknowledgement document plus an email and a message through the selected channel. Customers should receive a trip-start update for freight and passenger journeys and be able to track their booking.

### Dispatch, fleet, and trip operations

- Define independent freight and passenger workflows over shared booking and trip records. Cover enquiry, quotation or price confirmation, booking approval, assignment, trip start, transit, completion, and exceptions. Freight needs pickup, delivery, and any approved delivery evidence. Passenger trips need pickup, boarding or no-show handling if selected, and ride completion. Define which actor can advance each state and handling of cancellations, reschedules, failed deliveries, and vehicle swaps.
- Give admins UI controls to add, edit, activate, deactivate, take out for maintenance, and remove vehicle listings. Define removal and restoration rules that preserve trip, finance, and audit history. Track operational status separately from availability for a requested time window. Prevent conflicting assignments and block vehicles in maintenance or with expired documents according to business rules. For an active trip, require an explicit handover or reassignment workflow.
- Propose a dispatch role, an administrator role, a limited driver interface, and relevant finance and owner access. The dashboard should show enquiries awaiting follow-up, bookings requiring action, available vehicles, active trips, outstanding incidents, and notification failures. Give drivers access to assigned work, trip status actions, and approved channels to contact dispatch.
- Track trips with the chosen GPS source. Show last update and stale/offline state. Compare trusted location samples to an approved route and raise a route-deviation alert for admin review. Design for GPS drift, approved detours, reroutes, coverage gaps, duplicate samples, and late updates. Make thresholds configurable, with separate distance and persistence settings. Define alert severity, acknowledgement, escalation, resolution, and audit history. Treat deviation as a signal for review.
- Propose a notification matrix by event, recipient, channel, and language. Include request received, booking confirmed, assigned, trip started, delayed or ETA changed where reliable, arrived, delivered or completed, cancelled, and delivery failure. Route deviation and GPS loss should go to authorised operations staff according to the approved escalation rules.

### Partner fleet and acknowledgements

- Support businesses and individuals who supply vehicles. Model provider contacts, vehicle make/type/model/year, registration, load capacity or seating, availability, document status, and trip history. Store ownership, commercial agreement, and vehicle record separately.
- Support per-trip hire, percentage commission, and monthly rent. Agree on the basis for commission, advances and adjustments, tolls, taxes, waiting or extra charges, settlement approval, balance, and reporting. Snapshot agreed terms when a trip or hire is confirmed so later changes do not rewrite historical obligations. Keep customer charges and partner payables separate.
- Provide a deliberate **Send acknowledgement to vehicle owner** checkbox during the relevant workflow. Preview the recipient and document, send by email after saving the agreement or assignment, and show sent, failed, and retry state. Prevent duplicates on repeated saves. Ask whether the acknowledgement is for onboarding, dispatch, settlement, or more than one event, and confirm who is authorised to send each document.

### WhatsApp lead capture

- Show a WhatsApp entry point on the public site. A prefilled link opens a chat. Once a customer sends a message, the configured WhatsApp Business integration can receive it, create or update a lead, send the chosen reply, and alert the admin. A website form can capture contact details before opening WhatsApp if the owner chooses that flow.
- Recommend a short flow for language, freight versus passenger, route, date, basic cargo or passenger details, and human handoff. Capture only the fields needed for follow-up. Define lead ownership, consent and contact preferences, deduplication, and what happens on repeat messages, missed replies, and provider outages. Verify current provider onboarding, templates, messaging rules, and costs before selecting an integration.

## 3. Research and feasibility review

Use primary sources and record the feature, source link, date checked, applicability, and proposed phase. Expand the shortlist only where it helps answer a business or feasibility question. Benchmark workflow patterns and design an original interface.

| Reference | Pattern to evaluate for Sai Harsha Logistics |
| --- | --- |
| [Porter Spot FAQ](https://porter.in/spot-faq) | Vehicle selection and trip tracking for goods booking. Evaluate a separate catalogue and quote flow for heavier loads. |
| [Delhivery order tracking](https://help.delhivery.com/docs/track-orders) and [B2B order workflow](https://help.delhivery.com/home/docs/b2b-order-creation) | Shipment milestones, reference numbers and proof of delivery. Select only the milestones needed for direct dispatch. |
| [Routematic transport operations](https://routematic.com/employee-transport-management-software/) and [trip monitoring SOP](https://routematic.com/blog/sop-for-employee-transportation/) | Live monitoring and escalation for passenger trips. Calibrate deviation handling for the company's freight and cab routes. |
| [WhatsApp click to chat](https://faq.whatsapp.com/5913398998672934/) and [Meta WhatsApp Business Platform](https://developers.facebook.com/documentation/business-messaging/whatsapp/overview) | Chat entry, inbound messages, replies, and provider prerequisites. Compare direct integration with an approved provider. |
| [Google Routes API](https://developers.google.com/maps/documentation/routes/quick-reference) and [Roads API](https://developers.google.com/maps/documentation/roads/snap) | Planned route geometry and GPS map matching. Validate suitable commercial-vehicle routes, provider coverage, licensing, and costs for the selected routes. |

Verify current India-specific permit, document, invoicing, privacy, and operational requirements against official sources and confirm the owner's actual process with their qualified adviser where needed. Check goods and passenger permissions separately before making public coverage claims. Confirm treatment of cargo categories, LRs or consignment notes, invoices, e-way bill references, and proof of delivery by service type. Flag requirements that need owner or adviser verification in the decision log.

## 4. Interview the owner and retain the decisions

Ask the questions in groups of roughly five. Explain what each option changes for the customer, the operations team, launch timing, and costs when material. Allow a custom answer or “defer.” A recommendation remains proposed until the owner accepts it. Reuse prior answers and ask focused follow-ups where needed.

| ID | Decision | Options and suggested starting point |
| --- | --- | --- |
| D01 | Launch scope | A. Freight and passenger request, admin approval and milestone tracking, with live GPS for a pilot fleet. B. Both services with live GPS and automated alerts on all booked trips at launch. C. Freight first, passenger trips later. Suggest A if provider readiness varies. |
| D02 | Services and coverage | A. Pan-India domestic trips subject to route and vehicle confirmation. B. Domestic service plus port pickup and delivery for traders. C. Include a separately defined cross-border service. Confirm base city, branches, priority routes, cargo restrictions, trip types, verified payloads and permit coverage. |
| D03 | Quotes and booking | A. Staff quote and confirm both services. B. Estimated fares for standard cabs with staff quotes for freight. C. Instant prices and confirmation for eligible services. Suggest A until rate rules and availability are verified. Ask about distance, tolls, timing, loading, waiting, discounts, and quote expiry. |
| D04 | Customer access and documents | A. Guest booking with private tracking links. B. Phone-OTP customer accounts. C. Both with business accounts if needed. Decide which documents customers get at launch, including booking acknowledgement, LR/consignment note, invoice, and proof of delivery. Confirm document samples, signatories, and attachment versus secure download. |
| D05 | WhatsApp and customer alerts | A. Click to chat with manual follow-up. B. Business Platform bot with lead inbox and human handoff. C. Website lead form with WhatsApp bot and both sources feeding the inbox. Suggest B or C for automated follow-up. Confirm existing business number, lead recipients, preferred message channel, languages, and which events warrant email, SMS, or WhatsApp. |
| D06 | Tracking and routing | A. Existing vehicle GPS provider integration. B. Driver phone location with background tracking tested on supported devices. C. Mixed providers behind a shared tracking interface. D. Milestone tracking at launch followed by a GPS pilot. Confirm provider, active fleet coverage, tracking frequency, customer visibility, and alert escalation. Evaluate a mobile driver app or hardware feed if reliable background tracking is required. |
| D07 | Customer fleet visibility | A. Vehicle classes with availability subject to dispatch confirmation. B. Date- and route-specific availability. C. Select a specific eligible vehicle. Suggest A until the scheduling inventory is reliable. Confirm maintenance lead time, substitute vehicle rules, and who can deactivate or archive vehicles. |
| D08 | Payments and finance | A. Staff record UPI, bank transfer, cash, or credit terms. B. Online deposit and manual balance. C. Full payment, refunds, and reconciliation in-app. Ask about GST invoicing and any accountant or Tally/Excel workflow. |
| D09 | Partner operations | A. Admin-managed partner records, terms, and email acknowledgements. B. Add partner portal for trips and settlement. C. Add vendor onboarding and self-managed availability. Suggest A first. Confirm settlement frequency, commercial bases, and who receives which document. |
| D10 | Driver and dispatch tools | A. Mobile web for assigned trips, status, and contact. B. Add location, offline recovery and delivery evidence. C. Dedicated driver app. Decide what drivers may see, who changes routes, and who handles after-hours alerts. Confirm whether messaging should be in-app or through a monitored business channel. |
| D11 | Languages and content | A. Four languages across public pages, booking, tracking, and key customer messages. B. Also localise driver screens and documents. C. Also localise the admin dashboard. Confirm exact public company name, approved contact channels, brand assets, content editors, and translation reviewers. |
| D12 | Business model and scale | A. Single company with branches and partner fleets. B. Single company now with an agreed path to multiple companies. C. Sell the software to independent transport companies at launch. Confirm budget, launch date, number of staff and vehicles, peak concurrent trips, monthly bookings, and growth forecast. |
| D13 | Service reliability | A. Business-hours operations. B. Extended dispatch with on-call incident alerts. C. 24/7 dispatch with defined response targets. Confirm acceptable downtime, recovery time, backup expectations, and retention for location, lead, trip, and finance records. |

Keep a decision register with ID, business question, options, recommendation, selected option, status, decision date, rationale, and requirements affected. Use statuses `Proposed`, `Confirmed`, `Deferred`, and `Superseded`. Maintain a version-controlled, shareable register containing approved non-sensitive choices. Store private contact data, contracts, live trip traces, and commercial rates only in an approved private location.

## 5. Run four reviews before drafting the design

1. **Business coverage.** Trace every owner request to a workflow, an interview decision, or an agreed later phase. Review one freight booking and one passenger booking end to end. Include a partner vehicle in at least one scenario.
2. **Product and usability.** Review the screens and responsibilities for customer, admin, dispatcher, driver, and finance or partner users if approved. Walk through mobile booking, quote follow-up, tracking, low connectivity, language switching, keyboard navigation, and relevant exception states. Check that each status label tells the user what happened and what action they can take.
3. **Technical and operational feasibility.** Review access rules, booking conflicts, notification reliability, dispatch and incident coverage, GPS feasibility, data and document handling, backups, and integrations. Verify provider limits and pricing. Model cost and load at launch, expected growth, and a peak scenario using stated assumptions.
4. **Release and acceptance.** Compare scope against budget and rollout dependencies. Check for missing decisions and turn major requirements into measurable acceptance criteria. Record each gap, owner, and resolution. Ask the owner to confirm the decision register and first release scope before drafting the final design.

## 6. Architecture to evaluate and document

- Compare a modular backend with a mobile-first frontend and versioned API contracts against alternatives warranted by the approved scope. Evaluate managed relational storage, private object storage for documents, and asynchronous workers for notifications, PDF generation, and tracking events. Keep booking, fleet, dispatch, partner finance, documents, and integration boundaries explicit. Use provider interfaces for maps, GPS, messaging, payments and document delivery.
- Keep business state consistent through atomic assignment and state changes, idempotency, a durable outbox or equivalent, bounded retries, and manual recovery for failed jobs. Isolate location ingestion from booking work. Separate latest vehicle position from historical traces. Replay delayed device events safely and distinguish recorded time from receipt time.
- Plan role-based access, scoped tracking links, signed downloads, audit trails, webhook verification, secret storage, encryption, data retention, and redacted logs. Confirm partner and tenant isolation if selling to separate companies becomes a requirement. Use synthetic data in demo and test environments.
- Define budgets for page load, API response, tracking update delay, notification delivery, concurrent bookings, and recovery. Estimate GPS updates from active vehicles and sample frequency, and estimate paid messaging, map requests, document storage, and hosting. State assumptions and cost drivers. Explain what metrics would justify scaling components independently.
- Include staging, deployment and rollback, schema migration, automated checks, observability, and backup restore verification. Define a phased launch and representative load and failure tests. Use the agreed first-release requirements to select the stack and providers.

## 7. Deliverables and approval gates

**Discovery prompt.** This file. Use it to run the research, interview and four review passes. Adjust phase recommendations when the owner's answers or provider evidence support a change.

**Decision register.** Keep accepted choices and deferred items traceable. Present the first release scope and unresolved dependencies to the owner for confirmation.

**Requirements and design document.** After the scope is confirmed, produce a document with service scope, original sitemap and screen inventory, role and permission matrix, workflow diagrams, status models, UI and accessibility guidelines, language plan, data model, API and integration boundaries, event and notification matrix, documents, observability and recovery plan, cost scenarios, delivery phases, and acceptance criteria. Cite the research used and identify assumptions separately from confirmed decisions.

Include acceptance scenarios for a freight booking, a family cab booking, a conflicting vehicle assignment, maintenance during scheduling, a trip-start acknowledgement, a received WhatsApp enquiry with a repeated webhook, a legitimate reroute, an unreviewed deviation, GPS loss, and a failed partner acknowledgement email. Cover unauthorised access to tracking and partner records and a full booking flow in each launch language.

**Development approval.** Present the requirements and design document for a separate owner approval before building the application. Once approved, build in reviewable increments, verify end-to-end workflows, and commit and push the approved project changes. The GitHub repository is public. Keep secrets, operational records, personal details, and confidential business inputs out of Git.
