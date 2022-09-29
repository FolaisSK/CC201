---
markdown-version: v1
tool-type: instructional-lab
branch: lab-1641-instruction
version-history-start-date: 2022-09-28T10:22:44.000Z
---
# Session Parameters Deletion

**Estimated Time Needed:** 20 minutes

Provide a brief  Scenario or Overview or a few introductory sentences

## Objectives

* In this lab, you will delete the below parameters of the `guestbook` image for creating the deployment again in the same session.

- Image Stream
- Service
- Route
- Build Config
- Deployment
- Secret


## Deleting the `guestbook` Image Stream

1. In the **Administrator Perspective** select **Builds** >> **Image Streams**.

2. Click on the 3 dots at the right of the `guestbook` Image Stream and click on **Delete Image Stream**.

![img_stream_deletion](images/img_stream_deletion.jpg)

3. Click on **Delete** in the confirmation pop-up.

![img_stream_deletion_confirmation](images/img_stream_deletion_confirmation.jpg)


## Deleting the `guestbook` Service

1. In the **Administrator Perspective** select **Networking** >> **Services**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Service**.

![service_deletion](images/service_deletion.jpg)

3. Click on **Delete** in the confirmation pop-up.

![service_deletion_confirmation](images/service_deletion_confirmation.jpg)

## Deleting the `guestbook` Route

1. In the **Administrator Perspective** select **Networking** >> **Routes**.

2. Click on the 3 dots at the right of the `guestbook` service and click on **Delete Route**.

![route_deletion](images/route_deletion.jpg)

## Deleting the `guestbook` Build Config

1. In the **Developer Perspective** click on **Builds**.











* If you do not see any route to your `guestbook` app  after creating the deployment again, please run the below command in the terminal to get the route:

```sh
oc status
```

![oc-status-cmd_for-route](images/oc-status-cmd_for-route.jpg)



## (Optional) Summary / Conclusion / Next Steps
Add ending info here, if required, and rename the title accordingly. Otherwise, remove this optional section.

## Author(s)
[Author1 Name](optional link to profile) 
[Author2 Name](optional link to profile) 

### Other Contributor(s) 
< Contributor 1 Name >, < Contributor 2 Name >, etc.

## Changelog
| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| yyyy-mm-dd | 0.1 | changer name | Initial version created |
|   |   |   |   |
|   |   |   |   |
