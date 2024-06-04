### FLAC 3D 基础知识

1. 求解过程
```
    建立网格-
    ->初始化条件-
    ->边界条件-
    ->初始应力平衡-
    ->外荷载-
    ->求解
```
2. 文件格式
    1) .sav----状态变量和用户定义条件
    2) .dat----ascii格式文件，包含一系列flac3d命令
    3) .fis----fish程序语言
    4) .flac3d----网格信息文件
    5) .his----输入输出值的ascii格式文件
    6) .bmp,.imf,.pcx,.jpg,.ps----图形文件
    7) .dcx----动画文件