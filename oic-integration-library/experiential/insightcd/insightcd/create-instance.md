# Create Your Oracle Integration (OIC) Instance

## Introduction

SHOULD USE NoVNC

**Estimated Time**: 20 minutes

### Objectives
* Create access policies for OCI Data Integration using Policy Builder UI in Oracle Cloud Infrastructure
* Create a Workspace for Data Integration resources

## Task 1: Create policies for OCI Data Integration

2. Here you will find the login tenant information required for this lab.  Now click on the **OCI CONSOLE** button to logon.

![](./images/oci-step2.png)

3. The credentials (username and password) to the login page.

![](./images/oci-step3.png)

4. Now you are on OCI mainpage. Click the hamburger icon at the top left corner. Select **Developer Services** on the left menu, then **Integration**. 

![](./images/oci-step4.png)

5. Select your assigned compartment in the compartment dropdown menu.  Then click on **Create** button on the right to create an OIC instance.

![](./images/oci-step5.png)

6. The **Create Integration Instance** window displays.  In **Display Name** field, give a name to your OIC instance.  Edition is **Enterprise**, License Type is **Subscribe to a new Oracle Integration license**.  Then click **Create** at the bottom of the form.

![](./images/oci-step6.png)

7. It takes around 10-15 minutes for a new OIC instance to be created for you.  Once it is done, the state will be changed from **creating** to **active** and you will be able to see a green dot.

![](./images/oci-step7.png)

8. Click on your instance link under Display Name.  Click the **Service Console** to activate the OIC instance. 

![](./images/oci-step8.png)

9. Now you are at Oracle Integration mainpage. Click the hamburger icon at the top right of Chrome browser to zoom out to 67-80% to optimize your viewing experience.

![](./images/zoom-out-screen.png)

## Task 2: Download and Import the Process Application

You need an exp file of Mama Maggy's process flow to import into your Oracle Integration instance while you are working on the labs.  Download it now before we start doing the lab.  

1. Click ****+**** on the top of the browser to add a new tab.  Copy and paste the below link to the URL field to download the below process application (exp file) we built for Mama Maggy:
NEED TO SETUP FILE in OBJECTSTORAGE
    - **WW0324_Order Request Processing** [](./files/WW0324_Order_Request_Processing.exp)

With the file downloaded, follow below steps to import it into your Oracle Integration instance now:

2. Return to the Oracle Integration tab on your browser.

3. Click on the ****hamburger menu icon**** at the top left to display the navigation pane.
![](./images/insight-image95.png)

4. Select ****Processes****, then ****Process Applications**** to enter the OIC Process page. 

5. Click ****Create**** at the top right corner.
![](./images/insight-image96.png)

6. Select the middle tile ****Import an Application****.

7. Click ****Choose File**** button, then the ****Open File**** window pops up.

8. Double click ****Download folder****, then you should be able to find the exp file you've just downloaded.  Select it, then click ****Open**** at the top right corner.
![](./images/insight-image97.png)

9. Click ****Import**** button. 
![](./images/insight-image98.png)

10. Wait a few seconds, it will then show this ****Application Home**** page having the file name displayed at the top. Feel free to click ****Request Evaluation**** box to take a look at the process flow embedded into this application before moving on to the Insight labs.
![](./images/insight-image99.png)

## Task 3: Import and Configure a Pre-Built Integration

