# Operating System - Extra

Operating system like Ubuntu, Fedora consists of 2 things: same OS kernel \(which is Linux and used for interacting with the underlying hardware\) and different software that differentiate between OSs. So we have common Linux kernel shared across all OSs. Docker containers share the underlying kernel, meaning docker with Ubuntu OS can run other flavor of OS \(Fedora, etc\) as long as they are all based on the same kernel, in this case Linux. All they need is the additional software that differentiate the OSs.

So for Windows that do not share the Linux kernel, you won't be able to run a Windows container on a docker host with Linux. So when you are installing docker on Windows, you are actually running a linux container on linux virtual machine under the hood. So is using Windows disadvantage not being able to run another kernel on the OS? The answer is no, because unlike hypervisor, docker is not meant to virtualize and run different OS and kernel on the same hardware.

