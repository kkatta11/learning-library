# Activate the Insight Model

## Task 1: Activate the Insight Model

With the milestones, unique identifier and indicators created, we are ready to activate the Insight model.

1. Click the ****<**** at the top left corner to navigate back to the Insight model list and look for the Order Request Workflow model you defined. 
![](./images/insight-image17.png)

2. Hover over the model and click the activate button.
![](./images/insight-image18.png)

3. Activate Confirmation window pops up.  Click ****Activate**** button to confirm this action.  Activation can take up to 5 minutes, but will likely be faster.

4. If the model is successfully activated, its status should be changed to ****Activated**** with a green dot like this.
![](./images/insight-image19.png)

The model is now active.  However, we have a few more tasks to do before it is able to collect metrics from the process application and integration we created for Mama Maggy.  One of important tasks is to link the model to the process application and integration we built in previous labs.  

In the previous ****Create an unique identifier**** section, you created an identifier called ****Order ID**** that will be used to correlate the various milestones of the same instance that allows Integration Insight to track each order request throughout the business process implementation.  However, in our Mama Maggy use case where its order request and creation process is implemented in BOTH Integrations and Processes (i.e. an OIC process application calls an OIC integration to create an order in ATP), you must set the identifier value using a special syntax:

****"model-id:identifier-id:" + identifier-value****

where:

- model-id and identifier-id are the model ID and unique instance identifier ID, static values specified in the Integration Insight console manifest
- identifier-value is the unique instance indentifier for the model, a dynamic value that resolves to a unique value for each business transaction 

Let's construct this syntax now using the above format.  

5. On the left pane, click ****Consoles****.
![](./images/insight-image20.png)

6. Select ****Order Request Workflow****. It brings you to the dashboard page but since we haven't done the mapping yet, so no data is collected to show on the dashboards.  Click on ****Console Manifest**** at the top right corner.
![](./images/insight-image21.png)

7. The Console Manifest dialog displays the ****console name and IDs**** for the associated model and dashboards. Expand the ****Filter Details**** list to view the IDs for the milestones, unique instance identifier, and indicators (dimensions and measures).
![](./images/insight-image22.png)

8. Open a notepad or Text Editor in Luna.  
![](./images/texteditor.png)

9. Find out the info for the following two IDs from the dialog box and copy it down into the notepad:
  - ****model-id**** 
  - ****identifier-id****
  - ****identifier-value**** is ```initiateFormDataObject.orderID``` 

Here is the place where you can locate the model-id of your own model.  Yours won't be the same as shown here. 
![](./images/Insight-image23.png)

And this is the identifier-id after you expand the ****Filter Details**** and find Identifier section (i.e. Order ID as defined for our model earlier)
![](./images/Insight-image24.png)

****identifier-value**** is ```initiateFormDataObject.orderID``` that is same for all of us.

10. We copy and paste those info into this syntax format: "model-id:identifier-id:" + identifier-value to form your own. Keep it on your notepad and you will use it when we come to the data association section.

For example: ```"OrderReques_ktbdpueP:OrderID_DVbgibza:" + initiateFormDataObject.orderID```  (NOTE: you must have your own syntax as the model id and identifier id are unique.)

![](./images/Insight-image91.png)

11. Close the Console Manifest dialog.  We are now ready to link the Insight model to the process application in next section.

## Task 2: Link the Insight Model to the Process Application

