
## LLVM14 and Later
NDK LLVM: https://android.googlesource.com/toolchain/llvm-project

Apple LLVM: https://github.com/apple/llvm-project

Normal LLVM: https://github.com/llvm/llvm-project

### LegacyPass
```
wget https://heroims.github.io/obfuscator/LegacyPass/ollvm14.patch
git clone -b release/14.x git@github.com:llvm/llvm-project.git
cd llvm-project
git apply ../ollvm14.patch
```
### NewPass
```
wget https://heroims.github.io/obfuscator/NewPass/ollvm14.patch
git clone -b release/14.x git@github.com:llvm/llvm-project.git
cd llvm-project
git apply ../ollvm14.patch
```
### Resolve Conflict
```
git apply --reject --ignore-whitespace ../ollvm14.patch
```
And then follow the .rej prompts to modify

## Please have a look at the [wiki](https://github.com/heroims/obfuscator/wiki)!

You can cite Obfuscator-LLVM using the following Bibtex entry:

```
@INPROCEEDINGS{ieeespro2015-JunodRWM,
  author={Pascal Junod and Julien Rinaldini and Johan Wehrli and Julie Michielin},
  booktitle={Proceedings of the {IEEE/ACM} 1st International Workshop on Software Protection, {SPRO'15}, Firenze, Italy, May 19th, 2015},
  editor = {Brecht Wyseur},
  publisher = {IEEE},
  title={Obfuscator-{LLVM} -- Software Protection for the Masses},
  year={2015},
  pages={3--9},
  doi={10.1109/SPRO.2015.10},
}
```


#### 使用方法

## 第一步
git checkout llvm-9.0.1
#新建build目录
mkdir build
cd build
#如果不想跑测试用例加上-DLLVM_INCLUDE_TESTS=OFF 
cmake -DCMAKE_BUILD_TYPE=Release -DLLVM_CREATE_XCODE_TOOLCHAIN=ON ../
make -j7

ps：编译 挺耗时

## 第二步
复制21.0.6113669 到 21.0.6113669-ollvm 

## 第三步 编译完成，将OLLVM的build/bin目录下的clang复制替换掉NDK目录中的对应文件。
   clang、clang-9、clang-format、clang++
复制替换到 ndk目录/toolchains/llvm/prebuilt/darwin-x86_64/bin

## 第四步  复制对应的头文件到NDK目录下
stdarg.h
stddef.h
__stddef_max_align_t.h
float.h
到 ndk目录/toolchains/llvm/prebuilt/darwin-x86_64/sysroot/usr/include 文件夹下


具体参考：https://blog.csdn.net/u013314647/article/details/117740784



