# Powershell

- Espandere nella cartella corrente tutti i file zip che si possono trovare dalla cartella attuale ricorsivamente

```powershell
 Get-ChildItem '.' -Filter *.zip -recurse | Expand-Archive -DestinationPath '.' -Force
```

## Windows Service

```powershell
# get list of service
Get-Service

#lista servizi e cerca un servizio
 Get-Service | findstr 'docker'
```

# Stop and remove all container DOCKER

https://coderwall.com/p/ewk0mq/stop-remove-all-docker-containers

Con bash

```shell
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

Con powershell

```powershell
docker ps -a -q | % { docker stop $_} | % { docker rm $_ }
```

rimuovere in base al nome di un'immagine (solo bash)

https://linuxconfig.org/remove-all-containners-based-on-docker-image-name

filtrare il risultato di docker ps 

https://container42.com/2016/03/27/docker-quicktip-7-psformat/

```shell
$ docker ps --format '{{.Names}}\t{{.Image}}'	
```

# Publish or expose port (-p, --expose)

https://docs.docker.com/engine/reference/commandline/run/#publish-or-expose-port--p-expose

  # Windows : How to list files, filtering by file and copy to clip

```powershell
#list files, filteryng by extension (pdf) and copy to clip the base name
PS> Get-ChildItem -Path .\ -Filter *.pdf -Recurse -File | Sort-Object Length -Descending | ForEach-Object {
    $_.BaseName
} | clip

#list files, filteryng by extension (pdf) and copy to clip the  name
PS> Get-ChildItem -Path .\ -Filter *.pdf -Recurse -File | Sort-Object Length -Descending | ForEach-Object {
    $_.Base
} | clip

#list files, filteryng by extension (pdf)and write as json all file
PS> Get-ChildItem -Path .\ -Filter *.pdf -Recurse -File | Sort-Object Length -Descending | ForEach-Object {
   ConvertTo-Json($_)
} 
#list files, filteryng by extension (pdf), and format with quote and comma separations, and copu in the clip
PS> Get-ChildItem -Path .\ -Filter *.pdf -Recurse -File | Sort-Object Leng
th -Descending | ForEach-Object {
>>      "`"{0}`"," -f $_.Name
>> }  | clip


```



https://blogs.technet.microsoft.com/heyscriptingguy/2014/06/15/powertip-send-output-to-clipboard-with-powershell/

https://stackoverflow.com/questions/31049454/how-to-retrieve-recursively-any-files-with-a-specific-extensions-in-powershell



# Format string

https://blogs.technet.microsoft.com/heyscriptingguy/2013/03/11/understanding-powershell-and-basic-string-formatting/

# Profile location

C:\Users\arugnone\Documents\WindowsPowerShell

#How to create new profile

see also [https://www.howtogeek.com/50236/customizing-your-powershell-profile/](https://www.howtogeek.com/50236/customizing-your-powershell-profile/)

#How to start from a directory

```powershell
Set-Location "C:\Users\arugnone\Documents\FC\DEV"	
```



# How to reload profile

```powershell
.$profile
```

# Select-String with context



```powershell
mvn dependency:tree -U  -pl .\project\   -am  | Select-String assertj -Context 10

```



# open  Hyper-V Manager via command line
see https://www.altaro.com/hyper-v/open-install-hyper-v-manager/

```powershell
 virtmgmt.msc
```


#Tail
 Nota potrebbe essere necessario lanciarlo da amministratore

```powershell
Get-Content "C:\Users\arugnone\AppData\Local\Docker\log.txt" -Wait -Tail 100
```

#Enable Hyper-v
```powershell
 Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V –All
```
#Disable Hyper-v
```powershell
 Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V –All
``
