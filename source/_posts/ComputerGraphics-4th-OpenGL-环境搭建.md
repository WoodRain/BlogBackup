title: "ComputerGraphics 4th(OpenGL) 环境搭建"
date: 2016-09-12 23:23:16
tags: [Computer Graphics, OpenGL]
categories: ComputerGraphics4th
---
最近刚好有些时间，打算学习一下图形学相关的理论知识，选定的课本为Computer Graphics with OpenGL (4th edition) 影印版. 之前对DirectX比较熟悉，这次也算是顺便学习下OpenGL的使用。 
# 本机环境
+ Windows 10 10586 x64 
> 其实我配置的都是Debug/x86这样的编译组合...
+ Visual Studio 2015 Community Edition
+ WDK 8.1/10240/10586. （以8.1为主， 切换其他WDK也很方便，不赘述）。
+ Glut3.7. (一个很旧的库了，官方都不推荐用的一个库，为啥我还要用呢？ 可能是为了跟书本保持一致的缘故吧。其他功能类似，但显然更现代的开源库有glfw, glew等，这些新库可以在YouTube上面找到不少视频，学起来应该也蛮快。:) )

# 环境配置
+ 放置glut目录
选择一个合适的目录，譬如我这边选的C:\GLUT\, 放入所有glut的文件。 如 ![](/img/CG4th/Chapter3/GlutPath.jpg)

+ 放置dll
将glut32.dll放入C:\windows\SysWoW64\.

+ 检查OpenGL头文件
以WDK8.1为例的话，路径为 C:\Program Files (x86)\Windows Kits\8.1\Include\um\gl\. 一般这个目录存在，且里面含有gl.h 和glu.h 两个文件的话， Windows系统的OpenGL开发支持基本上就具备了。

# 开始写代码了
+ 新建一个VS项目
要说的内容不多，就是选择一个Console的空项目，然后取个名字，不要勾选DSL等选项。
![](/img/CG4th/Chapter3/NewProj.jpg)

+ 配置额外库路径
右击新建项目，弹出属性列表，选择Linker/General/Additional Library Directories, 新建一个条目，将之前glut等文件存放目录放进去即可。
![](/img/CG4th/Chapter3/ProjAdditionLibDir.jpg)

+ 配置额外包含路径
属性列表中，选择C/C++/General/Additional Include Directories/
![](/img/CG4th/Chapter3/ProjAdditionInclude.jpg)
> 有时候可能看不到这个条目，这时在项目里面新建一个C++文件就可以看到了。

+ 编辑代码
手动打一遍书上代码，就跟下面截图这样：
![](/img/CG4th/Chapter3/source.jpg)

+ 跑一下结果
一图胜千言
![](/img/CG4th/Chapter3/Demo.jpg)

# 额外信息 
+ 顺便建立了一个repo用来保存学习过程中的各个项目
+ 更新时间不定，完全跟个人空闲时间挂钩...
+ 习题解答一般就放在[工程repo](https://github.com/WoodRain/ComputerGraphicsOpenGL)中
