# Standard Bug Report Document – WholeCart Marketplace

The following 23 unique bug reports are structured for QA assessment, with **Description, Steps to Reproduce, Expected Result, Actual Result, and Priority**.

**Priority definitions:** P1 – High business impact; P2 – Major functional issue; P3 – Moderate issue.

\---

## Bug 1: Multiple catalogue filters are not working

* **Description:** Applying multiple filters simultaneously in the product catalogue does not return the expected results.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to the product catalogue.
  3. Apply one filter, such as category.
  4. Apply another filter, such as price or availability.
  5. Observe the displayed products.
* **Expected result:** The catalogue should display products matching all selected filter criteria.
* **Actual result:** Multiple filters do not work as expected, and the displayed products do not match the combined criteria.
* **Priority:** P2 – Major

## Bug 2: Out-of-stock products are displayed in the catalogue

* **Description:** Products with zero available stock are still displayed in the buyer's product catalogue.
* **Steps to reproduce:**

  1. Log in as a seller.
  2. Set a product's stock quantity to zero.
  3. Save the product.
  4. Log in as a buyer.
  5. Navigate to the catalogue and search for the product.
* **Expected result:** Out-of-stock products should either be excluded from available products or clearly marked as unavailable, according to the business requirements.
* **Actual result:** The out-of-stock product continues to appear in the catalogue without appropriate availability handling.
* **Priority:** P1 – High

## Bug 3: Same-day delivery is unavailable before the 10:00 AM cutoff

* **Description:** The buyer cannot place an order for same-day delivery even when attempting checkout before the configured 10:00 AM cutoff.
* **Steps to reproduce:**

  1. Log in as a buyer before 10:00 AM.
  2. Add an eligible product to the cart.
  3. Select same-day delivery.
  4. Proceed to checkout.
  5. Submit the order.
* **Expected result:** The order should be accepted for same-day delivery if it meets the cutoff time and all other eligibility conditions.
* **Actual result:** The application does not allow the order to be placed for same-day delivery despite the request being made before 10:00 AM.
* **Priority:** P1 – High

## Bug 4: Duplicate orders are created on repeated checkout submission

* **Description:** Submitting the same checkout request twice, such as by double-clicking the Place Order button, creates duplicate orders.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Add products to the cart.
  3. Complete the checkout details.
  4. Double-click the Place Order button or submit the same request twice quickly.
  5. Navigate to the order history.
* **Expected result:** Only one order should be created for a single checkout transaction. Duplicate submissions should be prevented by frontend controls and backend idempotency.
* **Actual result:** Multiple orders are created from the same checkout submission.
* **Priority:** P1 – High

## Bug 5: HTTP 500 Internal Server Error occurs during checkout

* **Description:** The application returns an HTTP 500 Internal Server Error when the buyer clicks the checkout button.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Add an eligible product to the cart.
  3. Navigate to checkout.
  4. Complete the required checkout fields.
  5. Click the Checkout or Place Order button.
  6. Observe the application response and browser Network tab.
* **Expected result:** The checkout request should complete successfully and proceed to order confirmation, or display a meaningful validation message if the request cannot be processed.
* **Actual result:** The application returns an HTTP 500 Internal Server Error when checkout is initiated.
* **Priority:** P1 – High

## Bug 6: Message Seller functionality is not working

* **Description:** The Message Seller option does not allow the buyer to communicate with the seller.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to the catalogue or relevant product/order page.
  3. Click Message Seller.
  4. Attempt to open the conversation or send a message.
* **Expected result:** The messaging interface should open, and the buyer should be able to send a message to the relevant seller.
* **Actual result:** The Message Seller option does not work as expected.
* **Priority:** P2 – Major

## Bug 7: Redelivery request accepts a past date

* **Description:** The buyer can select and submit a redelivery request for a date in the past.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to an eligible order.
  3. Click Request Redelivery.
  4. Open the delivery-date selector.
  5. Select a past date.
  6. Submit the request.
* **Expected result:** Past delivery dates should be disabled or rejected during validation. Only dates permitted by the delivery rules should be accepted.
* **Actual result:** The application allows a redelivery request for a past date.
* **Priority:** P2 – Major

## Bug 8: Incorrect eligibility message appears when requesting a refund or exchange after cancellation

* **Description:** After an order is cancelled, attempting to initiate a refund or exchange displays the message: “Refunds and exchanges are only available for delivered orders.”
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Place an order and cancel it.
  3. Navigate to the cancelled order.
  4. Attempt to initiate a refund or exchange.
  5. Observe the displayed message.
* **Expected result:** The application should prevent refund/exchange requests for cancelled orders and display an appropriate message explaining that the order was cancelled and is not eligible.
* **Actual result:** The application displays the delivered-order eligibility message instead of a cancellation-specific message.
* **Priority:** P2 – Major

## Bug 9: Refund is credited for an exchange transaction

