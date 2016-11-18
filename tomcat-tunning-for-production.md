#


http://www.tomcatexpert.com/popular/tomcat_logging
http://www.tomcatexpert.com/presentation/optimizing-and-tuning-apache-tomcat
http://www.tomcatexpert.com/presentation/performance-tuning-apache-tomcat-production

## Tomcat versions

* Focused on Tomcat 6.0.x
* 5.5.x - bugs and security
* 4.1.x - occasional bugs and security
* 3.x, 4.0.x, 5.0.x are unsupported
* 7.x is on the horizon with some initial discussions on the mailing list

## Agenda

* Review of Part 1
* Logging
* The role of TCP and HTTP in performance
* Load balancing
* Tuning connectors for your network
    - Timeouts are critical
* Content delivery & caching
* Tuning the JVM

## Review of Part 1: The process

* Understand the system architecture
* Stabilise the system
* Set performance target
* Measure current performance
* Identify the current bottleneck
* Fix the root cause of the bottleneck
* Repeat until you meet the target

## Review of Part 1: Availability

* Clustering
* Multiple Tomcat instances
* Load balancer
    - httpd, IIS, hardware, etc.
* How stateful is your application?
* How seamless do you want failover to be?

## Review of Part 1: Reliability

* Redeployment can cause memory leaks
    - Include redeployment in your testing
* Design for scalability
    - Include clustering in your testing
* In highly concurrent environments turn off KeepAlive

## Apache Tomcat in Production

* Applications usually account for >80% of request processing time
* Recall the tuning process
* Focus your efforts on the bottlenecks
* Don't try and guess the bottleneck
* Out of the box Tomcat
    - Tomcat ready for production
* No JVM settings applied
* Tuning is fairly limited
    - So lets get to it
* What will we tune?
    - Adjust logging
    - Tune connectors
    - Tune content cache
    - JVM settings

## Production Logging


