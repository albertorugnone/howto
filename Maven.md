# Maven

- Un plugin si porta dei goal che possono essere agganciati a delle fasi

## Comandi utili

https://www.mkyong.com/maven/how-to-create-a-web-application-project-with-maven/

```shell
    $ mvn archetype:generate -DgroupId={project-packaging}
        -DartifactId={project-name}
        -DarchetypeArtifactId=maven-archetype-webapp
        -DinteractiveMode=false

    //for example
    $ mvn archetype:generate -DgroupId=com.mkyong
        -DartifactId=CounterWebApp
        -DarchetypeArtifactId=maven-archetype-webapp
        -DinteractiveMode=false
```

##Add submodule

https://stackoverflow.com/questions/6328778/how-to-create-an-empty-multi-module-maven-project



## Archetipi

http://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html#archetypeCatalog

https://maven.apache.org/guides/introduction/introduction-to-archetypes.html



## Starter

* gli starter sono dei progetti in packaging java che portano con se solo dipendenze

# Analisi dipendenze

https://stackoverflow.com/questions/28835418/mvn-dependencytree-fails-on-trivial-project

```powershell
PS C:\ mvn  dependency:tree
```

Quando alcuni dei tuoi progetti non sono installati usa il trucco indicato qui https://stackoverflow.com/questions/28835418/mvn-dependencytree-fails-on-trivial-project

```powershell
PS C:\ mvn test-compile dependency:tree
```

##Advanced maven option

http://blog.sonatype.com/2009/10/maven-tips-and-tricks-advanced-reactor-options/

```
-rf, --resume-from
   Resume reactor from specified project
-pl, --projects
    Build specified reactor projects instead of all projects
-am, --also-make
    If project list is specified, also build projects required by the list
-amd, --also-make-dependents
    If project list is specified, also build projects that depend on projects on the list
```



##Set JVM

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.2</version>
    <configuration>
        <source>1.8</source>
        <target>1.8</target>
    </configuration>
</plugin>
```

## Activate Integration test

```xml
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-failsafe-plugin</artifactId>
        <version>2.20</version>
        <executions>
          <execution>
            <goals>
              <goal>integration-test</goal>
              <goal>verify</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
```

## Reserve port

```xml
<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>build-helper-maven-plugin</artifactId>
    <version>3.0.0</version>
    <executions>
        
        <execution>
            <id>reserve-port</id>
            <phase>pre-integration-test</phase>
            <goals>
                <goal>reserve-network-port</goal>
            </goals>
            <configuration>
                <portNames>
                    <portName>sftp.server.port</portName>
                </portNames>
            </configuration>
        </execution>
    </executions>
</plugin>
```

## Add integration test source and resource

```xml
<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>build-helper-maven-plugin</artifactId>
    <version>3.0.0</version>
    <executions>
        <execution>
            <id>add-test-source</id>
            <phase>generate-sources</phase>
            <goals>
                <goal>add-test-source</goal>
            </goals>
            <configuration>
                <sources>
                    <source>src/it/java</source>
                </sources>
            </configuration>
        </execution>
        <execution>
            <id>add-test-resource</id>
            <phase>generate-resources</phase>
            <goals>
                <goal>add-test-resource</goal>
            </goals>
            <configuration>
                <resources>
                    <resource>
                        <directory>src/it/resources</directory>
                    </resource>
                </resources>
            </configuration>
        </execution>
  
</plugin>
```

## how to avoid warning

[WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!

```xml
<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
```
# Add plugin to be executed only in a submodule of a multimodule project

```xml
<!-- in the parent -->
<plugin>
    <groupId>io.fabric8</groupId>
    <artifactId>docker-maven-plugin</artifactId>
    <version>${fabric8.version}</version>
    <configuration>
        <verbose>true</verbose>
        <skip>true</skip>
       ...
    </executions>
</plugin>
```

```xml
<!-- in the submodule-->
<plugin>
    <groupId>io.fabric8</groupId>
    <artifactId>docker-maven-plugin</artifactId>
    <configuration>
        <skip>false</skip>
    </configuration>
</plugin>
```
# How to skip test

```
If you use failsafe-maven-plugin to run your integration tests then 

-DskipITs 

will skip only the integration tests (i.e. failsafe tests only) 

-DskipTests 

will skip the surefire and failsafe tests 

while 

-Dmaven.test.skip=true 

will skip compiling the tests as well as running them (surefire or failsafe) 
```

#Exclude group from test


#Recover build from a project

```shell
mvn install -rf :ecm-commons-utils
```

#How to clean repository
Note: this will require a lot of time and your ide probably would take more to indexing the repo so refreshed
```shell
mvn dependency:purge-local-repository)
```

#How to run a specific test

```shell

#prompt from parent to a specific project
mvn -pl project  surefire:test -Dtest=**/ReportTaskAdapterTest

#prompt from specific project
mvn surefire:test -Dtest=**/ReportTaskAdapterTest
```

see http://maven.apache.org/surefire/maven-surefire-plugin/examples/single-test.html


#Jgitflow - Add username and psw to mvn cli


```xml
<!-- pom.xml -->
...
    <plugin>
        <groupId>external.atlassian.jgitflow</groupId>
        <artifactId>jgitflow-maven-plugin</artifactId>
        <version>${jgitflow.version}</version>
        <configuration>
            <flowInitContext>
                <versionTagPrefix>v</versionTagPrefix>
            </flowInitContext>
            <autoVersionSubmodules>true</autoVersionSubmodules>
            <useReleaseProfile>true</useReleaseProfile>
            <username>${scv.username}</username>
            <password>${scv.password}</password>
        </configuration>
    </plugin>
```

```shell
# cli
$ mvn jgitflow:hotfix-start -D"scv.username"=username -D"scv.password"=psw
```
