# Apache Maven for Eclipse


## Eclipse

[Eclipse](https://www.eclipse.org/)

Download Eclipse IDE for Java Developera from Eclipse's official website, then decompress the zip package to some directory, e.g., D:\Program Files.


## M2Eclipse

[M2Eclipse](https://eclipse.org/m2e/)

You can install the latest M2Eclipse release (1.7.0) by using the update site offered by above link, e.g.,

https://download.eclipse.org/technology/m2e/releases


Open Eclipse > Help -> Install New Software..., click Add button to add M2Eclipse's update site with

```
name - m2e
location: https://download.eclipse.org/technology/m2e/releases
```

wait and check 'Maven Integration for Eclipse' to install M2Eclipse.


## Apache Maven

[Apache Maven](https://maven.apache.org/)

* Download Maven from Apache Maven's official website, decompress the zip package to some directory, e.g., D:\Program Files\.

* Add the bin directory of the created directory apache-maven-3.3.9, e.g., D:\Program Files\apache-maven-3.3.9\bin, to the PATH environment variable, and confirm with mvn -v in a new shell.

NOTE: environemt variable JAVA_HOME, e.g., D:\Program Files\Java\jdk1.8.0_91, should be added before above operations, or you will fail to install maven.

## Add Google Maven mirror

Copy settings.xml from D:\Program Files\apache-maven-3.3.9\conf\settings.xml to D:\Users\Michael\.m2\, then change the new settings.xml's content with some text editor, e.g., Notepad++,

```
<mirror>
    <id>google-maven-central</id>
    <name>Google Maven Central</name>
    <url>https://maven-central.storage.googleapis.com</url>
    <mirrorOf>central</mirrorOf>
</mirror>
```

You can create new Maven project...

Enjoy it:)
