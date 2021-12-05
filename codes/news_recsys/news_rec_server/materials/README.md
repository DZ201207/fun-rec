# 物料库

## news_scrapy/

scrapy项目结构的细节可以参考开源项目对应的文档

- 每天定时从新浪新闻上面爬取当天的新闻，并将新闻存入到mongodb数据库中
- 爬取新闻是一个增量的过程，每天只爬取当天的新闻
- 新闻爬取的时候需要提前之前物料池中的所有物料的标题给存下来用来去重


TODO:
1. 启动crontab，定时爬取（联调的时候再使用）
2. 爬取新闻的数量，最后需要改大一点

## materials/

- 根据爬取的数据制作物料画像
- 新闻物料去重逻辑的实现，需要依赖materials/中最新的物料画像

TODO:
1. 将前端展示数据根据news_id存储到redis中


注意：Redis的value存储中文后，get之后显示16进制的字符串”\xe4\xb8\xad\xe5\x9b\xbd”，如何解决？
启动redis-cli时，在其后面加上--raw即可，汉字即可显示正常, 如上面所示的内容

注意：zrange rec_list 0 9 返回的是排序之后的前10个元素，并且是按照value从小到大进行排序的
