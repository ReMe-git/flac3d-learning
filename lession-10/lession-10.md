### 初始条件

1. initial <关键字> <值> [grad gx gy gz] [range...]

    - den
    - pp
    - t
    - sxx
    - xdisp
    - xvel
    - add
    - mul
    - grad
    - ......

2. 渐变应力：

    ```
    ini szz -5.0e6 grad 0 0 2.5e4
    ini syy -2.5e6 grad 0 0 1.25e4
    ini sxx -2.5e6 grad 0 0 1.25e4
    ```


