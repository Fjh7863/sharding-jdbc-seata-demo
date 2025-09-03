# sharding-jdbc-seata-demo
sharding-jdbc集成seata实现分布式事务
表结构
CREATE TABLE `t_order` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `user_id` bigint DEFAULT NULL COMMENT '用户id',
  `product_id` bigint DEFAULT NULL COMMENT '产品id',
  `count` int DEFAULT NULL COMMENT '数量',
  `money` decimal(11,0) DEFAULT NULL COMMENT '金额',
  `status` int DEFAULT NULL COMMENT '订单状态: 0:创建中 1:已完结',
  PRIMARY KEY (`id`) USING BTREE
) COMMENT='订单表';

CREATE TABLE `t_account` (
  `id` bigint NOT NULL COMMENT 'id',
  `user_id` bigint DEFAULT NULL COMMENT '用户id',
  `total` decimal(10,2) DEFAULT NULL COMMENT '总额度',
  `used` decimal(10,2) DEFAULT NULL COMMENT '已用余额',
  `residue` decimal(10,2) DEFAULT NULL COMMENT '剩余可用额度',
  PRIMARY KEY (`id`) USING BTREE
) COMMENT='账户表';

CREATE TABLE `t_storage` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `product_id` bigint DEFAULT NULL COMMENT '产品id',
  `total` int DEFAULT NULL COMMENT '总库存',
  `used` int DEFAULT NULL COMMENT '已用库存',
  `residue` int DEFAULT NULL COMMENT '剩余库存',
  PRIMARY KEY (`id`) USING BTREE
) COMMENT='库存';
