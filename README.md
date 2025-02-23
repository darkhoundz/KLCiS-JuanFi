# KLCiS Voucher System (Embedded E-Payment) Hotspot Template for JuanFi v4.3

JuanFi is an open-source system for coinslot integration with Mikrotik Hotspot, developed by [Ivan Julius Alayan](https://github.com/ivanalayan15/JuanFi).

With the integration of the **KLCiS Voucher System**, JuanFi-operated machines can accept e-payments (Gcash, PayMaya, GrabPay, ShopeePay). Voucher codes are automatically generated after a successful payment, with SMS notifications for added convenience.

More details at [klinternetservices.com](https://klinternetservices.com).

![Control Panel Screenshot](https://github.com/darkhoundz/KLCiS-JuanFi/assets/28075740/3eb6e819-f966-41dc-a2b9-8bdcfd2d6ec5)

---

## I. Requirements

1. **KLCiS Voucher System account:** Create an account at [klinternetservices.com](https://klinternetservices.com).
2. **Voucher codes in CSV format:** Ensure each voucher corresponds to a specific amount. [Tutorial on using Mikhmon as a voucher generator](https://youtu.be/dnQ8RlyxbKE?t=1246).

---

## II. Installation

1. **Download the template:** Upload it to the Mikrotik hotspot directory.
2. **Edit `login.html`:**
    - Locate:
      ```html
      <select class="form-control" id="amountDropdown" name="amount" style="width:100%; font-size:16px; font-weight:500; color:green;">
          <option value="5">₱5.00 - 1 HOUR UNLIMITED</option>
          <option value="10">₱10.00 - 1 DAY UNLIMITED</option>
          <option value="100">₱100.00 - 7 DAYS UNLIMITED</option>
          <option value="300">₱300.00 - 30 DAYS UNLIMITED</option>
      </select>
      ```
      Edit the options to match the voucher codes in your KLCiS account.
      
    - Locate:
      ```html
      <input type="hidden" class="form-control" id="tokenInput" name="token" value="PUT_YOUR_KLCIS_API_KEY_HERE">
      ```
      Add your **KLCiS API Key**.

3. **Test KLCiS API Key:** Select a promo, enter an active number, and click "BUY NOW". Ensure you have an internet connection during testing.
4. **Check transactions:** Log in to your KLCiS account, navigate to **Transactions**, and verify that you see an "UNPAID" status for the test transaction.

---

## III. Walled Garden Setup

Allow clients to purchase voucher codes without session/internet load. Use the following Walled Garden script in the Mikrotik Terminal:

> **Follow this link:**  [Walled Garden Script](https://klcis-gen.pages.dev/).

## IV. PAY-OUT and FEES

1. **Usage Fee:** PHP 150.00/month.
2. Use the Pay-out calculator for reference. [this link](https://s2.klinternetservices.com/calculate)
3. **Pay-out:** Minimum PHP 100.00. Requests are available every 5 days after the last pay-out.
4. **Disbursement:** Funds are processed immediately or within 24 hours.
   
For additional information, join our official Facebook Group.
FOR OTHER SYSTEM AND INFORMATION, Please join our official Facebook Group: https://www.facebook.com/groups/klcis

