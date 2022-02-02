# AyudaTeam

The objective of Ayuda is as Everyday new information is being gathered about the novel Coronavirus COVID 19. Keeping track of new developments and sending out instant notifications to all departments in the hospitals is an essential activity. Poor communication, undirected updates, and delay in providing valuable information should not cost more lives due to this virus. Hospitals should deploy emergency notification software to spread accurate information and keep their staff and patients informed and safe. 



THE AYUDA SOLUTION is organized into two CHAPTERS:  Chapter One is a PRIME RESPONDER solution in MULTIPLE LANGUAGES to deliver a CONVERSATIONAL AVATAR in the NATIVE LANGUAGE of the local COMMUNITY where it is deployed. CHAPTER TWO is about PROTECTING the identity of the user of the PRIME RESPONDER by the  IDENTITY and ASSET TRANSFER protections of a BLOCKCHAIN. 

We addressed the following problems with current courageous efforts to tackle COVID19

SOLUTIONS ARE AVAILABLE ONLY IN ENGLISH YET THIS IS A GLOBAL PROBLEM
DIFFERENT CULTURES RESPOND TO COVID19 DIFFERENTLY
THERE IS NO EQUIPMENT TO TEST PEOPLE OR FACEMASKS FOR PROFESSIONALS LIKE N95
PEOPLE DO NOT LIKE AVATARS. THIS IS CALLED UNCANNY VALLEY
THERE IS NO WAY OF GETTING URGENT AND NEEDED SUPPLIES AND PAYING FOR THEM
SOLUTIONS NEED TO OBEY THE LAW. THESE ARE ANTI MONEY LAUNDERING, FDA, AND MANY OTHERS IN THE LOCAL CULTURE

CHAPTER ONE is the multi-lingual avatar
CHAPTER TWO is the BLOCKCHAIN or HYPERLEDGER FABRIC 2.0

CHAPTER ONE

We have many examples of avatars we used which can be accessed here https://www.avitarworld.com/

The Competition example is here 
* Here API used 


GPS+ Digital Tracing

Enhanced manual contact tracing tools
Hot spot exposure notifications



 


End-to-End System
Ayuda is designed to work with Safe Places, a tool for contact tracing teams to work with location data in the course of contact tracing interviews and to publish points of concern. Without having to sharing their own location history, a Ayuda user can download the points of concern from their PHA to identify if they have had risk of an exposure.
 
 
 
 
Create and use Avatar using a Mobile Application.
Integrate Watson Assistant and Python Flask application using Webhooks.
Customize based on the personal requirements.
Create a dynamic real time chatbot.

Flow
User asks a query to the AR Avatar (mobile app).
Mobile application converts the speech to text using Watson speech to text and sends the query to IBM Mobile Foundation.
IBM Mobile Foundation securely passes the query to Watson Assistant.
Watson Assistant triggers the appropriate IBM Cloud Function, based on the query received.
Based on the query, IBM Cloud Function triggers the appropriate service or services, in the backend server application.
Backend server application returns the response for the query.
IBM Cloud Function sends the response to Watson Assistant.
Watson Assistant frames a response to reply to the user and sends it to IBM Mobile Foundation.
IBM Mobile Foundation securely sends the response to the mobile application.
Mobile application converts the text into speech using Watson Text to Speech.
Mobile application replies to the user using the AR Avatar.
Watch the Video

Pre-requisites
IBM Cloud account: Create an IBM Cloud account.
Python 3: Install python 3.
Java 1.8.x: Make sure you have required version (Java 1.8.x).
Before you begin please note that this application uses AR-Core Library, and not all Android devices support AR-Core. To know which devices support AR-Core visit the Supported Devices page.
Android Studio : Download and Install Android Studio with SDK Version 26 or Above.
Steps
Please follow the below to setup and run this code pattern.
Clone the repo
Create Watson services with IBM Cloud
Update the details in the Backend Flask Application
Deploy the Flask Application
Setup Cloud Functions
Setup Watson Assistant
Setup IBM Mobile Foundation Server and CLI
Setup Google Cloud Anchors
Configure Android App
Build and Run Android App
1. Clone the repo
Clone this git repo. Else, in a terminal, run:
$ https://github.com/IBM/avatar-based-dynamic-chatbot-with-ai-and-ar-capabilities.git

