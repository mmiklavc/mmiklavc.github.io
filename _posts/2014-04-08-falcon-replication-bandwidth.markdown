---
layout: post
title:  "Setting maxMaps and mapBandwidth for Falcon Feed Replication"
date:   2014-04-08 00:30:00
categories: hadoop apache falcon jira
---

I'm happy to announce another contribution to the Apache Falcon project. A previous patch of mine exposed the maxMaps parameter to users through the feed's properties list. This patch includes the ability to set mapBandwidth as well.

[FALCON-391](https://issues.apache.org/jira/browse/FALCON-391)

{% highlight ruby %}
<properties>
    ...
    <property name="maxMaps" value="8"/> <!-- max mappers used during replication -->
    <property name="mapBandwidth" value="20"/> <!-- set bandwidth in MB/s used during replication -->
    ...
</properties>
{% endhighlight %}

