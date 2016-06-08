---
author: fritzvd
categories:
- development
- node
- nodeconf15
date: 2015-06-23T18:45:44Z
guid: http://blog.technokrat.nl/?p=638
id: 638
title: Containers (Docker, LXC) @ nodeconf 2015
url: /2015/06/23/containers-docker-lxc-nodeconf-2015/
cover: https://farm4.staticflickr.com/3711/18845642595_183c29c423_q_d.jpg
---

### Containers, like the ones you put sundries in?

Linux Containers (LXC) have been a hot new topic over the last 2 years. The easiest way to understand a container is to compare it with a Virtual Machine (VM). You can run a VM on your machine and it will pretend to be a computer inside a computer. It will emulate hardware so it can run an Operating System (OS) within your computer. When you start a VM you have to choose how much of your memory and CPU it can take up, and once you start the machine that piece of memory and CPU are designated to the VM (the guest) and lost to your computer (the host).

When you start a LXC however, you can start a box without it having to emulate machinery, it will create a &#8220;contained&#8221; environment, sharing the stuff that is common (the Linux kernel), and fork out a platform to run your processes and OS (any Linux variant) on. Running that container then, doesn&#8217;t take that much extra memory, because it doesn&#8217;t need to run an entire machine, with hardware and OS. But just the part that is different from the host. This also means bootups of a new container are close to instantaneous.

### Docker

One of the products that was born as a result of this kernel API is: Docker. Docker makes it possible to create a container that you can provision and deploy your app on, and commit those changes to the box. It&#8217;s like git for machines. All the changes to your box can be committed. Once you think your container is ready for deployment you can take the whole image and deploy that on a server. Instead of deploying your code, you now deploy your container.

[<img src="http://blog.technokrat.nl/wp-content/uploads/2015/06/62260701-300x200.jpg" alt="yo dawg" width="300" height="200" class="alignnone size-medium wp-image-641" srcset="http://blog.technokrat.nl/wp-content/uploads/2015/06/62260701-300x200.jpg 300w, http://blog.technokrat.nl/wp-content/uploads/2015/06/62260701.jpg 500w" sizes="(max-width: 300px) 100vw, 300px" />](http://blog.technokrat.nl/wp-content/uploads/2015/06/62260701.jpg)

### Why would you do that?

Instead of killing a process or restarting a server, you just swap out a container. Deployment can become instant. You test the container on your local box, integration server, staging and production, it will be a matter of switching to an image, instead of deploying the code on there. If it doesn&#8217;t work, you can just go back a commit. Easy as pie.

### Using Vagrant?

If you&#8217;re using Vagrant you can actually try this already instead of using your VM&#8217;s (read: slow VM&#8217;s). Check this vagrant plugin out: <a href="https://github.com/fgrehm/vagrant-lxc" target="_blank">vagrant lxc</a>. You can just try it out here. Play around, install all kinds of conflicting versions of software, destroy the box, and enjoy how you didn&#8217;t completely bork your dev environment.

The people from <a href="http://modulus.io" target="_blank">Modulus</a> were in the session too, telling how happy they&#8217;ve been with Docker. They were really excited about <a href="https://github.com/docker/swarm/" target="_blank">Docker Swarm</a>. A proxy API with which you can use the same Docker API you&#8217;re used to, but have it talk to multiple instances in one API call.

### Best practices for Docker containers

First of all, most people agreed they&#8217;re is not really a &#8220;wrong&#8221; way to do a Dockerfile. When your Docker container becomes more complex it will become bigger though. Just like a git repository, the more commits, the bigger the git tree will become. Because it tracks the changes. A common practice is to compile and build a docker container and copy the compiled version to an empty docker image, to keep it small.

Other people suggested running a startup script inside the Docker image, instead of having the Dockerfile do all the provisioning.

<a href="https://www.flickr.com/photos/matthewbergman/18845642595/in/album-72157654202715069/" target="_blank">Cover photo by Matthew Bergman</a>
