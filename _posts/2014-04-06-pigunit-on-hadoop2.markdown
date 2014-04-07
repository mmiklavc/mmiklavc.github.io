---
layout: post
title:  "Getting PigUnit Running With Hadoop 2 On Windows"
date:   2014-04-06 16:10:00
categories: hadoop pig pigunit testing
---

I'll keep this short and sweet. Currently, if you try to run PigUnit on a Windows machine, you'll get an exception as follows:
{% highlight ruby %}
java.io.IOException: Could not locate executable null\bin\winutils.exe 
in the Hadoop binaries.
{% endhighlight %}
I've put together a set of Maven project templates that accomplish two goals:

1. Provide poms for adding test dependencies with Maven
2. Provide a way to get around the Windows IOException

I've created a freely-available GitHub project to solve both problems. Check it out here - [maven project template](https://github.com/mmiklavc/maven-project-templates). First build the "testing" project (mvn clean install), then do the same in the pig-deps project. You just need to reference the pig-deps project in your Maven project as follows:
{% highlight ruby %}
<dependency>
    <groupId>com.michaelmiklavcic</groupId>
    <artifactId>pig-test-deps</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
{% endhighlight %}

Then be sure to invoke the PigUnitUtil.runFix() method. See example here - [PigUnitUtilTest](https://github.com/mmiklavc/maven-project-templates/blob/master/pig/pig-deps/src/test/java/com/michaelmiklavcic/hadoop/pig/PigUnitUtilTest.java)

Credit and thanks to @cestella and @mwacc for their contributions.
