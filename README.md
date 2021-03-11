<h1>Liunx-system 部署 KVM</h1>
<hr/>
<h3>因为Liunx系统中Androidstudio的intel HAXM插件 故而使用KVM代替</h3>
<hr/>
1.检测服务器是否支持VT 
egrep - o "(vmx|svm)" /proc/cpuinfo
如支持，输出结果如下：
egrep -o "(vmx|svm)" /proc/cpuinfo

2.开始安装KVM
sudo apt-get install qemu-kvm (ubuntu-vm-builder) bridge-utils 

3.启用KVM内核模块 （正常情况下，这3条命令执行成功和没有任何输出）
sudo modprobe kvm
sudo modprobe kvm_intel
sudo modprobe kvm_amd

4.AndroidStudio菜单选择 Run - Edit Configurations - Android App
在launch Flags一栏中加入
-qemu -m 512 -enable-kvm
