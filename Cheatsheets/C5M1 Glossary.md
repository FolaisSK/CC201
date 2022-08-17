<img src="images/IDSN.png" width="200">

<div align="center">
<b>Introduction to Containers, Kubernetes, and OpenShift</b>
</div>

<div align="center">
Glossary: Container Basics
</div>

<table>
<tr>
<th width="30%">Term</th width="70%"><th>Definition</th>
</tr>

<tr>
<td width="30%"><b>Agile</b></td>
<td width="70%">is an iterative approach to project management and software development that helps teams deliver value to their customers faster and with fewer issues.
</tr>

<tr>
<td width="30%"><b>Client-server architecture </b></td>
<td width="70%">is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters, called clients.
</tr>

<tr>
<td width="30%"><b>A container</b></td>
<td width="70%">powered by the containerization engine, is a standard unit of software that encapsulates the application code, runtime, system tools, system libraries, and settings necessary for programmers to efficiently build, ship and run applications.
</tr>

<tr>
<td width="30%"valign="top"><b>Container Registry</b></td>
<td width="70%">
Used for the storage and distribution of named 
container images. While many features can be built on 
top of a registry, its most basic functions are to store images and retrieve them.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>CI/CD pipelines</b></td>
<td width="70%">
A continuous integration and continuous deployment (CI/CD) pipeline is a series of steps that must be performed in order to deliver a new version of software. CI/CD pipelines are a practice focused on improving software delivery throughout the software development life cycle via automation. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Cloud native</b></td>
<td width="70%">
A cloud-native application is a program that is designed for a cloud computing architecture. These applications are run and hosted in the cloud and are designed to capitalize on the inherent characteristics of a cloud computing software delivery model.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Daemon-less</b></td>
<td width="70%">
A container runtime that does not run any specific program (daemon) to create objects, such as images, containers, networks, and volumes.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>DevOps</b></td>
<td width="70%">
is a set of practices, tools, and a cultural philosophy that automate and integrate the processes between software development and IT teams.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker</b></td>
<td width="70%">
An open container platform today for developing, shipping and running applications in containers. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>A Dockerfile</b></td>
<td width="70%">
is a text document that contains all the commands you would normally execute manually in order to build a Docker image. Docker can build images automatically by reading the instructions from a Dockerfile.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker client</b></td>
<td width="70%">
is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker Command Line Interface (CLI)</b></td>
<td width="70%">
The Docker client provides a command line interface (CLI) that allows you to issue build, run, and stop application commands to a Docker daemon.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker daemon (dockerd)</b></td>
<td width="70%">
creates and manages Docker objects, such as images, containers, networks, and volumes.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker Hub</b></td>
<td width="70%">
is the world's easiest way to create, manage, and deliver your team's container applications. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker localhost</b></td>
<td width="70%">
Docker provides a host network which lets containers share your host’s networking stack. This approach means that a localhost in a container resolves to the physical host, instead of the container itself.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker remote host</b></td>
<td width="70%">
A remote Docker host is a machine, inside or outside our local network which is running a Docker Engine and has ports exposed for querying the Engine API.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker networks</b></td>
<td width="70%">
help isolate container communications.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker plugins</b></td>
<td width="70%">
such as a storage plugin, provides the ability to connect external storage platforms.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Docker storage</b></td>
<td width="70%">
uses volumes and bind mounts to persist data even after a running container is stopped.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>LXC</b></td>
<td width="70%">
LinuX Containers is a OS-level virtualization technology that allows creation and running of multiple isolated Linux virtual environments (VE) on a single control host.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>IBM Cloud Container Registry </b></td>
<td width="70%">
stores and distributes container images in a fully managed private registry. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Image</b></td>
<td width="70%">
An immutable file that contains the source code,
libraries, and dependencies that are necessary for an 
application to run. Images are templates or blueprints 
for a container. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Immutability</b></td>
<td width="70%">
Images are read-only; if you change an image, you 
create a new image.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Microservices</b></td>
<td width="70%">
are a cloud-native architectural approach in which a single application contains many loosely coupled and independently deployable smaller components or services. 
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Namespace</b></td>
<td width="70%">
A Linux namespace is a Linux kernel feature that isolates and virtualizes system resources. Processes which are restricted to a namespace can only interact with resources or processes that are part of the same namespace. Namespaces are an important part of Docker’s isolation model. Namespaces exist for each type of resource, including networking, storage, processes, hostname control and others.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Operating System Virtualization</b></td>
<td width="70%">
OS-level virtualization is an operating system paradigm in which the kernel allows the existence of multiple isolated user space instances, called containers, zones, virtual private servers, partitions, virtual environments, virtual kernels, or jails.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Private Registry</b></td>
<td width="70%">
Restricts access to images so that only authorized 
users can view and use them.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>REST API </b></td>
<td width="70%">
A REST API (also known as RESTful API) is an application programming interface (API or web API) that conforms to the constraints of REST architectural style and allows for interaction with RESTful web services.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Registry</b></td>
<td width="70%">
is a hosted service containing repositories of images which responds to the Registry API.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Repository</b></td>
<td width="70%">
is a set of Docker images. A repository can be shared by pushing it to a registry server. The different images in the repository can be labelled using tags.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Server Virtualization</b></td>
<td width="70%">
Server virtualization is the process of dividing a physical server into multiple unique and isolated virtual servers by means of a software application. Each virtual server can run its own operating systems independently.
</td>
</tr>

<tr>
<td width="30%"valign="top"><b>Serverless</b></td>
<td width="70%">
is a cloud-native development model that allows developers to build and run applications without having to manage servers.
</td>
</tr>

<tr>
<td width="30%" valign="top"><b>Tag</b></td>
<td width="70%">
A tag is a label applied to a Docker image in a repository. Tags are how various images in a repository are distinguished from each other.
</td>
</tr>

</table>


## <h3 align="center"> © IBM Corporation 2022. All rights reserved. <h3/>
