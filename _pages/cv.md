---
layout: archive
title: "简历"
permalink: /cv/
lang: zh
alternate_url: /en/cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

## 基本信息

- 姓名：牟磊
- 城市：重庆
- 求职方向：嵌入式软件工程师
- 电话：18716577471
- 邮箱：[mouleineo@outlook.com](mailto:mouleineo@outlook.com)

## 工作经历

### 重庆三信电子股份有限公司

嵌入式软件工程师，2023.12 至今

- 开发摩托车 BCM 与通机 ECU 嵌入式软件，主要基于 PowerPC 架构 MCU。
- 负责寄存器级底层驱动、应用层逻辑、启动流程、中断处理、内存管理与系统级调试。
- 开发下线测试与老化测试系统，包括 C 语言下位机固件和 Python / PyQt5 上位机。
- 建设 MongoDB + Web 测试数据管理系统，实现测试日志存储、查询、序列号生成与产品绑定。
- 搭建并维护部门 Gitea 代码托管平台，支持团队版本管理与协作。

### 重庆浦仁达科技有限公司

硬件工程师，2018.03 - 2023.12

- 设计并开发基于 STM32 的工业控制器，覆盖 I/O 控制、RS485 Modbus RTU、GPRS 与 RTOS 应用。
- 负责工业控制项目电气设计、控制柜设计、元器件选型、PLC 编程、HMI 配置和现场调试。
- 参与高功率电机与风机控制系统改造，支持系统方案、硬件选型、安装调试与客户 DCS 对接。

## 代表项目

{% for post in site.portfolio %}
- [{{ post.title }}]({{ post.url | relative_url }})：{{ post.excerpt | strip_html | strip_newlines }}
{% endfor %}

## 技术能力

- C、Python、PyQt5
- SPC56、STM32、PowerPC MCU、Bootloader、RTOS
- CAN、UDS、CCP、J1939、K-Line、SPI、I2C、RS-232/485
- ADC、PWM、Flash 模拟 EEPROM、休眠唤醒、定时器任务调度
- Modbus RTU、PLC、HMI、DCS、工业控制系统集成
- MongoDB、Web 查询系统、Gitea、测试数据追溯

## 教育经历

重庆三峡学院，本科，物联网工程，2014 - 2018
