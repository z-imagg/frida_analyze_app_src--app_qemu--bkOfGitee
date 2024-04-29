半自动半人工分析linux-5.11源码步骤

1. frida_js+analyze_by_graph 分析出 qemu启动linux5的vmlinux 图
     qemu5正常运行启用PVH的linux-5.11编译产物vmlinux
     若不启用PVH,则qemu5不能运行该vmlinux
     【2024年4月29日已完成】 
         linux的docker编译环境: 启用PVH的、带调试符号的linux-5.11编译产物vmlinux
         qemu的docker编译环境
      【2024年4月30日任务】 
          【术语】prj_env == frida_js+analyze_by_graph 的docker环境
           让prj_env对qemu+vmlinux正常运行，以产生 qemu的函数调用日志
    
    
2. 【人工】以图逐步读懂qemu源码中 概念、主流程 即 基本理解qemu源码 

3. 【人工】找到 vmlinux函数在qemu源码中哪里(1)、以及该函数return在qeum中源码哪里(2)
    
4. 【人工】修改qemu源码中(1)、(2) 以实现 打印 vmlinux函数进入日志，   
     等同于  frida_js 作用于 vmlinux 而产生的函数进入日志，  (只是比喻， 实际 frida_js没法作用于vmlinux)

5. 编译带(1)、(2)修改的qemu，以该qemu运行vmlinux 产生 vmlinux的函数进出日志 ，日志 喂给 analyze_by_graph ，对 vmlinux函数调用日志 做 半成品可视化 ，得图

6. 【人工】以图逐步读懂vmlinux源码中 概念、主流程 ，即可 基本理解linux内核源码 