Demo Video
[](https://videohub.oracle.com/media/Import+Prebuilt+Integration+to+Process+Application/1_sgtru5ub)

Apart from the process application, we have also prepared a pre-built integration that is part of the process flow to pass the approved order request's data to ATP for order creatioin.  Let's now download that pre-built integration:

1. Return to the browser tab where you downloaded the exp file in the last section and download two more files.  Or you can click ****+**** to add a new tab and copy and paste the below link again if you closed that tab:

2. Download two files: NEED to DOWNLOAD FILES from OBJECT STORAGE
    - **WW0325_Create_New_Order_01.00.0000.iar** [](./files/WW0325_CREATE_NEW_ORDER_01.00.0000.iar)
    - **wallet_DBAPPINTSHARED** [](./files/wallet_DBAPPINTSHARED.zip)

3. Return to the OIC webpage by clicking the Integration tab at the Chrome browser.  Click the home icon at the top left corner to return to the OIC landing page. 

4. Click the ****Integrations**** option to access the ****Oracle Integration: Integrations**** page. If you can’t see the menu options at the left, click the hamburger menu icon in the upper-left to reveal the menu.

5. Click the ****Integrations**** option to come to this page and find the ****Import**** button at the top right corner.

![](./images/import-integration-step1.png)

6. Import Integration dialog box pops up.  Click ****Choose File**** button to upload the ****iar**** file you just downloaded.  It is located in the ****download**** directory.  Click ****Open**** to complete the upload.

7. Click ****Import and Configure****.  

![](./images/import-integration-step3.png)

8. The Configuration Editor appears and it shows there are two connections that have been pre-created for you in this integration.  One is REST_Trigger and the other one is ATP Invoke.  Now, we need to do some minor configurations before they can be used.

![](./images/import-integration-step4.png)

9. Let's start with REST_Trigger connection.  Mouse over this row and click the pencil icon.  Change the Security policy to ****OAuth 2.0 Or Basic Authentication****.  Then test it out by clicking ****Test**** button on the top right corner.  If successful, click ****Save****  and then click ****<**** at the left hand side to return to the Configuration Editor.

10. Now we configure ATP_Invoke connection.  Mouse over this row and click the pencil icon.  Scroll down the pane to the Security section to establish the security settings.  On the right, you will need to add credentials in order to access the ATP instance we prepared.  

![](./images/import-integration-step5.png)

**Perform the necessary configuration:**
    
For the ****Wallet**** fields, we can supply the connection with the database sign in details (the wallet) you established in that section.

11. Click on the ****Upload File**** check box to begin uploading your wallet file.  

12. Select the ****Choose File**** button and the ****Upload File**** dialog appears.

13. At the top of the dialog, it shows you are at the download folder. select ****wallet_DBAPPINTSHARED(2)**** that you have just downloaded into Luna's Download folder earlier.

14. Select your ****Wallet zip file**** and click the ****Open**** button.

15. Click the ****Upload**** button on the ****Upload File**** dialog to upload your database access credentials into your new connection.

16. For the ****Wallet Password**** , enter 
```
DBWelcome12345
``` 
17. For the Database Service Username, enter: 
```
atpc_user
```
18. For the Database Service Password, enter 
```
DBWelcome12345
```
19. Click the ****Test**** button in the upper-right and watch for the “****Connection ATP\_Invoke\_Insert\_Into\_DB was tested successfully****” message to appear in the upper-left corner.

20. Click the ****Save**** button in the upper-right corner to save your new connection.

21. Click the ****<**** button in the upper-left corner to return to the Configuration Editor page.  You should now be able to find that both REST and ATP connections have ****Configured**** status. 

One more step in this section is to activate our integration. .

![](./images/import-integration-step7.png)

22. Mouse over the ****Create New Order integration**** row, click on the one that shows ****Activate**** when it is hovered (it looks like an on/off button). The ****Activate Integration**** dialog appears.

![](./images/oic-activiate-icon.png)

23. Check the below boxes in the Activate Integration dialog that appears:
  - Enable tracing to view integration activity 
  - Include payload

![](./images/import-integration-step8.png)

24. Click the ****Activate**** button in the lower-right corner.

25. When the Activate Integration dialog closes, verify that the integration has been activated:
  - Click the ****Refresh icon**** at the top right corner.
  - See that the ****Active**** status is shown meaning that your integration has been activated and is ready for use. Keep refreshing if the message doesn’t appear.

![](./images/import-integration-step9.png)

26. Click ****<**** at the top left corner to return to Integration mainpage.

That completes the steps to prepare your OIC environment and you are ready to start the Insight Lab.

   **Congratulations!**  Now you have your OIC environment and instance.

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** - 
