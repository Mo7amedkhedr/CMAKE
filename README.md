# CMAKE
CMake is a cross-platform open-source meta-build system which can build, test and package software. It can be used to support multiple native build environments

## first step to do Cmake correctly\:

 - `CmakeLists.txt`  that include command you want to make
 - `then mkdir build directory `that include build and make files


## How to build 

- into build dir I have to run cmake command such as: `cmake -G "Unix Makefiles" .. `

## Here’s command included into Cmakelists.txt:
-  `make_minimum_required (VERSION 3.30)`
- ` project (HELLOAPP)`
-  `add_executable (hellobinary test.cpp src/calc.cpp)to included   source files` hellobinary this is the name of executable file 

## to include header file  Here’s command to include:
`• target_include_directories (hellobinary PUBLIC include/)`


## to make variable into cmake :
- `set ( SRC_FILE  test.cpp  src/calc.cpp )`
- `add_executable ( hellobinary  ${SRC_FILE} )`

## to print var into cmake:
-` message ( "the src file  contain ${SRC_FILE}" )`

## what is CMAKE_SOURCE_DIR :
<mark>**CMAKE_SOURCE_DIR** </mark>   : this built in variable that has full path to Cmakelists.txt)
## the structure of if condition is similar to preprocessor here is example
```
if ( EXISTS  ${CMAKE_SOURCE_DIR}/test.cpp ) // full path shall be provided to search correctly <br>
message ( STATUS"the test.cpp is found" ) <br>
else() <br>
message(FATAl_ERROR"the test.cpp is not found")<br>
endif()
```

> [!NOTE]  
> add_executable ( hellobinary ${SRC_FILE} ) >> to add to exe file 2 source file
<mark> target_include_directories ( hellobinary PUBLIC include/) </mark>  to include heder file
to exe file

> [!IMPORTANT]  
> - <mark> add_subdirectory ( ${CMAKE_SOURCE_DIR}/lib )</mark> --> to include cmake into your cmake file
> - <mark>target_link_libraries ( hellobinary PUBLIC wifi_lib )</mark> --> to make link with library generated into cmake

## Some import var in cmake :
```
- message( STATUS "CMAKE SOURCE DIR ${CMAKE_SOURCE_DIR}" )
- message( STATUS "CMAKE_CURRENT_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}" )
- message( STATUS "CMAKE_BINARY_DIR ${CMAKE_BINARY_DIR}" )
- message( STATUS "CMAKE_CURRENT_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}" )
- message( STATUS "CMAKE_GENERATOR ${CMAKE_GENERATOR}" )
```
## var to set into cmake:
```
- set(CMAKE_CXX_STANDARD 14)
- set(CMAKE_CXX_STANDARD_REQUIRED True)
```
> [!TIP]
> message(STATUS "CMAKE_CXX_STANDARD is ${CMAKE_CXX_STANDARD}") --> to print c++ standard<br>
> to set variable into cmake call : cmake .. -DCMAKE_CXX_STANDARD=14<br>
> to generate config file from another config file into cmake file :<mark> configure_file( defaultconfig.h.in defaultconfig.h )</mark><br>
> to get major and minor : @HELLOAPP_VERSION_MAJOR@ @HELLOAPP_VERSION_MINOR@<br>
> to include directory that include output here is command : <mark>target_include_directories( hellobinary PUBLIC ${PROJECT_BINARY_DIR} )</mark><br>

## to make library here’s example: in main cmake file
```
 add_subdirectory( ${CMAKE_SOURCE_DIR}/lib )   // to reach to makefile
 target_link_libraries( hellobinary PUBLIC wifi_lib )  // to link with library
```
## how to use some commands 
| Command | Description |
| --- | --- |
| Debug condition | cmake if (NOT DEBUG) # Your code for the NOT DEBUG case endif() |
| Logical AND condition | cmake if (Var AND var2) # Your code for the Var AND var2 case endif() |
| Logical OR condition | cmake if (var OR VAR2) # Your code for the var OR VAR2 case endif() |
|Regular expression match condition | cmake if (myval MATCHES "regularexpression") # Yourcode for the MATCHES case endif() |
| File existence condition | cmake if (EXISTS "file") # Your code for the file existence case endif() |
| Numeric comparison condition (LESS) | cmake if (Var LESS Var2) # Your code for the Var LESS Var2 case endif() |
| Check if a target exists | cmake if (TARGET wifi_lib) # Your code for the target  existence case case (e.g., add_executable, add_library ) |



## Explanation for previous command 

