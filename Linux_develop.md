# Linux 开发环境配置
---
## C/C++开发环境配置
### 1. 安装c++编译器
输入以下命令安装c++编译器
```shell
sudo apt install build-essential
```
验证是否安装成功
```shell
g++ --version
```
### 2. 安装cmake
输入以下命令安装cmake
```shell
sudo apt install cmake
```
验证是否安装成功
```shell
cmake -version
```
示例：
main.cpp:
```cpp main.cpp
#include <iostream>
int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```
CMakeLists.txt:
```cmake CMakeLists.txt

```

