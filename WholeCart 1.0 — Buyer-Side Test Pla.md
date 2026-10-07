**WholeCart 1.0 — Buyer-Side Test Plan**

**1. Objective**

Validate the complete Buyer journey of the WholeCart marketplace, ensuring that buyers can browse products, manage their cart, place and manage orders, and access invoices/statements accurately while all pricing, tax, inventory, delivery, authorization, and order-lifecycle business rules are correctly enforced.

**2. Scope**

In Scope – Buyer

\- Buyer login and session/access control

\- Product catalogue and search

\- Product details and unit selection

\- Add/update/remove cart items

\- Cart quantity validation

\- Multi-seller cart

\- Checkout and order placement

\- ₹2,000 minimum order per seller (CR-07)

\- Tax and delivery-fee calculation

\- Delivery date/slot selection

\- Slot availability, capacity and cutoff rules

\- Duplicate checkout prevention

\- Order history and order details

\- Order cancellation

\- Delivery-slot change

\- Failed-delivery/redelivery request

\- Reorder

\- Refund and exchange requests

\- Tax invoice validation

\- *CR-09 invoice requirements:*

&#x20; - Supply type: B2B

&#x20; - Place of supply: state name + state code derived from buyer GSTIN

\- Monthly statements

\- Buyer authorization/data isolation

\- UI validation and buyer-facing API behavior

\- Performance of search and checkout from the buyer perspective



**Out of Scope**

\- Seller UI/workflows

\- Operator UI/workflows

\- Seller product administration

\- Seller approval

\- Operator logistics/export functions

\- Inquiry attachments, as deferred by CR-11

\- Infrastructure/security attacks



3\. Test Approach

Area	Approach

Functional  --> Requirement-based + risk-based testing

UI	    --> End-to-end buyer journeys using Playwright/Manual

API	    --> Validate business rules, calculations, authorization and order state where exposed

Integration --> Validate buyer interactions across catalogue → cart → checkout → order → invoice

Data	    --> Boundary, negative, positive, equivalence and state-transition testing

Performance -->	Search and checkout against NF-01/NF-02, keeping traffic within the permitted limit

Regression  -->	Re-run critical buyer journeys after fixes





**4. High-Priority Buyer Areas**

P0 – Release/Business Critical

1\. Buyer authentication and authorization

2\. Product availability/out-of-stock behavior

3\. Cart quantity and price calculation

4\. Multi-seller checkout

5\. ₹2,000 minimum per seller

6\. Tax calculation and rounding

7\. Delivery-fee threshold

8\. Inventory/overselling protection

9\. Duplicate checkout/idempotency

10\. Order cancellation, including the exact 5-minute boundary

11\. Refund/exchange calculations

12\. Buyer order/invoice data isolation

13\. CR-09 tax invoice compliance



*P1 – Important*

\- Delivery-slot selection

\- Same-day cutoff

\- Slot capacity

\- Slot change

\- Failed delivery/redelivery

\- Reorder

\- Invoice details

\- Monthly statement calculation



**5. Entry Criteria**

\- Buyer account is active and login credentials are available.

\- Buyer catalogue/products are available.

\- Test data supports single- and multi-seller orders.

\- Required API endpoints are accessible/documented.

\- Release requirements and approved change requests are available.

\- Environment is stable enough to create and manage test orders.



**6. Exit Criteria**

\- All P0 buyer scenarios executed.

\- No open Critical/Blocker defects.

\- CR-07 and CR-09 requirements validated.

\- Pricing, tax, inventory and order totals verified.

\- Buyer data isolation validated.

\- Critical buyer regression suite passes.

\- Performance results for search/checkout are recorded.

\- All open defects and residual risks are documented.



**7. Key Risks**

&#x20;      Risk	                   Mitigation



\-Incorrect multi-seller  	  Test minimum independently for each seller

&#x20;minimum calculation



\-Incorrect tax/rounding	          Calculate expected values independently

\-Overselling	                  Concurrent buyer checkout

\-Duplicate orders        	  Repeat checkout submission

\-Incorrect cancellation boundary	  Test before, exactly at, and after 5 minutes

\-Financial discrepancy	          Compare cart → checkout → order → invoice → statement

\-Data leakage	                  Cross-buyer order/invoice/API access tests

\-CR-09 compliance failure       	  Dedicated invoice validation using buyer GSTIN

\-Slot timing defects	          Test cutoff, capacity and unavailable-slot states





**8. Release Recommendation**

Pass recommendation: Buyer-critical workflows, financial calculations, inventory integrity, authorization, and CR-07/CR-09 requirements must pass with no Critical/High release-blocking defects.

