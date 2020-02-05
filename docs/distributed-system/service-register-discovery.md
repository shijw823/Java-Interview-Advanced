**zk，一般来说还好，服务注册和发现，都是很快的**

**eureka，必须优化参数**

**eureka.server.responseCacheUpdateIntervalMs = 3000**
**eureka.client.registryFetchIntervalSeconds = 3000**

**eureka.client.leaseRenewalIntervalInSeconds = 3**
**eureka.server.evictionIntervalTimerInMs = 6000**
**eureka.instance.leaseExpirationDurationInSeconds = 6**

**服务发现的时效性变成秒级，几秒钟可以感知服务的上线和下线**

**参数说明**

```pr
#eureka server刷新readOnlyCacheMap的时间，注意，client读取的是readOnlyCacheMap，这个时间决定了多久会把readWriteCacheMap的缓存更新到readOnlyCacheMap上
#默认30s，优化为3s
eureka.server.responseCacheUpdateIntervalMs=3000

#eureka client间隔多久去拉取服务注册信息
#默认30s，优化为3s
eureka.client.registryFetchIntervalSeconds=3000

#eureka client发送心跳给server端的频率。如果在leaseExpirationDurationInSeconds后，server端没有收到client的心跳，则将摘除该instance
#默认30s，优化为3s
eureka.instance.leaseRenewalIntervalInSeconds=3

#eureka server每次主动失效检测间隔
#默认60s，优化为6s
eureka.server.evictionIntervalTimerInMs=6000

#服务过期时间配置,超过这个时间没有接收到心跳EurekaServer就会将这个实例剔除
#注意，EurekaServer一定要设置eureka.server.evictionIntervalTimerInMs否则这个配置无效，
#这个配置一般为服务刷新时间配置的三倍(eureka.instance.leaseRenewalIntervalInSeconds)
#默认90s，优化为6s
eureka.instance.leaseExpirationDurationInSeconds=6

#关闭自我保护
eureka.server.enableSelfPreservation=false
```









