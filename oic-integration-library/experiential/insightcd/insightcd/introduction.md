# Introduction

## About this Workshop

The purpose of this lab is to help you understand the ****Insight capability**** of Oracle Integration (OIC) which provides users with real time visibility and analytics into their process applications and integrations.   We adopt the same use case – Mama Maggy, a large pizza chain ordering pizza ingredients that we use in other two labs : Oracle Integration (Application Integration) and Oracle Integration (Process Automation) to demonstrate the steps to build an Insight model in OIC environment.

  - **What values does OIC Insight bring to you?**
  - **What needs are addressed by OIC Insight?**


**Estimated Time**: 1 Hour 30 Minutes

### About the use case for this workshop

Watch this 4-min video to learn more:
[](https://videohub.oracle.com/media/Why+OIC+Insight/1_j2mn3wic)

**Description of the Business Solution**

****Business Use Case****

Mama Maggy, a large pizza chain, has a pizza ingredient inventory order control problem with its 10,000 worldwide stores. Management is demanding a better automated process. Specifically, Mama Maggy wants to automate how stores
order their pizza ingredients and other essentials needed to operate a store. Their current process is manual and completely ineffective.

The solution is to provide an automated process for store managers to efficiently enter their order requests. The new system will also provide regional managers with a structured approach to approve or disapprove order requests making the process faster. Once an order request has been
approved, the new process automation solution is to interact with a backend system in the cloud to create a new order. Throughout the process, Mama Maggy's management will have full visibility into the order approval, rejection and creation status via real-time dashboards to help them make the right decisions.

Here is the proposed business process flow as shown below:

  - The workflow begins at a ****Submit Request**** start event where the Store Manager uses a web form to provide details for an inventory order request for their store.

  - When the Store Manager is done filling in the web form, they press the ****Submit**** button. This generates a workflow task for the Regional Manager at the ****Approve Request**** human activity.

  - The Regional Manager accepts the task and uses a web form to evaluate the request.

  - If the request looks reasonable:
    
      - The Regional Manager presses the ****Approve**** button on the web form.
    
      - Processing continues into the ****Create Order**** integration activity where an order is created in the backend system (simulated as a database table line item).
    
      - The process then ends at the ****Completed**** end event.

  - If the order request looks unreasonable:
    
      - The Regional Manager enters comments into the web form and presses the ****Reject**** button on the web form.
    
      - The ****Approved?**** exclusive gateway routes the request back to the Store Manager at the ****Resubmit**** human activity.
    
      - The Store Manager accepts the task and uses a Resubmit web form to read the Regional Manager’s comments and to add some additional notes to the request to plead their case.
    
      - When the Store Manager is done editing their request in the Resubmit web form, they press the ****Submit**** button. This generates a workflow task for the Regional Manager at the ****Approve Request**** human activity to review the same order request again. The Accept/Reject process continues as shown above.

![](./images/image1.png)

The creation of the above process flow is covered in the ****Oracle Integration (Process Automation) Lab****. Go search in Luna or Oracle Help Center for it if you are interested to learn to create that process on your own.  In the interest of time, we will provide you a link to download it soon.

**Insight End-to-End Workflow**

This is the last lab of the Mama Maggy use case series.  We develop OIC integration flow in OIC (Application Integration) Lab and a process application in OIC (Process Automation) Lab.  In this lab, you will use OIC Insight capability to create an Insight model that will enable Mama Maggy's management to collect and monitor metrics for the above business process and integration flow.

OIC Insight is very easy to use and it requires no coding. To use Insight to monitor a business process in Oracle Integration, there are ****three**** key tasks to perform.  

Watch this short video to learn more:
[](https://videohub.oracle.com/media/Insight+3-step+Approach/1_knqcwdms)

The high-level workflow is as follows:

- Create an Insight model and define milestones, a unique instance identifier and indicators for it.
- Associate the model to a business process implementation by mapping model milestones to the process.
- Map model milestones to an integration flow.
- Activate and test the model to view and analyze the business process and integration using dashboards.

### Objectives

- Create milestones

- Create an Unique Identifier

- Create dimensions and measures

- Create mappings of insight models to the business process and integration.

- Activate the model and review pre-configurated dashboards


## Learn More

 

## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** - 
