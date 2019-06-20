# K8s_User_Creation_X509_Certs

This script allow us to create, in an automate way, users in Kubernetes in order to use RBAC to manage authorizations.
We will use X.509 Client Certificat with OpenSSL for their simplicity. 

The process is the following:
  * Create a user in the edge node.
  * Create a private key for the user
  * Create a certificate signing request
  * Sign the csr with the Kubernetes CA
  * Move all the certificates in the .certs directory
  * Create the user inside Kubernetes
  * Create a context for the user
  * Create the config file for the user and move it into the .kube directory (don't forget to set variables inside the scripts. See below)
  
At the end of the script you will have a user created in Kubernetes and in your machine with limited access to your Kubernetes cluster. In order to learn how to manage authorizations with RBAC you can read [my article](http://www.adaltas.com/en/?p=7097&preview=true).

There is two scripts.
  * Interactive one : The script will ask you informations as the username, group and the number of days for the valid certificate.
    * user_creation_interactive.sh
    
  * Flags One : You have to pass the argument inside the shell command
    * user_creation_flags.sh -u User -g Group -d Days

You have to set the variables inside the bash script :
 * certificate_data
 * server
 
 Those information are available in your admin-cluster config. It can be found in /etc/kubernetes/admin.config.

Usage :
 * User is mandatory    
 * Group and Days (360 by default) are optionals


