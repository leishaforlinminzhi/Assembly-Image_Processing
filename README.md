
## IMAGE_PROCESSING

# 汇编与编译原理大作业

### 1. 开发环境

+ Windows10下VS2022+masm32

+ 常规 > windows SDK版本：

+ 常规 > 平台工具集：

+ 链接器> 附加库目录：

  链接器 > 系统 > 子系统：	

+ Microsoft  Macro Assemble > General > **~/masm32/include;**

### 2.实现原理

- #### 整体框架
  
  - 基于老师上课讲的Win32框架
  
  - asm结构：
  
  	


+ #### 图片读写和转化

  + 打开并读取图片信息

  	提示输入bmp格式的文件名，要求位于当前工作目录下

  	<!--可以考虑优化文件打开方式-->

  	执行`CreateFile`函数，成功则返回文件句柄，否则直接结束程序。

  	<!--ui处理一下打开成功or失败提示-->

  	通过`GetFileSize`函数获取文件的大小，计算需要读取的字节数，作为`ReadFile`函数的参数并按需分配存储数据的缓冲区`ddBaseFile`。

  	执行`ReadFile`函数，从打开的文件中读取数据，保存在缓冲区`ddBaseFile`中。

  + 格式转化 
    
    <!--这部分没看懂 ddBaseFile是存图片信息的缓冲区，ddBytesPerPixel应该是存像素的，但是这两个相互转化的部分没找到 也许bmp读出来就是二进制？-->
    
    + 将图片文件转化为像素矩阵
    
      通过读取文件时获得的数据计算像素矩阵的`RowSize`，单位为`byte`
    
      > RGB图⼀个像素占3*8=24bits，对于小数向下舍入所以分子需要加31
    
      $$
      RowSize=\frac{(BitsPerPixel *ImageWeight+31)}{32}*4
      $$
    
      从而计算存储像素矩阵所需要的空间` ddPixelArraySize`
      $$
      ddPixelArraySize=RowSize * ImageHeight
      $$
      
    
    + 将像素矩阵转化为图片文件
    
      
    
  + 保存图片

  	将存储的缓冲区`ddBaseFile`指针和更新后的字节数作为参数执行`CreateFile`函数创建输出文件`output.bmp`,

+ #### 图片裁剪、旋转、翻转


+ #### 添加滤镜

+ #### 图片液化



### 3. 难点和创新点



### 4. 小组分工



### 5.代码结构



### 6.参考资料