2. Create Watson services with IBM Cloud
Create the following services:
Watson Assistant: Create a Watson Assistant instance on your IBM cloud.
IBM Cloud Functions: Create an IBM Cloud Functions instance on your IBM cloud.
Speech to Text: Create a Speech to Text instance on your IBM cloud.
Text to Speech: Create a Text to Speech instance on your IBM cloud.
Mobile Foundation: Create a Mobile Foundation instance on Your IBM Cloud.
3. Update the details in the Backend Flask Application
Visit the url here.com API to generate the Api Key for running the application.
hit the green colored button Generate API KEY .
Fill the information form. And you will get the API KEY. Copy it to Clipboard.
Open the Python Flask File, go to line number 35 of the code in the function getRestaurants(coordinates) and update the user-key which you have generated in the above step.
header = {"User-agent": "curl/7.43.0", "Accept": "application/json", "user-key": "update the user-key here!"}


4. Deploy the Flask Application
Create a Cloud Foundry service with python runtime and follow the steps.

You can give any app name, in our case we have given the app name as my-api.
From the cloned repo, goto flask-api directory.
$ cd flask-api/
Make sure you have installed IBM Cloud CLI before you proceed.
Log in to your IBM Cloud account, and select an API endpoint.
$ ibmcloud login
NOTE: If you have a federated user ID, instead use the following command to log in with your single sign-on ID.
$ ibmcloud login --sso
Target a Cloud Foundry org and space:
$ ibmcloud target --cf
From within the flask-api directory push your app to IBM Cloud.
$ ibmcloud cf push <YOUR_APP_NAME>
Example: As our app name is my-api we use the following command.
$ ibmcloud cf push my-api
You will see output on your terminal as shown, verify the state is running:
Invoking 'cf push'...

Pushing from manifest to org  (YOUR ORG)
...

Waiting for app to start...

...

  state     since                  cpu     memory           disk           details
#0   running   2019-09-17T06:22:59Z   19.5%   103.4M of 512M   343.4M of 1G

Once the API is deployed and running you can test the API.
Goto IBM Cloud Resources and select the Deployed API, my-api in our case.

Inside the my-api dashboard, right click on Visit App URL and Copy the link address.
Example link address: https://my-api-xx-yy.eu-gb.mybluemix.net

NOTE: This API Link is Important, please save it in any notepad since it will be used in subsequent steps.
5. Setup Cloud Functions
Create a Cloud Function Action.

You will see a hello world code in the canvas.

Copy the code given below and replace it in the canvas as shown.

Replace the CloudFoundryURL in the code with the URL that you copied to your notepad in step 3.
Example: CloudFoundryURL = "https://my-api-xx-yy.eu-gb.mybluemix.net"
 


Click on Endpoints on the left panel and select Enable as Web Action finally click on Save.

Finally Copy the Public Link which is displayed.

NOTE: The Above URL should end with .json if it is not ending with .json please append .json at the end of the URL. NOTE: This URL is Important, please save it in any notepad since it will be used in subsequent steps.
6. Setup Watson Assistant
Create a Watson Assistant Service. 
Once you create a watson assistant service copy the API Key and URL into a notepad as it will be used in step 6.

Click on Launch Watson Assistant after copying the credentials. In the Watson Assistant Dashboard click on Skills tab as shown.

Click on Create Skill as shown.

Click on Dialog Skill and click next.

Click on Import Skill and choose the json file from /watson assistant/skill-Avatar-chatbot.json.

You will now see the Assistant Dashboard with skills as shown.

Click on the Options button in the left panel and under Webhooks Enter the URL that was copied in step 4.

