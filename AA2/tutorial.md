Remove the Account
==============




In this activity, you will learn to remove a particular account with an address from the database.


<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10752771/pasted-from-clipboard.png" width = "480" height = "320">


Follow the given steps to complete this activity.


1. Create a method to delete the account from the database.


* Open the file `wallet.py`.


* Define a method that takes the address of the selected account in the `Wallet` class.
~~~python
def deleteFromDB(self, address):
~~~
* Create a reference to the databas’s node `"accounts/"+address+"/"`.
~~~python
ref = db.reference("accounts/" + address + "/")
~~~
* Delete the data associated with the specified account's address from the database. 
~~~python
ref.delete()
~~~
 * Print a message to indicate that the account has been deleted from the database. 
~~~python
print("✨✨ ⚡️⚡️ Account deleted from database! ⚡️⚡️ ✨✨") ‘ 
~~~
2. Define the path to delete account


* Open the file `app.py`.


* Define the web route at the URL path `/deleteAccount` to handle the delete requests.
~~~python
@app.route("/deleteAccount", methods= ["GET", "POST"])
~~~
* Define the `deleteAccount()` function.
~~~python
def deleteAccount():
~~~
* Access the global variables account and myWallet.
~~~python
global account, myWallet
~~~
* Delete the account from the database using the `deleteFromDB` method from `Wallet` class.
Check if the variable type of `account` is a dictionary to access the account address from a dictionary or a list.
~~~python
if(type(account) == dict):
	myWallet.deleteFromDB(account["address"])
else:
myWallet.deleteFromDB(account.address)
~~~
* Set the current account to the first account in the `allAccounts` list.
~~~python
account = allAccounts[0]
~~~


* Redirect to the home page ("/"), after successfully deleting the account.
~~~python
` return redirect("/") `
~~~
* Save and run the code to check the output.