# How to Install Java with apt-get on Ubuntu 16.04


##

https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

__openjdk__

    $ sudo apt-get update
    $ sudo apt-get install default-jre default-jdk


__oracle jdk__

    $ sudo add-apt-repository ppa:webupd8team/java
    $ sudo apt-get update
    $ sudo apt-get install oracle-java6-installer
    $ sudo apt-get install oracle-java7-installer
    $ sudo apt-get install oracle-java8-installer
    $ sudo apt-get install oracle-java9-installer

NOTE:

Java 6 or 7 are very old versions of Java which reached end of life in February 2013 and April 2015 respectively. It's not recommended to use them, but they are still here available for some leagcy programs.

Java 9 is a developer preview and the general release is scheduled for March 2017, so that it's also not recommended.


##

There can be multiple Java installations on one server. You can configure which version is the default for use in the command line by using `update-alternatives`, which manages which symbolic links are used for different commands.

    $ sduo update-alternatives --config java


This can also be done for other Java commands, such as the compiler `javac`, the documentation generator `javadoc`, the JAR signing tool `jarsigner` and more.

    $ sudo update-alternatives --config javac
    $ sudo update-alternatives --config javadoc
    $ sudo update-alternatives --config jarsigner


##

Many programs, such as Java servers, use the `JAVA_HOME` environment variable to determine the Java installation location. To set this environment variable, we will first need to find out where Java is installed. You can do this by executing the same command as in the previous section.

    $ sudo update-alternatives --config java

Copy the path from your preferred installation and then open `/etc/environment` using `vim`:

    $ sudo vim /etc/environment

At the end of this file, add the corresponding line, save and exit.
