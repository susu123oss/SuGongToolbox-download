# 苏工工具箱

**面向 SOLIDWORKS 的参数化设计与工程自动化工具箱**

[下载最新版本](https://github.com/susu123oss/SuGongToolbox-download/releases/latest) · [查看源码仓库](https://github.com/susu123oss/SuGongToolbox)

苏工工具箱面向机械设计、工艺和制造团队，把 SOLIDWORKS 模型、参数模板、业务表单与批量执行连接起来。它不会替代 SOLIDWORKS，而是将重复的建模、配孔、工程图整理和文件交付工作转化为可复用、可追踪的工程流程。

## 主要功能

### 参数化模板与批量驱动

- 从 SOLIDWORKS 目录树选择零件和装配体，采集尺寸、特征、配置及自定义属性
- 支持数值、整数、布尔、文本、下拉选项、单位、范围和必填校验
- 模板保存为带稳定 ID 的 JSON，可重复使用、复制和版本管理
- 执行前统一预检，执行后自动重建、保存并记录结果

### Excel 双向交换

- 企业 `.xlsx` 模板采用 Open XML 读写，不依赖本机 Excel COM
- 支持业务输入、文档定义、参数配置与执行结果回写
- 兼容旧 `.xlsm` 工作簿，并保留 VBA 工程、控件和图片

### SOLIDWORKS 工程自动化

- **批量配孔**：按目标面和孔规格创建原生 Hole Wizard，并保留参考几何关系
- **批量铆接螺母**：在宿主零件中创建安装孔、参考关系和螺母特征，支持零件及装配体流程
- **工程图整理尺寸**：遍历图纸页和视图，使用 SOLIDWORKS 原生能力整理尺寸与孔标注
- **工程图导出**：支持图层映射以及 PDF、DWG 输出
- **快速打包**：通过 Pack and Go 整理模型、工程图、仿真结果和 Toolbox 引用
- **带工程图改名**：同步模型及工程图引用，也可生成独立副本
- **常用工具**：颜色设置、视图转 CAD、目录定位、文件整理等

## 典型工作流程

```text
工程师定义模型规则
        ↓
采集尺寸 / 特征 / 配置 / 属性
        ↓
保存参数模板或导出 Excel
        ↓
填写业务参数并执行
        ↓
插件批量驱动 SOLIDWORKS
        ↓
重建、保存、导出和记录结果
```

## 兼容范围

| 项目 | 要求 |
| --- | --- |
| SOLIDWORKS | 2018–2026，64 位 |
| 操作系统 | Windows 10 / Windows 11，64 位 |
| 运行框架 | .NET Framework 4.8 |
| 安装权限 | 需要管理员权限 |

发布客户版本前，建议在对应 SOLIDWORKS 版本和本机模板环境中完成基础功能测试。

## 下载与安装

1. 打开 [Releases / 最新版本](https://github.com/susu123oss/SuGongToolbox-download/releases/latest)。
2. 下载 `SuGongToolbox-setup-vX.Y.Z.exe`。
3. 保存当前工作并正常关闭 SOLIDWORKS。
4. 右键安装包，选择“以管理员身份运行”。
5. 安装完成后启动 SOLIDWORKS，在顶部“苏工工具箱”选项卡中使用各项功能。

安装器同时支持命令行静默模式：

```text
SuGongToolbox-setup-vX.Y.Z.exe /silent
SuGongToolbox-setup-vX.Y.Z.exe /uninstall
SuGongToolbox-setup-vX.Y.Z.exe /uninstall /silent
```

## 在线更新

在 SOLIDWORKS 顶部选择 **苏工工具箱 → 版权声明 → 检测更新**，插件会读取本仓库最新 Release：

1. 比较当前版本与最新语义版本号
2. 将安装包下载到 `%LOCALAPPDATA%\BZXParametric\updates\`
3. 校验安装包大小和 SHA-256
4. 等待用户保存工作并正常关闭 SOLIDWORKS
5. 静默安装新版并重新启动 SOLIDWORKS

检测和下载阶段不会强制关闭 SOLIDWORKS。

## 校验安装包

每个版本同时提供 `.sha256` 文件。也可以在 PowerShell 中执行：

```powershell
Get-FileHash .\SuGongToolbox-setup-vX.Y.Z.exe -Algorithm SHA256
```

计算结果应与 Release 页面及对应 `.sha256` 文件一致。

## 日志与数据位置

- 运行日志：`C:\Program Files\BZXParametric\load.log`
- 日志回退目录：`%LOCALAPPDATA%\BZXParametric\load.log`
- 模板默认目录：`C:\Program Files\BZXParametric\Templates\`
- 模板回退目录：`%LOCALAPPDATA%\BZXParametric\Templates\`
- 更新下载目录：`%LOCALAPPDATA%\BZXParametric\updates\`

## 仓库说明

本仓库仅用于发布苏工工具箱的安装包、SHA-256 校验文件和在线更新清单，不存放开发源码。

- 下载仓库：<https://github.com/susu123oss/SuGongToolbox-download>
- 源码仓库：<https://github.com/susu123oss/SuGongToolbox>

问题定位时，请保留 SOLIDWORKS 版本、复现步骤和 `load.log`，以便快速分析。
