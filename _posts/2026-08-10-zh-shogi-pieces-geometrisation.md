---
title: "将棋棋子几何化"
categories: [Chinese, zh-design]
tags: [design]
lang: zh
---

![Example](https://raw.githubusercontent.com/zihong-xie/blog-image-hosting/main/img/shogi-geometrised-0.png)

## 设计
因将棋本就以朝向辨别敌我，双方的设计将完全一致。因完全根据朝向分辨敌我，若无棋子朝向提示，必须加入额外标记。在实际游玩时，依然用将棋传统可表示朝向的棋子外形。

- 玉将：六角星（由两个正三角形合成）
- 王将：六角星中间加上一点
- 飞车：正方形
- 角车：正方形转45度
- 金将：正三角形中间加上一点
- 银将：正三角形
- 桂马：无底座的倒三角形，类似V字
- 香车：五边形
- 步兵：圆

可升变的棋子用着同样的方法升变：在中心加上一个红点，颜色从黑色变为红色。

![Example](https://raw.githubusercontent.com/zihong-xie/blog-image-hosting/main/img/shogi-geometrised-1.png)

## 设计解释
- 玉将、王将：代表中枢，对称与坚固。王将的点代表权力
- 飞车、角车：正方形表示其走法
- 金将：守护君主者，三角形代表稳固，中心一点代表地位
- 银将：副守护君主者，取自金将，升变加上点后外形如同金将
- 桂马：逆三角形表示其走法
- 香车：五边形指向前方，表示其走法
- 步兵：表示最基本的职位，圆也可理解为盾