# CostDistance_IDW
This repository contains the sorce code of Cost Distance and IDW  algorithms



### Instalation gdal Windows CLion

Use MSYS2 (msys2.org). 

Install MSYS2 and follow the tutorial on their website (pacman -Syu, pacman -Su).

Then use the command (pacman -S mingw-w64-x86_64-toolchain) 
you need to install Cmake and link to clion

First run the command (pacman -S mingw-w64-x86_64-cmake) in the msys2 prompt

Sencondly configure the Clion, In clion go to FILE -> SETTINGS -> Build, Execution, Deployment -> TOOLCHAINS ->
In the option enviroment apears a link, change for (your disk):/msys64/mingw64 (you can install msys2 in another disk diferent where you install clion)
In cmake apears a link, change it for (your disk):\msys64\mingw64\bin\cmake.exe for example D:\msys64\mingw64\bin\cmake.exe "D" is where I install all packages
then the others spaces like c compiler change theirs links.
  
Install Gdal

Then using pacman in the msys2 command prompt, get the MingW (pacman -S mingw-w64-x86_64-gcc) and GDAL (pacman -S mingw-w64-x86_64-gdal).
check if gdal is installed with te following command, you should be in the root, use the comand -pwd, and you see where you are /user name/home go to /
then use the comand  (pacman -Qo gdal) to find gdal.

### Link Gdal to Cmake 

#### CMakelists 

you need to put the following in your cmake list and do the changes in the links
```
cmake_minimum_required(VERSION 3.13)
project(cost_distance)
add_compile_options(-std=c++11)

set(CMAKE_CXX_STANDARD 14)
set(DCMAKE_SH="CMAKE_SH-NOTFOUND")
set(SOURCE_FILES main.cpp)

include_directories( include  D:/msys64/mingw64/include)  # D is the disk where You Install MSYS2
set(GDAL_LIBRARY+="D:/msys64//mingw64/lib/libgdal.dll.a")  # Where you install the lib
set(GDAL_INCLUDE_DIR+=" D:/msys64/mingw64/include")

add_executable(cost_distance main.cpp raster.cpp raster.h raster_cost_dist.cpp raster_cost_dist.h)
#Specify GDAL libraries to link your cpp executable target against
target_link_libraries(cost_distance D:/msys64//mingw64/lib/libgdal.dll.a)
target_link_directories(cost_distance PUBLIC D:/msys64/mingw64/include)
```

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](https://github.com/mofuss/mofuss/blob/main/LICENSE) file for details.
