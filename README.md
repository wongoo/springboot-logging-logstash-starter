spring boot logback log to logstash

# 1. logstash tcp socket
## maven dependency:
```
<dependency>
     <groupId>springboot.logging.logstash</groupId>
    <artifactId>springboot-logging-logstash-tcp-starter</artifactId>
    <version>1.0.0</version>
</dependency>
```

## config sample:
```
spring.application.name=test

logstash.version=5
logstash.disable_other_appenders=false
logstash.destinations=127.0.0.1:5046,127.0.0.1:5046
logstash.keep_alive_duration=5000
logstash.reconnection_delay=1000
logstash.write_buffer_size=16384
logstash.custom_fields={"service_name":"${spring.application.name}","profiles":"${spring.profiles.active:default}"}
```

before running unit test, you can run `nc -lkv 5046` to simulate logstash listening.

# reference:
- https://github.com/logstash/logstash-logback-encoder