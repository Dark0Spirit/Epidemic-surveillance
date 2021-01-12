# 项目架构

符合MVC模式，用到的技术栈有Flask、Mysql、ECharts

- **Flask** 
  搭建Web服务器，提供网站运行环境

- **MySql** 
  数据存储

- **ECharts**
  数据可视化渲染，百度开源工具



# ECharts

## 使用方法

1. 下载js文件
2. 准备一个有宽高的Dom容器
3. 初始化，传入容器
4. 选择一个提供的图形模板option，中国地图需要额外下载china.js







# 文件结构

- **`static`**
  - **`css`**
    - mian.css
  - **`js`**
    - china.js（中国地图支持js）
    - controller.js（让中国地图根据数据库中的数据实时变化）
    - ec_center.js（绘制中国地图）
    - ec_left1.js（绘制累计趋势图）
    - ec_left2.js（绘制新增趋势图）
    - ec_right1.js
    - echarts.min.js（echarts库）
    - echarts-wordcloud.min.js
    - jquery-1.11.1.min.js
- **`templates`**
  - main.html（首页）
- app.py
- README.md（本文档）
- spider.py（爬虫爬取腾讯的数据）
- utils.py（数据库）





# Json结构

- lastUpdateTime  # 最后更新时间
- chinaTotal  # 总数
- chinaDayList  # 历史记录
- chinaDayAddList  # 历史新增记录
- areaTree:  # 国家级数据
  - name
  - today
  - total
  - children  # 省级
    - name
    - today
    - children  # 市级
      - name
      - today
      - total





# Ajax



```javascript
    $.ajax({
        type:"post",   		 //请求类型
        url: "/xxx",       	 //请求地址
        data:{"xx":"xx","xx":"xx"},       	 //请求参数
        dataType:"json",	 //返回数据类型
        success: function (data){   //成功执行

        },
        error:function (){          //失败执行

        }
    })


```





# MySql表结构

详情

```mysql
Create Table

CREATE TABLE `details` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `update_time` datetime DEFAULT NULL COMMENT '数据最后更新时间',
  `province` varchar(50) DEFAULT NULL COMMENT '省',
  `city` varchar(50) DEFAULT NULL COMMENT '市',
  `confirm` int(11) DEFAULT NULL COMMENT '累计确诊',
  `confirm_add` int(11) DEFAULT NULL COMMENT '新增确诊',
  `heal` int(11) DEFAULT NULL COMMENT '累计治愈',
  `dead` int(11) DEFAULT NULL COMMENT '累计死亡',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=925 DEFAULT CHARSET=utf8mb4

```



历史记录

```mysql
Create Table

CREATE TABLE `history` (
  `ds` datetime NOT NULL COMMENT '日期',
  `confirm` int(11) DEFAULT NULL COMMENT '累计确诊',
  `confirm_add` int(11) DEFAULT NULL COMMENT '当日新增确诊',
  `suspect` int(11) DEFAULT NULL COMMENT '剩余疑似',
  `suspect_add` int(11) DEFAULT NULL COMMENT '当日新增疑似',
  `heal` int(11) DEFAULT NULL COMMENT '累计治愈',
  `heal_add` int(11) DEFAULT NULL COMMENT '当日新增治愈',
  `dead` int(11) DEFAULT NULL COMMENT '累计死亡',
  `dead_add` int(11) DEFAULT NULL COMMENT '当日新增死亡',
  PRIMARY KEY (`ds`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4

```



