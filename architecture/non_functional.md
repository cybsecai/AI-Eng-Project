# Non-Functional Requirements (NFR) Specification
## Telemetry Thresholds & Compliance Enforcements

The architecture enforces strict quantitative guardrails to guarantee operational resilience, universal accessibility, cryptographic data protection, and predictable user latencies[cite: 54, 55].

| NFR Reference ID | Quality Attribute Class | Target Quantitative Metric | Maximum Allowed Constraint Bound | Telemetry Validation Protocol |
| :--- | :--- | :--- | :--- | :--- |
| **NFR1** | Operational Availability | Active runtime availability of $A \ge 99.5\%$ inside core operational hours (07:00:00 to 22:00:00 local time)[cite: 95, 97]. | Maximum unplanned downtime is strictly capped at 135 minutes per rolling 30-day calendar cycle[cite: 99]. Infrastructure maintenance must execute between 01:00:00 and 04:00:00 GMT/BST[cite: 100]. | Automated external synthetic monitoring nodes executing HTTP GET ping hooks at 60-second intervals from three distinct geo-distributed Edge locations[cite: 101]. |
| **NFR2** | Performance Latency | P95 page asset load $\le 3.0$ seconds on initial viewport boot; P95 dynamic filter and search query execution $\le 1.0$ second[cite: 103, 106, 107]. | Total transferred initial page asset bundle weight is restricted to $\le 1.85$ MB[cite: 108, 109]. Static assets must serve from geographic CDN nodes with TTL cache settings $\ge$ 7 days[cite: 110]. | Continuous client-side instrumentation via OpenTelemetry wrappers capturing Largest Contentful Paint (LCP) and Interaction to Next Paint (INP)[cite: 111]. |
| **NFR3** | Portability / Interface Responsiveness | Seamless interface rendering down to exactly 360px layout widths; administrative dashboard layouts explicitly locked to 1024px x 768px viewports[cite: 112, 114, 115, 116]. | All interactive touch components must maintain minimum structural tap targets of $\ge 44 \times 44$px with surrounding physical isolation margins $\ge 8$px[cite: 117]. | Automated visual regression tracking engines utilizing headless browser instances executing on every delivery integration pipeline[cite: 118]. |
| **NFR4** | Accessibility Compliance | Strict interface conformity to the global Web Content Accessibility Guidelines (WCAG) 2.2 Level AA standardization[cite: 119, 121]. | Contrast ratios for body text strings must maintain $C \ge 4.5:1$ against backgrounds; large headers $\ge 24$px must maintain $C \ge 3.0:1$[cite: 122, 123]. Interactive components must feature $\ge 2$px focus outlines[cite: 124]. | Programmatic accessibility audit engines executing within CI/CD build blocks, supplemented by manual screen-reader and keyboard-only entry test validations[cite: 125]. |
| **NFR5** | System Security & Authentication | Mandatory TLS 1.3 encrypted transport rules across all data pipelines. Credentials must undergo security hashing via salted Argon2id profiles[cite: 126, 129, 130]. | Active administrative sessions (JSON Web Tokens in memory) must automatically expire and clear from memory after exactly 1,800 seconds of absolute operator inactivity[cite: 131, 132]. | Automated weekly OWASP vulnerabilities scanning loops coupled with active audit log parsing tracking authentication token invalidations[cite: 134]. |
| **NFR6** | Regulatory Data Privacy | Structurally automated data workflows executing complete PII export or deletion sequences within a hard limit of $\le 30.0$ calendar days[cite: 135, 137]. | Marketing data capture points must default to a strict unselected opt-out configuration[cite: 138, 139]. Relational database columns containing PII data must utilize AES-GCM-256 encryption[cite: 140]. | Automated hourly server scripts executing pattern matching routines to locate and flag unencrypted PII blocks within relational database layers[cite: 141]. |
| **NFR7** | Concurrency Control & State Integrity | Master database inventory revisions must synchronize, validate, and propagate down to client layouts within a latency window of $\le 30.0$ seconds[cite: 142, 144]. | Database storage engines must implement strict transaction isolation layers (Serializable level) to eliminate multi-user race conditions up to 500 concurrent checkout attempts[cite: 145]. | Programmatic concurrent load execution suites running load scripts during release engineering cycles to measure product cache lookups[cite: 146]. |
| **NFR8** | Business Resilience & Continuity | Recovery Point Objective (RPO) bounded at $\le 15.0$ minutes; Recovery Time Objective (RTO) for core records recovery bounded at $\le 4.0$ hours[cite: 147, 150, 151]. | Complete encrypted database state snapshots must generate automatically once every 24 hours at 02:00:00 UTC, transferring data blocks to decoupled physical storage[cite: 152]. | Mandatory quarterly disaster recovery simulation events executing automated script routines to measure restore duration and completeness benchmarks[cite: 153]. |
| **NFR9** | Administrative Usability | Trained operators must successfully isolate any anomalous data block flagged as delayed within a maximum lookup time of $\le 30.0$ seconds[cite: 154, 156]. | Core management operations (routing edits, status adjustments, inventory alterations) must require no more than exactly 3 sequential interaction steps[cite: 157]. | In-app event instrumentation logs capturing administrative cursor movements, navigation button counts, and interaction process times[cite: 158]. |
| **NFR10** | Support AI Intelligence | Conversational automated UI layers must return natural language text responses within a processing speed cap of $\le 5.0$ seconds[cite: 159, 161]. | Hard validation guardrails must prevent the engine from processing arbitrary pricing models[cite: 162, 163]. The system must execute a live support handover if confidence targets drop below 70%[cite: 164]. | Production pipeline analytics tracking query sub-second latencies, intent tracking precisions, and boundary exception flags[cite: 165]. |


