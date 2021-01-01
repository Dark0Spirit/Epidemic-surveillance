# 项目架构

符合MVC模式，用到的技术栈有Flask、Mysql、ECharts

- **Flask** 
  搭建Web服务器，提供网站运行环境

- **MySql** 
  数据存储

- **ECharts**
  数据可视化渲染，百度开源工具



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
  - main.html
- app.py
- README.md
- spider.py
- utils.py





# ECharts

## 使用方法

1. 下载js文件
2. 准备一个有宽高的Dom容器
3. 初始化，传入容器
4. 选择一个提供的图形模板option，中国地图需要额外下载china.js