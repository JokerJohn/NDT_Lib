# NDT Lib  

These libraries are from [AutoWare](https://github.com/autowarefoundation/autoware)  and [ndt_omp](https://github.com/koide3/ndt_omp.git)   
---
## Environment
`CUDA9.0` is required.
> 1. check GPU version: `lspci | grep -i nvidia`
> 2. check NVIDIA version: `sudo dpkg --list | grep nvidia-*`
> 3. check CUDA version: `nvcc --version`

## Usage:
1. 将lib和include文件夹丢在你的项目中

2. 在cmakelist中合适位置添加  
```makefile
find_package(OpenMP REQUIRED) #可选，仅ndt_omp用到
if(OPENMP_FOUND)
    message(STATUS "OPENMP FOUND")
    set(OpenMP_FLAGS ${OpenMP_CXX_FLAGS})  # or if you use C: ${OpenMP_C_FLAGS}
    set(OpenMP_LIBS gomp)
endif()

include_directories(include) #头文件目录
link_directories(lib) #找到.so
```

链接相应的库

```makefile
target_link_libraries(xx ${OpenMP_LIBS} ndt_cpu ndt_omp) #OpenMP_LIBS是ndt_omp需要用到的,ndt_cpu不需要
```

3. 在main.cpp中引入头文件

```c++
#include <pclomp/ndt_omp.h> //按include相对路径即可
#include <ndt_cpu/NormalDistributionsTransform.h>
```

4. 写法可参考example示例代码