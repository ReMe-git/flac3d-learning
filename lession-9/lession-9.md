### 边界条件

1. 边界种类
    - 真实边界：真实存在于模型中的真实物理对象，如隧道或地面；
    - 人为边界：人为边界不真实存在；为封闭单元体而假定。

2. 边界的力学条件
    - 指定位移
    - 指定应力

3. 边界条件命令
    - apply：
    
    ```
        apply + 节点边界条件(xforce xvelocity nvelocity)/
        单元体边界条件(xbodyforce ybodyforce zbodyforce)/
        面边界条件(sxx dstress nstress)/
        其它边界条件(add hist gradient)
    ```

    - fix：
    - free：

4. 应力边界

    1) 对倾斜边界施加法向应力：apply nstress -1e6 range plane dip 60 dd 270 origin 0.1 0 0 above
    
    2) 施加渐变力 (S = S0 + gx * x + gy * y + gz * z)：apply sxx -1e6 gradient 0 0 1e5 range z -100 0

    3) 使用FISH函数

    4) 使用FISH history 改变应力边界：apply sxx 1.0 hist @x_stress range x 5.9 6.1 y 0 6 z 0 2

    5) 使用TABLE history 改变应力边界：apply sxx 1.0 hist table 1 range x 5.9 5.1 y 0 6 z 0 2

    6) 9-6
    ```
    new
    gen zone radcyl p0 0 0 0 p1 add 18 0 0 p2 add 0 8 0 p3 add 0 0 18 dim 1.75 1.75 1.75 ratio 1.0 0.83 1.0 1.2 size 6 6 6 10
    gen zone radcyl p0 0 8 0 p1 add 18 0 0 p2 add 0 8 0 p3 add 0 0 18 dim 1.75 1.75 1.75 1.75 ratio 1.0 1.2 1.0 1.2 size 6 6 6 10 fill
    mo mo
    pro bulk 33.33e9 she 25e9 fric 45 coh 10e6 ten 5e6
    ini sxx -65e6 syy -65e6 szz -65e6
    fix x range x -0.1 0.1
    fix x range x 17.9 18.1
    fix y range y -0.1 0.1
    fix y range y 15.9 16.1
    fix z range z -0.1 0.1
    fix z range z 17.9 18.1
    def relax
        if step < ncyc then
            relax = 1.0 - (float(step) / float(ncyc))
        else
            relax = 0
        end_if
    end
    set ncyc = 1000
    app nstress -65e6 hist relax range cyl end1 0 0 0 end2 0 8 0 r 1.75
    hist unbal
    hist gp xdisp 1.75 0 0
    hist gp zdisp 0 0 1.75
    cyc 2000
    ```

5. 位移边界
