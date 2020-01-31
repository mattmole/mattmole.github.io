---
title: "Installing VMWare tools on VMWare Virtual Machines using MDT"
excerpt: ""
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - mdt
  - edtech
  - windowsimaging
---

I trust this post is a little less dry than the last one!

# MDT testing using VMs

Testing MDT task sequences is so much easier using VMs than physical machines. The main issue I found was that without VMWare tools installed, the mouse usage with the VM is incredibly jerky.

While it is easy to install the VMWare tools manually, carrying out this task as part of the task sequence would be great!

# Step 1 - Create a group

Firstly I created a group, which contains an application installation step and a computer reboot step.

![Application being installed](/assets/images/2020-01-31/mdt4.jpg)

# Step 2 - Set a query for the task sequence group

The first thing I tried was to use a WMI query, using the query below. This didn't work as expected and everytime the task sequence failed with errors relating to an incorrect WQL query

![WMI Query that wouldn't work](/assets/images/2020-01-31/mdt1.png)

While checking out the logs I noticed that there are a couple of task sequence variables that can be used. 

* **IsVM** is binary and shows True or False
* **VMPlatform** shows VMWare in my case and a list can be found [here](https://systemscenter.ru/mdt2012.en/vmplatform.htm)

Once I discovered these variables, I created a set of conditions where all criteria had to be matched. See screenshot below

![Task sequence variables](/assets/images/2020-01-31/mdt2.jpg)

# Step 3 - Create an application with the correct flags

The final step was to create an application pointing to the VMWare Tools installation files and then to link this within the application installation step

![Silent installation flags for VMWare tools](/assets/images/2020-01-31/mdt3.jpg)

When running the task sequence once more, the VMWare tools were installed on the VM at the relevant point in the task sequence.

I hope this is useful! If I have time I will look to add steps into the task sequence that would install drivers for other VM platforms, such as virtualbox.