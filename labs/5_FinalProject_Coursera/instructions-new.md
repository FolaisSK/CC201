---
markdown-version: v1
tool-type: theiaopenshift
branch: lab-2240-instruction
version-history-start-date: '2022-11-15T08:43:09Z'
---
::page{title="Final Project"}

<img src="/images/IDSN-logo.png" width="200" alt="cognitiveclass.ai logo"  />

##

## Objectives

In this lab, you will:

- Build and deploy a simple Guestbook application
- Autoscale the Guestbook application using Horizontal Pod Autoscaler
- Perform Rolling Updates and Rollbacks

::page{title="Project Overview"}

## Guestbook application

Guestbook is a simple web application that we will build and deploy with Docker and Kubernetes. The application consists of a web front end which will have a text input where you can enter any text and submit. For all of these we will create Kubernetes Deployments and Pods. Then we will apply Horizontal Pod Scaling to the Guestbook application and finally work on Rolling Updates and Rollbacks.

::page{title="Verify the environment and command line tools"}

1. If a terminal is not already open, open a terminal window by using the menu in the editor: `Terminal > New Terminal`.

> **Note:** Please wait for some time for the terminal prompt to appear.

![](/images/Screenshot1.jpg) <br>

2. Change to your project folder.

>> **Note: If you are already on the `/home/project` folder, please skip this step.**

```
cd /home/project
```

3. Clone the git repository that contains the artifacts needed for this lab.

```
[ ! -d 'guestbook' ] && git clone https://github.com/ibm-developer-skills-network/guestbook
```

<img src="images/new_clone_command.png"/> <br>

4. Change to the directory for this lab.

```
cd guestbook
```

5. List the contents of this directory to see the artifacts for this lab.

```
ls
```

::page{title="Build the guestbook app"}

To begin, we will build and deploy the web front end for the guestbook app.

1. Change to the `v1/guestbook` directory.

```
cd v1/guestbook
```

