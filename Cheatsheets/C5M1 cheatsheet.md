---
markdown-version: v1
tool-type: instructional-lab
branch: lab-2817-instruction
version-history-start-date: '2022-12-15T12:21:40Z'
---
<img src="/images/IDSN-logo.png" width="200" alt="cognitiveclass.ai logo"  />

##

<div align="center">
<b>Cheat Sheet: Docker CLI</b>
</div>

<br>

<table>
<tr>
<th width="30%">Command</th width="70%"><th>Description</th>
</tr>

<tr>
<td width="30%"><b>curl localhost</b></td>
<td width="70%">Pings the application.
</tr>

<tr>
<td width="30%"><b>docker build</b></td>
<td width="70%">Builds an image from a Dockerfile.
</tr>

<tr>
<td width="30%"><b>docker build . -t</b></td>
<td width="70%">Builds the image and tags the image id.
</tr>

<tr>
<td width="30%"valign="top"><b>docker CLI</b></td>
<td width="70%">
Start the Docker command line interface.
</td>

</tr>

<tr>
<td width="30%"valign="top"><b>docker container rm</b></td>
<td width="70%">
Removes a container.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>docker images</b></td>
<td width="70%">
Lists the images.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>docker ps</b></td>
<td width="70%">
Lists the containers.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>docker ps -a</b></td>
<td width="70%">
Lists the containers that ran and exited successfully.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>docker pull</b></td>
<td width="70%">
Pulls the latest image or repository from a registry.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>docker push</b></td>
<td width="70%">
Pushes an image or a repository to a registry.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker run</b></td>
<td width="70%">
Runs a command in a new container.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker run -p</b></td>
<td width="70%">
Runs the container by publishing the ports.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker stop</b></td>
<td width="70%">
Stops one or more running containers.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker stop $(docker ps -q)</b></td>
<td width="70%">
Stops all running containers.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker tag</b></td>
<td width="70%">
Creates a tag for a target image that refers to a source image.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>docker –version</b></td>
<td width="70%">
Displays the version of the Docker CLI.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>exit</b></td>
<td width="70%">
Closes the terminal session.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>export MY_NAMESPACE</b></td>
<td width="70%">
Exports a namespace as an environment variable.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>git clone</b></td>
<td width="70%">
Clones the git repository that contains the artifacts needed.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud cr images</b></td>
<td width="70%">
Lists images in the IBM Cloud Container Registry.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud cr login</b></td>
<td width="70%">
Logs your local Docker daemon into IBM Cloud Container Registry.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud cr namespaces</b></td>
<td width="70%">
Views the namespaces you have access to.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud cr region-set</b></td>
<td width="70%">
Ensures that you are targeting the region appropriate to your cloud account.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud target</b></td>
<td width="70%">
Provides information about the account you’re targeting.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ibmcloud version</b></td>
<td width="70%">
Displays the version of the IBM Cloud CLI.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>ls</b></td>
<td width="70%">
Lists the contents of this directory to see the artifacts.
</td>
</tr>

</table>

## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>
