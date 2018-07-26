Maven Use Aliyun as Global Repository Demo
==========================================

Check the configuration files using by maven
--------------------------------------------

Run:

```
mvn -X
```

and search `settings`, you will see following output:

```
[DEBUG] Reading global settings from /usr/local/Cellar/maven/3.5.3/libexec/conf/settings.xml
[DEBUG] Reading user settings from /Users/freewind/.m2/settings.xml
[DEBUG] Reading global toolchains from /usr/local/Cellar/maven/3.5.3/libexec/conf/toolchains.xml
[DEBUG] Reading user toolchains from /Users/freewind/.m2/toolchains.xml
[DEBUG] Using local repository at /Users/freewind/.m2/repository
[DEBUG] Using manager EnhancedLocalRepositoryManager with priority 10.0 for /Users/freewind/.m2/repository
```

Very useful information.

Create ~/.m2/settings.xml
-------------------------

Check if `~/.m2/settings.xml` exist. If not, create it and fill with the basic content:

```
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
</settings>
```

also you can view the global `settings.xml` to see the complete example.

Add aliyun
----------

Add aliyun as a mirror of `central` to `~/.m2/settings.xml`:

```
<mirrors>
    <mirror>
          <id>alimaven</id>
          <name>aliyun maven</name>
          <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
          <mirrorOf>central</mirrorOf>
    </mirror>
</mirrors>
```

or use the superset of maven central -- jcenter:

```
<mirrors>
    <mirror>
          <id>alimaven</id>
          <name>aliyun jcenter</name>
          <url>http://maven.aliyun.com/nexus/content/repositories/jcenter</url>
          <mirrorOf>central</mirrorOf>
    </mirror>
</mirrors>
```

Test
----

Run `mvn` command in this project, and add the `-X` argument, like

```
mvn test -X
```

You will see the url it uses in the log.

Resources
---------

- <https://www.jianshu.com/p/d95d0b1b6975>

