# 2019暑假 西班牙葡萄牙摩洛哥旅游计划


## 2. 计划行程

```seq

Title: 行程

上海 -> 迪拜: 转机
迪拜->马德里(西班牙)
->萨拉戈萨->图卢兹(法国)->安道尔(安道尔)->巴塞罗那(西班牙)->巴伦西亚->格拉纳达->Tarifa->
丹吉尔(摩洛哥)->卡萨布兰卡->拉巴特->梅内克斯->菲斯->舍夫沙万->丹吉尔->Tarifa->
塞维利亚(西班牙)->里斯本(葡萄牙)->赛哥维亚(西班牙)->托雷多->马德里->迪拜->上海

```

gantt
    title 行程计划
    section 西班牙
        马德里       :a1, 2019-08-21, 1d
        萨拉戈萨     :after a1, 1d
    section 法国    
        图卢兹       : 1d
    section 西班牙
        概要设计      :2019-08-15, 1d
        详细设计      :2019-08-16, 1d
        编码          :2019-08-17, 1d
        测试          :2019-08-18, 1d
    section 发布验收
        发布: 2d
        验收: 3d

gantt
dateFormat  YYYY-MM-DD
title Adding GANTT diagram to mermaid
excludes weekdays 2014-01-10

section A section
Completed task            :done,    des1, 2014-01-06,2014-01-08
Active task               :active,  des2, 2014-01-09, 3d
Future task               :         des3, after des2, 5d
Future task2               :         des4, after des3, 5d
