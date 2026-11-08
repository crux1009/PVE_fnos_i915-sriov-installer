# PVE_fnos_i915-sriov-installer
组件内容i915-sriov-dkms 
源码2026.11.05 最新版（支持内核 6.18.x ~ 7.3.x）
install_init 脚本8 步自动安装流程（251 行）uninstall_init 脚本完整卸载清理（91 行）
upgrade 脚本升级时自动卸载旧版、编译新版main 
脚本驱动状态检查（DKMS/i915/renderD128/xe 屏蔽/GuC）
wizard/install安装向导页面，展示说明和注意事项

安装脚本自动执行的操作:

1,检查内核兼容性 — 确认 6.18.x ~ 7.3.x
2,卸载旧版本 — 自动检测并清理已安装的旧版 DKMS
3,安装编译依赖 — build-essential、dkms、linux-headers，并处理飞牛特殊 headers 包名
4,解压源码 — 到 /usr/src/i915-sriov-dkms-2026.11.05/
5,DKMS 编译 — dkms add + dkms build + dkms install
6,屏蔽 xe 驱动 — 创建 /etc/modprobe.d/blacklist-xe.conf
7,启用 GuC — 创建 /etc/modprobe.d/i915.conf（enable_guc=3）
8,更新 GRUB — 添加 module_blacklist=xe i915.enable_guc=3 到内核参数
