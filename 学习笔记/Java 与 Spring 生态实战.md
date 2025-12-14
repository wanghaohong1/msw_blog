# Java 与 Spring 生态实战

Java 仍然是企业级后端的主力语言，Spring 生态提供了从快速开发到微服务治理的全链路支持。本文聚焦高频使用的核心组件与实战要点，帮助构建稳定、可维护的业务系统。

## 编程基础与工程规范

- 掌握 Java 集合框架、泛型、异常处理及常用设计模式（工厂、策略、模板、单例）。
- 熟练使用 JDK 并发包（`java.util.concurrent`），理解线程池参数、锁与原子类使用场景。
- 建立统一代码规范：包结构、命名约定、日志规范（`log.info("orderId={} status={}", id, status)`）。
- 使用 Maven 或 Gradle 管理依赖，划分模块（domain、infra、interface），引入统一版本管理。

## Spring Boot 核心能力

1. **自动配置原理**
   - 理解 `@SpringBootApplication`、`SpringFactoriesLoader` 和条件装配机制。
   - 学会编写自定义 Starter，封装内部通用能力。
2. **Web 层设计**
   - 使用 `@RestController`、`@ControllerAdvice` 实现统一出入参与异常处理。
   - 结合 `Bean Validation` 与自定义注解实现参数校验。
3. **数据访问层**
   - 使用 MyBatis-Plus / JPA 进行 ORM 映射，编写分页、批量、动态 SQL。
   - 统一封装 Repository 层，隔离业务与数据访问逻辑。
4. **配置与环境管理**
   - 区分 `application-{profile}.yml`，敏感信息使用配置中心或密钥管理服务。
   - 通过 `@ConfigurationProperties` 与 `@Value` 管理配置，避免硬编码。

## Spring Cloud 与分布式支持

- **注册与发现**：选型 Nacos/Eureka，关注健康检查、续约机制与多数据中心部署。
- **配置中心**：集中管理配置并支持灰度发布，结合 `@RefreshScope` 动态更新。
- **服务网关**：使用 Spring Cloud Gateway 或 Nginx + Lua，实现鉴权、限流、路由。
- **服务容错**：Hystrix/Sentinel 提供熔断、限流、降级策略，配置线程池隔离。
- **链路追踪与日志**：引入 Sleuth + Zipkin 或 SkyWalking 采集 TraceId/SpanId，结合 ELK 统一日志。

## 测试与质量保障

- 单元测试：`JUnit 5 + Mockito`，对核心业务逻辑进行最小粒度验证。
- 集成测试：使用 `@SpringBootTest` + 测试容器（Testcontainers）模拟依赖中间件。
- 合同测试：利用 `Spring Cloud Contract` 或 `Pact` 保持服务接口兼容。
- 性能测试：JMH 评估热点方法、JMeter 或 Locust 对外部接口压测。

## 性能与调优

- JVM 调优：掌握 GC 算法（CMS、G1、ZGC），根据场景设置堆大小、Metaspace、直接内存。
- 工具链：使用 `jstat`、`jmap`、`arthas`、`async-profiler` 分析内存与 CPU。
- 数据库调优：配合连接池（HikariCP）与 Statement 缓存，控制慢查询。
- 缓存策略：通过 Spring Cache 或自定义注解，配合 Redis 实现多级缓存。

## 常见问题排查

- **循环依赖**：合理拆分 Bean，使用构造器注入或 `@Lazy`。
- **内存泄漏**：避免 ThreadLocal 未清理、Listener/Observer 未移除。
- **事务失效**：确认 `@Transactional` 生效范围、代理方式及传播机制。
- **分布式锁**：评估 Redis、Zookeeper、数据库锁的可靠性与性能差异。

## 自查清单

- 是否能独立搭建基于 Spring Boot 的多模块项目并完成自动化测试？
- 是否理解常见 Starter 的装配流程并能编写业务 Starter？
- 是否熟练使用 Spring Cloud 组件完成配置、调用链、容错治理？
- 是否能定位 JVM、数据库、远程调用的性能瓶颈并提出优化方案？

## 推荐资料

- Spring 官方文档、Spring Guides、Spring Security Reference
- 《Java 并发编程的艺术》《深入理解 Java 虚拟机》
- 《Spring Cloud 微服务实战》《Spring Boot 实战（第 3 版）》
- GitHub: `spring-projects/spring-boot`、`alibaba/spring-cloud-alibaba` 阅读源码与 issue

