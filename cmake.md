# CMake

CMake is a meta build tool that allows you to generate native build scirpts for a range of platforms as Unix Makefiles, Xcode, Visual Studio etc.

We by creating a CMakeLists.txt file in the root of our project.

​	

```cmake
cmake_minimum_required(VERSION x.x)
project(app_project)
add_executable(myapp main.c)
install(TARGETS myapp DESTINATION bin)
```

Thats all we need to be able to build our app with any of the available generators.

**add_executable** defines our binary with all linked source files.

**install** tells cmake to install our binary into the bin directory of the install directory.

**Building**

CMake supports out-pf-source builds -- so all our compiled code goes into a directory seperate to the sources.

To start a build we create a new folder:

```
mkdir build
cd build
```

And call cmake with the path to the project's root (in this case the parent folder):

```
cmake ..
```

This will generate build scripts using the default generator -- on Linux/OSX this should be Makefiles.

By default cmake will install our build into the system directories. To define a custom install directory we simply pass it to cmake:

```
cmake .. -DCMAKE_INSTALL_PREFIX=../install
```

To run the build script you can simply use the Makefile:

```
make
make install
```

We can now run our binary from the install directory:

```
../install/bin/myapp
```

If we wanted to use a different generator we pass it to cmake using the -G parameter:

```
cmake .. -GXcode
```

This will output a readily configured Xcode project to build our app.

```
set(CMAKE_CXX_STANDARD 14)
```

 Sets the CMAKE_CXX_STANDARD variable to the value of 14, as we selected when creating the project.

**Using CMake with libraries**