# Publish Process Application

## Task 1: Publish and Activate the Process Application

Given all the changes we made to the process application, it is time to publish and activate the process, so we can send data to the process flow and integration for testing purpose.

1. Click the drop-down field at the top right corner, select ****Processes**** this time. 
![](./images/insight-image73.png)

2. Click the ****Publish**** button at the top of the window.
![](./images/insight-image74.png)

3. In the ****Publish Application dialog**** that pops up, enter an explanation in the Comments fields: 
```
This version of process application includes an Insight model.
```

4. Click the ****Publish**** button in the lower-right corner. 
![](./images/insight-image75.png)

5. There is no feedback when the publishing is done. However, wait about 15 seconds before proceeding.

After you publish, you need to activate the process application so it is available for use:

6. Click on the ****Test**** option at the top right of the window. 

7. Click the ****Activate**** button in the ****blue box****. 
![](./images/insight-image76.png)

8. A pop-up window appears.  Make sure the ****Add me to All Roles**** box is checked.  This enables you to take the roles of both Store Manager and Regional Manager when we come to the testing in a minute.

![](./images/activate-to-test-screen.png)

9. Click ****Activate****. You should then see a little pop-up saying ****Application Activated Successfully****.  Your process application is now ready for testing.

> **NOTE:** It is also likely that you encounter an error message about the non-existence of wire target. ![](./images/insight-error.png)  Let's fix it.  Close all pop-up windows first.  Click **Request Evaluation** tab on the bar above to return to the workflow diagram.  Click **Request Submitted milestone** and then **Open Data Association** to display the data mapper.  In the first field on the left column (i.e. your syntax "model-id:identifier-id:" + identifier-value), delete the empty spaces before and after **+**.  ![](./images/insight-errorfix.png)  Click **Apply** and save it.  Go publish and activiate the app again by following the step 2 to 9 above.

## Task 2: Test the Process Application to Start Collecting Metrics

Let’s now perform an end-to-end test of your process application by assuming the ****Store Manager**** and ****Regional Manager**** roles. This allows Insight model to collect metrics from the application. We are going to submit ****three order requests**** in the role of Store Manager via the application and make ****two approved and one rejected**** on behalf of Regional Manager to see how they will display at Insight Dashboard.

1. Click ****Try in Test Mode**** button at the bottom.

![](./images/insight-image77.png)

You should then be able to find your process application under ****My Apps**** tab. And the ****Testing Mode**** is ****On**** as shown under My Apps.

****Initiate Requests as a Store Manager****

As said, we will submit three order requests.

2. Initiate your Order Request Processing application:
    
      - Click on your process application.

![](./images/process-app-under-my-apps-screen.png)

  - Notice that your ****InitiateRequest form**** displays for the store manager to enter an order request.

  - Submit a new order request as a store manager by entering the values in the web form that has appeared:
    
      - Order ID: ****\<insertYourInitialsHere\>001**** (e.g. AB001)

  NOTES:

  - The Order ID must be unique since ****orderID**** is the unique identifier for the Insight model to correlate data that pass through different milestones for each instance.

  - The Order ID ****must not exceed 8 characters in length**** since that is the maximum length for the ****orderID**** column in the ORDERS table in ATP.

  - Order Date: Select ****today’s date**** by clicking on the ****Select Date icon**** at the right of the field and picking it from the popup calendar.

  - Store ID: ****10****

  - Stock ID: ****10****

  - Quantity to Order: ****100****

  - Estimated Cost: ****$200****

  - Initiator Comments: leave it blank

  - Click the ****Submit**** button (highlighted above) in the upper-right corner of the form to move the process instance along its way in the process flow. You are returned to the ****My Apps**** window.

![](./images/insight-image78.png)

You are done with the first order request submission. Click your process application again and do two more submissions using the following sample data:

****2nd order request****:
  - Order ID: ****\<insertYourInitialsHere\>002**** e.g. AB002 (must be different from the first one you entered)
  - Order Date: Select ****today’s date**** by clicking on the ****Select Date icon**** at the right of the field and picking it from the popup calendar.
  - Store ID: ****12****
  - Stock ID: ****15****
  - Quantity to Order: ****200****
  - Estimated Cost: ****$200****
  - Initiator Comments: Leave it blank
  - Click ****Submit****

****3rd order request****:
  - Order ID: ****\<insertYourInitialsHere\>003**** e.g. AB003 (must be different from the previous two you entered)
  - Order Date: Select ****today’s date**** by clicking on the ****Select Date icon**** at the right of the field and picking it from the popup calendar.
  - Store ID: ****14****
  - Stock ID: ****12****
  - Quantity to Order: ****50****
  - Estimated Cost: ****$150****
  - Initiator Comments: Leave it blank
  - Click ****Submit****

After submitting three order requests, here is where we are in the process now as the application is waiting for the regional manager's evaluation at the Approve Request activity:

![](./images/image104.png)


****Work a Task As a Regional Manager****

3. Recall that our process application has a form (****EvaluateForm****) created for this Approve Request human activity. Use it now, as a regional manager, to approve or reject the new order requests you have just submitted:
  - Click the ****My Tasks**** option on the left menu.
  - See that, since you are also in the Regional Manager role, there are three tasks listed that require your evaluation:

![](./images/insight-image79.png)

4. Let's approve the top two requests while rejecting the last one at the bottom. Click on each requests and do the actions as below:
  - For the two Approved cases, click the ****Approve**** button at the top of the Evaluation Form.
  - For the Rejected case, click the ****Reject**** button instead.  

![](./images/insight-image80.png)


   **Congratulations!**  

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** -
