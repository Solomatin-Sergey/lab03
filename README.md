# lab03
## Изучение систем автоматизации сборки проекта на примере CMake 
### Task I.
> Вам поручили перейти на систему автоматизированной сборки CMake. Исходные файлы находятся в директории formatter_lib. В этой директории находятся файлы для статической библиотеки formatter. Создайте CMakeList.txt в директории formatter_lib, с помощью которого можно будет собирать статическую библиотеку formatter.

>>Создаем CMakeLists.txt

cmake_minimum_required(VERSION 2.8) 

add_library(formatter STATIC formatter.h formatter.cpp)

>>Подключаем их друг к другу:

cmake ~/lab03_dz/tasks/lab03-master/formatter_lib

Вывод:

-- The C compiler identification is GNU 9.3.0
-- The CXX compiler identification is GNU 9.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/sergsolo/lab03_dz/tasks/lab03-master/formatter_lib

### Task II.
>У компании "Formatter Inc." есть перспективная библиотека, которая является расширением предыдущей библиотеки. Т.к. вы уже овладели навыком созданием CMakeList.txt для статической библиотеки formatter, ваш руководитель поручает заняться созданием CMakeList.txt для библиотеки formatter_ex, которая в свою очередь использует библиотеку formatter.

>> Скопируем formatter_lib в formatter_ex_lib.
>> Cоздаем и подключаем CMakeLists.txt по аналогии с предыдущим заданием.

cmake_minimum_required(VERSION 2.8)
project(formatter_ex)
include_directories(formatter_lib) #Подключаем директорию с заголовочными файлами
add_subdirectory(formatter_lib) #Подключаем директорию с библиотекой
add_library(formatter_ex STATIC formatter_ex.h formatter_ex.cpp)
target_link_libraries(formatter_ex formatter) #Подключаем библиотеку

>> Подключаем их друг к другу:

cmake ~/lab03_dz/tasks/lab03-master/formatter_ex_lib

-- The C compiler identification is GNU 9.3.0
-- The CXX compiler identification is GNU 9.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/sergsolo/lab03_dz/tasks/lab03-master/formatter_ex_lib

### Task III.
>Конечно же ваша компания предоставляет примеры использования своих библиотек. Чтобы продемонстрировать как работать с библиотекой formatter_ex, вам необходимо создать два CMakeList.txt для двух простых приложений:

    hello_world, которое использует библиотеку formatter_ex;
    solver, приложение которое испольует статические библиотеки formatter_ex и solver_lib.
    
    
