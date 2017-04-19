---
title: Hexo_next加入站点内容搜索功能
date: 2017-04-19 15:07:32
tags:
categories: 随笔
---
*****



本文添加的是Local Search

********



* ### 安装 *hexo-generator-searchdb*

```
$ npm install hexo-generator-searchdb --save
```

* ### 在站点配置文件中添加字段`search`

  ```
  search:
    path: search.xml
    field: post
    format: html
    limit: 10000
  ```

* ### 修改主题配置文件 next下的_config.yml

  > local_search的enable改为true

  ```
  # Local search
  local_search:
    enable: true
  ```

  ![serach](/upload/image/localsearch.jpg)

   		

  ​