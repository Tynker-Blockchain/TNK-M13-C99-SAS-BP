Display the Account Addresses
==============================


In this activity, you will learn to fetch the account addresses from Firebase and display them on the webpage.


<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10752407/SA2.gif" width = "480" height = "320">


Follow the given steps to complete this activity.


1. Retrieve the Accounts


* Open the file `wallet.py`.


*  Define a method within the Wallet class to retrieve all the accounts from the database.
~~~python
def getAccounts(self):
~~~
*  Create a reference to the "accounts/" path in the database.
~~~python
ref = db.reference('accounts/')
~~~
* Store the data retrieved from the database using the reference in a variable.
~~~python
   accounts = ref.get()
~~~    
* Convert the values in the variable account to a list. Save the converted values in the same variable.
~~~python
accounts = list(accounts.values())
~~~
* Return the list of accounts with addresses and private key values stored as dictionaries.
~~~python
return accounts
~~~
2. Check if an account exist


* Open the file `app.py`.


*  Initialize an empty list that can be used to store a collection of accounts.
~~~python
allAccounts = []
~~~
* Access the global variable allAccounts.
~~~python
global myWallet, account, allAccounts
~~~
* Use the userdefined function `getAccounts()` method on `myWallet` to retrieve the list of accounts and store them in the `allAccounts` variable.
~~~python
allAccounts = myWallet.getAccounts()
~~~
* Check if the account address is None and if allAccounts is not empty.
~~~python
if(account == None and allAccounts):
~~~       
* Store the first account from the `allAccounts` as the current account.
~~~python
account = allAccounts[0]
~~~
3. Fetch the account balance and transactions


*  Check if the data type of the account is a dictionary, as the account set from the list of accounts is in the form of a dictionary and while creating an account address is an object.
~~~python
if(type(account) == dict):
~~~
*  Call the `getBalance` method from the `Wallet` class to set the balance of the account address.
~~~python
balance = myWallet.getBalance(account['address'])
~~~
* Call the `getTransactions` method from the `Wallet` class to get the transactions of the account.
~~~python
transactions = myWallet.getTransactions(account['address'])
~~~
4. Display the accounts
   
* Move the code to get the balance and transactions of an account when a new account address is created (which is already in the boilerplate) to the `else` part. 
~~~python
balance = myWallet.getBalance(account.address)
transactions = myWallet.getTransactions(account.address)
~~~
* Render all the accounts to the web page.
~~~python
return render_template('index.html', isConnected=isConnected, account= account, balance = balance, transactions = transactions, allAccounts = allAccounts)
~~~
* Save and run the code to check the output.