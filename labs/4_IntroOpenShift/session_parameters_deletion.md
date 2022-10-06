---
markdown-version: v1
tool-type: instructional-lab
branch: lab-1647-instruction
version-history-start-date: 2022-09-30T07:47:11.000Z
---
# Deletion & Redeployment to Openshift

**Estimated Time Needed:** 30 minutes

## Objectives

In this lab, you will delete the below parameters of the `guestbook` image for re-deploying your `guestbook` app again.

- Image Stream
- Service
- Route
- Build Config
- Deployment
- Secret


## Step 1: Deleting the Image Stream

1. In the **Administrator Perspective** select **Builds** >> **Image Streams**.

2. Click on the 3 dots at the right of the `guestbook` Image Stream and click on **Delete Image Stream**.

![img_stream_deletion](images/img_stream_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Image Stream.

![img_stream_deletion_confirmation](images/img_stream_deletion_confirmation.jpg)


## Step 2: Deleting the Service

1. In the **Administrator Perspective** select **Networking** >> **Services**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Service**.

![service_deletion](images/service_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Service.

![service_deletion_confirmation](images/service_deletion_confirmation.jpg)


## Step 3: Deleting the Route

1. In the **Administrator Perspective** select **Networking** >> **Routes**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Route**.

![route_deletion](images/route_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Route.


## Step 4: Deleting the Build Config

1. In the **Developer Perspective** click on **Builds**.

2. Click on the 3 dots at the right of the `guestbook` Build Config and click on **Delete Build Config**.

![service_deletion](images/service_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Build Config.


## Step 5: Deleting the Deployment

1. In the **Developer Perspective** go to **Topology** and click on the `guestbook` deployment.

2. Click on **Actions** and then click on **Delete Deployment**.

![deployment_deletion](images/deployment_deletion.jpg)


## Step 6: Deleting the Secrets

1. In the **Developer Perspective** click on **Secrets**.

2. Click the **Filter** option. Type the name as **GUESTBOOK** under `Name` and press `Enter` to retrieve the secrets pertaining to the `guestbook` image.

3. Click on the 3 dots at the right of  **guestbook-generic-webhook-secret** and click on **Delete Build Config**. 
![secret_deletion](images/secret_deletion.jpg)

4. Please select `Delete` from the confirmation prompt that appears to delete the secret.

5. Repeat steps 3 & 4 for the **guestbook-github-webhook-secret** & any other `guestbook` secrets.


## With these steps, the above paramters pertaining to your `guestbook` image will be deleted from Openshift Console. You can create the image streams and continue further with the labs.


## Author
K Sundararajan

## Changelog
| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 06-10-2022 | 1.0 | K Sundararajan | Initial version created |
