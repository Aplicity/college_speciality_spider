# college_speciality_spider
高校专业录取分爬虫及分析

对985高校历年各专业在各地区的录取分数据爬取及数据处理

## 文件结构
* DataSets:39所985高校的录取数据，每个csv文件对应每个高校，以高校名称为命令

* script：
  - get_data.ipynb：爬取数据。类proxy主要用于建立IP池，具体说明见：https://github.com/Aplicity/found_IPpool
  - analyse.ipynb：主要用于数据清洗及数据汇总
* 汇总数据.csv：通过./script/analyse.ipynb处理后的汇总数据
* image：存放分析的图
* 985高校清单.txt
* 基于高校招生数据的数据分析及应用研究.pdf：分析报告

## 抓包
### 构建IP池
类proxy主要用于建立IP池。对代理网站https://www.xicidaili.com/wt 爬取代理IP，具体说明见：https://github.com/Aplicity/found_IPpool

### 高考数据爬虫
目标URL规则：http://college.gaokao.com/spepoint/o + 高校名字 + /p/ + 页码

爬到的数据字段有：['专业', "学校", "平均分", "最高分", "考生地区", "文理科", "年份", "批次", "爬取页编码"]

数据存在缺失，如部分年份的高校数据缺失、录取最高分、平均分缺失等。在爬虫是可能出现服务器抛出假的页面，来迷惑程序已经爬取结束的现象。
建议对于爬取数据少于1000条的高校重新爬虫。在get_data.ipynb中有相关代码。

## 数据处理
* 部分高校含有众多分校或下属院校，除了医学院之外，
* 剔除这些院校。数据可能含有大量的重复，因此需要去重。
* 对于缺失平均分的数据用最高分来填充
* 对于缺失最高分的数据用平均分来填充
* 剔除平均分和最高分都缺失的数据
* 计算某专业xx年分文理科在xx省份下xx专业的排名，及排名得分
* 计算某专业xx年分文理科在xx省份下xx专业的排名，及排名得分

Note：对于更详细的处理公式或技巧请见分析报告：基于高校招生数据的数据分析及应用研究.pdf


## 分析结论
[基于高校招生数据的数据分析及应用研究.pdf](https://github.com/Aplicity/college_speciality_spider/blob/master/%E5%9F%BA%E4%BA%8E%E9%AB%98%E6%A0%A1%E6%8B%9B%E7%94%9F%E6%95%B0%E6%8D%AE%E7%9A%84%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E5%8F%8A%E5%BA%94%E7%94%A8%E7%A0%94%E7%A9%B6.pdf)
