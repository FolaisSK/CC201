<center>
<img src="images/labs_module_1_images_IDSNlogo.png" width = "300">
</center>

# Introduction to Containers, Docker, and IBM Cloud Container Registry

## Objectives
In this lab, you will:
- Pull an image from Docker Hub
- Run an image as a container using `docker`
- Build an image using a Dockerfile
- Push an image to IBM Cloud Container Registry

>> **Note: Kindly complete the lab in a single session without any break because the lab may go on offline mode and may cause errors. If you face any issues/errors during the lab process, please logout from the lab environment. Then clear your system cache and cookies and try to complete the lab.**

**Important:**
You may already have an IBM Cloud account and may even have a namespace in the IBM Container Registry (ICR). However, in this lab **you will not be using your own IBM Cloud account or your own ICR namespace**. You will be using an IBM Cloud account that has been automatically generated for you for this excercise. The lab environment will _not_ have access to any resources within your personal IBM Cloud account, including ICR namespaces and images.

# Verify the environment and command line tools
1. Open a terminal window by using the menu in the editor: `Terminal > New Terminal`. 
>> **Note:If the terminal is already opened, please skip this step.**

<img src="images/env&cmdlinetools_1.png" width='800'> <br>

2. Verify that `docker` CLI is installed.
```
docker --version
```
{: codeblock}

You should see the following output, although the version may be different:

<img src="images/env&cmdlinetools_2.png"> <br>


3. Verify that `ibmcloud` CLI is installed.
```
ibmcloud version
```
{: codeblock}

You should see the following output, although the version may be different:

<img src="images/env&cmdlinetools_3.png"> <br>


4. Change to your project folder. 
>> **Note: If you are already on the '/home/project' folder, please skip this step.**
```
cd /home/project
```
{: codeblock}

5. Clone the git repository that contains the artifacts needed for this lab, if it doesn't already exist.
```
[ ! -d 'CC201' ] && git clone https://github.com/ibm-developer-skills-network/CC201.git
```
{: codeblock}

<img src="images/env&cmdlinetools_5.png"> <br>


6. Change to the directory for this lab.
```
cd CC201/labs/1_ContainersAndDocker/
```
{: codeblock}

7. List the contents of this directory to see the artifacts for this lab.
```
ls
```

{: codeblock}

<img src="images/env&cmdlinetools_6.png">  <br>


# Pull an image from Docker Hub and run it as a container
1. Use the `docker` CLI to list your images.
```
docker images
```
{: codeblock}

You should see an empty table (with only headings) since you don't have any images yet.

<img src="images/pullimg_ctr_1.png"> <br>

2. Pull your first image from Docker Hub.
```
docker pull hello-world
```
{: codeblock}

<img src="images/pullimg_ctr_2.png"> <br>

3. List images again.
```
docker images
```
{: codeblock}

You should now see the `hello-world` image present in the table.

<img src="images/pullimg_ctr_3.png"> <br>

4. Run the `hello-world` image as a container.
```
docker run hello-world
```
{: codeblock}

You should see a **'Hello from Docker!'** message.

There will also be an explanation of what Docker did to generate this message.

<img src="images/pullimg_ctr_4.png"> <br>

5. List the containers to see that your container ran and exited successfully.
```
docker ps -a
```
{: codeblock}

Among other things, for this container you should see a container ID, the image name (`hello-world`), and a status that indicates that the container exited successfully.

<img src="images/pullimg_ctr_5.png"> <br>

6. Note the CONTAINER ID from the previous output and replace the **<container_id>** in the command below with this value. This command removes your container.
```
docker container rm <container_id>
```
{: codeblock}

<img src="images/pullimg_ctr_6.png"> <br>

7. Verify that that the container has been removed. Run the following command.

```
docker ps -a
```
{: codeblock}

<img src="images/pullimg_ctr_7.png"> <br>

Congratulations on pulling an image from Docker Hub and running your first container! Now let's try and build our own image.

# Build an image using a Dockerfile
1. The current working directory contains a simple Node.js application that we will run in a container. The app will print a hello message along with the hostname. The following files are needed to run the app in a container:
- app.js is the main application, which simply replies with a hello world message.
- package.json defines the dependencies of the application.
- Dockerfile defines the instructions Docker uses to build the image.

2. Use the Explorer to view the files needed for this app. Click the Explorer icon (it looks like a sheet of paper) on the left side of the window, and then navigate to the directory for this lab: `CC201 > labs > 1_ContainersAndDocker`. Click `Dockerfile` to view the commands required to build an image.


![Dockerfile in Explorer](images/dockerfile-explorer.png)

>> **You can refresh your understanding of the commands mentioned in the Dockerfile below:**<br>
>> The FROM instruction initializes a new build stage and specifies the base image that subsequent instructions will build upon. <br>
>> The COPY command enables us to copy files to our image. <br>
>> The RUN instruction executes commands. <br>
>> The EXPOSE instruction exposes a particular port with a specified protocol inside a Docker Container. <br>
>> The CMD instruction provides a default for executing a container, or in other words, an executable that should run in your container. <br>


