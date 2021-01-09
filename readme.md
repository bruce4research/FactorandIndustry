## 前期准备工作
本项目是按照R包的结构进行组织的，这有利于我们代码的编写和优化。在利用本项目重现欧阳志刚和陈普(2020)的内容时，先按如下步骤进行准备：

1. 将本项目克隆到本地。你可以通过命令行克隆，这最好。也可以打开网址，https://github.com/common2016/FactorandIndustry后，鼠标点击下载。
2. 解压后，双击打开`FactorandIndustry.Rproj`。这保证了路径设置是正确，为后续工作做好准备。

## 数据

- 因变量：主营业务收入，源自Wind数据库。
```r
devtools::load_all()
     data("Ind0111")
     head(Ind0111)
##    province year IndCode employment         industry
## 33     安徽 2006     B06   372.5108 煤炭开采和洗选业
## 34     安徽 2006     B08    48.6659 黑色金属矿采选业
## 35     安徽 2006     B09    17.3862 有色金属矿采选业
## 36     安徽 2006     B10    18.4796   非金属矿采选业
## 37     安徽 2006     C13   264.5922   农副食品加工业
## 38     安徽 2006     C14   129.1723       食品制造业
```
- 自变量包括两个部分，一个是不分行业的自变量，另一个是分行业的工资和就业人数
```r
# 不分行业
data("FactorEndw")
head(FactorEndw[,1:6])
##    province year water   rain forest CropArea
## 6      安徽 2006 580.5 1491.0 412.32  9145.12
## 7      安徽 2007 712.5 1637.9 412.32  8853.87
## 8      安徽 2008 699.3 1598.4 412.32  8976.55
## 9      安徽 2009 733.1 1665.4 439.40  9036.18
## 10     安徽 2010 922.8 1825.7 439.40  9053.37
## 11     安徽 2011 602.1 1484.6 439.40  9022.94
# 分行业的工资和就业
data("CityEmp")
data("CityWage")
head(CityEmp[,1:5])
##   province year 电力、热力生产和供应业 电气机械和器材制造业 纺织服装、服饰业
## 1     安徽 2005                  70665                39350            15794
## 2     安徽 2006                  73748                39278            17489
## 3     安徽 2007                  73430                47365            20887
## 4     安徽 2008                  76941                44490            16595
## 5     安徽 2009                  74132                47843            20449
## 6     安徽 2010                  75408                68511            22250
head(CityWage[,1:5])
##   province year 电力、热力生产和供应业 电气机械和器材制造业 纺织服装、服饰业
## 1     安徽 2005                  19356                12734             9091
## 2     安徽 2006                  23179                15693            10909
## 3     安徽 2007                  28828                16403            12416
## 4     安徽 2008                  33671                18581            14865
## 5     安徽 2009                  38776                21215            16584
## 6     安徽 2010                  44190                26414            18679
```

## 绘图
`data-raw`文件下储存的`main.R`和`draw_partial_effect.R`是我们分别获得原文图2、图4(图5)的主体代码。这些代码，直接打开，运行即可。

## 其他说明
- 本代码进行了大幅优化，主要是加入了并行运算，把运行时间从3个小时左右缩短到了20多分钟左右(具体运行时间，取决于你的机器性能,我测试的电脑是i9, 8核，16线程的)，但该并行优化只针对Windows系统，如果是Mac或者Linux系统则会报错。

## 参考文献
- 欧阳志刚与陈普, 要素禀赋、地方工业行业发展与行业选择. 经济研究, 2020(1): 第82-98页.