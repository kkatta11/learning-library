# Introduction

## About this Workshop

The purpose of this lab is to familiarize yourself with the **process automation** capabilities of Oracle Integration (OIC). In this lab, you’ll use the Process component of Oracle Integration (OIC) to build a process automation application Mama Maggy’s store managers use to enter order requests. Regional managers use the application to evaluate order requests from store managers. If the requests are approved, orders will be created in the ATP database using an imported integration. 

**Estimated Time**: 1 Hour 30 Minutes

### About the use case for this workshop

Watch this short video that gives an overview of the use case for the process workshop:
[](https://videohub.oracle.com/media/Process+Lab+-+Business+use+case/1_qwlsznhf)

Oracle Cloud Infrastructure Data Integration is a **fully managed, multi-tenant, serverless, native cloud service** that helps you with common **extract, load, and transform (ETL) tasks** such as **ingesting data from different sources, cleansing, transforming, and reshaping that data, and then efficiently loading it to target data sources on Oracle Cloud Infrastructure**. Oracle Cloud Infrastructure Data Integration is a key component of Oracle Cloud Infrastructure that provides a fully managed data integration offering. It is simple, intuitive, fast, scalable, resilient, secure, and managed by Oracle.Mama Maggy, a large pizza chain, has a pizza ingredient inventory order control problem with its 10,000 worldwide stores. Management is demanding a better automated process. Specifically, Mama Maggy wants to automate how stores
order their pizza ingredients and other essentials needed to operate a store. Their current process is manual and completely ineffective as reflected by these comments we have heard from our internal champions at Mama Maggy:

  - "Submitting order requests takes too much time for store managers."

  - "Order requests are not being promptly evaluated by regional managers."

  - "Evaluating order requests is cumbersome for our regional managers."

  - "Transforming order requests into approved orders in the backend system is a manual, error-prone process."

The solution is to provide an automated process for store managers to efficiently enter their order requests and have visibility into order status during the approval process. The new system will also provide regional managers with a structured approach to approve or disapprove order requests making the process faster. Once an order request has been
approved, the new process automation solution is to interact with a backend system in the cloud to create a new order. In these labs, the backend system will be a cloud-based database rather than a SaaS system.

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
      
      The solution will provide the following business values for Mama Maggy:
      
    - Lower costs: more efficient entry and evaluation of order requests

    - Better efficiency: faster entry of order requests and faster evaluations

    - Lower error rates: approval of order requests automatically results in orders being created in the backend system

    - Enhanced visibility: status of in-process order requests is constantly available

### Objectives

* Need to complete


## Learn More

Search for **Oracle Integration (Application Integration)** if you are interested to learn how to build a new OIC integration from scratch. 

## Acknowledgements

* **Author** - 
* **Contributors** -  
* **Last Updated By/Date** - 
