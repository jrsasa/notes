基于FPGA的关联成像数据采集和处理系统主要由采集模块、散斑矩阵存储模块、关联算法运算模块、DMD同步触发信号接收模块、重构物体显示模块和通信模块等部分组成。

基于FPGA的关联成像数据采集和处理系统主要由采集模块、散斑矩阵存储模块、关联算法运算模块、DMD同步触发信号接收模块、重构物体显示模块和通信模块等部分组成。

本文设计了基于FPGA关联成像数据采集与处理系统

管理计算机       显示屏

USB转串口 JTAG    VGA

		 FPGA
		 
采集模块 IO  SD DDR2

探测器  DMD

ARM 运行速度比较快且性能较稳定，拥有较好控制管理能力，这些性能使ARM更实用于界面，操作系统等方面
DSP 专用于数字信号微处理器 数据处理能力较好 FPGA并行运算为主 这种处理方式使得数据处理速度较串行速度大大提高，适用于系统采样率较高、数据吞吐量大、需要进行快速运算、实时性要求较高的应用。
存储部分 为确保系统满足存储要求，需要对存储模块的存储容量进行计算，存储空间过小无法满足数据存储需求。
内存计算 需求空间
数据存储

基本电路类型：组合逻辑功能和时序逻辑功能/
组合逻辑电路在任意时刻的输出仅仅取决于输入

id: d4836ef98731439da62461ee6dc6e638
parent_id: 9e794f5aaa9344b3b757c9a73cce837b
created_time: 2020-08-28T09:03:23.113Z
updated_time: 2020-08-28T09:51:25.384Z
is_conflict: 0
latitude: 0.00000000
longitude: 0.00000000
altitude: 0.0000
author: 
source_url: 
is_todo: 0
todo_due: 0
todo_completed: 0
source: joplin-desktop
source_application: net.cozic.joplin-desktop
application_data: 
order: 0
user_created_time: 2020-08-28T09:03:23.113Z
user_updated_time: 2020-08-28T09:51:25.384Z
encryption_cipher_text: 
encryption_applied: 0
markup_language: 1
is_shared: 0
type_: 1