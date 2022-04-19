---
layout: post
title:  "C#软件技巧"
date:   2022-4-19 
categories: [sours]
tags: [C#]  

---
### 判断一个点是否在图形的内部
用于色坐标的分BIN
![certificate.pdf](https://raw.githubusercontent.com/lurenjun/imgs/main/blog/rank.png)

---
コード
```
 static bool PointInPolygon(PointF p, PointF[] poly)
        {
            PointF p1, p2;
            bool inside = false;
            PointF oldPoint = poly[poly.Length - 1];
            for (int i = 0; i < poly.Length; i++)
            {
                PointF newPoint = poly[i];
                if (newPoint.X > oldPoint.X) { p1 = oldPoint; p2 = newPoint; }
                else { p1 = newPoint; p2 = oldPoint; }
                if ((p1.X < p.X) == (p.X <= p2.X) && (p.Y - p1.Y) * (p2.X - p1.X) < (p2.Y - p1.Y) * (p.X - p1.X))
                {
                    inside = !inside;
                }
                oldPoint = newPoint;
            }
            return inside;
        }
}
```


