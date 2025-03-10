- **Running Docker**
```
docker run --rm -it --privileged --group-add sudo --network host -w /root/workspace -v /home/avirgoel/work:/root/workspace rocm/composable_kernel:ck_ub22.04_rocm6.3 /bin/bash
```
- **Building CK**
```
cmake -D CMAKE_PREFIX_PATH=/opt/rocm -D CMAKE_CXX_COMPILER=/opt/rocm/llvm/bin/clang++ -D CMAKE_BUILD_TYPE=Release -D GPU_TARGETS="gfx942" -DCMAKE_CXX_FLAGS=" -O3" ..
```
