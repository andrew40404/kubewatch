This document will describe how to install Kubewatch on IBM Cloud using Kubernetes services.

**Step 1 - provision Kubernetes Cluster**

- Click the **Catalog** button on the top
- Select **Service** from the **Catalog**
- Search for **Kubernetes Service** and click on it

  ![installing Kubewatch (1)_html_46d1c04e26ba5eea](https://user-images.githubusercontent.com/5286796/106396369-7ab63700-642d-11eb-803d-854f917fcf39.png)

- You are now at the Kubernetes deployment page. You need to specify some information about the cluster.

- Choose either of the following plans; **standard** or **free**. The free plan only have one worker node and no subnet. To provision a standard cluster. You will need to upgrade your account to Pay-As-You-Go
- To upgrade to a Pay-As-You-Go account, complete the following steps:
- In the console, go to Manage > Account.
- Select Account settings and click `Add credit card`.
- Enter your payment information, click Next, and submit your information
- Choose **classic** or **VPC** , read the docs and choose the most suitable type for yourself

  ![installing Kubewatch (1)_html_4d3a968071544952](https://user-images.githubusercontent.com/5286796/106396367-79850a00-642d-11eb-92cb-ed60e5998b4d.png)

- Now choose your location settings,
- Choose **Geography** (continent)

![installing Kubewatch (1)_html_72496e6b0b2c820d](https://user-images.githubusercontent.com/5286796/106396363-768a1980-642d-11eb-8eef-f5b71e6b24a4.png)

- Choose Single or Multizone. 

> In single zone, your data is only kept on the datacenter while on the other hand with Multizone, it is distributed to multiple zones, thus safer in an unforeseen zone failure
>
> If you wish to use Multizone, please set up your account with VRF
> 

- If at your current location selection, there is no available Virtual LAN, a new VLAN will be created for you
- Choose a Worker node setup or use the preselected one. SSet Worker node amount per zone
- Choose **Master Service Endpoint**. 

> In VRF-enabled accounts, you can choose private-only to make your master accessible on the private network or via VPN tunnel. Choose public-only to make your master publicly accessible. When you have a VRF-enabled account, your cluster is set up by default to use both private and public endpoints.
   
- Give desired **tags** to your cluster, for more information visit tags
- Click **create**
- Wait for your cluster to be provisioned
- Your cluster is ready for usage

**Step 2 Deploy IBM Cloud Block Storage plug-in**

The Block Storage plug-in is a persistent, high-performance iSCSI storage that you can add to your apps by using Kubernetes Persistent Volumes (PVs).

- Click the **Catalog** button on the top
- Select **Software** from the catalog
- Search for **IBM Cloud Block Storage plug-in** and click on it
- On the application page, click in the dot next to the cluster you wish to use
- Click on Enter or Select Namespace and choose the default Namespace or use a custom one (if you get error please wait 30 minutes for the cluster to finalize)
- Give a **name** to this workspace
- Click **install** and wait for the deployment

# **Step 3 Installing Kubewatch on IBM Cloud**

## **Install Kubeapps**

**Requirements:**

- A running Kubernetes cluster, on which you need to have cluster-admin privileges
- A Slack account

**Steps:**

- Congifure 	Stack- 	You 	will need to create a Slack bot and invite the bot to the Slack 	channel in which you want kubewatch to post all the notifications. 	Kubewatch uses webhooks to display notifications

- Create 	a private channel and invite the bot in your channel by 	typing **/invite 	@name_of_your_bot** in 	the Slack message area

- Create 	a kubewatch config map with the Slack token and the channel name. 	You can also modify the flags to configure kubewatch to notify on 	changes to particular types of Kubernetes resources. The below 	configuration only monitors pods and services

- Create 	a service account for kubewatch to interact with the Kubernetes 	resources and assign the relevant privileges through 	a **ClusterRole** and 	a **ClusterRoleBinding**

- Create 	a kubewatch deployment
- Check 	if the pod is running
- view 	the kubewatch container logs 
- Check 	 the 	Slack channel for notifications
- Kubewatch 	will now monitor the cluster and send data to the Slack channel


 


 
