**SHADOW-TD-NONSINGULAR**（Simulation of Black Hole Shadow with Thick Disks for Nonsingular Black Holes）是一个用于 **非奇异黑洞在厚吸积盘条件下阴影成像** 的科研计算项目，基于光线追踪方法实现。  
支持球对称、薄盘、厚盘等几何模型，可输出观测平面图像和数值数据，方便分析非奇异黑洞阴影结构及辐射分布。

**版本0.1（此版本仅限课题组内部使用）**

**项目结构**
      SHADOW-TD-NONSINGULAR/
      │
      ├── run_all.py # 主程序入口
      ├── requirements.txt # 依赖包列表
      ├── README.md # 项目说明
      │
      ├── config/ # 参数配置文件（黑洞质量、吸积盘几何、观测角度等）
      ├── scripts/ # 数据处理、可视化脚本
      └── output/ # 运行结果：图像、数据

**语言** Python 

**首次运行时，确保所需要的依赖包正确安装，在项目*根目录*执行：**
``bash
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/

**运行主程序：** python run_all.py

默认会读取 config/ 下的参数文件，执行光线追踪计算，并将结果保存到 output/ 文件夹中。默认导出文件为黑洞的2-D平面照片,如果需要特定极角的辐射分析以及对比分析，可在scripts文件夹下执行相应文件。

**非奇异黑洞度规说明：**

本版本使用非奇异黑洞（Regular Black Hole）度规，其形式为：
  B(r) = 1 - R_g(r) / r
  
其中：
  R_g(r) = 2M * (1 - exp(-r^3 / (r_star^3)))
  r_star^3 = 2M * r0_vac^2
  
这里 M 是黑洞质量，r0_vac 是正则化参数（临界尺度），用于消除中心奇点。

在远距离处（r >> r0_vac），度规退化为标准施瓦西度规：B(r) ≈ 1 - 2M/r
在近距离处（r << r0_vac），度规平滑，避免了中心奇点。

关于吸积盘的模型构造和更多物理背景，详见Phys.Rev.D 112 (2025) 6, 064052 (arXiv:2506.21148 [gr-qc])
作者：汪子梁，江苏科技大学 ziliang.wang@just.edu.cn

**修改说明：**
本版本基于标准施瓦西黑洞版本（schwarzschild_Shadow_TD）修改而来，专门用于非奇异黑洞的阴影计算。
