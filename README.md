# ShadowSync
ShadowSync--一款自动白加黑工具
本工具是一款高度自动化的白加黑（DLL劫持）攻击辅助工具，旨在简化和加速红队操作中的DLL劫持攻击链。全流程自动化，该工具能够在几分钟内完成从目标识别到最终Payload生成的全过程，提升在比赛中的效率。
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

V1.1升级***（delay尽量不要改，默认就好，改了可能会出现程序启动失败问题）
<img width="1114" height="974" alt="image" src="https://github.com/user-attachments/assets/5c22edb4-619a-4334-8594-7a55db5faf90" />
<img width="1885" height="765" alt="image" src="https://github.com/user-attachments/assets/88ef431d-8b48-41b7-af6b-53819e9e6f68" />
<img width="1470" height="830" alt="image" src="https://github.com/user-attachments/assets/3f73eb32-4de3-47f7-b17b-c65fe93eaf07" />

