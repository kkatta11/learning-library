# View Insight Console

## Task 1: View and Analyze Data in the Insight Console

1. It's time we go back to the Insight model to check how the status looks like for each of the order requests submitted.  Click the ****home icon**** on the top left menu to return to the OIC landing page.

2. Click ****Insight****, then ****Consoles****.

3. When a model is activated, Insight automatically creates an associated console. At the right side of our Insight model - ****Order Request Workflow****, you may notice there is a bar chart under Today's Business Transaction that shows the Active and Completed data in last 24 hours.   
  - ****Active**** in brown represents a healthy status that the last milestone passed was either initial or standard but haven't reached the last milestone for some reason.  
  - While for ****Complete**** in blue, it means the transaction is successful where the instance passed through the terminal milestone.  
  - If you remember that we have approved two order requests and the data were then sent to OIC Integration for creating orders in ATP database.  That means they hit the terminal milestone (i.e. Order Created), so these two entries are marked as Complete in Insight.  
  - For the rejected request, since it got rejected, it was then routed back to the Store Manager to re-submit the form.  So its status is Active (pending for Store Manager to resubmit the request), but not completed as it has yet to hit the terminal milestone. 

Let's click ****Order Request Workflow**** to go into Insight dashboards.
![](./images/insight-image81.png)

4. Insight dashboards help LOB, process owners and business analysts to identify bottlenecks in the process and track key metrics immediately and in real time. To save our customer's time, ****five default dashboards**** on the console page are preconfigured. They display the aggregate state of the business process based on milestones.  Let's quickly walk through them one by one with our seeding data as the examples:

****Milestones Summary****

For the first dashboard shown on the left, the Milestones Summary shows details on the number of times all milestones have been passed within the filter criteria specified (currently set at last 5 days but changeable). The bubble colors correspond to the milestone types and the numbers correspond to the amount of times these milestones have been passed.  In our seeding data set, we created three order requests (green bubble), two of them were approved (blue bubble), 1 was rejected (orange bubble) and two approved ones were successfully turned into created orders at ATP that hit the terminal milestone (purple bubble).  
![](./images/insight-image82.png)
    
From any of those ****milestones****, you can drill across to the instance list. The filter will be set to show only instances (or business transactions) that have passed the selected milestone.  For example, you can double click on the “Request Submitted” milestone and see all three requests' details (i.e. values of the indicators assigned to the selected milestone).
![](./images/insight-image83.png)

Clicking on an ****order number**** opens the single order view with milestones along a timeline. This provides a graphical view of the entire order emphasizing the time taken to move across the various milestones. In a demo/testing environment, the individual milestones are close together, but in a real system they are likely spaced further apart.
![](./images/insight-image84.png)

****Passed Milestones****
This dashboard displays a bar graph view of all milestones passed each day within the filter specified period (currently set at 5 days).  This quickly helps business owners understand which milestones have been passed most often on each day.  In the order request process, this chart provides immediate insight into the number of approved, rejected requests and created orders by order date. Feel free to sumbit more order requests with different order dates, then you will see different groups of milestone bars by date to display on this dashboard.
![](./images/insight-image85.png)

****Active Order requests****
This gives a summary of orders that are still active (no Terminal milestone has been passed yet). This includes those instances that have passed an error milestone like “Request Rejected”, or standard milestones but not reach the terminal milestone.  The chart visualizes where business process are stuck that may potentially need human intervention.  In our use case, the Request Rejected instance as shown on the dashboard will need Store Manager to re-submit the request by providing stronger justification.
![](./images/insight-image86.png)

****Order request Errors****
This displays a pie chart view of the count of business transactions that have passed an Error milestone. In our use case, that is when a request is rejected.
![](./images/insight-image87.png)

****Avg. Order request Completion Time****
It displays a bubble view of the average time it took for a business process to complete, both in case of success (Terminal milestone passed) and failure (Terminal Error milestone passed).  We didn't set Terminal Error milestone in our lab, so the only bubble shows is the Completed one.  The two orders successfully created at the end of the process took an average of 70 seconds.
![](./images/insight-image88.png)

All of the above dashboards have the ability to drill across to the instance or business transaction list.

****Custom Dashboards****
Often business owners will want to track metrics, ratios, and trends on their console that are important to their business, but for which the preconfigured dashboards do not provide clarity.  Insight allows users to do this by creating custom dashboards that can be used to visualize indicators defined in the model and extracted as the application runs. You can add as many custom dashboards as you like.  If you are interested to create one, refer to [*<span class="underline">https://docs.oracle.com/en/cloud/paas/integration-cloud/user-int-insight-oci/create-custom-dashboards.html</span>*](https://docs.oracle.com/en/cloud/paas/integration-cloud/user-int-insight-oci/create-custom-dashboards.html). Once they were created, you will be able to display them by clicking ****All**** button at the top and select ****Custom****. 
![](./images/insight-image89.png)


****Congratulations! This completes all lab exercises for OIC Insight.****

## Learn More



## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** -
