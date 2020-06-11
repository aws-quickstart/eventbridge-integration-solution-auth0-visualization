# eventbridge-integration-solution-auth0-visualization
## Amazon EventBridge Integration Solution for Auth0 Visualization

This Quick Start demonstrates how to capture user events and monitor user behavior by using the Amazon EventBridge partner integration with Auth0. This enables you to gain insights to help deliver a more customized application experience for your users.

![Quick Start architecture for EventBridge Integration Solution for Auth0 Visualization](https://github.com/aws-quickstart/eventbridge-integration-solution-auth0-visualization/raw/master/images/auth0-visualization-arch.png)


To post feedback, submit feature ideas, or report bugs, use the **Issues** section of [this GitHub repo](https://github.com/aws-quickstart/eventbridge-integration-solution-auth0-visualization).

## How it works

1. Events are emitted from Auth0 when a user interacts with the login service on the front-end application.
1. These events are streamed into a custom SaaS event bus.
1. Kinesis FireHose is the target for the events.
1. Kinesis delivers the JSON objects that detail the event to S3.  
1. These objects are captured by a QuickSight data source manifest file and used as datapoints on a QuickSight dashboard. 

Follow the prompts in the deploy process to set the stack name, AWS Region and other parameters.

## Amazon QuickSight manifest file

* {your-s3-bucket-name}: in manifest.JSON, replace this token with your S3 bucket name

## Building the QuickSight dashboard

Before building your first visual you must:

Ensure that QuickSight has permission to access your S3 bucket:

1.	Choose the user profile icon in the top right of the menu bar, then choose Manage QuickSight.
2.	Choose Security & permissions, then choose Add or remove.
3.	Choose the checkbox next to Amazon S3, then select the application bucket, the name contains AuthZeroToEventBridgeActivityLogs. Choose Finish. 

Create a new Data source. 

1.	Go to the QuickSight console and choose Manage data
2.	Choose New data set, then choose S3
3.	Enter auth0UserLogs in the Data source name field, then choose the Upload radio button.
4.	Choose the Folder Icon in the Upload a JSON manifest file field, browse to the example manifest.json file you edited earlier and choose Open, then choose Connect.
5.	Once the dataset has been created, choose Visualize.

## Example QuickSight Visual
To build a visual that shows the different types of log-ins, drag the detail.data.type field onto the visual. Then choose the Pie chart icon from the Visual types section.