Back to Watson Assistant Dashboard, open options menu from the recently imported skill Avatar-chatbot Demo and select View API Details as shown.

Copy the Skill ID in a notepad as it will be used in subsequent steps.

7. Setup IBM Mobile Foundation Server and CLI
7.1 Setup Ionic and MFP CLI
Install Node.js by downloading the setup from https://nodejs.org/en/ (Node.js 8.x or above)
$ node --version
v10.15.0

Install IBM Mobile Foundation Platform CLI
$ sudo npm install -g mfpdev-cli
$ mfpdev --version
8.0.0-2018121711

Note: If you are on Windows, instead of using sudo, run the above command without sudo in a command prompt opened in administrative mode.
Note: While installing MFP CLI, if you hit an error saying npm ERR! package.json npm can't find a package.json file in your current directory., then it is most likely due to MFP CLI not being supported in your npm version. In such a case, downgrade your npm as below, and then install MFP CLI. $ sudo npm install -g npm@3.10.10
Install Java SDK 8 from https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=openj9
$ java -version
java version "1.8.0_101"

Note: Java version 1.8.x is required to build the Java Adapters. Do not Download Java version 11.x. If you already have java version above 1.8.x then you can follow the guide in TROUBLESHOOTING.md to uninstall the java and reinstall 1.8.x.
Install Maven: On Mac, you can use brew install for installing Maven as shown below:
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew install maven
$ mvn --version
Apache Maven 3.6.0 ...

On Windows, you can follow this Tutorial to install Maven.
7.2 Create Mobile Foundation service and configure MFP CLI
In the IBM Cloud Dashboard,open Mobile Foundation. Click on Create as shown below.

In the Mobile Foundation service overview page that gets shown, click on Service credentials. Expand View credentials and make a note of the url, user and password as shown below.

NOTE: The user, password and url is Important as it will be used in subsequent steps.
NOTE: Make Sure the Cloud Foundry App for Mobile Foundation-Server gets at least 768MB of Memory.(Recommended is 1GB) You can verify it by going to IBM Cloud Dashboard > Resources > Cloud Foundry Apps > MobileFoundation-Server as shown below.

Note: If Mobile Foundation service is not available with your current account type, then you can:
Upgrade your account, and avail the Mobile Foundation service's free Developer plan which allows the use of the service free for up to ten daily client devices for development and testing activities.
Back on your local machine, configure MFP CLI to work with Mobile Foundation server by running the following command in console.
Note: For Enter the fully qualified URL of this server:, enter the url mentioned in credentials followed by :443 (the default HTTPS port).
$ mfpdev server add

Follow the Instructions.
? Enter the name of the new server profile: MyServer
? Enter the fully qualified URL of this server: https://mobilefoundation-xxxx-xxxxx.xx-xx.mybluemix.net:443
? Enter the Mobile Foundation Server administrator login ID: admin
? Enter the Mobile Foundation Server administrator password: **********
? Save the administrator password for this server?: Yes
? Enter the context root of the Mobile Foundation administration services: mfpadmin
? Enter the Mobile Foundation Server connection timeout in seconds: 30
? Make this server the default?: Yes
Verifying server configuration...
The following runtimes are currently installed on this server: mfp
Server profile 'MyServer' added successfully.

Next Verify If the Server is added.
$ mfpdev server info
Name         URL
---------------------------------------------------------------------------------------
MyServer  https://mobilefoundation-xxxx-xxxxxx.xx-xx.mybluemix.net:443  [Default]
---------------------------------------------------------------------------------------

Note: If this step fails check TROUBLESHOOTING.md to fix commonly occuring errors.
7.3 Deploy the MFP Adapter and Test it
7.3.1 Build and Deploy the MFP adapters
Go to the Adapter/avatarchatbot directory.
$ cd /AvatarChatbot/Adapter/avatarchatbot

Build the avatarchatbot adapter as shown below.
$ mfpdev adapter build
Building adapter...
Successfully built adapter

