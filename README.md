# simple-spring-security-facelets-taglib
Simple spring security facelets taglib

This little lib is base on spring-flow facelet taglib,  basically It is only adding methods to evaluate with hasAuthority 
so if you have a Role - Privilege schema you will be able to check the Privileges and not only the Roles

Tested with:

 - org.glassfish.web:el-impl:2.2
 - javax.servlet:javax.servlet-api:3.1.0
 - javax.servlet:jstl:1.2
 - spring-security-taglibs:4.2.3.RELEASE
 - spring version 4.2.3.RELEASE

Install

 1.- Download the project
 2.- run mvn install
  Or download jar 
```cmd
   run mvn install:install-file -Dfile=simple-spring-security-facelets-taglib-0.1.jar \
     -DgroupId=org.nl \
     -DartifactId=simple-spring-security-facelets-taglib \
     -Dversion=0.1 \
     -Dpackaging=jar
```
 4.- add to your pom 
```xml
    <dependency>
        <groupId>org.nl</groupId>
        <artifactId>simple-spring-security-facelets-taglib</artifactId>
        <version>0.1</version>
    </dependency>    
```

Sample usage

```xml
<!DOCTYPE composition PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<ui:composition xmlns="http://www.w3.org/1999/xhtml"
    xmlns:ui="http://java.sun.com/jsf/facelets"
    xmlns:h="http://java.sun.com/jsf/html"
    xmlns:sec="http://www.springframework.org/security/tags">

    <sec:authorize ifAllGranted="ROLE_FOO, ROLE_BAR">
        Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize ifNotGranted="ROLE_FOO, ROLE_BAR">
        Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize ifAnyGranted="ROLE_FOO, ROLE_BAR">
        Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize ifAllAuthorityGranted="FOO, BAR">
        Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize ifNotAuthorityGranted="FOO, BAR">
         Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize ifAnyAuthorityGranted="FOO, BAR">
         Lorem ipsum dolor sit amet
    </sec:authorize>

    <h:outputText value="Lorem ipsum dolor sit amet" rendered="#{sec:areAllAuthorityGranted('FOO, BAR')}"/>

    <h:outputText value="Lorem ipsum dolor sit amet" rendered="#{sec:areNotAuthorityGranted('FOO, BAR')}"/>

    <h:outputText value="Lorem ipsum dolor sit amet" rendered="#{sec:areAnyAuthorityGranted('FOO, BAR')}"/>

    <!-- This are from spring-security-taglibs -->
    <sec:authorize access="hasRole('ROLE_FOO')" >
        Lorem ipsum dolor sit amet
    </sec:authorize>

    <sec:authorize access="hasAuthority('FOO')" >
        Lorem ipsum dolor sit amet
    </sec:authorize>

</ui:composition>

```