* **Description:** The application credits a refund amount to the buyer even though the transaction is an exchange intended to provide replacement goods.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to an eligible delivered order.
  3. Submit an exchange request for a product.
  4. Get the exchange request approved.
  5. Complete or observe the exchange processing workflow.
  6. Check the buyer's refund balance or transaction history.
* **Expected result:** The exchange should process replacement goods without issuing a monetary refund, unless a separate refund is explicitly approved under the business rules.
* **Actual result:** A refund amount is credited to the buyer even though the request is processed as an exchange.
* **Priority:** P1 – High

## Bug 10: Repeated partial refund requests are allowed for the same product

* **Description:** The application allows another partial refund request for a product after a partial refund has already been approved and processed.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to an eligible delivered order.
  3. Submit a partial refund request for a product.
  4. Get the refund approved and processed.
  5. Submit another partial refund request for the same product.
* **Expected result:** The application should calculate the remaining refundable amount and prevent refund requests that exceed the eligible balance.
* **Actual result:** The application allows another partial refund request for the same product without correctly restricting the previously refunded amount.
* **Priority:** P1 – High

## Bug 11: Partial refund is allowed after a full refund

* **Description:** The buyer can submit a partial refund request for a product after the full refundable amount has already been refunded.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Navigate to an eligible delivered order.
  3. Submit a full refund request for a product.
  4. Get the full refund approved and processed.
  5. Attempt to submit a partial refund request for the same product.
* **Expected result:** Once the full refundable amount has been refunded, the remaining refundable balance should be zero, and additional refund requests should be rejected.
* **Actual result:** The application allows a partial refund request after a full refund has been processed.
* **Priority:** P1 – High

## Bug 12: Seller GST information is missing from the tax invoice

* **Description:** The generated tax invoice does not contain the seller's required GST information.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Place and complete an eligible order.
  3. Generate or download the tax invoice.
  4. Review the seller's tax information.
* **Expected result:** The tax invoice should display the seller's required GST details as specified by the invoice requirements.
* **Actual result:** The seller's GST information is missing from the generated tax invoice.
* **Priority:** P1 – High

## Bug 13: Delivery fee information is missing from the tax invoice

* **Description:** The generated tax invoice does not display the delivery fee charged for the order.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Place an order for which a delivery fee applies.
  3. Complete the order.
  4. Generate or download the tax invoice.
  5. Review the charges listed on the invoice.
* **Expected result:** The invoice should display the applicable delivery fee and the required tax breakdown.
* **Actual result:** The delivery fee information is missing from the generated tax invoice.
* **Priority:** P1 – High

## Bug 14: Supply Type information is missing from the tax invoice

* **Description:** The generated tax invoice does not include the Supply Type information required by the business requirements.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Place and complete an eligible order.
  3. Generate or download the tax invoice.
  4. Review the invoice fields.
* **Expected result:** The invoice should display the appropriate Supply Type information according to the invoice requirements.
* **Actual result:** Supply Type information is missing from the generated tax invoice.
* **Priority:** P1 – High

## Bug 15: Monthly statement includes cancelled orders (BR-20 violation)

* **Description:** The buyer's monthly statement includes cancelled orders, violating business requirement BR-20.
* **Steps to reproduce:**

  1. Log in as a buyer.
  2. Place an order during a given month.
  3. Cancel the order.
  4. Navigate to the monthly statement for that month.
  5. Review the listed transactions.
* **Expected result:** As per BR-20, the monthly statement should list orders delivered during that month, minus approved refunds. Cancelled orders must not be included.
* **Actual result:** Cancelled orders are included in the monthly statement.
* **Priority:** P1 – High

## Bug 16: Pagination displays the Next option when no additional page exists

* **Description:** The application displays the Next pagination option even when the result set does not contain another page.
* **Steps to reproduce:**

  1. Navigate to the relevant list or table view.
  2. Load a dataset that fits on a single page.
  3. Review the pagination controls.
  4. Check whether Next is enabled or displayed.
* **Expected result:** The Next option should be hidden or disabled when there are no additional pages.
* **Actual result:** The Next option is displayed even though no additional page is available.
* **Priority:** P3 – Moderate

## Bug 17: Seller-side order cancellation is not reflected in the buyer's order status

* **Description:** When the seller cancels an order, the buyer's order status remains “Placed” instead of updating to “Cancelled.”
* **Steps to reproduce:**

  1. Log in as a buyer and place an order.
  2. Log in as the seller associated with that order.
  3. Cancel the order from the seller's order management page.
  4. Log back in as the buyer.
  5. Navigate to the order tab and check the status.
* **Expected result:** The buyer's order status should update to “Cancelled” after the seller cancels the order.
* **Actual result:** The buyer's order status remains “Placed.”
* **Priority:** P1 – High

## Bug 18: CSV import does not trim leading and trailing whitespace

