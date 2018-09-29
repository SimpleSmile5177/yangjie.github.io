---
layout: Ehcache入门基础
title: Ehcache入门基础
date: 2018-09-29 15:38:35
toc: true
tags: Ehcache
---

## ehcache的简介   
EhCache 是一个纯Java的进程内缓存框架，具有快速、精干等特点，是Hibernate中默认的CacheProvider。  

<!--more--> 
## ehcache入门实例  
**1.首先先导入ehcache相关的jar依赖，我这里有的是maven项目做得演示，所以要在pom.xml里面添加依赖。**  
```xml  
<dependency>  
    <groupId>net.sf.ehcache</groupId>  
    <artifactId>ehcache</artifactId>  
    <version>2.10.2</version>  
</dependency> 
```
  
**2.创建配置文件 ehcache.xml,ehcache在启动的时候会默认去classpath根目录下找名为ehcache.xml的文件，也可以放在其他位置，使用时指明即可。为了方便，这次就在src/main/resources/创建一个配置文件 ehcache.xml。**  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<ehcache xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
         xsi:noNamespaceSchemaLocation="http://ehcache.org/ehcache.xsd">  
  <!-- 磁盘缓存位置 -->  
  <diskStore path="java.io.tmpdir/ehcache"/>  
  
  <!-- 默认缓存 -->  
  <defaultCache  
          maxEntriesLocalHeap="10000"  
          eternal="false"  
          timeToIdleSeconds="120"  
          timeToLiveSeconds="120"  
          maxEntriesLocalDisk="10000000"  
          diskExpiryThreadIntervalSeconds="120"  
          memoryStoreEvictionPolicy="LRU">  
    <persistence strategy="localTempSwap"/>  
  </defaultCache>  
  
  <!-- helloworld缓存 -->  
  <cache name="HelloWorldCache"  
         maxElementsInMemory="1000"  
         eternal="false"  
         timeToIdleSeconds="100"  
         timeToLiveSeconds="100"  
         overflowToDisk="false"  
         memoryStoreEvictionPolicy="LRU"/>  
</ehcache>
```
  
**3.测试类**  
```java  
package com.hz.demo;  
  
import net.sf.ehcache.Cache;  
import net.sf.ehcache.CacheManager;  
import net.sf.ehcache.Element;  
  
public class EhcacheTest1 {  
  
    public static void main(String[] args) {  
        // 1. 创建缓存管理器  
            CacheManager cacheManager = CacheManager.create();  
            // 2. 获取缓存对象  
            Cache cache = cacheManager.getCache("HelloWorldCache");  
            // 3. 创建元素  
            Element element = new Element("key1", "HelleWorld");  
            // 4. 将元素添加到缓存  
            cache.put(element);  
            // 5. 获取缓存  
            Element value = cache.get("key1");  
            // 6.输出缓存中的值  
            System.out.println("key1="+value.getObjectValue());  
            // 7.删除缓存中的值  
            cache.remove("key1");  
            // 8. 刷新缓存  
            cache.flush();  
            // 9. 关闭缓存管理器  
            cacheManager.shutdown();  
    }  
}
```
  
**4.输出结果**  
![哎呀，图片跑丢了](https://images2018.cnblogs.com/blog/1142546/201802/1142546-20180228135419211-541871724.png)