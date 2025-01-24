# Docker Tips and Techniques Guide
  
## Reducing Docker Image Sizes
What's the problem? Well, larger Docker image sizes can lead to...

* Delays in container development and deployment (along with lengthier startup and image transfer periods).
* Overly complex systems (complicates compliance auditing and routine maintenance).
* Excessive build times (an unnecessary burden on project management and CI/CD pipelines).
* Introduction of vulnerabilities/security risks (unused components can increase attack surface for clients and hosts).
* Expensive storage and bandwidth costs (and larger bills for Cloud service utilization).

How does it happen?
  
* Excess dependencies (code libraries and other technologies that are either unused or not necessary in the production environment).
* Higher space base images (instead of using lightweight distros, such as Scratch and Alpine, and their system images).
* Excess layers (ones that could be compressed or removed from images).
* Persistence of data from previous builds (temp files that should be removed from images).

What are some solutions to Docker image size related challenges?

* Separating dependencies by whether they are applicable to runtime or the building process (using a multistage approach to building). 
* Mitigating excess build times by closely monitoring and modifying Dockerfile orders and turning on/applying caching.
  + Likewise, simplifying Dockerfiles can reduce complexity issues. 
* Preparing to test and troubleshoot system images by keeping extra copies that can be modified and otherwise experimented with as-needed.
  + Furthermore, debuggers and compilers/interpreters should be kept *out* of production environments.
* Using official base images from routinely maintained distros.
  + Would still need to regularly audit these images for unneeded components and potential reduction of attack surface.
* Evaluating system compatibility and related requirements prior to moving images from staging areas to production.
  
<hr />

## Docker Volumes

**Definition/Overview:** Docker volumes are files or directories located outside of a container's filesystem. They enable Docker containers to store and manage data, providing data persistence even after a container is removed, otherwise beyond its lifecycle, or stopped.
  
Types of Docker volumes include:

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
  
TODO #1: Add example of compressed Docker image.  
TODO #2: Complete section on Docker Volumes.
