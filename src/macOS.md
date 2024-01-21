1. install necessary packages
    ```shell
    homebrew install boost spdlog cmake nanomsg rapdijson
    ```

2. change src/CMakeLists.txt, add include in lib directory, link ```fmt iconv``` library, change library suffix
    ```cmake
    INCLUDE_DIRECTORIES("/opt/homebrew/include")
    link_directories("/opt/homebrew/lib")
    add_definitions(-w)
    link_libraries(fmt iconv)   # -l flags for linking prog target
    ```
   
3. ln some boost libraries
   ```shell
   ln -s /opt/homebrew/lib/libboost_thread-mt.a /opt/homebrew/lib/libboost_thread.a
   ln -s /opt/homebrew/lib/libboost_thread-mt.dylib /opt/homebrew/lib/libboost_thread.dylib
   ```
4. change headers in src/Share/fmtlib.h
5. change ```yield``` in SpinMutex.hpp
6. add fmt::formatter to work
7. demo build command for making one Project
   ```shell
   cmake -DCMAKE_BUILD_TYPE=Release ../src/
   make -j4 QuoteFactory
   ```