**Detailed Non Functionl Requirements**:
Quantifiable Non-Functional Requirements and System Constraints

NFR1 — System Availability & Operational Reliability
    • Quality Attribute Class: Operational Availability / Service Reliability.
    • Target Metric: The public e-commerce platform shall maintain an active runtime availability of A ≥ 99.5% within the core operational hours of 07:00:00 to 22:00:00 local time (GMT/BST) over any rolling 30-day calendar cycle.
    • System Constraints & Execution Bounds:
        ◦ Maximum allowable unplanned downtime during the core window is exactly 135 minutes per calendar month.
        ◦ Scheduled infrastructure maintenance, migrations, and database schema updates must execute strictly within the low-traffic window of 01:00:00 to 04:00:00 GMT/BST and shall not exceed an aggregate of 240 minutes per calendar year.
    • Verifiable Telemetry Protocol: Verified via automated external synthetic monitors executing HTTP GET ping hooks at 60-second intervals from three distinct geo-distributed Edge nodes. Downtime is logged if at least two nodes report an HTTP status code S>400 or connection timeout T>10.0 seconds for three consecutive checks.

NFR2 — Core Transactional & Interface Page Latency Targets
    • Quality Attribute Class: Efficiency / Performance Characteristics.
    • Target Metric: Page loading performance must meet the following percentile boundaries under a simulated throttled mobile network profile (defined as a standard 4G connection of 1.6 Mbps down, 750 kbps up, and 150 milliseconds round-trip time [RTT]):
        ◦ P95 Page Load Latency: ≤ 3.0 seconds for the homepage, product catalog listing page, product detail page, and checkout path on initial mobile viewport boot.
        ◦ P95 Dynamic Filtering & Search Update Latency: ≤ 1.0 seconds from the physical client touch/click input event trigger to complete rendering of filtered product matrices on screen.
    • System Constraints & Execution Bounds:
        ◦ Maximum initial page asset payload budget is restricted to ≤ 1.85 MB of total transferred bundle weight.
        ◦ All static assets (including greyscale wireframe product images, icons, and fonts) must be served from an optimized geographic Content Delivery Network (CDN) with caching TTL set to ≥ 604,800 seconds (7 days).
    • Verifiable Telemetry Protocol: Continuous client-side performance auditing tracked via OpenTelemetry wrappers capturing Google Web Vitals (specifically focusing on Largest Contentful Paint [LCP] and Interaction to Next Paint [INP]) transmitted to the centralized server monitoring dashboard.

NFR3 — Layout Responsiveness & Bounding Viewport Constraints
    • Quality Attribute Class: Portability / Layout Adaptability.
    • Target Metric: The client-facing and admin interfaces must render cleanly across geo-diverse hardware targets under strict CSS breakpoint boundaries:
        ◦ Client Mobile Web Viewports: Must fit smoothly within viewports down to exactly 360px width without generating any horizontal scrollbars or displaying truncated text blocks.
        ◦ Store Admin iPad Interface: Must display and operate cleanly on a generic iPad tablet frame (viewport dimension constraints of exactly 1024px x 768px in landscape and portrait orientation) without interface wrap collapse.
    • System Constraints & Execution Bounds: All touch-interactive components (buttons, dropdowns, input elements) must feature a minimum physical tap target dimension profile of ≥ 44 x 44px with surrounding safety margins of ≥ 8px.
    • Verifiable Telemetry Protocol: Evaluated through automated visual regression testing using headless browser containers capturing mobile and tablet snapshots during every pull request deployment pipeline.

NFR4 — Universal Digital Interface Accessibility Compliance
    • Quality Attribute Class: Accessibility / Universal Usability.
    • Target Metric: The web platform's customer and administrative portals must conform strictly to the Web Content Accessibility Guidelines (WCAG) 2.2 Level AA standard.
    • System Constraints & Execution Bounds:
        ◦ Contrast Bound: Normal body typography text strings against background elements must have a colour contrast ratio C ≥ 4.5:1, and large headers (larger than 24px) must possess a contrast ratio C ≥ 3.0:1.
        ◦ Focus Ring Bound: Active focus styles on interactive components must render a highly visible border stroke (≥ 2px thickness, solid configuration, contrast ratio of at least 3.0:1 against the element) when indexed via step-wise keyboard controls.
    • Verifiable Telemetry Protocol: Automated accessibility auditing engines integrated directly into the CI/CD test block runner, backed by weekly manual test scripts executed using screen readers and key-only input sequences.

