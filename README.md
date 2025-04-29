# Docker Tips and Techniques Guide
  
#### Table of Contents:

1. [Reducing Docker Image Sizes](#reducing-images)
2. [Docker Volumes](#docker-volumes)
3. [Supplemental Resource](#supplemental)
  
## 1. <a name="reducing-images">Reducing Docker Image Sizes</a>
  
What's the problem? Well, larger Docker image sizes can lead to...

+ **Delays in container development and deployment.**
  - Lengthier startup and image transfer periods) may likewise result.
+ **Overly complex systems.**
  - This complicates compliance auditing and routine maintenance.
+ **Excessive build times.**
  - This causes unnecessary burdens on project management and CI/CD pipelines.
+ **Introduction of vulnerabilities/security risks.**
  - Unused components can increase attack surface for clients and hosts.
+ **Expensive storage and bandwidth costs.**
  - This means larger bills for Cloud service utilization.

How does it happen?
  
+ **Excess dependencies.**
  - Ccode libraries and related technologies that are either unused or not necessary in the production environment.
+ **Higher space base images.**
  - Instead of using lightweight distros, such as Scratch and Alpine, and their system images.
+ **Excess layers.**
  - Ones that could be compressed or removed from images.
+ **Persistence of data from previous builds.**
  - Temp files that should be removed from images.

What are some solutions to Docker image size related challenges?

+ **Separating dependencies into runtime and building process categories.**
  - Using a multistage approach to building). 
+ **Decreasing build times by monitoring/modifying Dockerfile orders and applying caching.**
  - Likewise, simplifying Dockerfiles can reduce *complexity* issues. 
+ **Keeping extra copies of system images for testing and troubleshooting.**
  - Furthermore, debuggers and compilers/interpreters should be kept *out* of production environments.
+ **Using official base images from routinely maintained distros.**
  - Would need to regularly audit images for unneeded components.
    + This could potentially reduce the system's attack surface.
+ **Evaluating system compatibility and requirements.**
  - Doing so *prior* to moving images from staging to production prevents challenges.
  
<hr />

## 2. <a name="docker-volumes">Docker Volumes</a>

**Definition/Overview:** Docker volumes are files or directories located outside of a container's filesystem. They enable Docker containers to store and manage data, providing data persistence even after a container is removed, otherwise beyond its lifecycle, or stopped.
  
*Docker volume types include:*

* **Anonymous Volumes**
  + Docker creates these automatically for storage of volatile (temporary) data.
* **Bind Mounts**
  + These map host directories (any path located on a host system) to container directories, as specified.
* **Named Volumes**
  + Users name these volumes, so that they can be quickly identified when needed for reuse.
  + Unlike with bind mounts...
    - You can expect to find these in Docker's directory.
    - Performance should always be optimized for Docker usage.
    - Specific path setups are not necessarily to port volumes.
  
<hr />

## 3. <a name="supplemental">Supplemental Resource</a>
  
* *[Official Docker Website](https://www.docker.com/)*
  
<hr />
  
TODO #1: Add example of compressed Docker image.  
TODO #2: Complete section on Docker Volumes.