Deploy the adapter as shown bellow.
$ mfpdev adapter deploy
Verifying server configuration...
Deploying adapter to runtime mfp on https://mobilefoundation-xxxx-xxxxxx.xx-xx.mybluemix.net:443/mfpadmin...
Successfully deployed adapter

Note: In [Step 7.2], if you specified No to Make this server the default?, then you need to specify the name of your server profile (MyServer in our case) at the end of mfpdev adapter deploy command as shown below.
$ mfpdev adapter deploy MyServer

7.3.2 Launch MFP dashboard and update adapter configurations
Launch MFP Dashboard as below:
In the IBM Cloud dashboard, under Cloud Foundry Services, click on the Mobile Foundation service you created in [Step 7.2]. The service overview page that gets shown, will have the MFP dashboard embedded within it. You can also open the MFP dashboard in a separate browser tab by appending /mfpconsole to the url https://mobilefoundation-xxxx-xxxxx.xx-xx.mybluemix.net.
Example: https://mobilefoundation-xxxx-xxxxx.xx-xx.mybluemix.net/mfpconsole
NOTE: username & password can be found in Service credentials in step 7.2.
Inside the MFP dashboard, in the list on the left, you will see the avatarchatbot adapter listed.
Update MFP Adapter configuration as below:
Inside the MFP dashboard, click on the avatarchatbot adapter. Under Configurations tab, you should see the various properties as shown.

Save the changes by clicking Save.
Click on Resources tab. You should see the various REST APIs exposed by avatarchatbot adapter as shown below.

7.3.3 Test the CloudantJava adapter
To Test the adapter use any REST Clients like Postman. After Installing postman type the url created in [step 3.2] and append it with /mfp/api/adapters/avatarchatbot/resource/mfpapi.
Example: https://mobilefoundation-xxxx-xxxxxx.xx-xx.mybluemix.net/mfp/api/adapters/avatarchatbot/resource/mfpapi.
Now click on Send button to run the GET /mfp/api/adapters/avatarchatbot/resource/mfpapi API. The API response should get shown in the Response Body as shown in snapshot below.
The GET API on /mfp/api/adapters/avatarchatbot/resource/mfpapi should return a JSON object containing s2tapi, s2turl, t2sapi, t2surl, assistantapi, assistanturl, assistantworkspaceid & cloudfuncurl from your Cloudant as shown below.

8. Setup Google Cloud Anchors
Create a Google Cloud Account.
In the Google Cloud Dashboard click on Go To Console.

Create a new Project in Google Cloud Platform.
Once you create a project in the Dashboard search for ARCore Cloud Anchor API.

Click on Enable.

Now in the left panel click on Credentials.

Click on Create Credentials.

Click on Help me choose.

Select the api key option in the top as shwon.

Finally click on Create to create the api key.


NOTE:Copy the API key as it will be required in the subsequent step.
9. Configure Android App
There are 3 more things to be done before running the APP.
9.1. Add the ARCore Cloud API Key in Android Studio
Open Android Studio and click on Open an existing Android Studio Project and locate the AvatarChatbot directory from the cloned directory.
In Android Studio open the AndroidManifest.xml file in app -> manifests -> AndroidManifest.xml and enter your ARCore Cloud API Key which was copied in step 8.

9.2. Setup Poly Objects in Android Studio
In Android Studio goto File > Preferences > Plugins and click on Browse Repositories button.
Search for the keyword sceneform and install it as shown.

Click on Build > Make Project to build the android project.
NOTE: The Initial Gradle Build may take much longer time please be patient.
Download the poly objects from the bellow URL's.
Asset
Credits
Link
Female Human Avatar
Dominic Barnard
https://poly.google.com/view/5sDdEAo2zfq
Arrow
Vanessa Cao
https://poly.google.com/view/bC3FokNqTpi

Extract the .zip files.
In Android Studio, in the left panel right click and select New > Sample Data Directory as shown.

