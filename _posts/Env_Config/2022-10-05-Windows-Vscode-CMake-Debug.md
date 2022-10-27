---
name: "Windows Vscode Debug C++ Configuration"
categories: ["Configuration"]
tag: ["Configuration"]
---

Folder Structure:
!["Folder Structure"](\assets\img\post\Env_Config\Windows-Vscode\folder_structure.png)

CMakeLists.txt:
```cmake
project(main)

aux_source_directory(src SRCS)

add_executable(${PROJECT_NAME} ${SRCS})
```

launch.json
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Windows launch",
            "request": "launch",
            "type": "cppvsdbg",
            "program": "${command:cmake.launchTargetPath}",
            "cwd": "${workspaceFolder}",
            "console": "externalTerminal",
        }
    ]
}
```

Compiler: Use Visual Studio's Compiler

Debug:
```
F5
```

Build command:
```sh
cmake --build build
```