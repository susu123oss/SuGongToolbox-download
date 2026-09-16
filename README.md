# 苏工工具箱

**面向 SOLIDWORKS 机械设计的工程自动化工具箱**

[下载最新版本](https://github.com/susu123oss/SuGongToolbox-download/releases/latest) · [查看源码仓库](https://github.com/susu123oss/SuGongToolbox)

苏工工具箱运行在 SOLIDWORKS 内部，面向机械设计、钣金、机柜、储能、电气箱体等设计场景，把大量重复的选面、建孔、压铆、线束、焊缝、工程图整理和文件交付操作变成可预览、可重复执行的标准流程。

> 支持 **SOLIDWORKS 2018–2026（64 位）**

## 主要功能

### 装配体与钣金自动化

- **批量配孔**：在装配体中按目标面和孔规格批量创建 Hole Wizard 安装孔，并保留参考关系和后续可编辑性。
- **钣金压铆**：批量创建压铆螺母、安装孔和定位参考，支持多规格、多面以及装配体上下文。
- **批量打孔**：零件环境下快速批量创建孔特征，减少重复定位和建孔操作。
- **平面刻字**：支持钣金、普通实体和 STEP 导入实体平面，可在零件或装配体中直接使用。

### 轻量线束

用于机柜、储能、电气箱体等装配体内部快速布置线缆：

- 可选择起点、出线方向以及多个中间绕行位置。
- 支持边线、平面和圆弧面等装配体几何作为路径参考。
- 中间必经位置可按顺序参与路径计算，并支持实时路径预览。
- 支持线径、线规和线缆颜色等参数。
- 最终生成可见扫描线缆实体，方便方案设计和布置检查。

### 装配体焊缝

“添加焊缝”用于装配体中的角焊缝快速建模：

- 支持多焊接面、多条焊缝路径批量添加。
- 支持连续焊、断续焊和定位焊。
- 可设置焊脚尺寸、焊段长度、中心间距和端部避让。
- 自动根据两焊接面的理论交线校准焊缝根部。
- 自动避让孔洞、缺口和悬空区域。
- 实时黄色预览，便于生成前检查焊缝位置。
- 规则断续焊优先使用实体阵列，提高多焊段场景生成速度。

当前焊缝功能仅在**装配体**中使用。

### 工程图自动化

- **自动中心线**：自动补充中心标记和中心线，同时兼顾 STEP / X_T / IGES 等导入件的几何识别。
- **整理尺寸**：自动整理线性、径向等常见尺寸，优化间距、层级和避碰。
- **工程图导出**：批量导出 PDF / DWG，并支持图层整理和 DXF 图层映射。

### 文件与交付

- **快速打包**：通过 Pack and Go 整理模型、工程图、仿真结果和 Toolbox 引用。
- **带工程图改名**：模型改名时同步处理工程图引用，也可生成独立副本。
- **视图转 CAD**：将当前模型视图快速输出为 CAD 文件。
- **设置颜色**：快速调整零件或装配体外观。
- **打开目录**：快速定位当前模型或所选组件文件位置。

### 参数化模板与 Excel

除工具箱命令外，还保留参数化模板和批量驱动能力：

- 从 SOLIDWORKS 目录树采集尺寸、特征、配置和自定义属性。
- 支持 JSON 参数模板、数值/文本/布尔/下拉选项、单位和范围校验。
- 支持企业 `.xlsx` 模板，采用 Open XML 读写，不依赖本机 Excel COM。
- 兼容现有 `.xlsm` 工作簿，并保留 VBA 工程、控件和图片。

## 顶部“苏工工具箱”命令

当前 CommandManager 主要包含：

`批量配孔` · `钣金压铆` · `平面刻字` · `轻量线束` · `添加焊缝` · `批量打孔` · `设置颜色` · `视图转CAD` · `打开目录` · `工程图导出` · `整理尺寸` · `自动中心线` · `快速打包` · `带工程图改名` · `版权声明`

不同命令会根据当前零件、装配体或工程图环境自动显示或启用。

## 下载与安装

1. 打开 [Releases / 最新版本](https://github.com/susu123oss/SuGongToolbox-download/releases/latest)。
2. 下载 `SuGongToolbox-setup-vX.Y.Z.exe`。
3. 保存当前工作并关闭 SOLIDWORKS。
4. 双击安装包，Windows 会自动弹出管理员权限（UAC）提示。
5. 安装完成后重新启动 SOLIDWORKS，在顶部 **苏工工具箱** 选项卡中使用各项功能。

安装包文件名保留“右键管理员安装”提示以兼容原有使用习惯，但正常双击即可触发管理员权限。

安装器同时支持命令行模式：

```text
SuGongToolbox-setup-vX.Y.Z.exe /silent
SuGongToolbox-setup-vX.Y.Z.exe /uninstall
SuGongToolbox-setup-vX.Y.Z.exe /uninstall /silent
```

## 在线更新

在 SOLIDWORKS 顶部选择 **苏工工具箱 → 版权声明 → 检测更新**：

1. 检测当前版本与最新版本。
2. 下载最新版安装包。
3. 校验文件大小和 SHA-256。
4. 等待用户保存工作并正常关闭 SOLIDWORKS。
5. 启动新版安装程序并重新打开 SOLIDWORKS。

检测和下载阶段不会强制关闭 SOLIDWORKS。

## 兼容范围

| 项目 | 要求 |
| --- | --- |
| SOLIDWORKS | 2018–2026，64 位 |
| 操作系统 | Windows 10 / Windows 11，64 位 |
| 运行框架 | .NET Framework 4.8 |
| 安装权限 | 管理员权限 |

插件针对不同 SOLIDWORKS 版本做兼容处理。对于复杂导入件、特殊装配关系和关键生产图纸，仍建议在实际项目中复核生成结果。

## 安装包校验

每个版本同时提供 `.sha256` 校验文件，可在 PowerShell 中执行：

```powershell
Get-FileHash .\SuGongToolbox-setup-vX.Y.Z.exe -Algorithm SHA256
```

计算结果应与对应 Release 中的 SHA-256 一致。

## 日志与数据位置

- 运行日志：`C:\Program Files\BZXParametric\load.log`
- 日志回退目录：`%LOCALAPPDATA%\BZXParametric\load.log`
- 模板默认目录：`C:\Program Files\BZXParametric\Templates\`
- 模板回退目录：`%LOCALAPPDATA%\BZXParametric\Templates\`
- 更新下载目录：`%LOCALAPPDATA%\BZXParametric\updates\`

遇到问题时，建议保留 SOLIDWORKS 版本、复现步骤和 `load.log`，便于定位。

## 仓库说明

本仓库仅用于发布苏工工具箱安装包、SHA-256 校验文件和在线更新清单，不存放开发源码。

- 下载仓库：https://github.com/susu123oss/SuGongToolbox-download
- 源码仓库：https://github.com/susu123oss/SuGongToolbox