Right click on the newly created sampledata directory and select Reveal in Finder for Mac.
On Windows Right click on the newly created sampledata directory and select Show in Explorer.

Create two directories named Avatar and Arrow and extract the contents from the respective .zips into the directories.

Back to Android Studio, go to sampledata > Avatar and right click on female.obj file and select Import Sceneform Asset as shown.

You will get an Import Wizard, Click on Finish.

Repeat the same for Arrow, go to sampledata > Arrow and right click on model.obj file and select Import Sceneform Asset.
Once you Import both the Assets, you can verify them under Assets directory as shown.

You are done Importing the Sceneform Assets at this point.
9.3. Register the Android App to Mobile Foundation Server
On the Commandline, enter the following command to register the app to Mobile Foundation server.
$ mfpdev app register
Verifying server configuration...
Registering to server:'https://mobilefoundation-xxxx-xxxxx.xx-xx.mybluemix.net:443' runtime:'mfp'
Registered app for platform: android

10. Build and Run Android App
Install Android SDK Platform 24 (or higher) as below:
Launch Android Studio.
Click on Configure -> SDK Manager.
Under SDK Platforms, select Android 7.0 (Nougat) API Level 24 or higher. Click Apply and then click OK. This will install Android SDK Platform on your machine.
Enable USB debugging on your Android phone as per the steps in https://developer.android.com/studio/debug/dev-options
Launch the Settings app on your phone. Select About Device -> Software Info. Tap Build number 7 times to enable developer options.
Return to Settings list. Select Developer options and enable USB debugging.
If you are developing on Windows, then you need to install the appropriate USB driver as per instructions in https://developer.android.com/studio/run/oem-usb.
Connect the Android phone to your development machine by USB cable, you will get a prompt displaying adb access required, allow the access.
Note: If you have android adb tools you can check whether your device is connected or not by entering adb devices.
Connect the android device to the deployment machine it will be displayed on the screen. Select that and click ok.

Note: You will get a prompt displaying adb access required, allow the access only then the device will be shown in the above window.
Wait for Gradle to finish the build and install the Apk on your android device.
 
 
 
 
 
 
Here are the Resources list of IBM Cloud






 
 
Sample output
NOTE: Please follow the tutorial in the app to train the path before folowing this flow.
 
The workflow of the app is as follows.
NOTE: The user has to follow the exact same workflow for the app to function as intended.
The user summons the Avatar Chatbot by taping on the Anchors in the app.
 
 
 
 
INSERT  WEBSITE ADDRESS HERE
 
The Avatar Chatbot tells user their location.
Bot: Looks like you are in <YOUR-LOCATION>?
The user has to reply with yes to confirm.
Yes
The Avatar Chatbot can then read the user's Interest based on their activities on the phone.
I got to know that you are a massive Nike fan, Do you want me to guide you to a nearby Nike store that has got new collections?
NOTE: This feature is just to showcase the capabilities of watson services and is not currently implemented in the code pattern. You can modify as per your requirements.
Asuming user wants to do something else user has to reply with no thanks.
No thanks
The Avatar Chatbot will ask the following.
Okay, do you want me to help with anything else?
Asuming user is looking for restaurants the user has to say the following.
I am looking for a good restaurant near me
NOTE: In this code pattern we have just inplemented Food API to get food related queries, you can have any service APIs to increase the functionality of the chatbot.
The Avatar Chatbot finds out the best restaurant nearby.
<Restaurant-Name> has the best rating around this place. Do you want me to guide you to <Restaurant-Name>?
Asuming the user is satisfied with the result, the user confirms by saying cool works.
cool works!
The Avatar Chatbot says the following.
Please follow the path.
The User will then click on SHOW ROUTE button and the Augmented path will appear guiding you to the destination that you trained earlier.
 
NOTE: This code pattern acts as a foundation for building intelligent AR based chatbots. You can modify this code pattern and build as per your requirement.

 
ADD IBM SERVICES HERE:             

 





