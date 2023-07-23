用于测试驱动开发（C++）演示的基础目录文件框架

docker exec -it mygcc bash

cmake -S . -B build
cmake --build build
cd build
ctest
cd ..
lcov --rc lcov_branch_coverage=1 -c -d build -o coverage.info_tmp
lcov --rc lcov_branch_coverage=1  -e coverage.info_tmp "*src*" -o coverage.info
genhtml --rc genhtml_branch_coverage=1 coverage.info -o coverage_report
