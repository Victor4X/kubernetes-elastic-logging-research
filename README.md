# kubernetes-elastic-kafka

## Findings
+ ELK Stack - (1)
   + Elasticsearch, Kibana, Logstash
   + Expanded with Kafka
 + We are doing "User Centric API Metrics"
    + Tracking the individual user's behaviour
       + When do they leave the adoption funnel
       + Which are most loyal
       + Average session length
       + etc.
    + User based data store
 + And "Infrastructure metrics"
    + Tracking service behaviour
       + Tracking error rates and service logs
       + Inter-service communication issues
    + Time based data store
    + This is where you commonly see Kibana used



### User centric API metrics

See [this article](https://www.moesif.com/blog/technical/metrics/User-Centric-Metrics-vs-Infrastructure-Metrics-and-How-to-Choose-The-Right-Analytics-Architecture-and-Data-Store/?utm_source=dzone&utm_medium=blog&utm_campaign=placed-article&utm_term=leverage-elasticsearch-ubm-api-security)

+ All events are linked to a single user
+ Tools
  + Moesif, Amplitude, Mixpanel
+ Is doable with elastic, but this requires mapping the API/OAuth key to the relevant user id (We need to ask another group for  how to do this)
  + We can log a cache of this in Redis if we want to.
+ Grouping all of a specific user's events is a costly process.
+ 



## EFK (Elastic, Fluentd, Kibana) Stack

![img](https://miro.medium.com/max/700/1*Q35qZUaaKHId7fJ2DKZ2gA.png)

Better and more momentum than ELK:
https://logz.io/blog/breaking-change-to-beats-impacts-elasticsearch-elk-stack-users/
https://logz.io/blog/fluentd-logstash/

Tutorials:
https://medium.com/hepsiburadatech/fluent-logging-architecture-fluent-bit-fluentd-elasticsearch-ca4a898e28aa
https://www.digitalocean.com/community/tutorials/how-to-set-up-an-elasticsearch-fluentd-and-kibana-efk-logging-stack-on-kubernetes

+ In addition to container logs, the Fluentd agent will tail Kubernetes system component logs like kubelet, kube-proxy, and Docker logs.
  + Might replace TEK with that sentence







## ELK (Elastic, Logstash, Kibana) Stack

https://logz.io/learn/complete-guide-elk-stack/#intro

![img](https://dytvr9ot2sszz.cloudfront.net/wp-content/uploads/2021/04/Group-1207.jpg)





## TEK (Tyk, Elastic, Kibana) Stack

+ Can do basically everything we need for user based stuff
+ Coupled with Beats and Kafka, we should be able to do everything.

https://medium.com/@asoorm/observing-your-api-metrics-with-tyk-elasticsearch-kibana-74e8fd946c39





### What is Kafka?

Kafka is a queing 



### What is Logstash?



### What is Tyk?

Tyk is a service that acts as a reverse proxy and API middleman for gathering requests and sending them to elastic (or Kafka)



### What is Beats?

Beats is a collection of services used to monitor logs and performance metrics of services.
These are used for infrastructure monitoring.



## Articles

1) [How to Properly Leverage Elasticsearch and User Behavior Analytics for API Security](https://dzone.com/articles/how-to-properly-leverage-elasticsearch-and-user-be)
2) [Kafka vs logstash](https://stackshare.io/stackups/kafka-vs-logstash)
3) [User-Centric API Metrics vs Infrastructure Metrics and how to choose the right analytics architecture and data store](https://www.moesif.com/blog/technical/metrics/User-Centric-Metrics-vs-Infrastructure-Metrics-and-How-to-Choose-The-Right-Analytics-Architecture-and-Data-Store/?utm_source=dzone&utm_medium=blog&utm_campaign=placed-article&utm_term=leverage-elasticsearch-ubm-api-security) - MUST READ
4) [Deploying Kafka with ELK](https://logz.io/blog/deploying-kafka-with-elk/)
5) [Complete guide to ELK stack](https://logz.io/learn/complete-guide-elk-stack/)
6) [A Practical Guide to Kubernetes Logging](https://logz.io/blog/a-practical-guide-to-kubernetes-logging/) - Ikke super vigtig

