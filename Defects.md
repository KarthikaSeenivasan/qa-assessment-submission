**Case 1 — Multiple Catalogue Filters Not Working**



**Description:**

The Catalogue filtering functionality does not work as expected when two filters are applied at the same time.



**Steps to Reproduce:**

\-Navigate to the Catalogue page.

\-Select any value from the first filter.

\-Select a value from a second filter.



**Expected Result:**

The catalogue should apply both filters simultaneously and display products matching the selected criteria.



**Actual Result:**

The search/filter functionality does not work correctly when two filters are selected simultaneously.



*Severity:* Medium

*Priority*: High



**Case 2 — No Explicit Delete Option in Cart**



**Description**:

The Cart screen does not provide a dedicated delete/remove option for an individual item. The user must manually reduce the item quantity to zero to remove it from the cart.



**Steps to Reproduce:**



\-Add a product to the cart.

\-Navigate to the Cart screen.

\-Locate the added product.

\-Look for an option to remove/delete the product.



**Expected Result:**

Each cart item should have an explicit Remove/Delete option so the user can easily remove the item from the cart.



**Actual Result:**

No explicit Remove/Delete option is available. The user has to decrease the quantity to 0 to remove the item.



Severity: Medium

Priority: Medium



**Case 3 — Incorrect Stock Validation During Checkout**



**Description:**

The checkout process fails when ordering Chef's Cardamom even though the product shows 105 pieces available in stock.



**Steps to Reproduce:**



\-Navigate to the Catalogue.

\-Search for Chef's Cardamom.

\-Verify that the product has 105 pieces in stock.

\-Add the product to the cart.

\-Proceed to checkout.

\-Observe the stock validation message.



**Expected Result:**

If the requested quantity is within the available stock of 105 pieces, the user should be allowed to proceed with checkout.



**Actual Result:**

Checkout is blocked and the system displays an incorrect error message indicating:

"Only -105 pieces of Chef's Cardamom in stock."



Severity: High

Priority: High



**Case 4 — Incorrect Delivery Date in Change Delivery Slot**



**Description:**

The Change Delivery Slot option on the Order screen displays the current date even when the order was originally booked for a different delivery date.



**Steps to Reproduce:**



\-Place an order and select a delivery date different from the current date.

\-Complete the order successfully.

\-Navigate to the Order screen.

\-Select Change Delivery Slot.

\-Observe the displayed delivery date.



**Expected Result:**

The Change Delivery Slot screen should display the originally selected/booked delivery date and the available slots associated with that date.



**Actual Result:**

The Change Delivery Slot option displays the current date instead of the date selected during the original order.



Severity: Medium

Priority: High



**Case 5 — Minimum Order Value Not Enforced**



**Description:**

The system allows users to place an order below the configured minimum order value of ₹2,000 net per seller.



**Steps to Reproduce:**



\-Add products from a seller to the cart.

\-Ensure the net order value for that seller is less than ₹2,000.

\-Proceed to checkout.

\-Attempt to place the order.



**Expected Result:**

The system should prevent the user from placing the order when the seller-specific net order value is below ₹2,000 and should display an appropriate validation message.



**Actual Result:**

The system allows the user to proceed with checkout and place an order even when the seller-specific net order value is less than ₹2,000.



Severity: High

Priority: High



**Case 6 — Supply Type Missing from Tax Invoice**



**Description:**

The generated Tax Invoice does not include the Supply Type information.



**Steps to Reproduce:**



\-Place an order successfully.

\-Navigate to the Order or Invoice section.

\-Open/download the Tax Invoice.

\-Review the invoice details.

\-Check for the Supply Type field.



**Expected Result:**

The Tax Invoice should display the applicable Supply Type along with the other required invoice details.



**Actual Result:**

The Supply Type field is not present in the generated Tax Invoice.



Severity: Medium

Priority: High

