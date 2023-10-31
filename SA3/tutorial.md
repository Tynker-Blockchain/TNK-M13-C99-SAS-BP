Display the Selected Account
====================================




In this activity, you will understand how to display the details of an account on the web page.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10752756/SA3.gif" width = "480" height = "320">


Follow the given steps to complete this activity.


1. Set the private key.


* Open the file `app.py`.


* Initialize a variable to store the private key and assign it the value. None in the `makeTransaction()` method.
~~~python
privateKey = None
~~~
* Check if the account variable is of type dict (dictionary). 
~~~python
if(type(account) == dict):
~~~
* Check if the the sender account matches to set the sender type and private key.
~~~python
if(sender == account['address']):
            senderType = 'newAccountAddress'
            privateKey = account['privateKey']
~~~
* Move the code in the boilerplate to the `else` part.
~~~python
if(sender == account.address):
            senderType = 'newAccountAddress'
            privateKey = account.privateKey
~~~
2. Display the information of the selected account


* Define the web route at the URL path `”/changeAccount”` to handle requests to change the account.
~~~python
@app.route("/changeAccount", methods= ["GET", "POST"]) `
~~~
* Define the changeAccount() function.
~~~python
def changeAccount():
~~~
* Access the global variables `account` and `allAccounts`.
~~~python
global account, allAccounts
~~~
* Access the address from the request sent by the web page.
~~~python
newAccountAddress = int(request.args.get("address"))
~~~
* Retrieve the values of the new account from `allAccounts` variable and store it in the `account` variable. 
~~~python
account = allAccounts[newAccountAddress]
~~~
* Redirect the page to the home page `”/”`.


` return redirect("/") ` 
 
* Save and run the code to check the output.