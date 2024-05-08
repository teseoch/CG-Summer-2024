# Windows Instructions

If you are using Windows, you have two main options to compile and run the assignments:
1. Use Visual Studio (**not** Visual Studio Code), RECOMMENDED
2. Use Microsoft WSL

**Option 1** requires installing Visual Studio, which is big and free only for students.

**Option 2** requires installing Microsoft WSL, which is free and will allow running Linux **natively** on Windows. This will enable you to follow the Unix instructions.


## Option 1

Download and install [Visual Studio](https://visualstudio.microsoft.com).


If you have a modern version of Visual Studio, you should be able to use the `cmake` integrated into Visual Studio. Just open Visual Studio and click the `continue without code` option at the bottom. This will open Visual Studio without opening the code.

![](img/vs-open.png)

Then click on the `File` menu, then `open`, and finally `cmake`. Navigate to the folder where the `CMakeLists.txt` is and select it. This will run `cmake` and configure your Visual Studio project.

![](img/vs-cmake.png)



## Option 2

Open a powershell with administrative privileges and type `wsl --install` ([Microsoft Documentation](https://docs.microsoft.com/en-us/windows/wsl/install)). Wait for the process to finish and restart your machine. Upon restart, finish the Linux installation by creating a username (all lowercase) and a password.

Open Visual Studio **Code** and install the [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extension, if not present. Then click on the bottom left green corner with `><` and select new `Remote-WSL: New Window`. This will connect Visual Studio Code to the Linux subsystem. Once it is open, click open folder and navigate to your code. **Note** your Windows files are under `/mnt/c/Users/`. Check the [complete documentation](https://code.visualstudio.com/docs/remote/wsl) in case of a problem.

Once you open the folder with the code, click on the *Terminal* menu and go to the **Linux** terminal. There you need to install cmake
```bash
sudo apt install cmake
```
and `g++`
```bash
sudo apt install g++
```

From here you can follow the Unix instructions, that is
```bash
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Debug ..
./<executable>
```

If cmake fails because of `Detecting CXX compiler ABI info` try this:

1. Create file `wsl.conf` in `/etc/` with content:
```
[automount]
options = "metadata"
enabled = true
```
2. Reboot your wsl
```
wsl.exe -t Ubuntu
```

To create the file, use
```bash
sudo nano /etc/wsl.conf
```
Paste the content and type `ctrl + x` to close; when closing, answer `Y` to save the file.

If other `cmake` failures occur, delete the file `CMakeCache.txt` inside the `build` folder (`rm CMakeCache.txt`) and rerun `cmake`.




## Option 1.b (Using Visual Studio with cmake)


Run `cmake` from a power shell as for Unix. This should generate a file `.sln`: a Visual Studio project. If the command fails, try using the cmake gui.

![](img/cmake-gui.png)

Once you open the Visual Studio project, you should see several projects in the solution explorer. Right-click on the one you want to run and select *Set as StartUp Project*

![](img/startup-proj.png)

Finally, you can press the play button to compile and run.

