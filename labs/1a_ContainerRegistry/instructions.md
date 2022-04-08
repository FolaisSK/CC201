<center>
<img src="images/labs_module_1_images_IDSNlogo.png" width = "300">
</center>

# Creating an IBM Cloud Container Registry Namespace

## Objectives

After completing this lab, you will be able to:

- Describe the IBM Cloud Container Registry service
- Create a Container Registry namespace

## Lab Overview
In this lab you will create an IBM Cloud Container Registry namespace, which you will use in a subsequent labs.

## Pre-requisites
You will need an IBM Cloud account to do this lab. If you have not created one already, click on this [link](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CC0100EN-SkillsNetwork/labs/IBMCloud_accountCreation/CreateIBMCloudAccount.md.html) and follow the instructions to create an IBM Cloud account.

## About IBM Cloud
The IBM Cloud platform is deployed across data centers around the world. It combines platform as a service (PaaS) with infrastructure as a service (IaaS) to provide an integrated experience. The platform scales and supports both large enterprise businesses and small development teams and organizations.

The platform is built to support your needs, whether it's working only in the public cloud or taking advantage of a multicloud deployment model. IBM Cloud offers a variety of services, including Compute, Network, Storage, Management, Security, Databases, Analytics, AI, and Cloud Paks.

## About IBM Cloud Container Registry namespaces
IBM Cloud® Container Registry provides a multi-tenant, encrypted private image registry that you can use to store and access your container images in a highly available and scalable architecture. The namespace is a slice of the registry to which you can push your images. The namespace will be a part of the image name when you tag and push an image. For example, `us.icr.io/<my_namespace>/<my_repo>:<my_tag>`.

# Create a Container Registry namespace
1. Go to the [IBM Cloud catalog](https://cloud.ibm.com/catalog) page. 

2. In the **Catalog** search box, type <code>Container Registry</code>.

<img src="images/createns_2.png"/>

3. Click on **Container Registry** in the search results.<br>

<img src="images/createns_3.png"/>

4. You can now read about the Container Registry service and visit links for API documentation and docs about how to use the service.<br>

<img src="images/registry-catalog.png" width="600" alt="Registry catalog"/>

5. At the top right, click **Get started**.

<img src="images/createns_5.png"/>

6. Ensure that the location is set to **Dallas**.<br>

<img src="images/registry-location.png" width="600" alt="Container Registry location"/>

7. On the left hand side panel, click the **Namespaces** tab.<br>

<img src="images/registry-namespaces-menu.png" width="300" alt="Container Registry namespaces menu"/>

8. On the right side of the Namespaces panel, click **Create**.

<img src="images/createns_8.png"/>

9. A **Create namespace** panel opens.

<img src="images/createns_9.png"/>

10. In the **Resource group** field, select the name of the resource group you would like this namespace to reside in. For this lab, you can simply leave the selection as **Default**.

<img src="images/createns_10.png"/>

11. In the **Name** field, type a unique name for the namespace. The name must be unique across all users of the Container Registry service in this region.<br>

<img src="images/createns_11.png"/>

12. Click **Create** at the bottom of the panel to create the namespace.

<img src="images/createns_12.png"/>


You now have a namespace (as below) to which you can push images.

<img src="images/createns_13.png"/>

Congratulations! You have completed the first lab for the first module of this course.
