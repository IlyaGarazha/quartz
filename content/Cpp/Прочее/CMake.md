Создайте папку sem_11 следующего содержания или скопируйте [папку](https://github.com/garazha-ilya/Semester_2/tree/main/sem_11):
```
sem_11__
	src__
		main.cpp
		sem_11.cpp
		sem_11.h
	CMakeLists.txt
```

Содержимое CMakeLists.txt:

```cmake
cmake_minimum_required(VERSION 3.25)  # Версия CMAKE

set(CMAKE_CXX_STANDARD 17)            # Стандарт C++
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(sem_11)                       # Название нашего проекат

# Создаём переменную source, в которой лежат наши файлы
# Они лежат в src/main, а не просто в src, так как иногда добавляют src/test
file(GLOB_RECURSE sources   src/main/*.cpp src/main/*.h)

# После сборки в папке build будет лежать файл sem_11_exec
# (для Windows будет создан sem_11_exec.exe)
add_executable(sem_11_exec ${CMAKE_SOURCE_DIR} ${sources})

target_compile_options(sem_11_exec PUBLIC -std=c++17 -Wall -Wextra)

# Без этого можно обойтись, но в VS Code это проще использовать "из коробки"
include(CTest)
enable_testing()
```

Те, кто используют VS Code:
1. Установите [расширение_1](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) и [расширение_2](https://marketplace.visualstudio.com/items?itemName=twxs.cmake)
2. Перейдите в папку с нашими файлами и CMakeLists.txt
3. Нажмите `Ctrl+Shift+P` и наберите CMake Configure
![[Pasted image 20231123110753.png]]
Далее выберите подходящий вашей системе компилятор. И после этого у вас должна появиться папка build (на том же уровне, что и CMakeLists.txt, т.е. в sem_11).

Теперь можете набрать `Ctrl+Shift+P` -> CMake: Build или же нажать `Shift+F5`

В результате у вас выполнится файл, а также будут указаны предупреждения
![[Pasted image 20231123111627.png]]