# Hyperledger-Fabric
Supply Chain Management App for Hyperledger Fabric

Recommended Specs:
1. Core i5 4th gen
2. 8gb Ram
3. Virtualbox
4. Ubuntu 16.04
5. 250gb HDD

Prerequisites:
1. Golang 1.11
2. Postman
3. Docker Engine 1.8 or Higher
4. Node 8.9 or Higher
5. NPM v5.x
6. Git 2.9 or Higher
7. Code Editor (Ex. VS Code)
8. Cloned Fabric Sample from github.

Set-up instructions:
1. Open fabric-samples/fabcar in Terminal.
2. Type and press Enter: ./openScm.sh (optional: npm install before or after this command)
3. Type and press Enter: node enrollAdmin.sh
4. Type and press Enter: node registerUser.sh
5. Type and press Enter: node rSupplier1.js
6. Type and press Enter: node rOEM.js
7. Type and press Enter: node rBank.sj
8. To test all functions, type and press Enter: node app_scm.sh

   Listening to Port 3000.
   
9. To test as supplier1, open a new Terminal window, type and press Enter: node appSupplier1.js

    Listening to Port 3001.

    Note: supplier1 can only raise an invoice (number 3 below).

10. To test as OEM, open a new Terminal window, type and press Enter: node appOEM.js

    Listening to Port 3002.

    Note: OEM can only set that goods are received (number 4 below).
    
11. To test as OEM, open a new Terminal window, type and press Enter: node appBank.js

How to use:
1. Open Postman
2. To display all invoices, set it to GET, type localhost:<Port>/queryAllInvoice in the address bar and click Send.
3. To raise an invoice, set it to POST, go to Body tab, and tick x-www-form-urlencoded

   Type in the following keys: (one key per line, case-sensitive)

	     Key			Value (sample)
	
	invoiceNumber		INV002
	billedTo		Lenovo
	invoiceDate		2/9/2019
	invoiceAmount		50000
	itemDescription		any description here
	gr			no
	isPaid			no
	paidAmount		0
	repaid			no
	repaymentAmount		0

   Type localhost:<Port>/invoice in the address bar and click Send.

   Do number 2 to check if it worked.

4. To set that goods are received in an invoice, set it to PUT, go to Body tab, and tick x-www-form-urlencoded

   Type in the following keys: (one key per line, case-sensitive)

	     Key			Value (sample)
	
	invoiceNumber		INV002
	gr			yes

   Type localhost:<Port>/invoice in the address bar and click Send.

   Do number 2 to check if it worked.

5. To pay the supplier by bank, set it to PUT, go to Body tab, and tick x-www-form-urlencoded

   Type in the following keys: (one key per line, case-sensitive)

	     Key			Value (sample)
	
	invoiceNumber		INVxxx
	isPaid			yes
	paidAmount		49000 (this must be less than the invoiceAmount)

   Type localhost:<Port>/invoice in the address bar and click Send.

   Do number 2 to check if it worked.

6. To repay the bank by OEM, set it to PUT, go to Body tab, and tick x-www-form-urlencoded

   Type in the following keys: (one key per line, case-sensitive)

	     Key			Value (sample)
	
	invoiceNumber		INVxxx
	repaid			yes
	repaymentAmount		51000 (this must be greater than the paidAmount)

   Type localhost:<Port>/invoice in the address bar and click Send.

   Do number 2 to check if it worked.
