How to get file from url
=====================

```
  $client = new-object System.Net.WebClient
  #to get credentials
  $client.Credentials =  Get-Credential    
  $client.DownloadFile("http://www.xyz.net/file.txt","C:\tmp\file.txt")
```
