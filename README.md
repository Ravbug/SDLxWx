# SDLxWx
This demo app shows how to use both wxWidgets and SDL3 in the same process. 
It creates two separate windows, one owned by SDL and one owned by wxWidgets, and sets up event listening in each.

![image](https://github.com/user-attachments/assets/bf361259-bea7-46d0-9501-876057777c61)


### Building
2. git clone with `--recurse-submodules` flag. This will ensure SDL and wxWidgets are available.
3. `cmake -S . -B build`
4. `cmake --build build --target SDLxWx`

