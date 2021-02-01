# test_rpath


查看文件属性：

    readelf -s *.so

查看导出函数：

    nm -D *.so
    objdump -tT *.so // 可以显示符号版本信息
	
查看libc/libc++库的版本

    `strings "/lib/libc.so.6" | grep LIBC`
    `strings "/lib/libstdc++.so.6" | grep LIBC`
    把库的路径换成你机器的路径即可
	
查看elf文件需要的库的版本

    `readelf -s ltrace  | grep -oP "GLIBC_[\d\.]*" | sort | uniq`
    把`-s`后面的文件换成你的程序

win10子系统：
https://docs.microsoft.com/zh-cn/windows/wsl/install-win10