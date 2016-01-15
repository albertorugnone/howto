#How to about maven

##How to set jdk version for maven compiling

Add the following plugin in the list of build.plugins

```
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <configuration>
        <source>${jdk.version}</source>
        <target>${jdk.version}</target>
      </configuration>
    </plugin>
```

jdk.version is the version of jdk you want. If you want 1.8 set to this value, 1.7 for 1.7 and so on.