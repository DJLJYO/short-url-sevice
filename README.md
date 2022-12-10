# Fast Url

## short-url-sevice

### database:short_url

#### 主表：short_definitional

定义 id,short关键词,源地址,创建时间

```mysql
CREATE TABLE `short_url`.`short_definitional`
(
    `id`             int           NOT NULL AUTO_INCREMENT,
    `short_key`      varchar(128)  NOT NULL UNIQUE KEY COMMENT 'short url关键词',
    `md5_composite`  int           NOT NULL DEFAULT 0 COMMENT 'short_key是否加盐,1:加盐 0:常规',
    `origin_url_md5` varchar(128)  NOT NULL UNIQUE KEY COMMENT '源地址32位MD5',
    `origin_url`     varchar(1000) NOT NULL COMMENT '源地址',
    `create_time`    datetime      NOT NULL DEFAULT now() COMMENT '创建时间',
    PRIMARY KEY (`id`)
);
```