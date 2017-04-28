BASH
====

#Group list

cut -d: -f1 /etc/group

#cut command meaning

https://www.tutorialspoint.com/unix_commands/cut.htm

#how to know if <username> exist

grep ^ausername /etc/passwd

#add an not existing user to a group

useradd -G groupname username

#add an existing user to a group

sudo usermod -a -G groupname  username

#how to know groups of a user

groups username

#Chown recursive

chwon -R 

#How to change group acl 

setfacl -m g::rwx /path/to/directoryOrFile


# lista risorse prese dal processo con pid
sudo lsof -p pid
