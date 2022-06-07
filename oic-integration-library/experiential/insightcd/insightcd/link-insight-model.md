# Link the Insight Model

## Task 1: Link the Insight Model to the Integration

Video:
[](https://videohub.oracle.com/media/Insight+Lab+-+Link+Insight+to+Integration/1_ekxylqom)

If you completed the previous labs on Integration and Process Automation in the same series, you may notice that the process workflow involves an OIC integration namely ****Create Order**** that passes the data of the approved order requests from the OIC process to the ATP database to create orders in the backend.  From Insight perspective, the way of mapping the Insight model to an integration is different from mapping to the process workflow as we did in last section.  We have two milestones left that require us to map them to this integration in order to track the order approval and order creation activities. They are ****Order Approved**** and ****Order Created****.  In this session, we will focus on this task.
![](./images/Insight-image50.png)

1. Click the ****home icon**** on the top left corner to return to the OIC mainpage.
![](./images/Insight-image51.png)

2. Click the ****hamburger menu**** icon on the left corner to display the navigation pane.

3. Select ****Integrations****, then ****Integrations**** again under the Integration menu.
![](./images/Insight-image52.png)

4. It will then display those integration(s) that you created/imported.  
![](./images/Insight-image53.png)

5. At the right of your integration when it is hovered, there are three circle buttons. Click the hamburger menu icon, then select ****Insight Designer****.  
![](./images/Insight-image104.png)

6. This displays a split view of the integration flow on the left and available Insight models on the right. This is where you will do the mapping of milestones, identifier and indicators.

7. On the Models pane, click ****Order Request Workflow**** to display the milestone list that we created earlier.
![](./images/Insight-image55.png)

8. As a reminder, we have mapped ****Request Submitted**** and ****Request Approved**** milestones in the previous section to the process workflow.  So we have two milestones pending for mapping.  They will be mapped to the integration shown on the left.  

    - From the integration flow on the left, drag the ****Accept_Order_Data_Endpoint**** trigger connection to the ****Request Approved**** milestone on the right to map them.  When the Regional Manager approves an order, the order request form data will be sent to this OIC trigger connection as the first step of creating order in ATP.     
![](./images/Insight-image56.png)
  - Once done, the mapping is reflected on the trigger connection and the Request Approved milestone by a ****green pin****.  And under ****Mappings****, the connection name is listed there.
![](./images/Insight-image57.png)

9. For the last milestone - ****Order Created****, we will map it to another end of integration namely ****Insert_Order_Endpoint**** which is the invoke connection created for connecting the process app to the ATP database to insert data into the order table. When data is captured at this stage, it means an order is successfully created in ATP that completes the entire process.  

    - Drag the ****Insert_Order_Endpoint**** to the ****Order Created**** milestone on the right.  Again, you will see the green pins on both sides when they are mapped. 
![](./images/Insight-image58.png)

  - Click ****Save****

## Task 2: Define Extraction Criteria for Identifier and Indicators in Integrations

After the milestones have been mapped to the integration, the next step is to define extraction criteria for the indicators. This defines how to extract data from the integration variables available at the point when the respective milestone has been mapped.  We have done something similar for indicators when we mapped the first two milestones to the process workflow in the process mapper by using data association function there.  However, in the case of Integration, defining extraction criteria for Indicators is different but simpler.     

1. Notice the orange 5 icon at the top of the models pane indicating that there are 5 alert messages we need to pay attention to. Click it to expose the list.  It shows we are missing the mappings for indicators and identifier.  Let's address them now.
![](./images/Insight-image59.png) 

2. Click on the first alert message - ****Store ID****.  It then shows the status of this indicator by milestones.  For the first two milestones of ****Request Submitted**** and ****Request Rejected****, we completed the mappings for Store ID using the process mapper.  Hence, there is no alert shown in these columns.  Scroll down to ****Request Approved**** and ****Order Created**** milestones, alert messages appear that ask us to define extraction criteria for this indicator.
![](./images/Insight-image60.png)

3. Click the first ****Define extraction criteria**** link under ****Request Approved**** mileston.  

4. This opens the XPath expression builder where we will define the extraction criteria. Click ****Store ID**** in the Source on the left and drag it into the ****Expression**** field or click the ****>**** button.
![](./images/Insight-image61.png)

5. Click on ****Validate**** at the top right. Wait for the successful validation message and click on ****Close**** to return to the Integration canvas.

6. Repeat the same steps for ****Order Created**** milestone. When it is done, the number in the orange circle is reduced from 5 to 4.  It means the ****Store ID**** mapping is complete and we have 4 more indicators and Identifier that need mapping.  Now it should look like this.
![](./images/Insight-image62.png)

7. Click ****Save**** frequently.

8. Repeat the same steps of mapping in XPath expression builder for other indicators and identifier according to the below table:

| ****Indicators and identifier**** | ****Milestones****                     |
| --------------------------------- | -------------------------------------- |
| **Stock ID**                      | **Request Approved**, **Order Created**|
| **Order Date**                    | **Request Approved**, **Order Created**|
| **Order Quantity**                | **Request Approved**, **Order Created**|
| **Order ID**                      | **Request Approved**, **Order Created**|

9. When you finish all mappings, the orange circle will not appear any more.  It would look like this.
![](./images/Insight-image63.png)

This concludes the mapping of milestones and definition of indicators and identifier. Click ****Save**** and then ****Close**** to return to the Integration mainpage.

## Task 3: Re-activate the Insight Model and Update the Process Application

We have completed the mapping for the Insight model to the process application as well as the integration flow.  In order to get them implemented in runtime, we have to re-activate the Insight model.

1. Click the ****Home icon**** on the left pane to return to the OIC landing page. Click the ****hamburger menu**** and select ****Insight****.
![](./images/Insight-image64.png)

2. Click ****Models****, then your Insight model ****Order Request Workflow**** displays.  Since we have made changes to it after it was activated, Insight puts all changes into a new version that marks a ****Configured**** state.  It requires user to re-activate the model in order to implement those changes in the runtime engines. Notice that there is an arrow icon next to it.  Click on it.
![](./images/Insight-image65.png)

3. The configured model is displayed.  Click the ****Activate**** icon to activate it.   
![](./images/Insight-image66.png)

4. The Activate Confirmation window pops up. Click the ****Activate**** button and wait a few minutes.  It will then show the ****Activated**** status when it is done.
![](./images/Insight-image67.png)

5. Since we made changes to the Insight model and reactivated it, this also impacts to our process application as the model is now part of the process workflow.  We need to refresh the process application as well as the integration flow to ensure it will pick up all changes from the latest model. Let's go back to the OIC Process to verify it.  Click ****<**** at the top left corner next to ****Insight****. 
![](./images/Insight-image68.png)

6. On the left navigation pane, select ****Process****, then ****Process Applicatioon****.  Click your process application.
![](./images/Insight-image69.png)

7. Click the drop-down field at the top right corner, select ****Insight****.
![](./images/Insight-image70.png)

8. The linked Insight model shows that an update is available. Click the ****Update definition**** link.
![](./images/Insight-image71.png)

9. This pops up the ****Update Insight Model**** window that shows our Order Request Workflow model.  Click ****Update**** button to confirm the updating action. The ****Update is available**** message disappears when it is done.
![](./images/Insight-image72.png)

10. We need to update the Integration flow too. Click the drop-down field at the top right corner, select ****Integrations****.

11. Choose the tile on the right (WW0325CreateNewOrder), that is the integration we downloaded and configured earlier.  ****Update is available**** message is shown underneath.
![](./images/Insight-image102.png)

12. A pop up window ****Edit the Integration**** displays.  Click ****Update now**** link. 
![](./images/Insight-image103.png)

13. Press ****OK**** button to complete the step.


   **Congratulations!**  

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** -
