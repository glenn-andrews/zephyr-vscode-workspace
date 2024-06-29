# zephyr-vscode

This is a workspace file developed by Jonathan Beri (beriberikix) to set up Visual Studio Code for Zephyr Application Development. The original files are at https://github.com/beriberikix/zephyr-vscode-example

It has been modified by Glenn Andrews to use with the EMBSYS 330 course to cover basic application development and debugging on the B-L475E-IOT01A Discovery Kit.

## Example details

There are many, many different ways to develop a Zephyr application. This example currently assumes:

* Using Windows (other OS are supported, but paths must be edited)
* All paths follow the Getting Started Guide
    * Zephyr is located at `%HOMEPATH%\zephyrproject`
    * SDK installed at `C:\Program Files\zephyr-sdk-0.16.3`
    * OpenOCD installed at `C:\Program Files\OpenOCD`
    * `C:\Program Files\OpenOCD\bin` added to path
* Uses the Zephyr SDK where possible (ex. Host tools are not available on macOS or Windows)
* Projects located within the `zephyrproject` directory
* Use of Python Virtual Environments
* Building `samples/basic/thread` so we can demonstrate thread-aware debugging
* Targeting the B-L475E-IOT01A Discovery Kit

## Setup Steps (First Time)

1. Follow the Zephyr [Getting Started Guide](https://docs.zephyrproject.org/latest/develop/getting_started/index.html) for your OS and make sure to use virtual environments
2. Turn on Compilation Database with `west config build.cmake-args -- -DCMAKE_EXPORT_COMPILE_COMMANDS=ON`
4. Retrieve `ZEPHYR_SDK_INSTALL_DIR` with `cmake -P zephyr/cmake/verify-
   toolchain.cmake`. It'll be the prefix of the `C_Cpp.default.compilerPath`
    1. This should already be set, but confirm correctness in case the version number 
       has changed.
5. Set the `Python: Interpreter Path`

## Working with a Zephyr Project

1. Copy the `.code-workspace` for your OS to your demo directory
2. Rename the `.code-worksace` file from `zephyr-linux`, `zephyr-macos` or
   `zephyr-windows` to a filename that matches the project (not required,
   but makes it easier to find in the recent workspace list)
3. Use "File->Open Workspace from File..." and open the `.code-workspace` file 
4. From the Workspace menu at the top of VSCode, select "Run Task", then "Show all Tasks". You should find the following tasks:
    1. West Build
    2. West Configurable Build
    3. West Pristine Build
    4. West Flash
5. Use West Build to build the project
6. Use West Flash to flash the board without debugging.
7. To debug the application click on the "Run and Debug" icon on the left toolbar, and select "Launch (workspace)" from the top of the "RUN AND DEBUG" panel.
8. If you want to use OS awareness add `CONFIG_DEBUG_THREAD_INFO=y` to your
   `prj.conf` file
9. You can use the Serial Monitor window as a terminal


## Example With Threads Demo
1. Copy the `%HOMEPATH%\zephyrproject/zephyr/samples/basic/threads` directory to the `%HOMEPATH%\zephyrproject` directory
2. Follow the steps above to set up the workspace file
3. Confirm you can run and debug the application, and view the results on the Serial Monitor

## Credits

https://github.com/beriberikix/zephyr-vscode-example

https://zmk.dev/docs/development/ide-integration