NFR5 — System Security, Token Architecture, & Role-Based Access Control (RBAC)
    • Quality Attribute Class: Security / Cryptographic Data Protection / Authorisation.
    • Target Metric: Secure operations must be governed by cryptographically signed authorisation tokens and strict session limits:
        ◦ All administrative database access pipelines must go through TLS 1.3 encrypted transport rules.
        ◦ User passwords stored in the system database must be hashed using a cryptographically secure, salted hashing algorithm such as Argon2id.
    • System Constraints & Execution Bounds:
        ◦ Active administrative sessions (JSON Web Tokens [JWT] held in memory) must automatically expire, step-down, and clear after exactly 1,800 seconds of absolute operator inactivity.
        ◦ The administrative routing block must intercept and block any unauthorised web requests aimed at endpoints matching /admin/* paths, throwing a strict 403 Forbidden status code.
    • Verifiable Telemetry Protocol: Monitored via weekly OWASP automated compliance scanners and active audit logs tracking token invalidation occurrences on the authentication controller layers.

NFR6 — General Data Protection Regulation (GDPR) Compliance
    • Quality Attribute Class: Regulatory Privacy / Personal Data Protection.
    • Target Metric: Full structural workflow automation to execute PII (Personally Identifiable Information) export or permanent erasure request loops within a hard calendar limit of ≤ 30.0 days of user transaction validation.
    • System Constraints & Execution Bounds:
        ◦ Initial registration flows must have marketing sign-up option toggles set to "opt-out" (deselected) by default.
        ◦ PII database columns containing billing records, recipient details, and exact shipping street coordinates must undergo dynamic anonymisation, or be securely encrypted using AES-GCM-256 keys.
    • Verifiable Telemetry Protocol: Programmatic security scripts running hourly checks to locate and alert on unencrypted PII database blocks, coupled with automated deletion queue audits verifying the erasure timeline.

NFR7 — Live Inventory Cache Synchronicity & Transactional ACID Concurrency Integrity
    • Quality Attribute Class: Concurrency / System Synchronicity / Data Integrity.
    • Target Metric: Modification entries recorded inside Lily's administrative database master repository must synchronize, validate, and propagate down to client catalog pages within a maximum latency window of ≤ 30.0 seconds.
    • System Constraints & Execution Bounds: The underlying inventory controller must implement strict transaction isolation blocks (Serializable level), completely preventing multi-user race conditions from dropping available item stock counts below zero under a high concurrency test baseline of up to 500 concurrent checkout attempts.
    • Verifiable Telemetry Protocol: Programmatic load execution testing simulating transaction checkout waves under concurrent connection limits while measuring product lookup synchronicity rates on CDN endpoints.

NFR8 — Automated Data Backups & Disaster Recovery Protocols
    • Quality Attribute Class: System Resiliency / Disaster Avoidance / Business Continuity.
    • Target Metric: Restorations from backup storage states must align with strict continuity limits:
        ◦ Recovery Point Objective (RPO): The maximum allowable data loss window must be bounded at ≤ 15.0 minutes.
        ◦ Recovery Time Objective (RTO): Total structural restoration of core transaction registries and inventory records to functional, online operation must finish within ≤ 4.0 hours of server outage events.
    • System Constraints & Execution Bounds: Complete database system state snapshots must generate automatically once every 24 hours at 02:00:00 UTC, transmitting encrypted data blocks directly to decoupled physical cloud storage environments.
    • Verifiable Telemetry Protocol: Mandatory quarterly disaster recovery simulation drills executing automated recovery scripts to measure backup completeness and validation time benchmarks.

NFR9 — Administrative Usability & Order Resolution Latency
    • Quality Attribute Class: Usability / Operational Task Efficiency.
    • Target Metric: A trained store administrator using an iPad interface must be capable of locating any single order flagged as delayed within a maximum elapsed lookup time of ≤ 30.0 seconds on initial canvas visual display.
    • System Constraints & Execution Bounds: Executing standard order management operations (including updating delivery routing status, adding internal driver notes, or initiating inventory changes) must require no more than exactly 3 sequential tap interactions on an iPad tablet surface.
    • Verifiable Telemetry Protocol: In-app instrumentation capturing operator navigation click paths, counting every button event loop, and measuring active user interaction time limits during fulfilment phases.

NFR10 — Conversational AI Engine Guardrails & Latency Metrics
    • Quality Attribute Class: Support Automation / Conversational Interface Logic.
    • Target Metric: The virtual chatbot assistant UI block must initiate a contextually valid, natural language text response return sequence within a processing limit of ≤ 5.0 seconds for at least 95% of all typical user queries.
    • System Constraints & Execution Bounds:
        ◦ The system must implement hard validation guardrail blocks that automatedally prevent the assistant from pledging specific pricing models or shipping slots unless validated by real-time inventory queries.
        ◦ The chatbot system must instantly execute a graceful handover routing to Lily's mobile support channel whenever the automated intent confidence rating drops under 70% for two consecutive user turns.
    • Verifiable Telemetry Protocol: Automated pipeline log metrics monitoring exact message sub-second latency intervals, intent extraction precision rates, and automated boundary protection exceptions.