Watch this 4-min video to learn more:
[](https://videohub.oracle.com/media/Insight+Lab+-+Link+Insight+to+Process+Application/1_8yddksvh)

1. Click ****<**** on the top left corner to return to the Insight main page.  

2. Click ****<**** once again to display the OIC navigation pane.  Select ****Processes**** > ****Process Applications****, the Mama Maggy process app displays. 

![](./images/insight-image26.png)

3. Click on the process application you built or downloaded earlier.  On the top right, click on the drop down box and select ****Insight****.
![](./images/insight-image27.png)

4. Click ****Link**** button in the middle of the page.

5. The Link to Insight Models dialog is displayed, listing activated Integration Insight models available for linking. Select the Order Request Workflow model we created earlier and click ****Link**** button at the bottom.
![](./images/Insight-image28.png)

6. Now, your insight model is successfully linked to the process application as you see it displayed under your process name.
![](./images/insight-image29.png)

Let's retrieve it from the process application and place its milestones into the process, so the data can be collected for tracking purpose.

7. On the top right, click on the drop down box and select ****Processes****.
![](./images/insight-image30.png)

8. Click ****Request Evaluation**** to display the process flow that resides in the process application.
![](./images/Insight-image31.png)

9. In the structured editor's BPMN palette, notice an Insight category is listed after linking an Integration Insight model. Click to expand it, and you'll see the Order Request Workflow Insight model linked to the process application.
![](./images/Insight-image92.png)

10. To link the Insight model to a process application, simply drag the model to a point(s) on the process flow where you want to extract data for analysis in Integration Insight dashboards.  We are going to place the model in two tracking points for two of our milestones: ****Request Submitted**** and ****Request Rejected****.
Let's do the first one.  Drag the model to right below ****Submit Request icon****.

![](./images/Insight-image32.png)

11. Double-click the default name of the Insight model to rename it. This is highly recommended to reflect the milestone to which each Insight element is mapped. We name it ****Request Submitted**** that corresponds to our initial milestone as defined in our Insight model. 
![](./images/Insight-image33.png)

12. For each Insight element on the process flow, set the properties and data association (the data you want to extract for the metrics you want to analyze). Click on the Insight model icon, then click on the hamburger icon.
![](./images/Insight-image34.png)

13. Select ****Open Properties**** to open the properties pane.

14. Ignore the Is Draft checkbox. It does not apply to Integration Insight models. From the ****Insight Model**** list, leave the selection as the current model i.e. ****OrderRequestWorkflow****.

15. For ****milestone file****, select ****Request Submitted****.  This is the first milestone we want to keep track and extract data for analysis when it is passed.
![](./images/Insight-image35.png)

16. Click the down arrow icon below the BPMN pane to close the properties pane.
![](./images/Insight-image36.png)

17. Click ****Request Submitted**** Insight element again.  Then click hamburger icon and select ****Open Data Association**** to open the Data Association editor.

18. In the Data Objects pane on the left, click ****RequestEvaluation****, then ****Data Object**** and ****initiateFormDataObject****. It shows a list of values that will be entered by Store Manager via the process application form when he/she requests for an order of pizza ingredients. We will pass these values to the Insight model whenever the order request hits the Request Submitted milestone. 
![](./images/Insight-image37.png)

19. On the right hand side where shows the Insight element ****Request Submitted**** we just added to the process, click ****body**** to expand the list that shows those data objects that pertain to the selected milestone. They are the indicators you defined when the model was created earlier.  You'll pass values from the store manager's request form to these objects.  Hence, we need to match those data fields between these two columns once, so OIC will automatically do for us afterwards.
![](./images/Insight-image38.png)

20. Simply drag and drop fields from ****body**** (on the right) to the ****initiateFormDataObject**** (on the left), map the matching fields so data transfer occurs at runtime. 

21. Start from the ****identifier**** on the right, drag it into the ****Request Submitted**** column.  
![](./images/Insight-image39.png)

22. Open your notepad and copy and paste the syntax you prepared to the field under ****Request Evaluation**** column.
![](./images/Insight-image40.png)
![](./images/Insight-image41.png)

23. Now drag and drop the other fields from both sides according to the following table:

| **initiateFormDataObject**     | **body**            |
| ------------------------------ | ------------------- |
| **orderDate**                  | **orderDate**       |
| **orderID**                    | **orderID**         |
| **quantityToOrder**            | **orderQuantity**   |
| **stockID**                    | **stockID**         |
| **storeID**                    | **storeID**         |

It should look like this:
![](./images/Insight-image42.png)

24. As you map, you will encounter some error messages that indicate type mismatches between the Data Object column and the Request Submitted column. You will need to do some casting (data conversion).

  - You’ll use the ****string()**** function to convert the ****date****, ****stockID**** and ****storeID**** data type to ****string****.
  - The ****int()**** function is used to convert the ****quantityToOrder**** data to ****integer****.
  - To implement these functions, click in the cells where shows the error message to add the ****string**** or ****int**** function calls and to surround the data field with the ****parentheses****. Press ****Return**** after you perform each edit.

If you do it right, the error messages will disappear and all mapping lines will turn green as below:
![](./images/Insight-image43.png)

25. Click ****Apply**** in the upper-right corner to save your mappings.

26. When the process modeling canvas reappears, click ****Save**** in the upper-right corner.  We have completed the setup of the first Insight model that has been mapped to the Request Submitted milestone!  Let's add another insight model for tracking the ****Request Rejected**** scenario by following similar steps.

27. Drag the Order Request Workflow Insight model from the BPMN palette on the right to the ****No**** path.  For those order requests got rejected by Regional Manager will route to the ****No**** path that allows Store Manager to re-submit the request after providing additional information.
![](./images/Insight-image44.png)

28. Double-click the default name of the Insight model to rename it as ****Request Rejected****.

29. Select ****Open Properties**** to open the properties pane. From the ****Insight Model**** list, make sure it shows ****OrderRequestWorkflow**** as default.

30. For ****milestone file****, select ****Request Rejected****.  This is the second milestone we want to keep track and extract data for analysis.
![](./images/Insight-image45.png)

31. Click the down arrow icon below the BPMN pane to close the properties pane.

32. Click ****Request Rejected**** Insight element again.  Then click hamburger menu icon and select ****Open Data Association**** to open the Data Association editor.

33. In the Data Objects pane on the left, click ****RequestEvaluation****, then ****Data Object****. 

34. On the right hand side, it shows the Insight element ****Request Rejected**** we've added to the process, click ****body**** to expand the list that shows those data objects that pertain to the selected milestone. They are the indicators you defined for Request Rejected milestone.  Again, we need to match those data fields between these two columns to get the data across in the run-time.

35. Let's start the mapping from the right side.  Drag ****Identifier**** to the ****Request Rejected**** column.  On the left, copy and paste the syntax from your note pad to the field under ****Request Evaluation**** to complete this mapping.

36. Under Data Object on the left pane, there is an item called TaskOutcomeDataObject which stores the outcome of the evaluation (i.e. APPROVE or REJECT based on the button that the regional manager clicks on the evaluate form as defined in the process). We have to map this item in order to enable the data flow to the **No** path from the Approved? exclusive gateway element and so the Insight model can capture data for those rejected requests.     
    - Drag ****TaskOutcomeDataObject**** to the left box under ****Request Evaluation**** column.
    - Drag ****orderID**** to the right box under ****Request Rejected**** to form the mapping.

It should look like this:
![](./images/Insight-image46.png)

37. There are still some indicators like orderDate and order quantity on the right pane under ****Request Rejected**** that require mappings in order for the Insight model to capture the data from the evaluation form shown on the left.  On the left pane, click ****evaluateFormDataObject**** to expand the list that shows the values stored in the EvaluateForm used by the regional manager to evaulate the order request.  
![](./images/Insight-image47.png)

38. Drag and drop the below items according to this table:

| ****evaluateFormDataObject**** | ****body****        |
| ------------------------------ | ------------------- |
| **orderDate**                  | **orderDate**       |
| **orderID**                    | **orderID**         |
| **quantityToOrder**            | **orderQuantity**   |
| **stockID**                    | **stockID**         |
| **storeID**                    | **storeID**         |

Here is what you should have done:
![](./images/Insight-image48.png)

39. Error messages pop up again for couple of mappings as you experienced in previous task.  Use the ****string()**** function to convert the ****date****, ****stockID**** and ****storeID**** data type to ****string****. The ****int()**** function is used to convert the ****quantityToOrder**** data to ****integer****.  Click in the cells where shows the error message to add the ****string**** or ****int**** function calls and to surround the data field with the ****parentheses****. Press ****Return**** after you perform each edit.

40. This shows the completed mappings if you got them correctly.
![](./images/Insight-image49.png)

At this point, you have completed the linking of two Insight milestones to the process application. 
![](./images/Insight-image93.png) 

41. Click ****Apply**** in the upper-right corner to save your mappings. 

42. Click ****Save**** when you return to the process modeling canvas.


   **Congratulations!**  

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** -