2. Dockerfile incorporates a more advanced strategy called multi-stage builds, so feel free to read more about that [here](https://docs.docker.com/develop/develop-images/multistage-build/).

Complete the Dockerfile with the necessary Docker commands to build and push your image. The path to this file is `guestbook/v1/guestbook/Dockerfile`.

<details>
<summary>Hint!</summary>
The FROM instruction initializes a new build stage and specifies the base image that subsequent instructions will build upon.<br>
The COPY command enables us to copy files to our image. <br>
The ADD command is used to copy files/directories into a Docker image. <br>
The RUN instruction executes commands.<br>
The EXPOSE instruction exposes a particular port with a specified protocol inside a Docker Container.<br>
The CMD instruction provides a default for executing a container, or in other words, an executable that should run in your container.<br>
</details>

> Copy the code of the completed dockerfile with you. You will be prompted to submit it in the text box in the Peer Assignment.

3. Export your namespace as an environment variable so that it can be used in subsequent commands.
 

```
export MY_NAMESPACE=sn-labs-$USERNAME
```

<img src="images/build_guestbook_3.png"/> <br>

4. Build the guestbook app using the Docker Build command.
<details>

<summary>Hint!</summary>

```
docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1
```

<br>
<img src="images/build_guestbook_4.png"/> <br>

</details>

5. Push the image to IBM Cloud Container Registry.

<details>

<summary>Hint!</summary>

```
docker push us.icr.io/$MY_NAMESPACE/guestbook:v1
```

<img src="images/build_guestbook_5.png"/> <br>

</details>

> **Note:** If you have tried this lab earlier, there might be a possibility that the previous session is still persistent. In such a case, you will see a **'Layer already Exists'** message instead of the **'Pushed'** message  in the above output. We recommend you to proceed with the next steps of the lab.

6. Verify that the image was pushed successfully.

```
ibmcloud cr images
```

![](/images/Screenshot6.jpg) <br>



>📷 Take a screenshot of the output of Step 6 and save it as a .jpg or .png with the filename `crimages.png`. You will be prompted to upload the screenshot in the Peer Assignment.

7. Open the `deployment.yml` file in the `v1/guestbook` directory & view the code for the deployment of the application:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: guestbook
  labels:
    app: guestbook
spec:
  replicas: 1
  selector:
    matchLabels:
      app: guestbook
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      labels:
        app: guestbook
    spec:
      containers:
      - image: us.icr.io/<your sn labs namespace>/guestbook:v1
        imagePullPolicy: Always
        name: guestbook
        ports:
        - containerPort: 3000
          name: http
        resources:
          limits:
            cpu: 50m
          requests:
            cpu: 20m  
  replicas: 1
```

> **Note:** Replace `<your sn labs namespace>` with your SN labs namespace. To check your SN labs namespace, please run the command `ibmcloud cr namespaces`

- It should look as below:

<img src="images/adding-deployment.yml.png"/> <br>

8. Apply the deployment using:

```
kubectl apply -f deployment.yml
```

<img src="images/deployment configuration--after updation.png"/> <br>

9. Open a New Terminal and enter the below command to view your application:

```
kubectl port-forward deployment.apps/guestbook 3000:3000
```

<img src="images/port-forward__inital-guestbook.jpg"/> <br>

10. Launch your application on port 3000. Click on the Skills Network button on the right, it will open the **“Skills Network Toolbox”**. Then click the **Other** then **Launch Application**. From there you should be able to enter the port and launch.

<img src="images/Launch_Application.PNG"/> <br>

11. Now you should be able to see your running application. Please copy the app URL which will be given as below:

![](/images/Screenshot11.jpg) <br>

>📷 Take a screenshot of your deployed application and save it as a .jpg or .png with the filename `app.png`. You will be prompted to upload the screenshot in the Peer Assignment.

12. Try out the guestbook by putting in a few entries. You should see them appear above the input box after you hit **Submit**.

::page{title="Autoscale the Guestbook application using Horizontal Pod Autoscaler"}

1. Autoscale the Guestbook deployment using `kubectl autoscale deployment`

<details>

<summary>Hint!</summary>

```
kubectl autoscale deployment guestbook --cpu-percent=5 --min=1 --max=10
```

<img src="images/autoscale1.jpg"/> <br>

</details>

2. You can check the current status of the newly-made HorizontalPodAutoscaler, by running:

```
kubectl get hpa guestbook
```

The current replicas is 0 as there is no load on the server.

>📷 Take a screenshot of your Horizontal Pod Autoscaler and save it as a .jpg or .png with the filename `hpa.png`. You will be prompted to upload the screenshot in the Peer Assignment.

2. Open another new terminal and enter the below command to generate load on the app to observe the autoscaling (Please ensure your port-forward command is running. In case you have stopped your application, please run the port-forward command to re-run the application at port 3000.)

```
kubectl run -i --tty load-generator --rm --image=busybox:1.35.0 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- <your app URL>; done"
```

- Please replace your app URL in the `<your app URL>` part of the above command.

> Note: Use the same copied URL which you obtained in step 11 of the previous task.

The command will be as below:

<img src="images/app-load-generation.jpg"/> <br>

> **Note:** In case you get a `Load generator already exists` error, please suffix a number after `load-generator` eg. `load-generator-1`, `load-generator-2`.

- You will keep getting an output similar as below which will indicate the increasing load on the app:

<img src="images/load-generation-2.png"/> <br>

> **Note:** Continue further commands in the 1st terminal

3. Run the below command to observe the replicas increase in accordance with the autoscaling:

```
kubectl get hpa guestbook --watch
```

<img src="images/hpa-watch-1.png"/> <br>

4. Run the above command again after 5-10 minutes and you will see an increase in the number of replicas which shows that your application has been autoscaled.

<img src="images/hpa-watch__increased-RS.jpg"/> <br>

>📷 Take a screenshot of your Autoscaler details and save it as a .jpg or .png with the filename `hpa2.png`. You will be prompted to upload the screenshot in the Peer Assignment.

5. Run the below command to observe the details of the horizontal pod autoscaler:

```
kubectl get hpa guestbook
```

<img src="images/get-hpa-final.png"/> <br>

- Please close the other terminals where load generator and port-forward commands are running.

::page{title="Perform Rolling Updates and Rollbacks on the Guestbook application"}

> **Note:** Please run all the commands in the 1st terminal unless mentioned to use a new terminal.

1. Please update the title and header in `index.html` to any other suitable title and header like **<Your name> Guestbook - v2** & **Guestbook - v2**.

<details>
<summary>Hint!</summary>

<img src="images/guestbook-content-updation.png"/> <br>

</details>

2. Run the below command to build and push your updated app image:

<details>
<summary>Hint!</summary>

```
docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1 && docker push us.icr.io/$MY_NAMESPACE/guestbook:v1
```

<img src="images/updated-guestbook__docker-build.png"/> <br>

</details>

>📷 Take a screenshot of your updated image and save it as a .jpg or .png with the filename `upguestbook.png`. You will be prompted to upload the screenshot in the Peer Assignment.

3. Update the values of the CPU in the `deployment.yml` to **cpu: 5m** and **cpu: 2m** as below:

<details>
<summary>Hint!</summary>

<img src="images/deployment.yml__cpu-updation.png"/> <br>

</details>

4. Apply the changes to the `deployment.yml` file.

<details>
<summary>Hint!</summary>

```
kubectl apply -f deployment.yml
```

<img src="images/deployment configuration--after updation.png"/> <br>

</details>

>📷 Take a screenshot of the details of the output of Step 4 and save it as a .jpg or .png with the filename `deployment.png`. You will be prompted to upload the screenshot in the Peer Assignment.

5. Open a new terminal and run the port-forward command again to start the app:

```
kubectl port-forward deployment.apps/guestbook 3000:3000
```

<img src="images/get replicaset--after undo rollout.png"/> <br>

6. Launch your application on port 3000. Click on the Skills Network button on the right, it will open the **“Skills Network Toolbox”**. Then click the **Other** then **Launch Application**. From there you should be able to enter the port and launch.

<img src="images/Launch_Application.PNG"/> <br>

7. You will notice the updated app content as below:

<img src="images/updated_guestbook--browser.png"/> <br>

>📷 Take a screenshot of your updated application and save it as a .jpg or .png with the filename `up-app.png`. You will be prompted to upload the screenshot in the Peer Assignment.

> **Note:** Please stop the application before running the next steps.

8. Run the below command to see the history of deployment rollouts:

```
kubectl rollout history deployment/guestbook
```

<img src="images/rollout-history_1.jpg"/> <br>

6. Run the below command to see the details of Revision of the deployment rollout:

```
kubectl rollout history deployments guestbook --revision=2
```

<img src="images/rollout-history--rev2.jpg"/> <br>

>📷 Take a screenshot of the details of the correct Revision and save it as a .jpg or .png with the filename `rev.png`. You will be prompted to upload the screenshot in the Peer Assignment.

7. Run the below command to get the replica sets and observe the deployment which is being used now:

```
kubectl get rs
```

<img src="images/get_replicaset__before-undo-rollout.jpg"/> <br>

8. Run the below command to undo the deploymnent and set it to Revision 1:

```
kubectl rollout undo deployment/guestbook --to-revision=1
```

<img src="images/undo rollout.png"/> <br>

9. Run the below command to get the replica sets after the Rollout has been undone. The deployment being used would have changed as below:

```
kubectl get rs
```

<img src="images/get replicaset--after undo rollout.png"/> <br>

>📷 Take a screenshot of the output of Step 9 and save it as a .jpg or .png with the filename `rs.png`. You will be prompted to upload the screenshot in the Peer Assignment.

Congratulations! You have completed the final project for this course. Do not log out of the lab environment (you can close the browser though) or delete any of the artifacts created during the lab, as these will be needed for grading.

## Changelog

| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 2022-07-21 | 1.0 | K Sundararajan | Created Lab instructions |
| 2022-07-25 | 1.1 | K Sundararajan | Updated Lab instructions |
| 2022-08-02 | 1.2 | K Sundararajan | Added new IDSN logo |
| 2022-08-04 | 1.3 | K Sundararajan | Updated Lab instructions |
| 2022-08-12 | 1.4 | K Sundararajan | Updated Lab instructions |
| 2022-09-21 | 1.5 | K Sundararajan | Updated screenshot for Git clone command |
| 2022-11-15 | 1.6 | Lavanya Rajalingam | Updated screenshots |

## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>

