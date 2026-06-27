### 0 代码示例（以下半角方括号内的内容均需替换）
```verilog
//file.v
module top(); //top 是主模块
mod inst(.a(a));
endmodule
module mod(a);
...
endmodule
```
### 1 流程
1. 创建项目，在项目中创建 `file.v` 文件
2. 敲代码 → **保存**
3. 右键文件 → `compile all`
4. 按 “启动仿真 → 添加波形 → 运行顺序” 进行（指令见下文）
### 2 Transcript 中输入
#### 2.1 常规
2.1.1 启动仿真
```tcl
vsim -novopt work.top
```
2.1.2 添加波形
```tcl
add wave /top/*
```
2.1.3 运行
```tcl
run -all
```
#### 2.2 其他（通常不用）
2.2.1 退出当前仿真
```tcl
quit -sim
```
2.2.2 指定运行时间地运行（此处 `200ns` 时间可换）
```tcl
run 200ns //时间可以自定义
```
2.2.3 编译 `file.v`
```tcl
vlog file.v
```