How to get file from url
=====================

#Example 1
```
  wget http://blog.stackexchange.com/ -OutFile out.txt
```

#Example 2
```
  $client = new-object System.Net.WebClient
  # to get credentials
  $client.Credentials =  Get-Credential    
  $client.DownloadFile("http://www.xyz.net/file.txt","C:\tmp\file.txt")
```

#Refernces

- [How to download files in windows like wget is doing](http://superuser.com/questions/25538/how-to-download-files-from-command-line-in-windows-like-wget-is-doing)
