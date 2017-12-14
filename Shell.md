# Bash

- Elencare solo i nomi dei file

```bash
ls -A1
```

#aggiungere un utente esistente ad un gruppo esistente

```bash
usermod -a -G ftp tony	
```
Note: if usermod command not found /usr/sbin is not in your path

[https://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](https://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

#aggiungere path all'utente

The easiest way is to add this line to your user's ``~/.bashrc`` file:

``export PATH=$PATH:/usr/local/sbin``

[https://superuser.com/questions/595818/add-usr-local-sbin-to-the-path-of-a-user/](https://superuser.com/questions/595818/add-usr-local-sbin-to-the-path-of-a-user/)

#reload .bashrc

```bash
source ~/.bashrc
# or 
. ~/.bashrc
```

#chmod
https://www.tutorialspoint.com/unix/unix-file-permission.htm


#call a function from a script

https://stackoverflow.com/questions/8818119/how-can-i-run-a-function-from-a-script-in-command-line

```shell
. ./myScript.sh && func()
```

#unzip files
https://stackoverflow.com/questions/107995/how-do-you-recursively-unzip-archives-in-a-directory-and-its-subdirectories-from

```shell
find . -name "*.zip" | while read filename; do unzip -o -d "`dirname "$filename"`" "$filename"; done;
```

```shell
find . -name "*.zip" | xargs -P 5 -I fileName sh -c 'unzip -o -d "$(dirname "fileName")/$(basename -s .zip "fileName")" "fileName"'
```

#find all file except

find  /path/ ! '(' -name "*detail*xml" -o -name "*ok" ')'


#find all file and extract filename
https://stackoverflow.com/questions/3362920/get-just-the-filename-from-a-path-in-a-bash-script

find  /mnt/spst00/ftpnew/Conai/Finance_PEC/FattureAttive/ ! '(' -name "*detail*xml" -o -name "*ok" ')' | while read filepath; do echo $(basename "${filepath%.*}")  ; done;


#Average file size within a directory

http://vivekjain10.blogspot.it/2008/02/average-file-size-within-directory.html


```shell
#To calculate the average file size within a directory on a Linux system, following command can be used:

ls -l | grep -v ^total | gawk '{sum += $5; n++;} END {print sum/n;}'

#If you'd like to know the average size of some particular kind of files (like jpg files) then use the following:

    ls -l *.jpg | grep -v ^total | gawk '{sum += $5; n++;} END {print sum/n;}'

```

#wget to stdout

https://fischerlaender.de/en/redirecting-wget-to-stdout
https://superuser.com/questions/321240/how-do-you-redirect-wget-to-standard-out/321241

wget --user some --password somepsq http://172.16.122.201/alfresco/service/index/all
