Store Account data in Firebase
============================


In this activity, you will learn to store the account address in Firebase by building a real-time database, connecting to it, and adding the account address.


<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10752394/SA1.gif" width = "480" height = "320">


Follow the given steps to complete this activity.


1. Build a database on Firebase 


* Build a database on Firebase by creating a new project and building a real-time database in the test mode.
<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10751821/SA1_step1.gif" width = "480" height = "320">


2. Connect the database with the app
Connect to the Firebase by copying its link.
<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10751836/copy_link.gif" width = "480" height = "320">


* Generate its private key and save it as a serviceAccountKey.json file in the config folders of all the activities.
<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10751856/Generate_Private_Key.gif" width = "480" height = "320">


* Open the file “`app.py`.


* Import firebase_admin and credentials to import the necessary modules from the firebase_admin library that allow to interact with Firebase services.
~~~python
import firebase_admin
from firebase_admin import credentials
~~~       
* Define the function firebaseInitialization() to initialize the Firebase connection.
~~~python
def firebaseInitialization():
~~~
*  Initialize the credentials from a JSON certificate key file which was saved in the config folder.
~~~python
cred = credentials.Certificate("config/serviceAccountKey.json")
~~~
* Copy the Firebase Realtime Database's URL from your Firebase account. 
<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10751836/copy_link.gif" width = "480" height = "215">


* Create a new app instance using the credentials and the URL. 
Sample URL: “https://blockchain-wallet-a2812-default-rtdb.firebaseio.com”
~~~python
firebase_admin.initialize_app(cred, {'databaseURL': 'paste the url to your databe here'})
~~~
* Print “Firebase connected!” to indicate that the Firebase connection has been established.
~~~python
print("🔥🔥🔥🔥🔥 Firebase Connected! 🔥🔥🔥🔥🔥")
~~~
* Call the firebaseInitialization() function, which contains all the steps mentioned above, to ensure that Firebase is properly initialized.
~~~python
firebaseInitialization()
~~~


3. Add address to database




* Open the file `wallet.py`.


* Import the `db` module from the `firebase_admin` library. 
The `db` module provides functionality to interact with the Firebase Realtime Database.
~~~python
from firebase_admin import db
~~~
*  Call the `addToDB()` method to add the account address and the private key to the database.
~~~python
self.addToDB(self.address, self.privateKey)
~~~   
* Define the `addToDB` method that takes the account address and private key.
~~~python
def addToDB(self, address, privateKey):
~~~
* Create a reference for the node `account/address/` in the database.
~~~python
ref = db.reference("accounts/" + address + "/")
~~~
* Set the data at the reference location to a dictionary value of address and privateKey.
~~~python
ref.set({
"address" : address,
"privateKey" :privateKey
})
~~~   
* Save and run the code to check the output.