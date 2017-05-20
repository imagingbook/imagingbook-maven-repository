# imagingbook-maven-repository
Public Maven repository for imagingbook.com artefacts

## How to use

Add the following lines to your project's POM file (pom.xml):

````
<repositories>   
  <repository>      
    <id>imagingbook-maven-repository</id>
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

For beginners, getting started with Maven can become a strange and long learning experience.
The last step is to make your project artefacts available to other Maven users, which
adds another level of complexity, which some people (including myself) find too much
to handle. For those who prefer to keep things simple, setting up a public Maven repository
on GitHub offers a lean and efficient alternative. An inspiring 
[blog by Mike Mitterer](http://www.mikemitterer.at/infopoint/programmierung/maven-repository-github.html)


Public Maven artefacts are typically hosted on Maven Central or another official repository. 
The file and directory structure of a Maven repository is precisely defined.



