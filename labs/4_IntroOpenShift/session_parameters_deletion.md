---
markdown-version: v1
tool-type: instructional-lab
branch: lab-1647-instruction
version-history-start-date: 2022-09-30T07:47:11.000Z
---
# Session Parameters Deletion

**Estimated Time Needed:** 20 minutes

## Objectives

* In this lab, you will delete the below parameters of the `guestbook` image for creating the deployment again in the same session.

- Image Stream
- Service
- Route
- Build Config
- Deployment
- Secret


## Deleting the Image Stream

1. In the **Administrator Perspective** select **Builds** >> **Image Streams**.

2. Click on the 3 dots at the right of the `guestbook` Image Stream and click on **Delete Image Stream**.

![img_stream_deletion](images/img_stream_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Image Stream.

![img_stream_deletion_confirmation](images/img_stream_deletion_confirmation.jpg)


## Deleting the Service

1. In the **Administrator Perspective** select **Networking** >> **Services**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Service**.

![service_deletion](images/service_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Service.

![service_deletion_confirmation](images/service_deletion_confirmation.jpg)


## Deleting the Route

1. In the **Administrator Perspective** select **Networking** >> **Routes**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Route**.

![route_deletion](images/route_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Route.


## Deleting the Build Config

1. In the **Developer Perspective** click on **Builds**.

2. Click on the 3 dots at the right of the `guestbook` Build Config and click on **Delete Build Config**.

![service_deletion](images/service_deletion.jpg)

3. Please select `Delete` from the confirmation prompt that appears to delete the Build Config.


## Deleting the Deployment

1. In the **Developer Perspective** go to **Topology** and click on the `guestbook` deployment.

2. Click on **Actions** and then click on **Delete Deployment**.

![deployment_deletion](images/deployment_deletion.jpg)


## Deleting the Secrets

1. In the **Developer Perspective** click on **Secrets**.

2. Click the **Filter** option. Type the name as **GUESTBOOK** under `Name` and press `Enter` to retrieve the secrets pertaining to the `guestbook` image.

3. Click on the 3 dots at the right of  **guestbook-generic-webhook-secret** and click on **Delete Build Config**. 
![secret_deletion](images/secret_deletion.jpg)

4. Please select `Delete` from the confirmation prompt that appears to delete the secret.

5. Repeat steps 3 & 4 for the **guestbook-github-webhook-secret** & any other `guestbook` secrets.


## Next Steps

- With these steps, the above paramters pertaining to your `guestbook` image will be deleted. You can create the image streams and continue with the labs.

## Additional (Keep/Remove)

- If you do not see any route to your `guestbook` app  after creating the deployment again, please run the below command in the terminal to get the route:

```sh
oc status
```

![oc-status-cmd_for-route](images/oc-status-cmd_for-route.jpg)

- The guestbook app may show a 'Waiting for Database connection' status for some time. You need to wait for sometime for putting the guestbook entries and seeing them appear correctly.

## Author
K Sundararajan

## Changelog
| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 04-10-2022 | 1.0 | K Sundararajan | Initial version created |
