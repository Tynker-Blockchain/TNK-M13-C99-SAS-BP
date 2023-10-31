Show the Total Balance of all Accounts
=================




In this activity, you will learn to calculate the total balance available in all accounts and show it on the web page.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10752764/pasted-from-clipboard.png" width = "480" height = "320">


Follow the given steps to complete this activity.


1. Calculate the total balance


* Open the file `app.py`.


* Initialize a variable to 0 to store the total balance of all accounts.
~~~python
totalBalance = 0
~~~
* Loop through the accounts in the `allAccounts` list to find the balance of each account.
~~~python
for acnt in allAccounts:
~~~
* Store the balance of each account in the `acntBalance` variable using the `getBalance()` method of the `Wallet` class.
~~~python
acntBalance = myWallet.getBalance(acnt['address']) 
print(acntBalance)
~~~


* Add the balance of each account to the total balance.
~~~python
 totalBalance += acntBalance
 print(totalBalance)
~~~
* Render the total balance to the web page.
~~~python
return render_template('index.html', isConnected=isConnected, account= account, balance = balance, transactions = transactions, allAccounts = allAccounts, totalBalance = totalBalance)
~~~

* Save and run the code to check the output.