---
layout: black_white
title: 生成lua的静态库.动态库.lua.exe和luac.exe
---

打开VC命令行提示窗口，执行以下命令即可：
 
生成~~~ 静态库：
 
del *.obj liblua.lib
 
cl -c -nologo -O2 -Ob1 -Oi -Gs -MT lapi.c lcode.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c ltm.c lundump.c lvm.c lzio.c lauxlib.c lbaselib.c ldblib.c liolib.c lmathlib.c loslib.c ltablib.c lstrlib.c loadlib.c linit.c
 
link -lib -out:liblua.lib -verbose:lib *.obj
 
 
生成~~~ 动态库：
 
del *.obj liblua.dll
 
cl -c -nologo -O2 -Ob1 -Oi -Gs -MT -DLUA_BUILD_AS_DLL lapi.c lcode.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c ltm.c lundump.c lvm.c lzio.c lauxlib.c lbaselib.c ldblib.c liolib.c lmathlib.c loslib.c ltablib.c lstrlib.c loadlib.c linit.c
 
link -link -dll -out:liblua.dll -verbose:lib *.obj
 
 
生成~~~ lua.exe：
 
del *.obj lua.exe
 
cl -c -nologo -O2 -Ob1 -Oi -Gs -MT lapi.c lcode.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c ltm.c lundump.c lvm.c lzio.c lauxlib.c lbaselib.c ldblib.c liolib.c lmathlib.c loslib.c ltablib.c lstrlib.c loadlib.c linit.c lua.c
 
link -link  -out:lua.exe -verbose:lib *.obj
 
 
生成~~~ luac.exe：
 
del *.obj luac.exe
 
cl -c -nologo -O2 -Ob1 -Oi -Gs -MT lapi.c lcode.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c ltm.c lundump.c lvm.c lzio.c lauxlib.c lbaselib.c ldblib.c liolib.c lmathlib.c loslib.c ltablib.c lstrlib.c loadlib.c linit.c print.c luac.c
 
link -link -out:luac.exe -verbose:lib *.obj


至于如果没有配置VS环境变量的话需要自己设置下:

方法1.运行脚本vsvars32.bat：
D:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat

这个批处理 主要就是在运行CMD的时候先为我们设置一下环境变量(临时的) (这个脚本中写入的是bin, lib,include , tools的路径信息，也可以自己配置)

抑或可以参考 [这里](http://www.cppblog.com/ownwaterloo/archive/2009/04/15/80059.aspx) or [这里](http://www.cnblogs.com/bluestorm/p/3321558.html)