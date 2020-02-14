# Explorium Demo

## Description

Hey! I made this vagrant environment using `ansible_local` provisioner (in case you have Windows as host OS).
This code creates and provisions 3 VMs in VirtualBox using Vagrant and Ansible:  

- app (192.168.77.21): sample application (hostname: app.explorium)
- registry (192.168.77.22): docker registry (hostname: registry.explorium)
- jenkins (192.168.77.23): jenkins master (hostname: jenkins.explorium)

**SSH user/pass for all vms**  
User: root  
Password: explorium  
Port: 22  

alternatively you can use:  
`vagrant ssh app`  
`vagrant ssh registry`  
`vagrant ssh jenkins`

Jenkins URL: http://jenkins.explorium
Registry: http://registry.explorium
App: http://app.explorium

## Dependencies

The packages you need to install on your host machine in order to run this code:
1. `VirtualBox (latest)`
2. `Vagrant (latest)`

## Usage

It would be good idea to add these host entries to your hosts file:  

```
192.168.77.21   app.explorium           app
192.168.77.22   registry.explorium      registry
192.168.77.23   jenkins.explorium       jenkins
```

It's very simple and straightforward.  
To run this code do the steps below:
```
git clone https://github.com/gothicfann/explorium-demo
cd explorium-demo/
vagrant up
```
wait for it to finish provisioning all three vms. 
#### Note! 
**At the end of Jenkins provisioning `Initial Admin Password` will be printed to the terminal. Copy it!**

### Jenkins setup
1. Visit the Jenkins URL (http://jenkins.explorium) using browser and use `Initial Admin Password` to unlock it.  
2. Install all suggested plugins.
3. Sign up or continue with admin user.
4. Click `create new jobs`. Set some name for project, choose `Pipeline`,click `OK`.
5. At the bottom from dropdown menu choose `Pipeline script from SCM`. Choose `Git` as SCM.
6. Paste following github repository url: https://github.com/gothicfann/angular-realworld-example-app.
7. Save pipeline and run build. Wait for it to finish.
8. Check new version of application on: http://app.explorium

This Angular project is forked from https://github.com/gothinkster/angular-realworld-example-app.

#### Note: As this demo lab is running using Vagrant and VirtualBox, Github Webhook triggers cannot be applied. In that case Jenkins instance needs to be accessable from Internet.

This project is tested on Linux (Fedora 31). It should work also on Windows too (but have not tested). 

Thanks!

## Author
Irakli Korpashvili


