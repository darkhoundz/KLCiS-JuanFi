# KLCiS Voucher System (Embedded E-Payment) Hotspot Template for JuanFi v4.3
JuanFi is an open source system for coinslot integration for mikrotik hotspot developed by Ivan Julius Alayan.
https://github.com/ivanalayan15/JuanFi

With the integration of KLCiS Voucher System, JuanFi operated machines will be able to accept e-payments (Gcash, PayMaya, GrabPay and ShopeePay)
Voucher codes will be automatically generated after a successful payment coupled with SMS notification.
https://klinternetservices.com



![2023-12-04 00_43_44-Control Panel](https://github.com/darkhoundz/KLCiS-JuanFi/assets/28075740/3eb6e819-f966-41dc-a2b9-8bdcfd2d6ec5)

====================== <br>
I. REQUIREMENTS: <br>
====================== <br>

1. A KLCiS Voucher System account, create an account at https://klinternetservices.com
2. Voucher codes with the corresponding amount in CSV format. Here's the tutorial using Mihkmon as voucher generator: https://youtu.be/dnQ8RlyxbKE?t=1246

====================== <br>
II. INSTALLATION: <br>
====================== <br>

1. Download the template in this repository and upload it to the Mikrotik hotspot directory.
2. Find this line in the login.html:

		<select class="form-control" id="amountDropdown" name="amount" style="width:100%; font-size:16px; font-weight:500; color:green;">
			<option value="5">₱5.00 - 1 HOUR UNLIMITED</option>
			<option value="10">10.00 - 1 DAY UNLIMITED</option>
			<option value="100">₱100.00 - 7 DAYS UNLIMITED</option>
			<option value="300">₱300.00 - 30 DAYS UNLIMITED</option>
	    </select>

	Edit the option value matching to the voucher code in the uploaded CSV file in your KLCiS account.
   
4. Find this line in the login.html:
   
   		<input type="hidden" class="form-control" id="tokenInput" name="token" value="PUT_YOUR_KLCIS_API_KEY_HERE">
   
   Add the KLCiS Voucher System API Key.

5. Test your KLCiS API Key if working, try to select a promo, add your active number and click the buy BUY NOW button. A payment gateway will appear. NOTE YOU MUST HAVE FIRST AN INTERNET CONNECTION DURING TESTING.

6. Log-in to your KLCiS Account, the go to Transactions you will then see your transaction log with the status UNPAID with your mobile number. Congratulations your KLCiS is now active!

============================ <br>
III. WALLED GARDEN SETUP <br>
============================ <br>

If you want your clients to be able to purchase voucher codes using e-payment without session/internet load, run this Walled Garden script to the Mikrotik's Terminal.

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
	add action=accept disabled=no dst-host=cdnjs.cloudflare.com comment="cdnjs.cloudflare.com"
	add action=accept disabled=no dst-host=checkout.xendit.co comment="checkout.xendit.co"
	add action=accept disabled=no dst-host=xqd9eal.x.incapdns.net comment="xqd9eal.x.incapdns.net"
	add action=accept disabled=no dst-host=45.60.160.35 comment="45.60.160.35"
	add action=accept disabled=no dst-host=xnd-merchant-logos.s3.amazonaws.com comment="xnd-merchant-logos.s3.amazonaws.com"
	add action=accept disabled=no dst-host=rum-ingest.us1.signalfx.com comment="rum-ingest.us1.signalfx.com"
	add action=accept disabled=no dst-host=110.75.232.97 comment="110.75.232.97"
	add action=accept disabled=no dst-host=110.75.232.98 comment="110.75.232.98"
	add action=accept disabled=no dst-host=110.75.232.99 comment="110.75.232.99"
	add action=accept disabled=no dst-host=110.75.232.100 comment="110.75.232.100"
	add action=accept disabled=no dst-host=snowplow-collector.iluma.ai comment="snowplow-collector.iluma.ai"
	add action=accept disabled=no dst-host=xen.to comment="xen.to"
	add action=accept disabled=no dst-host=18.138.78.193 comment="18.138.78.193"
	add action=accept disabled=no dst-host=3.0.107.195 comment="3.0.107.195"
	add action=accept disabled=no dst-host=3.1.78.74 comment="3.1.78.74"
	add action=accept disabled=no dst-host=traefik-public.ap-southeast-1.tidnex.com comment="traefik-public.ap-southeast-1.tidnex.com"
	add action=accept disabled=no dst-host=e9816.cj.akamaiedge.net comment="e9816.cj.akamaiedge.net"
	add action=accept disabled=no dst-host=104.67.185.229 comment="104.67.185.229"
	add action=accept disabled=no dst-host=*.gcash.com.edgekey.net comment="*.gcash.com.edgekey.net"
	add action=accept disabled=no dst-host=assets.xendit.co comment="assets.xendit.co"
	add action=accept disabled=no dst-host=checkout-ui-gateway.xendit.co comment="checkout-ui-gateway.xendit.co"

====================== <br>
IV. PAY-OUT and FEES <br>
====================== <br>

1. To be able to use the KLCiS Voucher System, you must pay PHP 150.00/month for the usage fee. We have provided a Pay-out calculator for your reference: https://s2.klinternetservices.com/calculate
2. You can request PAY-OUT once your balance reached PHP 100.00. Pay-out request is available once a week.
3. Funds will be disbursed within 24 hours.

FOR OTHER SYSTEM AND INFORMATION, Please join our official Facebook Group: https://www.facebook.com/groups/klcis

