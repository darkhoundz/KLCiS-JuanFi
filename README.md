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

> **Note:** This script supports only V1 and V2 offline/online stores. For V3 and V4, refer to [this link](https://s2.klinternetservices.com/voucher_store).

```bash
/ip hotspot walled-garden ip
add action=accept disabled=no dst-host=klinternetservices.com comment="klinternetservices.com"
add action=accept disabled=no dst-host=s2.klinternetservices.com comment="s2.klinternetservices.com"
add action=accept disabled=no dst-host=payments.gcash.com comment="payments.gcash.com"
add action=accept disabled=no dst-host=gcash-api.pulseid.com comment="gcash-api.pulseid.com"
add action=accept disabled=no dst-host=beacons.gcp.gvt2.com comment="beacons.gcp.gvt2.com"
add action=accept disabled=no dst-host=irisk-sea.alipay.com comment="irisk-sea.alipay.com"
add action=accept disabled=no dst-host=mss.paas.mynt.xyz comment="mss.paas.mynt.xyz"
add action=accept disabled=no dst-host=api.mynt.xyz comment="api.mynt.xyz"
add action=accept disabled=no dst-host=login.mynt.xyz comment="login.mynt.xyz"
add action=accept disabled=no dst-host=customer-segment-api.mynt.xyz comment="customer-segment-api.mynt.xyz"
add action=accept disabled=no dst-host=gw.alipayobjects.com comment="gw.alipayobjects.com"
add action=accept disabled=no dst-host=mdap.paas.mynt.xyz comment="mdap.paas.mynt.xyz"
add action=accept disabled=no dst-host=mgs-gw.paas.mynt.xyz comment="mgs-gw.paas.mynt.xyz"
add action=accept disabled=no dst-host=checkout.xendit.co comment="checkout.xendit.co"
add action=accept disabled=no dst-host=xqd9eal.x.incapdns.net comment="xqd9eal.x.incapdns.net"
add action=accept disabled=no dst-host=45.60.160.35 comment="45.60.160.35"
add action=accept disabled=no dst-host=xnd-merchant-logos.s3.amazonaws.com comment="xnd-merchant-logos.s3.amazonaws.com"
add action=accept disabled=no dst-host=110.75.232.97 comment="110.75.232.97"
add action=accept disabled=no dst-host=110.75.232.98 comment="110.75.232.98"
add action=accept disabled=no dst-host=110.75.232.99 comment="110.75.232.99"
add action=accept disabled=no dst-host=110.75.232.100 comment="110.75.232.100"
add action=accept disabled=no dst-host=xen.to comment="xen.to"
add action=accept disabled=no dst-host=18.138.78.193 comment="18.138.78.193"
add action=accept disabled=no dst-host=3.0.107.195 comment="3.0.107.195"
add action=accept disabled=no dst-host=3.1.78.74 comment="3.1.78.74"
add action=accept disabled=no dst-host=traefik-public.ap-southeast-1.tidnex.com comment="traefik-public.ap-southeast-1.tidnex.com"
add action=accept disabled=no dst-host=e9816.cj.akamaiedge.net comment="e9816.cj.akamaiedge.net"
add action=accept disabled=no dst-host=104.67.185.229 comment="104.67.185.229"
add action=accept disabled=no dst-host=checkout-ui-gateway.xendit.co comment="checkout-ui-gateway.xendit.co"
add action=accept disabled=no dst-host=assets.xendit.co comment="assets.xendit.co"
add action=accept disabled=no dst-host=assets.xendit.co comment="api.xendit.co"
add action=accept disabled=no dst-host=assets.xendit.co comment="payments.paymaya.com"
```


## IV. PAY-OUT and FEES

1. **Usage Fee:** PHP 150.00/month.
2. Use the Pay-out calculator for reference. [this link](https://s2.klinternetservices.com/calculate)
3. **Pay-out:** Minimum PHP 100.00. Requests are available every 5 days after the last pay-out.
4. **Disbursement:** Funds are processed immediately or within 24 hours.
   
For additional information, join our official Facebook Group.
FOR OTHER SYSTEM AND INFORMATION, Please join our official Facebook Group: https://www.facebook.com/groups/klcis

