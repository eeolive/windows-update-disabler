# Windows 更新禁用器 (Windows Update Disabler)

![](https://i.imgur.com/pGsWaOt.png 'Something went wrong')

⚡ 一键永久禁用自动更新，不留任何后台残留。

> [!WARNING]  
> 在运行此脚本之前，请确保 Windows 已完全更新，且当前没有正在安装或下载的更新！中断更新可能会导致 Windows 系统损坏！

## 使用方法

### 简单快捷！

1. **克隆或下载：**
    - 使用 `git clone https://github.com/tsgrgo/windows-update-disabler.git` 克隆此仓库，或者下载 ZIP 文件并解压。

2. **检查当前更新状态：**
    - 确保当前没有任何正在安装的更新。前往 **设置 > 更新与安全 > Windows 更新** 检查并确认。

3. **运行脚本：**
    - 以管理员权限执行 `disable updates.bat`。这将禁用 Windows 自动更新。

4. **重新启用更新（可选）：**
    - 如果你需要重新开启自动更新，运行 `enable updates.bat`。这是 `disable updates.bat` 的完全逆向操作，将撤销其所做的所有更改。

## 如何手动更新

为了系统安全，建议定期进行更新。若要手动更新：

1. **启用更新：**
    - 运行 `enable updates.bat` 重新启用 Windows 更新。

2. **执行更新：**
    - 前往 **设置 > 更新与安全 > Windows 更新** 并安装可用更新。

3. **再次禁用更新：**
    - 更新完成后，再次运行 `disable updates.bat` 以保持禁用状态。

## 临时使用更新服务

某些应用程序（如 Microsoft Store）依赖于 Windows 更新服务。若要临时启用该服务：

1. **启用更新服务：**
    - 运行 `use update service.bat` 重新启用 Windows 更新服务。

2. **使用相关应用程序：**
    - 你现在可以使用那些需要更新服务的应用程序了。

3. **再次禁用更新服务：**
    - 使用完毕后，运行 `disable updates.bat` 再次禁用。

## 脚本原理

该脚本通过执行以下操作来彻底拦截更新：

- 禁用 **Windows 更新服务 (wuauserv)**。
- 禁用 **更新编排器服务 (UsoSvc)**。
- 禁用 **Windows 更新修复服务 (WaaSMedicSvc)**。
- 禁用所有与更新相关的**计划任务**。
- 修改 **注册表** 以阻止自动更新检测。

## 为什么需要 PsExec？

涉及到的某些服务和任务受到系统保护，普通管理员权限也无法直接修改。PsExec 允许脚本以 **SYSTEM** 权限运行命令，从而绕过这些限制。

PsExec 是微软官方 Sysinternals 工具包的一部分。更多信息请访问：https://docs.microsoft.com/en-us/sysinternals/downloads/psexec
