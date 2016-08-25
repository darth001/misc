#


##
SYNOPSIS:
Sync with Gradle for project failed: SSL peer shut down incorrectly

RESOLUTION:

After analyzing log(C:\Users\{USERNAME}\.AndroidStudio2.1\system\log/idea.log), we know that there's something wrong downloading gradle zip package.
Download gradle manually via [Gradle](https://services.gradle.org/distributions/gradle-2.10-all,zip)
Extract this zip package to C:\Users\{USERNAME}\.gradle\wrapper\dists\

##
