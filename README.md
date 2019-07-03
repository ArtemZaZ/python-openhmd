#[python-openhmd](https://github.com/lubosz/python-openhmd)

Сначала ставите [OpenHMD](https://github.com/OpenHMD/OpenHMD/tree/7213580b5748160fedcecc58b11d937b1e88d778):   

    pip3 install meson
    pip3 install ninja
    cd OpenHMD
    meson build -Dexamples=simple,opengl
    ninja -C build
    sudo ninja -C build install

P.S. Если в процессе компиляции появляются ошибки, устанавливайте библиотеки, которых не хватает   

После сборки надо дать права устройству, как показано [тут](https://github.com/OpenHMD/OpenHMD/wiki/Udev-rules-list), или запускайте все из-под sudo   

Можно переходить к сборке под питон

    pip3 install Cython
    python3 setup.py build
    sudo python3 setup.py install
   
Если все прошло нормально, то можно попробовать запустить пример

    ./test.py
    
####TODO: потом еще дополню 
    



