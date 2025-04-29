### 职得智面云
基于 Spring Boot + Redis + MySQL+ Elasticsearch的Ai智能八股文刷题平台。
项目运用 Druid + HotKey热key缓存+ Sa-Token权限认证+ Sentinel限流熔断化性能和安全性。管理员可以创建题库并批量关联题目，用户可以ES分词检索题目、在线刷题并提交题解等。
### 主要工作：
1.采用动静分离策略构建 ES 题目索引，仅存储需要检索且修改不频繁的字段，而将修改频繁的字段(如点赞数)从数据库中关联查询，从而减少了 ES 数据同步更新的成本、保证数据一致性。使用 Kibana DevTools + DSL 调试 ES 的搜索效果，并使用 Spring Data Elasticsearch 的 QueryBuilder 组合查询条件，实现对题目的灵活查询。
2.为保护系统，基于 Sentinel 注解+ Dashboard 对获取题库列表接口进行限流，基于 Sentinel 的热点参数限流机制对单 IP 获取题目进行流控，并通过拉模式配置将规则持久化到本地文件。
3.通过 UserAgent 识别用户设备，并基于 Sa-Token 快速实现同端登录冲突检测，防止账号共享。基于 Redis 实现用户访问题目频率统计，超限时自动给管理员发送告警和封禁用户，有效防止内容盗取，实现分级反爬虫策略
4.通过宝塔 Linux 的 Java 项目管理器部署 jar 包，并通过 Nginx 配置反向代理解决跨域问题，使用 Knife4j+ Swagger 自动生成后端接口文档
![image](https://github.com/user-attachments/assets/7d7c03f0-301f-4247-ab91-5e8ca6b85cdb)
![image](https://github.com/user-attachments/assets/f3a48a23-8dee-41b7-81cf-0d39efae8919)
![image](https://github.com/user-attachments/assets/050de75d-44df-4fe5-9795-b0b47fe9e2fe)
![image](https://github.com/user-attachments/assets/7ee7ccc2-2da1-4575-8397-54b9356c373a)