| Command | Description |
| --- | --- |
| cmake_minimum_required(VERSION 3.22)|[Specifies the minimum version of CMake required tobuild the project ](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)    |                                                                                  
|project (HELLOAPP VERSION 3.2)  |[Sets the name and version of the project 1](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)  |
| set(SRC_FILE test.cpp src/calc.cpp) |Defines a variable named SRC_FILE with the value oftest.cpp src/calc.cpp  |
| set(PRODUCT_YEAR “2021”) |Defines a variable named PRODUCT_YEAR with thevalue of “2021”  |
| add_subdirectory(${CMAKE_SOURCE_DIR}/lib) |[Adds a subdirectory named lib to the build 1](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)  |
|add_executable (hellobinary ${SRC_FILE}) |[Creates an executable named hellobinary from the source files specified by the SRC_FILE variable 1](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)|
|target_include_directories(hellobinaryPUBLIC include/) | [Adds include/ as a public include directory for the hellobinary target 2](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html) |
|target_include_directories (hellobinaryPUBLIC lib/)|[Adds lib/ as a public include directory for the hellobinary target 2](https://cmake.org/cmake/help/book/mastering-cmake/cmake/Help/guide/tutorial/index.html)|
|target_link_libraries(hellobinary PUBLIC wifi_lib)  |[Links the wifi_lib library to the hellobinary target as a public dependency 2 ](https://cmake.org/cmake/help/book/mastering-cmake/cmake/Help/guide/tutorial/index.html)  |
|target_include_directories(hellobinaryPUBLIC ${PROJECT_BINARY_DIR})   |[Adds the project binary directory as a public include directory for the hellobinary target 2](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)|
|if(debug) … endif()   | [Executes a conditional block of commands if the debug variable is true 3](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html)|
| set(DEBUGINFO “Ahmed Author”)  |  Defines a variable named DEBUGINFO with the value of “Ahmed Author” |
|message(FATAL_ERROR “Your fatal error message here”)   | [Displays a fatal error message and stops processing 4](https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html) |
|configure_file(defaultconfig.h.in defaultconfig.h)   |Copies and configures a file named defaultconfig.h.in to defaultconfig.h    |

## if condition 
![first](https://github.com/user-attachments/assets/783d7c52-a29e-416a-b6e9-de77d8bcf100) 

## For loop
![second](https://github.com/user-attachments/assets/5d256a29-68c6-4e52-9b6b-7e1db36d81f2)

## while Loop
![third](https://github.com/user-attachments/assets/a8ec8855-2dac-4a0f-ba5c-8e7ec132d57b)

## Function
![fourth](https://github.com/user-attachments/assets/6b619aed-016e-438f-917d-1f0be84ccb4d)

## explanation for each line

- Define a function named happynewyear
> function (happynewyear arg1)
- Print the name of the first argument
> message ("ARG1 ${arg1}")
- Print the value of the variable whose name is the first argument
> message ("ARG1 ${${arg1}}")
- Print the list of extra arguments
> message ("ARGN ${ARGN}")
- Print the number of arguments
> message ("ARGC ${ARGC}")
- End the function definition
> endfunction ()
## how to define var into cmake cach 
![fifth](https://github.com/user-attachments/assets/9b48f35a-0257-4db1-a4b4-5b21df72c0b7)

## how to use install method in cmake to transfer files
![sixth](https://github.com/user-attachments/assets/be505125-7c34-4c21-af72-b4a126eca9ef)

## command to do installion 
![sevnth](https://github.com/user-attachments/assets/df3822af-896e-4fa9-9ba9-963d93d939a4) 

## File command into cmake 
![eigth](https://github.com/user-attachments/assets/733ce4b8-b57e-4d97-950c-4b9c321baa88)

## string command 
![ninth](https://github.com/user-attachments/assets/721a4712-c33d-44d1-93c6-72dbdcf58ee3)

## how to make shared library 
![tenth](https://github.com/user-attachments/assets/7cc1cfde-e0b3-4816-bdf0-0a45bfdfcaca)

## Cmake for avr 32
![eleventh](https://github.com/user-attachments/assets/3b1a5a88-be1d-4d41-994c-b5fb48f86276)
> ## Explanation for previous code
> ![twelvth](https://github.com/user-attachments/assets/397bcd4b-e548-466e-b3c6-8178c1b27ce5)

## this command generic for embedded target
![thhhhi](https://github.com/user-attachments/assets/f0fcb8a1-ee6b-4c94-8ab1-9c82815556d1)

## this is command for Rasberry pi 
>![fourteeen](https://github.com/user-attachments/assets/71778d13-ceee-44e0-9d14-6cc745d4f508)
>![fifteen](https://github.com/user-attachments/assets/a501159b-ea1f-4d8e-9b6a-86e48698cef7)







