### FISH语言

1. 函数定义：函数不能递归调用，在函数中使用函数名会覆盖变量的原本定义，由于FISH变量的全局有效性，在调用后，便不能再次调用函数
    
    ```
    define <name>
        ...
    end
    ```

2. 程序行
    
    - 条件 if
    - 自定义函数
    - 分配语句
    - 循环 loop
    - 命令 command
    - 空行以分号开始的行

3. 保留名

4. 变量范围：变量名和函数名是全局的，save、restore来保存和恢复变量值

5. 数据类型
    
    - 整型
    - 浮点型
    - 字符型
    - 指针型

6. 语句

    - 说明语句
    - 控制语句：
        1) 定义语句
        ```
        define
            ...
        end
        ```
        2) 选择语句
        ```
        caseof 表达式
        case n1
            ...
        case n2
            ...
        endcase
        ```
        3) 条件语句
        ```
        if <条件表达式> then
            ...
        else
            ...
        endif
        ```

        4) 循环语句
        ```
        loop var
        ...
        end_loop

        loop while <条件表达式>
        ...
        end_loop
        ```

        5) 退出语句
        ```
        exit
        ```

        6) 段标语句
        ```
        section
        ...
        end_section
        ```

        7) 转向语句
        ```
        exit section
        ```

7. 内建变量、函数和数组

    1) 节点变量
    2) 体变量
    3) 分界面变量
