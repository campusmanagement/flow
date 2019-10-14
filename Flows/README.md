# What is Microsoft Flow?
  Microsoft Flow is an online workflow service that automates actions across the most common apps and services.
## Flow Triggers and Actions
  Flows have triggers and actions.
### Triggers
  As name suggests, triggers are action which is initiated by an external action which starts a Microsoft flow, for Example: Create/ Update/ Delete a record in CDS can trigger a flow, When one are more messages are received in a Azure Service Bus can trigger a flow etc…
### Actions
  Actions are steps performed after a flow is triggered. Actions process the trigger data, to perform a business action.
## Flow packages (Templates)
  Flows can be created from scratch or import a flow package from another environment as a template and extend the flow meet the functional need.
### Importing Flow templates
  Once Microsoft flow and its basics are understood, one can start a flow from scratch or import a flow package and start from a certain step to extend the flow.
  Steps to follow to Import Flow templates
  1. Download the flow packages from any source.  
  2. Navigate to <B>Flow.microsoft.com<B>  
  3. Select a Desired Environment at the top right corner. 
  4. Click on <B>Import</B> under <B> My Flows </B>
  5. Upload the Downloaded package.
  6. After successful import, extend it as a individual flow.
  7. If the flow needs to be under a Power platform solution, navigate to <B>Make.Powerplatapps.com</B> and click on <B>Solutions</B>
     and select the desired solution. 
  7. Select <B>Add Existing</B>, and then <B>Flow</B> .
  8. Select the uploaded flow and thus it will be part of the desired Solution

### CMC Flow Templates
#### Pre-requisites 
1.  Basic Understanding on Azure Service Bus.
2   Azure Service Bus name space.
3.  Azure Service Bus Queue.
4.  Azure Service Bus Topic.

  CMC flow templates demonstrates how we can use Azure service Bus Queues and Topics in flows to integrate with Campus nexus Student. Campus Nexus student adds the event data to a Azure service Bus Queue/topic.
  
 #### Steps are to be performed after CMC Flow templates are imported in a given Environment.
    1. The Service Bus Connection string needs to be updated.
    2. A desired Queue/ Topic needs to be selected.
    3. If topics is selected then a desired Subscription needs to be selected.
    
  #### Triggers
    In CMC Flow templates, Flow is triggered when one or more message is received in a Azure Service Queue or Topic from Campus Nexus Student.
  #### Actions
    1.  Once the flow is triggered, the message is parsed as Json.
    2.  Parsed Json is used to identify which entity is being processed.
    3.  If there are any validation failure, then the message is pushed to a Dead letter queue.
    4.  If the Data is processed successfully then the Message is completed from the queue. 
    
 Once CMC flow templates are Imported, these flows can be added to a Power platform Solution and extended to perform a desired functionality.
     

