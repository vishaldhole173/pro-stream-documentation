# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/file-invoice-dollar.svg" width="20" height="20"> Invoices

Invoices allow account holders to view a comprehensive list of invoices associated with their accounts.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

All the invoices are displayed in a table, providing users with essential details such as invoice numbers, customer email, payment status, remaining balance, due dates, and invoice creation dates.

## Invoice Number

* It displays a unique identifier assigned to each invoice.
* It helps quickly identify and reference specific invoices for further actions or inquiries.

## Customer

* It presents the identification of the customer associated with each invoice.
* This information allows to identify which user the invoice is related to, especially in scenarios where multiple users may be linked to the same account.

## Paid

* It indicates the amount paid by the customer for each invoice.
* It displays the cumulative payment made till now against the invoice.
* This information helps users track the progress of payment for each invoice.

## Left

* It represents the remaining balance on each invoice after deducting any payments made.
* It helps users quickly assess how much is left to be paid for each invoice.

## Due

* It displays the due date for each invoice, indicating the deadline by which the payment should be made.
* This information helps users prioritize their payments and avoid late fees or penalties.

## open or paid badge

* It indicates the payment status of each invoice.
* The ‘paid’ badge is shown When the invoice has been fully paid.
* In case of unpaid or partially paid invoices, the 'open' badge is shown.

## Created

* It shows the date and time when each invoice was created.
* It provides users with a reference point for tracking the age of the invoice and helps in identifying the order of invoice creation when multiple invoices are present.

**When a user clicks on the corresponding invoice number Invoice Details page is shown with a detailed view of a specific invoice**

## Invoice Details

* This page presents comprehensive information about the invoice, including billing details, customer information, payment status, and a detailed overview of the amount charged for each service used.
* If there is any amount left to be paid for the invoice, users are provided with an option to make a payment.
* By clicking on the payment option, users are presented with a payment form where they can enter their card details to complete the payment process.
* Once the payment is successfully processed, the invoice payment status is updated accordingly.

## Making Payment

* The payment form prompts the user to enter their card details, including the card number, CVV (Card Verification Value), and zip code.
* The user submits the payment form, which securely transmits the entered payment information to the Stripe payment gateway.
* Stripe validates the payment information and processes the payment using the associated payment card.
* Upon successful payment processing, the invoice payment status is updated to reflect the payment received.
* Once the payment is successfully processed, the application generates an invoice PDF and sends it to the account owner's email address.
* This ensures a smooth payment experience and provides users with a digital copy of their invoice for record-keeping and reference purposes.
