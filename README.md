# test_rpath


查看文件属性：

    readelf -s *.so

查看导出函数：

    nm -D *.so
    objdump -tT *.so