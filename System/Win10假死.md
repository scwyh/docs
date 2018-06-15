# Win10假死解决方法

可能是由于使用Win10默认的AHCI驱动导致的。  
可先检查：  
1.进入win10后，打开【设备管理器】。  
2.查看【IDE ATA/ATAPI控制器】下是否为【标准SATA AHCI控制器】，并且其驱动程序日期为2006/6/21。若是，则是使用的Win10默认AHCI驱动。  
3.查看主板芯片，进入Intel或AMD官网下载包含AHCI控制器驱动的芯片组“南桥驱动”，然后安装该驱动以取代系统自带的标准AHCI驱动。  


如果按以上操作后进入系统蓝屏，可按以下步骤操作：  
1.进入BIOS，修改硬盘模式为IDE或兼容模式。  
2.启动Win10进入安全模式（若无法进入安全屏式，在启动出现Win标志时按电源键强制关机，连续三次后就可进入安全模式）  
3.打开注册表，依此点击目录项展开，分别删除这两个目录下的 “StartOverride” 项  
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\storahci
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStorV 
```

4.重启进BIOS修改SATA MODE 为 AHCI，保存后就可以进入系统。  
5.如果修改后还是蓝屏，先改回原来的模式，进入系统，打开记事本，复制粘贴下面命令
```
reg delete “HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\storahci\” /v StartOverride /f
```

把文件扩展名改为*.bat   ，然后右击“以管理员身份运行”，这样问题应该就可以解决了。  