* **Description:** The seller CSV import process does not consistently trim leading and trailing whitespace before validation and database insertion, potentially causing duplicate or inconsistent records.
* **Steps to reproduce:**

  1. Log in as a seller.
  2. Prepare a CSV file containing values with leading or trailing spaces.
  3. Include a value that matches an existing record except for the extra whitespace.
  4. Import the CSV file.
  5. Review the validation results and imported records.
* **Expected result:** Leading and trailing whitespace should be removed before validation and insertion. Duplicate checks should use the normalized values.
* **Actual result:** Values with extra whitespace are processed without the expected normalization, potentially resulting in inconsistent or duplicate records.
* **Priority:** P2 – Major

## Bug 19: Numeric configuration fields accept special characters

* **Description:** The admin configuration page allows special characters or invalid non-numeric values in fields intended to accept numeric values.
* **Steps to reproduce:**

  1. Log in as an administrator.
  2. Navigate to the configuration settings page.
  3. Enter special characters or invalid non-numeric values in the following fields:

     * Cancellation window (minutes)
     * Orders per delivery slot
     * Minimum order per seller (₹)
     * Free delivery from (₹)
     * Delivery fee (₹, before tax)
  4. Click Save.
  5. Check the validation messages and saved values.
* **Expected result:** Each field should enforce the appropriate numeric type, range, and business constraints. Invalid values should be rejected with a clear validation message and should not be saved.
* **Actual result:** The fields accept special characters instead of enforcing the expected numeric validation.
* **Priority:** P1 – High if invalid values affect checkout, pricing, or delivery calculations; otherwise P2 – Major.

## Bug 20: Browser console error occurs when saving admin configuration

* **Description:** A JavaScript console error occurs when the administrator clicks Save on the configuration settings page.
* **Steps to reproduce:**

  1. Log in as an administrator.
  2. Navigate to the configuration settings page.
  3. Open browser developer tools and select the Console tab.
  4. Modify a configuration field with valid input.
  5. Click Save.
  6. Review the console output and verify whether the changes are persisted.
* **Expected result:** The application should save valid settings successfully without unexpected JavaScript errors and display a clear success or failure message.
* **Actual result:** A console error occurs when Save is clicked. Whether the settings are saved successfully requires verification.
* **Priority:** P2 – Major, pending confirmation of functional impact.

\---

## Bug 21: No explicit delete option in the cart

* **Description:** The Cart screen does not provide a dedicated delete/remove option for an individual item. The user must manually reduce the item quantity to zero to remove it from the cart.
* **Steps to reproduce:**

  1. Add a product to the cart.
  2. Navigate to the Cart screen.
  3. Locate the added product.
  4. Look for an option to remove or delete the product.
* **Expected result:** Each cart item should have an explicit Remove/Delete option so the user can easily remove the item from the cart.
* **Actual result:** No explicit Remove/Delete option is available. The user has to decrease the quantity to zero to remove the item.
* **Severity:** Medium.
* **Priority:** P2 – Major

## Bug 22: Incorrect stock validation during checkout

* **Description:** The checkout process fails when ordering Chef's Cardamom even though the product shows 105 pieces available in stock.
* **Steps to reproduce:**

  1. Navigate to the Catalogue.
  2. Search for Chef's Cardamom.
  3. Verify that the product has 105 pieces in stock.
  4. Add the product to the cart.
  5. Proceed to checkout.
  6. Observe the stock validation message.
* **Expected result:** If the requested quantity is within the available stock of 105 pieces, the user should be allowed to proceed with checkout.
* **Actual result:** Checkout is blocked and the system displays an incorrect error message: “Only -105 pieces of Chef's Cardamom in stock.”
* **Severity:** High.
* **Priority:** P1 – High

## Bug 23: Incorrect delivery date displayed in Change Delivery Slot

* **Description:** The Change Delivery Slot option on the Order screen displays the current date even when the order was originally booked for a different delivery date.
* **Steps to reproduce:**

  1. Place an order and select a delivery date different from the current date.
  2. Complete the order successfully.
  3. Navigate to the Order screen.
  4. Select Change Delivery Slot.
  5. Observe the displayed delivery date.
* **Expected result:** The Change Delivery Slot screen should display the originally selected/booked delivery date and the available slots associated with that date.
* **Actual result:** The Change Delivery Slot option displays the current date instead of the date selected during the original order.
* **Severity:** Medium.
* **Priority:** P2 – Major (confirm based on delivery impact).

## Summary of reported defects

|Priority|Count|Main concerns|
|-|-:|-|
|P1 – High|14|Checkout, duplicate orders, refunds, invoices, stock, order status and financial correctness|
|P2 – Major|8|Filters, messaging, redelivery, cart removal, delivery-slot date, CSV normalization and validation|
|P3 – Moderate|1|Pagination|
|**Total**|**23**|**Unique bug reports**|



