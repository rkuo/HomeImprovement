# Home Improvement

## Motivation  
To gain hands-on experience by prototyping an open source software based development and production platform. 

This will improve the understanding the features and functions, and limitations of available open source software; it also develops the appreciation of the required efforts to connect them together to deliver services.  

## Approach  
* can be developed locally and remote
* support version and CI/DI
* support runnable and development branches
* document with repeatable setup, automate as much as possible
* follow the best practice

## Technology  

  Initial package list:
    
* scalable, auto-update and self-healing cluster OS, [CoreOS][1], [Ubuntu-Snappy][2],…
* hyper-scale resource management, [mesos][3], [YARN] will be used to support Hardoop apps
* container management, [kubernetes][4],  
* microservices with service registration and discovery [consul][5], leverage exist services from [Netflix][6], [Walmart],…
* big data and data analytic [Apache Spark][7], [Zeppelin][8] and [Hortonworks] or [Cloudera]
* … TBD

## Construction

### Platforms support containers

#### Bare metal
##### RPi2  
* copy Snappy image to RPi2


### Resource orchestrator  
#### Mesos   




[Reference]:

[0]:https://github.com/rkuo/HomeImprovement
[1]:https://coreos.com/
[2]:https://developer.ubuntu.com/en/snappy/start/
[3]:http://mesos.apache.org/
[4]:http://kubernetes.io/
[5]:https://www.consul.io/
[6]:https://netflix.github.io/
[7]:http://spark.apache.org/
[8]:http://zeppelin.incubator.apache.org/




