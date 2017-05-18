# Application Onboarding Guide

This guide assumes that you have successfully run the example with it's default configuration as described in [the example README](../README.md). Once in place, here are the steps you will take to onboard your own app into the environment created by the example:

- Decide the name of the projects you are going to use for your app
- Create the outline of the vars file, using those projects
- Run the automation to create the projects
- Incorporate the Jenkins pipeline into your applications source code.
- Run `oc new-app` commands to make sure the Jenkins file works
- Incorporate the templates into the vars file


# Test The Build
https://access.redhat.com/documentation/en-us/red_hat_jboss_middleware_for_openshift/3/html-single/red_hat_java_s2i_for_openshift/

`oc new-build --binary=true --name=test -i=redhat-openjdk18-openshift -e JAVA_APP_JAR=helloworld-java-rest-api-3.4.1-SNAPSHOT-fat.jar`
`mvn clean package`
`oc start-build test --from-dir=target/ --follow`
`oc new-app test`
`oc expose svc test`
click URL and you should see hello world

# Test the Jenkinsfile

- you can remove the -Dhsql