### lession-2 创建一个简单分析计算样例

1. 问题：在任意一土体中开挖一2mX4mX3m的沟渠，进行应力，应变场分析

2. 步骤

    1) 重置系统, command:
    ```
        ;刷新系统
        new
    ```
    2) 创建几何模型，划分网格，command:
    ```
        ;模型的结构:节点->体->组
        generate zone brick size 6,8,8
    ```
    3) 定义材料模型及参数，flac3d中不预定义单位由使用者自行定义，model 定义模型，property设置模型参数，command:
    ```
        ;选择摩尔库仑模型
        model mohr
        ;bulk为体积模量，shear为切变模量，friction为内摩擦角
        property bulk=1e8 shear=0.3e8 friction=35
        ;cohesion为内聚力，tension为抗拉强度
        property cohesion=1e10 tension=1e10
    ```
    4) 加载及边界条件，fix用于固定面，set用于设置模型属性，initial用于设置网格初始条件
    ```
        ;设置模型的受力情况，只有重力
        set gravity 0,0,-9.81
        ;设置模型网格密度kg/m^3
        initial density=1000
        ;固定左面
        fix x range x -0.1,0.1
        ;固定右面
        fix x range x 5.9,6.1
        ;固定前面
        fix y range y -0.1,0.1
        ;固定后面
        fix y range y 7.9,8.1
        ;固定底面
        fix z range z -0.1,0.1
    ```
    5) 求解，history用于记录数据
    ```
        ;每迭代5次采样一次
        history nstep=5
        history unblance
        history gp zdisplacement 4,4,8
        set mechanical force 50
        solve
    ```
    6) 显示数据
    ```
        plot history 1
        plot history 2
    ```
    7) 沟渠开挖，property默认对整体定义，添加range指明范围
    ```
        ;重新设置内聚力和抗拉强度
        property cohesion=1e3 tension=1e3
        ;定义沟渠的模型，为空模型
        model null range x=2,4 y=,2,6 z=5,10
        ;设置大变形，显示形变
        set large
        ;清除遗留下的变形
        initial xdisplacement=0, ydisplacement=0
        ;设置迭代次数为2000
        step 2000
    ```

![history-01](./images/history-01.png)

![history-02](./images/history-02.png)

![history-03](./images/history-03.png)

![history-04](./images/history-04.png)

![model](./images/result.png)
