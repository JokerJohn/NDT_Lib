# NDT library  

These libraries are from [AutoWare](https://github.com/autowarefoundation/autoware)  
We use these libraries to create dynamic link libraries

---
## Environment
`CUDA9.0` is required.
> 1. check GPU version: `lspci | grep -i nvidia`
> 2. check NVIDIA version: `sudo dpkg --list | grep nvidia-*`
> 3. check CUDA version: `nvcc --version`

## Usage:
1. Download all these files, and build it.
> * create a new project, and put all these files under `src` folder.
> * conduct `catkin_make -DCMAKE_BUILD_TYPE=Release`
> * check `devel/lib` folder, and you can get all the `.so` files.(the `libndt_gpu.so` is about 1.1MB)

2. Put all the `.so` files to other folder you want, and add the folder to `.bashrc`   
> for example:  
> `export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH`

3. Check `CMakeLists.txt` to make sure the directory is linked.