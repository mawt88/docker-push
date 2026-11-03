
#在 PowerShell（管理员）里执行：
wsl --shutdown

第二步：用 DiskPart 压缩虚拟磁盘
继续在管理员 PowerShell 里操作。首先需要找到那个 .vhdx 文件的位置，Docker Desktop 的常见路径是 C:\Users\你的用户名\AppData\Local\Docker\wsl\disk\docker_data.vhdx（旧版本可能在 ...\wsl\data\ext4.vhdx）

diskpart
# 进入 diskpart 后，依次输入（替换成你的实际路径）
select vdisk file="C:\Users\Administrator\AppData\Local\Docker\wsl\disk\docker_data.vhdx"
attach vdisk readonly
compact vdisk
detach vdisk
exit