### 初级实体建模技术
1. 3d网格原始形状
```
    名字                        关键字      参考点      size数         维数        填充
    矩阵网格                    brick           8           3           0           no
    退化矩形网格                dbrick          7           3           0           no
    楔形网格                    wedge           6           3           0           no
    金字塔网格                  pyramid         5           3           0           no
    四面体网格                  tetrahedron     4           3           0           no
    圆柱体形网格                cylinder        6           3           0           no
    矩形外环绕放射状网格        radbrick        15          4           3           yes
    平行六面体外环绕放射状网格  radtunnel       14          4           4           yes
    圆柱体外环绕放射状网格      radcylinder     12          4           4           yes
    柱形壳体网格                cshell          10          4           4           yes
    交叉圆柱体网格              cylint          14          5           7           yes
    交叉平行六面体网格          tunint          17          5           7           yes
```
    
2. 网格生成器

3. 单元体生成

4. 三维面生成
