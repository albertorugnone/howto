# Regular Expression

## Regex Match all characters between two strings 

https://stackoverflow.com/questions/6109882/regex-match-all-characters-between-two-strings



```shell
(?<=String1)(.*)(?=String1)
```



```shell
#get all artifactId values in a pom
(?<=<artifactId>)(.*)(?=</artifactId>)
```

