# 安装gogs的必备文件
- 配置文件
    - app.ini
    - 位置:/root/software/gogs/custom/conf
- 守护进程文件
    - gogs.service
    - 位置:/usr/lib/systemd/system/gogs.service

# 具体注意事项
Systemd 服务
在 GitHub 上的 Gogs 仓库有一个 systemd 服务模版文件，您需要做出一定的修改才能够使用它：

更新 User、Group、WorkingDirectory、ExecStart 和 Environment 为相对应的值。其中 WorkingDirectory 为您的 Gogs 实际安装路径根目录。
[可选] 如果您 Gogs 安装示例使用 MySQL/MariaDB、PostgreSQL、Redis 或 memcached，请去掉相应 After 属性的注释。
当您完成修改后，请将文件保存至 /usr/lib/systemd/system/gogs.service，然后通过 sudo systemctl enable gogs 命令激活，最后执行 sudo systemctl start gogs。

您可以通过 sudo systemctl status gogs -l 或 sudo journalctl -b -u gogs 命令检查 Gogs 的运行状态。