用于测试驱动开发（C++）演示的基础目录文件框架

下载到本地：
git clone git@github.com:tzs919/demo_tdd_cxx-v1.0.git

根目录下执行以下命令，获取googletest
git submodule init
git submodule update

docker exec -it mygcc bash

cmake -S . -B build
Windows下要用：cmake -G "Unix Makefiles" -S . -B build
这样就会使用gcc version 8.1.0编译器（C:\mingw64\bin\gcc.exe），否则会使用msvc编译器

cmake --build build
cd build
ctest
cd ..
lcov --rc lcov_branch_coverage=1 -c -d build -o coverage.info_tmp
lcov --rc lcov_branch_coverage=1  -e coverage.info_tmp "*src*" -o coverage.info
genhtml --rc genhtml_branch_coverage=1 coverage.info -o coverage_report
