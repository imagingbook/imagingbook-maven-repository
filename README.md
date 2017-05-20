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
The last step is to make your project artefacts available to other Maven users.
Public Maven artefacts are typically hosted on Maven Central or another official repository but this
adds another level of complexity, which some people (including myself) find too much
to handle. For those who prefer to keep things simple, setting up a public Maven repository
on GitHub offers a lean and efficient alternative. Of great help in this context is this
[blog by Mike Mitterer](http://www.mikemitterer.at/infopoint/programmierung/maven-repository-github.html).
The file and directory structure of a Maven repository are precisely defined and we must make sure 
that our repository strictly complies with these rules.

1. Create and intialize a **public** repository on GitHub - let's call it ``maven-repo`` 
(assuming your Github account is ``MyGithubId``). 
Note that if the repository is *private*, then some resources (e.g., pom-xml files) are 
not publicly accessible!

2. Clone your repository to your local file system,
e.g., into a folder ``maven-repo`` next to your project folder ``maven-project``.
So assume have this directory structure:
````
    maven-project/
		pom.xml
		...
	maven-repo/
````

3. Add the following to your projects POM file (``maven-project/pom.xml``):
````
<distributionManagement>
	<repository>
		<id>my-maven-repo</id>
		<name>My Maven Repository</name>
		<url>file:///${project.basedir}/../maven-repo</url>
	</repository>
</distributionManagement>
````

4. Create a ``.gitattributes`` file in ``maven-repo/`` and add the following lines:
````
* text=auto

# Never modify line endings for the following:
*.xml -text
*.md5 -text
*.sha1 -text
*.pom -text

# Denote all files that are truly binary and should not be modified.
*.jar binary
````
Note: This step is important because by default Git treats ``.xml`` files as text and
modifies the line endings, such that the checksum (hash) values of the online files do not match
any longer.


5. Run the ``deploy`` goal on your Maven project, i.e.,
````
mvn deploy
````
This should place your project's artefacts in ``maven-repo/``. This must be repeated
for every new project release.

6. Commit and push ``maven-repo`` to GitHub.

7. Other project depending on your Maven artefacts need to include 
the following in their ``pom.xml`` files:
````
	<repositories>
		<repository>
			<id>my-maven-repo</id>
            <url>https://raw.github.com/MyGithubId/maven-repo</url>
			<layout>default</layout>
		</repository>
	</repositories>

	<dependencies>

		<dependency>
			<groupId>MyGroupId</groupId>
			<artifactId>MyArtefact</artifactId>
			<version>1.0</version>
		</dependency>

	</dependencies>
````


