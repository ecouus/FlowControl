# TrafficControlX
#### 流量监控与限制系统

![GitHub](https://img.shields.io/badge/license-MIT-blue)
![Bash](https://img.shields.io/badge/language-bash-green)

这是一个强大的Linux服务器流量监控与限制系统，允许服务器管理员监控特定端口的流量使用情况，并在流量超过预设限额时采取措施。

## 功能特点

- **端口流量监控**：监控特定端口的入站和出站流量使用情况
- **流量限额设置**：为每个端口设置流量上限，以GB为单位
- **用户标识**：为每个监控端口添加用户名或服务标识
- **流量计数器重置**：支持手动重置流量计数器
- **流量超限阻断**：当端口流量超过限额时自动阻断该端口
- **Telegram通知**：
  - 流量使用接近限额时自动发送警报
  - 支持通过Telegram Bot进行远程管理
  - 提供完整的命令界面，包括查看流量状态、添加/删除端口监控等
- **多种阻断方式**：支持nftables和iptables两种阻断方式
- **灵活的阻断策略**：支持reject（向客户端发送拒绝连接消息）和drop（直接丢弃数据包）两种阻断行为

## 系统要求

- Linux操作系统（Debian/Ubuntu/CentOS等）
- root权限
- 依赖包：curl, bc, jq, nftables
- 如需使用Telegram通知功能，需有有效的Telegram Bot Token

## 快速安装与使用
使用以下一行命令可以快速下载、安装并启动流量监控系统：
```bash
curl -sS -O https://raw.githubusercontent.com/ecouus/TrafficControlX/refs/heads/main/traffic-menu.sh && sudo chmod +x traffic-menu.sh && ./traffic-menu.sh
```

安装完成后，系统会自动进入主菜单界面，您可以开始配置和使用流量监控系统。

对于后续使用，您可以直接运行：

```bash
./traffic-menu.sh
```

### 主菜单选项

1. **显示所有端口流量状态**：查看当前所有被监控端口的流量使用情况
2. **查看端口监控列表**：显示所有配置了监控的端口、限额和用户信息
3. **添加端口监控**：配置新的端口进行流量监控
4. **删除端口监控**：移除现有的端口监控
5. **重置流量计数器**：重置特定端口或所有端口的流量计数器
6. **设置Telegram通知**：配置Telegram Bot通知和远程管理功能
7. **流量超限阻断设置**：配置端口流量超限时的阻断策略
9. **卸载监控系统**：完全卸载流量监控系统

### Telegram Bot 命令

一旦配置了Telegram Bot，您可以使用以下命令：

- `/status` - 查看所有端口流量状态
- `/status [端口]` - 查看特定端口流量状态
- `/add [端口] [限额GB] [用户名]` - 添加新的端口监控
- `/rm [端口]` - 删除端口监控
- `/reset [端口]` - 重置特定端口的流量计数器
- `/reset_all` - 重置所有端口的流量计数器
- `/help` - 显示帮助信息

## 流量超限阻断

当端口流量超过设定的限额（100%）时，系统可以自动阻断该端口的流量。阻断功能可以通过以下设置进行配置：

1. **启用/禁用阻断功能**：选择是否启用自动阻断
2. **阻断方式**：选择使用nftables或iptables进行阻断
3. **阻断行为**：选择reject（向客户端发送拒绝连接消息）或drop（直接丢弃数据包）
4. **立即运行检查**：手动执行一次流量检查，对超限端口进行阻断

阻断功能每5分钟自动执行一次检查，当端口流量恢复到限额以下时会自动解除阻断。

## 注意事项

- 该系统需要root权限才能运行
- 推荐使用nftables作为阻断方式，它提供更现代化的防火墙功能
- 阻断功能可能会影响正常服务，请谨慎使用
- 建议定期备份配置文件和流量日志

## 更新日志

### v1.0.0 (2023-10-15)
- 初始版本发布
- 支持基本的端口流量监控功能

### v1.1.0 (2023-10-30)
- 添加Telegram通知功能
- 增强用户界面体验

### v1.2.0 (2023-11-15)
- 添加流量超限阻断功能
- 支持多种阻断策略
- 改进流量统计算法

## 许可证

本项目采用MIT许可证。详见LICENSE文件。

## 贡献

欢迎贡献代码、报告问题或提出功能建议。请通过GitHub Issues或Pull Requests参与项目开发。

## 联系方式

有任何问题或建议，请通过GitHub Issues或以下方式联系作者：

- Telegram: [@ecouus](https://t.me/ecouus)
- Email: ecouus@example.com
