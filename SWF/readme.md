#SWF

#Core Concepts

### Workflow
Workflows coordinate and manage the execution of activities that can be run asynchronously across multiple computing devices and that can feature both sequential and parallel processing.

### Actors
 Actors can be workflow starters, deciders, or activity workers. These actors communicate with Amazon SWF through its API. You can develop these actors in any programming language.

### Starter
A workflow starter is any application that can initiate workflow executions.

### Deciders
A decider is an implementation of a workflow's coordination logic. Deciders control the flow of activity tasks in a workflow execution. Whenever a change occurs during a workflow execution, such as the completion of a task, a decision task including the entire workflow history will be passed to a decider. When the decider receives the decision task from Amazon SWF, it analyzes the workflow execution history to determine the next appropriate steps in the workflow execution. The decider communicates these steps back to Amazon SWF using decisions.

### decision
A decision is an Amazon SWF data type that can represent various next actions.

### Task

Amazon SWF interacts with activity workers and deciders by providing them with work assignments known as tasks. There are three types of tasks in Amazon SWF:

- **Activity task** – An Activity task tells an activity worker to perform its function, such as to check inventory or charge a credit card. The activity task contains all the information that the activity worker needs to perform its function.
- **Lambda task**     – A Lambda task is similar to an Activity task, but executes a Lambda function instead of a traditional Amazon SWF activity. For more information about how to define a Lambda task, see AWS Lambda Tasks.
- **Decision task** – A Decision task tells a decider that the state of the workflow execution has changed so that the decider can determine the next activity that needs to be performed. The decision task contains the current workflow history.


### Decoupling
Amazon Simple Queue Service (SQS) and Amazon Simple Workflow Service (SWF) are the services that you can use for creating a decoupled architecture in AWS. Decoupled architecture is a type of computing architecture that enables computing components or layers to execute independently while still interfacing with each other.

Amazon SQS offers reliable, highly-scalable hosted queues for storing messages while they travel between applications or microservices. Amazon SQS lets you move data between distributed application components and helps you decouple these components. Amazon SWF is a web service that makes it easy to coordinate work across distributed application components.    
