# mythinkfan
This a personal thinkfan setup for thinkpad W530 for summer 😎
first you need to install thinkfan

On Arch
```sudo pacman -S thinkfan```
 
 On debian based distro: 
```sudo apt install thinkfan```

 ```find /sys/devices -type f -name 'temp*_input' | xargs -I {} echo "hwmon {}" >> /etc/thinkfan.conf```

use your favourite editor to edit this file
```
/etc/thinkfan.conf
```
add my conf if you want without the lines that start with ```hwmon``` because 
you already have them

edit this file too 
```
/etc/modprobe.d/thinkfan.conf
```
and add these two :
```
options thinkpad_acpi fan_control=1 
experimental=1 
```
two commands:
```sudo modprobe -rv thinkpad_acpi```
```sudo modprobe -v thinkpad_acpi```

test it now: 
```thinkfan -n```

if it works and hear the fan spinning fast 
Enable it as a service and we are done:
```
    sudo systemctl enable thinkfan
    sudo systemctl start thinkfan
    sudo systemctl status thinkfan
```

#TODO 
Automate the whole thing, stop being lazy and experimental=1 is wrong delete it. 
