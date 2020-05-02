## Prototyping with Node-RED

In this exercise you will learn how to build simple prototypes that integrate with different Watson APIs. A preview of what you are going to build is available at
- https://node-red-demo.eu-de.cf.appdomain.cloud/ui/visual-recognition
- https://node-red-demo.eu-de.cf.appdomain.cloud/ui/tone-analyzer
- https://node-red-demo.eu-de.cf.appdomain.cloud/ui/translator
- https://node-red-demo.eu-de.cf.appdomain.cloud/ui/digit-recognizer

These examples can be used as a basis for wiring together your own prototypes for other use-cases.

### Prerequisites
- Node-RED running locally or provisioned in the Cloud (e.g. IBM Cloud)
- basic knowledge about REST APIs, HTML and JavaScript

### Instructions

#### Step 1 - Import Flows
- Access your Node-RED instance and log in
- Install [Node-RED nodes for IBM Watson services](https://flows.nodered.org/node/node-red-node-watson)
  - Select _Manage palette_ in the main menu
  ![](./screenshots/1.png)
  - Install the `node-red-node-watson` nodes if they are not yet preinstalled (e.g. in IBM Cloud)
  ![](./screenshots/2.png)
- Select _Import_ in the main menu
![](./screenshots/3.png)
- Select the provided [flows.json](./flows.json) file and click _Import_ 
![](./screenshots/4.png)
![](./screenshots/5.png)
- Click _Deploy_ in the upper right corner to save the changes

To verify that it works as expected, try to access the different prototypes with your web browser
- `{protocol}://{node-red-url}/ui/visual-recognition`
- `{protocol}://{node-red-url}/ui/tone-analyzer`
- `{protocol}://{node-red-url}/ui/translator`
- `{protocol}://{node-red-url}/ui/digit-recognizer`

(`{protocol}` is either `http` or `https`, `{node-red-url}` is the hostname of your Node-RED instance (`localhost:1880` or `127.0.0.1:1880` when working locally). You should see different web pages that are not expected to work yet, e.g.
![](./screenshots/7.png)


#### Step 2 - Understand Basics
Click through the different tabs (e.g. Visual Recognition, Tone Analyzer) and review different basic types of Nodes in use. Additional details are available at
- https://nodered.org/docs/user-guide/nodes
- https://cookbook.nodered.org/http/

Try to understand why you were able to open the URLs of the prototypes in the previous steps. 
  
#### Step 3 - Make the examples work
The examples do not work out-of-the box because they integrate with different Watson APIs and the imported flows do not include corresponding credentials or API keys. In this step, you will learn how to connect the example with your own Watson Service instances.

##### Step 3.1 - Visual Recognition
This example makes use of the [Watson Visual Recognition](https://www.ibm.com/cloud/watson-visual-recognition) service. 

- Create an instance at https://cloud.ibm.com/
![](./screenshots/8.png)
- Access the service credentials and note the `apikey` and `url` properties
![](./screenshots/9.png)
- Update the visual recognition node (copy the apikey property to the API Key field and the url property to the Service Endpoint field).
![](./screenshots/10.png)
- Click _Done_ and _Deploy_ your changes
- Try the demo, you should see the classified objects in the result section
![](./screenshots/11.png)

Check the [API documentation](https://cloud.ibm.com/apidocs/visual-recognition/visual-recognition-v3) for details about the response format.


##### Step 3.2 - Tone Analyzer
This example makes use of the [Tone Analyzer](https://www.ibm.com/watson/services/tone-analyzer/) service. 

- Create an instance at https://cloud.ibm.com/
![](./screenshots/12.png)
- Access the service credentials and note the `apikey` and `url` properties
![](./screenshots/13.png)
- Update the tone analyzer v3 node (copy the apikey property to the API Key field and the url property to the Service Endpoint field).
![](./screenshots/14.png)
- Click _Done_ and _Deploy_ your changes
- Try the demo, you should find the matching document and sentence tones in the result section
![](./screenshots/15.png)

Check the [API documentation](https://cloud.ibm.com/apidocs/tone-analyzer) for details about the response format.

##### Step 3.3 - Translator
This example makes use of the [Watson Language Translator](https://www.ibm.com/watson/services/tone-analyzer/) service. 

- Create an instance at https://cloud.ibm.com/
![](./screenshots/16.png)
- Access the service credentials and note the `apikey` and `url` properties
![](./screenshots/17.png)
- Update the language translator node (copy the apikey property to the API Key field and the url property to the Service Endpoint field).
![](./screenshots/18.png)
- Click _Done_ and _Deploy_ your changes
- Try the demo, you should be able to translate texts (from German to English).
![](./screenshots/19.png)

Check the [API documentation](https://cloud.ibm.com/apidocs/language-translator) for details about the response format.

##### Step 3.4 - Digit Recognizer
This example requires a deployed model for the MNIST data set. Make sure to work through the [TensorFlow model deployment](../tf-model-deployment) exercise first and note the endpoint URL of the model deployment.

- Update the _Update_ node in the _Global_ tab
![](./screenshots/20.png)
- Fill in the apiKey and instanceId of your Machine Learning service instance and the deploymentEndpointUrl from the previous exercise
![](./screenshots/21.png)
- Click done and deploy
- Try the demo, you should be able to recognize hand-written digits
![](./screenshots/22.png)

The configuration you updated in the _Global_ tab is read from two nodes in the _Digit Recognizer_ tab and used to communicate with the [Watson Machine Learning](https://watson-ml-api.mybluemix.net/#!/Deployments/listAllDeployments) API with REST requests.
![](./screenshots/23.png)
- If you allow unauthenticated access to your flow editor, be aware that everyone can review the API key configured in the _Update_ node.
