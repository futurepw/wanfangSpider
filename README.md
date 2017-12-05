# 万方爬虫 wanfangSpider
该项目用于爬取万方数据库文献摘要数据，爬虫文件在万方文件夹里面，爬取数据在data1里面，目前data1里面有一份数据可供参考

# 使用方法

  * 1 需要安装scrapy爬虫框架
  * 2 git此项目
  * 3 修改wanfang/wanfang/spiders/wanfang.py 的关键字
  * 4 使用 scrapy crawl wanfang 进行爬取
# 关键字修改说明
  ### 主要修改该两个地方
  
* 1 目录url抓取起始页 讲中医修改为你需要爬取的关键字
```
start_urls = [
        'http://s.wanfangdata.com.cn/Paper.aspx?q=中医&f=top&p=1'
    ]

```
* 2 摘要抓取url 讲self.key 修改为你需要爬取的关键字
```
def __init__(self):
    self.key = '中医'
    self.count = 0
    self.url_1 = 'http://s.wanfangdata.com.cn/Paper.aspx?q='+ self.key +'&f=top&p='
```
> 注意： 两个关键字必须一样

# 格式说明
```
{
  "abstract":[], 存放摘要数据
  "C_title": [], 存放中文标题
  "E_title": [], 存放英文标题
  "C_author": [], 存放作者中文姓名
  "E_author": [], 存放作者英文姓名
  "periodical": [], 存放杂志社名称
  "keywords": [], 存放中英文关键字
  "time": [], 存放发表时间
  "fund": []，存放基金组织
  "link": [] 存放文章链接
}
```

# 结果展示
```
{
  "abstract":
            ["铁路客运专线的轨道形式确定较晚,为使施工顺利进行,桥梁专业先为上部结构预留固定高度,等到轨道形式确定后,通过调整垫石顶高程
            来保证轨道的架设,计算垫石顶高程任务繁重、过程复杂、出错率较高,如何保证计算的快速与正确性具有重要意义.总结影响垫石顶高程计
            算的各种因素,建立相应的数据库进行量化,设计出计算流程规范计算过程,构思智能读图算法核对控制高程.选用Excel作为数据库存储数
            据,采用VB语言结合Excel和CAD编制程序,实现垫石顶高程的智能计算.经过京津城际铁路和京沪高速铁路两条线的验证,结果表明,该程序
            计算速度快,计算结果准确,操作简单,界面友好,把大量技术人员从繁重而重复的任务中解脱出来."],
  "C_title": ["客运专线桥墩支承垫石顶高程的智能计算"],
  "E_title": ["Intelligent Computing of Bearing Pad Stone Top Elevation in Bridge Piers on Passenger Dedicated Line"],
  "C_author": ["廖立坚"],
  "E_author": ["Liao Lijian"], 
  "periodical": ["铁道建筑技术", "RAILWAY CONSTRUCTION TECHNOLOGY"],
  "keywords": ["支承垫石顶高程", "数据库", "计算流程", "智能读图", "智能计算"],
  "time": "2011年4月7日", 
  "fund": "U44 TP3", 
  "link": "http://d.wanfangdata.com.cn/Periodical/tdjzjs201012003"
}
```

# 备注
> 详细数据请见data1 里面的d1TCM.txt文件
