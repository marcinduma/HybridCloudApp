# Connectivity Check

## 1. Lab access general description

The lab has been built leveraging multiple cloud environments as following:

- Amazon Web Services
- Google Cloud
- Private intrastructure on-prem

You will have access to Cisco Container Platform GUI, where you will setup new Kubernetes Clusters deployed in AWS, GKE and On-Prem. In the end you will manage your application that will be deployed in 3 different environments. In this lab you will see how to connect microservices together to make whole application work.
Most of the tasks you will do from Linux Jumphost that is running on-premise. From there you will deploy components of your application in Kubernetes Cluster in AWS, GKE and on-premise.

## 2. Cisco dCloud dashboard

The entire lab for the session is built using Cisco dCloud environment. To access it, you need to login to dCloud dashboard first. To do so, open https://dcloud.cisco.com in your browser.

<img src="https://github.com/marcinduma/HybridCloudApp/blob/master/HybridCloudApp/Documentation/images/dCloud-start.PNG" width = 500>

On the right top corner is button to login. To enter dCloud dashboard, please use your CCO account. It's same credentials which you use to access cisco.com resources ie downloading the Cisco software.

Once login to the Cisco dCloud dashboard, change your Data Center to be LON - EMEAR. To do it, click on the button left to your profile - right top corner.

<img src="https://github.com/marcinduma/HybridCloudApp/blob/master/HybridCloudApp/Documentation/images/dCloud-start-frame.png" width = 500>

When moved to correct DataCenter for the session, navigate to "My Hub" section, where you will see your assigned session.

<img src="https://github.com/marcinduma/HybridCloudApp/blob/master/HybridCloudApp/Documentation/images/dCloud-dashboard.PNG" width = 500>

On your session list you will see the one for HOLCLD-2101. Please open "view" to check details, how to login to VPN.

<img src="https://github.com/marcinduma/HybridCloudApp/blob/master/HybridCloudApp/Documentation/images/dCloud-dashboard-view.png" width = 500>

## 3. Cisco dCloud infrastructure access (VPN)

In order to get access to dcloud network, you will get assigned a individual session with  username and password for VPN. Please then use Cisco AnyConnect VPN client from your desktop, to connect to Cisco dCloud network.

### Cisco Anyconnect Mobility Client

Run Cisco Anyconnect VPN client available on your desktop. Check credentials and URL in the dCloud session dashboard.

You’ll need to review and configure the AnyConnect options. After Anyconnect launches, you’ll need to click on the “Configuration” button on the main panel. See image below.

<img src="https://github.com/marcinduma/HybridCloudApp/blob/master/HybridCloudApp/Documentation/images/anyconnect_without_IP.png?raw=true" width = 500>

In case of the issues with certificate, you will need to uncheck the option that says “Block connections to untrusted servers”. Your selection is immediately saved.

![anyconnect settings picture here](https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/anyconnect_settings.png)

Close the Configuration window.

**Enter VPN IP Address as provided in credentials page on your desk or on below screenshot. Then choose “Connect”.**

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/anyconnect_with_IP.png" width = 500>

After a few seconds, you’ll see a new window notifying you of an “Untrusted Server Certificate”. This is expected and not a real issue. Choose “Connect Anyway”.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/anyconnect_accept_cert.png" width = 500>

You’ll see a new window prompting you to provide your Lab’s network credentials. Enter the Username and Password as provided in credentials page. Choose “OK”.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/anyconnect_login2.png" width = 500>

Next you’ll see the main AnyConnect window go through several connection states. When it has completed establishing the connection, AnyConnect will iconify in the Notification Area of the Windows Taskbar. When you have an established VPN connection, the AnyConnect icon will display a symbol of a padlock.  

Your are connected to infrastructure on-prem. 

## 3 Accessing Linux Jumphost

Open PuTTY client (icon available on the desktop). If there is no icon for PuTTY, click start, and type `putty`

Enter following IP address, make sure SSH is the selected protocol.

    Computer: 172.18.0.50
    User name: student<XX>
    _where XX is your lab ID_ ie. student7 or student12

You can find password in credentials page on your desktop.

## 4 Accessing Cisco Container Platform

Cisco Container Platform manages Kuberenetes clusters in the private infrasturcture. You will have access to dedicated instance of Cisco Container Platform, from which you will manage you own Kuberenetes Clusters used later on to deploy application.

Please find login credentials and URL to your CCP instance in credentials page.

> **You can explore CCP through the GUI, but please respect other participants and follow only steps from instruction for changes.**

## 5. Google Cloud access

Open Chrome web browser from your desktop
Go to [http://cloud.google.com](https://cloud.google.com), click on sign-in in the top right corner

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-sign-in.png">

Enter username for your lab pod which you can find in the credentials page. You can change language to your preferred.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-login1.png" width = 500>

Once logged in, click on the `Console` button in the top right corner to open Google Cloud Platform Console.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-console-button1.png">

When you sign-in to Google Cloud admin panel for the first time, you will be asked to accept Terms of Service, provide country of residence and email updates. Please select following options, and click `AGREE AND CONTINUE`

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-accept-terms1png.png" width=500>

Next, you will have to select project - click on the `Select a project`

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-select-project1.png">

In the new window, select project `fwardz001`

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-select-project1-2.png" width=500>

Now you can access Google Kubernetes Engine - a Kubernetes Cluster in the Google Cloud

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-go-gke1.png">

You should see screen with warning about no sufficient rights to see the GKE Cluster object, however, you can still navigate to "Workloads" where you can deploy applications on the GKE Cluster.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/gcp-gke-workloads1.png">

## 6. Amazon Web Services access

From Chrome web browser on your desktop, please open URL [https://fwardzic.signin.aws.amazon.com/console](https://fwardzic.signin.aws.amazon.com/console)

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/aws-login-screen.png">

Enter your credentials that you can find in credentials page.

Once logged in, make sure you will use Frankfurt region (eu-central-1). This is important since VPN is established to that particular region.

<img src="https://raw.githubusercontent.com/pradeesi/HybridCloudApp/master/HybridCloudApp/Documentation/images/aws-region-set.png">