# [python-openhmd](https://github.com/lubosz/python-openhmd)

Клонируете репозиторий, а также инициализируете подмодуль OpenHMD:
    
    cd OpenHMD
    git submodule init
    git submodule update
    cd ..

Устанавливаете необходимые зависимости:
    
    sudo apt install libusb-1.0 libglew-dev libsdl2-dev
   
P.S. могут потребоваться доп. библиотеки, во время компиляции смотрите, чего не хватает и доустанавливайте

Ставите [OpenHMD](https://github.com/OpenHMD/OpenHMD/tree/7213580b5748160fedcecc58b11d937b1e88d778):    
**meson и ninja обязательно ставить из-под sudo, если они уже установлены, переустанавливайте из-под sudo**  

    sudo pip3 install meson
    sudo pip3 install ninja
    cd OpenHMD
    meson build -Dexamples=simple,opengl
    ninja -C build
    sudo ninja -C build install
    cd ..

P.S. Если в процессе компиляции появляются ошибки, устанавливайте библиотеки, которых не хватает   

После сборки надо дать права устройству, как показано [тут](https://github.com/OpenHMD/OpenHMD/wiki/Udev-rules-list), или запускайте все из-под sudo   

Можно переходить к сборке под питон

    pip3 install Cython
    python3 setup.py build
    sudo python3 setup.py install
   
Если все прошло нормально, то можно попробовать запустить пример

    ./test.py

Если появляется ошибка 
    
    ImportError: libopenhmd.so.0: cannot open shared object file: No such file or directory

То создаете файл:
    
    sudo nano /etc/ld.so.conf.d/oculusLib.conf

и пишите в него путь до libopenhmd.so.0, сохраняете и закрываете:
    
    /usr/local/lib/x86_64-linux-gnu

Вызываете:
    
    sudo ldconfig

Все должно заработать)
