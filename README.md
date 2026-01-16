# ShadowSync
ShadowSync--一款自动白加黑工具
本工具是一款高度自动化的白加黑（DLL劫持）攻击辅助工具，旨在简化和加速红队操作中的DLL劫持攻击链。全流程自动化，该工具能够在几分钟内完成从目标识别到最终Payload生成的全过程，提升在比赛中的效率。

<img width="899" height="729" alt="image" src="https://github.com/user-attachments/assets/0e814aea-9bb2-497f-8339-2663964d5891" />
工具很简单，结合了 ZeroEye 的白程序挖掘逻辑和 AheadLib 的导出转发逻辑

ZeroEye介绍：用于扫描 EXE 文件的导入表，列出导入的DLL文件，并筛选出非系统DLL，符合条件的文件将被复制到特定的 binX64 或 binX86 文件夹，并生成 Infos.txt 文件记录DLL信息。自动化找白文件，**灰梭子（关联项目）**好搭档！！！

项目地址：

```
https://github.com/ImCoriander/ZeroEye
```

## \### 完成的工作 

1. 自动化挖掘 (ZeroEye逻辑) ：脚本会自动扫描指定目录下的所有 .exe 文件，分析其导入表 (Imports)，自动排除系统 DLL (如 kernel32.dll , user32.dll 等)，筛选出适合劫持的非系统 DLL。 
2. 自动化导出转发 (AheadLib逻辑) ：无需手动生成 .asm 跳转代码。脚本使用更高级的 Linker Export Forwarding (链接器导出转发) 技术生成 .def 文件。这使得 "黑DLL" 会自动将所有原有函数调用转发给重命名后的 "白DLL" ( ApiHelp.dll )，保证原程序正常运行，且编译更简单（无需汇编器）。 
3. 自动化模板填充 ：   - 自动将白程序的名称填充到 DllMain 的宿主进程判断逻辑中。   - 自动将输入shellcode插入模板代码中。   
4. 自动化编译 ：脚本自动调用 g++ 将生成的 C++ 代码编译为最终的 DLL。
## ###使用方式

1、输入想扫描文件的路径

2、输入c格式的shellcode

3、点击scan ，会生成Output_ShadowSync_GUI文件夹

4、只需将子文件夹内的白程序，ApiHelp.dll，生成的dll三个文件上传机器执行即可上线
<img width="891" height="719" alt="image" src="https://github.com/user-attachments/assets/2dd8de13-cddf-48e5-aae9-f389c88748a5" />
<img width="1815" height="705" alt="52780171bf7576c07a159c82db4df74b" src="https://github.com/user-attachments/assets/1b1804bc-5bcd-4395-a511-e684b85527da" />
<img width="1309" height="651" alt="42a2059bdd0fec63b25480e1eccfa063" src="https://github.com/user-attachments/assets/aca75227-3890-4edc-89b8-c7b4eb932a5c" />
