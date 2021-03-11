<h1>Liunx-system 部署 KVM</h1>
<hr/>
<h3>因为Liunx系统中Androidstudio的intel HAXM插件 故而使用KVM代替</h3>
<hr/>
1.检测服务器是否支持VT <br/>
egrep - o "(vmx|svm)" /proc/cpuinfo <br/>
如支持，输出结果如下：<br/>
egrep -o "(vmx|svm)" /proc/cpuinfo<br/>

2.开始安装KVM<br/>
sudo apt-get install qemu-kvm (ubuntu-vm-builder) bridge-utils <br/>

3.启用KVM内核模块 （正常情况下，这3条命令执行成功和没有任何输出）<br/>
sudo modprobe kvm<br/>
sudo modprobe kvm_intel<br/>
sudo modprobe kvm_amd<br/>

4.AndroidStudio菜单选择 Run - Edit Configurations - Android App<br/>
在launch Flags一栏中加入<br/>
-qemu -m 512 -enable-kvm<br/>
