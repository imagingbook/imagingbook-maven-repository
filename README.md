# imagingbook-maven-repository
Public Maven repository for imagingbook.com artefacts

## How to use

Add the following lines to your project's POM file (pom.xml):

````
<repositories>   
  <repository>      
    <id>imagingbook-maven-repository</id>
    <name>imagingbook-maven-repository on GitHub</name>
    <url>https://raw.github.com/imagingbook/imagingbook-maven-repository/master</url>
    <layout>default</layout>
  </repository>
</repositories>

<dependencies>
  <dependency>
    <groupId>com.imagingbook</groupId>
    <artifactId>imagingbook-common</artifactId>
    <version>1.5</version>
  </dependency>
  <!-- other dependencies ... -->
</dependencies>
````

## Hints for setting up a public Maven repository on GitHub


