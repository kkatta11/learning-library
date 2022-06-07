# Create an Insight Model

## Introduction

In this section, we will create an OIC Insight model for Mama Maggy's order request process. The Insight model defines what characteristics stakeholders care about, and includes abstractions such as milestones and indicators.

1. Click ****<**** at the top left to display the navigation pane.  Then click on ****Insight**** > ****Models****. 

![](./images/Insight_image1.png)

2. Click on ****Create**** at the top right corner, and enter the following:
  - Name: 
  ```
  Order Request Workflow
  ```
  - Description: 
  ```
  To create Insight dashboards for tracking the order request process.
  ```

![](./images/Insight_image2.png)

3. Click ****Create****. This then opens the Insight model editor.

![](./images/Insight_image3.png)

4. Click on ****Name and Description**** on the right-hand side. Enter the name you want to give to a single instance of the order process model in the ****Business Transaction Label**** field. Enter a valid value e.g. ****Order request****.
 
5. Enter the name you want to give to multiple instances of the order process model in the ****Business Transaction Label**** field. Enter a valid value e.g. ****Order requests****.

![](./images/Insight_image4.png)

6. Click ****Save**** at the top right corner to save the model.

## Task 1: Create Milestones

Watch video:
[](https://videohub.oracle.com/media/Insight+Lab+-+Create+Milestones/1_x5l2kttc)

Milestones are key components in an Insight model. They define points in a business process that represent progress and map to at least one activity in the business process implementation.  Setting up milestones enable us to track those key activities if they are passed or not from the monitoring perspective.  Let's set them up now.

The order request process is started when the request is submitted by the store managers through the web form created in OIC (covered in OIC - Process Automation Lab). The ****Request Submitted**** milestone will be mapped to this point in the implementation and is defined as ****initial****. Every time this milestone is passed, a new instance (order request) is initiated.

For this lab, we will create ****four milestones**** where we would like to map them to different process activities for tracking purpose:
- ****Request Submitted**** - Initial milestone
- ****Request Rejected**** - Error milestone
- ****Request Approved**** - Standard milestone
- ****Order Created**** - Terminal milestone

They will be mapped to the business process as shown below:

![](./images/insight-image90.png)

1. Let's start creating the ****Request Submitted**** - initial milestone which is the first tracking point of the process.  Enter the following in the first milestone box:

  - Name: 
  ```
  Request Submitted
  ```

  - Milestone Type: ****Initial****

  - Description: 
  ```
  Order request initiated by store managers
  ```

![](./images/insight_image5.png)


2. For the last tracking point for the process, the terminal milestone is already pre-defined by Insight Editor.  We need to specify the details though.  Just enter its name and description.  In our use case, ****Order Created**** activity at ATP database is the end of the process.

  - Name: 
  ```
  Order Created
  ```

  - Milestone Type: ****Terminal****

  - Description: 
  ```
  The approved order was successfully created in ATP database.
  ```

![](./images/insight-image6.png)

3. Click on ****Save****. (Note: Remember to save your model often.)

4. We have two other milestones to add between the initial and terminal milestones.  Click on ****+ Add milestone**** to add more.  

![](./images/insight-image7.png)

5. Enter the following in the milestone box:

  - Name: 
  ```
  Request Rejected
  ```
  - Description: 
  ```
  Order request was rejected by the regional manager and it needs to be resubmitted by the store manager.
  ```
  - Milestone Type: ****Error****

Select the radio button for milestone type ****‘Error’****.

This milestone is passed whenever the order request is rejected by the Regional Manager. It is an error milestone as this puts the order request into an unsuccessful state that requires the requestor (i.e. Store Manager) to resubmit request with more justification. It’s not terminal as it can still be remedied. 

![](./images/insight-image8.png)

6. Let's create one more milestone by clicking ****+ Add milestone****

  - Name: 
  ```
  Request Approved
  ```
  - Description: 
  ```
  Order request was approved by the regional manager and sent to ATP database for order creation.
  ```
  - Milestone Type: ****Standard****

This milestone marks the approved status of the order request by the Regional Manager after reviewing it.

![](./images/insight-image9.png)


7. Click ****Save****.


## Task 2: Create Unique Identifier

Every Insight model must have a unique instance identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. Insight uses the unique instance identifier to correlate the actions and data that belong to the same instance (business transaction) of the business process.   For example, a unique instance identifier of ****orderID**** specifies that each unique orderID value is considered to be a separate instance of your business process. Actions with the same orderID value are considered part of the same order, or instance. 

Since our use case is about an order request and creation process, an order is identified through the order number. We will use Order ID as the identifier.

1. Select the ****Identifier**** tab

![](./images/insight-image10.png)

2. In the Identifier section, enter the following values:

  - Name: 
  ```
  Order ID
  ```
  (This indicates the name of the unique identifier)
  - Description: 
  ```
  Unique order number.
  ```
  (This is an optional field which is used to indicate the business relevance.)
  - Milestone: Click on the triangle to display the drop-down, then select ****Request Submitted****. (This indicates which milestone in the business transaction flow the identifier value needs to be captured.)
  - Select a data type: ****String**** (This represents the data type of the value of the identifier being mapped.)

![](./images/insight-image11.png)

3. We need to map the same Identifier to other three milestones as well, so the data/actions associated with it could be correlated to the other milestones when they are passed.  
Click ****Assign to Another Milestone**** button ****three times**** until all milestones are mapped.

![](./images/insight-image12.png)

It should then look like this:
![](./images/insight-image13.png)

4. Click ****Save****.

## Task 3: Create a Data Flow - 1

A **data flow** is a logical diagram representing the flow of data from source data assets, such as a database or flat file, to target data assets, such as a data lake or data warehouse.
The flow of data from source to target can undergo a series of transformations to aggregate, cleanse, and shape the data. Data engineers and ETL developers can then analyze or gather insights and use that data to make impactful business decisions.

You will create a data flow to ingest data from **two source files**, containing Customers (`CUSTOMERS.json`) and Orders (`REVENUE.csv`) information. The data from the files will go through a process of transformations and filtering based on the order status and country code of the customers, and in the end will be loaded to `CUSTOMERS_TARGET` table in Autonomous Data Warehouse.

1. From the **Project Details** page for `DI_Workshop` project, click on **Data Flows** from the submenu.

  ![](./images/click-data-flows.png " ")

2. Click **Create Data Flow**.

  ![](./images/click-create-df.png " ")

3. The data flow designer opens in a new tab. In the Properties panel, for **Name** enter `Load Customers and Revenue Data`, then click **Save**. *Note*: Be sure to save often during design time!

   On the left side of the canvas, you can find the data flow operators which represent input sources, output targets, and transformations that can be used. The Shaping Operators currently available are Filter, Join, Expression, Aggregate, Distinct, Sort, Union, Minus, Intersect, Split and Lookup Operator. From the Operators panel, you can drag and drop operators onto the canvas to design a data flow. Then use the Properties panel to configure the properties for each operator. For more details on Data Flow Operators, please see the following [link](https://docs.oracle.com/en-us/iaas/data-integration/using/using-operators.htm).

   ![](./images/data-flow-name.png " ")

4. You will add the **Source operator**. You add source operators to identify the data entities to use for the data flow. From the Operators panel on the left, **drag and drop a Source operator** onto the canvas.

  ![](./images/source-operator.png " ")

5. On the canvas, select **SOURCE_1 operator**. The Properties panel now displays the details for this operator.

  ![](./images/source-operator-properties.png " ")

6. In the **Details** tab from Properties panel, click Select next to each of the following options to make your selections:

    - For **Data Asset**, select `Object_Storage`.
    - For **Connection**, select `Default Connection`.
    ![](./images/source-selections.png " ")
    - For **Schema**, select your **compartment** and then your **bucket**. For the purposes of this workshop, Object Storage serves as the source data asset, this is why you select your bucket here.
    ![](./images/compartment-bucket.png " ")
    - For **Data Entity**, click on **Browse by name**. Select `CUSTOMERS.json` and then choose **JSON** for the file type.
    ![](./images/select-file.png " ")
    ![](./images/select-entity.png " ")

   In the end, the details for the source operator should look like this:

   ![](./images/source-operator-details.png " ")

7. When you complete your selections for **SOURCE\_1**, the operator name becomes **CUSTOMERS\_JSON**, reflecting your data entity selection. In the Identifier field, rename the source operator to **CUSTOMERS**.

  ![](./images/customers-source.png " ")

8. You will now drag and drop onto the data flow canvas another **source operator**.

  ![](./images/new-source.png " ")

9.  On the canvas, select the **new source operator**. The Properties panel now displays the details for this operator.

  ![](./images/source-operator-properties-new.png " ")

10. You will now fill in the details for this source, in **Properties** panel:

    - For **Data Asset**, select `Object_Storage`.
    - For **Connection**, select `Default Connection`.
    ![](./images/source-selections.png " ")
    - For **Schema**, select your **compartment** and then your **bucket**. For the purposes of this workshop, Object Storage serves as the source data asset, this is why you select your bucket here.
    - For **Data Entity**, click on **Browse by name**. Select `REVENUE.csv` and then choose **CSV**  for the file type. Accept the default values for the remaining items.
    ![](./images/revenue-csv.png " ")

   In the end, your details for this new source operator should look like this:
   ![](./images/csv-source.png " ")

11. When you complete your selections for **SOURCE\_1**, the operator name becomes **REVENUE\_CSV**, reflecting your data entity selection. In the Identifier field, rename the source operator to **REVENUE**.
   *Note*: Be sure to save often during design time!

   ![](./images/revenue.png " ")

12. While you still have the **REVENUE** operator selected, click on **Attributes** tab in Properties panel.
In the Attributes tab, you can view the data entity's attributes and apply **exclude** or **rename** rules to the attributes from their respective **actions icon** (three dots). You can also use the **filter** icon on the Name or Type column to apply one or more filters on the attributes to be excluded.

  ![](./images/prop-attributes.png " ")

13. While you still have the **REVENUE** operator selected, click on **Data** tab in Properties panel. In the Data tab, you can view a sampling of data from the source data entity. Scroll to the right and click on field REVENUE_CSV.CURRENCY to view the **data profile**.

  ![](./images/currency-profile.png " ")

14. Click on the  **Validation** tab from the Properties bar. Here you can check for warnings or errors with the configuration of the source operators. The warning with the message "Complete your data flow by connecting the operators input and output ports. Remove any unused operators from the canvas." will appear, to warn us that the operators in the data flow should be connected to other operators, for the data to flow from one node to the other. Also, the data flow must include at least one source operator and one target operator to be valid.

  ![](./images/validate-revenue.png " ")

15. You will now **filter your source data**. The **Filter operator** produces a subset of data from an upstream operator based on a condition. From the Operators panel, drag and drop a Filter operator onto the canvas.

  ![](./images/canvas-filter.png " ")

16. Connect **REVENUE** source operator to **FILTER_1** operator:
    - Place your cursor on REVENUE.
    - Click the connector circle at the side of REVENUE.
    ![](./images/revenue-operator.png " ")
    - Drag and drop the connector to FILTER_1.
    ![](./images/connect-revenue-filter.png " ")

17. Click on **FILTER_1** on the Data Flow canvas.

  ![](./images/click-filter.png " ")

18. In the Properties panel of FILTER_1, click **Create** for **Filter Condition**.

  ![](./images/click-create-filter.png " ")

19. You will now add your **filter condition**:

    - In the Create Filter Condition panel, enter `STA` in the Incoming attributes search field.
    - Double-click or drag and drop **ORDER\_STATUS** to add it to the filter condition editor.
    ![](./images/filter-condition-edit.png " ")
    - In the condition editor, enter `='1-Booked'`, so your condition looks like the following: `FILTER_1.REVENUE_CSV.ORDER_STATUS='1-Booked'`
    - Click **Create**.
    ![](./images/filter-condition.png " ")

20. The details for **FILTER_1 operator** should now look like this: *Note*: Be sure to save often during design time!

  ![](./images/filter-details.png " ")

21. From the Operators panel, drag and drop a new **Filter operator** onto the canvas after CUSTOMERS. **Connect CUSTOMERS to FILTER_2**.

  ![](./images/new-filter.png " ")

22. In the Properties panel of FILTER_2, click **Create** for **Filter Condition**.

  ![](./images/new-filter-condition.png " ")

23. You will now add your **filter condition** for **FILTER_2**:

    - In the Create Filter Condition panel, enter `COU` in the Incoming attributes search field.
    - Double-click **COUNTRY_CODE** to add it to the Filter condition editor.
    - Enter `='US'`, so your condition looks like the following: `FILTER_2.CUSTOMERS_JSON.COUNTRY_CODE='US'`
    - Click **Create**.

    ![](./images/new-filter-create.png " ")

24. The details for **FILTER_2 operator** should now look like this:

  ![](./images/filter-new-details.png " ")

25. You will now work on the **Data Transformation** part of your Data Flow. In the **Properties** panel for FILTER_2, click the **Data** tab.
All data rows and attributes are displayed. You can use the vertical scrollbar to scroll the rows, and the horizontal scrollbar to scroll the attributes.

  ![](./images/data-tab.png " ")

26. In the **Filter by pattern** search field, enter `STATE*`.
The number of attributes in the table are filtered. Only those attributes that match the pattern are displayed.

  ![](./images/filter-state.png " ")

27. Click the **transformations icon** (three dots) for `FILTER_2.CUSTOMERS_JSON.STATE_PROVINCE`, and then select **Change Case**.

  ![](./images/change-case.png " ")

28. In the **Change Case** dialog:

    - From the **Type** drop-down, select **UPPER**.
    - Do **not** select the check box Keep Source Attributes
    - Leave the **Name** as-is.
    - Click **Apply**.

    ![](./images/change-case-apply.png " ")

29. An **Expression operator** is added to the data flow. In the Properties panel, the Details tab is now in focus, showing the expression details. You can see the generated expression, `UPPER(EXPRESSION_1.CUSTOMERS_JSON.STATE_PROVINCE)`, in the Expressions table.

  ![](./images/expression-operator.png " ")

30. With the new **EXPRESSION\_1** operator selected in the data flow, in the Properties panel, change the name in Identifier to **CHANGE\_CASE**. *Note*: Be sure to save often during design time!

  ![](./images/expression-name.png " ")

31. Click the **Data** tab, and then use the horizontal scrollbar to scroll to the end. **EXPRESSION\_1.STATE\_PROVINCE** is added to the end of the dataset. You can preview the transformed data for EXPRESSION\_1.STATE\_PROVINCE in the Data tab.

  ![](./images/state-province.png " ")

32. From the Operators panel, drag and drop a **new Expression** operator onto the canvas after **CHANGE_CASE** operator. **Connect CHANGE\_CASE to the new Expression**.

  ![](./images/new-expression.png " ")

33. With **EXPRESSION\_1** selected, in the Properties panel, change the **Identifier** to **CONCAT\_FULL\_NAME** and then click **Add Expression** button in the Expressions table.

  ![](./images/add-expression.png " ")

34. In the **Add Expression** panel:

    - Rename the expression to `FULLNAME` in the **Identifier** field.
    - Keep **Data Type** as `VARCHAR`.
    - Set **Length** to `200`.
    - Under Expression Builder, switch from the Incoming list to the **Functions list**.
    - In the **filter by name search field**, enter `CON`. Then locate `CONCAT` under String. You can either search for CONCAT in the functions list yourself, or enter CON to use the auto-complete functionality
    - Enter

    ```
    <copy>CONCAT(CONCAT(EXPRESSION_1.CUSTOMERS_JSON.FIRST_NAME, ' '),EXPRESSION_1.CUSTOMERS_JSON.LAST_NAME)</copy>
    ```

   in the **expression box**.
   You can also highlight a function's placeholders and then double-click or drag and drop attributes from the Incoming list to create an expression.

    - Click **Add**.

    ![](./images/expression-conditions.png " ")

35. The new expression is now listed in the **Expression operator**. You can add as many expressions as you want. *Note*: Be sure to save often during design time!

  ![](./images/final-expression.png " ")

36. After you apply filters and transformations, you can join the source data entities using a unique customer identifier, and then load the data into a target data entity.
To join the data from expression **CONCAT\_FULL\_NAME** with the data from **FILTER\_1**, drag and drop a **Join operator** from the Operators panel onto the canvas next to CONCAT\_FULL\_NAME and FILTER\_1. Connect CONCAT\_FULL\_NAME to JOIN\_1 and then connect FILTER\_1 to JOIN\_1.

  ![](./images/add-join.png " ")

37. Select the **JOIN\_1** operator. **Inner Join** as the join type is selected by default. In the Details tab of the Properties panel, click **Create** next to **Join Condition**.

  ![](./images/create-join-condition.png " ")

38. In the **Create Join Condition panel**:

    - Enter `CUST` in the filter by name search field.
    - You want to join the entities using CUST\_ID and CUST\_KEY. In the editor, enter
    ```
    <copy>JOIN_1_1.CUSTOMERS_JSON.CUST_ID=JOIN_1_2.REVENUE_CSV.CUST_KEY</copy>
    ```
    - Click **Create**.

    ![](./images/join-condition.png " ")

39. Your **Join operator properties** should now look like this:

  ![](./images/join-properties.png " ")

40. From the Operators panel, drag and drop a **Target operator** onto the canvas. Connect JOIN\_1 to TARGET\_1. *Note*: Be sure to save often during design time!

  ![](./images/target-operator.png " ")

41. Select **TARGET_1** operator on the canvas. The details for this operator are now displayed in the **Properties** bar.

  ![](./images/target-properties.png " ")

42. In the **Details** tab of the Properties panel complete the fields accordingly:

    - Leave the default value for **Integration Strategy** as **Insert**.
    - For **Data Asset**, select `Data_Warehouse`.
    - For **Connection**, select `Beta Connection`.
    - For **Schema**, select `BETA`.
    - For **Data Entity**, select `CUSTOMERS_TARGET`.
    ![](./images/target-operator-selections.png " ")
    - For **Staging Location**, select the **Object Storage data asset**, its **default connection** and your **compartment**. Then for **Schema**, select the **Object Storage bucket** that you created before importing the sample data in _Setting up the Data Integration prerequisites in OCI_. Click **Select**.
    ![](./images/staging-location.png " ")

43. The properties details for **CUSTOMERS_TARGET operator** should now look like this:

  ![](./images/target-operator-properties.png " ")

44. To review the Attributes mapping, click the **Map tab**. By default, all attributes are **mapped by name**. For example, CUST\_ID from JOIN\_1 maps to CUST\_ID in the target data entity.

  ![](./images/mappings.png " ")

45. To manually map attributes that are not yet mapped, click the **All** drop-down in the Target attributes table, and then select **Attributes not mapped**. You can do the same in the Source attributes table (for the incoming fields). You can see that there is one attribute that is not mapped, more specifically attribute FULL_NAME from target.

  ![](./images/attributes-not-mapped.png " ")

46. Now drag and drop **FULLNAME** under Source attributes to **FULL_NAME** under Target attributes. All attributes from target are now mapped.

  ![](./images/map-fullname.png " ")

47. Click **View Rules** to filter and view the applied Rules.

  ![](./images/view-rules.png " ")
  ![](./images/view-rules-map.png " ")

48. You have now completed the data flow. Click on **Validate** to see the validation output. There shouldn't be any warnings or errors.

  ![](./images/validate.png " ")

49. To save the data flow, click **Save**.

  ![](./images/save-df.png " ")

## Task 4: Create Dimensions and Measures

Dimensions and Measures are also called indicators. Indicators allow business users to gain insight into a business process, and also allow comparisons between business process transactions (instances), such as each order or service request. They help to quantify the performance of the business, and are used to create dashboards and reports for tracking business metrics.
There are two types of indicators:
- ****Measures**** identify values, which allow the state of the application to be quantified. 
- ****Dimensions**** provide a type of grouping and categorization of applications, allowing for "slicing and dicing" of aggregate measures.
As part of this lab, you will create 3 dimensions (Order Date, Stock ID and Store ID) and 1 measure (Order Quantity).

1. Click on ****Indicators**** tab and then ****Add Dimension****, 
![](./images/insight-image14.png)

2. Enter the details as below:
  - Name: 
  ```
  Order Date
  ``` 
  - Milestone: ****Request Submitted****

3. Click ****Assign to Another Milestone**** three times to get it mapped to the other three milestones as well.

4. Select a data type: ****String****.  It will then look like below:

![](./images/insight-image15.png)

Now you need to add three more indicators by following the above steps with below info:

5. Click ****Add Dimension****
  - Name: 
  ```
  Stock ID
  ``` 
  - Milestone: ****Request Submitted****
  - Data type: ****String****
  - Click ****Assign to Another Milestone**** three times

6. Click ****Add Dimension****
  - Name: 
  ```
  Store ID
  ``` 
  - Milestone: ****Request Submitted**** 
  - Data type: ****String****
  - Click ****Assign to Another Milestone**** three times

7. Click ****Add Measure****
  - Name: 
  ```
  Order Quantity
  ``` 
  - Milestone: ****Request Submitted**** 
  - Data type: ****Integer****
  - Click ****Assign to Another Milestone**** three times


8. Click ****Save****.  Click ****Outline**** tab on the right pane.

Now the outline of the model looks like below.
![](./images/insight-image16.png)

   **Congratulations!**  

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** - 
* **Last Updated By/Date** - 
