## How can I provision a free Node-RED instance on IBM Cloud?

- Access https://cloud.ibm.com/login to log in to IBM Cloud
![](./screenshots/1.png)
- Search for _Node-RED_ and select _Node-RED App_ from the search results
![](./screenshots/3.png)
- Switch to the _Create_ tab and enter details as shown below (choose a nearby region)
![](./screenshots/4.png)
![](./screenshots/5.png)
- Select _Deploy your app_
![](./screenshots/6.png)
- Create an API key via the _New_ button
![](./screenshots/7.png)
![](./screenshots/8.png)
- Choose a region with an existing Cloud Foundry Organization (here: London) or follow the instructions on the right to create one.
![](./screenshots/9.png)
- Choose the host name to make your app available at and click _Next_
![](./screenshots/10.png)
- Click _Create_
![](./screenshots/11.png)
- Switch to the _Delivery Pipeline_
![](./screenshots/12.png)
- Wait until both stages (Build & Deploy) succeeded
![](./screenshots/14.png)
- Your app is now available at the host name you specified in a previous step
![](./screenshots/15.png)
- Access your Node-RED instance (e.g. https://node-red-demo.eu-de.cf.appdomain.cloud/)
![](./screenshots/16.png)
- Configure your Node-RED instance
![](./screenshots/17.png)
![](./screenshots/18.png)
![](./screenshots/19.png)
- Select _Go to your Node-RED flow editor_
![](./screenshots/20.png)
- Log in
![](./screenshots/21.png)
![](./screenshots/22.png)
![](./screenshots/23.png)
![](./screenshots/24.png)

Happy prototyping. 

For other deployment options see also https://nodered.org/docs/getting-started/.