3. Run the following command to build the image:
```
docker build . -t myimage:v1
```
{: codeblock}

As seen in the module videos, the output creates a new layer for each instruction in the Dockerfile.

<img src="images/buildimg_3.png"> <br>

4. List images to see your image tagged `myimage:v1` in the table.
```
docker images
```
{: codeblock}

Note that compared to the `hello-world` image, this image has a different image ID. This means that the two images consist of different layers -- in other words, they're not the same image.

You should also see a `node` image in the images output. This is because the `docker build` command pulled `node:9.4.0-alpine` to use it as the base image for the image you built.

<img src="images/buildimg_4.png"> <br>

# Run the image as a container
1. Now that your image is built, run it as a container with the following command:
```
docker run -p 8080:8080 myimage:v1
```
{: codeblock}

The output should indicate that your application is listening on port 8080. This command will continue running until it exits, since the container runs a web app that continually listens for requests. To query the app, we need to open another terminal window.

<img src="images/run_img_as_ctr_1.png"> <br>

2. To split the terminal, click `Terminal > Split Terminal`.

<img src="images/run_img_as_ctr_2.png"> <br>

3. In the second terminal window, use the `curl` command to ping the application.
```
curl localhost:8080
```
{: codeblock}

The output should indicate that **'Your app is up and running!'.**

<img src="images/run_img_as_ctr_3.png"> <br>

4. In the second terminal window, stop the container. The following command uses `docker ps -q` to pass in the list of all running containers:
```
docker stop $(docker ps -q)
```
{: codeblock}

<img src="images/run_img_as_ctr_4.png"> <br>

5. In the second terminal window, check if the container has stopped by running the following command.
```
docker ps
```
<img src="images/run_img_as_ctr_5.png"> <br>

6. Close the second terminal window, as it is no longer needed.
```
exit
```
{: codeblock}

<img src="images/run_img_as_ctr_6.png"> <br>

In the original terminal window, the `docker run` command has exited and you are able to type commands in that terminal window again.
>>**Note: If you face any issues in typing further commands in the terminal, press Enter.**

<img src="images/run_img_as_ctr_7.png"> <br>


# Push the image to IBM Cloud Container Registry
1. The environment should have already logged you into the IBM Cloud account that has been automatically generated for you by the Skills Network Labs environment. The following command will give you information about the account you're targeting:
```
ibmcloud target
```
{: codeblock}

<img src="images/push_img_1.png"> <br>

2. The environment also created an IBM Cloud Container Registry (ICR) namespace for you. Since Container Registry is multi-tenant, namespaces are used to divide the registry among several users. Use the following command to see the namespaces you have access to:
```
ibmcloud cr namespaces
```
{: codeblock}

You should see two namespaces listed starting with `sn-labs`:

- The first one with your username is a namespace just for you. You have full _read_ and _write_ access to this namespace.
- The second namespace, which is a shared namespace, provides you with only Read Access 

<img src="images/push_img_2.png"> <br>

3. Ensure that you are targeting the region appropriate to your cloud account, for instance `us-south` region where these namespaces reside as you saw in the output of the `ibmcloud target` command.
```
ibmcloud cr region-set us-south
```
{: codeblock}

<img src="images/push_img_3.png"> <br>

4. Log your local Docker daemon into IBM Cloud Container Registry so that you can push to and pull from the registry.
```
ibmcloud cr login
```
{: codeblock}

<img src="images/push_img_4.png"> <br>

5. Export your namespace as an environment variable so that it can be used in subsequent commands.
```
export MY_NAMESPACE=sn-labs-$USERNAME
```
{: codeblock}

<img src="images/push_img_5.png"> <br>

6. Tag your image so that it can be pushed to IBM Cloud Container Registry.
```
docker tag myimage:v1 us.icr.io/$MY_NAMESPACE/hello-world:1
```
{: codeblock}

<img src="images/push_img_6.png"> <br>

7. Push the newly tagged image to IBM Cloud Container Registry.
```
docker push us.icr.io/$MY_NAMESPACE/hello-world:1
```
{: codeblock}

<img src="images/push_img_7.png"> <br>

8. Verify that the image was successfully pushed by listing images in Container Registry.
```
ibmcloud cr images
```
{: codeblock}

<img src="images/push_img_8.png"> <br>

Optionally, to only view images within a specific namespace.
```
ibmcloud cr images --restrict $MY_NAMESPACE
```
{: codeblock}

You should see your image name in the output. Recall from the module videos that we discussed Vulnerability Advisor, which scans images in IBM Cloud Container Registry for common vulnerabilities and exposures. In the last column of the output, note that Vulnerability Advisor is either scanning your image or it has provided a security status, depending on how quickly you list the images and how long the scan takes.

<img src="images/push_img_9.png"> <br>

Congratulations! You have completed the second lab for the first module of this course.

## Changelog
| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 2022-04-08 | 1.1 | K Sundararajan | Updated Lab instructions |
|   |   |   |   |


## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>
